% Forest Disease Dynamics and Management - Outline
% Noam Ross
% 12-12-12 12:00:06

Overall Questions
=================

-   How does forest disease spread through forest systems?
-   What aspects of forest structure (species composition, age and spatial
    strucuture) are important in predicting the spread and impact of disease?
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

General Approach
================

-   Extend mechanistic model from @Cobb2012 that incorporates disease and stand
    dynamics.
-   Build series of nested models of varying complexity that incorporate
    -   Species differences in demographic and epidemiological parameters
    -   Size structure in demographic and epidemiological parameters
    -   Density dependence on recruitment, growth, and mortality
    -   Shape of spore dispersal kernel

-   Compare models to determine best predictor of disease outbreak
-   Determine optimal combination of host- (harvesting) and pathogen-centric
    (spraying) controls over management periods, given constraints, to minimize
    probability of disease outbreak

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

References
==========
