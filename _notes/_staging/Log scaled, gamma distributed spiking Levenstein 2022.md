---
title: Logarithmically scaled, gamma distributed neuronal spiking
usemathjax: true
---

> **tl;dr:**  

>**Citation:** @inproceedings{DBLP:journals/corr/KingmaW13,
  author    = {Diederik P. Kingma and
               Max Welling},
  editor    = {Yoshua Bengio and
               Yann LeCun},
  title     = {Auto-Encoding Variational Bayes},
  booktitle = {2nd International Conference on Learning Representations, {ICLR} 2014,
               Banff, AB, Canada, April 14-16, 2014, Conference Track Proceedings},
  year      = {2014},
  url       = {http://arxiv.org/abs/1312.6114}
}


**Paper link:** [https://physoc.onlinelibrary.wiley.com/doi/pdf/10.1113/JP282758](https://physoc.onlinelibrary.wiley.com/doi/pdf/10.1113/JP282758)

---

# Background
- Interval distributions and the average firing rates across populations of neurons are often gamma or distributed
- Better to visual log-normal or gamma distributions on a log scale
	- transforms differences in exponential rates to a translation 
- Many neurons are silent (firing rates across the population has been shown to be log-normal)
# Summary


# Key Findings
- LIF neurons in fluctuation driven regime are approximately gamma and better plotted on a log scale (okay, but not new)
- Interval distribution in the non-stationary context can be seen as a mixture of gamma dsitributions (they act like different activation states similar to energy levels)
- CV decreases as the firing rate increases. Approximately 1 when firign rates are low. 
- Average firing rates follows a Lorentz curve (shown below)
	- Spiking budget is not uniform across the population. Some neurons spike a lot more than others. 
- Neuropixel probes miss out on some of the very low firing rate neurons (dark neurons)
- Lorentx curve better fit by gamma distributed firing rates
- Different brain areas have distinct Lorenz curves (why???)
- Log-rate distriubtion get stretched between non-REM and REM sleep and low/high arousal
- Fluctuation-driven neurons are naturally log-scaled because of having a supra-linear I/O function
	- transforms Gaussian input (CLT) into a distribution with a heavy tail
- E/I interaction can also cause E/I gamma oscillations (Brunnel 2000, Buzaki 2012)
- E/I balalnce changes ground state activity, but not active states (this is thought to be due to dendritic activty etc)
- Computational benefits of this firing regieme (mostly low rates)
	- energy conservation 
	- spiking at specific timescles can have import roles for signal propagation (multiplexing) and synpatic processes
	- Heterogeneous networks are more robust to changes from synaptic plasticity
- Log-scale firing rates are also present in spinal cords of turtles (spinal cord circuitry is much older than cortex, has glycine instead of GABA!)

# Take-home message
- Interval distributions and the average firing rates in a population are often log-scaled (log-normal or gamma). 
- Log-scaled distributions are good for computation
	- Q: But are they best? What about other scalings? 

# Favorite Figure

- Shows the Lorenz curves
	- we expect the line to be horizontal if all neurons contribute equally to the firing budget
- Firing rate dist is approx gamma because of supra-linear I/O function and gaussian inputs because of the CLT
	
![[fig.png]]