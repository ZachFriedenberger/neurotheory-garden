---
title: Factor Analysis
usemathjax: true
tags:
  - dimensionality-reduction
  - machine-learning
  - unsupervised
---
> **tl;dr:** Extension of principal component analysis but with an explicit noise model. Similar to probabilistic PCA, but with diagonal covariance matrix. Decomposes shared vs. specific variance. 
---

Factor analysis is a method to describe high-dimensional data in terms of a smaller number of latent "factors". The observations are modelled as a linear combination of the factors plus specific error terms. In this way, it is similar to multivariate regression, but the independent variables are unobserved latent variables. 


## Model definition

We assume the observations, $x\in\mathbb{R}^{D}$, come from a linear Gaussian model with a diagonal covariance matrix $\Psi\in\mathbb{R}^{D\times D}$,

$$p(x|z)=\mathcal{N}(x|Wz+\mu, \Psi).$$

The columns of $W\in\mathbb{R}^{D \times M}$ then define the principal subspace of the data. These are referred to as the "factor loadings" and are equal to the covariance between the observations and the factors ("shared variance"). Each element of $x$ has an independent mean $\mu\in\mathbb{R}^{D}$ and variance given by the diagonal elements of $\Psi$ (referred to as "specific variance"). 

The latent variable $z\in \mathbb{R}^{M}$ has dimension $M\leq D$ and is also assumed to be a standard normal Gaussian,
$$p(z) = \mathcal{N}(0, 1).$$

In factor analysis these are referred to as the underlying "factors". 

## Inference

No closed form solutions can be found. Iterative methods such as gradient ascent of the marginal distribution $p(x)$, the [[EM algorithm]], or [[Variational inference|variational methods]] are required. 

The marginal log-likelihood function is given by, 


$$
\log{p(x_{1},...,x_{N})} \propto  -\frac{N}{2} \log(|C|) - \frac{1}{2}\sum_{i=1}^{N} (x_{i}-\mu)^{T} C^{-1} (x_{i}-\mu)
$$

where $C=WW^{T} + \Psi$ and I have omitted the terms that do not depend on the on the model parameters. This can then be optimized using gradient ascent. 

## Factor rotations

As in [[probabilistic PCA]], we can only infer the factors up to an orthogonal rotation matrix. In practice, a rotation can be chosen to aid in the interpretation of the factors in the model. A common choice is Varimax Rotation which finds the rotation that maximizes the variance of the squared loadings. 



## Examples from neuroscience?


## References

Some nice notes on FA:
https://online.stat.psu.edu/stat505/lesson/12


