---
title: Model-based targeted dimensionality reduction (mTDR)
usemathjax: true
tags:
  - dimensionality-reduction
  - targeted
  - machine-learning
  - behavior
  - regression
---

> **tl;dr:** probabilistic extension of targeted dimensionality reduction ([[TDR]]) that allows task variables to be multi-dimensional. Advantageous for missing data and Bayesian formulations. 

---

Similar to [[dPCA|demixed PCA]] and the original [[TDR]] method, in mTDR the goal is to find the subspaces within the neural activity that best corresponds to specific task variables (e.g., stimulus parameters, behavior, or task outcomes). However, unlike the original mTDR is not limited to a one-dimensional subspace per task variable and can easily handle missing data as a result of its probabilistic formulation. 

I like to think about this as being similar to the extension of [[PCA 🚧]] to [[probabilistic PCA 🚧]]. Which was allows for the formulation of [[Bayesian PCA]] and methods such as - for identifying the dimensionality of subspaces.  However, the original mTDR papers (Aoi & Pillow 2018,  and Aoi et al. 2020) took an alterative approach and created a greedy search algorithm. 


### Model definition

Assume the firing rates during trail k, represented as a matrix $Y_{k}\in \mathbb{R}^{NxT}$ with N neurons in the rows and T time points, can be modelled as a linear combination P task variables and neuron specific noise E_{k}.

$$  
Y_{k} = x_{k}^{(1)}B^{(1)} + x_{k}^{(2)}B^{(2)} + ... + x_{k}^{(P)}B^{(P)} + E_{k}  
$$

  

As neural activity is typically low-rank, we seek a low-dimensional factorisation of coefficients, B^{(P)} = W^{(P)}S^{(P)}, where W^{(P)} \in \mathbb{R}^{N\times r_{P}} can be interpreted as neuron specific weights for the task variable specific temporal basis functions S^{(P)} \in \mathbb{R}^{r_{p}\times T}. Unlike TDR, each task variable can be associated with more than one dimension, r_{P} = \rank{B^{(P)}}. Additionally, as not all neurons are recorded on the same trial, we let Y_{k} be a latent variable of the population activity, with the actual observed firing rates being given by, Z_{k} = H_{k}Y_{k}, where H_{k} is a one-hot encoding of the neurons that were recorded in this specific trial.

To make inference tractable, the model is assumed to have a linear Gaussian form such that the marginal and posterior distributions will also be Gaussian and the likelihood functions are tractable. That is, the marginal likelihood is maximised through direct gradient ascent or through the use of EM algorithm.

Might be easier to formulate a model, but analysing the data in an interpretable way involves projecting data onto subspaces and then analysing those trajectories still. In the original paper they do this using a method called sequential PCA (seqPCA) to find the compnents that correspond with different timepoints in the rotating dynamics.


### Inference


### References

- Original two papers