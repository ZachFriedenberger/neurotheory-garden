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


To extend [[PCA 🚧]] to a probabilistic framework, we simply model the data generation process using a latent variable model. While conventional [[PCA 🚧]] is formulated as a projection from a $D$ dimensional data space to an $M$ dimensional subspace, probabilistic PCA is a mapping from an $M$ dimensional latent space to the data space. We will see that the conventional [[PCA 🚧]] procedure appears doing [[MLE|maximum likelihood estimation]]. 

By defining PCA a generative model, it is easy to formulate [[Bayesian PCA]] by defining prior distributions over the parameters  ($W$, $\mu$, and $\sigma$). Using the Bayesian formulation allows us to automatically infer the number of subspace dimensions using methods such as [[ARD|automatic subspace determination]]. 

### Model definition

We assume the observations, $x\in\mathbb{R}^{D}$, come from a linear Gaussian model with isotropic variance ,

$$p(x|z)=\mathcal{N}(x|Wz+\mu, \sigma^{2}I).$$

The columns of $W\in\mathbb{R}^{D \times M}$ then define the principal subspace of the data. Each element of $x$ has an independent mean $\mu\in\mathbb{R}^{D}$ and variance $\sigma^{2}\in\mathbb{R}^{D}$. All correlations in the data are therefore captured by the structure of $W$. 

The latent variable $z\in \mathbb{R}^{M}$ has dimension $M\leq D$ and is also assumed to be a standard normal Gaussian,
$$p(z) = \mathcal{N}(0, 1).$$

### Inference

To infer the parameters ($W$, $\mu$, and $\sigma$) we can simply choose our favorite [[statistical inference|inference method]].  However, as the latent variable distribution and the observation model are both Gaussian, the marginal distribution, $$
p(x) = \int p(x|z)p(z)dz,
$$is also a Gaussian, 

$$p(x) = \mathcal{N}(x| \mu, WW^{T} + \sigma^{2}I).$$

This allows us to find the model parameters analytically by maximizing the log-likelihood, 

$$
\log{p(x_{1},...,x_{N})} \propto  -\frac{N}{2} \log(|C|) - \frac{1}{2}\sum_{i=1}^{N} (x_{i}-\mu)^{T} C^{-1} (x_{i}-\mu)
$$

where $C=WW^{T} + \sigma^{2}I$ and I have omitted the terms that do not depend on the on the model parameters. We can then optimize the likelihood using gradient ascent. However, the analytic solution is given by, 

$$W_{MLE} = U_{M}(L_{M}-\sigma^{2}I)^{1/2}R$$

where $U_{M}$ is a matrix with columns corresponding to a set of $M$ eigenvectors from the data covariance matrix $S$. Typically the $M$ components with the largest eigenvalues are chosen (i.e., the maximum of the likelihood function). $L_{M}$ is a diagonal matrix with the corresponding $M$ eigenvalues. Lastly, $R$ is an arbitrary orthogonal rotation matrix. 

The mean is simply given by the sample mean, $\mu_{MLE} = \frac{1}{N}\sum_{i}x_{i}$ and the variance is given by the average of the $D-M$ smallest eigenvalues, $\sigma^{2}_{MLE} = \frac{1}{D-M}\sum_{i}\lambda_{i}$.  This can be interpreted as the lost variance averaged over the discarded dimensions. 

### Identifiability

We can only identify the matrix $W$ defining the subspace up to an orthogonal rotation. Therefore when using the analytic solution, we are free to set the rotation matrix to the identity. To see why this is the case, consider a solution found by MLE that is rotated with respect to the true subspace directions, $W_{MLE} = W R$. The covariance of the marginal distribution is then equal to the true covariance, $C_{MLE}=C$, using the fact that $RR^{T}=I$ for orthogonal matrices. Therefore, the marginal data distribution is invariant to orthogonal rotations in the latent space. 

### Dimensionality reduction

With the identified model parameters we can then determine the distribution of the latent parameters. This is easy to do given the conditional distribution of the latent variables given the observations is also Gaussian, 

$$p(z|x) = \mathcal{N}(z|M^{-1}W_{MLE}^{T}(x-\mu_{MLE}), \sigma^{2}_{MLE}M^{-1}),$$

where $M = W_{MLE}^{T}W_{MLE}+\sigma^{2}_{MLE}$.

### Handling missing data

Often when we are analyzing neural data, there are multiple recordings across different experimental conditions, animals, or days. The activity of each neuron in not present in each of the conditions. To not limit ourselves to only using data when all the neurons were recorded simultaneously, we can use probabilistic PCA. To do this we need to use the [[EM algorithm]] for probabilistic PCA. See the original paper from Tipping & Bishop to see this and other use cases. 

### References 

Christopher M. Bishop. 2006. Pattern Recognition and Machine Learning (Information Science and Statistics). Springer-Verlag, Berlin, Heidelberg.

Tipping, M. E. & Bishop, C. M. Probabilistic Principal Component Analysis. Journal of the Royal Statistical Society Series B: Statistical Methodology vol. 61 611–622 (1999)

Examples using probabilistic PCA in neuroscience?