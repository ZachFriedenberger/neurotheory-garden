---
title: Gaussian Processes
usemathjax: true
tags:
  - machine-learning
---
> **tl;dr:**  

---



- Multivariate Gaussian but with infinite dimensions
- Give $x\in\mathbb{R}^{N}$ and get back $y\in\mathbb{R}^{N}$, where the components of y are the probability of observing $x_{i}$ according to a Gaussian living in dimension $i$.
- Useful for Bayesian formulations
- Non-parametric regression
- A GP is a stochastic process (or stochastic function)

- kernel controls how likely functions are to be sampled
	- kernels can be on any two objects! Not necessarily vectors/points
	- measures similiarity between the two objects
		- e.g., Radial basis function RBF
- Similar outputs for similar inputs i.e., smooth functions
- hyperparameters control the amount of smoothness

Modelling by combining kernels -> adding them together
	- multiplication of kernels

- Data that you fit is considered to be only one N-dimensional sample



- GP's are distributions over functions if n->infinity

$$
GP(\mathbf{x}) \sim \mathcal{N}(m(\mathbf{x}), K(\mathbf{x}))
$$


where $m(\mathbf{x})$ is a mean function and $K(\mathbf{x})$ is the kernel matrix. The element of the ith row and jith column of the kernel matrix is given by, $k(x_{i}, x_{j})$.

A popular choice is the squared exponential kernel, 

$$k(x_{i},x_{j}) = e^{-\frac{1}{2}\big(\frac{x_{i}-x_{j}}{\tau}\big)^{2}}$$

This will make it so that values that are closer together have a larger covariance. The parameter $\tau$ controls the smoothness of the GP. 



 



Can be used for [[GPR|GP Regression]] or [[GPFA|GP Factor Analysis]]. 











## References

https://cs.stanford.edu/~rpryzant/blog/gp/gp.html

Applications in neuroscience

- estimating firing rates from spike trains - Cunningham/Shenoy

