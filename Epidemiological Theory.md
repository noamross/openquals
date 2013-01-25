% Quals Reading: Epidemiological Theory
% Noam Ross
% 13-01-03 13:48:56

A core topic for my exam: epidemiological theory.

@Gilligan2008
=============

Summary
-------

-   Models help answer major questions in plant epidemiology, particularly
    related to scale, control, invasion and persistence.
-   Invasion require introduction and presistence, occurs is $R_0$ \> 1
-   Persistence requires steady supply of susceptible hosts
-   $R_0$ is the growth rate of infection cases, and is the invasion criterion
    across many different disease model structures
    -   Nonlinarity and stochasticity introduce other thresholds for invasion

-   Spatial division of the host population limits the effective number of hosts
    for invasion, reduing $R_0$
    -   Protection of a limited number of sites can confer spatial "herd
        immunity"

-   Persistence is inherently a stochastic process, because it involves small
    numbers near extinction. It is often summarized using extinction times.
    -   (Partial) Spatial division can increase persistence through the "rescue
        effect"

Intro
-----

-   Major questions in epidemiology
    1.  Why do some diseases take off, whereas others do not?
    2.  Why do some strains, races, or pathotypes die out, coexist, or come to
        dominate pathogen populations?
    3.  How does inherent variability associated with epidemics translate to
        risk?
    4.  How do we scale from invidividual inection scale to population epidemic
        scale?
    5.  How can this information be used to optimize control mechanisms?
    6.  How does the way we manage populations affect outcomes?

Concepts for invasion and persistence
-------------------------------------

**Invasion** is *introduction* plus *increase* of a pathogen in the host
population. Basically, this occurs if one infected unit gives rise to more than
one infected unit during its infectious period. **Persistence** require a
sufficient supply of susceptibles to maintain both pathogens and hosts.

SI models can be extended to SIR, or including $E$ (exposed) and/or $D$
(detected/sympotomatic classes). Inoculum may be repesented, as well, often as
$X$.

Invasions occur through processes that occur at many scales, but the common S/I
mathematical frameowrk can work across scales. Individuals can be infected, but
also fields, or tissues. Control should be matched to the scale of the infection
process.

\$\$ Criteria for invasion

Criteria for invasion are functions of host density at time of invasion.

For an SIR model with a logistic growth rate for hosts, the carrying capacity
must be large enough $(\kappa > \mu / \beta)$ for the pathogen to invade. That
is:

\$\$R\_0 = \frac{\Beta \kappa}{\mu}

In addition to $R_0$, we can also derive $R_\infty$, the final level of removed
individuals.

$$R_\infty = 1 - e^{-R_0 R_\infty}$$

Another criterion is the stability of the pathogen-free host population. If it
is unstable, a small amount of inoculum may have a large effect even if
$R_0 < 1$

$R_0$ has been derived as the expected number of offspring for an individual,
across the distribution of lifetimes:

$$R_0 = \int_0^\infty b(\tau) F(\tau) d\tau$$

Where $b$ is the average number of infections per unit time, and $F$ is the
probability of surviving to time $\tau$.

$R_0$ is robust to a lot of complexity. Adding a latent period does not normally
influence it, as long as hosts become infectious before dying. Host dynamics
don't affect it *as long as the host population is above the invasion threshold
level*. Secondary infection changes $R_0$ and makes a pathogen more invasive, as
does parent-to-offspring and sibling-sibling infection.

With nonlinear transmission
$(\text{Transmission } = \beta \times I^m \times S^n)$, representing complicated
spatial interactions, pathogen density is important as well as host in
determining $R_0$. In this case, the pathogen itself has a population Allee
threshold. Another similar case is when low levels of infection stimulate
growth, but high levels inhibit growth.

For (demographic) stochastic models, invasion thresholds identify a point below
which invasion does not occur, but above which it *may* occur, with varying
probability. Whittle and Bailey both show that initial infection results in
extinction of the pathogen with probability $q$:

$$q = \begin{cases}
    \mu/\beta n && n > \mu/\beta \\
    1 && n \leq \mu / \beta 
    \end{cases}$$

Environmental stochasticity is different, but can be used to link
climate/weather data with epidemiological models. Analytically, they are
approached by Sdes of Fokker-Planck equations.

$R_0$ and space
===============

Four ways to model space:

1.  Grids with nearest-neighbor contact
2.  Networks
3.  Continuous landscape with dispersal kernels
4.  Metapopulations with subpopulations

For $Z$ nearest neighors, $R_0 = \beta Z / \mu$

For continuous space with power-law dispersal, $R_0$ still holds, but its
magnitude is decreased by disperal. See papers by Filipe & Maule.

In a spatially explicit system, the availability of hosts in a locality can
limit the growth rate of the pathogen. The asymptotic $R_0$ reflects the network
structure and parameters.

For metapopulations, Park et. al.'s approximation of $R_0$ is

$$R_0 = R_P (1 + z \varepsilon)$$

Where $R_P$ is the sub-population $R_0$, $z$ is the number of patches and
$\varepsilon$ the strength of coupling (0-1), the ratio of within- to
between-patch transitions.

Percolation, or spread across a lattice, involves multiplicative probabilities
of spread between each point. At critically low probabilities (or host
distnaces), spread is suppressed. Protecting some set of sites can increase the
effective distance betwen sites.

Invasion criteria and control strategies
========================================

Both deterministic and stochastic models show one doesn't have to protect all
hosts to protect the herd. The herd immunity threshold is $p$:

$$p = 1 - \frac{1}{R_0}$$

From this result folows the idea that host heterogeneity can reduce the
probability of invasion. As can gaps in the dispersal landscape, even temporary
ones.

Major areas for future research on $R_0$

-   The assumption that the pathogen invades an equilibrium population
-   That no resident pathogens are displaced.
-   Practical ways of estimating R\_0 for real populations
-   Dynanmic optimization
-   Eco-evolutionary changes

Criteria for persistence
------------------------

Persistence is an essentially stochastic process, because it involves low levels
of pathogen. These are often described by extinction times. The mean extinction
time is a function of population:

$$T_E = a \ln N$$

For metapopulations, the "rescue effect" can extend $T_E$. For a two-dimensional
metapopulation grid:

$$T_E = a \ln N + bn^{1/2}$$

Here, the force of infecton on patch $j$ is

$$\lambda_j = \beta I_j + \varepsilon \beta \sum_{k \in \text{neighbors}} I_k$$

Rescue effect is most important when patch populations are large enough to
spread to adjacent patches, but small enough where rescue is still relevant.

Some practical applications
---------------------------

### Dutch Elm

Dutch Elm pandemic was due to a more virulent strain outcompeting a
low-virulence one, and models were used to develop controls of re-introducing
hypovirulent versions.

The fungus grows in beetle galleries in dead trees. Beetles spread it to live
trees and it kills them.

In the model, $R_0$ was independent of the lethality of the disease, but
depended on the equilibrium density of healthy and dying trees in the absence of
disease. Also, there was a minimum threshold of disease level for invasion.

An extended version of the model included competition between genotypes to
examine optimal control scenarios. These showed that compeitive exclusion is
driven by transmissilibility rather than lethality, showing that a non-lethal
type could compete successfully.

The models also identified four possible equilibria between the compeitive
strains: disease free, competitive exclusion of either, or exclusion. These are
divided by different $R$ values. Horizontal transmission (between hosts at the
same life stage infected with different diseases) is required for coexistence.

Stochastic models showed that high horizontal transmission leads to extinction
of both species, so it leads to successful invasion of the control but also
extinction eventually. It a metapopulation, this makes control tougher, because
the control must persist to spread among populations.

### Rhizomania

Rhizomania is a beet disease caused by a soil-borne virus that is transmitted by
bacteria. It persists for \>30 yrs in soil. Symptoms do not appear until a
threshold bacterial density is reached, usually over several seasons of
amplification, during which dispersal also occurs.

An SID model at the field level showed that local control (field containment)
failed because of the lag between infection and control. Instead, the better
strategy was to stop production in fields adjacent (or adjacent-adjacent) to
infected fields. Efficiency of control fell if fields further away were retired.

### Selection of disease strains

Viruse strains build up antibody concentrations (titers) within crops, so
selection for crop resistance may also also select for different titer levels,
which may result in different effects at the population level.

van den Bosch found that the evolutionary stable titer level would be low enough
to successfully infect cells but high enough to become highly transmissible due
to its high concentrations in the hosts (and therefore vectors). Selecting for
tolerance in the plants increases the optimal titer, but not for transmission
resistance.

@Anderson1985 - Age Structure in SIR Models
===========================================

-   SIR models should account for age structure in (a) epidemiological
    parameters, and (b) heterogenous mixing of populations
-   Epi theory suggests that while infection is endemic, the density of
    susceptibles will remain constant. The critical level of herd immunity for
    eradication is then $1-S_0$, Where $S_0$ is the pre-vaccination proportion
    of susceptibles.
-   Vaccination campaigns may have age-related effects
-   Force of infection on a class depends on both contact rate and infection
    level with/in other age classes

Model structure without age dependence
--------------------------------------

-   SEIR, age-dependent, continuous in both time and age
-   Mass action assumed, transition rates constant
-   Mortality occurs at age $L$ for all
-   Force of infection is

    $$\lambda(t) = \beta \int_0^L I(a,t) \, da$$

-   At equilibrium, the proportion susceptible at age $a$ is
    $s(a) = e^{-\lambda a}$
-   $R_0$ is approximated by the age at mortality divided by the average age at
    first infection, as long as the age is low.
    -   Average age at infection is negatively related to $R_0$ or force of
        infection. Thus, immunization increases the average age of first
        infection.

-   At equilibrium, $R_0 S_eq =1$. Since the number immune is $p$ or $1-S_eq$
-   Thus, to keep $R_0 < 1$, $p \geq 1 - 1/R_0$
-   If immunization occurs at age $V$, this is $p \geq \frac{1-1/R_0}{1-V/L}$
-   Immunization acts to reduce force of infection *not* by reducing
    susceptibles, but by reducing density of infectious individuals

Age-dependent rates of infection
--------------------------------

    $$\lambda(a,t) = \beta(a',a) \int_0^L I(a',t) \, da'$$

In this case $\beta$ represents the probability of contact between two classes
*and* the likelihood transmission occurs due to this contact ("who acquires
infection from whom", or WAIFW). Both may be related to age.

A two age-class model
=====================

Since each age class is a much shorter time span than the time of infection, it
can be shown that $I_i \approx \frac{S_i \lambda_i}{\gamma}$, where $\gamma$ is
$\text{infectious period}^{-1}$

The age-specific $R_{0i}$ is the number of *total* infections spawned by an
infectious casein age class $i$:

$$R_{0i} = \frac{1}{\gamma} \int_0^L \beta{a,i} N(a) \, da$$

Where $N(a)$ is the total individuals of age $a$.

It is difficult to calculate $\boldsymbol{\beta}$ because typically, if we only
know populations and forces of infection, there are more unknown $\beta$'s than
equations. However, in practice many of the elements of $\boldsymbol{\beta}$
will be identical.

Case-by-case examination in a 2-class model
-------------------------------------------

-   Some configurations of $\boldsymbol{\beta}$ are not possible
-   If the force of infection is greater on the younger class, the critical
    proportion to be immunized is *less* than the proportion of immunes at
    equilibrium in the unvaccinated population, not equal as in the
    age-independent case. The reverse is also true, and it is independent of the
    configuration of $\boldsymbol{\beta}$. This is because vaccination increases
    the average age at infection. **TODO: Include in proposal**
-   Average age of infection is determind by the forces of infection, and
    independent of $\boldsymbol{\beta}$.

Empirical Results
-----------------

-   Using serological data, you get the cumulative distribution of infection
    rates by age, from which $\lambda_i$ can be calculated as

    $$\lambda_i = \ln \left( \frac{1 - p_{i+1}}{1-p_i}\right)$$

-   Scottish data indicate that immunization has increased average age at
    infection
-   This pattern holds in other data sets
-   However, some of this pattern may be due to reporting patterns.
-   In virgin populations, age structure in force of infection is less dramatic

Age-independent heterogneity in susceptibility/exposure
-------------------------------------------------------

-   When two groups have different susceptibility, the more susceptible get it
    ealier, the less susceptible later and some may not get it at all. If these
    groups are mixed together, it would suggest strong age-dependency, though
    there is no actual age structure in force of infection.

Vaccination programs for measles.
---------------------------------

-   Identifiability if The WAIFW is structured to have nove more than $n$ unique
    values. **TODO: Put in model options**
-   If force of infection is extremely low in adult age class, vaccination
    coverage can be reduced.

WAIFW Matrix configuration and short-term disease dynamics
----------------------------------------------------------

-   Realistic matrix structures can accentuate oscillatory paterns.

# @Metcalf2011 - Inference with Structured Disease Models

## Introduction

-   It's tough to fit structured models to data due to coarseness of
    scale-incompatibility of data
-   Rubella case study
    -   In unstructured model analysis, low enough $I_eq$ must be reached via
        vaccination to offset rise in average age of infection

Structured model
----------------

-   Discrete-time, M(immune)SIRV(vaccinated), age-structured
-   Time step is one disease cycle, so $I \rightarrow R$ is 1.
-   Force of infection is function of the population vector, $\beta$.
    Nonlinearity in contact represented by $I^\gamma$ rather than just $I$ in
    infection term **TODO: incorporate in model options**
-   $R_0$ is dominant eigenvalue of next-generation matrix (at $\gamma = 1$, see
    @Klepac2010)
-   Stochastic, using draw from multinomial distribution for advancement,
    poisson for births, and a stochastic Poisson introductions of infected
    individuals

Parameterization
----------------

-   Several parameters (birth rate, life expectancy), changed over course of
    time period, but this was incorporated
-   Calculated force of infection with the "catalytic" model:

$$P(a) = 1 - \exp \left[ -\int_0^a \lambda (a) \, da \right]$$

**TODO**: Note that relative time period of disease is long compared to
lifetimes in SOD system, violates many epidemiological assumptions. - Calculated
a WAIFW matrix by using European structure, scaling so that $R_0$ matched
empirical estimates

(Note, read Klepac, P., Caswell, H., 2010. The stage-structured epidemic:
linking disease and demography with a multi-state matrix approach. Theoretical
Ecology 4, 301–319.

Simulation
----------

-   Simulated pre-vaccination stationary distribution, then introduced
    vaccination.

Perturbation analysis
---------------------

-   Following @Caswell2007, performed perturbation analysis. (See eq.9, p. 5 for
    equation for $\frac{d(\boldsymbol{n} +1 }{d\theta}$
-   At low coverage, reducing birth rates makes it harder to reduce the burden
    of disease, because vaccinated individuals aren't getting into the
    population fast enough
-   **TODO: Question: how important is age structure, anyway?**
    -   Interesting question: Should you kill all the tanoak and then restore
        them after the disease is gone? What about Bay? Will it reside in the
        other, less important foliar hosts?

@Klepac2010
-----------

Introduction
------------

-   Disease and demographic transitions are dependent
-   For many diseases, demographic stages other than age may be important
-   Separate disease and demographic transition matrices, linked using
    vec-permutation, produce a periodic matrix model as processes alternate
    within a period.

Model structure
---------------

-   Individuals classes in $s$ stages and $c$ infection states
-   $\boldsymbol{N}(t)$ is the $s \times c$ population matrix, which is
    transformed into a vector $\boldsymbol{n} = \text{vec} (\boldsymbol{N})$ by
    stacking columns (or $\boldsymbol{m} = \text{vec} (\boldsymbol{N}^T)$,
    stacking rows). $\boldsymbol{n}'$ is an intermediate vector with an extra
    stage of newborns, length $(s+1)c$
-   Demographic dynamics within an infection category are given by a transition
    matrix designated $\boldsymbol{R}_i$, of dimension $(s+1) \times s$,
    designating newborns as distinct from juveniles for purposes of maternal
    immunity, etc.
-   Demographic transitions are by
    $\boldsymbol{n}'(t) = \mathbb{R} \boldsymbol{n}(t)$, where $\mathbb{R}$ is a
    block diagonal matrix of all $\boldsymbol{R}$ matrices
-   In their model, there are parental effects, in that offspring of parents of
    different disease classes have varying disease class probabilities. The
    matrix $\boldsymbol{G}$ represents these probabilitiesn and is $c \times c$.
    It is used to update the population vector after the demographic transition.
-   Disease transitions are described by
    $$m = \mathbb{A}[\boldsymbol{m}] \boldsymbol{m}(t)$$ Where $\mathbb{A}$ is a
    diagonal block matrix of $\boldsymbol{A}_i$, which describe transitions
    among infection states. Note that this includes the force of infection which
    may be a function of all classes
-   The total model is
    $$\boldsymbol{t+1} = \boldsymbol{K}_{s,c}^T \mathbb{A}[\boldsymbol{m} \mathbb{M} \boldsymbol{K}_{s+q,c} \mathbb{R} \boldsymbol{n}(t)$$
-   **TODO** My model will have a similar structure, but will leave out the
    maternal effects component.
-   Note that this model can be structured for the disease and demographic
    transitions to occur at different scales. See 'periodic matrix models' in
    @Caswell2001.

$R_0$ for the stage-structured epidemic
=======================================

Invasion of disease occurs in the disease free population \$\hat{\boldsymbol{n}}

$$\hat{\boldsymbol{n}} = \begin{pmatrix} \hat{\boldsymbol{n}}_S \\ 0 \\ 0   \end{pmatrix}$$

$\hat{\boldsymbol{n}}$ may or may not be an equilibrium. Now we are only
interested in $\boldsymbol{n}_I$ to determine this, which can be described as
$$\boldsymbol{n}_I(t+1) = \boldsymbol{Y[n] n_I}(t) + \boldsymbol{X[n] n}_S + \boldsymbol{Z[n] n}_R$$
where $\boldsymbol{X,Y,Z}$ are parts of the matrix created in the main model
equation. We linearize to calculate
$$J = \frac{d\boldsymbol{n}_I(t+1)}{d\boldsymbol{n}_I (t) } \bigg|_\boldsymbol{\hat{n}}$$
The dominant eigenvalue of $\boldsymbol{J}$\$ is similar but not exactly $R_0$
(though they assume it is in @Metcalf2011).

-   We can decompose $\boldsymbol{J}$ into $\boldsymbol{F+U}$, production of new
    individuals and new transmissions. Note that
    $\boldsymbol{U} = \boldsymbol{J}|_{\beta=0}$, because $\beta > 0$ is require
    for new transmissions. Finally,

$$R_0 = \max \text{eig} \left(\boldsymbol{F} (\boldsymbol{I-U})^{-1}\right)$$

Dynamics
--------

If $R_0 > 1$, but reduces the population, there can be an equilibrium on the
annual time scale, though there is an oscilation within the year between the
growth and disease seasons.

Perturbation analysis
---------------------

Use matrix calculus to calculate the sensitivity matrix. This is some crazy.

$$\frac{d\boldsymbol{\hat n}_i }{d\boldsymbol{\theta}^T }$$

Sensitivity to age distribution.
--------------------------------

Consider the equilibrium prevalance of disease to be:

$$\hat{P} = \frac{\boldsymbol{a^T \hat n} }{\boldsymbol{b^T \hat{n}} }$$

Where $\boldsymbol{a,b}$ are vectors that depend on what measure of $P$ (total
or stage-specific) you want. Perturbation analysis of this is also possible.

**TODO: Perturbation analyses of the SOD model. How about reactivity**

An example model
----------------

-   2 stage, SIR.
-   2 $\beta$ values, one for intra- and onother inter-stage contact
-   Parameters result in exponential growth initially, equilibrium with disease
-   See example of perturbation analysis
    -   Increased $\beta$'s reduce prevelance of most stages, increases in
        stage-specific transmission lead to increase prevelance in that stage

Multiple time scales
====================

-   When outbreak is on short time scale, model by multiple infection transition
    matrices $(\Delta t < 1)$ between demographic transitions.
-   In example, parameters are kept the same, but divided by number of disease
    intervals in one demographic interval
-   Annual results qualitatively similar, but intra-annual results show
    oscillations.
-   Sensitivities of population levels to parameter a much greater, though
    elasticities are similar.
-   Note that in both models sensitivity to disease parameters greater than
    demographic, but elasticities greater for demographic parameters than
    disease

@Klepac2009 - Empirical Fitting of a Stage-Structured Outbreak Model
====================================================================

-   Goal of fitting series of models to outbreak data, estimate WAIFW, and
    calculate $R_0$
-   Phocine disteper virus (PDV) affects seals in the North Sea rgion, causing
    mass mortality. Has latent and infectious stages
-   Fit 3-stage SIR model
-   Tried four different configurations of $\boldsymbol{\beta}$
    -   Homogenous
    -   Strongeest within stages (2 values, on the diagonal and otherwise)
    -   Heteogenous but symmetrical
    -   Frequency and density-dependent transmission

-   Demographic parameters derived from literature, epidemiological ones derived
    from data using maximum-likelihood, with a Poisson model for observation of
    diseased seals
-   Best f it model (via AIC) had heterogenous mixing and density dependence

@Holt2003 - Parasite establishment in host communities
======================================================

-   For initial establishment, assuming constant host population and infected
    loss rate $\Gamma$, $$R_0 = e^{\beta S/\Gamma -1}$$
-   The minimum host density for parasite invasion is where $R_0 = 0$, or
    $$N_T = \frac{\Gamma}{\beta}$$
-   For multiple hosts, rather than a threshold $N_T$, there should be zero
    net-growth isoclines. Their shape depends on if the hosts are
    -   Noninetractive
    -   Substitutable
    -   Complementary (or alternating, *requiring* both species)
    -   Weakly interacting, or
    -   Inhibitory (where one host is a "sink")

**TODO: Ask - is SOD complementary or substitutable w.r.t. Tanoak and Bay
Laurel?)**

@Dobson2004
===========

-   Multi-species continuous-time SIR model, with each species having density
    dependence but no competitive interactions aside from disease transmission.
-   $\beta_{ij}$ values are assumed to be the average of $\beta_{ii}$ and
    $\beta_{jj}$, adjusted by a scaling constant $c_{ij}$. $c$ is constant
    across species in the model, allowing simple adjustment of relative between-
    and within-species transmision.
-   $c_{ij}$ can reflect spatial arrangement, physiological components, may be
    symmetrical or assymetrical

$R_0$ For Multiple Hosts
------------------------

**TODO: Open question for Cobb/Rizzo. Do Bay trees ever lose their infection? I
guess also a question for the data**

Let $\boldsymbol{G}^1$ be the matrix of $\beta$ values times the duration of
infection times $p_{ij}$, which is 1 in the case of frequency-dependent
transmission, equal to density $\times$ proportion of contacts in
density-dependent transmission, and equal to vector density $\times$ proportion
of contacts with vector. So $\boldsymbol{G}^1$ is a matrix of transmission
probabilities, not just contact rates.

The dominant eigenvalue of $\boldsymbol{G}^1$ is equivalent to the reproductive
rate of $R_0$

-   With density-dependent transmission, increased abundance of either species
    increases $R_0$. With frequency-dependent, $R_0$ decreases until one species
    is dominant, then increases. Vector-transmitted are similar to
    frequency-dependent.

Scaling parameters by allometry for multiple species
----------------------------------------------------

-   Epidemiological parameters tend to scale with body size in vertebrates. With
    this assumption we can construct artificial communities
-   In these communities $R_0$ increases with diversity is density dependent
    communities, and the reverse for frequency-dependent, assuming interspecies
    transmission is less that intraspecies transmission

Asymmetrical Matrices and Pathogen Emergence
--------------------------------------------

-   Where transmission is unidirectional, the uppen diagonal of the matrix is
    empty, and the dominant eigenvalue is the largest of the diagonal terms.\
-   Essentially three independent epidemics

Transient dynamics
------------------

-   If interspecies transmission is low, outbreaks will occur periodically at
    same rate as would absent other species
-   As interspecific transmission increases, cycles are buffered, then settle
    into constant levels. With very high transmission, those that recover
    quickly drive the others extinct. Similar dynamics in frequency and
    density-dependent models.
-   Multiple species likely enhance disease persistence

@Craft2008
==========

-   Stochastic multihost SIR model of Sergengeti Carnivores
-   Spatially explicit - different population of all 3 in each grid cell
-   Each species has within- and across-cell transmission, parameterized based
    on their social structure
-   Between-species contact was varied.\
-   Species (hyenas) with strongest across-cell transmission (fluid social
    structure) had highest number of infections
-   Coupling species increased infections in low-contact species (Lions) because
    of repeatd infections from others. More connected species (Jackals) have
    fewer infections due to diluting effect.
-   At high coupling, increased population increases spread of disease, but at
    low coupling it depends on contact structure of additional hosts

@Brown2004a - Effect of Host Clustering in Plants
=================================================

-   There is experimental evidence that both plant population density and size
-   Clumped population have faster epidemics at first, slower later
-   Model results show that a "pandemic" threshold exists for hosts with varying spatial density
-   For lattice models, local buildup can cause high densities of infectives, and saturation can then reduce spread compared to mass action.  Metapopulation models are similar
-   Spatial point process hav discrete organisms in continuous space.  Approximate spatial structures with means and spatial covariances of individuals
-   Show that mass action models will overestimate the rate of disease invasion
-   Local equilibria establish before global
-   Use Stochastic SIR model to ask:
    1.  How does the epidemic threshold depend on the spatial distribution of
        host plants?
    2.  How does the epidemic threshold depend on the dispersal scale and kernel
        shape of the pathogen?

## Model

- Continuous in time and space
- Space is homogenous
- Host a location $x$ is infected by spores arriving from all other points.  Spore dispersal is a probability density function times the contact rate $\lambda$, which incorporates spore production, survival, and infection rates
- Exponential, Normal, and Fat-tailed dispersal kernels used (radially symmetrical), compared by effective area.  Density is normalized to $S_0$
- Hosts arranged in either uniform spatial poisson process, or clustered by having $\text{Poisson}(n)$ "daughter" plants placed around parents via a host distribution kernel $H(r)$.  Anticlustered population is generated by starting with Poisson distribution and eliminating plants with $a$ distance of another.
- $p_{SI}(r)$ are joint density of population at distance $r$, the probability of finding an individual of $S$ or $I$ class in a unit area in regions $r$ apart, as the area goes to zero.   Global densities of each class are functions of $\lambda$, the kernel, $p_{SI}(r)$, and the recovery rate $\mu$
- Nondimensionalize to time units of recovery rate and space units of density 1.
- Spatial covariance is $c_{SI}(r) = p_{SI}(r) - SI$, as is scaled to $$\mathcal{C}_{SI}(r) = c_{SI}(r)/SI$$
The weighted version $\bar{\mathcal{C}}$ is weighted by the dispersal kernel, and is a clustering index, with positiive values clustered and negative anticlustered.  With this, the nondimensionalized global densities are:
$$\dot{I} = \lambda(1 + \mathcal{C}_{SI})SI - I$$
$$\dot{S} = -\lambda(1 + \mathcal{C}_{SI})SI$$

- With zero covariance, we have mass action, but it is modified by mass action.    
- $\mathcal{C}_{SI}$ modifies $R_0$
  $$R_0 = \lambda(1+\mathcal{C}_{SI})$$
  
 - However, this only holds for the initial phase of the epidemic, because it does not incorporate the spatial clustering of infected hosts in later stages
 - Simulation shows the epidemic is smaller but longer
 
## Moment closure

- **Moment closure** approximates the behavior include $\mathcal{C}_{SI}$, even though we do not know the covariances.  It assumes that three-way interactions can be written down as functions of the mean densities and pairwise covariances.

## Dynamics

- Moment closure improves on the mean field approximation, making smaller, long-lasting epidemics
- As epidemic progresses, local buildup of infective individuals leads to negative covariance between $I$ and $S$, slowing spread of disease
- Moment closure does not capture clustering well

## Threshold structure

 - At "pseudoequilibrium", $I \approx 0$ and $S \approx 1$.  The pseudoequilibrium spatial structure can be computed.  It depends only on spatial components (clustering and dispersal), but not the transmission and recovery rates. 
 - However, spatial structure evolves over time with the spread of disease.
 - So, $R_0$ is computed at the peak number of infected
 - As disease dispersal scale lessens relative to the host scale, the real $R_$ falls, but it can increase at mid-scales with clustering.
 - We can compute $R_0$ or the transition rate $\lambda$ by varying the host and pathogen dispersal parameters, computing $\mathcal{C}_{SI}$, and solving for the critical rate
 - Clustering can make epidemics more or less likely than mean field, depending on dispersal scale.  If pathogen dispersal is too short relative to host pattern, then it depletes supply of susceptible.  Intermediate scale is more likely than in mean-field theory.  If dispersal very long, it is as if you have mean-field.
 - More clustering makes epidemics more likely, but may not increase their size.
 - Anticlustering increases the threshold transmission rate required to make $R_0 > 1$, though the effect is small given the limits of anticlustering
 - Thin-tailed kernels yield larger differences from mean-field than fat, when kernel effective area or mean dispersal distance is normalized
 
## Discussion

 - Moment closures five useful approximations
 - Local pathogen dispersal cause local saturation, which can check spread due to loss os susceptible hosts
 - Clustering promotes the occurrence, though not neccessarily the size of epidemics, anticlustering has the opposite effect
 - The critical transmission rate (to exceed $R_0 = 1$) increases as the pathogen dispersal scale decreases when the hosts are randomly or anticlustered
 - When host are clustered, transmission rate required is *below* the mean field value at intermediate levels.
 - Increasing degree of clustering lowers the critical transmission rate, opposite for anticlustering
 - Fat-tailed kernels reduce the critical transmission relative to thin-tailed ones
 



Maybe look up:

 - Jeger, M. J. (1986). Asymptotic behaviour and threshold criteria in model plant disease epidemics. Plant Pathol. 35, 355–361.
 - Jeger, M. J. (Ed.), (1989). Spatial Components of Plant Disease Epidemics, Englewood Cliffs: Prentice Hall.
 - Jeger, M. J. and F. van den Bosch (1994). Threshold criteria for model plant disease epi- demics. I. Asymptotic results. Phytopathology 84,24–27.

# @Park2001

 - Plant pathogens are inherently spatially restricted, imposing spatial structure on the epidemic, and divides the plant population into subpopulations
 - Empirical studies have shown that diseases depend on patch population size and status of neighboring patches
 - Model has patches with homogenous mixing, linked with transmission.  Both deterministic and stochastic versions
 
##  Model

 - SI, structured by patches, with density dependence of both birth and death resulting in a carrying capacity for each patch.  Additional mortality from infection.
 - Force of infection is given by sum of in-patch ~$\beta I_j$ and sum of neghborhood $\varepsilon \beta \sum I_k$, so essentially weaker between- than within- coupling.
 - Neighborhood defined as patches within a fixed radius $(\rho)$ within a square grid, but strength of interaction is independent of distance within the neighborhood
 - Stochastic version uses binomial transition probabilities and discrete time, with approximating distributions in some cases
 
## Results

 - Within-patch $R_0$ (or $R_p$) dependent on the carrying capacity $\kappa$, so can define invasion criterion as critical patch size allowing invasion to occur.  For homogenous population $R_0 = nR_p$.
 - A heuristic result for $R_0$ in the metapopulation is $R_p(1 + z\varepsilon)$, where $z$ is the number of patches in the neighborhood.  Critical patch size in this case is
$$\kappa_m = \frac{\mu+d_0}{\beta(1+z\varepsilon) - d_1}$$
 - Invasion cannot occur below thresholds of $R_p$ and $\varepsilon$, above these, probability of invasion increases in the stochastic case as these values increase.  Stochastic threshods are higher than deterministic.
 - Threshold values of $R_p$ and $\varepsilon$ decrease as neighborhood size increases.  (Of course, $\varepsilon$ and $\rho$ are both components of inter-patch connectivity)
-   Probability of invasion is related to initial level of infected hosts via
    $$\text{Pr}(\text{Invasion}) = 1 - \left( \frac{1}{R_0} \right)^{I_0}$$ 
-   Invasion threshold is same as persistence in deterministic model, different in stochastic.  In stochastic, high $R_0$ leads to extinction, intermediate values lead to patchy persistence
-   Highest persistence occurs at intermediate of coupling $\varepsilon$, high values of $R_p$, and larger neighborhood sizes $\rho$

**TODO: Look at references in page 169 for alternative plant systems with epidemic thresholds**



# @Park2002

 - 2 components to extinction time in a metapopulation: spreading, dependent on transit between and number of patches, and within-patch persistence (based on size)
 
## Model
 
 - Model system has no host births or deaths (other than those caused by disease), so assumes epidemic is faster than population demographics
 - Force of of infection same as in @Park2001.  Population constant at carrying capacity $\kappa$.
 - For each patch $R_p = \beta \kappa / \mu$
 - Square array
 
## Results 

 - For homogenous populations, time to extinction depends on the log of population size
 - Extinction time is approximately linear in log patch size in model
 - Transit speed (1/avg. time to appearance in adjacent patch) and probability of transit both increase with $R_p$ and strength of coupling $\varepsilon$, thohgh less at smaller $\kappa$.
 - For metapopulation, three distinct regimes for extinction time as patch size/coupling increase:
   - Extinction occurs within the original patch, because transit is rare
   - Epidemic spreads and has long and variable extinction time, because of rescue effects
   - As probability of transit iis close to one, extinction time is short as transits homogenize the population
   - In two-dimensional structure, extinction time is estimated as $T_E = a + b^{\frac{1}{2}}$, where $a$ is in-patch extinction time, $b$ is transit time and $n$ is the number of transits.  This fits simulation well. 
 
 
Maybe look up:

-   Onstad, D.W. & Kornkven, E.A. (1992). Persistence and endemicity of pathogens in plant populations over time and space. Phytopathology, 82, 561–566.
-   Park, A.W., Gubbins, S. & Gilligan, C.A. (2001). Invasion and persistence of plant parasites in a spatially-structured host population. Oikos, 94, 162–174


References
==========
