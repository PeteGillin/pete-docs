# How to think about async

---

## Agenda

- Why async?
- Threadpool best practice
- Async API choices in Java
- Async API best practice
- Reactor fundamentals

---

## Why async?

Note: Understanding the problem async programming is solving really helps us
think about how to do it right.

---

## Disclaimer

- None of this code is production-ready.
- The next slide contains a stupid suggestion.

---

Let's build a server in Java — from scratch!

---

(&#128072; Never do this.)

---

But let's do it anyway!

---

- Serve a generic TCP request/response protocol.
- Use only the JVM.

---

```java
ServerSocket server = new ServerSocket(port);
while (true) {
  Socket socket = server.accept();
  byte[] request = toByteArray(socket.getInputStream());
  byte[] response = handler.handle(request);
  socket.getOutputStream().write(response);
  socket.close();
}
```

---

...where `handler` is an instance of...

---

```java
interface Handler {
  byte[] handle(byte[] request);
}

```

---

## Problems

- No error handling.
- No graceful shutdown.
- Not even basic amenities such as logging.

---

## But remember our disclaimer

- None of this code is production-ready.

---

## Problem

Can only handle one request at a time.

Note: We're just going to concentrate on this problem for now.

---

## Solution

Use threads!

---

```java
ServerSocket server = new ServerSocket(port);
while (true) {
  new Thread(
      () -> {
        Socket socket = server.accept();
        byte[] request = toByteArray(socket.getInputStream());
        byte[] response = handler.handle(request);
        socket.getOutputStream().write(response);
        socket.close();
      })
    .start();
}
```

Note: This is so not-production-ready that it doesn't even compile! (We need to
catch `IOException`.) Whatever.

---

## Problem

Uses an unlimited number of threads — and threads aren't free.

---

## Threads

- A system-level construct for preemptive multitasking:
    - If there are more runnable threads than cores...
    - ...then the kernel will choose which to schedule...
    - ...and preempt them to give another thread a chance.
- Too much preemption hurts performance.
- System-level stack per thread &rArr; large memory footprint.

---

## Runnable vs sleeping threads

- When you make a blocking system call...
- ...your thread goes into a sleeping state...
- ...and the kernel won't schedule it until something wakes it.
- Examples:
    - I/O
    - Waiting on another thread
    - Timed waits (`Thread.sleep`)

Note: This will be important later.

---

## Problem

Uses an unlimited number of threads — and threads aren't free.

---

## Solution

Use virtual threads!

---

Virtual threads sound cool, right?

---

```java
ServerSocket server = new ServerSocket(port);
while (true) {
  Thread.ofVirtual().start(
    () -> {
      Socket socket = server.accept();
      byte[] request = toByteArray(socket.getInputStream());
      byte[] response = handler.handle(request);
      socket.getOutputStream().write(response);
      socket.close();
    });
}
```

---

## Problem

Virtual threads are a 'preview' feature in Java 19 (released Sept '22).

---

## Virtual threads

- Java implementation of "green threads".
- A JVM-level construct for cooperative multitasking:
    - JVM decides which virtual threads to schedule on real threads.
    - Kernel schedules real threads as normal.
- No preemption — threads must yield.
    - Automatic yield on all blocking operations.
- JVM-level stack per virtual thread &rArr; lighter memory footprint.

---

The jury is still out on whether virtual threads will solve all our problems.

---

But anyway, we can't use them, so we're back to real threads.

---

## Problem

Uses an unlimited number of threads — and threads aren't free.

---

## Solution

Use a thread pool!

---

```java
Executor executor = new ThreadPoolExecutor(...);
ServerSocket server = new ServerSocket(port);
while (true) {
  executor.execute(
    () -> {
      Socket socket = server.accept();
      byte[] request = toByteArray(socket.getInputStream());
      byte[] response = handler.handle(request);
      socket.getOutputStream().write(response);
      socket.close();
    });
}
```

---

## Executor

- Manages a pool of threads.
- Also manages a work queue.
- Submitted tasks are queued until a thread is available.

---

## Problem

If the server serves a mix of fast and slow requests, they'll all compete for
the same threadpool — and the slow requests will tend to monopolize it.

Note: This may sound picky, but it's at the core of this whole thing.

---

## Example

- We get a burst of requests which need slow database access.
- They're arriving faster than we can handle them!
- They start piling up on the executor's work queue.
- A health check request comes in.
- We should be able to respond quickly...
- ...but it's stuck at the back of the queue.
- If our server is too slow to respond, our baby-sitting infrastructure (e.g.
  kubernetes) may kill it!

---

## Solution

Use two thread pools — one for fast requests and one for slow ones.

---

## Problem

We can't do this with our current `Handler` interface — our for loop has to
decide which thread pool to use, but it doesn't know what kind of request it's
dealing with.

Note: The whole point of the `Handler` abstraction is that its caller shouldn't
have to know anything about what it's doing.

---

## Solution

Give `Handler` an async API!

---

```java
interface Handler { 
  void handle(byte[] request, Consumer<byte[]> callback);
}
```

---

...so now our server loop looks like...

---

```java
Executor executor = new ThreadPoolExecutor(...);
ServerSocket server = new ServerSocket(port);
while (true) {
  executor.execute(
    () -> {
      Socket socket = server.accept();
      byte[] request = toByteArray(socket.getInputStream());
      handler.handle(
        request,
        response -> {
          socket.getOutputStream().write(response);
          socket.close();
        });
    });
}
```

---

## Basic principle

Once the async `handle` method has been called, the decision whether to do
everything on the calling thread or to transfer execution to another thread (or
threads!) is made by the `Handler`...

---

...or by code that the `Handler` calls out to.

---

For example, we can move to another thread at the point in the stack where we do
a blocking call to some backend.

---

The caller doesn't need to know or care which thread the callback is executed
on.

---

Once execution has been transferred to another thread, the calling thread is
freed up to handle the next request.

---

## Hang on: Thread... or threads?

- Async APIs make it easy to do multiple blocking calls in parallel.
- Example: If joining results from two backends, make both calls in parallel.
- This is good for latency.

---

## Parallelizing tasks in a blocking

- Start each task on its own thread.
- Wait for all tasks to be complete.
- Combine the results and continue execution on the calling thread.
- Bad: One thread is just blocked waiting for other threads.
- Can be fiddly to code.

---

## Parallelizing tasks in a blocking v2

- Could do one of the tasks on the calling thread instead of a new thread.
- Then have to wait for all other tasks to be complete.
- Bad: One thread is still just blocked waiting for other threads.
  - Unless we correctly pick the slowest task.
- More fiddly to code.

---

## Parallelizing tasks in an async world

- Start each task on its own thread.
- Calling thread returns.
- Tasks save their results as they complete.
- Combine the results and continue execution on whichever thread finishes last.
- Good: No unnecessary blocking.
- Most async frameworks make this easy.

---

## Can we avoid blocking a thread per task?

Sometimes, yes!

---

Suppose we're implementing a client library for talking to a backend.

---

## Blocking client library

- Open socket to backend.
- Send request.
- Wait for response.
- Close socket.
- Return response.

---

## Async client library.

- On calling thread:
  - Open socket to backend.
  - Send request.
- On a single background thread:
  - Wait for responses from _any_ of the open sockets.
  - Hands off work to another threadpool.
- On that other threadpool:
  - Close socket.
  - Invoke callback, passing in response.

---

Waiting for responses from any of the open sockets is done using the `select`
system call — exists for exactly this purpose.

---

Can't do this with a blocking client API — that has to return the response, so
it has to block the calling thread.

---

- Blocking client library:
  - One thread blocked for each concurrent request.
- Async client library:
  - One thread blocked _in total_.
  - Only start a thread to handle each response when it's available.

---

## Or, even better...

- Instead of opening a socket for each request...
- ...multiplex many requests over one connection...
- ...if your protocol supports this.
- Example: gRPC does this over HTTP/2.

---

## So, why async?

- Allows decision to transfer execution to a different thread pool be made at
  the appropriate layer of the system.
- Makes parallelizing tasks easier and more efficient.
- Enables client libraries which don't block a thread per concurrent request.

---

## Threadpool best practice

---

## How many threadpools do you need?

- Segregate fast and slow tasks.
  - Avoids slow tasks starving out fast ones.
- Consider segregating different classes of slow task.
  - Can scale each appropriately.
- Never block on a task scheduled in your own threadpool.
  - Segregate parent and child tasks.
- Sometimes just cleaner for components to own their own threadpools.

Note: We covered the first point already. We'll cover the second and third
points later.

---

## What are 'fast' and 'slow' tasks?

- Slow:
  - Most blocking operations, esp. network I/O.
  - Anything sufficiently computationally intensive.
- Fast:
  - Anything else.
  - Includes logging.

Note:

- There's no firm definition of 'sufficiently computationally intensive'.
- Logging could technically be blocking, depending on the configuration.

---

## Terminological inexactitude

It is common to use the terms 'blocking' and 'non-blocking' instead of 'slow'
and 'fast' — even when this isn't technically accurate.

---

We'll do the same from now on.

---

## Aside on computationally intensive tasks

- Will often move these off our server and into a worker pool.
- Now the server is just waiting for a response — which really is blocking.

---

## What type of threadpool should I use?

That depends on what it's doing.

---

## Bounded elastic threadpools

- For work in response to variable load.
  - Add more threads when under load...
  - ...up to some upper bound.
  - Stop threads when idle...
  - ...down to some lower bound.
    - (Avoids cold starts.)
- Includes most server work.

---

## Fixed threadpools

- For when you just want to plough through work.
- More common for batch processors.

---

## What size of threadpool should I use?

Again, that depends on what it's doing.

---

## Sizing non-blocking threadpools

- Scale with number of cores.
  - Threads will be runnable all/most of the time.
  - Avoid too much overhead from preemption.
- What scaling factor?
  - Depends.
  - At first, pick something reasonable.
  - Fine-tune later, when you have enough load to experiment.
- Again, keep an eye on the memory usage.

---

## Sizing blocking threadpools

- Normally no need to scale with number of cores.
  - Threads will be sleeping most of the time.
- Often associated with some kind of resource.
  - Example: Each thread has a database connection.
  - Thread pool size determines number of concurrent connections.
- Again, keep an eye on the memory usage.

---

## Avoiding deadlock

Never block on a task scheduled in your own threadpool.

---

- Suppose some kind of request triggers a 'parent' task...
- ...And each 'parent' tasks schedules a 'child' task and then blocks until it's
  complete...
- ...And the 'parent' and 'child' tasks are scheduled on the same threadpool.

---

- We get a burst of requests which need slow database access.
- They're arriving faster than we can handle them!
- The threadpool gets filled with 'parent' tasks.
- The 'child' tasks go to the back of the executor's work queue.

---

- The 'parent' tasks can't complete until the 'child' tasks do.
- But the 'child' tasks can't even start while the 'parent' tasks are filling
  the threadpool.
- DEADLOCK!

---

Solution: Use a different threadpool for the 'parent' and 'child' tasks.

---

Also need to avoid longer dependency chains — don't schedule 'grandparent' and '
grandchild' tasks in same threadpool, and so on.

---

The deadlock danger only applies if you one thread is waiting for another to
complete (blocking style).

---

It's always safe to hand over execution to continue on another thread (async
style).

---

(This is one reason to avoid blocking where possible.)

---

## Async API choices in Java

---

## Async API best practice

---

## Reactor fundamentals

