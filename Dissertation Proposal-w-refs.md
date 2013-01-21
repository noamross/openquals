% Forest Disease Dynamics and Management
% Noam Ross
% 13-01-21 13:40:28

Abstract
========

Forest disease spreads through plant communities structured by species
composition, age distribution, and spatial arrangement. Each of these types of
population structure have known effects on the outcomes and transient dynamics
of disease, but their effects . Optimal management of such disease requires
estimates of the time-dependent risk of disease outbreak in such communities.
Using the study system of *Phytophthora ramorum* spread in Redwood forests of
Northern California, I propose to examine how these elements of population
structure interact to determine the dynamics of disease spread. I determine the
types of structure most important for predicting outbreaks in forests. With such
predictions, we can determine optimal silvicultural treatments for minimizing
the outbreak of disease.

Introduction: Modeling Disease in Complex Populations for Management
====================================================================

Forest diseases can radically transform ecosystems. In North America, chestnut
blight, Dutch elm disease and beech bark disease have caused precipitous
declines in their hosts, leading to changes in the structure and function of
forests. Changes from such diseases may be the dominant force changing the face
of some forests in coming decades, overwhelming other forms of rapid
environmental change such as climate change (Lovett et al. 2006).

Even simple host-disease systems exhibit complex dynamics(Kermack and Mckendrick
1927). Forest disease dynamics include additional complexity driven by variation
in pathogen and host populations, pathogen life cycles, and demographic and
environmental stochasticity (Hansen and Goheen 2000, Holdenrieder et al. 2004).
These factors yield greater complexity in disease dynamics. This complexity,
combined with limited monitoring data and the novelty of emergent diseases,
makes prediction of disease dynamics difficult. Yet such prediction is needed
for long-term management of disease.

Quantitative disease forecasts are essential for optimal management.

One area of complexity in forest systems is structured variation in host
populations. Host tree populations may consist of multiple species or genotypes,
and consist of multiple sizes, each of which may interact with disease or each
other differently [@REF]. All forest tree populations are spatially structured;
non-motile individuals can not be "well-mixed". Each of these forms of
population structure have consequences for population dynamics that have been
examined in theoretical models [@REFS]. However, the interaction of these
components of population structure are not well-characterized.

Modeling multidimensional population structure is problematic for several
reasons. First, as models get increasingly complex, analytic solutions are less
likely to be tractable, and complete characterization of model behavior is
unlikely. Thus model (and) system behavior is more difficult to explore.
Secondly, high-dimensional models are difficult to estimate; each additional
form of population structure multiplies the parameters involved, and requires
additional data.

Thus, selection of a parsimonious model for predictive managemnent has two major
components. From a theoretical perspective, which components of population
structure are most important for determining the relevant components of
population dynamics? And what model is most parsimonious for purposes of
prediction? The first question provides a universe of models from which to
answer the second.

Such models give us the ability to mechanistically explore alternative
management models with some level of confidence. Models with both adequate
mechanistic structure and predictive power are required for optimal management.

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

Overall Questions
-----------------

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

Background
==========

Sudden Oak Death
----------------

-   Caused by water mold *Phytophthora ramorum* (Rizzo et al. 2002)
-   Spreads via wind-blown raid and fog, as well as human vectors (short- and
    long-distance dispersal) (Meentemeyer et al. 2011)
-   Dynamics dependent on forest composition:
    -   Wide host range, but lethality and transmissivity vary by host
    -   Lethal in tanak, spreads most widely from Bay Laurel, little effect or
        spread in Redwood and other species (DiLeo et al. 2009)
    -   Lethality varies by tree size (Cobb et al. 2012)

Sudden Oak Death (SOD) is an emerging forest disease in California and Oregon
that poses risks to forest across North America. First observed in California in
the mid-1990s, SOD is caused by the water mold *Phytophthora ramorum* (Rizzo et
al. 2002a). *P. ramorum* often kills tanoak (Notholithocarpus densiflorus),
which provide habitat and food to many vertebrate species, and are the primary
host of ectomycorrhizal fungi in redwood forests (Rizzo and Garbelotto 2003).
Loss of this species may have cascading effects on other species. The disease
has also caused significant economic damage through removal costs and property
value reduction (Kovacs et al. 2011). It has the potential to spread to species
in other regions, such as northern red oak (Quercus rubra), one of the most
important eastern timber species (Rizzo et al. 2002b).

Disease in Structured Populations
---------------------------------

Description of population structure and disease

-   Contact structure 1 - tanoak-bay
-   Contact structure 2 - size pop
-   Contract structure 3 - space and dispersal kernel

How the $G'$ matrix changes in each of these circumstances

Approximations in long-distance work.

Study Approach
==============

-   Extend mechanistic model from Cobb et al. (2012) that incorporates disease
    and stand dynamics.
-   Build series of nested models of varying complexity that incorporate
    -   Species differences in demographic and epidemiological parameters
    -   Size structure in demographic and epidemiological parameters
    -   Spatial structure

-   How does inclusion of each component of structure modify
    -   $R_0$ (global and local)
    -   Epidemic size
    -   Probability of outbreak
    -   Time to extinction of tanoak and *P. ramorum*.

-   Compare models to determine best predictor of disease outbreak
-   Determine optimal combination of host- (harvesting) and pathogen-centric
    (spraying) controls over management periods, given constraints, to minimize
    probability of disease outbreak

Nested Models
-------------

Table 1: Model Structures

-   Mean field
-   Mean field with species classification
-   Mean field with size classification
-   Mean field with species and size classification
-   Spatially explicit
-   Spaitally explicit with species classification
-   SE with size class
-   SP with size class and species

Use Klepac and Caswell (2010) structural framework, extended to include multiple
species *and* life stages.

-   Multinomial draws for transition stochasticity
-   Poission distributions for births
-   Environmental stochasticity - what does this most effect?
    -   Spore distribution/creation

Contact Structures
------------------

Contact rates in SOD are not driven by differential mixing of groups, but of 3D
structure and differing physiological response of the disease. Inter-species
studies have mostly focused on (symmetrical) contact structures where
within-group contact rates exceed intra-group contact rates, or assymetric
contact rates simulating rare jumps between species.

-   Observational stochasticity
    -   Binomial observation probability
    -   Ask Richard - what do we think false positive and negative rates are
        like?

Model Fitting and Selection
---------------------------

**Goal**: Indentify the most parsimonious model structure for predicting the
spread of disease and mortality through the forest stand

Model fitting
-------------

-   Model data as a *hidden Markov process* (Gimenez et al. 2012)
    -   Smallest size classes (seeds, seedlings) unobserved
    -   Disease observations imperfect - binomial process with underlying
        probability dependent on tree class and disease status

-   With likelihoods for the mechanistic model intractable, likelihoods can be
    calculated using particle filtering (Arulampalam et al. 2002)
-   Maximum likelihood estimates of parameters calculated using *iterated
    filtering* (Ionides et al. 2006, He et al. 2010)

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
    AICc weight (following Maunder and Deriso (2011))

Two possible methods may be used, depending on computational efficiency or,
*iterated filtering* (Ionides et al. 2006, IF) or *particle filter MCMC* (Knape
and de Valpine 2012, PFMCMC). Particle filtering methods provide unbiased
estimates for dynamic state space models. IF determines the maximum likelihood
fit by approximating a random walk of the parameters. PFMCMC uses an MCMC to
find the maximum likelihood, utilizing particle filtering at each step.

Model selection has multiple purposes. First, to determine which model best is
most like the true purpose, and to estimate the valdiity of the models for the
purposes of prediction. DIC has several advantages. First, it incoporates any
random variables. Secondly, it estimates the loss of parameters from Bayesian
inference. As several components of the model have useul priors estimated form
either data sets, this is useful in this case.

### Data

Data to fit the model comes from a collaboration with the Rizzo lab's diease
monitoring plot network. The data consist of 14 sites, each of which contains
X-X plots, seperated by minimium distances of Z. Size, health, and disease
status of all trees were measured in 2002 and 2007, as well as for a ramble
sample of 5 trees of each species in the years 2003-2006. Disease status was
measured by asessing sympotoms in the filed, and confirmign with molecular
methods. Observations are thus probibalistic, with a binomial distribution.

Optimization
------------

Arulampalam, M. S., S. Maskell, N. Gordon, and T. Clapp. 2002. A tutorial on
particle filters for online nonlinear/non-Gaussian Bayesian tracking. IEEE
Transactions on Signal Processing 50:174–188.

Cobb, R. C., J. A. N. Filipe, R. K. Meentemeyer, C. A. Gilligan, and D. M.
Rizzo. 2012. Ecosystem transformation by emerging infectious disease: loss of
large tanoak from California forests. Journal of Ecology.

DiLeo, M. V., R. M. Bostock, and D. M. Rizzo. 2009. Phytophthora ramorum does
not cause physiologically significant systemic injury to California bay laurel,
its primary reservoir host.. Phytopathology 99:1307–11.

Gimenez, O., J. D. Lebreton, J. M. Gaillard, R. Choquet, and R. Pradel. 2012.
Estimating demographic parameters using hidden process dynamic models.
Theoretical Population Biology 82:307–316.

Hansen, E. M., and E. M. Goheen. 2000. Phellinus Weirii and other Native Root
Pathogens as Determinants of Forest Structure and Process in Western North
America. Annual review of phytopathology 38:515–539.

He, D., E. L. Ionides, and A. a King. 2010. Plug-and-play inference for disease
dynamics: measles in large and small populations as a case study. Journal of the
Royal Society, Interface / the Royal Society 7:271–83.

Holdenrieder, O., M. Pautasso, P. J. Weisberg, and D. Lonsdale. 2004. Tree
diseases and landscape processes: the challenge of landscape pathology.. Trends
in ecology & evolution (Personal edition) 19:446–52.

Ionides, E. L., C. Bretó, and a a King. 2006. Inference for nonlinear dynamical
systems. Proceedings of the National Academy of Sciences of the United States of
America 103:18438–43.

Kermack, W. O., and A. G. Mckendrick. 1927. A Contribution to the Mathematical
Theory of Epidemics. Proceedings of the Royal Society of London. Series A:
Mathematical and Physical Sciences 115:700–721.

Klepac, P., and H. Caswell. 2010. The stage-structured epidemic: linking disease
and demography with a multi-state matrix approach model. Theoretical Ecology
4:301–319.

Knape, J., and P. de Valpine. 2012. Fitting complex population models by
combining particle filters with Markov chain Monte Carlo.. Ecology 93:256–63.

Lovett, G. M., C. D. Canham, M. A. Arthur, C. Kathleen, R. D. Fitzhugh, and K.
C. Weathers. 2006. Forest Ecosystem Responses to Exotic Pests and Pathogens in
Eastern North America. BioScience 56:395–405.

Maunder, M. N., and R. B. Deriso. 2011. A state – space multistage life cycle
model to evaluate population impacts in the presence of density dependence :
illustrated with application to delta smelt ( Hyposmesus transpacificus ).
Canadian Journal of Fisheries and Aquatic Science 1306:1285–1306.

Meentemeyer, R. K., N. J. Cunniffe, A. R. Cook, J. A. N. Filipe, R. D. Hunter,
D. M. Rizzo, and C. a Gilligan. 2011. Epidemiological modeling of invasion in
heterogeneous landscapes: spread of sudden oak death in California (1990–2030).
Ecosphere 2:1–24.

Rizzo, D. M., M. Garbelotto, J. M. Davidson, G. W. Slaughter, and S. T. Koike.
2002. Phytophthora ramorum and sudden oak death in California: I. Host
relationships. Pages 733–740 *in* Fifth Symposium on Oak Woodlands: Oaks in
California’s Changing Landscapes. . USDA Forest Service, San Diego, CA.
