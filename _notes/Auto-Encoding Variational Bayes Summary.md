---
title: Auto-Encoding Variational Bayes 🟥
usemathjax: true
---

> **tl;dr:**  This paper shows how to perform efficient inference in directed probabilistic models with continuous latent varaibles, where the posterior or marginal distributions are intractable and dataset is large. The auto-encoder is shown as an example.

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


**Paper link:** [https://arxiv.org/abs/1312.6114](https://arxiv.org/abs/1312.6114/)

---

# Problem Formulation
 
Consider dataset $\bf{X}=\\{x^{(i)}\\}^{N}\_{i=1}$ with $N$ i.i.d. samples of random variable $\bf{x}$. Where $\bf{x}$ depends on the outcome of some unobserved latent varaible $\bf{z}$. i.e., $\bf{x} \sim p_{\Theta}(\mathbf{x}\vert\bf{z})p_{\Theta}(\mathbf{z})$.  


We want to perform inference in the case where there is:

1. *Intractability*: marginal likelihood $p_{\mathbf{\Theta}}(\mathbf{x})$ or the posterior density is intractable $p_{\mathbf{\Theta}}(\mathbf{z} \vert \mathbf{x})$ 
2. *Large datasets*: dataset is too large for [[sampling-based inference]] 
 

And we look for a solution that has:

1. Efficeint MLE/MAP estimation of the parameters $\mathbf{\Theta}$. 
2. Efficient approximate posterior inferrence of the latent variables $\mathbf{z}$, given observations $\mathbf{X}$ and a set of parameters $\mathbf{\Theta}$.
3. Efficeint marginal inference of variable $\mathbf{x}$. Which is necessary when a prior over $\mathbf{x}$ is required. 


# Solution 

- We introduce a variational distribution $q_{\mathbf{\mathbf{\phi}}}(\mathbf{z}\vert\mathbf{x})$  as an approximation to the true intractable posterior $p_{\mathbf{\Theta}}(\mathbf{z}\vert\mathbf{x})$. 

- We can think of $\bf{z}$ as a latent [[representation]] or *code*,  $q_{\mathbf{\mathbf{\phi}}}(\mathbf{z} \vert \mathbf{x})$ as a **probabilistic encoder**, and $p_{\mathbf{\mathbf{\Theta}}}(\mathbf{x} \vert \mathbf{z})$ as a **probabilistic decoder**. 

- We perform inference by combining [[amortized variational inference]] and a [[pathwise-based gradient estimator]]

**Note:** Not factorial and its parameters $\mathbf{\phi}$ are not computed from some closed-form expecation as is done in [[mean-field variational inference]]. 



## The variational bound
- Here we use the typical [[variational lower bound]] 

- For MLE inference we want to infere the parameters $\Theta$ by maximizing the log likelihood $\log{p_{\mathbf{\Theta}} (\mathbf{x^{(1)}}, \mathbf{x^{(2)}},..., \mathbf{x^{(N)}})} = \sum_{i=1}^{N} \log{p_{\mathbf{\Theta}}(\mathbf{x^{(i)}})}$. 

- Unfortunately $p_{\mathbf{\Theta}}(\mathbf{x})$ and $p_{\Theta}(\mathbf{z} \vert \mathbf{x})$ are often intractable because we have to marginalize over the latent varaibles

- We want to approximate the true posterior density $p_{\mathbf{\Theta}}(\mathbf{z} \vert \mathbf{x})$ with the variational distribution $q_{\mathbf{\phi}}(\mathbf{z} \vert \mathbf{x})$, so we want to minimize $D_{KL}(q_{\mathbf{\phi}}(\mathbf{z} \vert \mathbf{x^{(i)}}) \vert \vert p_{\mathbf{\Theta}}(\mathbf{z} \vert \mathbf{x^{(i)}}))$.

- Introduce unnormalized distribution $\tilde{p}_{\Theta}(z \vert x^{(i)}) = p\_{\Theta}(x^{(i)} \vert z) p\_{\Theta}(z) = p\_{\Theta}(z \vert x^{(i)}) p\_{\Theta}(x^{(i)})$.


Then we can write, 

$$\begin{align} J(q_{\phi}(z \vert x^{i})) &= \int_{Z}q_{\phi}(z \vert x^{(i)}) \log{\frac{q_{\phi}(z \vert x^{(i)} )}{\tilde{p}_{\Theta}(z \vert x^{(i)})}} dz\\ &= \int_{Z}q_{\phi}(z \vert x^{(i)}) \log{\frac{q_{\phi}(z \vert x^{(i)} )}{p_{\Theta}(z \vert x^{(i)})}} dz - \log{p_{\Theta}(x^{(i)}}) \\ &= D_{KL}(q_{\phi}(z \vert x^{(i)})\vert \vert p_{\Theta}(z \vert x^{(i)})) - \log{p_{\Theta}(x^{(i)}})\end{align}$$


Because $D_{KL}(\cdot \vert\vert\ \cdot)\geq 0$, we get the following inequality,

$$\log{p_{\Theta}(x^{(i)}}) \geq -J(q_{\phi}(z|x^{i})) = -\int_{Z}q_{\phi}(z|x^{(i)}) \log{\frac{q_{\phi}(z|x^{(i)} )}{\tilde{p}_{\Theta}(z|x^{(i)})}} dz$$


Then letting  $\tilde{p}_{\Theta}(z \vert x^{(i)}) = p\_{\Theta}(x^{(i)}\vert z)p\_{\Theta}(z)$ and simplifying we get,

$$\text{log} \space p_{\bf{\Theta}}(\bf{x^{(i)})}) \geq \mathcal{L}(\bf{\theta}, \bf{\phi};\bf{x^{(i)}})= -D_{KL}\big(q_{\phi}(z|x^{(i)}||p_{\Theta}(z))\big) +  \mathbb{E}_{q_{\bf{\phi}}(\bf{z|x^{(i)}})}\big[\text{log} \space p_{\Theta}(x^{(i)}|z))\big]$$


- To perform inference we then maximize $\sum_{i} \mathcal{L}(\bf{\theta}, \bf{\phi};\bf{x^{(i)}})$ wr.t. both $\Theta$ and $\phi$ 


## Naive gradient

- Typical score-function estimator of the gradient has high variance - Mohamed et al. (2020)
- Also known as a [[measure-based gradient estimator]]


e.g., Score-function gradient (this is how we approximate a gradient of an expectation)

$$\begin{align}\eta = \nabla_{\Theta} \mathbb{E}_{p_{\Theta}(x)}[f(x)] &= \int_{X}f(x)\nabla_{\Theta}p_{\Theta}(x)dx \\ &= \int_{X}p_{\Theta}(x)f(x)\nabla_{\Theta}\log{p_{\Theta}(x)}dx \\ &= \mathbb{E}_{p_{\Theta}(x)}[f(x)\nabla_{\Theta}\log{p_{\Theta}(x)}] 
  \end{align}$$
Where we have use the fact that, $$\nabla_{\Theta}\log{p_{\Theta}(x)} = \frac{\nabla_{\Theta} p_{\Theta}(x)}{p_{\Theta}(x)}$$
The emperical estimator then becomes, $$\begin{align} \hat{\eta} &= \frac{1}{N}\sum_{i=1}^{N}f(x^{(i)})\nabla_{\theta}\log{p_{\Theta}(x^{(i)})} \\ x^{(i)} &\sim p_{\Theta}(x) \end{align}$$
Need to work out estimator for model above as an example!


## The reparameterization trick
- Also known as a [[pathwise-based gradient estimator]]
	- Sometimes called the "push-in method" because the parameters are pushed inside and do not appear directly in the expectation
- Sample from a simpler base distribution then scale (e.g., Gaussian varaible can be representated as a mean + varaince)
- Has lower variance than score-based estimator when the number of parameters is large - Monte Carlo Gradient Estimation in Machine Learning 2020 (WHY??)


First we reparameterize $z \sim q_{\phi}(z \vert x)$ using the differentiable transformation $g_{\phi}(\epsilon, x)$ , where $\epsilon$ is an auxillary noise varaible

$$z \sim g_{\phi}(\epsilon, x) \space\space\space \text{with} \space\space\space \epsilon \sim p(\epsilon)$$

Then the gradient can be rewitten as,

$$\begin{align}\eta &= \nabla_{\phi} \mathbb{E}_{p_{\phi}(x)}[f(x)] \\ &= \nabla_{\phi} \mathbb{E}_{p(\epsilon)}[f(g_{\phi}(\epsilon))] \\ &=  \mathbb{E}_{p(\epsilon)}[\nabla_{\phi} f(g_{\phi}(\epsilon))] \end{align}
  $$
- Also known as the *Law of unconcious statistician* - Grimmett and Stirzaker (2001)

The emperical estimator then becomes, $$\begin{align} \hat{\eta} &= \frac{1}{N}\sum_{i=1}^{N}\nabla_{\phi}f(g_{\phi}(\epsilon^{(i)})) \\ \epsilon^{(i)} &\sim p(\epsilon) \end{align}$$

## Stochastic Gradient Variational Bayes (SGVB) estimators

- Two different estimators for when $D_{KL}(q_{\phi}(\bf{z \vert x^{(i)}})\vert\vert p_{\Theta}(\bf{z}))$ is either anlaytically intractable or tractable. 


For the **intractable case**:

 $$\begin{align}\tilde{\mathcal{L}}(\bf{\theta}, \bf{\phi};\bf{x^{(i)}})&= \mathbb{E}_{q_{\phi}(z|x^{(i)})}[\log{p_{\Theta}(x^{(i)}, z)} - \log{q_{\phi}(z|x^{(i)})}] \\ &\simeq \frac{1}{N}\sum_{n=1}^{N}\big[\log{p_{\Theta}(x^{(i)}, z^{(i, n)})} - \log{q_{\phi}(z^{(i, n)}|x^{(i)})}\big] \\ &\text{where} \space\space\space z^{(i,n)} \sim g_{\phi}(\epsilon^{(i,n)}, x^{(i)}) \space\space\space \text{and} \space\space\space \epsilon^{(n)}\sim p(\epsilon) \end{align}$$


For the **tractable case**: 

$$\begin{align}\tilde{\mathcal{L}}(\bf{\theta}, \bf{\phi};\bf{x^{(i)}})&\simeq -D_{KL}\big(q_{\phi}(z|x^{(i)}||p_{\Theta}(z))\big) + \frac{1}{N}\sum_{n=1}^{N}\big[\log{p_{\Theta}(x^{(i)}| z^{(i,n)})}\big] \\ &\text{where} \space\space\space z^{(i,n)} \sim g_{\phi}(\epsilon^{(i,n)}, x^{(i)}) \space\space\space \text{and} \space\space\space \epsilon^{(n)}\sim p(\epsilon) \end{align}$$


## AEVB Algorithm

We can then write the mini-batch estimator as:


$$\tilde{\mathcal{L}}^{M}(\Theta, \phi ; X^{M}) = \frac{N}{M}\sum_{i=1}^{M} \tilde{\mathcal{L}}(\Theta, \phi, x^{(i)})$$


Which gives us the following optmization/inference algorithm:

<img src="/assets/AEVB algorithm.png"/>


## Full VB
- Here is the extension to variational inference of both the generative model parameters $\mathbf{\Theta}$ and the latent variables $\mathbf{z}$ as opposed to just the latent varaibles $\textbf{z}$ as shown above.


- Introduce a variational prior $q_{\mathbf{\phi}}(\mathbf{\Theta})$ as an approximation to the true prior $p_{\mathbf{\alpha}}(\mathbf{\Theta})$

- 


## Variational Auto-Encoder Example

- Let prior over the latents be a standard normal $p_{\Theta}(z)=\mathcal{N}(z;0,I)$

- Let the decoder $p_{\Theta}(x \vert z)$ be a multivaraite Gaussian or Bernoulli distribution (continuous vs. discrete output) 

- Assume the encoder $q_{\phi}(z \vert x)$ is a multivaraite Gaussian with a diagonal covariance structure, $q_{\phi}(z \vert x) = \mathcal{N}(z;\mu^{(i)}, \sigma^{2^{(i)}}I)$. 
	- Where $\mu^{(i)}$ and $\sigma^{2^{(i)}}$ are the outputs of an MLP 


$$\begin{align}\tilde{\mathcal{L}}(\bf{\theta}, \bf{\phi};\bf{x^{(i)}})&\simeq -D_{KL}\big(q_{\phi}(z|x^{(i)}||p_{\Theta}(z))\big) + \frac{1}{N}\sum_{n=1}^{N}\big[\log{p_{\Theta}(x^{(i)}| z^{(i,n)})}\big] \\ &\text{where} \space\space\space z^{(i,n)} \sim \mu^{(i)} + \sigma^{(i)} \odot \epsilon^{(n)} \space\space\space \text{and} \space\space\space \epsilon^{(n)}\sim \mathcal{N}(0, I) \end{align}$$



### Bernoulli MLP decoder

$$\begin{align} \log{p_{\Theta}(x|z)} &= \sum_{i=1}^{D} x_{i}\log{y_{i}} + (1-x_{i})\log{(1-y_{i})} \\ y_{i} &= f_{\sigma}(W_{2}\tanh{(W_{1}z + b_{1})} +b_{2}) \\ \Theta &= \{W_{1}, W_{2}, b_{1}, b_{2}\}\end{align}$$


### Gaussian MLP decoder/encoder
$$\begin{align} \log{p_{\Theta}(x|z)} &= \log{\mathcal{N}(x;\mu, \sigma^{2}I)} \\ \mu &= W_{4}h + b_{4}\\ \log{\sigma^{2}} &= W_{5}h + b_{5}\\ h &= \tanh{(W_{3}z +b_{3})}\\\Theta &= \{W_{3}, W_{4},W_{5},  b_{3}, b_{4}, b_{5}\}\end{align}$$



# VAE vs. AE

1) VAE has a normalized latent space and AE do not
	- probability distribution adds a smoothness contraint to the latent space
	- allows the model to be used in generator mode like a GAN
		- i.e., can freely sample latent space to generate similar output
		
2) VAE's were consructed for general varraitional inference of latent variable models while AE's were not
