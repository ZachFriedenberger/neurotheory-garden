---
title: Cortical state dynamics and selective attention define the spatial pattern of correlated variability in neocortex
authors: Yan-Liang Shi, Nicholas A. Steinmetz, Tirin Moore, Kwabena Boahen, Tatiana A. Engel
year: 2022
---

#attention #theory #correlatedactivity


# Background

- Noise correlations a modulated by behavioral and cognitive states (e.g., wakefullness, attention, etc) 
- Many recordings use Utah arrays which sample neurons from superficial layers across cortical columns
	- These studies show decreases in noise correlations [[@cohenAttentionImprovesPerformance2009]] 

- In V4, noise correlations decreased during attention only in input layers during stimulus evoked but not spontaneous activity
	- not observed in superficial or deep layers 
	- Reynolds 2018 paper Nat Neuro

- V1 noise correlations decrease only in supergranular layers 
	- no changes in granular or infragranular layers
	- Tolias 2018 Nat Comm

- Within column changes in noise correlation were smaller than across column changes 
	- This suggests that attentional modulation on correlated variability is not uniform
	- Depends on lateral distance and coritical layer

- Past theories are based on EI balance and a single global fixed point 
	- [[@huangCircuitModelsLowDimensional2019]] 
		- predicts spatail uniform changes in noise correlations
	- paper by Hennequin Ken Miller Nueron 2018
	- They do not capture the bistable switching 
	- 

# Key Findings

- Data was from a previous published Steinmetz paper, Eye movement preparation modulated neuronal responses... Data is freely availible online
- On-off dynamics predict magnitude of noise correlations
	- noise correlations were slightly reduced in superficial and enhanced in deep layers in the attention relative to control conditions
	- Noise correlations correlated with the number of HMM states
	- Change in noise correlations within columns much smaller than reductions across columns (an order of magnitude)

- Attention modulates the effective correlation length for lateral distances



# Take-home message

- On-off dynamics of population activity is a mjor source of changes in correlated variability 
- They find that this expalins the attentional modulation and dependence on lateral distance
- Attention modulates the On-off dynamics -> modulates the correlation length (scale of lateral correlations)

# Favorite figure
![[shi.png]]

# Data analysis

- Used 400-600 ms after cue onset to measure noise correlations (200 ms time bin)