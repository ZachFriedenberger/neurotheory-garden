---
title: Dimensionality reduction for neural data
tags:
  - dimensionality-reduction
---
---

## What is dimensionality reduction?

Produce low-dimensional representation of high-dimensional data while preserving a feature of interest in the data. 

Extract $M\leq D$ explanatory variables (or latent variables) / principal subspace of the data using a specific objective function.  $D$ is the number of recorded neurons.

Variance not captured by the latent variables = noise. How much extra variance can we capture by considering alternative noise models? Neurons are often over dispersed and variability depends on location along the hierarchy. 

Can think of latent variables as common input / collective input from unobserved neurons. 

Common to assume that action potential generation of a single-neuron can be represented by a time-varying firing rate (i.e., inhomogeneous Poisson process). This is a major assumption that is not often check in models. How different would the subspaces be? 

Applications

- Data compression
- Whitening or sphering data (zero mean and unit covariance)
- Data visualization
- Decomposing high-dimensional neural data into components that are associated with task variables and behavior

A major problem is that we often have to estimate the dimensionality of the subspace before applying these methods. There are many different techniques to do this. E.g., [[persistent homology]] from [[topological data analysis]]. 

## Why is it useful for analyzing neural data?

Goal: Perform multivariate analyses of multiple spike train data

- large amounts of data (sequential or simultaneous)
- neural population doctrine
- neural activity is fundamentally low-dimensional -> covariation of many neurons
- single-trial analysis essential for internal variables that change in time/are not controlled. e.g., attention
	- leverage population activity to extract summaries on individual trials
- useful for single-trail analysis, exploratory analysis, understanding population structure
- Many areas show heterogeneous response properties. Even lower sensory areas. 
- 


Targeted approaches using behavior or task variables to help determine the latent subspace vs. only using behavior after the subspace has been obtained to verify the usefulness of the latent variables. Often the latent representation is first found and then a decoder is build to relate the latent space to behavior. This has been done to study how population activity differs on error trials. 

- TDR gives a low-dimensional representation through a simple projection, not a decoded estimate. 
	- i.e., they had to define the firing rate using a traditional PSTH instead of inferring a model for data generation



We have a breakdown into unsupervised vs. supervised methods and linear vs. non-linear methods. There are also a bunch of techniques for estimating the dimensionality of a manifold.

A major problem is that we often have to estimate the dimensionality of the subspace before applying these methods.


Optimization gets increasingly tricky as methods become more complex...


## Applications in neuroscience

- PFC / decision making /rule learning
- Premotor cortex / prepatory movements
- Olfactory system / ordor discrimination
- Visual attention!


## Methods

## Covariance methods

Use covariance matrix of observed firing rates. Static time points. 

- [[PCA 🚧]]
- [[probabilistic PCA 🚧]]
- [[FA 🚧]]


### Time series methods

leverage temporal features of spiking data. Lots of point process models. Provide low-dimensional, latent neural trajectories that capture the shared variability across neurons.

- [[HMMs|Hidden Markov Models]]
- Kernel smoothing + static dimensionality reduction

Explicit noise models
- [[GPFA|Gaussian Process Factor Analysis]]
- [[LDS|Latent linear dynamics systems]]
- [[NLDS|Nonlinear latent dynamical systems]]


"the dynamics model in GPFA is stationary and encourages the trajectories to be smooth, whereas that in LDS and NLDS is generally nonstationary and encourages the trajectories to follow particular dynamical motifs."



### Dependent variable methods (supervised methods)

Project the data in such a way that the dependent variables (i.e., task or behavioral variables) are preserved. 

- [[LDA]]
	- groups well separated

### Demixed methods (targeted)

Want to demix the effects of multiple dependent variables. Find a single axis for each dependent variable. 

- [[TDR]] regression approach
- Covariate approach -> Machens, C.K. et al. Functional, but not anatomical, separation of ‘what’ and ‘when’ in prefrontal cortex. J. Neurosci. 30, 350–360 (2010).
- [[Demixed PCA]] probabilistic approach

"covariate approach when there is no clear ordering to stimulus intensities and regression approach when there is a continuum of values"

Q: What if we have a mix of both?

### Nonlinear methods

if manifold is nonlinear, linear methods may over estimate the true dimensionality

Fragile in the presence of noise

Requires a dense sampling of the high-dimensional space 

- [[Isomap]]
- [[LLE|Locally linear embedding]]



### Methods for estimating dimensionality of manifolds

- Explained variance cutoff
- maximize cross-validated data likelihood
- cross-validated leave-neuron-out prediction error
- participation ratio
- persistent homology

### Other related methods

- Can use GLM's instead of linear-Gaussian models
	- Can have hidden states (e.g., dependent variables that are not observed) in a GLM approach too 
	- Can also do dimensionality reduction with these models
- Non-parametric approaches that use the spike count vector to define a probability distribution and use information theoretic measures
	- keeps higher order correlations intact
- 

## References
#### Review articles

Cunningham, J. P. & Yu, B. M. Dimensionality reduction for large-scale neural recordings. Nature Neuroscience vol. 17 1500–1509 (2014).

#### Selected papers

Brown, E.N. et al. Multiple neural spike train data analysis: state-of-the-art and future challenges. Nat. Neurosci. 7, 456–461 (2004)

Churchland, M.M. et al. Stimulus onset quenches neural variability: a widespread cortical phenomenon. Nat. Neurosci. 13, 369–378 (2010).

Cohen, M.R. & Maunsell, J.H.R. A neuronal population measure of attention predicts behavioral performance on individual trials. J. Neurosci. 30, 15241–15253 (2010)

Mante, V. et al. Context-dependent computation by recurrent dynamics in prefrontal cortex. Nature 503, 78–84 (2013).

Churchland, M.M. et al. Neural population dynamics during reaching. Nature 487, 51–56 (2012)

#### Blog posts
https://xcorr.net/2021/07/26/dimensionality-reduction-in-neural-data-analysis/