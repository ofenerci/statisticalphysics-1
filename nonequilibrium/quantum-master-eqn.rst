Quantum Master Equation
=======================================================

.. role:: highlit

The game of quantum master equations is presented in this lecture notes.


Quantum Master Equation
------------------------

.. important::
   In quantum mechanics, probability is not complete. We need density matrix.

Quantum mechanics observables are averaging over all density matrix elements,

.. math::
   \langle O \rangle = \sum_{m,n} O_{nm}\rho_{mn}.

For diagonalized density matrix, this averaging becomes the ordinary probability averaging.

However, even if we start with a diagonalized density matrix, the averaging procedure won't stay on the classical averaging procedure as time goes on. Off diagonal elements can be created out of the diagonal elements.

In that sense, it's not even possible to use the classical master equation to solve most quantum problems. We need the quantum master equation.

The first principle of quantum mechanics is

.. math::
   i\hbar \frac{d}{dt}\hat \rho = [\hat H,\hat \rho] = \hat L \hat \rho.

Then the question is, as the first idea, how to derive an equation for the probability.


Pauli's Mistake
~~~~~~~~~~~~~~~~~


Pauli derived the first quantum master equation which is not quite right.

The solution to a quantum system is

.. math::
   \hat \rho(t) = e^{-iL(t-t_0)} \hat \rho(t_0) .


In Heisenberg picture,

.. math::
   \hat \rho(t+\tau) = e^{-i\tau \hat H} \hat \rho(t) e^{i\tau \hat H} .

The diagonal elements of density matrix are

.. math::
   \rho_{mm}(t+\tau) = \bra{m}e^{-i\tau \hat H} \hat \rho(t) e^{i\tau \hat H} \ket{m}.


The left hand side is the probability, :math:`P_m`. Right had side becomes

.. math::
   \text{RHS} = \sum_{n,l}\bra{m}e^{-i\tau \hat H} \ket{n} \bra{n}\hat \rho(t) \ket{l}\bra{l} e^{i\tau \hat H} \ket{m}.


Here is where Pauli's idea comes in. He assumed that the system is dirty enought to have repeatedly recurance of diagonalized density matrix. Then he use diagonalized density matrix to calculate the probability,

.. math::
   P_m(t+\tau) &= \sum_{n}\bra{m}e^{-i\tau \hat H} \ket{n} \bra{n}\hat \rho(t) \ket{n}\bra{n} e^{i\tau \hat H} \ket{m} \\
   & = \sum_{n} P_n \left\vert \bra{m} e^{-i\tau \hat H} \ket{n}  \right\vert^2 .

The term :math:`\left\vert \bra{m} e^{-i\tau \hat H} \ket{n}  \right\vert^2` RHS is the probability of a state n to be at state m after a short time :math:`\tau`. We'll define this as :math:`Q_{mn}(\tau)`.

So in short the probability is

.. math::
   P_m(t+\tau) = \sum_n Q_{mn}(\tau)P_n(t).

Then we can repeat the Chapman method to derive a master eqution.


.. important::
   However, the Pauli assumption is basically the Fermi golden rule which requires a infinite amount of time. This is obviously not valid for an master equation system.


Then it comes the van Hove derivation.


van Hove's Derivation
~~~~~~~~~~~~~~~~~~~~~~~


van Hove argued that Pauli's result is nonsense. He started with

.. math::
   P_m(t+\tau) &= \sum_n Q_{mn}(\tau) P_n(t) \\
   P_m(t-\tau) & = \sum_n Q_{mn}(-\tau) P_m(t) .


The key point is that :math:`Q_{mn}(\tau) = Q_{mn}(-\tau)`,

.. math::
   Q_{mn}(\tau) & = \left\vert \bra{m} e^{-i\tau \hat H} \ket{n}  \right\vert^2 \\
   & = \left\vert \bra{m} e^{i\tau \hat H} \ket{n}  \right\vert^2 \\
   & = Q_{mn}(-\tau) .

Without any calculations, we just know imediately that

.. math::
   P_m(t+\tau) = P_m(t-\tau) ,

in other words, there's no evolution of probability density.

van Hove
---------------------------------------------------


.. important::
   van Hove made a great progress by bringing up the following questions.

   1. What systems can be described by master equations?
   2. What's the time scale for quantum master equation to be valid?
   3. How to derive a quantum master equation?


Suppose we have a quantum system with Hamiltonian,

.. math::
   \hat H = \hat H_0 + \lambda(t)\hat W .

van Hove's idea was that quantum master equations can describe systems with diagonal singularity conditions.


Then he said, the time scale of the system should be long enough, the perturbation should be as small as the condition :math:`\lambda^2 t \approx \text{constant}`.

.. warning::
   This looks weird to me because I can not see why this is good for an approximation.


So we can write down the diagonal elements

.. math::
   P_m & = \bra{m}\hat \rho \ket{m} \\
   & = \sum_{m,n} \bra{m} e^{i\hat H t/\hbar} \ket{n}\bra{n} \hat \rho(0) \ket{l}\bra{l} e^{-iHt/\hbar} \ket{m} \\
   & = \sum_{m,n} \left\vert \bra{m} e^{i (\hat H_0 + \lambda \hat W) t/\hbar } \ket{n} \right\vert^2 \rho_{nl}(0) .

van Hove applied random phase condition for only initial condition, :math:`\rho_{nl}(0)` is diagonalized at initial :math:`t=0`.

Then we have

.. math::
   \rho_{nl} (0) = \rho_{nn} \delta_{nl} = P_n(0) \delta_{nl} .

Put this result back to the probability,

.. math::
   P_m = \sum_n \left\vert \bra{m} e^{i (\hat H_0 + \lambda \hat W) t/\hbar } \ket{n} \right\vert^2 P_n(0) .


Then use the whole Dyson series then selectively make some terms zero and use the assumptions to derive a master equation.




Zwawzig and Nakajiwa
---------------------


They invented the projection technique.

First of all define a diagonalizing operator :math:`\hat D` which just keeps the diagonal elements and simply drops the off diagonal elements. We see that :math:`1-\hat D` will element all diagonal elements.

We can define the diagonalized density matrix as :math:`\hat \rho_d = \hat D \hat \rho` and off-diagonalized density matrix as :math:`\hat \rho_{od} = (1-\hat D)\hat \rho`. As an application,

.. math::
   \hat \rho = \hat \rho_d + \hat \rho_{od} .

Starting from the von Neumann equation,

.. math::
   i\hbar \partial_t \hat \rho = \left[\hat H, \hat \rho \right] .

By using the Liouville operator,

.. math::
   \partial_t \hat \rho = -i \hat L \hat \rho .

Apply :math:`\hat D` and :math:`1-\hat D` to the von Neumann equation,

.. math::
   \partial_t \hat \rho_d & = -i \hat D  \hat L \hat \rho \\
   \partial_t \hat \rho _{od} & = -i (1 - \hat D)  \hat L \hat \rho .

Use the relation that :math:`\hat \rho = \hat \rho_d + \hat \rho_{od}`, we have

.. math::
   \partial_t \hat \rho_d & = -i \hat D  \hat L \hat \rho_d - i \hat D  \hat L \hat \rho _ {od} \\
   \partial_t \hat \rho _{od} & = - i (1 - \hat D)  \hat L \hat \rho _ d - i (1 - \hat D)  \hat L \hat \rho_{od}  .

Solve the second equation using Green function technique,

.. math::
   \hat \rho_{od} = e^{-i(1-\hat D)\hat L t} + \int_0^t dt' e^{-i(1-\hat D) \hat L (t-t')}(-i(1-\hat D)\hat L \hat \rho_d(t')) .

.. hint::
   Recall that the solution for

   .. math::
      \dot y + \alpha y = f

   is

   .. math::
      y = e^{-\alpha t} y(0) + \int_0^t dt' e^{-\alpha (t-t')} f(t') .


Insert this solution to the equation of :math:`\hat \rho_d`,

.. math::
   {\color{red}\partial_t \hat \rho_d = - i\hat D\hat L \hat \rho_d -  \hat D\hat L \int_0^t dt' e^{-i(1-\hat D) \hat L (t-t')}(1-\hat D)\hat L \hat \rho_d(t')} {\color{blue} - i \hat D \hat L e^{-i(1-\hat D)\hat L t} \rho_{od}(0) }.

What happened to the blue term? It disapears when we apply the initial random phase condition.

When it happens we get our closed master equation for :math:`\hat \rho_d`, which is an equation for the probability.



About Off-diagonal Elements
-----------------------------

Though we need to set :math:`\rho_{od}(0)=0` to have a closed master equation, that doens't mean we have to make only localized initial condition on only one state.

    "We can always use phasers."

    -- V. M. Kenkre


Suppose we have a system with five possible states, the off-diagonal elements don't exist initially if the system is in only one state.

.. image:: images/quantum1state.png
   :align: center

The density matrix will contain off-diagonal elements if we have two states initially.

.. image:: images/quantum2states.png
   :align: center

However, we can always choose a combination of the states to use as the basis, so that the density matrix becomes diagonalized.



Simplify Quantum Master Equation
-----------------------------------

We derived some sort of quantum master equation using projection method. Here we will simplify it.


Let's stare at the results for a minute.

.. math::
   {\color{red}\partial_t \hat \rho_d = - i\hat D\hat L \hat \rho_d -  \hat D\hat L \int_0^t dt' e^{-i(1-\hat D) \hat L (t-t')}(1-\hat D)\hat L \hat \rho_d(t')} {\color{blue} - i \hat D \hat L e^{-i(1-\hat D)\hat L t} \rho_{od}(0) }.

By definition, :math:`\rho_d=\hat D\rho`. So what is :math:`\hat D \hat L \rho_d`?

.. math::
   \hat D \hat L \rho_d & = \hat D\hat L \hat D \hat \rho \\
   & = \hat D \left[ {\color{magenta}  \begin{pmatrix}\rho_{11} & 0 & 0 & \cdots \\ 0 & \rho_{22} & 0 & \cdots \\ 0 & 0 & \rho_{33} & \cdots  \\ \vdots & \vdots & \vdots &  \ddots  \end{pmatrix} \begin{pmatrix} H_{11} & H_{12} & H_{13} & \cdots \\ H_{21} & H_{22} & H_{23} & \cdots  \\ H_{31} & H_{32} & H_{33} & \cdots \\ \vdots & \vdots \vdots & & \ddots \end{pmatrix}    } -  {\color{green} \begin{pmatrix} H_{11} & H_{12} & H_{13} & \cdots \\ H_{21} & H_{22} & H_{23} & \cdots  \\ H_{31} & H_{32} & H_{33} & \cdots \\ \vdots & \vdots \vdots & & \ddots   \end{pmatrix} \begin{pmatrix} \rho_{11} & 0 & 0 & \cdots \\ 0 & \rho_{22} & 0 & \cdots \\  0 & 0 & \rho_{33} & \cdots \\ \vdots & \vdots & \ddots & \cdots \end{pmatrix} } \right]


We can easily see that the diagonal elements are equal for the two terms (magenta and green) in the braket so all the diagonal elements go away. Now when the :math:`\hat D` outside of the bracket applied, the whole term is zero.

We are so lucky to eliminate the term :math:`-i\hat D\hat L\hat \rho_d`.

We do perturbation theory most of the time. Consider the case that Hamiltonian of the system is :math:`\hat H = \hat H_0 + \lambda \hat W`. We can split the Liouville operator into two parts, :math:`\hat L = \hat L_0 + \lambda \hat L_W `.

Our master equation becomes

.. math::
   \partial_t \hat \rho_d & =  -  \int_0^t dt' \hat D (\hat L_0 + \lambda \hat L_W ) e^{-i(1-\hat D) (\hat L_0 + \lambda \hat L_W  )(t-t')}(1-\hat D)\hat L \hat \rho_d \\
   & =  -  \int_0^t dt' \hat D (\hat L_0 + \lambda \hat L_W ) e^{-i(1-\hat D)  (\hat L_0 + \lambda \hat L_W ) (t-t')} (\hat L_0 + \lambda \hat L_W ) \hat \rho_d \\
   & =  -  \int_0^t dt' \mathscr K(t-t') \hat \rho_d .

in which :math:`- i \hat D \hat L e^{-i(1-\hat D)\hat L t} \rho_{od}(0) = 0` (initial condition), :math:`\hat D \hat L \rho_d = 0` (just proved).

We have the definition

.. math::
   \mathscr K(t-t') & = \hat D (\hat L_0 + \lambda \hat L_W ) e^{-i(1-\hat D)  (\hat L_0 + \lambda \hat L_W ) (t-t')} (\hat L_0 + \lambda \hat L_W ) .

In weak coupling interaction, :math:`\lambda \rightarrow 0`, we can put :math:`\lambda = 0` in the exponential.

.. math::
   \mathscr K(t-t')  &=  \hat D (\hat L_0 + \lambda \hat L_W ) e^{-i(1-\hat D)  (\hat L_0 + \lambda \hat L_W ) (t-t')} (\hat L_0 + \lambda \hat L_W )  \\
   &= \hat D (\hat L_0 + \lambda \hat L_W ) e^{-i(1-\hat D)  \hat L_0 (t-t')} (\hat L_0 + \lambda \hat L_W ) \\
   &= \hat D \hat L_0  e^{-i(1-\hat D)  \hat L_0 (t-t')} \hat L_0  + \lambda \hat D \hat L_0  e^{-i(1-\hat D)  \hat L_0 (t-t')}   \hat L_W   \\
   \phantom{\mathscr K(t-t')} & \phantom{{} = } + \lambda \hat D  \hat L_W  e^{-i(1-\hat D)  \hat L_0 (t-t')} \hat L_0  + \lambda^2 \hat D   \hat L_W  e^{-i(1-\hat D)  \hat L_0 (t-t')}  \hat L_W  \\
   &=  \lambda^2 \hat D   \hat L_W  e^{-i(1-\hat D)  \hat L_0 (t-t')}  \hat L_W  \\
   &=  \lambda^2 \hat D   \hat L_W  e^{-i\hat L_0 (t-t')}  \hat L_W  .


I dropped several terms even the first order of :math:`\lambda`. This has been done correctly because the interaction term can be very different from the zeroth order. [1]_

With a lot of terms being disappears, we can now start to look at the numbers which ia the density matrix elements sandwiched between states,

.. math::
   \bra{m} \partial_t \rho_d \ket{m} = -\lambda^2 \bra{m} \int_0^t dt' \hat L_W e^{-i(t-t')\hat L_0} \hat L_W \rho_d(t') \ket{m}.






.. hint::
   Here is an useful relation,

   .. math::
      e^{iA\hat L} \hat O & = \hat O + i A \hat L \hat O + \frac{(iA)^2}{2} \hat L \hat L \hat O + \cdots \\
      & = \hat O + iA[\hat H, \hat O] + \frac{(iA)^2}{2}  [\hat H, [\hat H,\hat O]] + \cdots \\
      & = e^{iA\hat H}\hat O e^{-iA\hat H}


Notice that :math:`\hat L_W \hat \rho_d = \frac{1}{\hbar}[W, \rho_d]`. Define :math:`\hat{\mathscr M} = e^{-i(t-t')\hat H_0}[\hat V,\hat \rho_d]e^{i(t-t')\hat H_0}`.


.. math::
   \bra{m} \partial_t \rho_d \ket{m} &= -\lambda^2 \bra{m} \int_0^t dt' [\hat W, e^{-i(t-t')\hat L_0}[\hat W, \rho_d(t')]] \ket{m}  \\
   & = -\lambda^2 \bra{m} \int_0^t [\hat W, ] dt' \ket{m}  \\
   & = -\lambda^2 \left( \bra{m} \int_0^t dt' \hat W\hat{\mathscr M} \ket{m} - \bra{m} \int_0^t \hat{\mathscr M}\hat W\ket{m} dt' \right) \\
   & = -\lambda^2 \int_0^t dt' \left( \bra{m} \hat W\hat{\mathscr M} \ket{m} - \bra{m} \hat{\mathscr M}\hat W\ket{m}  \right) \\
   & = -\lambda^2 \int_0^t dt' \sum_n (W_{mn}\mathscr M_{nm} - \mathscr M_{mn}W_{nm}).

We know that :math:`\rho_d = P_{m}`. So the master equation becomes

.. math::
   \partial_t P_m(t) = -\lambda^2 \int_0^t dt' \sum_n (W_{mn}\mathscr M_{nm} - \mathscr M_{mn}W_{nm}).


The eigen function of the system is

.. math::
   \hat H_0 \ket{m} = \epsilon_m \ket{m} .

With this result we can calculate the matrix elements,

.. math::
   \mathscr M_{mn} &= \bra{m} e^{-i(t-t')\hat H_0}[\hat W,\hat \rho_d]e^{i(t-t')\hat H_0} \ket{n} \\
   & = e^{-i(t-t')\epsilon_m} \bra{m} [\hat W, \hat \rho_d] \ket{n} e^{i(t-t')\epsilon_n} \\
   & = \sum_\mu e^{-i(t-t')\epsilon_m} (\bra{m} \hat W \ket{\mu} \bra{\mu} \hat \rho_d \ket{n} - \bra{m} \hat \rho_d \ket{\mu}\bra{\mu} \hat W \ket{n} )e^{i(t-t')\epsilon_n} \\
   & = \sum_\mu  e^{-i(t-t')\epsilon_m} (W_{m\mu}\rho_{\mu n} - \rho_{m\mu}W_{\mu n}) e^{i(t-t')\epsilon_n} \\
   & = e^{-i(t-t')\epsilon_m} ( W_{mn}P_{n} - P_{m}W_{m n} ) e^{i(t-t')\epsilon_n} .

Finally we have our quantum master equation,

.. math::
   \partial_t P_m &= -\lambda^2 \int_0^t dt' \sum_n \left[ ( W_{mn} e^{-i(t-t')\epsilon_n} ( W_{nm}P_{m} - P_{n}W_{n m} ) e^{i(t-t')\epsilon_m}) - (e^{-i(t-t')\epsilon_m} ( W_{mn}P_{n} - P_{m}W_{m n} ) e^{i(t-t')\epsilon_n} )W_{nm}  \right] \\
   & =  -\lambda^2 \int_0^t dt' \sum_n \left[ ( W_{mn} e^{-i(t-t')(\epsilon_n - \epsilon_m )  }  W_{nm} (P_{m} - P_{n}) - (e^{-i(t-t')\epsilon_m} ( W_{mn}P_{n} - P_{m}W_{m n} ) e^{i(t-t')\epsilon_n} )W_{nm}  \right] \\
   & = -2 \lambda^2 \int_0^t dt' \sum_n \left\vert W_{mn} \right\vert^2 \left[ P_n- P_m \right] \cos((\epsilon_m-\epsilon_n)(t-t'))

which is actually the :highlit:`Fermi's golden rule`.

Define :math:`\Omega_{mn}(t-t')=\Omega_{nm}(t-t') = 2\lambda^2 \left\vert W_{mn} \right\vert^2\cos((t-t')(\epsilon_m-\epsilon_n))`, we can write the master equation into a really simple form,

.. math::
   \partial_t P_m = \int_0^t dt' \sum_n \left( \Omega_{mn}(t-t') P_n - \Omega_{nm}(t-t') P_m \right).


Markovian - Kenkre Approach
------------------------------

We can simplify the equation more using Markovian approximation,

.. math::
   \Omega_{mn}(t) = \delta(t) \left[\int_0^t d\tau \Omega_{mn}(\tau) \right].

We can see that the Laplace transform of this is really simple,

.. math::
   \tilde \Omega_{mn}(\epsilon) =  \Omega_{mn}(0).



.. hint::
   Laplace transform of integral and delta function are

   .. math::
      \mathscr L (\delta(t-a)) &= e^{-a\epsilon}, \qquad \text{for } a>0. \\
      \mathscr L (\int_0^t f(t') dt') & = \frac{1}{\epsilon} \mathscr L_\epsilon (f(t)).

   So we have the Laplace transform of :math:`\Omega_{mn}(t) = \delta(t) \int_0^t d\tau \Omega_{mn}(\tau)` on both sides,

   .. math::
      \tilde \Omega_{mn}(\epsilon) & = \int_0^\infty dt e^{-\epsilon t}  \delta(t) \int_0^t d\tau \Omega_{mn}(\tau) \\
      & = \int_0^\infty \frac{1}{-\epsilon}  \delta(t) \int_0^t d\tau \Omega_{mn}(\tau) d e^{-\epsilon t} \\
      & = \frac{1}{\epsilon} \int_0^\infty   e^{-\epsilon t} d\left(\delta(t) \int_0^t d\tau \Omega_{mn}(\tau) \right)  \\
      & = \frac{1}{\epsilon} \int_0^\infty   e^{-\epsilon t} \int_0^t d\tau \Omega_{mn}(\tau)   d\left(\delta(t) \right) + \frac{1}{\epsilon} \int_0^\infty   e^{-\epsilon t}  \delta(t)  d\left( \int_0^t d\tau \Omega_{mn}(\tau) \right)  \\
      & = \frac{1}{\epsilon} \int_0^\infty   e^{-\epsilon t}  \delta(t) \Omega_{mn}(t)  dt  \\
      & = \frac{1}{\epsilon}   \Omega_{mn}(0)



.. warning::
   Derive the Fermi's golden rule from this.

Finally we can reach Fermi's golden rule.



Markovian - Another Approach
-------------------------------

**I'll put all the :math:`\hbar`s back into the equations in this subsection.**

I read the Markovian idea on quantiki [2]_ . Here is my derivation of Fermi's golden rule from quantum master equation using this approach.


First of all, we can use interaction picture. Master equation here can be rewritten using interaction picture.

.. math::
   \partial_t P_m & =  -\lambda^2/\hbar^2 \int_0^t dt' \sum_n \left[ ( W_{mn} e^{-i(t-t')(\epsilon_n - \epsilon_m ) /\hbar }  W_{nm} (P_{m} - P_{n}) - (e^{-i(t-t')\epsilon_m/\hbar} ( W_{mn}P_{n} - P_{m}W_{m n} ) e^{i(t-t')\epsilon_n/\hbar} )W_{nm}  \right] \\
   & = -\lambda^2/\hbar^2 \int_0^t dt' \sum_n \left[ ( e^{it\epsilon_m/\hbar}W_{mn} e^{-i t \epsilon_n/\hbar } e^{it'\epsilon_n/\hbar} W_{nm} e^{-it'\epsilon_m/\hbar} (P_{m} - P_{n}) - (e^{it\epsilon_m/\hbar}  W_{mn} e^{-it\epsilon_n/\hbar} (P_{n} - P_{m}) e^{it'\epsilon_n/\hbar} )W_{nm} e^{-it'\epsilon_m/\hbar} \right] \\
   & = -\lambda^2/\hbar^2 \sum_n \left[  \int_0^t dt' W_{mn}^I W_{nm}^I(P_m-P_n) - \int_0^t dt' W_{mn}^I W_{nm}^I(P_n-P_m)  \right]


Markovian means there is no dependence on the past, in other words, **the two point correlation in time** is non-zero only when the two time are equal in the correlation function, :math:`\mathrm{Corr}(t_1,t_2)=0` for all :math:`t_1\not= t_2`. In our master equation case,

.. math::
   &\int_0^t dt' W_{mn}^I(t) W_{nm}^I(t')(P_m(t')-P_n(t')) \\
   & = \int_0^t dt' W_{mn}^I(t-t') W_{nm}^I(0)(P_m(t)-P_n(t)) \\
   & = (P_m(t)-P_n(t)) \lim_{t\rightarrow \infty}\int_0^t dt' W_{mn}^I(t-t') W_{nm}^I(0) .

.. hint::
   This is corresponding to the Kenkre definition of Markovian.



So our master equation becomes

.. math::
   \partial_t P_m(t) &= -\frac{\lambda^2}{\hbar ^2} \sum_n(P_m - P_n) \left[ \lim_{t\rightarrow \infty} \left( \int_0^t dt' e^{i(t-t')\epsilon_m/\hbar} W_{mn} e^{-i(t-t')\epsilon_n/\hbar} W_{nm} + \int_0^t dt' e^{-i(t-t')\epsilon_m/\hbar} W_{mn} e^{i(t-t')\epsilon_n/\hbar} W_{nm} \right) \right] \\
   & = -\frac{\lambda^2}{\hbar^2} \sum_n (P_m - P_n) \left[ \lim_{t\rightarrow \infty} \left( \frac{\left| W_{mn}\right|^2 }{i\omega_{nm}} \left( e^{-it\omega_{mn}}  - e^{it\omega_{mn}}  \right) \right)   \right] \\
   & = -\frac{\lambda^2}{\hbar^2} \sum_n (P_m - P_n) \left[ 2\left| W_{mn}\right|^2  \lim_{t\rightarrow \infty}   \left( \frac{i\sin(\omega_{mn}t)}{i\omega_{nm}}   \right)   \right] \\
   & =  \sum_n (P_m - P_n) \left[  \frac{2 \pi \lambda^2 \left| W_{mn}\right|^2 }{\hbar^2}  \lim_{t\rightarrow \infty}   \left( \frac{\sin(\omega_{mn}t)}{\pi\omega_{nm}}   \right)   \right]


.. important::
   We have the following expression,

   .. math::
      \lim_{\epsilon\rightarrow 0} \frac{\sin(x/\epsilon)}{\pi x} = \delta(x) .


Using this expression of delta, we derived the Fermi's golden rule.

.. math::
   \partial_t P_m & =  \sum_n (P_m - P_n)   \frac{2 \pi \lambda^2 \left| W_{mn}\right|^2 }{\hbar^2}  \delta(\omega_mn)  \\
   & =  \sum_n (P_m - P_n)   \frac{2 \pi \lambda^2 \left| W_{mn}\right|^2 }{\hbar^2}  \delta((\epsilon_m - \epsilon_n)/\hbar) \\
   & =  \sum_n (P_m - P_n)   \frac{2 \pi \lambda^2 \left| W_{mn}\right|^2 }{\hbar}  \delta(\epsilon_m - \epsilon_n)


Comparing this result with the classical master equation, we can find out the transition rate,

.. math::
   \Omega_{mn} = \frac{2 \pi \lambda^2 \left| W_{mn}\right|^2 }{\hbar}  \delta(\epsilon_m - \epsilon_n)


which is exactly the Fermi's golden rule.



Footnotes
-----------


.. [1] Refer to *Quantum Noise* by Gardiner and Zoller, Chapter 5, Section 1.
.. [2] `Quantiki <http://www.quantiki.org/wiki/>`_ is a website of quantum information etc. The item about master equation is `here <http://www.quantiki.org/wiki/Master_equation>`_ .
