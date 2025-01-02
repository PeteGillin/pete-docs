# Norton's Dome: some thoughts

## Introduction

Norton's Dome is a thought experiment proposed in 2003 by John D Norton, a philosopher of physics. It purports to show that Newtonian mechanics exhibit both non-determinism and non-causality. If you're not familiar with it, I recommend reading the write-up on [write-up on his site][Norton]. It's short and accessible.

This page contains my thoughts on the subject. I'll give my view on the claims, and on some of the other responses out there (though I'll only scratch the surface). And I'll share some ideas which I haven't seen elsewhere (though my research has been far from exhaustive).

I include almost no maths in here. So if you're looking for rigorous proofs, you're going to be disappointed, sorry.

## Continuity saves the day

The most important point to make is that the class of non-trivial solutions to the equations of motion which Norton presents are only possible because his dome has a singularity at its apex. I believe that the fundamental existence and uniqueness theorem for ordinary differential equations guarantees that Newtonian mechanics will be deterministic when the boundary conditions are continuous. I recommend reading [David B Malament][Malament] for more on that.

I also believe that this restores causality. This follows because, if one solution involving spontaneous movement is possible then a whole class of such solutions must be — there is, at least, a degree of freedom in when the movement happens; and in this case there is also a degree of freedom in the direction of the movement — and that would violate uniqueness.

I would argue that, from a practical physics point of view, we lose none of the utility of Newtonian mechanics by restricting its use to situations with continuous boundary condititions. We already know that it is an approximation to reality, and specifically that it does not apply at subatomic scales where quantum effects become important. So, to use Newtonian mechanics, we are replacing real surfaces made out of atoms with idealized ones, and we can just as easily choose a continuous one as a discontinous one.

This doesn't mean that it is a dumb question to ask whether Newtonian mechanics really does exhibit the surprising properties that Norton claims. It just means that it is of theoretical interest only.

## On time reversal

The 'time-reversal trick' that Norton describes gets a lot of attention in the commentary, and rightly so since it provides an intuitive way to make his non-trivial solutions seem less surprising. However, there is an important caveat which Norton himself highlights but which many casual readers seem to miss, so I'm going to reiterate it here. This will be important later on.

The gotcha is that the 'time-reversal trick' appears to apply to _any_ dome. We just need to launch the particle up the slope with the right velocity and it will come to rest at the apex. (That velocity is √( 2 _g_ _h_ ) where _g_ is the gravitational field strenght and _h_ the vertical distance we're starting below the apex. I mention this not because the formula is important, but to show that it can be easily deduced from the conservation of energy in a way that is indepenedent of the shape of the dome.) And yet many domes do not have anything like Norton's non-trivial solutions — in particular, continuous ones do not. So there must be something more to this time-reversal gag than meets the eye.

Here's the way out of that hole: While conservation of energy tells us that, for the correct starting velocity, a state where the particle is at rest at the apex of the dome is possible, it does not fully provide the dynamics of how it will reach that equilibrium state (although it does tell us that the particle must slow down as it climbs). If we run the equations of motion on, say, the surface of a hemispherical dome, we find that the particle asymptotically approaches the apex, but it does not reach it in any finite time. When we reverse the direction of time, we therefore see that if the particle starts at rest on the apex of a hemispherical dome it will never move away from it (by any finite distance) in any finite time.

(To reiterate for clarity: All the above is discussed by Norton.)

I don't have a direct proof, but it seems clear from chaining together the lines of reasoning we've discussed that the same asymptotic behaviour will be seen on any continuous dome, and that it is the singularity at the apex of Norton's dome which allows that particle to come to rest at the apex in finite time.

## The case of the cone

There is a related thought experiment which I find interesting, where we replace Norton's dome with a cone. Away from the apex, the equations of motion are high-school level physics, much simpler than Norton's are. We clearly see that there are partial solutions akin to the bottom branch of Norton's non-trivial solutions, i.e. where from a time _T_ onwards the particle is moving down from the apex with increasing speed. Or, to employ the time-reversal trick, we see that we can certainly slide the particle up the cone with the correct velocity to make it come to rest at the apex, and that it will do so in finite time.

Things get trickier when we try to figure out what happens for a particle which starts at rest on the apex — or one which we slide up the slope and which comes to rest there. Does it stay there? If not, when does it start moving, and in which direction? The equations of motion depend on the slope, and the slope is not well-defined at the apex. So it rather seems as though Newtonian mechanics can't answer these questions. (Again, this is not a problem in practice, since we cannot construct a perfectly pointy cone out of atoms.)

So we have a system much simpler than Norton's where a discontinuity in the boundary conditions causes problems for Newtonian mechanics. There is an important difference , which is that the slope at the apex of Norton's dome _is_ well-definined — it's zero — and so on the dome we can write down and find solutions to the equations of motion. I find that considering the case of the cone makes it less surprising that introducing a different kind of singularity that exists on the dome is still able to cause problems.

## So, _are_ Newtonian mechanics with discontinous boundary conditions deterministic?

I have argued that this question is only of theoretical interest. But I think it _is_ of interest, so let's pursue it a bit further. Norton argues that the answer is 'no'. Some commentators argue, with varying degrees of success, that the answer is 'yes'. Some commentators even seem to argue that the very ideas of non-determinism and non-causality are unphysical, and thus that we can _a priori_ discard such solutions. Spoiler alert: my answer is 'it depends'.

## Newton's first law

One potential line of defence for determinism lies in Newton's first law. There's a passage in Norton's text which leapt out at me on first reading:

> It is natural to visualize "uniform motion in a straight line" over some time interval, but we will need to apply the law at an instant.

He goes on to reformulate the first law accordingly (in such a way that it is just a special case of the second law for _F_ = 0). My immediate reaction is to ask: _why_ do we need to apply the law in this way? One plausible answer is that we need to do so in order to permit the non-trivial solutions. But then we would be in real danger of circular reasoning: we'd have shown that Newtonian mechanics are non-deterministic only when we reformulate one of the laws in a way specifically chosen to allow non-determinism. Perhaps Norton has another, more principled, reason for choosing this restricted application of the first law: if he does, he doesn't give it in this work.

This suggests an alternative analysis: we could apply the first law in the stronger form implied by its normal wording. In the case of Norton's dome, this is enough to eliminate the whole class of non-trivial solutions, and therefore restore determinism and causality.

It is tempting, **but, I believe, unjustified**, to give an answer to the question of determinism along these lines: "It depends. With the narrow, point-in-time version of the first law, Newtonian mechanics are non-deterministic. With the broader version, they are deterministic." Norton has demonstrated the truth of the first half of that claim. But I don't think we can state the second half with confidence. We've shown that the broader version of the first law restores determinism _in this case_, but we haven't shown it in general. And we can't appeal to the uniqueness theorem. So more thought is needed here.

(Aside: Somewhere along this journey, I found myself thinking: If there is really an ambiguity about what Newton's first law means, wouldn't there have been enough of a fuss about that in the last three-hundred-and-some years that I'd have heard about it? I think the resolution of that connundrum is that the two versions are equivalent in the continuous case, and so the difference only emerges when you engineer a situation like this one.)

## Sliding a particle around the inside of a bowl

I propose another thought experiment. This time, instead of sliding a particle on the outside of a dome, we're going to slide it around the inside of a bowl. (Let's consider a bowl to be any surface which is concave when viewed from above and rotationally symmetric about the vertical axis.)

(If I were a better person, I'd include diagrams here. I'm not. Sorry.)

There is (at least for some bowl shapes) a class of solutions to the equations of motion here which consist of the particle orbiting the vertical axis at constant height. We just need to ensure that the vertical component of the normal force cancels out gravity and that the radial component of the normal force is exactly the centripetal force needed to maintain circular motion. The starting condition needed to achieve such an orbit is that the particle is moving tangentially to the bowl surface, with no vertical component to its velocity, and with the 'correct' speed. That speed is a function of the radius of the orbit (or, equivalently its height, since there is a 1:1 relationship between those things), the gradient of the bowl at that radius, and the gravitational field strength. Start the particle 'too fast' and it will slide up the bowl, and slow down as it does so; start it 'too slow' and it will slide down the bowl and speed up.

Let us now consider the starting point where we start the particle 'too fast' for a constant-height orbit, but also angled up the slope of the bowl. It will slide up the surface of the bowl as it orbits, and slow down. We can choose the initial speed, the initial angle, the initial radius/height, and the shape of the bowl. With a careful choice, we can ensure that, at exactly the height where the vertical component of the velocity drops to zero, the tangential component is that required for a constant-height orbit. The maths to make that choice is not hard, at least in principle: we just apply the conservation of energy — as we did when sliding particles up domes — alongside the conservation of angular momentum, and the appropriate geometry. So it looks like we have a solution where we start out with the particle moving both up and around the slope, and we end up with it transitioning into a constant-height orbit.

Of course, as with the dome experiment, the conservation principles don't give us the full dynamics, and in particular don't tell us whether it will achieve that constant-height orbit in finite time, or just asymptotically approach it.

Again, as with the dome experiement, this question is important when apply the time-reversal trick. If we have a solution where the particle transitions into a constant-height orbit, having not been in such an orbit earlier, with a finite elapsed time, then reversing time gives us a solution where the particle starts in a constant-height orbit and then, seemingly spontaneously, transitions out of it. In fact, it gives us a whole class of such solutions. So, once again, we have non-determinism and non-caussality.

I don't have a direct proof, but I believe that it must therefore be the case that, if the shape of the bowl is continuous, the particle will only asymptotically approach the constant-height orbit (just as, on the dome, the particle only asymptotically approaches the apex). The chain of reasoning is, once again, analogous to that for the dome.

(I have sketched out maths and confirmed this to my satisfaction for one specific continuous bowl. The maths isn't fit to be published, so I'm not including it. Once again, sorry.)

So now we find ourselves asking whether we can arrange things such that the particle transitions into a constant-height orbit in a finite time, thus giving a class of non-causal solutions via time reversal and breaking determinism. I haven't had time to even attempt to construct such shape, but hypothesize that we can.

If we want to rescue determinism, we need to find a way to rule out that class of non-causal solutions. Unfortunately, I don't think that Newton's first law does the job for us here. That talks about particles subject to no net force; our particle, when in its constant-height orbit, is subject to a net force, precisely the centripetal force needed to keep it moving in a circle. And so the first law does not apply.

Instinctively, I find myself wanting to reach for some kind of generalization of the first law which would help. My gut says that, in its constant height orbit, the particle is 'at rest' in the vertical direction, and subject to no net force in the vertical direction, so it should remain at rest in the vertical direction. We have to accept, though, that this isn't what the first law actually says. And it isn't obvious to me exactly how you'd formulate a generalization of the first law that legislates for this gut feeling.

TODO: Write bit on [Gruff Davies][Davies]

TODO: Wrap things up

TODO: Proof

[Norton]: https://sites.pitt.edu/~jdnorton/Goodies/Dome/index.html
[Malament]: https://philsci-archive.pitt.edu/3195/1/NortonDome.pdf
[Davies]: https://blog.gruffdavies.com/2017/12/24/newtonian-physics-is-deterministic-sorry-norton/
