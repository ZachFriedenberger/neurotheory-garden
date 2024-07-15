---
title: Amortized Variational Inference 
usemathjax: true
---

Status: 🟨

- Idea that instead of optimizing a set of free parameters, we can optimize a patameterized function that maps points from observation space to the space of parameters.
	- e.g., A neural network that maps observations to model parameters
	- Allows the number of parameters to be decoupled from the number of observations

## Issues with regular VI 
- Need to introduce a separate parameters for each observation (assuming that each observation $x$ has a corresponding latent variable $z$). 
	- e.g. For gaussian posterior approximation $p_{\Theta}(z \vert x)$, we would need a mean and variance for each observation (data-point)
	- Scales at minimum linearly with the number of data-points
	- Need to retrain model when new data becomes available

## Downsides
- Amortized posterior approximation is **less experssive** than using the free-parameters
	- Known as amortization gap (Cremer, Chris, et al. Inference Suboptimality in Variational Autoencoders. 2018)
	- Gap goes away for a network with infinite capacity 
- Constraints set by range of the network output
	- e.g. Sigmoid outputs limit range from 0 to 1


- 