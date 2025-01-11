# Norton's Dome: some thoughts

## Introduction

Norton's Dome is a thought experiment proposed in 2003 by John D Norton, a philosopher of physics. It purports to show that Newtonian mechanics exhibit non-determinism. If you're not familiar with it, I recommend reading the write-up on [write-up on his site][Norton]. It's short and accessible.

This page contains my thoughts on the subject. I'll give my view on the claims, and on some of the other responses out there (though I'll only scratch the surface). And I'll share some ideas which I haven't seen elsewhere (though my research has been far from exhaustive).

I include almost no maths in here. So if you're looking for rigorous proofs, you're going to be disappointed. Sorry about that.

## Continuity saves the day

The most important point to make is that the class of non-trivial solutions to the equations of motion which Norton presents, where the particle sits at rest at the apex of the dome until some arbitrary moment when it starts sliding down the slope, are only possible because his dome has a singularity at its apex. I believe that the fundamental existence and uniqueness theorem for ordinary differential equations guarantees that Newtonian mechanics will be deterministic when the boundary conditions are sufficiently continuous. I recommend reading [David B Malament][Malament] for more on that. (I am being deliberately vague about what 'sufficiently continuous' means as I want to avoid getting bogged down in detail. Again, sorry about that, if it bothers you.)

I would argue that, from a practical physics point of view, we lose none of the utility of Newtonian mechanics by restricting its use to situations with continuous boundary condititions. If we look sufficiently closely, we find that matter is made out of electrons and nucleons and the like, and that the normal reaction is actually due to the electromagnetic interactions of those particles. The closest we could come to constructing Norton's dome would be to attempt to balance a single atom on the top of a dome made of atoms, and the forces that single atom would feel would be gravitational and electromagnetic — and they would be continous functions of position around the equilibrium point. Or, to look at it another way: idealized models involving pointlike particles and perfectly smooth and hard surfaces are only ever approximations, and we can choose surfaces without awkward singularities without making them any more approximate. (As it happens, we also know that quantum mechanics will become important at subatomic scales, although that's not central to this argument.)

## The case of the cone

There is a related thought experiment which I find interesting, where we replace Norton's dome with a cone.

Away from the apex, the equations of motion are high-school level physics. There are partial solutions akin to the bottom branch of Norton's non-trivial solutions: the distance from the apex at time _t_ is proportional to (_t_ - _T_)<sup>2</sup> for _t_ > _T_ and some arbitrary choice of _T_.

If we also had partial solutions akin to the top branch of Norton's non-trivial solutions, where the particle remains at rest at the apex for _t_ < _T_, then we would have shown non-determinism just like Norton does (and with significantly simpler maths). But we run into a problem here: The equations of motion of a point sliding on a slope depend on its gradient, and the gradient is not well-defined at the apex of a cone. So it rather seems as though we can't answer the question of what happens if we try to balance a particle there.

It's worth being clear about the exact nature of the problem here. There's nothing wrong with Newton's laws of motion: _F_ still equals _m_ _a_. It's the boundary conditions where we come unstuck. Specifically, our thought experiments involve a perfectly smooth and hard surface, which provide a normal force of exactly the magnitude required to prevent the particle penetrating it — but there is no well-defined normal at the apex of a cone. So the process by which we figure out what forces to put into our force diagram deosn't work.

(Some readers may want to argue that the force must be straight up, appealing to symmetry. I'm not sure how I feel about that. We can sidestep it by imagining a sheered cone which is asymmetric.)

There is an important difference between the cone and Norton's dome: The gradient at the apex of the dome _is_ well-definined — it's zero — and so we can write down and find solutions to the equations of motion. The novel point we learn from Norton is that a gradient which is well-defined but whose rate of change diverges is enough to cause us problems with determinism.

## On time reversal

There's one other point I want to make before getting onto the main question.

The 'time-reversal trick' that Norton describes gets a lot of attention in the commentary, and rightly so since it provides an intuitive way to make his non-trivial solutions seem less surprising. However, there is an important caveat which Norton himself highlights but which many casual readers seem to miss, so I'm going to reiterate it here. This will be important later on.

The thing is, the 'time-reversal trick' appears to apply to _any_ dome. We just need to launch the particle up the slope with the right velocity and it will come to rest at the apex. (That velocity is √( 2 _g_ _h_ ) where _g_ is the gravitational field strenght and _h_ the vertical distance we're starting below the apex. I mention this not because the formula is important, but to show that it can be easily deduced from the conservation of energy in a way that is indepenedent of the shape of the dome.) And yet many domes do not have anything like Norton's non-trivial solutions — in particular, sufficiently continuous ones do not. So there must be something more to this time-reversal business than meets the eye.

And here's what that something is: While conservation of energy tells us that, for the correct starting velocity, a state where the particle is at rest at the apex of the dome is possible, it does not fully provide the dynamics of how it will reach that equilibrium state. (It does tell us that the particle must slow down as it climbs.) If we run the equations of motion on, say, the surface of a hemispherical dome, we find that the particle asymptotically approaches the apex, but it does not reach it in any finite time. When we reverse the direction of time, we therefore see that if the particle starts at rest on the apex of a hemispherical dome it will never move away from it (by any finite distance) in any finite time.

I don't have a direct proof, but it seems clear from chaining together the lines of reasoning we've discussed that the same asymptotic behaviour will be seen on any sufficiently continuous dome, and that it is the singularity at the apex of Norton's dome which allows that particle to come to rest at the apex in finite time.

For what it's worth, I find myself just about able to intuitively understand why this might be. On a continuous dome, the gradient must fall towards zero as we approach the apex. Therefore, the force decelerating a particle also falls towards zero as we approach the apex. Therefore, if the particle is to come to a halt at the apex, it must be moving slowly when the gradient is small. We can see how an asymptotic slow-down can happen. The cone avoids this because the gradient is constant as we approach the apex, and the constant deceleration this provides is able to slow and stop the particle in finite time. Seemingly, the dome also avoids it, because the gradient drops sharply to zero (specifically, its rate of change diverges) and so it is able to provide "enough" deceleration to slow and stop the particle in finite time whilst still flattening out at the apex. (Not convinced? Never mind: Your intuition may vary. The maths still works.)

## So, _are_ Newtonian mechanics deterministic if we _don't_ require continuity?

I have argued that restricting, for practical purposes, it is fine to restrict ourselves to continuous cases, where determinism is secure. That doesn't stop us whether Newton is deterministic if we drop that restriction. Norton argues that the answer is 'no'. Some commentators argue, with varying degrees of success, that the answer is 'yes'. Some commentators even seem to argue that the very idea of non-determinism is unphysical, and thus that we can _a priori_ discard such solutions. Malament argues that the answer is 'it depends', and I am inclined to agree. The rest of this note will unpack this further.

(Another option is to reject the question as meaningless. In the case of the cone, where we cannot even confidently say what forces apply to the particle on the apex, there is some force to this argument. In the case of the dome, we have forces, and equations we can solve, and it seems that the question of determinism is a reasonable one, if only on the level of a thought experiment.)

## Newton's first law

One potential line of defence for determinism lies in Newton's first law. There's a passage in Norton's text which leapt out at me on first reading:

> It is natural to visualize "uniform motion in a straight line" over some time interval, but we will need to apply the law at an instant.

He goes on to reformulate the first law accordingly (in such a way that it is just a special case of the second law for _F_ = 0). My immediate reaction is to ask: _why_ do we "need" to apply the law in this way? One plausible answer is that we need to do so in order to permit the non-trivial solutions. But then we would be in real danger of circular reasoning: we'd have shown that Newtonian mechanics are non-deterministic only when we reformulate one of the laws in a way specifically chosen to allow non-determinism. Perhaps Norton has another, more principled, reason for choosing this restricted application of the first law: if he does, he doesn't give it in this work.

This suggests an alternative analysis: we could apply the first law in the stronger form implied by its normal wording. In the case of Norton's dome, this is enough to eliminate the whole class of non-trivial solutions, and therefore restore determinism.

It is tempting, **but, I believe, unjustified**, to give an answer to the question of determinism along these lines: "It depends. With the narrow, point-in-time version of the first law, Newtonian mechanics are non-deterministic. With the broader version, they are deterministic." Norton has demonstrated the truth of the first half of that claim. But I don't think we can state the second half with confidence. We've shown that the broader version of the first law restores determinism _in this case_, but we haven't shown it in general. And we can't appeal to the uniqueness theorem. So more thought is needed here.

(Aside: Somewhere along this journey, I found myself thinking: If there is really an ambiguity about what Newton's first law means, wouldn't there have been enough of a fuss about that in the last three-hundred-and-some years that I'd have heard about it? I think the resolution of that connundrum is that the two versions are equivalent in the continuous case, and so the difference only emerges when you engineer a situation like this one.)

## Sliding a particle around the inside of a bowl

I propose another thought experiment. This time, instead of sliding a particle on the outside of a dome, we're going to slide it on the inside of a bowl. (Let's consider a bowl to be any surface which is concave when viewed from above and rotationally symmetric about the vertical axis.) And instead of restricting ourselves to radial motion, we're going to allow circular motion as well.

(If I were a better person, I'd include diagrams here. I'm not. Sorry.)

(It may help to consider that this is analogous to a particle in a plane orbiting a central mass with a gravitational field whose strength is some function of distance, that function being determined by the shape of the bowl.)

There is (at least for some bowl shapes) a class of solutions to the equations of motion here which consist of the particle orbiting the vertical axis at constant radius (which also means constant height). We just need to ensure that the vertical component of the normal force cancels out gravity and that the component of the normal force towards the axis is exactly the centripetal force needed to maintain circular motion. The starting condition needed to achieve such an orbit is that the particle is moving tangentially to the bowl surface, with no radial component to its velocity, and with the 'correct' speed. That speed is a function of the radius of the orbit, the gradient of the bowl at that radius, and the gravitational field strength. Start the particle 'too fast' and it will slide up the bowl, and slow down as it does so; start it 'too slow' and it will slide down the bowl and speed up.

Let us now consider the starting point where we start the particle 'too fast' for a constant-radius orbit, but also angled up the slope of the bowl. It will slide up the surface of the bowl as it orbits, and slow down. With a careful choice of the initial speed and angle, we may be able to ensure ensure that, at exactly the point where the radial component of the velocity drops to zero, the circular component is that required for a constant-radius orbit. The maths to make that choice is not hard, at least in principle: we just apply the conservation of energy (as we did when sliding particles up domes) alongside the conservation of angular momentum, and the appropriate geometry. So it looks like we have a solution where we start out with the particle moving both up and around the slope, and we end up with it transitioning into a constant-radius orbit.

Of course, as with the dome, the conservation principles don't give us the full dynamics, and in particular don't tell us whether it will achieve that constant-radius orbit in finite time, or just asymptotically approach it. If we have a solution where the particle transitions into a constant-radius orbit, having not been in such an orbit earlier, with a finite elapsed time, then reversing time gives us a solution where the particle starts in a constant-radius orbit and then, seemingly spontaneously, drops out of it. In fact, it gives us a whole class of such solutions. So, once again, we have non-determinism.

I don't have a direct proof, but I believe that it must be the case that, if the shape of the bowl is sufficiently continuous, the particle will only asymptotically approach the constant-radius orbit (just as, on the dome, the particle only asymptotically approaches the apex). The chain of reasoning is analogous to that for the dome.

(I have sketched out maths for one specific continuous bowl and confirmed to my satisfaction that this asymptotic approach occurs. The maths isn't fit to be published, so I'm not including it. Once again, sorry.)

So now we find ourselves asking whether, if we allow the bowl's gradient's rate of change to diverge, we can arrange things such that the particle transitions into a constant-radius orbit in a finite time. I haven't had time to even attempt to construct such shape, but hypothesize that we can.

Suppose that my hypothesis is correct, and so we have that class of spontaneously de-orbiting solutions, and we have non-determinism. My gut instinct is that this feels wrong, and I want to find a way to rule those solutions out. I'm don't think we should trust my gut here, since we are talking about unrealistic thought experiments here. But it is still interesting to speculate what it would take to rescue determinism.

Unfortunately, I don't think that Newton's first law does the job for us here, like it does for Norton's dome if we assume its broader form. That talks about particles subject to no net force; our particle, when in its constant-height orbit, is subject to a net force, precisely the centripetal force needed to keep it moving in a circle. And so the first law does not apply.

My first thought was to generalize the first law, so that it applies separately in each spatial dimension. We'd then be able to say that the particle in a constant-radius orbit is at rest _in the vertical dimension_ (i.e. that its velocity has no vertical component), and the vertical component of the net force is zero, and thus that it stays at rest in the vertical dimension. This handily eliminates the unwanted solutions. We have to accept that this would be a stronger statement than the first law as normally stated, but it would give us back our determinism in this case.

However, I'm not convinced that it would do so in all cases. I suspect that we might be able to constuct situations, either on a carefully selected bowl or perhaps on a bowl-like surface which lacks rotational symmetry, where we have stable orbits which do not have constant radius. (Think of the elliptical orbits in the case where the inward force follows an inverse square law, for example.) And I suspect that, if we allow the rate of change of the gradient to diverge, we might be able to construct classes of solution where the particle seems to spontaneous drop out of those orbits. In this case, this generalization of the first law does not apply either.

There is a somewhat frustrating post by [Gruff Davies][Davies] which nevertheless contains the seed of a possible solution. I have several problems with Davies' take, but the most important is that he dismisses the importance of continuity. He argues that "Newton’s laws are deterministic, but they’re not complete". I think that, if you have to choose between determinism and completeness, choosing determinism is a reasonable stance to take. But we should not lose sight of the fact that, for sufficiently continuous boundary conditions, Newtonian mechanics _are_ both deterministic and complete. I believe that Davies' assertion that "Smooth domes are just as badly behaved" is incorrect, and that his justification for this statement is based on the flawed understanding of the time-reversal trick described above.

However, while I may differ with Davies over the circumstances in which we need to strengthen Newton's laws to make them deterministic, I am intrigued by the proposal he makes to accomplish this, which is to look at the higher derivatives. I Norton's non-trivial solutions, the acceleration at _t_ = _T_ is zero (as it must be by the second law, since there is no net force), and so is the third derivative of the position with respect to time (aka the _jerk_)... but the fourth derivative (the _snap_ or _jounce_) jumps from zero for _t_ < _T_ to a constant finite value at _t_ > _T_, and the fifth derivative (the _crackle_) therefore diverges. Perhaps we add a law which disallows such solutions? (I am not even attempting a formal statement of such a law here. We have to be careful. Our traditional approach to Newtonian mechanics accepts a divergent acceleration when a particle bounces off a perfectly hard surface. While it feels like we should be able to distinguish between that kind of situation and the kinds of situation we're dealing with here, the precise formulation would need more attention to detail than I've got time for.)

I believe that such a law would imply the stronger form of Newton's first law, and would therefore restore determinism in all cases where the stronger first law does so, including on Norton's dome. I also believe that it would outlaw the class of solutions where the particle spontaneously de-orbits in the bowl examples, and so restore determinism there. I strongly suspect that it would be enough to guarantee determinism in all reasonable cases.

Let's be clear about what we're dealing with here. Such a proposed new law might be a way to extend Newton's three to ensure determinism even in the presence of singularities in the boundary condtions. It is, however, useless as a proposal for an actual law of physics. This is because we could never design a real experiment in which it gave a different result to regular Newtonian mechanics, and so it is unfalsifiable.

TODO: Wrap things up

TODO: Proof-read

[Norton]: https://sites.pitt.edu/~jdnorton/Goodies/Dome/index.html
[Malament]: https://philsci-archive.pitt.edu/3195/1/NortonDome.pdf
[Davies]: https://blog.gruffdavies.com/2017/12/24/newtonian-physics-is-deterministic-sorry-norton/
