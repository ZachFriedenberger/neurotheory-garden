---
title: Predictive Coding
usemathjax: true
---
Status: 🟥

- Postulate that **neural circuits estimate probabilistic models** of other neural activity and sensory inputs through feed-forward and feed-back processes. 

- Top-down neural projections are thought to carry predictions, while bottom-up connections carry predition errors, which update the state estimates. 

- Can be divded into **spatiotemporal** and  **heiarchical** settings.

## Spatiotemporal 

- Has been posulated to occur in the retina and LGN (lower levels of sensory processing)
- Predictions are formed across spatial dimensions and temporal sequences

- For the **temporal** setting, we can consider an [[autoregressive model]] defined over observation sequences. e.g., Gaussian AR model.

$$ p_{\Theta}(\bf{x}_{t}|\bf{x}_{<t}) = \mathcal{N}\bigg(\bf{x}_{t}; \bf{\mu}_{\Theta}(\bf{x}_{<t}), diag\big(\bf{\sigma_{\Theta}^{2}(\bf{x_{<t}})}\big)\bigg)$$


Using the [[reparameterization trick]], we can introduce an auxillary (noise) variable. $$\bf{y}_{t}\sim \mathcal{N}(\bf{0}, \bf{I})$$
Expressing the seqeunce as, $$\bf{x}_{t} = \bf{\mu_{\Theta}(\bf{x}_{<t})} + \bf{\sigma_{\Theta}^{2}(\bf{x_{<t}})} \odot \bf{y}_{t}$$
Which has an inverse given by, $$\bf{y}_{t} = \frac{\bf{x}_{t} - \bf{\mu_{\Theta}(\bf{x}_{<t})}}{\bf{\sigma_{\Theta}^{2}(\bf{x_{<t}})} }$$

We can think of this as a weighted prediction error. i.e., if past acticity is used to predict the next outcome of the sequence is a weighted error. 

This can be applied in the spatial dimension as well, by replacing time with multiple spatial dimensions. 

This kind of [[whitening]] can be used at stages of sensory processing to remove redundancy. 

- Retina is thought to perform a similar spatiotemporal normalization using center-surround receptive fields and on and off resposnes (Srinivasen 1982).

- Normalization in neural circuits uses inhibitory interneurons. i.e., lateral inhibition performs normalization. 
- Some how this is useful for video processesing??

## Hierarchical
- Has been postulate to occur in cortex because repeating layered structure 
	- Cortical columns interact locally via inhibitory interneurons and project up and down the hierarchy
	- Forward connections are driving, backwards connections are driving and modulatory
- Mumford 1992 - Thalamus is an active blackboard 
	- cortext tries to reconstruct the activity of the thalamus and lower hierarchical areas 
	- backward projections convey predictions and forward projections use prediction errors to update estiamtes
	- negative feedback is used in inference and learning. Minimize prediction errors. 
	- Model of this by [[Rao and Ballard (1999)]]
	- Generalization to [[variational inference]] by [[Friston (2005)]]

Consider a single level latent varaible model, with observations $x$ and latent varaibles $z$. 

$$p_{\Theta}(\bf{x}|\bf{z}) = \mathcal{N}(\bf{x};\mathcal{f}(\bf{Wz}), diag(\bf{\sigma_{z}^{2}}))$$

$$p_{\Theta}(\bf{z}) = \mathcal{N}(\bf{z};\bf{\mu_{z}}, diag(\bf{\sigma_{z}^{2}}))$$
Where $\mathcal{f}(\cdot)$ is an element-wise non-linearity. e.g., A sigmoid or hyperbolic tangent. 

To perform inference and fit the model to data, we can find the maximum-a-posteriori (MAP) estimate. 

$$\text{arg max}_{\bf{z}} \frac{p_{\Theta}(\bf{x}, \bf{z})}{p_{\Theta}(\bf{x})} = \text{arg max}_{\bf{z}} p_{\Theta}(\bf{x}, \bf{z}) = \text{arg max}_{\bf{z}} p_{\Theta}(\bf{x}|\bf{z})p_{\Theta}(\bf{z})$$

Where we have removed $p_{\Theta}(x)$ because it is often intractable as a result of the integration over the latent varaibles.

Plugging in the model above and simplifying (removing constants) we get

$$\text{arg max}_{\bf{z}} \bigg[-\frac{1}{2}\bigg|\bigg| \frac{\bf{x} - \mathcal{f}(\bf{Wz})}{\bf{\sigma_{x}}}\bigg|\bigg|^{2}_{2} -\frac{1}{2}\bigg|\bigg| \frac{\bf{z} - \bf{\mu_{z}}}{\bf{\sigma_{z}}}\bigg|\bigg|^{2}_{2}\bigg]$$


We can then evaluate the gradient $\nabla_{z}\mathcal{L}(\bf{z};\Theta)$, (for the linear case)



$$\nabla_{z}\mathcal{L}(\bf{z};\Theta) = \bf{W}^{T}\bigg(\frac{\bf{x}-\bf{Wz}}{\bf{\sigma_{x}}}\bigg) - \frac{\bf{z} - \bf{\mu_{z}}}{\bf{\sigma_{z}}}$$

$$\nabla_{z}\mathcal{L}(\bf{z};\Theta) = \bf{W}^{T}\bf{\xi_{x}} - \bf{\xi_{z}}$$

$$\nabla_{W}\mathcal{L}(\bf{z};\Theta) = \bf{\xi_{x}}\bf{z^{T}}$$
- Conditional likelihood $p_{\Theta}(x\vert z)$ is implemented by feedback connections while inference $\nabla_{z}\mathcal{L}(\bf{z};\Theta)$  is implemeted by the forward connections. Local errors $\xi_{x}$   and $\xi_{z}$ are implemeted using interneurons. 
	- Not quite clear on this yet!!?


## Some historically relevent papers
- Srinivasen 1982 - Retina
- Dong and Atick 1995 - Thalamus
- Mumford 199/1992 - Cortex
- [[Rao and Ballard (1999)]] - Formal model
- Kalman 1960 - Kalman filter


## Review papers
- Marino (2021) - Predictive coding + Autoencoders (this is the original paper I used to write these notes)


## New papers




