
- A way to fit data with a Gaussian probability distribution at each point
	- e.g., linear regression
- Gaussian processes define a probability distribution over possible funtions for the data
- This can be extended to other problems
	- e.g., classification, clustering, latent variable models



## Multivaiate Gaussian distributions

- $\vec{\mu}$ is a vector of the means along each dimension 
- $\Sigma$ is the covariance matrix 
	- [[Symmetric matrix]] and [[positive semi-definite]]
	- diagonals are the individual varianes along each dimension $\sigma_{i}^{2}$

$X = [X_{1},  ..., X_{N}] \sim \mathcal{N}(\vec{\mu}, \Sigma)$ 

- We say $X$ follows a multidimensional normal distribution 

$\Sigma = \mathbb{E}[(X_{i}-\mu_{i})(X_{j}-\mu_{j})^{T}] = K(t_{1}, t_{2})$

- covariance funtion $K(t_{1}, t_{2})$ defines the "kernel" of the Gaussian process


## Kernels





