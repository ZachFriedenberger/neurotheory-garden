---
title: A theory of cortical responses 🟥
usemathjax: true
---

> **tl;dr:**  

> **Citation:**  


**Paper link:** [https://elifesciences.org/articles/71263](https://elifesciences.org/articles/71263/)

---
# Introduction
- Understand neural responses in terms of perceptual inference and learning
- Distinction between percepts (recognizing causes of sensory input) and sensation 
- Recognition  
	- depends on models learned from experience
	- is the inverse of the of generating sensory data from their causes
	- Emperical bayes
		- heirarchical model of how data is caused
		- [[predictive coding]] is an implemtation of emperical bayes
		- 
- emperical bayes and [[predictive coding]] are related to "analysis-by-synthesis"
	- An appraoch to perception from cognitive psychology
	- adapting internal model to match sensory input
	- espistemological automata (MacKay 1956)
	- [[Rao and Ballard (1999)]] is an implemtation of this
	- These models emphasize backward connections in mediating predictions of lower level input, based on acitivity of higher coritcal areas
	- This is also related to the burst predictive coding paper (not yet published)
- Recognition = solving an inverse problem by minimizing prediction error at all levels of the hierarchy
- cortical responses = transient expressions of predicition errors
- This perspective accomodates experiemental observations
	- extra classical refecptive fields
	- repetition suppresion
	- MMN and P300 in ERPs?
	- These emerge from basic principles of inference in hierarchical generative models
- Orignal theory paper (Friston 2002 and 2003)

- Generative models can solve inverse problems in the nonlinear setting

# Functional specialization and integration


## Background
- Each area of the brain is thought to be associated with a seperate function (Brodmann)
- Early excitation studies inconclusive because connected pathways could have an effect (1881 conference on localization of function in the cortex cerebri)
- Lesion studies were used instead (disconnection syndromes)
- Functional specialization is only meaningful in the context of functional integration and vice versa


## Functional specialization and segregation

- Cortical connectivity rules
	- cells with similar functional properties are grouped together
	- "patchy connectivity"

## Anatomy and physiology of cortico-cortical connections
- extrinsic connections coupled external areas
- intrinsic connections are confined to the cortical sheet
- forward vs backward connections (Maunsell and Van Essen 1983)

### Intrinsic cortico-cortical connections
Hierarchical organization (Mesulam 1998)
- hierarchy of cortical levels
- forward from lower to higher areas
- backward from higher to lower areas
- lateral connections within a level 

Reciprocal connections 
- laminar specificity
- forward connections are topographically organized 
	- originate in supragranular layers (1, 2, 3)
	- spares axonal bifurcations
	- terminate in layer 4
- backward
	- diffuse topgraphy
	- abundant axonal bifurcations
	- originate in the infragranular layers
	- terminate in agranular layers
	- more divergent
- Much more backward connections than forward connections!
	- 1:10 in LGN
	- backward also traverse multiple levels in the heiarchy while forward levels do not
		- TE to V1, but not the other way around


- Backward connections modulate responses to forward inputs
- **The driver can transmit RF properties while the modulator can be identified as altering the probability of certain aspects of transmission (i.e., like the burst probability) (Sherman and Guillery 1998)**

Summary of the above:

- forward connections are concerned with the promulgation and segregation of sensory information is consistent with: (i) their sparse axonal bifurcation; (ii) patchy axonal terminations; and (iii) topographic projections. In contrast, backward connections are considered to have a role in mediating contextual effects and in the co-ordination of processing channels. This is consistent with: (i) their frequent bifurcation; (ii) diffuse axonal terminations; and (iii) more divergent topography
	- Crick and Kock 1998

- In the cat LGN, cortical feedback is partly mediated by type 1 metabotropic glutamate receptors, which are located exclusively on distal segments of the relay-cell dendrites. Rivadulla et al. (2002) have shown that these backward afferents enhance the excitatory centre of the thalamic RF.

Associative plasticity
- STP/STD vs LTP/LTD
- Long term = protein syntehsis, synaptic remodelling and structural changes
- An important aspect of NMDA receptors, in the induction of long-term potentiation, is that they confer associativity on changes in connection strength. This is because their voltage-sensitivity allows calcium ions to enter the cell when, and only when, there is conjoint pre-synaptic release of glutamate and sufficient postsynaptic depolarization (i.e. the temporal association of pre- and post-synaptic events).
- Calcium entry renders the post-synaptic specialization eligible for future potentiation by promoting the formation of synaptic ‘tags’ (e.g. Frey & Morris 1997) and other calciumdependent intracellular mechanisms
	- Somehow related to eligibility traces???

- In summary, the anatomy and physiology of cortico-cortical connections suggest that forward connections are driving and commit cells to a prespecified response given the appropriate pattern of inputs. Backward connections, on the other hand, are less topographic and are in a position to modulate the responses of lower areas. Modulatory effects imply the postsynaptic response evoked by presynaptic input is modulated by, or interacts in a nonlinear way with, another input. This interaction depends on nonlinear synaptic or dendritic mechanisms.


## Representational Inference and Learning


### Causes and representations
- representation = some neural response that represents some "cause"
- Causes may be categorical (idenitiy of a face)
- or semantic?
- parametric (position of the object)
- e.g. let causes be a deterministic function $u=g(v,\Theta)$ 
	- $v$ is a vector of underlying causes in the environment
	- $u$ is the sensory input
- brain must perform a nonlinear unmixing of causes and context
- recognition of causes from sensory data is the inverse of generating data from causes
- if the generative model is not invertible, the recignition can only occur if there is an explicit generative model in the brain 

### Generative models and representational learning
- The goal of the generative model is to learn representations that are economical to describe but allow the inout to be reconstructed accurately
- This relates to the distinction between inference and learning

#### Inference versus learning
- The objective is to make inferences about the causes and learn the parameters 
- Inference could be estimating the most likely cause of the sensory data
- Generative model is define with a prior over tha causes and a likelihood of the data given the causes

$$p(u;\Theta) = \int p(u \vert v ; \Theta)p(v;\Theta)$$

The recognition model is defined than as the inverse given by Bayes Rule. 

$$p(v \vert u;\Theta) = \frac{p(u\vert v; \Theta)p(v ; \Theta)}{p(u ; \Theta)}$$
- This may be intractable (not inverted easily) requiring that we instead optimize a variational distribution $q(v \vert u ; \phi)$ 
- Estimating moments of this distribution = inference 
- Estimating the parameters of the generative model = learning
- This maps directly onto the [[EM  algorithm | expectation-maximization algorithm]]


#### Expectation maximization
