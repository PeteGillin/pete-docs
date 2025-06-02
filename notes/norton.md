# Norton's Dome: some thoughts

## What is Norton's Dome?

Norton's Dome is a thought experiment proposed in 2003 by John D Norton, a philosopher of physics. It purports to show that Newtonian mechanics exhibit non-determinism. If you're not familiar with it, I recommend reading the write-up on [write-up on his site][Norton]. It's short and accessible.

## What am I reading?

In this page, I'll give my view on the claims, and on some of the other responses out there (though I'll only scratch the surface). And I'll share some ideas which I haven't seen elsewhere (though my research has been far from exhaustive).

I include almost no maths in here. So if you're looking for rigorous proofs, you're going to be disappointed. Sorry about that.

## Are Newtonian mechanics with continuous boundary conditions deterministic?

Yes.

I believe that the fundamental existence and uniqueness theorem for ordinary differential equations guarantees that Newtonian mechanics will be deterministic when the boundary conditions are sufficiently continuous. From what I've seen, this is the consensus view. I recommend reading [David B Malament][Malament] for more.

(I am being deliberately vague about what 'sufficiently continuous' means as I want to avoid getting bogged down in detail. If that sort of thing bothers you, this might not be the write-up you are looking for.)

## Do we have to care about Newtonian mechanics with discontinuous boundary conditions?

As far as practical physics is concerned, no. You cannot construct a system with truly discontinous boundary conditions.

To put it another way: Regular matter is made out of electrons and nucleons and the like, interacting primarily through the gravitational and electromagnetic forces. When we frame things in terms of solid objects and normal forces and the like, we are making an approximmation. We will never be forced to choose an approximation which involves singularites. (As it happens, we also know that quantum mechanics will become important at subatomic scales, although that's not central to this argument.)

## Great, then can I go home now?

If you like, yes.

The two previous answers mean that, in practice, all is right with the world, and everything that follows has the status of a thought experiment. If you're interested in the thought experiment then you're welcome to stick around.

## Are Newtonian mechanics with discontinuous boundary conditions deterministic?

No. At least, I don't think so.

Norton's Dome goes some way towards illustrating this. There are some quibbles about the Dome and the First Law, but I think we can address those.

## Are the time-reverals arguments that the singularity in Norton's Dome is irrelevant wrong, then?

Yes.

The argument typically goes something like this: Newtonian mechanics are symmetric under time reversal. The 'spontaneous motion' solution on Norton's Dome is the time-reversal of a solution where the object slides up the side of the dome and comes to rest at the peak. But we can silde an object up the side of _any_ shape of dome and have it come to rest at the peak: we just need to ensure that the kinetic energy at the start is exactly equal to the difference in gravitational potential energy between the starting height and the peak. So, reversing time, we can have spontaneous motion solutions on any shape of dome, right?

The flaw here is that, for a continuous dome, the object will asymptotically approach the peak, but will not reach it in finite time. (Conservation of energy only requires that it would be stationary if it did reach the peak, it doesn't say it will ever get there.) And so, reversing time, the object will not move any finite distance from the peak in finite time.

(We should be fair to Norton: He mentions the time-reveral idea in his paper, and then immediately points out this caveat.)

I think this claim about asymptotic approach follows from time reversal symmetry and the fundamental existence and uniqueness theorem. As an example, you can solve the equations of motion on a semispherical dome, and you do indeed find that the object only asymptotically approaches the peak.

For what it's worth, there is a kind of intuitive way to understand this, too. As we approach the peak of a continuous dome, the gradient decreases. That means that the deceleration of the object decreases. That means that it must be moving slower and slower as it approaches the peak if it is not going to overshoot. And that's why it can only asymptotically approach the peak. We need the discontinuity for the slope to drop to zero at the peak while still providing enough deceleration to stop the object in finite time.

## Is Norton's Dome uniquely interesting?

Not uniquely, no. But it is interesting.

Other interesting examples to think about include balancing an object on the point of a cone, and swirling an object inside a bowl.

## Okay, I'll bite: What's this about balancing an object on the point of a cone?

Suppose that, instead of Norton's Dome, we have a cone shape, sloping down with a constant gradient from a peak.

This has one significant advantage as a thought experiment, which is that the equations of motion (away from the peak, at least) are high-school level physics. You can certainly slide an object up the slope with the correct starting velocity to have it come to rest at the peak, and it will reach the peak in finite time. If we also allow that it can remain stationary at the peak when it gets there, then time-reversal shows us that we also have solutions _à la_ Norton, where it rests at the peak for some time before spontaneously starting to slide down. And we again have non-determinism.

This version of the thought experiment also has a significant disadvantage, however. The equations of motion for an object on a slope depend on its gradient, and the gradient of the cone is not well-defined at its peak. So it's hard to write down, let alone solve, the equations of motion at the peak, or to talk about whether we can balance an object there.

(If you are tempted to argue that the force at the peak must be straight up, by symmetry, then I'd invite you to consider the case of a sheared cone which is not symmetric.)

The key thing that distinguishes Norton's Dome from the cone is that the Dome _does_ have a well-defined gradient at the peak, and therefore that we can write down the equaitions there. Norton shows that it's enough for the rate of change of the gradient to diverge to cause problems for determinism.

## And what about swirling an object in a bowl?

Now suppose that, instead of sliding an object on the outside of a dome, we are sliding it on the inside of a bowl. And also suppose that, instead of starting it at rest at the apex, we are starting it at some point away from the bottom/centre, with a non-zero velocity which has a component pointing around the bowl, and may have a component up or down the slope. That is, the object is swirling around the inside of the bowl.

(All our bowls are going to have rotational symmetry.)

There is one class of solution which has the object orbiting the centre of the bowl, i.e. moving in a circle of constant height around the inside surface. We just have to start it moving in a circle, and pick the correct speed (which will be a function of the gravitational field strength, the radius of the circle, and the gradient of the bowl at that point).

If you start it in a circular motion with the wrong speed, or if you start it with a radial as well as a circular component to its velocity, then it will move either inwards and downwards or upwards and outwards instead of orbiting at constant height. If you have it moving upwards, it will slow down. If you get the starting conditions right, you might be able arrange that this solution turns into a constant-height orbital solution. (Conservation of energy and conservation of angular momentum are enough to determine the constaints on the starting condition.) If it so happens that it reaches that orbital solution in finite time, then we can reverse time and get a solution where the object starts out in an apparently stable orbit and then, at an arbitrary moment, spontaneously falls out of it. And, once again, we have non-determinism.

I assert that, for a sufficiently continuous bowl, the object will only asymptotically approach the orbital solution, and will not reach it in finite time, and therefore determinism is saved. I believe that this again follows from the fundamental existence and uniqueness theorem.

(I have sketched out maths for one specific continuous bowl and confirmed to my satisfaction that this asymptotic approach occurs. The maths isn't fit to be published, so I'm not including it. Sorry.)

I also believe that, for a discontinous bowl, the object can reach the orbital solution in finite time, and therefore we do really have non-deterministic solutions. I don't have any proof of this, and I haven't even tried to construct a bowl of a suitable shape. This belief is only based on intuition. (I am very sorry.)

## Does Newton's First Law rescue determinism?

No, I don't think so, although not for the reasons that Norton gives.

The First Law is normally stated something like this: "A body which is subject to no net force remains at rest, or in uniform motion in a straight line." This provides a potential line of defence for determinism in the case of the Dome. After all, the object starts at rest, and is subject to no net force, so it should remain at rest.

Norton rejects this. There's a passage in his text which leapt out at me on first reading:

> It is natural to visualize "uniform motion in a straight line" over some time interval, but we will need to apply the law at an instant.

He goes on to reformulate the first law accordingly, in such a way that it is just a special case of the second law where the force is zero. My immediate reaction is to ask: _why_ do we "need" to apply the law in this way? As far as I can see, he gives no justification. Maybe we _can_ apply it over some time interval, as Norton concedes is "natural", and reject his spontaneous motion solutions on that basis.

An aside: At first glance, it seems startling that there should be two rival ways of interpreting something as basic as Newton's First Law and that it hasn't been a big deal until now. However, I'd assert that, with continuous boundary conditions, the two interpretations become identical. So there is no practical physical situation where the distinction is meaningful.

Given this ambiguity, why have I asserted that the First Law does _not_ rescue determinism? This is where the object swirling in the bowl comes into its own. Although I have not proved it, I believe that there are solutions where the object can spontaneously fall out of orbit — and, while in orbit, it was subject to a net force (and so is neither at rest nor in uniform motion in a straight line) and so the First Law does not apply.

## Can we add to Newton's Laws in a way that restores determinism?

My answer here is a firm "maybe" with a side-order of "but maybe we're wrong to want to".

I mean, I get it: The idea that Newtonian mechanics may admit non-deterministic solutions just _feels_ wrong. It goes against everything we are taught and against intuition. However, we're talking about situations with non-continuous boundary conditions, which are inherently non-physical, so maybe we shouldn't try to apply our intuition to them.

Having said that, let's explore some options.

One thought was to generalize the First Law, and state that it applies separately in each spatial dimension. We'd then be able to say that the particle in a constant-radius orbit is at rest _in the vertical dimension_ (i.e. that its velocity has no vertical component), and the vertical component of the net force is zero, and thus that it stays at rest in the vertical dimension. This handily eliminates the unwanted solutions.

However, I suspect that won't always work. I suspect there might be other solutions, perhaps ones which resemble elliptical rather than circular orbits, which exhibit similar spontaneous de-orbiting. And that generalized First Law won't help there. (I accept that I am hypothesizing even more wildly here. Sorry.)

There is a somewhat frustrating post by [Gruff Davies][Davies] which nevertheless contains the seed of a possible solution. I have several problems with Davies' take. He argues that "Newton’s laws are deterministic, but they’re not complete", and asserts that "Smooth domes are just as badly behaved". As I've made clear by now, I am with Malament here: smooth domes are well-behaved, and Newton's Laws are both deterministic and complete in those cases. (It appears that Davies has fallen victim to the flawed appeal to time-reversal, as described above.)

While I might differ from Davies in the continuous case, in the non-continuous case I agree that, if we want determinism then we need to complete, i.e. add to, Newton's Laws. And I am intrigued by the proposal he makes to accomplish this, which is to look at the higher derivatives. In Norton's non-trivial solutions, the acceleration at the moment the object spontaneous starts its slide is zero (as it must be by the second law, since there is no net force), and so is the third derivative of the position with respect to time (aka the _jerk_)... but the fourth derivative (the _snap_ or _jounce_) jumps from zero a constant finite value at that moment, and the fifth derivative (the _crackle_) therefore diverges. Perhaps we add a law which disallows such solutions? (I am not even attempting a formal statement of such a law here. We have to be careful. Our traditional approach to Newtonian mechanics accepts a divergent acceleration when a particle bounces off a perfectly hard surface. While it feels like we should be able to distinguish between that kind of situation and the kinds of situation we're dealing with here, the exact wording isn't obvious to me.)

I believe that such a law would restore determinism to Newtonian mechanics in the case of non-continuous boundary conditions. Again, I have no proof.

But now we return to the quesiton of whether, just because we might be able to add such a law, is it reasonable to do so? Isn't it maybe perverse to demand continuity in our solutions when we don't have it in our boundary conditions? Shouldn't we maybe learn to live with counter-intuitive answers to counter-intuitive questions?

I'll close by noting that this proposed new "law" is nonsense as a physics theory. We can't imagine any realistic experiment where it would change the results, and so it is unfalsifiable. As far as practical physics goes, Newtonian mechanics as traditionally formulated are unambiguous, complete, and deterministic... and only ever approximately correct.

[Norton]: https://sites.pitt.edu/~jdnorton/Goodies/Dome/index.html
[Malament]: https://philsci-archive.pitt.edu/3195/1/NortonDome.pdf
[Davies]: https://blog.gruffdavies.com/2017/12/24/newtonian-physics-is-deterministic-sorry-norton/
