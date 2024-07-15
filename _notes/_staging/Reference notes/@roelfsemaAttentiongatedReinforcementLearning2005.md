---
title: Attention-gated reinforcement learning of internal representations for classification
authors: Pieter R. Roelfsema, Arjen van Ooyen
year: 2005
---

#attention #reinforcement-learning #plasticity #learing-rules

# Background

- Credit assignment problem - backpropagation of error is not biologically plausible
- Reiniforcement learning is more biologically plasuible - global error signal to the entire network based on reward
- Unknown how behaviorial relevence of stimuli influences sensory representaions and the mechanisms that guide plasticity
- Consequences of attentional feedback on learning in a neural network were not well known
- Feedforward and feeback connections are believed to be reciprocal


# Key-findings

- Learning rule with global error (reinforcement learning) and attention like feedback can approximate supervised learning performance

![[roelfsema.png]]

- Winning neuron at output choosen stochatically, then feedback from winning units modualtes the weight update for $v_{i,j}$ 
- Weight changes with AGREL are on average the same as those in BP

- They assume units are columns with different feedforward and feedback activity - feedback network propagates activity that modulates plasticity and not error signals
