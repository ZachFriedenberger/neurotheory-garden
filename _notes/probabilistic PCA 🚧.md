---
title: Probabilistic PCA
usemathjax: true
tags:
  - dimensionality-reduction
  - machine-learning
  - unsupervised
  - generative-model
---

> **tl;dr:** probabilistic extension of principal component analysis.  Advantageous for handling missing data and extending PCA to a Bayesian framework. 

---



To extend [[PCA 🚧]] to a probabilistic framework, we simply model the data generation process using a latent variable model. While conventional [[PCA 🚧]] is formulated as a projection from a $D$ dimensional data space to an $M$ dimensional subspace, probabilistic PCA is a mapping from an $M$ dimensional latent space to the data space. We will see that the conventional [[PCA 🚧]] procedure appears doing maximum likelihood estimation. 

By defining PCA a generative model, it is now easy to formulate [[Bayesian PCA]] by simply defining prior distributions over the parameters  ($W$, $\mu$, and $\sigma$). Using the Bayesian formulation, we can then automatically infer the number of subspace dimensions using methods such as [[ARD|automatic subspace determination]]. 

### Model definition

We assume the observations, $x\in\mathbb{R}^{D}$, come from a linear Gaussian model with isotropic variance ,

$$p(x|z)=\mathcal{N}(x|Wz+\mu, \sigma^{2}I).$$

The columns of $W\in\mathbb{R}^{D \times M}$ then define the principal subspace of the data. Each element of $x$ has an independent mean $\mu\in\mathbb{R}^{D}$ and variance $\sigma^{2}\in\mathbb{R}^{D}$ parameter. All correlations in the data are therefore captured by $W$. 

The latent variable $z\in \mathbb{R}^{M}$ has dimension $M\leq D$ and is also assumed to be a standard normal Gaussian,
$$p(z) = \mathcal{N}(0, 1).$$

### Inference

To infer the parameters ($W$, $\mu$, and $\sigma$) we can simply choose our favorite [[statistical inference|inference method]].  However, as the latent variable distribution and the observation model are both Gaussian, the marginal distribution, $$
p(x) = \int p(x|z)p(z)dz,
$$is also a Gaussian given by, 

$$p(x) = \mathcal{N}(x| \mu, WW^{T} + \sigma^{2}I).$$

We can then maximize the log-likelihood, 

$$
\log{p(x)} \propto  N \log(|C|) + \sum_{i=1}^{N} (x_{i}-\mu)^{T} C^{-1} (x_{i}-\mu)
$$

where $C=WW^{T} + \sigma^{2}I$. 




While we can optimize the likelihood using gradient ascent, the analytic solution is given by, 



where $R$ is an arbitary rotation vector. 

### Identifiability

- Can only identify the subspace up to a scalar and rotation -> show why this is true

### Handling missing data

- Motivate with neuroscience experiments in mind

However, we can also just optimize the likelihood function directly. In our implementation we make use of Cholesky decomposition to avoid the weight matrix from becoming singular. 

By defining PCA a generative model, it is now easy to formulate [[Bayesian PCA]] by simply defining prior distributions over the parameters  ($W$, $\mu$, and $\sigma$). This has the benefit of 


### References 

- Bishop ML textbook
- Original probabilistic PCA paper
- Examples using probabilistic PCA in neuroscience?