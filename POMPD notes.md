POMDP Papers from Alan,

@Chades2008 use POMDP to determine wheter to continue to manage habitat and survey for species that are difficult to observe but may be extinct. The more threatened the species, the more time spent managing relative to surveying

POMDP algorithm finds an optimal allocation in each year given current beliefs.

Have set of states, set of actions. The transition matrix gives the next state
distributionn given each combination of states and actions. To make it partially
observed, there is also a belief satate. Find the best actions given belief
state and time. A value function

@Regan2011
==========

@Regan2011 use POMDP to examine eradication strategies, finding that when
detectability is low, it isi optimal to deply less efficient, low cost tools
when the species is not detected.

Belief states represent a uous but fully observable state space.

The probability of observation $z$, given the system is in state $s$, is the
observation model.

Have a probability of change for each transitiojn, vien each action.

The more expensive the actions, the less likely they are deployed in each ear.

@McDonald-Madden2011
====================

Like @Chades2008, but with mutiple populations.

@Chades2011a
============

Creates rules of thumb based on POMPD. Looks at networks of locations, rather
than physical space. Uses factored MDP to examine multiple optimal solutions.

see: Williams, B. K. 2009. Markov decision processes in natural resources
management: observability and uncertainty. Eco- logical Modelling 220:830–840.

@Chades2012
===========

An hmMDP - hidden model Markov Decision Process, has completely observable
states, but the actual transition matrix (dynamic model), is hidden, and can be
one of several.

% Optimal Control of Disease Literature % Noam Ross % 13-02-04 16:23:25

@Haight2010
===========

-   Invasives are expensive
-   Invasions often go undetected until after damage occurs. Value to monitoring
    to allow avoidal of costly treatment, but monitoring expensive, too.
-   Species invasion is a POMDP
-   Objective of decision maker is to minimize sum of (discounted) management
    and monitoring costs, in light of imperfect info
-   Lit review: return to this for references
-   General results: No action when sufficient probability that there is no
    infestation, monitoring alone with intermediate probability, and treatment
    alone when with high probability or large infestation.

Model
-----

-   Ecosystem has $n_t$ states $(\theta)$, each believed by the manageer at
    probability $\pi_{i,t}$
-   A transition matrix $\boldsymbol{P}^a$ defines transition probabilities
    between states
-   An observation matrix $\boldsymbol{R}^a$ defines the probability of
    observing each state given the actual state. (Elements are $r$). If
    observation were perfect, it would be an identity matrix.
-   Note that there are $a$ matrices of each type, corresponding to each action
    $(a)$ that the manager may take in a period.
-   Manager's beliefs $\boldsymbol{\pi}_t$ are changed at each time step using
    $\boldsymbol{R}^a$ via a Bayesian updating:

$$\pi_{j,t+1} | \theta, a = \frac{\sum_{i=1}^n \pi_{it} p^a_{ij} r^a_{j\theta}}{\sum_{i=1}^n \sum_{k=1}^n \pi_{it} p^a_{ik} r^a_{k\theta}}$$

-   Manager pays both damage and management costs, which differ by action and
    state $(d^a_i, m^a_i)$.
-   Optimal value function given beliefs is the min. cost of optimal actions of
    period with initial belief state $\boldsymbol{\pi_1}$
-   Minimize the value function by the selection of actions over time.

$$\min_{a \in A} \left[ \text{expected costs in this period summed across states, weighted by beliefs} + \delta \times \text{expected cost in next period} \right]$$

Across all $t \in T$.

Expected discount cost in next period is the weighted sum of optimal values
associated with all possible belief states. Weight is the probability of
starting in state $i$, moving to state $j$, and making observation $\theta$,
after taking action $a$. There is a terminal condition that the last action has
minimal cost in that period.

-   Use algorithm, rather than exact solution
-   Define probabilities as discrete classes.
-   Solve backwards from terminal period. Solve for the minimum cost of each
    action given each belief in each period.
-   This is very computationally intense for anything but simple problems.

Application
-----------

-   States are no, moderate, and high infestation
-   Can treat or not, monitor or not. Monitoring conveys perfect info, some info
    available without monitoring. Treatment knocks down high infestatin and
    imperfectly reduces moderate or no infection.
-   Damage is zero with no infestation, 10 and 20 for moderate and high
    infestation. Monitoring costs 4. Treatment costs 20. Discount rate 0.95 and
    20 year period.

Results
-------

-   In base case, optimal policy is no action with large probability of no
    infestation, monitoring for intermediate, and treatement when probability of
    moderate or high infestation is large. Never optimal to both treat and
    monitor.
-   To evaluate value of perfect monitoring, compare cases of perfect and
    costles and zero monitoring. With none, action is just treat or not treat.
    Generally treeat with \>50% chance of non-zero infection. Treat less often
    with monitoring. Difference in overall cost with free perfect monitoring is
    on the order of overall costs
-   Imperfect monitoring still has value
