# Review of previous optimization work in forest disease control

Previous work in forest disease control has been closely related to control of invasive species and other forest pests, especially insects.  Models have used invasive species spread paradigms, and at other times SIS disase models.  Implicitly, these are pathogen-focused and do not include disease dynamics.  This is most important in later stages of disease invasion, when the disease is endemic and eradication or slowing spread is no longer an option.

The main difference between these control models and the disease models here is the inclusion of host species dynamics and feedback between the disease and hosts. Many models of disease [@Horie2013], in fact, do not include host dynamics at all, but treat disease as a species growing or spreading in a static environment.  

Host dynamics may be included implicitly in the process model of disease spread [@REF], and in cases where any area of host plants are "lost", or where goals are strictly based on pest/disease area, these are sufficient.  However, when managment goals are tied to the state of the host population, disease does not cause total loss, and host population dynamics are complex, explicit modeling of host-pathogen interactions is needed.  In the case of SOD, conservation of the most vulnerable species, tanoak, is a major management goal.  Invasion management in uninvaded regions may be sufficiently represented with pathogen-only models, but not control in regions where the disease is endemic.   Also, where disease is endemic, the objective may not be just to minimize the number of infected individuals [@Rowthorn2009], but to minimize the worst effects (e.g., death). SOD may take many years to kill a tree, during which ecosystem services continue to flow, though perhaps at reduced levels.

Control studies have had several goals:

1. Optimize allocation of resources towards controlling the spread of disease, minimizing the combination of damage and management costs.  Examining the relative efficacy of eradication and slow-the-spread strategies.

2. Examine the trade-off between monitoring and eradication efforts [@Horie2013]

3. Optimize allocation of monitoring and eradication effort across space. [@Horie2013]

4. Examine the robustness of these strategies to uncertainty in model parameters [@Carrasco2010]

Methods use include:

1) Optimal control of a continuous, deterministic system via the Hamiltonian equation [@Carrasco2010]

2) Partially-observed Markov decision processes [Cassandra1994; @Haight2010]

3) Info-gap theory [@Carrasco2010]

Studies that have used SIR models and optimal control for the management of forest or wildlife disease:

