% Forest Disease Dynamics and Management - Outline
% Noam Ross
% 12-12-12 12:00:06

# Abstract

Forest disease spreads through plant communities structured by species composition, age distribution, and spatial arrangement.   Each of these types of population structure have known effects on the outcomes and transient dynamics of disease, but their effects .  Optimal management of such disease requires estimates of the time-dependent risk of disease outbreak in such communities.  Using the study system of *Phytophthora ramorum* spread in Redwood forests of Northern California, I propose to examine how these elements of population structure interact to determine the dynamics of disease spread.  I determine the types of structure most important for predicting outbreaks in forests.  With such predictions, we can determine optimal silvicultural treatments for minimizing the outbreak of disease.


Specific Aims: Broad, long-term, big picture objectives., then specific questions. 500 Words.


Overall Questions
=================

-   How does forest disease spread through forest systems?
-   What aspects of forest structure (species composition, age and spatial
    structure) are important in predicting the spread and impact of disease?
-   What forest composition minimizes the risk of outbreak while maintaining
    desirable populations of at-risk species?
-   What is the most cost-effective strategy for maintaining populations of tree
    species?

Context: Landscape management of disease
========================================

-   Forest diseases and pests have the potential to cause damage
-   Diseases in forests are multi-host. Even when not, they influence multiple
    species in stand dynamics
    -   Disease in stand dynamic temporal scale. Can be deterministic (like
        spread of root disease), but also stochastic (Weather driven spread)

-   Importance of spatial extent of system.\
-   Potentially a different set of goals than in managing wildlife or crop
    systems
-   Importance of scale for management decisions (@Joao2012)

Modeling for management

-   Structured models to understand the system and scenario analysis
-   Unstructured approaches for forecasting
-   Combination needed for real-time decision-making
    -   Probabilistic component important

-   Confronting dynamics model with data - fitting data to individual components
    inadequate for complex system
    
# Context: Population Structure and Disease

Contact rates in SOD are not driven by differential mixing of groups, but of 3D structure and differing physiological response of the disease.
Inter-species studies have mostly focused on (symmetrical) contact structures where within-group contact rates exceed intra-group contact rates, or assymetric contact rates simulating rare jumps between species.  

Spatial structure, in both continuous-space and lattice populations, has been found to break epidemics in to both local and global stages.  The threshold for global outbreaks is greater than local, but spatial structure can also maintain the population.

Real communities contain structure along the lines of groups, stages, and space.  

@Cobb2012 and @Joao2013 use such a mixed-structure model to simulate dynamics.  However, the types of behavior such a system is capable of are not well characterized.    Nor are the consequences of the model on stochastic processes such as extinction time and outbreak length.

Sub-question 1: How do tansient dynamcs, as defined by $R_0$, epidemic size and extinction time, change with the addition of multiple forms of population structure?

 - Interaction of age and spatial classes
 
In this case, spatial structure creates greater local than global connectivity, creating a higher (but acheived in this case) threshold for global outbreak, and increasing the length of the disease, reducing the probability of extinction.

 

Study System - Sudden Oak Death in Redwood/Tanoak/Bay Forests
=============================================================

-   Caused by water mold *Phytophthora ramorum* [@Rizzo2002b]
-   Spreads via wind-blown raid and fog, as well as human vectors (short- and
    long-distance dispersal) [@Meentemeyer2011]
-   Dynamics dependent on forest composition:
    -   Wide host range, but lethality and transmissivity vary by host
    -   Lethal in tanak, spreads most widely from Bay Laurel, little effect or
        spread in Redwood and other species [@DiLeo2009]
    -   Lethality varies by tree size [@Cobb2012]

Description of population structure and disease

 - Contact structure 1 - tanoak-bay
 - Contact structure 2 - size pop
 - Contract structure 3 - space and dispersal kernel
 
How the $G'$ matrix changes in each of these circumstances

Approximations in long-distance work. 



General Approach
================





-   Extend mechanistic model from @Cobb2012 that incorporates disease and stand
    dynamics.
-   Build series of nested models of varying complexity that incorporate
    -   Species differences in demographic and epidemiological parameters
    -   Size structure in demographic and epidemiological parameters
    -   Spatial structure
-   How does inclusion of each component of structure modify
    - $R_0$ (global and local)
    - Epidemic size
    - Probability of outbreak
    - Time to extinction of tanoak and *P. ramorum*.
-   Compare models to determine best predictor of disease outbreak
-   Determine optimal combination of host- (harvesting) and pathogen-centric
    (spraying) controls over management periods, given constraints, to minimize
    probability of disease outbreak

# Data description

Model
=====

SIS model with a structured population, implemented in discrete time and space.

Forest stand is represented as a lattice, with populations of trees in each grid
cell. Populations in each cell are divided into classes with the following
attributes:

-   Species
-   Size class
-   Disease status (S or I)

Each class has its own demographic and epidemiological parameters:

  -----------------------------------------------------------------------
          Parameter Symbol         Description
  -------------------------------- --------------------------------------
          $\boldsymbol m$          Probability of death per year.

          $\boldsymbol b$          Fecundity per individual per year.

          $\boldsymbol g$          Probability of transition to the next
                                   size class.

          $\boldsymbol R'$         Probability of recovery from disease.

          $\boldsymbol r$          Probability of resprouting after death
                                   by disease.

          $\boldsymbol w$          Relative space taken up by an
                                   individual tree of the class, or the
                                   competitive coefficient.

        $\boldsymbol\theta$        Spore production and dispersal kernal
                                   parameters

          $\boldsymbol E$          Effect of density on $m$,$b$,and $g$.
  -----------------------------------------------------------------------

  : Class-specific demographic and epidemiological parameters

In different variations of the nested model, these parameters will either be
held at zero, be held constant across classes or allowed to vary across classes.

At each time step, populations transition between classes and new individuals
enter and exit each cell via recruitment and mortality. Transition between S and
I depends on the class-specific force of infection $(\boldsymbol\Lambda)$.
$\boldsymbol\Lambda$ on each class depends on both the burden of spores arriving
in the cell and the class's susceptibility to those spores. Spores arriving in
the cell are calculated by summing the dispersal of spores for each infected
class in the lattice, to get a vector of spore burden from each class for a
location. This is multiplied by a "Who Acquires Infection From Whom" matrix
(WAIFW, @Anderson1985) to get $\boldsymbol \Lambda$. There will be an addition
component of $\Lambda$ representing the force of infection from arrival of
spores from outside the stand.

Stochasticty will be incorporated into the model. Spore production and
transmission will be subjec to environmental stochasticity, and recruitment,
demographic transitions, and infection will be subject to demographic
stochasticity.

Additions
----------

Use @Klepac2010 structural framework, extended to include multiple species *and* life stages.

 - Multinomial draws for transition stochasticity
 - Poission distributions for births
 - Environmental stochasticity - what does this most effect?
     - Spore distribution/creation

 - Observational stochasticity
     - Binomial observation probability
     - Ask Richard - what do we think false positive and negative rates are like?
     
     
Need to meet with Alan to discuss data/model matchup?

Essential topics and papers related to disease modeling
-------------------------------------------------------

-   SIR Models: @Kermack1927, @Kermack1932, @Kermack1933, @Anderson1991
-   Host heterogeneity: @Anderson1985
-   Multispecies transmission: @Dobson2004, @Craft2008
-   Age-structured models: , @Klepac2009
-   Plant-specific spatial models: @Ferrari2006, @Bolker2009, @Gilligan2008
-   Stochastic spatial spread: @Lewis2000
-   Kernels for spatial spread on a discrete grid: @Chesson2005

The model selection process
===========================

**Goal**: Indentify the most parsimonious model structure for predicting the
spread of disease and mortality through the forest stand

Model fitting
-------------

-   Model data as a *hidden Markov process* [@Gimenez2012]
    -   Smallest size classes (seeds, seedlings) unobserved
    -   Disease observations imperfect - binomial process with underlying
        probability dependent on tree class and disease status

-   With likelihoods for the mechanistic model intractable, likelihoods can be
    calculated using particle filtering [@Arulampalam2002]
-   Maximum likelihood estimates of parameters calculated using *iterated
    filtering* [@Ionides2006; @He2010]

Model selection
---------------

-   Fit all possible combinations of models:
    -   Including or excluding size structure of each species (by fixing
        parameters across classes)
    -   Including or excluding density dependence on reproduction, growth, and
        mortality
    -   Including or excluding disease effects on reproduction, growth, and
        mortality
    -   Normal, fat-tailed, or uniform (no spatial structure) dispersal

-   Compare models via AICc. Eliminate models with AICc weights \< 4x the lowest
    AICc weight (following @Maunder2011)

Other Essential topics and papers related to model fitting
----------------------------------------------------------

-   @Hartig2011 and @Wood2010 describe a summary statistic approach (Approximate
    Bayesian Computing), also implemented in the `pomp` package in R
    [@King2010]. An example in @Martinez2011
-   More theory about the approach in @Andrieu2010a
-   If only distinguishing between a couple of models for hypothesis testing,
    might follow @Boettiger2012
-   General approach for forecasting, example from dynamic range models:
    @Pagel2012

Optimization
============

**Goal**: Determine the optimal course of action for minimizing probability of
disease outbreak over a management period, given budget constraints and and
species conservation goals

-   The best-fit model provides us with estimates of the probability over
    disease outbreaks in a forest stand over a management period. This
    probability is contingent on both forest composition and spatial structure,
    and the burden of spores from other areas, and changes over time as forest
    dynamics change the host population.

-   Both composition and the arrival of disease can be modified by controls.
    Select cutting may modify the composition and managment actions such as the
    cleaning of logging equipment can reduce the arrival of spores. Pesticides
    can also reduce the probability of spores successfully infecting healthy
    trees. All of these management actions (including logging) have costs, and
    are limited by budget constraints of management agencies and/or landowners

-   The solution to this optimal control problem will be an optimal *treatment
    rotation* - a schedule of harvest and spraying actions that minimize risk
    over the treatment period.

-   An alternative useful formulation of the problem is to determine the
    minimum-cost method given constraints of desired tree population and
    *maximum acceptable probability of outbreak*. An advantage of this approach
    is to provide managers with an method of implicit valuation of the tanoak
    population by illustrating the trade-off between costs and acceptable tree
    populations and risks.

-   Examine under a variety of regulatory constraints: limiting herbicide use
    for suppressing sprounts and others, harvest regulations in riparian areas,
    endangered species limitation on time/space of cutting.

-   An extension of the analysis above will include the parameter uncertainty of
    the best-fit model, and an optimization under the scenario that parameter
    uncertainties decrease with time

Topics and papers relevant to optimization
------------------------------------------

-   Optimal rotation under stochastic risk: @Reed1984
-   Forestry with multiple age classes: @Tahvonen2004
-   Optimal Management with risk of crossing uncertain thresholds:
    @Polasky2011c, @Chen2012
-   Risk minimization over time

Data to fit the model comes from a collaboration with the Rizzo lab's diease monitoring plot network.   The data consist of 14 sites, each of which contains X-X plots, seperated by minimium distances of Z.  Size, health, and disease status of all trees were measured in 2002 and 2007, as well as for a ramble sample of 5 trees of each species in the years 2003-2006.  Disease status was measured by asessing sympotoms in the filed, and confirmign with molecular methods.  Observations are thus probibalistic, with a binomial distribution.

Fitting methods

Two possible methods may be used, depending on computational efficiency or, *iterated filtering* [@Ionides2006, IF] or *particle filter MCMC* [@Knape2012, PFMCMC].  Particle filtering methods provide unbiased estimates for dynamic state space models.  IF determines the maximum likelihood fit by approximating a random walk of the parameters.  PFMCMC uses an MCMC to find the maximum likelihood, utilizing particle filtering at each step.

Model comparison and selection:

Model selection has multiple purposes.  First, to determine which model best is most like the true purpose, and to estimate the valdiity of the models for the purposes of prediction.  DIC has several advantages.  First, it incoporates any random variables.  Secondly, it estimates the loss of parameters from Bayesian inference.  As several components of the model have useul priors estimated form either data sets, this is useful in this case.  

Table 1:  Model Structures

 - Mean field
 - Mean field with species classification
 - Mean field with size classification
 - Mean field with species and size classification
 - Spatially explicit
 - Spaitally explicit with species classification
 - SE with size class
 - SP with size class and species



------------

# Introduction: Modeling Disease in Complex Populations

Forest diseases can radically transform ecosystems. In North America, chestnut blight, Dutch elm disease and beech bark disease have caused precipitous declines in their hosts, leading to changes in the structure and function of forests. Changes from such diseases may be the dominant force changing the face of some forests in coming decades, overwhelming other forms of rapid environmental change such as climate change [@Lovett2006].

Even simple host-disease systems exhibit complex dynamics[@Kermack1927]. Forest disease dynamics include additional complexity driven by variation in pathogen and host populations, pathogen life cycles, and demographic and environmental stochasticity [@Hansen2000; @Holdenrieder2004].  These factors yield greater complexity in disease dynamics.  This complexity, combined with limited monitoring data and the novelty of emergent diseases, makes prediction of disease dynamics difficult.  Yet such prediction is needed for long-term management of disease.

Quantitative disease forecasts are essential for optimal management.

One area of complexity in forest systems is structured variation in host populations.  Host tree populations may consist of multiple species or genotypes, and consist of multiple sizes, each of which may interact with disease or each other differently [@REF].  All forest tree populations are spatially structured; non-motile individuals can not be "well-mixed".  Each of these forms of population structure have consequences for population dynamics that have been examined in theoretical models [@REFS].  However, the interaction of these components of population structure are not well-characterized.

Modeling multidimensional population structure is problematic for several reasons.  First, as models get increasingly complex, analytic solutions are less likely to be tractable, and complete characterization of model behavior is unlikely.  Thus model (and) system behavior is more difficult to explore.  Secondly, high-dimensional models are difficult to estimate; each additional form of population structure multiplies the parameters involved, and requires additional data.

Thus, selection of a parsimonious model for predictive managemnent has two major components.  From a theoretical perspective, which components of population structure are most important for determining the relevant components of population dynamics?  And what model is most parsimonious for purposes of prediction?  The first question provides a universe of models from which to answer the second.

Such models give us the ability to mechanistically explore alternative management models with some level of confidence.  Models with both adequate mechanistic structure and predictive power are required for optimal management.  

## Overall Questions

-   How do interactions between community, size, and spatial structure affect
    disease dynamics in forests?
-   What aspects of population structure are most important in determining the 
    probability and size of forest disease outbreaks in theoretical models?
-   What aspects of population structure are most important in *predicting* the 
    probability and size of real forest outbreaks?
-   What population structure minimizes the risk of outbreak while maintaining
    desirable populations of at-risk species?
-   What is the most cost-effective strategy for maintaining populations of tree
    species in the presence of disease?


# Background

## Sudden Oak Death

Sudden Oak Death (SOD) is an emerging forest disease in California and Oregon that poses risks to forest across North America. First observed in California in the mid-1990s, SOD is caused by the water mold *Phytophthora ramorum* (Rizzo et al. 2002a). *P. ramorum* often kills tanoak (Notholithocarpus densiflorus), which provide habitat and food to many vertebrate species, and are the primary host of ectomycorrhizal fungi in redwood forests (Rizzo and Garbelotto 2003). Loss of this species may have cascading effects on other species. The disease has also caused significant economic damage through removal costs and property value reduction (Kovacs et al. 2011). It has the potential to spread to species in other regions, such as northern red oak (Quercus rubra), one of the most important eastern timber species (Rizzo et al. 2002b).

## Disease in Structured Populations

# Study Approach

## Nested Models 

## Model Fitting and Selection

### Data

## Optimization

Emerging Forest disease. 

Forest diseases can radically transform ecosystems. In North America, chestnut blight, Dutch elm disease and beech bark disease have caused precipitous declines in their hosts, leading to changes in the structure and function of forests. Changes from such diseases may be the dominant force changing the face of forests in coming decades, overwhelming other forms of rapid environmental change such as climate change (Lovett et al. 2006).

Much recent work has focused on predicting and managing the spread of SOD (Meentemeyer et al. 2011, Filipe et al. 2012). Yet in many areas, SOD is already so well established that eradication is infeasible. Landowners thus need strategies to manage forest and conserve species under an ever-present risk of disease.
The dynamics of SOD are highly dependent on forest community composition, which changes as forests age. This is because P. ramorum has a wide host range, yet its lethality and transmissivity vary greatly by host. For instance, while it most often kills tanoak, it produces many more spores in California bay laurel (Umbellularia californica), which suffers no ill effects (DiLeo et al. 2009). It has intermediate effects on many other species. Lethality also varies considerably with tree size (Cobb et al. 2012), and both lethality and transmissivity vary between individuals of the same species (Rizzo and Garbelotto 2003). Epidemiological modeling (Cobb et al. 2012) indicates that the disease has a host-density threshold. Below a critical concentration of host trees, the disease and hosts remain in a stable equilibrium. Above the threshold, increased transmission leads to disease outbreak and host decline. This dynamic could be exploited to maintain the disease at manageable levels.
While the host-density relationship is qualitatively robust, and has been observed in other disease and parasite systems (Davis et al. 2004, Frazer et al. 2012), actual threshold levels for SOD are uncertain. The relative novelty of the disease, its broad host range, and
considerable variation in individual and community properties mean that thresholds will be difficult to predict at small scales, such as the scale of an individual land parcel that must be managed. Also, P. ramorum infection requires considerable effort to detect - some species may show no signs of infection at early stages, and it is cost-prohibitive to examine every leaf. This limits the ability to estimate stand-level infection and manage forests appropriately. General techniques for estimating ecological thresholds are being developed (Scheffer et al. 2001, Carpenter et al. 2011), but they are limited in statistical power (Boettiger and Hastings 2012), and only work under a limited set of theoretical conditions (Hastings and Wysham 2010).
Management techniques for SOD must be robust to such uncertain thresholds. Such approaches are applicable to managing many diseases, pests and parasites, as new outbreaks must be managed even as details of the threat are unknown. This is a challenging economic problem that has not been studied in the context of forest management. Polasky et al. (2011) showed that, when managing natural resources subject to threshold-driven changes in dynamics, the optimal approach is to exercise precaution by reduce pressure. However, in this case the probability of regime shift was a known quantity. Brozović and Schlenker (2011) explored how optimal decisions change with uncertainty, but only under equilibrium conditions, not under a dynamic regime such as forest growth and management. Also, neither of these cases have examined optimal behavior when the natural resource primarily provides continuous ecosystem services, rather than timber harvest value, as is the case with tanoak. Previous work on managing forest diseases has focused on optimal balance between detection and control efforts (Bogich et al. 2008, Ndeffo Mbah and Gilligan 2010), and slowing spread vs. eradication strategies (Sharov and Leibhold 1998). These efforts have focused on landscape-level decisions, but not those faced at the scale of individual landowners.
3. Goal
My research will try to determine What is the best way to manage forests at risk from emerging disease outbreaks? Using a combination of epidemiological and economic modeling approaches, I will address these specific questions:
! How does the risk of disease affect optimal management under dual goals of species conservation and timber harvest?
! How should one allocate resources between preventative measures that reducw risk of disease entering the property, and removing trees to prevent the disease from reaching outbreak levels?
! How does the optimal strategy change with the level of uncertainty of disease outbreak? ! How does does the optimal strategy change if uncertainty decreases over time, as when
more is learned about the biology of a new disease?



Context: Landscape management of disease
========================================

-   Forest diseases and pests have the potential to cause damage
-   Diseases in forests are multi-host. Even when not, they influence multiple
    species in stand dynamics
    -   Disease in stand dynamic temporal scale. Can be deterministic (like
        spread of root disease), but also stochastic (Weather driven spread)
-   Importance of spatial extent of system.
-   Potentially a different set of goals than in managing wildlife or crop
    systems
-   Importance of scale for management decisions (@Joao2012)

Modeling for management

-   Structured models to understand the system and scenario analysis
-   Unstructured approaches for forecasting
-   Combination needed for real-time decision-making
    -   Probabilistic component important

-   Confronting dynamics model with data - fitting data to individual components
    inadequate for complex system
