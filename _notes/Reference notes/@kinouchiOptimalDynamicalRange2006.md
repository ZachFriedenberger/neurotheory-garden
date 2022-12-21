---
title: Optimal dynamical range of excitable networks at criticality
authors: Osame Kinouchi, Mauro Copelli
year: 2006
---

# Background
- Psychophysics studies how stimuli relate to high-level psychological phenomena 
- How microscopic elements lead to observed neural response curves is uknown
	- $F(S) = C\log{S}$ (Weber-Fechner law)
	- $F(S) = CS^{m}$ (Stevens law/Power law)
	- $F(S) = F_{max}S^{m}/(S^{m}+S^{m}_{0})$ (Hill function)
	- where $S$ is the stimuli strength, $C$ is a constant.
- Broad dynamic range is a collective phenomena #collectivecomputation
- Authors have have used a statistical-physics approach to show that Hill-like transfer function arise in networks of excitable elements

# Summary
- Network of excitable elements (neurons, excitable dendrites, etc) with small dynamic ranges cooperate to give rise to a collective repsonse with a broad dynamic range with high sensitivity
- Dynamic range is maximized if the spontaneous activity corresponds to a critical process 
	- This is a clear example of optimial information processing at criticality

# Model
- Discrete counting process neuron model (integer increments due to poisson input and recurrent connections). Resets after some threshold is reached.
- Poisson rate is proportional to the stimulus strength
- $N$ neurons in a [[Erdos-Renyi network]]
	- undirected random graph
- Braching ratio is used as a control paramter
	- average number of excited post synaptic neurons from a presynaptic spike

# Key Findings
- Dyanmic range of stimulus encoding is maximized at a branching ratio of 1 (critical point for sustained network dynamics)
- Firing rate vs. stimulus curves follow hill-like function

# Take-home Message
- Stimulus encoding is maximized when a random neural network has a branching ratio close to 1 and is near a critical point
