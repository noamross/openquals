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

Here, the forc of infecton on patch $j$ is

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
