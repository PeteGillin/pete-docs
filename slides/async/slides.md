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
threads!) is made by the `Handler` (or by code the `Handler` calls out to).

---

The caller doesn't need to know or care which thread the callback is executed
on.

---

Once it has invoked the async method, the calling thread is freed up to handle
the next request.

---

## Thread... or threads?

- Async APIs make it easy to do multiple blocking calls in parallel.
- Example: If joining results from two backends, make both calls in parallel.
- This is good for latency.

---

TODO: parallelization in a blocking world
TODO: parallelization in a blocking world (fancy version)
TODO: parallelization in an async world

TODO: select magic
TODO: multiplexing

---

## Threadpool best practice

TODO: split fast and slow
TODO: define fast and slow
TODO: terminological inexactitude
TODO: split slow according to scaling needs
TODO: bounded elastic vs fixed
TODO: guide for sizing, non-blocking and blocking
TODO: avoiding deadlock

---

## Async API choices in Java

---

## Async API best practice

---

## Reactor fundamentals

