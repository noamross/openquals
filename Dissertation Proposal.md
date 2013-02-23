% "Draft Disseration Proposal: Forest Disease Dynamics and Management"
% Noam Ross
% 13-01-27 19:18:49

Abstract
========

Forest disease spreads through plant communities structured by species
composition, age distribution, and spatial arrangement. I propose to examine the
consequences of the interaction of these components of population structure for
*Phytophthora ramorum* invasion of California redwood forests. First, I will
compare the dynamic behavior of a series of epidemiological models that include
different combinations of population and community structure. Then I will fit
these models to time-series data from a network of disease monitoring plots to
determine what components of forest population structure are most important for
prediction of disease spread. Using the most parsimoniuous models, I will
determine optimal schedules of treatment to minimize the probability of
precipitous decline of host populations.

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
needed to allocate limited reso

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
management planning requires confidence in their predictive power, particularly
under novel management treatments. Recent developments in *particle filter*
techniques allow estimation of the likelihoods of complex dynamic models
[@Arulampalam2002; @Ionides2006; @Knape2012], and subsequent comparison of
models in out-of-sample predictive performance [@Vehtari2012]. We can have more
confidence in the predictive power of the dynamics of such models than dynamic
models where parameters are derived from data, but the emergent dynamic
properties are not tested.

Sudden oak death (SOD) is an emerging forest disease in California and Oregon
that threatens populations of tanoak (*Notholithocarpus densiflorus*)
[@Rizzo2003]. The progression of the disease is strongly related to forest
species composition and structure. It has many host species, with variable
responses to the disease, and it has different effects on trees of different
sizes [@Cobb2010; Cobb2012].

SOD has has the potential to modify community structure [@Metz2012], and cause
significant economic damage [@Kovacs2011]. Silvicultural, chemical, and other
control techniques can modify the progression of disease], but eradication of
SOD is unlikely [@Swiecki2013; @Cobb2013] even at local scales. Short- and
long-term solutions for for disease control will require continuous treatment
and monitoring regimes. Under budget constraints, planning for such treatment
can be informed by dynamics models via optimal control techniques.

I aim to answer the following overall questions:

1.  How do interactions between tree species composition, size distribution, and
    spatial structure affect the dynamics of SOD is California forests?
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
ramorum* [@Rizzo2002]. *P. ramorum* often kills tanoak[\^1] , which provide
habitat and food to many vertebrate species, and are the primary host of
ectomycorrhizal fungi in redwood forests [@Rizzo2003]. Loss of this species may
have cascading effects on other species. Tanoak also has important cultural
value to Native American tribes in California [@Bowcutt2011]. The disease has
also caused significant economic damage through removal costs and property value
reduction [@Kovacs2011]. It has the potential to spread to species in other
regions, such as northern red oak (*Quercus rubra*), one of the most important
eastern timber species [@Rizzo2002].

*Notholithocarpus densiflorus*

Population Structure: Multiple Host Species
-------------------------------------------

*Phytophthora ramorum* infects over 100 species. Host species fall into three
types: passive hosts, foliar hosts, and canker hosts [@Swiecki2013]. Most
species are passive hosts. *P. ramorum* may infect passive hosts, but does not
cause ill effects or produce spores in these plants. In foliar hosts, *P.
ramorum* resides in and produces spores from the leaves and twigs. These spores
can then spread to other plants. The amount of spore produced varies greatly
from species to species. In canker hosts, *P. ramorum* infects the trunk,
producing cankers (lesions in the bark) and damaging the cambium. Few spores are
produced from the trunk, so these are "dead end" hosts. However, infection may
be lethal to canker hosts. In California, all canker hosts are oak species
(*Fagaceae*).

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

The interaction of multiple host species has important consequences for disease
dynamics. @Dobson2004 examined a model of disease in multiple host species based
on the SIR [@Kermack1927] framework. In Dobson's model, species had density
dependence but interacted only though disease transmission. Importantly,
transmission between species was always equal or less than transmission between
species. Transmission between species also dampened and synchronized disease
oscillations in each species. At very high contact rates between species, the
most susceptible species were more like to go extinct. @Craft2008 implemented a
stochastic version of the @Dobson2004 model in a system of mamallian carnivores,
finding that species with low intra-species contact rates acted as sinks for
disease, and their contact with more social species increased spread of the
disease within these low-contact species.

As in the models above, bay laurel and tanoak compete via disease transmission
[@Cobb2010], and this results in modification of the forest community
[@Metz2012]. Between-species transmission likely extends the length of
epidemics, as in the cases above, when one species act as reservoirs that
re-infect each other. However, SOD dynamics differ from these systemsin
important ways. The contact structure among species may not be symmetrical.
Contact rates among trees are driven by differences in species transmissivity
(amount of spore produced) and susceptibility (probability of infection per
spore) rather than social grouping. Where one species with high transmissivity
coexists with a species of high susceptibility, the probability of transmission
may be higher between species than within.

Another important result from the @Dobson2004 model was the difference between
density- and frequency-dependent transmission. In density-dependent
transmission, when the probability of disease transmission is related to the
density of infected individuals, species had a complementary effect on the
disease's rate of reproduction $(R_0)$; that is, a mix of both species led to
faster outbreaks. In the frequency-dependent case, where transmission was
related to the *proportion* of individuals with the disease, $R_0$ was greatest
when one species dominated. Density-dependent transmission is typical of
well-mixed wildlife populations at low density, while freqency-dependent
transmission is more common in cases where crowding, vector transmission, or
sexual disease transmission limits the number of individuals that may transmit
the disease to a new host. With tree populations in forest, both spatial
structure of species and the dispersal pattern of spores may result in a hybrid
between density and frequency-dependent disease transmission. While greater
populations of infected trees increase the local spore burden, the effective
number of trees any individual interacts with is limited by tree spacing and
spore dispersal distance.

Population Structure: Size/Stage Classes
----------------------------------------

Within the tanoak population, epidemiological characteristics vary with tree
size. Trees of larger size classes are more likely to be infected and die more
quickly than smaller trees [@Cobb2012], Possibly due to the vulnerability of
cracked bark and the amount of bark tissue available for invasion
[@Swiecki2005]. There is no evidence currently for variation in spore production
or other physiological effects across tree sizes [@Davidson2008].

When disease dynamics occur much faster than demographic processes, we can treat
size classes similarly to different species, and examine the progression of
disease in a constant population structure. However, when disease progression
and growth occur at similar rates, these processes can interact to produce
complex dynamics [@Klepac2010]. This is the case with SOD; infectious periods
can last many years, during which trees may continue to grow and produce
offspring. In addition, the disease has direct effects on reproduction, as trees
killed by the disease are likely to resprout [@Cobb2010; @Ramage2011]

The effects of age-based population structure and contact rates have been
studied extensively in the context of human disease and vaccination programs
[@Anderson1985; @Metcalf2011]. Reducing in-class transmission rates at young
ages increases the average age of infection, independent of the exact contact
structure. @Klepac2010 found that increases in within-age-class transmission
leads to larger infected and overall populations of those classes at equilibrium
in an SIR model. The reverse is likely in the SOD system, where infected trees
die rather than recover. @Klepac2010 also found that models were very sensitive
to reproduction rates, but very little is known about reproduction and age
structured fecundity in tanoak.

Size structure in forest diease disease can be either stabilizing or disruptive.
In tropical forests, size structure in disease is thought to be a mechanisms
supporting diversity and stability [@Gilbert1994; @Gilbert1995]. This occurs
when adult trees act as reservoirs of diseases which are more lethal in
juveniles. SOD more closely resembles chestnut blight, however, which had high
mortaility in canopy trees but maintained juvenile recruitment through
resprouting, and radically changed the structure of forests [@Burdon1991]. The
transient effects of size structure is less well understood in this system.
Rapid decimation of the most vulnerable (large) size classes might be expected
to result in the end of epidemics, only to follow by cyclical resurgence as
cohorts of small trees mature. The combination size structure and multiple
species hosts could dampen these cycles, as the reservoir of disease in
less-vulnerable hosts maintains a force of infection as the size stucture of the
more vulnerable hosts changes.

Size class is also important from a management perspective in this system. Large
trees provide a greater portion of ecosystem services. These trees provide
greater acorn crops for wildlife foraging and human use, and large-size trees
are often preferred aesthetically. Management goals are focused on maintaining
this segment of the population.

Population Structure: Space
---------------------------

*P. Ramorum* dispersal interacts with host population structure at many scales.
The pathogen spreads between trees via wind-blown rain and splash, limiting most
spores to spread within 15m of host plants [@Davidson2005]. However, occaisional
weather events, such as fog, can transport spores up to 3 km [@Rizzo2005]. Over
longer distances, *P. ramorum* can be transported in streams or spread via
human-mediated vectors such as nursery plant trade [@Osterbauer2004].
@Meentemeyer2011 found that the best fit model for a stateide-scale spread of
*P. ramorum* was the sum of two Cauchy kernels, one on the scale of tens of
meters and another on the scale of tens of kilometers.

The strong differences in spore dispersal at the scale of meters mean that trees
within a stand may be subject to different spore burdens, and thus can not be
considered "well mixed" in terms of contact rates between trees. Rather, contact
patterns across space arise from the interaction of spatial clustering of trees
and the dispersal kernel of the disease.

Spatial structure slows the progression of disease and increases thresholds
required for outbreaks. The effect of such spatial structure on development of
epidemics has been studied with continuous populations in space [@Bolker1999],
metapopulation models [@Park2001; @Park2002], models of individuals on a lattice
[@Filipe2003; @Filipe2004] and discrete individuals in continuous space
[@Brown2004a]. These approaches have reached similar conclusions of the effect
of spatial structure in non-mobile populations. In all cases, the threshold of
disease growth for a global outbreak $(R_0)$ is greater than the threshold for a
local epidemic $(R_L)$. For instance, in metapopulations on a lattice,
$R_0 = R_L (1 + z\varepsilon)$, where $z$ is the average number of connections
between patches and $\varepsilon$ is the inter-patch contact rate [@Park2001].
In models of individuals in continuous space,
$R_0 = \lambda(1 + \bar{\mathcal{C}} SI)$, where $\lambda$ would be the pathogen
growth rate in a well-mixed population, and $\bar{\mathcal{C}}$ is the spatial
correlation between susceptible and infected individuals. $\bar{\mathcal{C}}$
evolves over time but reaches a minimum that represents the threshold required
for a global epidemic [@Brown2004a].

Spatial structure has other important effects on disease dynamics. Both
clustering and anti-clustering (oversdispersal) reduce the rate of increase of
disease, except when clustering occurs at the scale of dispersal, in which case
it can accellerate spread [@Brown2004a]. Fat-tailed dispersal kernels, such as
those that arise through a mixture of splash- and human-mediated transport,
accellerate spread as well. In stochastic models of metapopulations, spatial
structure lengthens epidemics as populations are re-infected from subpopulations
that are still infected. [@Filipe2003].

In SOD epidemics, spatial structure will interact with other forms of population
structure. Clustering of species or size classes will reduce between-class
transmission, lengthening disease progression. On the other hand, the spacing of
trees, mixing of classes, and dispersal scale may interact so as to accellerate
spread and make the system behave more like well-mixed population.

Optimal Control of Forest Disease
---------------------------------

Managing the endemic disease will require trade-offs between structure that
provides ecosystem services and structure resilient to the disease. 15 years
into the SOD epidemic, effective contol techniques remain elusive. Chemical
controls can prevent infection of individuals but are cost-prohibitive for all
but small numbers of high-value ornamental trees. While intense monitoring and
eradication efforts are underway at the edge of the disease distribution in
Oregon [@Kanaskie2010], the disease will invade large areas of Northern
California and Oregon in the coming decades [@Meentemeyer2011]. Once the disease
has invaded, most treatment options involve modification of forest structure
[@Valachovic2010].

Most optimal control research on forest disease focuses on detection,
eradication, and slowing of the spread of disease. Models for optimal control
often model damage costs as a function to area invaded by disease, or number of
infected individuals. @Sharov1998 examined optimal control where a manager could
control the rate of spread of the invasion front, with costs proportional to the
length of the invasion front, and damages were proportional to the area.
@Sharov1998 found that control strategies had two distinct local maxima in net
benefits, which corresponded to eradication and slow-the-spread strategies. The
preferred strategy depended on how large an area was already invaded.
@Carrasco2010 extend this approach to spread that includes stochastic
long-distance dispersal, and examine the robustness of results to large
parameter uncertainy.

Several studies use this paradigm to examine optimal *detection* of disease, on
the basis that pre-detection damages and post-detection treatment increase with
time to detection as the invaded area expands. @Mehta2007 found that damage
costs, and uncertainty in both ecological and detection parameters increase
optimal search effort. @Bogich2008 included changes in colony detectability with
time, and @Epanchin-Niell2012 expended on this work to include stochasticity and
spatial stochasticity.

Several studies examine the trade-off between detection and control efforts.
@Homas2011 examines a case where new disease centers created via long-distance
dispersal will eventually be overtaken by a disease front (a case very similar
to the SOD at the edge of its distribution.). Though found both monitoring and
eradication efforts are better allocated to sites far away from the invasion
front. @Horie2013, examining the case of Oak Wilt in Minnesota, found that
surveying and treating sites where suspected disease levels are high and easy to
detect is the best strategy for limiting new infections.

A few optimization studies use epidemiological models that include both disease
and host . In most of these, the managment goal is to minimize the number of
infected individuals over time. @Haight2010 and @Horie2013 above do this.
@Forster2007 examined control of disease a SI model with a lattice
metapopulation of fields and found that spatial structure had little effect on
optimal strategy. @Rowthorn2009 used a SIS model to examine the best strategies
for treating metapopulations, with the goal of minimizing the integral of
infected individuals under a budget constraint. They conclude that treating
least-infected subpopulations is optimal, and that only leftover funds should be
applied to more heavily infected populations. In both studies, optimal
treatments were of the "bang-bang" variety: applying maximum treatment at first,
then falling to a lower or zero level of control.

All the above optimization models use "pathogen-centric" utility functions,
which place negative value of infected hosts or invaded area. These equate to
goals of of minimization or eradication of disease. However, are less applicable
where disease is endemic.

"Host-centric" strategies better match management goals of maximizing host
populations or the ecosystem services that flow from hosts. Host-centric goals
can add complexity to the model, as they require explict modeling of pathogen
effects on host and feedbacks. There are fewer such studies, which have more in
common with multiple-species management models [e.g., @Chaudhuri1996,
@Sanchirico2010c] than many of the previous disease control studies.

@Fenichel2010 optimize contol in a system with a goal of maximizing benefits of
harvest of a wild population subject to disease, using an SI model. They model a
wildlife disease that reduces the value of harvest, and also imposes a cost
through transmission to livestock populations. They defined the objective as
minimizing costs of control and lost harvest value when the disease is endemic.
They find that eradication of the disease is not optimal if the disease-free
population has $R_0 < 1$, as the loss of harvest revenues would be too great.

@Gaff2007 examined at optimal management of a plant disease in an agricultural
context. Using an integrodifference SI model, they examined disease spreading
through spatially connected fields, where the control method was to harvest
plants early that would otherwise become worthless if infected. They found a
"bang-bang" strategy optimal, harvesting all plants in infected and a
surrounding buffer zone early in the season, in order to obtain maximum harvest
of the remaining sites at the end of the season.

@Sims2010 examined optimal control of mountain pine beetles. As in the previous
cases, the only method of control was reduction of the host (lodgepole pine)
population. @Sims2010 explicitly include timber harvest, dead tree salvage, and
forest ecosystem services in their utility function. In this and subsequent
papers [@Sims2011; @Aadland2012], they showed that when local managers have
little influence over global pest popualtions, their management of the disease
is sub-optimal compared to centralized management.

Finally @Mbah2010 examined control SOD in a system with bay laurel and coast
live oak (a dead-end host), but otherwise unstructured populations. They
maximized host species density and while under a budget constraint for both
detection and eradication. They found it was optimal to remove all detected
infected trees as soon as detected, while maintaining a constant but moderate
level of detection effort.

Management goals for tanoak-bay-redwood forests with endemic SOD are varied, but
a common desire in Northern California is to maintain populations of tanoak,
especially larger, older trees. Such trees can provide ecosystem services even
while diseased, and death may take several years following infection
[@Cobb2012]. Thus, optimizing for the continued population of large trees is a
better approach than minimizing infections in such systems.

Study Approach
==============

I will examine the comparative effects of the above components of population
structure on SOD epidemics by (1) characterizing the dynamic behavior of models
that include each type of structure and their combinations and (2) identifying
the model structure that best predicts data of disease spread over time in
redwood-tanoak-bay forests. Using the best-fit model, I will determine optimal
control plans for stand protection efforts to minimize the risk of loss of host
plants.

Determining the Consequences of Population Structure via Comparative Dynamics
-----------------------------------------------------------------------------

>**1.  How do interactions between tree species composition, size distribution, and spatial structure affect the dynamics of SOD is California forests?**
>**2.  What aspects of population structure are most important in determining the probability and size of forest disease outbreaks in theoretical models?**

To characterize the effects of the population structure on disease dynamics, I
will compare four models, which are modifications of the model presented in
@Cobb2012. These models describe disease and population dynamics of infected
stands at the scale of tens to hundreds of meters. This is the relevant scale of
management for many property owners, and of management units such as high-value
cultural sites. At this scale, long-distance dispersal is primarily important
only as a source of innoculum from the outside, but the meter-scale of
short-distance scale of dispersal causes spatial clustering and indicates a role
of stand spatial structure in dynamics [@Kelly2002].

**Model 1** is the simplest of the four models, only representing structure in
the form of differences between species of trees. In this model, there are populations of both susceptible and infected trees of each species ($\boldsymbol{S}_t$ and
$\boldsymbol{I}_t$). New recruits enter the susceptible population at
rate $b(\boldsymbol{S}_t + \boldsymbol{I}_t)$, modified by a density-dependence term.  New trees also enter via resprouting of trees killed by disease, at a rate $(r)$ proportional to these deaths $(m_i \boldsymbol{I}_t)$.  Recruitment is a stochastic process, so at each step new recruits are drawn from a Poisson distribution.

Suceptible trees become infected at a rate of $e^{\text{force of infection}}$. The force of infection is the product of the vector of the infected tree population and a "Who Acquires Infection from Whom" matrix (WAIFW, $\beta$).  The WAIFW matrix represents the contact rates between different classes of trees.  An additional component of the force of infection is added this is $(\lambda_ex)$, representing the burden of spores arriving from outside the forest stand.  As infection is an infectious process, the number of trees infected in each time step is drawn from a Binomial distribution.  Death, which occurs at different rates for susceptible and infected trees $(m_S, m_I)$, is drawn from a binomial distribution, as well.

The model is characterized by this system of stochastic difference equations:

$$\begin{aligned}
\boldsymbol{S}_{t+1} &\sim \boldsymbol{S_t} + \overbrace{  \text{Pois}\left[\boldsymbol{b(S_t+I_t)}\left(1-\sum_{i=1}^n w_i (S_{it} + I_{it}) \right) + \boldsymbol{rm_I I_t}\right]}^{\text{new recruits}} \\ 
&- \overbrace{\text{Binom}_1\left((\underbrace{1 - e^{-\boldsymbol{\beta I_t} - \boldsymbol{\lambda_{ex}}}}_{\text{force of infection}})\boldsymbol{S_t} \right)}^{\text{infections}} -\overbrace{\text{Binom}_2(\boldsymbol{m_S S_t})}^{\text{mortality}} \\
\boldsymbol{I}_{t+1} &\sim \boldsymbol{I_t} + \text{Binom}_1\left((1 - e^{-\boldsymbol{\beta I_t} - \boldsymbol{\lambda_{ex}}})\boldsymbol{S_t} \right) - \text{Binom}_3(\boldsymbol{m_I} \boldsymbol{S_t}) 
\end{aligned}$$

The parameters are listed below in Table 1.

  ---------------------------------------------------------------------
      Parameter Vector Symbol      Description
  -------------------------------- ------------------------------------
       $\boldsymbol m_{S,I}$       Probability of death per year, for
                                   both susceptible and infectious
                                   trees

          $\boldsymbol b$          Fecundity per individual per year.

          $\boldsymbol r$          Probability of resprouting after
                                   death by disease.

          $\boldsymbol w$          Competitive coefficient (relative
                                   contribution to density-dependent
                                   recruitment)

     $\boldsymbol \lambda_{ex}$    Rate of contact of each species with
                                   pathogen spores from outside the
                                   site
                                   
        $\boldsymbol \beta$        The WAIFW matrix of contact rates 
                                   between  classes of trees
  ---------------------------------------------------------------------

  : Model A Parameters

This modifies the framework from @Cobb2012 in several ways: (1) inclusion of
demographic stochasticity, (2) conversion from continuous to discrete time, (3)
the inclusion of $\lambda_{ex}$, the force of infection from areas outside the
system, and (4) the exclusion of recovery of infected trees, which has not been
observed in the field. Finally, the only population structure in Model A is the
difference in species parameters. It excludes age structure and spatial
structure, assuming a well-mixed population and frequency-dependent transmission.

**Model 2** adds stage structure to Model 1. In this case, the vectors
$\boldsymbol{S_t}$ and $\boldsymbol{I_t}$ represent the population divided by
species *and* size class.  Individuals move up in size class at rates defined in the transition matrices $\boldsymbol{A_S}$ and $\boldsymbol{A_I}$.  These are block-diagonal matrices composed of Leslie matrices for each species. $\boldsymbol{A_S}$ and $\boldsymbol{A_I}$ differ only in mortality rates.  Demographic stochasticity is included by drawing from a multinomial distribution.

In this model, disease transitions are separated in time from demographic transitions [@Klepac2010]. In California, *P. Ramorum* reproduces and spreads during the winter rainy season while most tree growth occurs in the spring and fall, so this is a reasonable approximation.  At each time step, disease transitions occur first $(S_t, I_t \rightarrow S'_t, I'_t)$, then demographic transitions $(S_t, I_t \rightarrow S_{t+1}, I_{t+1})$

The following equations characterize Model 2

$$\begin{aligned}
S'_t &\sim S_t - \text{Binom}_1\left((1 - e^{-\boldsymbol{\beta I_t} - \boldsymbol{\lambda_{ex}}})\boldsymbol{S_t} \right) \\
I'_t &\sim I_t + \text{Binom}_1\left((1 - e^{-\boldsymbol{\beta I_t} - \boldsymbol{\lambda_{ex}}})\boldsymbol{S_t} \right) \\
S_{t+1} &\sim \text{Multinom}(\boldsymbol{A_S(S'_t,I'_t)S'_t}) + \text{Pois}\left[\boldsymbol{b(S'_t+I'_t)}\left(1-\sum_{i=1}^n w_i (S'_{it} + I'_{it}) \right) + \boldsymbol{rm_I I'_t}\right] \\
I_{t+1} &\sim \text{Multinom}(\boldsymbol{A_I(S'_t,I'_t)I'_t})
\end{aligned}$$

**Models 3 and 4** modify Models 1 and 2 by adding spatial structure in the form
of a hexagonal lattice metapopulation with 20-unit sides.  Hexagonal units are useful for approximating the circular sample plots, and also simplify some dispersal kernels.  In these models, $\boldsymbol{S_t}$ and
$\boldsymbol{I_t}$ become $\boldsymbol{S_{jt}}$ and $\boldsymbol{I_{jt}}$,
matrices of each species and class at each location. Furthermore, the force of
infection
$\left((1 - e^{-\boldsymbol{\beta I_t} - \boldsymbol{\lambda_{ex}}})\boldsymbol{S_t} \right)$
is replaced with an overall force of infection $\Lambda_{jt}$ at each location.  This is calculated as

$$\Lambda_{jt} =  \boldsymbol\beta \sum_{x=1}^J \phi (\boldsymbol I_{xt}, j, \boldsymbol{\theta}) + \lambda_{ex}$$

Here $j$ is the location, $\phi$ is the dispersal kernel of *P. ramorum* from
all locations $x$ to $s$, and $\theta$ is a vector of parameters of the
dispersal kernel. $\boldsymbol{\beta}$ remains the contact matrix, representing
physiological and vertical dispersal components of spore dispersal, and $\lambda_ex$ is the force of infection from outside the stand.

Using these four models, I will determine:

-   How global epidemic growth rate $R_0$, probability of global epidemic, the
    epidemic size, and time to extinction of both hosts and pathogens vary
    between the models
-   How the presence of each form of population structure affect these values
    when global species densities and mean parameter values remain identical
-   Whether the effects of population structure are additive or if they interact
    in a more complex way.

The models will be parameterized with three species: tanoak, bay, and redwood,
(the latter representing all non-host species). Parameters and initial
conditions will be drawn from @Cobb2012 and @Filipe2013.

In addition, I will examine the models' sensitivity to key demographic parameters, in particular the reproductive rates, for which data are limited.  I will also explore the consequences of modifying the structure of species density dependence, whether disease transmission is frequency- or density- dependent

Selecting the Model that Best Represents Observed Behavior
----------------------------------------------------------

> **3. What aspects of population structure are most important in *predicting*
> the probability and size of SOD outbreaks?**

To apply the understanding developed in exploring model structure to management,
I must determine which model best represents observed dynamics of SOD in
forests. I will fit the four models above to data of SOD spread in
redwood-tanoak-bay forests in California and compare their ability to predict
disease development.

### Data

Data to fit the models comes from a collaboration with the Rizzo lab's disease
monitoring plot network [@Maloney2005; @Cobb2010; @Cobb2012]. The data consist of observations tree size, alive/dead status, and disease status for trees greater than 1 cm diameter from the years 2002-2007. Trees were observed in 14 sites along the California coast from 36.16°N to 38.35°N, or from the Los Padres National Forest south of Carmel Valley north to Santa rosa. Each site contains an openpaverage of 8 500 m^2^ circular plots, seperated by minimium distances of 100m and arranged in a random linear sequence. All plots are in forests dominated by redwood, tanoak, and bay laurel.

Size, health, and disease status of all trees were measured in 2002 and 2007, as
well as for a random sample of 5 previously infected and 5 previously uninfected
trees of each species per plot in the years 2003-2006.

Since the time scale of the are not suffiently long to determine transition
between size classes, the parameters of transition matrices will be drawn from
other data from other sites and included as strong priors on these parameters. Longer-term data are available from sites established further north, and an additional monitoring network of plots in the Big Sur region [@Metz2012].

### The Observation Model

The process generating the data above may be considered a **hidden Markov
process** [@Gimenez2012]. These are processes where the state of the system is
dependent on its previous state, but where states are partially or imperfectly
observed.  Hidden Markov modeling provides a mechanism to confront theoretical models such as SIR with data and describe their adequacy in prediction [@Arulampalam2002; @Ionides2006].  These methods have been applied to model human disease  [@He2010; @Metcalf2012] and wildlife population dynamics [@Knape2012; @Gimenez2012].  


Specifying a hidden Markov process model requires a model of observation that links the underlying process with data.  In the case of SOD, imperfect observation is due to incomplete counting of trees and error in determination of tree disease status. 

Tree disease is determined by subjective examination of symptoms in the field, and then confirmed in the lab for those individuals with sufficiently suggestive
symptoms. There are both false positives and false negatives, and false
negatives are much more common.:

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

For incomplete census years, a sub-sample of trees is observed, stratified by
previously observed disease states. In these years, the probability of observing
disease is conditional on the observation in previous years.

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
particle likelihoods is an unbiased estimate of the model likeihood
[@Arulampalam2002].

With an estimate of likelihood available, one needs an approach to determine the
maximum-likelihood estimate of the model parameters $(\theta)$. Several methods
are available. **Iterated filtering** (ITF) estimates $\theta$ by replacing
constant parameter values with a random walk $\theta_t$ of decreasing variance
over time, and determining the "states" of this walk as the variance approaches
zero. ITF is computationally efficient but requires long time series.

Alternatively, **Particle Filter Markov Chain Monte Carlo** (PFMCMC) uses a
Markov Chain sampler (e.g., Metropolis-Hastings) in conjunction with a particle filter.  The Markov Chain samples from the likelihood distribution of the model parameters, using the particle filter in each iteration to calculate likelihood.  This is computationally expensive - the particle filter simulates the dyanamic hundreds to thousands of times at each step in the MCMC chain to determine likelihood, and the Markov chain may be many thousands of iterations long.  However, this method is more data-efficient than ITF, as it does not introduce the additional noise of the random walk.  Also, with ITF, this noise has a greater effect on short time series, making a fit against multiple time series much worse than a single long one.  In this case, where there are time series of infection for a period of seven years over several sites, the computational cost of PFMCMC is likely worth the additional power.  Also, PFMCMC
also integrates particle filtering into a Bayesian context.  It is simple to include an infromative prior, as will be likely needed for tree demographic parameters, and use Bayes' theorem to integrate it with the MCMC results.  I will used PFMCMC to determine maximum-likelihood
parameterizations for all four models.

When fitting models 1 and 2 to the data, populations from each plot in each site
will be aggregated. For models 3 and 4, each plot will represent a single
sub-population on a lattice spanning the site. Initial density, species, age and
disease distributions for other sub-populations will be randomly generated from
other points on the lattice using the proportions from the measured plots.
Epidemiological parameters will remain constant across sites except for the
external force of disease $\lambda_{ex}$, which will be represented as a
normally distributed random variable to account for site effects.

### Model selection

Model selection criteria have multiple purposes: to determine which model best
represents "true" processes, and to estimate the utility of models for the
purposes of prediction. In this case, I am interested in both - determining
which components of population structure matter, and also providing an estimate
of predictive stength of the best model. For these purposes, I will use the
**deviance information criterion** [@Spiegelhalter2002, DIC]. DIC has several
advantages. Since it estimates the model complexity, or effective number of
parameters, directly from the likelohood distribution, it makes it easy to
incorporate random parameters such as $\lambda_{ex}$ that have non-integer
contributions to model complexity. Secondly, it estimates the how priors on
parameter values affect their contribution to model complexity.

DIC is not suitable for model-averaging. However, model-averaged results will
not likely be useful for the optimization analysis below. Using the best-DIC
model for prediction is a compromise between predictive ability and tractable
analysis of the model used for prediction. Use of DIC assumes that there is a
"best" or "real" model within the comparison. While no models are "true"
[@Box1976], this excercise is selecting a "best" or "most useful" model for
scenario exploration.

Using Dynamic Optimization to Determine the Best Control Strategy
-----------------------------------------------------------------

> **4. What control strategy minimizes the probability of SOD outbreaks at least
> cost?**

### Using a partially-observed Markov decision process (POMPD)

POMDP

Given an observation in a given year, and an action, what is the distribution of
likely observations in the next state. Given the large potential state space of
the model (e.g., the "curse of dimensionality" @Bellmanref), there is no.
However, the state space can be reduced

The best-fit model that captures essential aspects of the disease dynamics will
be used to develop an optimal control solution to minimization of disease risk
over time.

Optimal of the discrete system above can be calculated using a Markov decision
process.

While forest disease management can occur under multiple, conflicting and
uncertain goals and priorities, here I consider the case where conservation of
large size-class tanoak and its ecosystem services are the goal. This is
approximately the case in Humboldt County, California, where large landowners
have agreed to work in tandem to control the disease. In this situation,
managers goals can be simplified to three components: (1) The minimum acceptable
density of the species of interest $(N_{min})$, (2) the acceptable probability
that the species will fall below that density $(p_{acc})$ during the management
period, and (3) the cost of disease control $C$. Using acceptable probabilities
avoids the challenge of defining and valuing the flows of ecosystem services as
a function of the forest composition [@Hartman1976].

The action selected in each step is thus the action that minimizes the

Tools for SOD control can be categorized into two types. Silvicultural
("host-centric") treatments change forest composition. "Pathogen-centric"
treatments, such as quarantine, equipment cleaning and spraying, reduce the
probability of spore arrival [@Swiecki2013].

Control treatment can involve one of several discrete actions. First, cutting
all known infected individuals. Second, cutting the forest to the disease-free
optimum. Third, imposing quarantine controls or spraying to reduce the
probability of external infection. Cutting is a periodic control treatment that
can be imposed in any year. I define the cut as a reduction in species density
to the levels that would minimize the probability of species densities falling
below the acceptable level over a management period without further controls.
This will be a value that balances stochastic risk of extinction with risk of
diseae outbreak, bounded by the minimum acceptable species density. As tanoak
and bay laurel trees have little timber value, each cut has a cost $(c_1)$. For
the purpose of this model $c_1$ is independent of the extent of density
reduction (that is, the variable costs of cutting are negligible. Thus, the
annual cost of cutting is $c_1 E_1$, where $E_1$ is a zero-one control variable

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

While exact solutions of POMDP are intractable for anything but a small number
of states, algorithms have been developed to approximate solutions for large and
continuous state spaces. [@Schapaugh2012, @Nicol2012, @Cassandra1994]

The reward function is is the negative of costs, but rejects any action that
permits the probability of outbreak to fall below $p_acc$.

Under a budget contraint, we add funds as an additional state variable, and our
reward function is the negative probability of the population falling below
$N_{\min}$, rejecting any solution that allows the spending to exceed the
budget. The problem can be simplified by assuming all funds will be spent.

References
==========
