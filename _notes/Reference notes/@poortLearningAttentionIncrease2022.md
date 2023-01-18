---
title: Learning and attention increase visual response selectivity through distinct mechanisms
authors: Jasper Poort, Katharina A. Wilmes, Antonin Blot, Angus Chadwick, Maneesh Sahani, Claudia Clopath, Thomas D. Mrsic-Flogel, Sonja B. Hofer, Adil G. Khan
year: 2022
---
#attention #experimental #noise-correlations #micro-circuit #V4 #mouse


# Background

- Learning and attention selectively enhance the processing of behaviorally relevent stimuli
	- increase in stimulus-evoked firing rates
	- changes in noise correlations (interactions between neurons)
	- these changes are restricted to subsets of neurons in the population
	- both learning and attention lead to sharper and more distinct information being sent to down-stream regions though subnetworks

- Interneurons also change their activity during learning and attenion (Look at citations)
	- more stimulus specific inhibition in the network
- Both attention and supervised learning are thought to rely the interaction between top-down and bottom-up inputs
- Learning and attention have been hypothesized to rely on similar neural mechanism [[@niLearningAttentionReveal2018]]
	- Or attention may co-opt circuitry used for learning (Kuchibhotla et al 2017 - read this)

- Is there a common subset of neurons modulated by attention and learning?
	- Do neurons undergo similar stimulus selectivity changes in firing rates?
	- Does learning and attention result in similar changes in interactions between excitatory and inhibitory cells?


# Experimental details

- Head-fixed mice, freely running, go-no go visual discrimiation task in a virtual maze
	- choice between two angled gratings, lick for vertical
	- mice could perform the task with 85% accuracy
- Attention switching between visual discrimiation and olfractory discrimination task
	- mice had to ignore the grating stimuli (occured 70% of the time) during these blocks 
	- This doesn't seem like it would be testing covert attention because the mice are free to saccad anywhere in the virtual maze
		- maybe this is measuring overt top-down attention
		- may have some bottom-up attention as well, since we do not know if the odors are that different from the backrgound?
		
- two-photon calcium imaging of L2/3 in V1
	- immunihistochemically strain brain slices to determine the cell types (PV, SOM, VIP) + excitatory PYR neurons
	- Neurons close to eachother (~ 20-100 um)

# Key findings

- Selectivity changes at the population level are similar across learning and attention
	- PYR and PV neurons showed an increase in average stimulus selectivity during attention and learning
	- SOM and VIP neurons did not show a signifcant change

- Selectivity changes at the single cell level are uncorrelated
	- All neurons selectivity was correlated between the post-learning and attend conditions (no change in what stimuli the neuron was responsive to)
	- All neurons change in selectivty for attention and learning was uncorrelated

- Mechanisms of selectivity change
	- Neurons can either increase their responses to prefered stimuli or decrease responses to non-prefered stimuli (Lee 2012 - Read this)
	- PYR cells decrease their stimulus response amplitude during learning (rewarded/unrewarded stimuli)
	- PYR cells changes more uniform for attention
	- Learning, unlike attention, was dominated by a suppression of responses
	- Attention showed both an increase and decrease in responses (mainly increase)

- Changes in interactions between excitatory and inhibitory cell classes
	- SOM cells decorrelated from PYR, PV, and VIP 
	- Reduction in nosie correlations between SOM-PV, SOM-VIP, and SOM-PYR cell pairs during learning
	- Largest absolute changes in noise correlations occured between pairs of the same cell types, mainly (SOM-SOM increase, VIP-VIP decrease). PYR-PYR and PV-PV also showed a decrease in noise correlations
	

- Modeling the changes
	- Linear auto-regressive model was fit to the neuron responses
	- Learning was associated with a reconfiguration of weights/interactions between neurons
	- Attention was associated with 


# Take-home message

- Effects of learning and attention uncorrrelated at the single cell level
- Distinct patterns of firing rate changes underlie increases in selectivity durign learning and attention
- learning and attentnion had different chaneges in functional intercations between cell classses

# Favorite figure

![[poort_Attention.png]]