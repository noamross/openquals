% Forest Disease Dynamics and Management: A Draft Dissertation Proposal
% Noam Ross
% 13-01-27 19:01:48


Abstract
========

Forest disease spreads through plant communities structured by species
composition, age distribution, and spatial arrangement. I propose to examine the
consequences of the interaction of these components of population structure
*Phytophthora ramorum* invasion of California redwood forests. First, I will
compare the dynamic behavior of a series of epidemiological models that include
different combinations of population structure. Then I will fit these models to
time-series data from a network of disease monitoring plots to determine what
components of forest population structure are most important for prediction of
disease spread. Using the most parsimoniuous models, I will determine optimal
schedules of treatment to minimize the probability of precipitous decline of
host populations.

Introduction: Modeling Disease in Complex Populations for Management
====================================================================

Forest diseases can radically transform ecosystems. In North America, chestnut
blight, Dutch elm disease and beech bark disease have caused precipitous
declines in their hosts, leading to changes in the structure and function of
forests. Changes from such diseases may be the dominant force changing the face
of some forests in coming decades, overwhelming other forms of rapid
environmental change such as climate change [@Lovett2006].

Even simple host-disease systems exhibit complex dynamics [@Kermack1927]. Forest
disease dynamics include additional complexity driven by pathogen life cycles,
variation in pathogen and host populations, spatial strucure, and demographic
and environmental stochasticity [@Hansen2000; @Holdenrieder2004]. These factors
yield greater complexity in disease dynamics. This complexity, combined with
limited monitoring data and the uncertainty of the parameters of emergent
diseases, makes prediction of disease dynamics difficult. Yet such prediction is
needed to allocate limited resources for treatment and prevention.

One source of complexity in forest disease dynamics is structured variation in
host populations. Host tree populations may consist of multiple species or
genotypes, and consist of multiple sizes, each of which may interact with
disease or each other differently [@Gilbert1996]. All forest tree populations
are spatially structured; non-motile individuals can not be "well-mixed"
[@Filipe2003]. Each of these forms of population structure have consequences for
population dynamics that have been examined in theoretical models [@Dobson2004;
@Klepac2010; @Park2001; @Park2002]. However, dynamics resulting from these
components of population structure *interacting* are not well-characterized.

Understanding modeled dynamics of disease in structured populations may provide
insights useful for management. However, the ability to use such models for
management planning depends requires confidence in their predictive power,
particularly under novel management treatments. Recent developments in *particle
filter* techniques allow estimation of the likelihoods of complex dynamic models
[@Arulampalam2002; @Ionides2006; @Knape2012], and subsequent comparison of
models in out-of-sample predictive performance [@Vehtari2012]. Fitting dynamic
models direclty provides more confidence in the dynamic results than deriving
madel parameters individually from data, because allows tests confidence in
models' emergent dynamics rather than separate components.

Sudden oak death (SOD) is an emerging forest disease in California and Oregon
that threatens populations of tanoak (*Notholithocarpus densiflorus*)
[@Rizzo2003], has the potential to modify community structure [@Metz2012], and
cause significant economic damage [@Kovacs2011]. Silvicultural, chemical, and
other control techniques can modify the progression of disease [@Swiecki2013],
but eradication of SOD is unlikely [@Cobb2013] even at local scales. Long and
short- and long-term solutions to limit the damage of disease will require
continuous treatment and monitoring regimes. Under budget constraints, planning
for such treatment can be informed by dynamics models via optimal control
techniques.

I aim to answer the following overall questions:

1.  How do interactions between community, size, and spatial structure affect
    disease dynamics in forests?
2.  What aspects of population structure are most important in determining the
    probability and size of forest disease outbreaks in theoretical models?
3.  What aspects of population structure are most important in *predicting* the
    probability and size of SOD outbreaks?
4.  What control strategy minimizes the probability of SOD outbreaks at least
    cost?

Background
==========

Sudden Oak Death
----------------

Sudden Oak Death (SOD) is an emerging forest disease in California and Oregon
that poses risks to forests across North America and Europe. First observed in
California in the mid-1990s, SOD is caused by the water mold *Phytophthora
ramorum* [@Rizzo2002]. *P. ramorum* often kills tanoak (*Notholithocarpus
densiflorus*), which provide habitat and food to many vertebrate species, and
are the primary host of ectomycorrhizal fungi in redwood forests [@Rizzo2003].
Loss of this species may have cascading effects on other species. The disease
has also caused significant economic damage through removal costs and property
value reduction [@Kovacs2011]. It has the potential to spread to species in
other regions, such as northern red oak (*Quercus rubra*), one of the most
important eastern timber species [@Rizzo2002].

Population Structure: Multiple Host Species
-------------------------------------------

*Phytophthora ramorum* has over 100 host species in 40 genera, which fall into
several functional types [@Swiecki2013]. In canker hosts, which are all members
of *Fagaceae* in California, pathogen produces cankers on the trunk. Few if any
spores are produced from the cankers, and these hosts are generally dead ends.
SOD is fatal to many canker costs. In foliar hosts, *P. ramorum* resides and
reproduces in leaves and twigs. Foliar hosts vary greatly in susceptibility to
disease and spore production from diseased individuals. Some hosts are dead
ends; others are major drivers of disease spread and survival.

In Redwood forests in Northern California, the hosts of importance are tanoak
and bay laurel (*Umbellularia californica*). Tanoak has the dubious distinction
of being the only species that is both a canker and foliar host, and the disease
is generally lethal in these trees. Bay laurel is a foliar host in which *P.
ramorum* produces prolifically, and bay suffers no harm from the disease
[@DiLeo2009]. Redwood and other species are unsusceptible or dead-end hosts
where *P. ramorum* has little detrimental effect. In forests of the
redwood-tanoak-bay complex, bay Laurel acts as the primary disease reservoir
[@Davidso2008]. Tanoak infection and mortality is dependent on bay density
[@Cobb2012], and removal of bay is a commonly suggested treatment to reduce risk
of SOD outbreaks [@Filipe2013; @Swiecki2013].

@Dobson2004 examined a model of disease in multiple host species based on an the
SIR [@Kermack1927] framework. In it, species had density dependence but
interacted only though disease transmission. Importantly, transmission between
species was always equal or less than transmission between species. Dobson found
that in when transmission was density-dependent, species had a complementary
effect on the disease's rate of reproduction $(R_0)$; that is, a mix of both
species led to faster outbreaks. However, in the frequency-dependent case, $R_0$
was greatest when one species dominated. Transmission between species dampens
and synchronizes disease oscillations in each species, and at very high contact
rates between species the most susceptible species are more like to go extinct.
@Craft2008 implemented a stochastic version of this model in a system of
mamallian carnivores, finding that species with low intra-species contact rates
acted as sinks for disease, and their contact with more social species increased
spread disease within these low-contact species.

SOD dynamics differ from these systems in a few important ways. First, the
contact structure among species may not be symmetrical. Contact rates among
trees are driven by differences in species transmissivity (amount of spore
produced) and susceptibility (probability of infection per spore) than social
grouping. Where one species with high transmissivity coexists with a species of
high susceptibility, the probability of transmission may be higher between
species than within. Also, the spatial structure of species, and the dispersal
pattern of spores, may result in a hybrid between density and
frequency-dependent disease transmissions.

Population Structure: Size/Stage Classes
----------------------------------------

Within the tanoak population, epidemiological characteristics vary with tree
size. Trees of larger size classes are more likely to be infected and die more
quickly than smaller tree [@Cobb2012], Possibly due to the vulnerability of
cracked bark and the amount of bark tissue available for invasion
[@Swiecki2005]. There is no evidence currently for variation in spore production
or other physiological effects across tree sizes [@Davidson2008].

When disease dynamics occur much faster than demographic processes, we can treat
size classes similarly to different species, and examine the progression of
disease in a constant population structure. However, when disease progression
and growth occur at similar rates, these processes can interact to produce
complex dynamics [@Klepac2010]. This is the case with SOD; infectious periods
can last many years, during which trees may continue to grow.

The effects of age-based population structure and contact rates have been
studied extensively in the context of human disease and vaccination programs
[@Anderson1985; @Metcalf2011]. Reducing in-class transmission rates at young
ages increases the average age of infection, independent of the exact contact
structure. When only the susceptibility, and not transmissivity, of each age
class varies. @Klepac2010 found that increases in within-class transmission
increases both the infected and recovered population of those classes, and
classes with high transissivity have higher equilibrium populations relative to
low-transmissivity classes.

Population Structure: Space
---------------------------

*P. Ramorum* dispersal interacts with host population structure at many scales.
The pathogen spreads between trees via wind-blown rain and splash, limiting most
spores to spread within 15m of host plants [@Davidson2005]. However, occaisional
weather events, such as fog, can transport spores up to 3 km [@Rizzo2005]. Over
longer distances, *P. ramorum* can be transported in streams or spread via
human-mediated vectors such as nursery plant trade [@Osterbauer2004].
@Meentemeyer2011 found that the best fit kernel for a statewide model of *P.
ramorum* spread was the sum of two Cauchy kernels, one on the scale of tens of
meters and another on the scale of tens of kilometers.

Despite the ability to spread long distance, strong meter-scale gradients mean
that individual trees in stands can not be considered "well mixed" in terms of
contact rates between trees. Rather, contact patterns across space arise from
the interaction of spatial clustering of trees and the dispersal kernel of the
disease. Neither frequency- nor density-dependent transmission characterizes
this arrangement.

The effect of such spatial structure on development of epidemics has been
studied with continuous populations in space [@Bolker1999], metapopulation
models (@Park2001; @Park2002), models of individuals on a lattice [@Filipe2003;
@Filipe2004] and discrete individuals in continuous space (@Brown2004a). These
approaches have reached similar conclusions of the effect of spatial structure
in non-mobile populations. In all cases, the threshold of disease growth for a
global outbreak $(R_0)$ is greater than the threshold for a local epidemic
$(R_L)$. For instance, in metapopulations on a lattice,
$R_0 = R_L (1 + z\varepsilon)$, where $z$ is the average number of connections
between patches and $\varepsilon$ is the inter-patch contact rates [@Park2001].
In models of discrete individuals in space,
$R_0 = \lambda(1 + \bar{\mathcal{C}} SI)$, where $\lambda$ would be the pathogen
growth rate in a well-mixed population, and $\bar{\mathcal{C}}$ is the dispersal
kernel-weighted spatial correlation between susceptible and infected
individuals. $\bar{\mathcal{C}}$ evolves over time but reaches a minimum that
represents the threshold required for a global epidemic [@Brown2004a]. Also,
both clustering and anti-clustering (oversdispersal) reduce the rate of increase
of disease, except when clustering occurs at the scale of dispersal, in which
case it can accellerate spread. Fat-tailed dispersal kernels accellerate spread,
as well.

Study Approach
==============

I will examine the comparative effects of the above components of population
structure on SOD epidemics by (1) characterizing the dynamic behavior of models
that include each type of structure and their combinations and (2) identifying
the model structure that best predicts data of disease spread over time in
redwood-tanoak-bay forests. Using the best-fit model, I determine optimal
control plans for stand protection efforts to minimize the risk of loss of host
plants.

Determining the Consequences of Population Structure via Comparative Dynamics
-----------------------------------------------------------------------------

> **1. How do interactions between community, size, and spatial structure affect
> disease dynamics in forests?**
>
> **2. What aspects of population structure are most important in determining
> the probability and size of forest disease outbreaks in theoretical models?**

To characterize the effects of the population structure on disease dynamics, I
will compare four models. All are extensions of the epidemiological model of
@Cobb2012.

**Model A** is the simplest of the four models, only representing structure in
the form of differences between species of trees. It is described by this system
of stochastic difference equations:

$$\begin{aligned}
\boldsymbol{S}_{t+1} &\sim \boldsymbol{S_t} + \overbrace{  \text{Pois}\left[\boldsymbol{b(S_t+I_t)}\left(1-\sum_{i=1}^n w_i (S_{it} + I_{it}) \right) + \boldsymbol{rm_I I_t}\right]}^{\text{new recruits}} - \overbrace{\text{Binom}_1\left((\underbrace{1 - e^{-\boldsymbol{\beta I_t} - \boldsymbol{\lambda_{ex}}}}_{\text{force of infection}})\boldsymbol{S_t} \right)}^{\text{infections}} -\overbrace{\text{Binom}_2(\boldsymbol{m_S S_t})}^{\text{mortality}} \\
\boldsymbol{I}_{t+1} &\sim \boldsymbol{I_t} + \text{Binom}_1\left((1 - e^{-\boldsymbol{\beta I_t} - \boldsymbol{\lambda_{ex}}})\boldsymbol{S_t} \right) - \text{Binom}_3(\boldsymbol{m_I} \boldsymbol{S_t}) 
\end{aligned}$$

Here $\boldsymbol{S}_t$ and $\boldsymbol{I}_t$ are vectors of the populations of
susceptible and infected individuals of each species, and $\boldsymbol{\beta}$
is the matrix of contact rates. Other parameters are listed below in Table 1.

  ----------------------------------------------------------------------
      Parameter Vector Symbol      Description
  -------------------------------- -------------------------------------
       $\boldsymbol m_{S,I}$       Probability of death per year, for
                                   both susceptible and infectious trees

          $\boldsymbol b$          Fecundity per individual per year.

          $\boldsymbol r$          Probability of resprouting after
                                   death by disease.

          $\boldsymbol w$          Competitive coefficient (relative
                                   contribution to density-dependent
                                   recruitment)

     $\boldsymbol \lambda_{ex}$    Rate of contact of each species with
                                   pathogen spores from outside the site
  ----------------------------------------------------------------------

  : Model A Parameters

New susceptible trees enter the system via density-dependent seedling
recruitment and resprouting from recently killed trees. Susceptible trees become
infected at rates proportional to contact with infected trees
(density-dependent), and pathogen migrating into the system. Both susceptible
and infected trees die at constant, but different, rates.

The model is modified from @Cobb2012 in several ways: (1) inclusion of
demographic stochasticity, (2) conversion from continuous to discrete time, (3)
the inclusion of $\lambda_{ex}$, the force of infection from areas outside the
system, and (4) the exclusion of recovery of infected trees, which has not been
observed in the field. Finally, the only population structure in Model A is the
difference in species parameters. It excludes age structure and spatial
structure, assuming a well-mixed population and frequency-dependent transmission
(Following @Diekmann1990)

**Model B** adds stage structure to Model A. In this case, the vectors
$\boldsymbol{S_t}$ and $\boldsymbol{I_t}$ represent the population divided by
species and size class as follows

$$\begin{aligned}
S'_t &\sim S_t - \text{Binom}_1\left((1 - e^{-\boldsymbol{\beta I_t} - \boldsymbol{\lambda_{ex}}})\boldsymbol{S_t} \right) \\
I'_t &\sim I_t + \text{Binom}_1\left((1 - e^{-\boldsymbol{\beta I_t} - \boldsymbol{\lambda_{ex}}})\boldsymbol{S_t} \right) \\
S_{t+1} &\sim \text{Multinom}(\boldsymbol{A_S(S'_t,I'_t)S'_t}) + \text{Pois}\left[\boldsymbol{b(S'_t+I'_t)}\left(1-\sum_{i=1}^n w_i (S'_{it} + I'_{it}) \right) + \boldsymbol{rm_I I'_t}\right] \\
I_{t+1} &\sim \text{Multinom}(\boldsymbol{A_I(S'_t,I'_t)I'_t})
\end{aligned}$$

Here $\boldsymbol{A}$ is the matrix of demographic rates specifying transitions
between classes and mortality. $\boldsymbol{A}$ is a block-diagonal matrix of
size transition matrices, with no transitions between species classes.

Disease transitions are separated in time from demmographic transitions
[@Klepac2010]. In California, *P. Ramorum* reproduces and spreads during the
winter rainy season while most tree growth occurs in the spring and fall.

**Models 3 and 4** modify Models 1 and 2 by adding spatial structure in the form
of a lattice metapopulation. $\boldsymbol{S_t}$ and $\boldsymbol{I_t}$ become
$\boldsymbol{S_{jt}}$ and $\boldsymbol{I_{jt}}$, matrices of each species and
class at each location. Furthermore, the force of infection
$\left((1 - e^{-\boldsymbol{\beta I_t} - \boldsymbol{\lambda_{ex}}})\boldsymbol{S_t} \right)$
is replaced with an overall force of infection $\Lambda_{jt}$ at each location

$$\Lambda_{jt} =  \boldsymbol\beta \sum_{x=1}^J \phi (\boldsymbol I_{xt}, j, \boldsymbol{\theta}) + \lambda_{ex}$$

Here $j$ is the location, $\phi$ is the dispersal kernel of *P. ramorum* from
all locations $x$ to $s$, and $\theta$ is a vector of parameters of the
dispersal kernel. $\boldsymbol{\beta}$ remains the contact matrix, representing
physiological and vertical dispersal components of spore dispersal. I will test
the models using normal, exponential, and power-law disperal kernels.

Using these four models, I will determine:

-   How global epidemic growth rate $R_0$, probability of global epidemic, the
    epidemic size, and time to extinction of both hosts and pathogens vary
    between the models
-   How the presence of each form of population structure affect these values
    when global species densities and mean parameter values remain identical
-   Whether the effects of population structure are additive or if they interact
    in a more complex way.

The model will be parameterized with three species: tanoak, bay, and redwood,
(the latter representing all non-host species). Parameters and initial
conditions will be drawn from @Cobb2012 and @Filipe2013.

Selecting the Model that Best Repesents Observed Behavior
---------------------------------------------------------

> **3. What aspects of population structure are most important in *predicting*
> the probability and size of SOD outbreaks?**

To apply the understanding developed in exploring model structure to management,
I must determine which model best represents observed dynamics of SOD in
forests. I will fit the four models above to data of SOD spread in
redwood-tanoak-bay forests in California and compare their ability to predict
disease development

### Data

Data to fit the models comes from a collaboration with the Rizzo lab's disease
monitoring plot network [@Ref; @Ref; 2012]. The data consist of observations
tree size, alive/dead status, and disease status for trees greater than 1 cm
diameter from the years 2002-2007. Trees were observed in 14 sites along the
California coast from X (36.16°N) to Y (38.35°N), each of which contains an
average of 8 500 m^2^, seperated by minimium distances of 100m and arranged in a
random linear sequence. All plots are in forests dominated by redwood, tanoak,
and bay laurel.

Size, health, and disease status of all trees were measured in 2002 and 2007, as
well as for a random sample of 5 previously infected and 5 previously uninfected
trees of each species per plot in the years 2003-2006.

Since the time scale of the are not suffiently long to data to determine
transition between size classes, the parameters of transition matrices will be
drawn from other data from other sites and included as strong priors on these
parameters.

### The Observation Model

The process generating the data above may be considered **hidden Markov
process** [@Gimenez2012], that is, processes where the state of the system is
dependent on its previous state, but where states are partially or imperfectly
observed. Imperfect observation in this case is due to incomplete counting of
trees and error in determination of tree disease status. Tree disease is
determined by subjective examination of symptoms in the field, and then
confirmed in the lab for those individuals with sufficiently suggestive
symptoms. There are both false positives and false negatives:

$$\begin{aligned}
 p_{OI} &= p(\text{Observing that tree is diseased}|\text{tree is diseased}) \\
 p_{OS} &= p(\text{Observing that tree is healty}|\text{tree is healthy})
\end{aligned}$$

Then, for each sub-population (by species, size class, or location) observed in
each time period, then, the observed number of susceptible and infected trees
are:

$$\begin{aligned}
S_{obs} \sim \text{Binom}\left(p_{OS} S + (1-p_{OI}) I \right) \\
N_{obs} \sim \text{Binom}\left(p_{OI} I + (1-p_{OS}) S \right) 
\end{aligned}$$

* * * * *

***OMITTED HERE: OBSERVATION MODEL FOR PARTIAL CENSUS YEARS THAT I REALIZED WAS
WRONG***

* * * * *

Finally, for models with size-class structure, the observations omit the
smallest size class (seeds and seedlings \< 1 cm), as these were not measured.

### Model Fitting

**Particle filtering** determines the likelihood of a hidden Markov process by
taking advantage of the fact that, at each time step, the likelihood of a system
state is dependent on the previous state $(X_{t+1})$, and the observation
$(Y_t)$.

$$p(X_t) = p(X_t | X_{t-1}, Y_t)$$

While $X_{1:t}$ is hidden, $p(X_t|X_{t-1})$ may be approximated by by simulation
of the model process. Repeated simulations (*particles*) provide a distribution
of outcomes from which average likelihood are determined from the observation
model $(p(X_t|Y_t))$. For each time step, the particles are re-sampled according
to their individual likelihoods, in order to prevent *particle degeneracy* -
most particles approaching zero likelihood. The product of all steps' averaged
particle likelihoods is an unbiased estimate of the model
likeihood.[@Arulampalam2002]

With an estimate of likelihood available, one needs an approach to determine the
maximum-likelihood estimate of the model parameters $(\theta)$. Several methods
are available. **Iterated filtering** (IF) estimates $\theta$ by replacing
constant parameter values with a random walk $\theta_t$ of decreasing variance
over time, and determining the "states" of this walk as the variance approaches
zero. IF is computationally efficient but requires long time series.

Alternatively, **Particle Filter Markov Chain Monte Carlo** (PFMCMC) uses a
Markov Chain sampler (e.g., Metropolis-Hastings), calculating the likelihood at
each iteration using a particle filter. While computationally expensive, it does
not require long time series and may be used with multiple time series. PFMCMC
also integrates particle filtering into a Bayesian context, allowing the use of
informative priors. I will used PFMCMC to determine maximum-likelihood
parameterizations for all four models.

When fitting models 1 and 2 to the data, populations from each plot in each site
will be aggregated. For models 3 and 4, each plot will represent a single
sub-population on a lattice spanning the site. Initial density, species, age and
disease distributions for other sub-populations will be randomly generated from
other points on the lattice using the proportions from the measured plots.
Epidemiological parameters will remain constant across sites except for the
external force of disease $\lambda_{ex}$, which will be represented as a
noramlly distributed random variable to account for site effects. varies.

### Model selection

Model selection criteria have multiple purposes: to determine which model best
represents "true" processes, and to estimate the utility of models for the
purposes of prediction. In this case, I am interested in both - determining
which components population structure matter, and also providing an estimate of
predictive stength of the best model. For these purposes, I will use the
**deviance information criterion** [@Spiegelhalter2002, DIC]. DIC has several
advantages. Since it estimates the model complexity, or effective number of
parameters, directly from the likelohood distribution, it makes it easy to
incorporate random parameters such as $\lambda_{ex}$ that have non-integer
contributions to model complexity. Secondly, it estimates the how priors on
parameter values effect their contribution to model complexity.

DIC is not suitable for model-averaging. However, model-averaged results will
not likely be useful for the optimization analysis below. Using the best-DIC
model for prediction is a compromise between predictive ability and tractable
analysis of the model used for prediction. Use of DIC assumes that there is a
"best" or "real" model within the comparison. While no models are "true"
[@Box1976], this excercise is selecting a "best" or "most useful" model for
scenario exploration.

Using Dynamic Optimization to Determine the Best Control Strategy
-----------------------------------------------------------------

> **4. What control strategy minimizes the probability of SOD outbreaks at least
> cost?**

The best-fit model that captures essential aspects of the disease dynamics will
be used to develop an optimal control solution to minimization of disease risk
over time.

While forest disease management can occur under multiple, conflicting and
uncertain goals and priorities, here I consider the case where conservation of
tanoak and its ecosystem services are the goal. This is approximately the case
in Humboldt County, California, where large landowners have agreed to work in
tandem to control the disease. In this situation, managers goals can be
simplified to three components: (1) The minimum acceptable density of the
species of interest $(N_{min})$, (2) the cumulative acceptable probability that
the species will fall below that density $(p_{acc})$ during the management
period, and (3) the cost of disease control $C$. Using acceptable probabilities
avoids the challenge of defining and valuing the flows of ecosystem services as
a function of the forest composition [@Hartman1976].

Tools for SOD control can be categorized into two types. Silvicultural
(“host-centric”) treatments change forest composition. “Pathogen-centric”
treatments, such as quarantine, equipment cleaning and spraying, reduce the
probability of spore arrival [@Swiecki2013].

I represent these two types of treatment with two control functions. Cutting is
a periodic control treatment that can be imposed in any year. I define the cut
as a reduction in species density to the levels that would minimize the
probability of species densities falling below the acceptable level over a
management period without further controls. This will be a value that balances
stochastic risk of extinction with risk of diseae outbreak, bounded by the
minimum acceptable species density. As tanoak and bay laurel trees have little
timber value, each cut has a cost $(c_1)$. For the purpose of this model $c_1$
is independent of the extent of density reduction (that is, the variable costs
of cutting are negligible. Thus, the annual cost of cutting is $c_1 E_1$, where
$E_1$ is a zero-one control variable

Spraying is an ongoing control treatment that represents the combined annual
effort to reduce the arrival of new spores at the site. This modifies the
external force of infection

$\lambda_{ex} \equiv \lambda_0 \times (1 - e^{-a E_2 c_2})$

where $a$ is the effectiveness of treatment, $E_2$ is the effort spent at
spraying and $c_2$ is the annual cost per unit effort.

The dynamic optimization problem is to determine the combination of treatment
effort over time $(E_1t, E_2t)$ that minimizes the cost of treatment while
maintaining the probability of species loss at an acceptable level. That is,

$$\min \sum_{t=1}^T c_1(E_1)+ c_2(E_2) \text{ s.t. } p(N_t < N_{\min}) < p_{acc}$$

An alternative formulation, also useful to managers, is to minimize the
probability of outbreak given budget constraints $(B)$. Budget constraints could
be forumulated as total budgets for the entire mangement period, or annual
limits on spending. That is

$$\min \sum_{t=1}^T p_{(N_t < N_{\min})} \text{ s.t. } \sum_0^T c_1 (E_2) +  c_2(E_2) \leq B_T$$

or

$$\min \sum_{t=1}^T p_{(N_t < N_{\min})} \text{ s.t. } c_1(E_1) + c_2(E_2) \leq B_{ann} \forall \, T$$

References
==========
