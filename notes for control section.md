# Review of previous optimization work in forest disease control

Much work in forest disease control has been closely related to control of invasive species and other forest pests, especially insects.  Models have used invasive species spread paradigms, and at other times SIS disase models.

These models have explicit or implict management goals of either minimizing invaded area, pest/pathogen populations, or infected individuals.  Many are concerened with doing so with minimum cost or under restricted budgets, and the value of eradication vs. slow-the-spread strategies.  Another major theme is optimal monitoring, and the trade off in allocating resources between monitoring and control.

Implicitly, these are pathogen-focused and do not include disease dynamics beyond arrival.  This is most important in later stages of disease invasion, when the disease is endemic and eradication or slowing spread is no longer an option.

The main difference between these control models and the disease models here is the inclusion of host species dynamics and feedback between the disease and hosts. Many models of disease [@Horie2013], in fact, do not include host dynamics at all, but treat disease as a species growing or spreading in a static environment.  

Host dynamics may be included implicitly in the process model of disease spread [@REF], and in cases where any area of host plants are "lost", or where goals are strictly based on pest/disease area, these are sufficient.  However, when managment goals are tied to the state of the host population, disease does not cause total loss, and host population dynamics are complex, explicit modeling of host-pathogen interactions is needed.  In the case of SOD, conservation of the most vulnerable species, tanoak, is a major management goal.  Invasion management in uninvaded regions may be sufficiently represented with pathogen-only models, but not control in regions where the disease is endemic.   Also, where disease is endemic, the objective may not be just to minimize the number of infected individuals [@Rowthorn2009], but to minimize the worst effects (e.g., death). SOD may take many years to kill a tree, during which ecosystem services continue to flow, though perhaps at reduced levels.

In high-value areas, such as parks, and traditional ceremonial sites, host-centric management is essential.

Control studies have had several goals:

1. Optimize allocation of resources towards controlling the spread of disease, minimizing the combination of damage and management costs.  Examining the relative efficacy of eradication and slow-the-spread strategies. In metapopulations [@Rowthorn2009]

Lowest cost eradication [@Blackwood2012]

2. Examine the trade-off between monitoring and eradication efforts [@Haight2010; @Horie2013]

Determining a constant optimal sampling effort [@Epanchin-Niell2012; @Bogich2008], with uncertainty in both ecological and search parameters [@Mehta2007]

3. Optimize allocation of monitoring and eradication effort across space. [@Horie2013; @Forster2007; @Homans2011]

4. Examine the robustness of these strategies to uncertainty in model parameters [@Carrasco2010]

Methods use include:

1) Optimal control of a continuous, deterministic system via the Hamiltonian equation [@Carrasco2010]

2) Partially-observed Markov decision processes [Cassandra1994; @Haight2010]

3) Info-gap theory [@Carrasco2010]

Studies that have used SIR models and optimal control for the management of forest or wildlife disease:

These models are more akin to multi-species optimizations (e.g. @Chaudhuri1996, @Kellner2010) than the previous control models.

@Fenichel2010 use an $SI$ model where the goal is not merely disease control, but the maximization of the benefits of harvest of a wild population.  They model a wildlife disease that reduces the value of harvest, and also imposes a cost through transmission to livestock populations.  Rather than minimize the disease, they define the objective as minimizing costs, including control costs, when the disease is endemic.  @Fenichel2010 argue that optimal control techniques are superior to $R_0$-based management approaches, because $R_0$ is a static condition of a disease-free population, and the transient dynamics of an invaded population are different.  They find that eradication of the disease is not optimal if the disease-free population has $R_0 < 1$, as the loss of harvest revenues would be too great.

@Gaff2007 looks at optimal management of a plant disease, this time in an agricultural context.  Using an integrodifference SI model, she examines disease spreading through spatially connected fields, where the control method is to harvest plants early that would otherwise become worthless if infected.  As in other cases, they find a binary control strategy optimal, harvesting all plants in infected and a surrounding buffer zone early in the season, in order to obtain maximum harvest of the remaining sites at the end of the season.

@Sims2010 examines optimal control of mountain pine beetles.  As in the previous cases, the only method of control is reduction of the host (lodgepole pine) population.  @Sims explicitly include timber harvest, dead tree salvage, and forest ecosystem services in their utility function.  In this and subsequent (@Sims2011; @Aadland2012) papers, the model is used to compare the differences in control by local managers to centralized management.

The role of age classes in forestry has been examined extensively [See @Reed1986 and @Tahvonen2004], with particular focus on the choice between even- and uneven-aged forestry and the role of the *normal forest*.   @Hartman1976 finds that adding ecosystem service value to the forest increases rotation length in even-aged models. @Tahvonen2004 examine this in the case of uneven-aged forest, and find setting aside areas for old-growth is optimal, though since the transition is assymetric, the conservation area can fluctuate.

In some areas, these monitoring and eradication are applicable to Sudden Oak Death.  In Oregon, an intense monitoring and eradication program has had some success in containing the disease. 

@Mbah2010 examined SOD in a system with bay laurel and coast live oak, which is a dead-end host, and the trade-off between detection and eradication costs.  @Mbah only removed infected (and detected) trees.  Under a budget constraint, they found it was optimal to remove all detected infected trees as soon as detected.  Under a constact detection effort regime, they 


