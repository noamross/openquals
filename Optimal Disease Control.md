% Optimal Control of Disease Literature
% Noam Ross
% 13-02-04 16:23:25


# @Haight2010

 - Invasives are expensive
 - Invasions often go undetected until after damage occurs.  Value to monitoring to allow avoidal of costly treatment, but monitoring expensive, too.
 - Species invasion is a POMDP
 - Objective of decision maker is to minimize sum of (discounted) management and monitoring costs, in light of imperfect info
-   Lit review: return to this for references
 - General results:   No action when sufficient probability that there is no infestation, monitoring alone with intermediate probability, and treatment alone when with high probability or large infestation.

## Model

-   Ecosystem has $n_t$ states $(\theta)$, each believed by the manageer at probability $\pi_{i,t}$
-   A transition matrix $\boldsymbol{P}^a$ defines transition probabilities between states
-   An observation matrix $\boldsymbol{R}^a$ defines  the probability of observing each state given the actual state. (Elements are $r$).  If observation were perfect, it would be an identity matrix.
-    Note that there are $a$ matrices of each type, corresponding to each action $(a)$ that the manager may take in a period.
- Manager's beliefs $\boldsymbol{\pi}_t$ are changed at each time step using $\boldsymbol{R}^a$ via a Bayesian updating:

$$\pi_{j,t+1} | \theta, a = \frac{\sum_{i=1}^n \pi_{it} p^a_{ij} r^a_{j\theta}}{\sum_{i=1}^n \sum_{k=1}^n \pi_{it} p^a_{ik} r^a_{k\theta}}$$

 
-   Manager pays both damage and management costs, which differ by action and state $(d^a_i, m^a_i)$.
-   Optimal value function given beliefs is the min. cost of optimal actions of period with initial belief state $\boldsymbol{\pi_1}$
-   Minimize the value function by the selection of actions over time.

$$\min_{a \in A} \left[ \text{expected costs in this period summed across states, weighted by beliefs} + \delta \times \text{expected cost in next period} \right]$$

Across all $t \in T$.

Expected discount cost in next period is the weighted sum of optimal values associated with all possible belief states.  Weight is the probability of starting in state $i$, moving to state $j$, and making observation $\theta$, after taking action $a$.  There is a terminal condition that the last action has minimal cost in that period.

-   Use algorithm, rather than exact solution
-   Define probabilities as discrete classes.
-   Solve backwards from terminal period.  Solve for the minimum cost of each action given each belief in each period.
-   This is very computationally intense for anything but simple problems.

## Application

-  States are no, moderate, and high infestation
-  Can treat or not, monitor or not.  Monitoring conveys perfect info, some info available without monitoring.  Treatment knocks down high infestatin and imperfectly reduces moderate or no infection.
- Damage is zero with no infestation, 10 and 20 for moderate and high infestation.  Monitoring costs 4.  Treatment costs 20. Discount rate 0.95 and 20 year period.

## Results

 - In base case, optimal policy is no action with large probability of no infestation, monitoring for intermediate, and treatement when probability of moderate or high infestation is large.  Never optimal to both treat and monitor.
-  To evaluate value of perfect monitoring, compare cases of perfect and costles and zero monitoring.  With none, action is just treat or not treat.  Generally treeat with >50% chance of non-zero infection.    Treat less often with monitoring.  Difference in overall cost with free perfect monitoring is on the order of overall costs
-  Imperfect monitoring still has value

# @Horie2013 - Optimal Monitoring and Control of Oak Wilt

## Introduction

-   See @Harwood2011 on Dutch elm disease model
-   Good refs here - use for introduction
-   Disease models have been simulation or simple optimizations.  More recently, spatial optimization, such as @Epanchin-Niell2012 or @Hauser2009
-   Model is to optimize one-time surveillance effort across sites, with uncertain level of infection.  Two stages:
    -   Select sites for surveillance
    -    Apply treatments where infestation found
-   Model is mixed-integer linear program adapted from @Snyder2004
-   Apply model to Oak Wilt in Anoka County, MN

## Model

-   Choices for management are yes/no to survey, and number of infected to remove.  Aim to minimize the number of newly infected trees following treatment
-   New infections are linear increase on old infections

$$Q_j = g_j (I_j-R_j)$$

Where at site $j$, newly infectious trees are $Q$, $g$ is the growth rate, $I$ are infected trees , and $R$ are trees removed.

Sites are independent - slow root-root spread.

 - Aim is to minimize $Q$ across all $j$.
-   Inspection choice is binary, removal choice is continuous, but is zero at non-inspected sites.
-    Removal number is dependent on detection efficiency (0-1)
-  Costs are per-tree for both inspection (total trees) and removal (removed trees).  A budget contrains the total cost
-  Because of limited budget, managers take sample of trees to estimate proportion infected at each site, and their belief is approximated as a Beta distribution.  The set of all these distributions is approximated using a set of random draws (scenarios).
-  The objective is to minimize the newly infected trees across all (equally likely) scenarios

## Application

-   Oak Wilt in Minnesota
-   Exponential growth rate of disease at all sites, "real" populations estimated from another model in @Haight2011.  Beta distributions assume sampling rate of 0.9% of trees per site.   
-   Tree density varies by site.
-   Relatively low infestation rates (ave <1 infection ha^-1^)

## Results

-   Expected percentage of healthy trees increases approximately linearly with cost.
-   At lower level of infestation, costs are lower but more of budget is take up by surveillance.
-   Optimal for manager not to survey more sites until all  infected trees on sites already surveyedare removed, so curve flattens several times.   Why? Lower-priority cells have many trees to inspect and few trees to find.

## Rules of thumb

-   Which sites to treat?
    -   Highest expected infestation (kill more)
    -   Highest proportion of infested (easier surveying per kill)
    - Highest number of trees to be saved

-    Second rule come closest to matching optimization, but still a penalty for non-optimal management
-   Optimization usually involves more surveillance than rules of thumb, because it involves picking sites that make it more efficient
-   Greater pre-optimization sampling improves optimization, but not much at low budget levels, because you don't bother with sites with low infestation, anyway.
-   With imprefect surveillance, more sites are optimally selected and more money dedicated to surveillance.
-   

# @Carrasco2010

Main question: How does optimal policy under no uncertainty differ from robust policy under certainty?

Study system: Colorado potato beetle invasion on UK.

# Model

 - Combination of @Sharov1998 and @Rowthorn2010
-   Spread by reaction-diffusion, with constant rate assuming constant diffusion and exponential growth.  Concentric spread circles
-  Damage assumed to be linear with area
-   Barrier zone treatment cost is proportional to length of invasion front and reduction in spread rate, the latter of which has a maximum
-  Continuous time
-   Goal is to minimize damage and control costs

## Model 2 - stratified diffusion

-  Discrete time
-   Colony produces emigrants at rate proportional to its area
-   New colonies establish in random locations - no spatial interaction between them
-   Probability of establishment is proportional to host in the landscape
-   Agency prioritizzes control of satellite colonies and uses the remainder of expenditure for control of initial colony.
-  Budget limits control measures, which are composed of search and control costs.
-  Search activity have diminishing marginal returns as the area of invasion 
-  Failure to eradicate and post-eradication monitoring costs included.

Both models had eradication as the optimal policy due to small area invaded at discovery.

## Information-gap theory

-   Meant to provide robust management in light of largest uncertainty range in the model, when measures of uncertainty are unavailable.  See @Ben-Haim2006
-   Requires process model, performance requirement, and uncertainty model.  In this case, Net Present Value of management and damage costs is performance requirement.  Also, can not spend more on control than damages without any control.  Alternative contraints are 50% higher and lower.
-   $\alpha$ represents the info gap, or the difference between knowledge of parameters and certainty, as a fraction, where $\alpha \geq$ the normalized difference between the best estimate and the actual value.  it is unknown.
-   Only the worse cases than the best estimate are considered
-    Info-gap theory identifies best policy as one most likely to satisfy the minimum constraint of success
-   The robustness function $\hat{a}$ is the maximum of $\alpha$ that fulfills the performance criteria given each policy options and the uncertainty in the parameters.
-   Four policies compared - attempt eradication and eventually give up attempt eradication (optimal model solution), allow invasion, attempt eradication for two years and chooses to continue if the invaded area has been reduced.

## Results

 - Optimal control solutions are all "bang-bang" style with initial control until eradication or budget exhaustion, or giving in if costs are too high
-    With stochastic model, colony eradication is cost effective but slowing of a very large parent colony is not
-    With the  info-gap deterministic model, an eradication policy is more robust to uncertainy than the optimal policy.  It meets the criteria for the largest values of $\alpha$ 
- For the stochastic stratified dispersal model, robust policy is also the optimal policy.  However, if performance criteria change, best policy changes.   With more  budget it is more robust to accept invasion than attempt to control.  With less money, optimal policy is same as robust one in both models
-   Differences between robust and optimal policies arise when there are high diffs between benefits of eradication and slowing down policy, such as if eradication could prevent a quarantine policy.

To Read:

Chadès, I., Martin, T.G., Nicol, S., Burgman, M.A., Possingham, H.P., Buckley, Y.M., 2011. General rules formanaging and surveyingnetworks of pests, diseases, and endangered species. Proceedings of the National Academy of Sciences of the United States of America 108 (20), 8323–8328.

Bogich, T.L., Liebhold, A.M., Shea, K., 2008. To sample or eradicate? A cost minimization model for monitoring and managing an invasive species. Journal of Applied Ecolo- gy 45, 1134–1142.

Hauser, C., McCarthy, M., 2009. Streamlining ‘search and destroy’: cost-effective surveillance for invasive species management. Ecology Letters 12 (7), 683–692.

Mehta, S.V., Haight, R.G., Homans, F.R., Polasky, S., Venette, R.C., 2007. Optimal detec- tion and control strategies for invasive species management. Ecological Economics 61, 237–245.

Homans, F., Horie, T., 2011. Optimal detection strategies for an established invasive pest. Ecological Economics 70, 1129–1138.

# @Rowthorn2009 - Control in metapopulations

Read:

 - Loose coupling in metapopulations leads to local fade-out but global persistence [@Keeling2000(Gilligan)]
-  Local deployment of control in one region may benefit other regions, but local control may be  compromised by re-invasion
-  Aim to optimize control deployment
-   One conclusion is that giving preference to most highly infected regions might be worst strategy in limiting the global epidemic

## Model

-   SIS model with natural recovery but no immunity
-   Number of infected modeled, other compartments implicit, two regions
-    Control is drug treatment on infected in each region
-    Budget is constant - no savings through time.  All must be spent at each period.
-  Minimize the integral of total infected, discounted through time.  Also consider the possibility of minimizing a power (>1) of the number of infected, to prioritize areas with higher levels of infection.
-  In an extension, connection between the two regions can be controlled by quarantine.  Efficacy is <1, with diminishing returns as more effort is spent.  Bugets between quarantine and treatment are separate, so goal is to minimize the extent of quarantine.

##  Results

 - With sufficent budget, infection is either eliminated, or brought to some equilibrium.
-   Bringing regions into equal levels of infection is worst strategy - maximizing the discounted infection over time.
-      Putting all resources to less-infected region and only remainder to more-infected region appears to be optimal, with numerical simulations
-   These are also the case when exponents emphasize equalization between the two regions
-   Difference between these strategies depends on iniitla conditions and parameters.  With low infection rate, both strategies control the disease.  At medium levels, only the optimal one can.
-  Medium level zone size spends on relative magnitude of within- and between-group transmission.  As between-transmission increases, the area where only the optimal solution works gets smaller.  That is, the outcome becomes less sensitive to choice of policy because it's like one big population
-    With quarantine, optimal solution is to start with high quarantine effort, end decrease as populations become similar.  As resources are used to suppress any infection in low infection region, they become freed up for high-infection region.

# @Forster2007 - Optimizing disease control at landscape scale


Look up: @Dybiec2004, @Dybiec2005

Main questions:  

 - Is it optimal to treat a fixed portion of infected fields?
 - How does the distinction between a single season and many seasons affect the outocome.  (Discount rate issue)

## Model:

 - SIS on a lattice, where S/I unit is each site
 - Mean-field approximation.   Change in proportion of infectious site is just current proportion times (inverse of infectious period + proportion of non-infected sites times beta)
-   Control shortens the infectious period for treated sites $(k)$, speeding recovery
-   A critical level of treatmet $k_c$ leads to eradication in the long-term
-    Objective is to minimize the cost of treatment and damage, which are linear on $k$ and $I$.  Within a season, no discount rate, but interannually, discount rate is included.

## Results

- For short-term control, bang-bang solution of initial treatment of all, then no sites is optimal, or not treat at all
-  For long-term control,  optimal path is similar, but switch is from treating all sites to treating an intermediate level

## Comparing to explicit spatial case with simulation model

 - Optimal strategy with spatial model is similar qualitatively, clearly outperforms constant treatment straategies. 
-   Biggest difficulty is estimating switch time, but there is considerable margin for error that

# @Fenichel2010

$R_0$ based approaches to disease management don't make sense when disease is already established.  They don't take into account transient dynamics, or the role of a population of already-infected hosts.  Assume performance criteria of eradication.

For a standard SI model, maintaining population below a threshold may be more stringent management than needed to cause $I$ to go towards zero, because the harvesting itself may modify dynamics.

When non-selective harvesting is included in the model, then the threshold density for disease outbreak is no longer constant.  The threshold density becomes an increasing function of the harvest rate.

Modify the SI model to a $N\theta$ model, when $N$ is total population and $\theta$ is proportioned with disease.  $\hat N$ is the population level that keeps $d\theta / dt$ below zero, *but only when $I=0$*

Once disease arrives, $\hat N$ changes with both the host population and the prevalance of disease.

Keeping host population below host-density threshold is sufficient for preventing disease invasion, but not for controlling it once it has occurred.   

Ecomomic model is that harvest is nonselective, but only healthy harvested organisms, have value, and infected ones also do damage (e.g. transmission to livestock)

Optimal path with disease is to redice populations even though they are below host-density thresholds, so as to spur reducetions in disease.  Then harvesting is reduced to let population growth while eradicating disease.  It may not be optimal to eradicate the disease, though, if its disease-free optimum population is above the threshoold for disease growth.  Initially, harvest may be great, but recovery is allowed at a level that still maintains some disease level.  Similar results when there is cross-species transmission across multiple hosts.

Read:
Fenichel, E. P., and R. D. Horan. 2007a. Gender-based harvesting in wildlife disease management. American Journal of Agricultural Economics 89:904–920.

Bicknell, K. B., J. E. Wilen, and R. E. Howitt. 1999. Public policy and private incentives for livestock disease control. Australian Journal of Agricultural and Resource Economics 43:501–521.

Gaff, H., H. R. Joshi, and S. Lenhart. 2007. Optimal harvesting during an invasion of a sublethal plant pathogen. Environ- mental and Development Economics 12:673–686.


# @Homans2011

Optimal detection effort ahead of a disease front with stochastic stratified dispersal.

Assumes a dynamically optimal managment plan of a spread center once it is detected.

##  Model 

 - Population spreads at constant rate from front
 - Choose detection effort that minimizes the costs that accrue in new invasions ahead of the front before the front arrives
 - Cost of detection effort increases quadratically with effort
 - Damage cost of pest increases with time from establishment with expotential growth of pest
 - Treatment removes pest, attempts to optimally minimize the damage function.  Removal costs are quadratic to removal amount
 - This is solved for the optimal cost of treating a new invasion, which is a function of the time from establishment to detection and the initial stock level
 - Greater detection effort reduces the time to detection of a new invasion and thus the size at detection
 - These are also influenced by distance from the front

## Results


For a gypsey moth case study:

Optimal detection effrot increases with distance from the front until a plateau is reached.  This is because it is worth more to eradicate populations that won't be overcome by the front for some time.    However, it plateaus because at a certain distance, eradication is the optimal strategy (the front never effectively reaches this point), and no benefit is gained from earlier detection.

Sensitivity analysis:

 - If infections are bigger, eradication is a better strategy and optimal detection there is worth more
 - If the pest growth rate is higher, optimal detection is worth more everywhere but eradication occurs closer to the front
 - Same if the damage caused by the pest is greater
 - Reverse if control cost is greater or detection cost is greater, or discount rate is greater, or if the pest is hard to detect.
 
 # @Gaff2007

 Optimal control of an integrodifference SI model

 Objective function is profit from harvest of healthy plants less the cost of harvesting effort

 Based on agricultural field system and single-season period.

 ## Model

 -   Dispersal kernel with a maximum radius - cosine function truncated at zero
 -    Harvest does not discriminate by disease status
 -    Optimal harvest would occur on last day of growing season
 -   Population grows exponentially, subject to harvest, which has a maximum value
 -     Susceptible population grows exponentially but is decreased by infection
 -    Profit only comes from selling the healthy plants

 ## Method

  - Iterative numerical method, solves for state variables forward in time and adjoints backwards in time.  See @Joshi2006

 ## Results

 - In case of no disease, harvest at all locations at last date of season
 - With disease, harvest at maximum rate over areas ~3X dispersal range from the initial infection, from the start, then stop harvest in those areas when innoculum sources are mostly gone.  Harvest from these areas is reduced but harvest in other areas is saved.

