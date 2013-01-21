% SOD and Epidemiological Theory
% Noam Ross
% 13-01-16 13:45:52


Parsing the independent effects of community, size, and spatial structure on disease
------------------------------------------------------------------------------------

Forest 
SOD occurs in forest systems that are structured in several important ways:

Multiple Host Species
---------------------

*Phytophthora ramorum* has many hosts, which fall into several functional types. Some hosts are passive; the pathogen can live in these species but but does not sporulate.  In canker hosts.pathogen produces cankers in the trunk, but few if any spores are produced from the cankers and these hosts are dead ends, though the disease may be fatal in them.  In foliar hosts, *P. ramorum* resides and reproduces in leaves and twigs, where it is generally nonlethal.

In Redwood forests in Northern California, the hosts of importance are tanoak (TODO:NAME) and bay laurel (TODO:Name). Other species are passive or do not host the pathogen at all.  Tanoak has the dubious distinction of being the only species that is both a canker and foliar host, and the disease is generally lethal in these trees.  Bay laurel is a foliar host in which *P. ramorum* produces prolifically.

Host Stage Structure
---------------------

Within the tanoak population, disease progression is influenced by the size of the host tree.  Larger trees are more susceptible to canker infection (TODO:CHECK, REF), possibly due to the vulnerability of cracked bark.  Larger trees also tend to die faster once infected than smaller trees [@Cobb2012], though there is no evidence that spore production changes with tree size.

When disease dynamics occur much faster than demographic processes, we can treat size classes similarly to different species, and examine the progression of disease in a constant population structure.  However, when disease progression and growth occur at similar rates, these processes can interact to produce complex dynamics.  This is the case with SOD; infectious periods can last many years, during which trees may continue to grow.

@Klepac2010 created a framwork for examining disease dynamics in stage-structured populations.  In this, disease and epidemiological processes are alternate in time (TODO: *periodic something*).  This approximation holds with SOD in California, where most sporulation occurs during the winter rainy months, while tree growth occurs in the spring and fall [TODO:ref].

Protecting a class drives average age at infection to other classes.    If infection is most common in the young, then vaccination increases age to infection.  Vaccination in the old will, too, but much less. Accentuates oscillation. ˜

Spatial Structure
------------------

Contact rates between trees are influenced by the complex spatial structure of the forest.  Since trees are stationary, the standard assumption in $SI$ models that individuals are well-mixed does not hold.  Nor does the system fit neatly into either the case frequency- or density-dependent transmission.  

Spore dispersal falls off quickly with distance from host trees, but occaisional long-distance transmission occurs.  The dispersal kernel is best represented as fat-tailed.

Metapopulation (@Park2001; @Park2002) and continuous-space (@Brown2004a) approaches have reached similar conclusions of the effect of spatial structure in non-mobile populations.  Disease progresses in two stages, initial growth in local clusters, and then global progression. Whether disease progresses to a global stage depends on the connectivity of patches and/or clustering of individuals and the dispersal kernel of the pathogen.  Certain patterns of clustering may increase the rate of spread of disease (even while global density remains constant).


Approach
--------

All three of the above components of population structure may be manipulated via silvicultural treatments in Redwood-Tanoak-Bay forests.

1)  How do community structure, stage structure, and spatial structure interact to effect the probability and size of outbreaks?
2)  What elements of population structure are most important in predicting and preventing SOD outbreak in Tanoak-Redwood-Bay forests?


$R_0$ is not neccessarily the right measure in a structured population, when corssing population groups is a stochastic event and in-population structure 


Collapse community structure: What are $R_0$, epidemic size, and probability of outbreak for:

Varying community structure:  Bay-only, tanoak-only, mean-field models against mixed bay-tanoak models.  Does host community structure affect the growth rate of the disease?

Size structure: How do epidemiological outcomes compare between homogeneous and size-stuctured population with similar mean epidemiological parameters?  How would $R_0$ and these other outcomes change in communities with a single size class?  How does it change with and without demographic transitions included?

Spatial structure:  How do mean-field approaches compare with spatially explicit ones for this system?  How do random distribution models compare with metapopulation?  What spatially implicit approach best approximates the spatially explicit?

TODO:Table of models

With SOD’s parameters, which of these models best approximates a fully developed spatial model?

Options for a spatial model:

 - Metapopulation has been used (@Cobb2012), and has qualitatively improved results for the rate of the outbreak.  However, there is no particular evidence for discrete patches within the forest.
 - Plants in continuous space (@Brown2004a).  In the approximation of this version, the contact rate evolves with the spatial autocorrelation of the $S$ and $I$ classes $(\mathcal{C}_{SI})$


Community structure:  How are 



*Phytophthora ramorum* is dispersal-limited.  The vast majority of spores are found within 15m of infected forest edges [@Davidson2005], and dispersal distances may be shorter in interior forest.  However, spores occasionally travel long distances (>3 km) via both human-mediated and windblown dispersal, allowing spread between forest fragments [@Meentemeyer2008].  

In @Meentemeyer2011, best modeled this stratified dispersal using mixture of two Cauchy kernels:
$$K= \gamma \left(1 + (d/\alpha_1)^2 \right)^{-1} + (1 - \gamma) \left(1 + (d/\alpha_2)^2)^{-1}$$
where $\alpha_1 = 20.57 \text{m}, \alpha_2=9.50 \text{km}$ and $\gamma=0.9947$.   

Other considerations:

Given that stage transitions are slow, can $R_0$ and other values calculated with fixed age classes approximate those with stage and transition?

Can we approximate outbreak risk by calculating $R_0$ for each stage of advance of disease-free forest?

TODO:Look again at Cobb supplement for their models

Stage-transition models?


 
# Part II: Fitting to data

# Part III: Dynamic Optimization
