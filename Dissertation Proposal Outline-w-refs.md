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

Study System - Sudden Oak Death in Redwood/Tanoak/Bay Forests
=============================================================

-   Caused by water mold *Phytophthora ramorum* (Rizzo et al. 2002)
-   Spreads via wind-blown raid and fog, as well as human vectors (short- and
    long-distance dispersal) (Meentemeyer et al. 2011)
-   Dynamics dependent on forest composition:
    -   Wide host range, but lethality and transmissivity vary by host
    -   Lethal in tanak, spreads most widely from Bay Laurel, little effect or
        spread in Redwood and other species (DiLeo et al. 2009)
    -   Lethality varies by tree size (Cobb et al. 2012)

General Apparoch
================

-   Extend mechanistic model from Cobb et al. (2012) that incorporates disease
    and stand dynamics.
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
(WAIFW, Anderson and May (1985)) to get $\boldsymbol \Lambda$. There will be an
addition component of $\Lambda$ representing the force of infection from arrival
of spores from outside the stand.

Stochasticty will be incorporated into the model. Spore production and
transmission will be subjec to environmental stochasticity, and recruitment,
demographic transitions, and infection will be subject to demographic
stochasticity.

Essential topics and papers related to disease modeling
-------------------------------------------------------

-   SIR Models: Kermack and Mckendrick (1927), Kermack and McKendrick (1932),
    Kermack and McKendrick (1933), Anderson (1991)
-   Host heterogeneity: Anderson and May (1985)
-   Multispecies transmission: Dobson (2004), Craft and Hawthorne (2008)
-   Age-structured models: Metcalf et al. (2012), Klepac et al. (2009)
-   Plant-specific spatial models: Ferrari et al. (2006), Bolker et al. (2009),
    Gilligan and van den Bosch (2008)
-   Stochastic spatial spread: Lewis and Pacala (2000)
-   Kernels for spatial spread on a discrete grid: Chesson and Lee (2005)

The model selection process
===========================

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

Other Essential topics and papers related to model fitting
----------------------------------------------------------

-   Hartig et al. (2011) and Wood (2010) describe a summary statistic approach
    (Approximate Bayesian Computing), also implemented in the `pomp` package in
    R [@King2010]. An example in Martínez et al. (2011)
-   More theory about the approach in Andrieu et al. (2010)
-   If only distinguishing between a couple of models for hypothesis testing,
    might follow Boettiger and Hastings (2012)
-   General approach for forecasting, example from dynamic range models: Pagel
    and Schurr (2012)

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

-   An extension of the analysis above will include the parameter uncertainty of
    the best-fit model, and an optimization under the scenario that parameter
    uncertainties decrease with time

Topics and papers relevant to optimization
------------------------------------------

-   Optimal rotation under stochastic risk: Reed (1984)
-   Forestry with multiple age classes: Tahvonen (2004)
-   Optimal Management with risk of crossing uncertain thresholds: Polasky et
    al. (2011), Chen et al. (2012)
-   Risk minimization over time

References
==========

Anderson, R. M. 1991. Discussion: the Kermack-McKendrick epidemic threshold
theorem. Bulletin of mathematical biology 53:121–134.

Anderson, R. M., and R. M. May. 1985. Age-related changes in the rate of disease
transmission: implications for the design of vaccination programmes. J. Hyg.
Camb.

Andrieu, C., A. Doucet, and R. Holenstein. 2010. Particle Markov chain Monte
Carlo methods. Journal of the Royal Statistical Society: Series B (Statistical
Methodology) 72:269–342.

Arulampalam, M. S., S. Maskell, N. Gordon, and T. Clapp. 2002. A tutorial on
particle filters for online nonlinear/non-Gaussian Bayesian tracking. IEEE
Transactions on Signal Processing 50:174–188.

Boettiger, C., and A. Hastings. 2012. Quantifying limits to detection of early
warning for critical transitions.. Journal of the Royal Society, Interface / the
Royal Society 9:2527–39.

Bolker, B. M., M. E. Brooks, C. J. Clark, S. W. Geange, J. R. Poulsen, M. H. H.
Stevens, and J.-S. S. White. 2009. Generalized linear mixed models: a practical
guide for ecology and evolution.. Trends in ecology & evolution 24:127–35.

Chen, Y., C. Jayaprakash, and E. Irwin. 2012. Threshold management in a coupled
economic–ecological system. Journal of Environmental Economics and Management
64:442–455.

Chesson, P., and C. T. Lee. 2005. Families of discrete kernels for modeling
dispersal.. Theoretical population biology 67:241–56.

Cobb, R. C., J. A. N. Filipe, R. K. Meentemeyer, C. A. Gilligan, and D. M.
Rizzo. 2012. Ecosystem transformation by emerging infectious disease: loss of
large tanoak from California forests. Journal of Ecology.

Craft, M. E., and P. L. Hawthorne. 2008. Dynamics of a multihost pathogen in a
carnivore community. Journal of Animal …:1257–1264.

DiLeo, M. V., R. M. Bostock, and D. M. Rizzo. 2009. Phytophthora ramorum does
not cause physiologically significant systemic injury to California bay laurel,
its primary reservoir host.. Phytopathology 99:1307–11.

Dobson, A. 2004. Population dynamics of pathogens with multiple host species..
The American naturalist 164 Suppl :64.

Ferrari, M. J., O. N. Bjø rnstad, J. L. Partain, and J. Antonovics. 2006. A
Gravity Model for the Spread of a Pollinator-Borne Plant Pathogen. The American
Naturalist 168.

Gilligan, C. A., and F. van den Bosch. 2008. Epidemiological models for invasion
and persistence of pathogens.. Annual review of phytopathology 46:385–418.

Gimenez, O., J. D. Lebreton, J. M. Gaillard, R. Choquet, and R. Pradel. 2012.
Estimating demographic parameters using hidden process dynamic models.
Theoretical Population Biology 82:307–316.

Hartig, F., J. M. Calabrese, B. Reineking, T. Wiegand, and A. Huth. 2011.
Statistical inference for stochastic simulation models–theory and application..
Ecology letters 14:816–27.

He, D., E. L. Ionides, and A. a King. 2010. Plug-and-play inference for disease
dynamics: measles in large and small populations as a case study.. Journal of
the Royal Society, Interface / the Royal Society 7:271–83.

Ionides, E. L., C. Bretó, and a a King. 2006. Inference for nonlinear dynamical
systems.. Proceedings of the National Academy of Sciences of the United States
of America 103:18438–43.

Kermack, W. O., and A. G. McKendrick. 1932. Contributions to the mathematical
theory of epidemics. II. The problem of endemicity. Proceedings of the Royal
society of London. Series A 138:55.

Kermack, W. O., and A. G. McKendrick. 1933. Contributions to the mathematical
theory of epidemics. III. Further studies of the problem of endemicity.
Proceedings of the Royal Society of London. Series A 141:94.

Kermack, W. O., and A. G. Mckendrick. 1927. A Contribution to the Mathematical
Theory of Epidemics. Proceedings of the Royal Society of London. Series A:
Mathematical and Physical Sciences 115:700–721.

Klepac, P., L. W. Pomeroy, O. N. Bjø rnstad, T. Kuiken, A. D. M. E. Osterhaus,
and J. M. Rijks. 2009. Stage-structured transmission of phocine distemper virus
in the Dutch 2002 outbreak.. Proceedings. Biological sciences / The Royal
Society 276:2469–76.

Lewis, M. A., and S. Pacala. 2000. Modeling and analysis of stochastic invasion
processes. Journal of Mathematical Biology 41:387–429.

Martínez, I., T. Wiegand, J. J. Camarero, E. Batllori, and E. Gutiérrez. 2011.
Disentangling the formation of contrasting tree-line physiognomies combining
model selection and Bayesian parameterization for simulation models.. The
American naturalist 177:136.

Maunder, M. N., and R. B. Deriso. 2011. A state – space multistage life cycle
model to evaluate population impacts in the presence of density dependence :
illustrated with application to delta smelt ( Hyposmesus transpacificus ).
Canadian Journal of Fisheries and Aquatic Science 1306:1285–1306.

Meentemeyer, R. K., N. J. Cunniffe, A. R. Cook, J. a. N. Filipe, R. D. Hunter,
D. M. Rizzo, and C. a Gilligan. 2011. Epidemiological modeling of invasion in
heterogeneous landscapes: spread of sudden oak death in California (1990–2030).
Ecosphere 2:1–24.

Metcalf, C. J. E., J. Lessler, P. Klepac, A. Morice, B. T. Grenfell, and O. N.
Bjø rnstad. 2012. Structured models of infectious disease: Inference with
discrete data.. Theoretical population biology 82:275–282.

Pagel, J., and F. M. Schurr. 2012. Forecasting species ranges by statistical
estimation of ecological niches and spatial population dynamics. Global Ecology
and Biogeography 21:293–304.

Polasky, S., A. de Zeeuw, and F. Wagener. 2011. Optimal management with
potential regime shifts. Journal of Environmental Economics and Management
62:229–240.

Reed, W. J. 1984. The effects of the risk of fire on the optimal rotation of a
forest. Journal of Environmental Economics and Management 11:180–190.

Rizzo, D. M., M. Garbelotto, J. M. Davidson, G. W. Slaughter, and S. T. Koike.
2002. Phytophthora ramorum and sudden oak death in California: I. Host
relationships. Pages 733–740 *in* Fifth Symposium on Oak Woodlands: Oaks in
California’s Changing Landscapes. . USDA Forest Service, San Diego, CA.

Tahvonen, O. 2004. OPTIMAL HARVESTING OF FOREST AGE CLASSES: A SURVEY OF SOME
RECENT RESULTS. Mathematical Population Studies 11:205–232.

Wood, S. N. 2010. Statistical inference for noisy nonlinear ecological dynamic
systems.. Nature 466:1102–4.
