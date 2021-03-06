Effect of Defects
===========================

.. role:: highlit




.. index:: Defect

Defects
--------------------



.. image:: images/effectsofDefects.png
   :align: center


A chain might have defects where the site captures the walker with a rate C. We would have a master equation of this kind

.. math::
   \frac{d}{dt}P_m = F(P_{m+1}+P_{m-1}-2P_m) - C \delta_{m,r} P_m .


Consider an equation

.. math::
   \frac{d}{dt}y+\alpha y = f(t)

1. Solution to the equation when :math:`\alpha` is a constant is

   .. math::
      y(t)  = e^{-\alpha t} y(0) + \int_0^t dt' e^{-\alpha (t - t')} f(t')

2. :math:`\alpha` can be time dependent, instead of the exponential term, we have :math:`e^{-\int_{t'}^t ds \alpha(s)}` as the Green function.



.. warning::
   Review Green function and Laplace transform.

   General solution to first order differential equation is

   .. math::
      y(t) = G(t,t_0) y(t_0) + \int_{t_0}^{t} df' G(t,t') f(t')

   If :math:`\alpha` is constant, use Laplace transform. Otherwise use Green function.



.. hint::
   Suppose we have a first order inhomogeneous differential equation with homogeous initial condition

   .. math::
      L[y]\equiv \dot y + \alpha(t)y = f(t), \qquad \text{for } a < t, \qquad y(a) = 0

   The solution to this ODE is

   .. math::
      y = \int_a^\infty G(t\vert \xi)f (\xi) d\xi,

   in which Green function is defined as

   .. math::
      L[G(t\vert \xi)] = \delta(t - \xi), \qquad \text{for } a < t, \qquad G(a\vert \xi) = 0.

   In this specific case, Green function is

   .. math::
      G(x\vert \xi) = e^{-\int_\xi^x \alpha(t) dt} H(t - \xi) .


.. hint::
   As a comparison to Green function method (which is not very helpful in 1st order ODE), general solution to first order differential equation

   .. math::
      \dot y + \alpha(t)y = f(t)

   is

   .. math::
      y(t) = \frac{\int\mu(t) f(t) dt + C}{\mu(t)}


   where :math:`\mu(t) := e^{\int \alpha(t') dt'}`.


.. hint::
   Green function method for second order inhomogeneous equation is `here in vacabulary <../vocabulary/green.html>`_.


.. hint::
   Laplace transform is a transform of a function :math:`f(t)` to a function of :math:`s`,

   .. math::
      L[f(t)] = \int_0^\infty f(t) e^{ - s t} dt .

   Some useful properties:

   1. :math:`L[\frac{d}{dt}f(t)] = s L[f(t)] - f(0)`;
   2. :math:`L[\frac{d^2}{dt^2}f(t) = s^2 L[f(t)] - s f(0) - \frac{d f(0)}{dt}`;
   3. :math:`L[\int_0^t g(\tau) d\tau ] = \frac{L[f(t)]}{s}`;
   4. :math:`L[\alpha t] = \frac{1}{\alpha} L[s/\alpha]`;
   5. :math:`L[e^{at}f(t)] = L[f(s-a)]`;
   6. :math:`L[tf(t)] = - \frac{d}{ds} L[f(t)]`.



   Some useful results:

   1. :math:`L[1] = \frac{1}{s}`;
   2. :math:`L[\delta] = 1`;
   3. :math:`L[\delta^k] = s^k`;
   4. :math:`L[t] = \frac{1}{s^2}`;
   5. :math:`L[e^{at}]= \frac{1}[s-a]`.

Suppose we have a time dependent source for master equation,

.. math::
   \frac{d}{dt}P_m = F(P_{m+1} + P_{m-1} - 2P_m) + g_m(t)

The solution to this equation is

.. math::
   P_m(t) = \eta_m(t) + \int_0^t dt'\sum_n \Pi_{m-n}(t-t') g(t')

Fourier transform of this solution

.. math::
   P^k(t) = \eta^k(t) + \int_0^t dt' \Pi^k(t-t') g^k(t')

Then Laplace transform

.. math::
   \tilde P^k  = \tilde \eta^k + \tilde \Pi^k \tilde g^k  .

.. warning::
   :highlit:`Laplace transform`





Then we have in position space

.. math::
   \tilde P_m(\epsilon) = \tilde \eta_m(\epsilon)  + \sum_n \tilde \Pi_{m-n}(\epsilon) \tilde g_n(\epsilon)


Now get back to our problem at the beginning.

.. math::
   \tilde g_n = - C\delta _{n,r} \tilde P_n

The solution becomes

.. math::
   \tilde P_m = \tilde \eta _m - C \tilde \Pi_{m-r} \tilde P_r .


We haven't solved it. The RHS depends on the probabillity. Notice that if we choose m=r, then

.. math::
   \tilde P_r  = \tilde \eta_r - C\tilde \Pi_0 \tilde P_r .



So we can write down the rth component,

.. math::
   \tilde P_r = \frac{\tilde \eta_r}{1+C\tilde \Pi_0}  .

Solution to the probability is

.. math::
   \tilde P_m &= \eta_m - C\tilde \Pi_{m-r}  \frac{\tilde \eta_r}{1+C\tilde \Pi_0} \\
   & = \eta_m - \frac{\tilde \Pi_{m-r} \eta_r}{1/C + \tilde \Pi_0}


The properties of this solution

1. :math:`C\gg 1`, :math:`\tilde \eta_m - \frac{\tilde \Pi_{m-r} \tilde \eta_r}{\tilde \Pi_0}`.
2. :math:`C\ll 1`, :math:`\tilde \eta_m`.



.. warning::
   We have to inverse using computer but why bother these transforms?


Survival Probability
----------------------


.. math::
   Q(t) = \sum_n P_m(t)

In our example,

.. math::
   \tilde Q(t) = \sum_m \tilde P_m = \frac{1}{\epsilon}\left( 1 - \frac{\tilde \eta_r}{1/C + \tilde \Pi_0} \right)

Recall that Laplace transform gives us

.. math::
   \frac{d}{dt}Q \to \tilde Q - 1

The survival probability can be written as

.. math::
   \frac{d}{dt} = - \int_0^t M(t-t') \eta(t').





Review of Effect of Defect
-----------------------------


A brief review:

Equation:

.. math::
   \frac{d}{dt} P_m = \text{Without Defect} - C \delta_{m,r} P_m


Suppose we have the propagator as :math:`\Pi_{m-n}(t,t_0)`. Laplace transform to solve it

.. math::
   \tilde P_m(\epsilon) = \tilde \eta_m(\epsilon) - C\tilde \Pi_{m-r}(\epsilon) \tilde P_r(\epsilon)

By substitution of m with r, we find out

.. math::
   \tilde P_r(\epsilon) = \frac{\tilde \eta_m(\epsilon)}{1+ \tilde \Pi_0(\epsilon)}.

Insert this result back to the solution, we can write donw the final result.

.. math::
   \tilde P_m(\epsilon) = \tilde \eta_m(\epsilon) - C\tilde \Pi_{m-r}(\epsilon) \tilde \eta_r(t) \frac{1}{1+C\tilde \Pi(\epsilon)}.

Survival probability is defined as

.. math::
   Q(t) = \sum_m P_m .

Then we can find out its Laplace transform, which is

.. math::
   \tilde Q(t) = \frac{1}{\epsilon} \left[ 1 - \frac{\tilde \eta_r(\epsilon)}{1/C + \tilde \Pi_0} \right]

Looking through the table of Laplace transform, we know it's a transform of the time derivative of survival probability,

.. math::
   \frac{d}{dt}Q(t) = - \int_0^t dt' \mathscr M(t-t') \eta(t')

in which

.. math::
   \mathscr M(t-t') = \frac{1}{1/C + \tilde \Pi_0} .


.. hint::
   The Laplace transform of propagator is

   .. math::
      \tilde \Pi_0 = \int_0^\infty e^{-\epsilon t} \Pi_0 dt,

   which is actually decreasing when :math:`\Pi_0` is a constant.


Take the limits to check the properties.

1. Motion limit is given by

   .. math::
      \frac{1}{C} \ll \tilde \Pi_0 .

   The meaning of this is that the propagator decrease with time so fast that it becomes very small. In this limit, the survival probability is dominated by motion not the capture.

2. Capture limit,

   .. math::
      \frac{1}{C} \gg \tilde \Pi_0 .

   In this limit, the survival probability is dominated by capture rate.



.. hint::
   This part is excerpted from the vocabulary part.

   A very nice property of Laplace transform is

   .. math::
      L_s [e^{at}f(t)] &= \int_0^\infty e^{-st} e^{-at} f(t) dt \\
      & =  \int_0^\infty e^{-(s+a)t}f(t) dt \\
      & = L_{s+a}[f(t)]

   which is very useful when dealing with master equations.

   Two useful results are

   .. math::
      L[I_0(2Ft)] = \frac{1}{\sqrt{ \epsilon^2 - (2F)^2 }}

   and

   .. math::
      L[J_0[2Ft]]  = \frac{1}{\sqrt{\epsilon^2 + (2F)^2}},

   where :math:`I_0(2Ft)` is the modified Bessel functions of the first kind. :math:`J_0(2Ft)` is its companion.


   Using the property above, we can find out

   .. math::
      L[I_0(2Ft)e^{-2Ft}]  = \frac{1}{\sqrt{(\epsilon + 2F)^2 - (2F)^2}} .




Photosynthesis
------------------


.. figure:: images/chloroplast.png
   :alt: chloroplast
   :align: center

   Captions are `here on wikipedia <https://en.wikipedia.org/wiki/Photosynthesis#mediaviewer/File:Chloroplast.svg>`_. Chloroplast ultrastructure: 1. outer membrane 2. intermembrane space 3. inner membrane (1+2+3: envelope) 4. stroma (aqueous fluid) 5. thylakoid lumen (inside of thylakoid) 6. thylakoid membrane 7. granum (stack of thylakoids) 8. thylakoid (lamella) 9. starch 10. ribosome 11. plastidial DNA 12. plastoglobule (drop of lipids)


The obsorbed energy of photons is random walking in the chloroplast until it hit on a reaction center. Besides that, the photons can be emited after some time. So the process can be descibed with the following master equation.

.. math::
   \frac{d}{dt} P_m = \text{Without reaction and emission} - C\delta_{m,r} P_m - \frac{P_m}{\tau}

where the last term is the emission term.

What experimentalists interest is the quantity called :highlit:`quantum yield`, which is defined in the following way:

.. math::
   \text{quantum yield} & = \frac{\text{ Number of excitations in the trap or reaction center } }{\text{Number of total excitations}}\\
   & = \frac{\text{Integration of survival probability with the reaction center}}{\text{Integration of survival probability without the raction center}} .

We know that without the reaction,

.. math::
   \frac{d}{dt}Q + \frac{Q}{\tau} = 0

so

.. math::
   Q(t) = Q(0) e^{-t/\tau}.

Do the integration,

.. math::
   \frac{1}{\tau} \int_0^\infty Q(t) dt = 1 .

The quantum yield is

.. math::
   \text{quantum yield} = \frac{\frac{1}{\tau} \int_0^\infty dt Q(t) \vert_{\text{with traps}} }{\frac{1}{\tau} \int_0^\infty dt Q(t) \vert_{\text{without traps}} } .



The problem becomes the derivation of the two survival probabilities. However, we don't need the inverse Laplace transform because

.. math::
   \int_0^\infty Q(t) dt = L_{\epsilon=0}[Q(t)] .

Let's define the quantities without traps to be with a prime. Notice that if we define a new quantity

.. math::
   \bar P_m = e^{t/\tau} P_m'

because if we plugin it into the master equation, we will get back to the case without emission. Then we the solution immediately.

.. math::
   \bar P_m = P_m.

So the survival probability with traps is

.. math::
   Q' = e^{-t/\tau} Q.

This means that

.. math::
   \int_0^\infty Q'(t) dt &= \int_0^\infty e^{-t/\tau} Q(t) dt \\
   & = L_{\epsilon=1/\tau} [Q(t)].

This result simplifies our calculation so much because we don't need to calculate the survival probability in the case of traps. What we do is to use the Laplace transform of :math:`Q(t)` and set different :math:`\epsilon`.

In details,

.. math::
   \tilde Q(\epsilon) = \frac{1}{\epsilon} \left( 1- \frac{\tilde \eta}{1/C + 1/\sqrt{\epsilon(\epsilon +4F)}} \right).


So

.. math::
   \frac{1}{\tau}\int_0^\infty dt Q(t)  &= L_{\epsilon=0}[Q(t)] = \tilde Q(\epsilon=0) \\
   \frac{1}{\tau}\int_0^\infty dt Q'(t)  &= L_{\epsilon=1/\tau}[Q'(t)] = \tilde Q(\epsilon=\frac{1}{\tau}).

Then put :math:`\tilde \eta (\epsilon) = \tilde \Pi_{m-r}(\epsilon) P_m(0)` .



Multiple Defects
-------------------



We can solve for finite defects in principle. For example the two defects case should give us the following master equation

.. math::
   \frac{d}{dt}P_m = \cdots - C_r\delta_{m,r}P_m  - C_s \delta_{m,s} P_m.

By using the two special cases that :math:`m=r` and :math:`m=s`, we get two equations about :math:`\tilde P_r` and :math:`\tilde P_s`,

.. math::
   \tilde P_r &= \eta_r - C_r \tilde \Pi_0 \tilde P_r - C_s \tilde \Pi_{r-s} \tilde P_r \\
   \tilde P_s = \eta_s - C_r \tilde \Pi_{s-r} \tilde P_s - C_s \tilde \Pi_0 \tilde P_s.

However, the problem gets very complicated as the number of defects becomes very large.
