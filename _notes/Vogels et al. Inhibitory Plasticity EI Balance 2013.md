---
title: Inhibitory Plasticity Balances
Excitation and Inhibition in Sensory
Pathways and Memory Networks
usemathjax: true
---

> **tl;dr:**  This paper proposes a simple Hebbian inhibitory plasticity rule that can maintain E/I balance in neural networks. The rule is able to self-organize the network into a state of detailed balance with asynchronous irregular spiking dynamics.

>**Citation:** @article{
doi:10.1126/science.1211095,
author = {T. P. Vogels  and H. Sprekeler  and F. Zenke  and C. Clopath  and W. Gerstner },
title = {Inhibitory Plasticity Balances Excitation and Inhibition in Sensory Pathways and Memory Networks},
journal = {Science},
volume = {334},
number = {6062},
pages = {1569-1573},
year = {2011},
doi = {10.1126/science.1211095},
URL = {https://www.science.org/doi/abs/10.1126/science.1211095},
eprint = {https://www.science.org/doi/pdf/10.1126/science.1211095}}


**Paper link:** [https://www.science.org/doi/full/10.1126/science.1211095](https://www.science.org/doi/full/10.1126/science.1211095)

---

# Background

- E/I balance is important for maintaining stable asynchronous irregular network dynamics (Brunnel, Somplolisky)
	- this is good for responding fast to changes in stimuli and for information processing (Harris, Vogels/Brunnel, review by Aeretas)
	- balanced amplifcation of selected inputs (selectively breaking balance to amplify certain inputs, Ken Miller)
- E/I is also tightly balanced in time (E followed shortly after by I)
- Not understood how this balance is maintained during experience/learning

# Summary
- Authors propose that E/I balance is maintained through a homeostatis inhibitory plasticity rule
- Plasticity rule tries to restore / maintain the balance of E/I

# Key Findings
- inhibitory rule $\Delta w = \eta (post \times pre - p_{0} \times pre)$, where $p_{0}$ is the target post-synaptic firing rate
- Rule can balance excitatory inputs given E/I starts in an unbalanced state
- Detailed balance (balance of each input channel) produced sparse spiking responses compared to global balance (total E/I balanced but not over individual input channels)
- Inhibitory rule captures change in frequency tuning of excitatory and inhibitory currents in rat primary auditory cortex
- Inhibiotry rule can restblish balance in recurrent networks
- cell assemblies can be encoded into the network (like a Hopfield attractor). Balance is restored. Then assembly can be activated with additional excitatory input. 
- CV in balanced state is approx 1.5

# Take-home message
- A simple Hebbian Inhibitory platicity rule can self-organize a state of E/I balance and asynchronous irregular activity


# Favorite Figure

- Shows how the inhibitory rule maintains balance in a recurrent network
- Shows how memories can be encoded in cell essemblies and reactived

![[Screenshot from 2022-09-14 17-26-22.png]]