# Physical Desing using Differentiable SImulators

- each node is updated using a neural network function of its neighbours
- Edges are also updated (information about the relations and not just the nodes themselves)
	- this seems like we are treating each neuron as a neural network (might correspond to dendrites or something)
- e.g., particles in a fluid (GNN simulator)
	- construct graph
	- then simulate??
- Add noise durign training (more robust)
- Can generalize to new arrangments easier 
- Can these simulators be used for inverse design/design problems? (Allen, Guevara Lopez Pfaff 2022 deepmind)
	- start with outcome/problem and find the optimal design
	- get Machine leanring to design new stuff
- Update designs through optmization!
	- can we do something similar to find optimal neural decoders?



# Why Dale's law? Peter Latham
- Dales law
	- neuron can be either all positive or all negative
	- almost always satisfied, even in invertebrates
- In a multilayer enural network
	- The larger the weights, the smaller the weight updates
	- More neurons = smaller the weight updates
	- small weights mean small activity changes
	- small changes are not helpful in a noisy environemnt
	- dales law networks are more resistent to noise
- Signal to noise analysis
- Start with a 2-layer network
- analyse it
- Vanilla ReLU deep network
- Found approximation for sclaing of the weight changes with the weights $\vert \Delta W \vert = \frac{1}{N\vert w\vert}$ ?
- I NEED TO REVIEW NOISE IN THE BRAIN REVIEW ARTICLE
- Read He Initialization and other papers
- Only excitatory neurons project fom layer to layer (inhibitory neurons are within each layer)


# Blake Richards

- Credit assingment is hard when rewards are sparse and there are multiple contingencies
- we learn invariant representations for sub-goals and reward
- We determine sub-goals by introspection and identify affordances that we require for success
- 