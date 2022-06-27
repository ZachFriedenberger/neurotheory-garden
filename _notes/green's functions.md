---
title: Green's Functions 
usemathjax: true
---

Status: 🟥

# Motivation
- We want a general technique to solve inhomogenous ordinary differential equations (i.e., dynamic inputs)
- Basic idea is to find how the system responds to a pulse input and then propagate the dynamic inputs using the greens function kernel

# Definition
Suppose we have a linear differential equation of the form, 

$$\mathcal{L}u(x) = f(x)$$
where $\mathcal{L}$ is a linear differential operator. 

We then look for a solution that is the inverse integral operator

$$u(x) = \int_{\Omega} G(x, x_0)f(x_0) dx_0$$

where $\Omega$ is the domain of $x_0$, and $G$ is called the green's function. We can think of $u(x)$ as the response at $x$ from the source function $f(x)$. Where the integral is adding up the influence of all the sources on the domain $\Omega$. Sometimes $G$ is also called the "response function" or "influence function".


We start by looking at the what appens when the source is a point source $f(x) = \delta(x-x_{i})$ 

$$$$

# Finding the Green's fucntion
Given an linear differential equation with some boundary conditions we can find the appropriate Green's function using the following conditions.

## Operator Condition
To find the greens function we look at the response to a point source $f(x) = \delta(x-x_{i})$

Plugging this into Eq. , we find, 

$$\mathcal{L}u(x) = \delta(x-x_{i})$$
plus some specified boundary conditions.

$$\begin{split} u(x) &= \int_{\Omega}G(x, x_{0})\delta(x_{0}-x_{i}) dx_{0} \\ 
&= G(x, x_{i})\end{split}$$

Because of the properties of the [[delta function]]


Plugging this into Eq. (), we find that the greens function must satisfy, 

$$\mathcal{L_{x}}G(x, x_{i}) = \delta(x-x_{i})$$
Where the subscript on $\mathcal{L_{x}}$ is notation for the differential operator acting on the variable $x$ and not on $x_{i}$.


- Note that $G(x,x_{i})$ and $G(x, x_{0})$ are the same function, so we can replace $x_{i}$ with $x_{0}$
- I was unable to find a name for this condition so I simply chose  "Operator conditon" because the condition only depends on the form of the linear differenital operator

## Boundary Conditions
- $G(x, x_{0})$ must satisfy the same boundary condtions as the initial problem

For example, take a homogensous Dirchlet boundary condition $u=0$ for all points on the boundary $x \in \partial \Omega$. 

Points along the boundary must satisfy

$$\int_{\Omega} G(x,x_{0})f(x_{0}) dx_{0} = 0 $$

This must hold for arbirtary choice of $f(x)$, therefore we conclude that $G(x,x_{0})=0$ on the boundary.

- The same thing can be shown for other boundary conditions (e.g., Van Neumann, mixed, etc.)

## Connection Conditions




# One-dimensional exmaple

We now show an example for finding the Green's function in one-dimension. In particular, we show how to find the Green's function for the stationary solutions to the [[ Neuronal Cable Theory|cable equation]]. 

$$\frac{d^{2}u(x)}{d x^{2}} - u(x) = -i_{ext}(x)$$

Subject to the boundary conditions

$$u(\pm \infty)=0$$
- This is also called the one dimensional Helmholtz problem


Using the operator condition we have a Green's function must satisfy

$$\frac{\partial^{2} G(x, x_{0})}{\partial x^{2}} -G(x, x_{0}) = \delta(x-x_{0})$$
or 
$$\frac{\partial^{2} G(x, x_{0})}{\partial x^{2}} -G(x, x_{0}) = 0$$
when $x\neq x_{0}$.



Which has the solution, 

$$G(x, x_{0}) = Ae^{-x} + Be^{x}$$

with the boundary conditions, 

$$\lim_{x \to \pm\infty}G(x, x_{0}) = 0 $$


Gives us. 
$$G(x, x_{0})=\begin{cases}
          Ae^{x} \quad &\text{if} \, x < x_{0} \\
          Be^{-x} \quad &\text{if} \, x > x_{0} \\
     \end{cases}
$$

for all possible point source locations $x_{0}$.

Using the conection conditions in Eq () and (),

We find that, 

$$G(x, x_{0})=\begin{cases}
          -\frac{1}{2}e^{(x-x_{0})} \quad &\text{if} \, x < x_{0} \\
          -\frac{1}{2}e^{-(x-x_{0})} \quad &\text{if} \, x > x_{0} \\
     \end{cases}
$$

Which can be rewritten more succinctly as, 

$$G(x, x_{0}) = -\frac{1}{2}e^{-\vert x-x_{0} \vert}$$

Plugging this into Eq. () we find the solution for an arbitray input is, 

$$u(x) = \frac{1}{2}\int_{-\infty}^{\infty} e^{-\vert x-x_{0}\vert} i_{ext}(x_{0}) dx_{0}$$

# Constructing new Green's functions from old ones

- We can find new greens function with different boundary conditions by using a superposition of the free-space solutions

For example, if we wish to solve the above equation on the domain $\Omega=[0, \infty)$ with boundary conditions $u(0)=u(+\infty)=0$

Our previous greens function no longer holds for the new boundary condition

for example, $G(0, x_{0})=-\frac{1}{2}e^{-\vert x_{0}\vert} \neq 0$ 


The key insight is that becasue the differential equation is linear, sums of the free-space greens functions will satisfy the operator condition as long as the additional impluse functions are outside the domain of interest. 

We can offset the constribution at $x=0$ by adding the reflection about the x axis

$$G(x, x_{0}) = G_{\infty}(x, x_{0}) + G_{\infty}(-x, x_{0})$$

 