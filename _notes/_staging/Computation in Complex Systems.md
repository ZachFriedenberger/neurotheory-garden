# Easy and Hard
- Why are some problems easier to solve than others?

## Two Kinds of Paths

- Eulerian path
	-  Bridges in Koningsberg Problem
	- Can you traverse the entire city only crossing all bridges exactly once
	- Euler used graph theory to solve this problem
	- Solution is related to the number of nodes and edges of the graph
	- Odd number of edges for each node makes it impossible
	- This is called an **Euler path**

- Hamiltonian path
	- path through a graph that cisits each node exactly once 
	- called a **Hamiltonian cycle** if the starting and ending nodes are adjacent
	- a graph with a Hamiltonian path is called **traceable**
	- Requires an exhaustive search process (i.e., no simple rule relating nodes and edges)
		- This is an exponential search tree
			- if there are n nodes it can take 2^n time
			- 2 ways to leave every node

Goal of theoretical computer science: When will we have to do this and what insights will allow us to skip it?

## Polynomials vs. Exponentials

- polynomial grows much slower with the n (e.g., number of nodes in the graph)

## Divide and Conquer
- breaking problem down into smaller steps 
- Towers of Hanoi 
- Recursion: break tasks into subtasks of the same structure
	- a function which calls itself


## Big 0 and All that

- Problem: family of puzzles/instances
- Chess is a finite puzzle. Can solve in O(1) time
- Chess on an NxN board is a problem!
- How does the computation time (memory or communication) T scale with the size n

- Don't worry about the constants
- f(n) = O(n^3), f(n) sclaes like n^3 or less
- f(n) = O(g(n) if there exists constants C and n_0 such that, for n>n_0, f(n) <= Cg(n)
- or: ratio f/g doesnt tend to infinity as n grows


- Big omega
	- f=omega(g) means f grows at least as fast as g: g=O(f)
	- ratio f/g doesn't tend to zero as n grows
- Big theta
	- f and g grow the same way 
	- can differ by a constant
- Little O
	- f grows more slowly than g
	- f/g tends to zero as n grows

## When the details don't matter
- n^2 bits for a nxn network matrix
- list of edges takes less memory when n is large, nlog(n)


# Algorithms and Landscapes

## Divide and conquer
- How long does it take to sort a list of n numbers?
- n! possible permutations - which is the right one?
	- merge sort uses divide and conquer
	- T(n) = 2T(n/2) +n , T(1)=0 (no work to be done for list of length 1)
	- n term is the merge and 2T(n/2) is the sorting of each half
- Fast-fourier transform is another example

## Dynamic Programming
- Alignment (insert, delete, or change)
	- e.g., gene edit distance or other optimization problem
- Basically optimization 

## Greedy Algorithm
- short-term strategy of choosing the largest weight
- e.g., minimum spanning tree
	- tree with the smallest total length
	- at each step add the shortest edge that doesn't complete a cycle
- Proof

- Traveling salesman problem
	- path through nodes, but doesn't branch
	- greedy approach doesn't work


## Landscapes
- possible local minima/maxima in the space of possible solutions
- reorganizing the landscape: max flow

# Reductions and Translations
- transform one problem into another problem
	- what does this tell us about the hardness of the problem?
- Date matching problem
	- transform problem to a max flow problem
	- bipartite matching complexity <= max flow complexity

## Lessons so far
- we only know a small number of families of algorithms that are guaranteed to be efficient
	- divide and conquer
	- dynamic programming
	- greedy (local search)
	- linear programming, convex programming, and duality

- Are there others we haven't found yet? Are there fundamental limits to what efficient algorithms can do? 
- When can we show that no strategy works?

## The best of all possible algorithms
- is there some lower bound?
- how can we show that it is optimal?
	- this is an open area of computer science
- e.g., how hard is it to multipy two n-digit numbers?
	- Theta(n^2) time
- Divide and conquer


## Computation and complexity
- Systems aren't simple or complex: questions about them are
- What do you want to know about the system?
- Intrinsic complexity of a problem: the running time of the best possible algorithm for it: an objective mathematical fact
- Upper bounds are wasy: just give an algorithm
- Lower bounds are hard! 
- Can we show that the Hamiltonian path has a exponential lower bound on the time complexity
- Reductions show that one problem is at least as easy or hard as another


# P vs. NP
## Finding vs. checking
