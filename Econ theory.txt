% Forestry Economics
% Noam Ross
% 13-02-12 11:20:51


# @Reed1986
        
- Generally, forest models are stand- or forest-level, he former of twhich are even- or unven-aged
- Forest models are generally comprised of many even-aged stands of different age, species, productivity
        
## Even-aged stand models
        
 - Stands regrow and are cut at age that maximizes the mean annual increment, which is the optimal rotation length $T_C$.  This is found by $v'(T) = v(T)/T$.
- Traditionally, aim of forest is to create a *normal forest*, which cotains equal areas of each class to ensure an even-flow of timber volume.
- The @Faustmann1849 model provides the *economic* optimum, accounting for harvest costs and discount rate.  In this model, the present value of the stand is:
        
$$PV = \frac{V(T) - C}{e^{\delta T} -1}$$
        
 Maximizing this, we get:
        
$$V'(T) = \frac{\delta \left(V(T) -C\right)}{1-e^{-\delta t}}$$
        
Solving this yield $T_F$, the optimal rotation age.  PV minus establishment costs are the *land expectation value*.  The value of the site is the value of timber in the next rotation plus the value of selling the site after that.   At the optimum, the marginal growth thourgh not cutting equals the maringla growth through cutting and selling the site.
        
The present net worth formulation is defined as the PV over one rotation.  In the simplest case it includes only the timber and not the site value.  The difference is small for normal discount rates, but the rotation period is independent of planting costs, which are considered "sunk".
        
An internal rate of return formulation treats the land value as exogenous, which doesn't make sense for forestry-only treatments but might make sense in the face of other land pressures.
        
The Faustmann model is, of course, overly simplistic,  @Hartman1976 finds that increasing the value of the standing forest lengthens the rotation age, even beyond the culmination (max volume) age of the forest.  It could be less, though, depending on the non-timber yield functions.
        
@Reed1984 shows that fire risk is equivalent to adding a premium to the discount rate, shortening the rotation period.
        
@Heaps1979 find that when the harvest rate is constrained, you can't harvest the whole stand and evenagedness is lost.  Harvesting takes place over a number of disjoint intervals.  Effectively you are adapting the age distribution to satisfy the harvesting constraint, so the the first few intervals are of different lengths.  Afterwards the Faustman rotation holds.  A similar pattern occurs if harvesting costs are nonlinear, and the final rotation age is set to the minimum average cost level.
        
Other related problems include that of optimal thinning pattern. to obtain maximum yield over a rotation.
        
Despite the attention to this problem, a single stand is rarely the management unit of interest.  A government  agency or timber company aims to assure a large flow of timber or optimize profits across many stands using shared resources and that are biologically and economically heterogenous.
        
## Forest-level models
        
Typical theory is based on a *normal forest*, from which timber can be extracted in perpetuity.  Very common in history of forestry planning.   Trouble is how to arrive at this state.  Traditional forestry tries to do so in one rotation, but this is nonoptimal.  
        
Following @Reed1985, the forest equation can be represented as
        
$$\vec{X}_t+1 = R\vec{X}_t - S\vec{h}_t$$
        
Where $\vec{X}$ and $\vec{h}$ are vectors of the area of forest in each age class and the amount harvested in each age class.   Transitions are via leslie matrix.  In a normal forest, all ages below the optimal cutting age are equal in population, and harvest only ocurs at cutting age.
        
@Nautiyal1967 sought to maximize NPV of transition to normal forest within $P$ transition periods.  That is,
        
$$J_{P,T} = \sum_1^P \alpha^t V'h_t$$
        
Where $\alpha$ is the discount factor, and $V'$ is a vector of the value of stands in each age class.  However, they found that the optimal conversion period time $P$ was infinite, showing that conversion to normal forest was sub-optimal.
        
Solving with an infinite time horizon is a similar problem to the "Model II" formulation [@Johnson1977].  Me maximize:
        
$$J  = \sum_1^N \alpha^t \vec{V'} \vec{h_t} + \alpha^{N+1} \vec{r'} \vec{X}_{N+1}$$
        
Subject to:
        
$$\vec{X}_t+1 = R\vec{X}_t - S\vec{h}_t$$
        
and
        
$$0 \leq \vec{h}_t \leq \vec{X}_t$$
        
There may be constraints in terms of max and min changes in volumes cut between periods, or standing timber.  $\vec{r'}$ represents teh terminal payoff for each age-class.
        
        
@Reed1985b also use a leslie matrix approach to stochastic control of fire events.      Fire probability as a function of age is placed in the matrices as death probabilities for each class.    Approximate optimal solution is to solve this system with the average matrices.
        
Flow constaints are often the most important factor in determining the harvest plan.  Many economists have criticized these.  They are not as applicable on private lands.  @Dawdle1976 regards flow constraints as a throwback to times to in which forests were managed in common.
        
Without flow constraints, optimal policy is rapid draw-down of old-growth, more than would happen in reality due to capital constraints.
        
## Uneven-Aged Stand Models
        
@Chang1981 uses a Faustman-style model in which harvest is partial and wood volume is a function of both time since harvest and the residual at the last harvest, and solves for optimal cycle time and the optimal residual stock.
        
@User1969a and @User1969b used a leslie stage-based model and showed that if the harvest distribution by size class was even, only one level of harvest would lead to equilibrium, and @Rorres showed that the optimal equilibrium harvest schedule could be derived by linear programming.
        
@Haight1985 consider the dynamic optimization of a non-linear, multi-age stand, with no specificied ending distribution.  Using a gradient metod, they get the optimal selection harvests adn size distributions.  The sequence is a pulse-like transtion scheme.
        
See: Haight et al. (1985) Optimizing the sequence of diamaeter distributions and selection harvests for uneven-age stand management.
        
        
# @Tahvonen2004
        
Bare forest land, according to @Faustman1849, is worth:
        
$$ PV = \sum_0^\infty \left(px(s)e^{-\delta s} -w \right) e^{-i\delta s} = \frac{px(s) e^{-\delta s} - w}{1 - e^{-\delta s}}$$ 
        
Where $x(s)$ is teh forest grwoth function, and $w$ is the planting cost.  It's optimal to cut the stand when the growth rate of the value of standing trees equals the interest on the standing trees plus the value of bare land.  At this state, the value of agricultural output should be equal to the value of bare land in forestry.  Cycles may exist if there is a cost to the change between agriculture/other uses and forestry.
        
## Ecosystem service value in age class models
        
        
        
In age structured models, optimal long-run state is an equilibrium with cyclical flow of timber and age classes, though this may be an artifact of discrete time.
        
Optimal plans designed by linear programming often yield uneven timber flow over time, unless constrained.
        
## The age-class model
        
Land in each age class $s$ is denoted by $x_{st}$ and is has volume $f_s$.  $f$ is increasing in age.  With discount fact $b$, the Faustman rotation age $m$ is less than $\max_s \equiv n$.  $s=m$ maximizes $\sum_t^\infty b^{si} f_s$.  The utility is increasing and concave in total harvest per period.
        
The problem is to optimize the time-discounted utility of all harvests across all periods, subject to the restrictions of forest growth and max harvest.  Typical modifications assume linear utility, finite planning horizon, restrictions on harvest level, and endpoint conditions of the age distribution.
        
Here they use KKT theorem to find the optimum.
        
## Stationary Cycles
        
In Faustman harvest, oldest vintage is clearcut and the remainder are left alone.  An Optimal Faustman Forests are those in which this harvest is optimal.  It is *interior* if it also includes all age classes.
        
Besides normal foreests, other forests are OFFs with periodic consumption.  For instance, if smaller size classes than the Faustman harvest age are greater than even distribution.  In this case, timber harvesst will fluctuate and not reach "normal forest", and doing so would be nonoptimal.  The cycle has been shown to be stationary in the case of 2 age classes.
        
## Multiple land classes
        
With land classes that each have multiple growth rates, there is a more complex cycle.
        
When land may also be used for some non, forestry use, but there are diminishing returns on increased allocation to this use, this limits the cycling.  If the value has a low initial slope, then cyclin is restricted.  If the slope is high, then the steady state is constant, a mix of normal forest and other use.
        
## Ecosystem service value and age classes
        
In this model, there's a maximum timber volume that is reached, but stands may be older than this.
        
Stands have different values by age, and in a special case, value is zero for stands below some age class, and constant for above.  If the initial slope of the ecosystem service value is high enough, it is worth it to keep some land in old growth, but cycles exist because conversion is assymetric between the classes.


# @Tahnoven2009

Size-structured leslie-style model with density dependence recruitment and growth.  Death somewhat density dependent because death is a constant fraction of non-growing trees.  Density dependent growth can be a function of stand density, effort in replanting, or amount of space cleared by harvest.    Density dependent growth is function of stand basal area or basal area of trees larger than the size class growing (shade intolerance, with sigmoidal shape).  Costs include both harvest (as a function of wood volume) and replanting.

Numerical analysis to examine the role of regeneration, density dependence, and shading.  Parameterization based on Norway spruce.

## Effects of density dependence on regeneration

With density dependent regeneration, optimum is constant flow of yield and basal area, only being allowed to reach larger size classes initially to promote regeneration.  

Cycles emerge with gap-based regeneration, with thinning from below due to excessive regeneration, though mostly in the larger size classes.

Cycles also from planting-based regeneration.

All three cases are uneven-aged continuous cover, but costly/harvest based regeneration include cycles.

## Effects of density dependence on growth

With density dependent growth, optimal solution is smooth steady state and uneven-aged forest.  The higher the discount rate, the lower the size class which is cut.

Adding costly replanting, though, yields a cycle in which planting occurs along with max harvest.

## Effects of shading

 With shading (and natural density-dependent  regeneration), there is a cycle in which a clear cut occurs, but largest trees are removed the previous year and smallest trees are left.   This is to maximize the growth of the new and large new cohort.  Increasing the discount rate shortens the rotation.

Changing to artificial regeneration with shading, again first thinning from above occurs, then a clearcut.

## Economic parameters

With moderate shading and natural+artifical regeneration, a low rate of interest leads to an even-aged rotation cycle with occaisional thinning from below, with some planting to invest in future revenue.

As rate of interest increases, uneven-aged forestry based on natural generation is optimal, also if planting costs are high or timber prices low.

Within a narrow range of discount rates, each of these are locally optimal solutions, which probably also depend on initial size class structure.

## Application to Norway Spruce

Using data on Norway Sprice, the authors find an optimal solution that has a stationary cycle with multiple discount rates, though amplitude is less with higher discount rates.

Higher discount rates favor cutting trees at smaller diameter and lower-quality product.

It is worth it to thin smallest size classes even if they have no values.

After each cohort established, some thinning from below, until most of the cohort is harvested.    This cycle is approached no matter the initial conditions.

When harvest costs increase nonlinearly and are convex, there is no cycle.

Modifying density dependence has the largest of all ecological effects.

Requiring even-aged management in these cases reduces value by about 30% with ~100 year rather than ~30 year rotations.

