---
title: Note on the coefficient of variations of neuronal spike trains
usemathjax: true
---

> **tl;dr:**  This paper explores how the coefficient of varaition of spike trains from a simplified model depend on the balance of excitation and inhbiition, neural parameters (reset and threshold), and probabilistic synapses.

>**Citation:** @article{10.1007/s00422-017-0717-y,
author = {Lengler, Johannes and Steger, Angelika},
title = {Note on the Coefficient of Variations of Neuronal Spike Trains},
year = {2017},
issue_date = {August 2017},
publisher = {Springer-Verlag},
address = {Berlin, Heidelberg},
volume = {111},
number = {3–4},
issn = {0340-1200},
url = {https://doi.org/10.1007/s00422-017-0717-y},
doi = {10.1007/s00422-017-0717-y},
journal = {Biol. Cybern.},
month = {aug},
pages = {229–235},
numpages = {7},
keywords = {Spike train, Probabilistic synapses, Coefficient of variation, Interspike interval variability, Poisson spike train}
}


**Paper link:** [https://dl.acm.org/doi/abs/10.1007/s00422-017-0717-y](https://dl.acm.org/doi/abs/10.1007/s00422-017-0717-y)


---


# Background

- Spike trains show CV's close to 1 in vivo
- This is mainly believed to be caused by a balance of excitation and inhibition

# Summary

- Authors create a discrete Markov chain model on the integers (incoming excitatory/inhbitory poisson inputs raise the membrane potential by $\pm 1$ respectively). Membrane is reset after reaching some threshold value $k$. Count is reset to 0. There is also a lower bound -$\hat{k}$. 
- Authors also investigate the effect of probabilistic synapses on the CV


# Key Findings

- $C_{v} \approx 1$ when inhibition dominates
- $C_{v} > 1$ in balanced regime if the threshold for spiking is low. Also depends on the reset potential.
- $C_{v}$ can increase over a chain of neurons (forward propagation in a network)


# Take-home Message

- Balanced excitation-inhibition doesn't always lead to a CV close to 1
- At p=0.5, CV depends also on the threshold/reset values, and magnitude of the inputs (more variance). 

# Favorite Figure
- Demonstrates how CV isn't necessarily bigger than 1 when E/I are balanced.
	- but it is hard to tell if this an artifact of the model being too simple... there are other types of noise and effects at the single neuron level that arn't accounted for here.

![[Screenshot from 2022-09-14 17-30-48.png]]