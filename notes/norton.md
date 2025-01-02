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

[Norton]: https://sites.pitt.edu/~jdnorton/Goodies/Dome/index.html
[Malament]: https://philsci-archive.pitt.edu/3195/1/NortonDome.pdf
