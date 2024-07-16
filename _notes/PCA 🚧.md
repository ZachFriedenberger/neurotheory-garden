---
title: Principal component analysis (PCA)
usemathjax: true
tags:
  - dimensionality-reduction
  - machine-learning
  - unsupervised
---
> **tl;dr:** identifies an ordered set of orthogonal directions that captures the greatest variance in the data. 

---


- Obscures spiking variability (output noise) with firing rate variability (temporal changes in time). 
- Typically applied to smoothed or averaged neural data in which the spiking variability has been minimized
- For raw spike counts, use [[FA 🚧|Factor Analysis]], as this can decompose changes in FR from spiking variability. I.e., separate independent noise for each neuron. FA is PCA but with an explicit noise model. 


