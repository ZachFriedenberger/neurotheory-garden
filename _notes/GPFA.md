---
title: Gaussian Process Factor Analysis
usemathjax: true
tags:
  - machine-learning
  - dimensionality-reduction
---


--- 


motivation: if neural activity is driven by internal processes instead of external drive, trial-averaging will obfuscate the underlying dynamics

For experiments involving perception, attention, and action, we will want to analyze activity on a trial-by-trial basis 


goal: extract smooth neural trajectory that embodies only the shared variability in firing rate across the population. 

Individual neural variability (assumed to reflect the noise process involved in spike generation) is discarded


Q: Can we decompose the shared variability into shared point process and FR fluctuation components?

## Existing methods

- first smooth spike trains with kernel and then use static dimensionality reduction techniques like [[PCA 🚧]]. 
	- other methods can be used for also estimating the FR profiles of single units (i.e., a small number of trials)
	- more advanced techniques
- Amount of smoothing is often arbitrary 
	- learn with GPFA


## Model definition

Want to use time information for the dimensionality reduction itself. More powerful than FA when dealing with time series data. 

GPFA is a set of factor analyzers, one for each time point. Strung together by a Gaussian process prior.

Smooth trajectories are a compromise between low-dimensional projection (FA) and points being close to each other in time (GP).


- First bin spike counts in non-overlapping bins
- Use square-root transform to control the variance of the spike trains (assumes a Poisson process)



## Inference



















## References

- Paper by Byron Yu