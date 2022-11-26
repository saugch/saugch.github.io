---
aliases: [Evolutionary models]
subject: Mathematical models in Biology
lecturer: Jesús Fernández
format: in-person
program: Master in Advanced Mathematics and Mathematical Engineering
dates: 12-09-2022, 14-09-2022
tags: #mamme #mathmodels #biology, phylogenetics
---
# Evolutionary models
## Markov matrices
Square matrix with real entries $\geq 0$ whose *rows sum to 1* is called a Markov matrix (or stochastic matrix). Equivalent to seighg that the vector $(1, \dots 1)^T$ is an eigenvector of eigenvalue 1.

In general our Markov matrices will be $4 \times 4$ (4 nucletoids).

###### Theorem (Perron-Frobenius)

###### Claim
...
1. 
2. 
3. [[convex sum]] of Markov matrices
Is $\Delta_n$ a [[Algebraic group]]? In other words, is the inverse of matrix A also a Markov matrix?
The answer is **no**. Per [[#Theorem Perron-Frobenius]], all eigenvalues are upper bounded by 1.

Consider
$$$\begin{pmatrix} \frac{1}{n} & \dots / \frac{1}{n} \\\\ \frac{1}{n} & \dots / \frac{1}{n}  \end{pmatrix}$$
The determinant is 0 and it's not invertible (Proof in book in the slides).

### Conditional probabilities
A is independent of B: $A \perp \!\!\! \perp B$.

...
Let's say A is independent of B given C: $A \perp \!\!\! \perp B \:|\: C$. Two dependent events that become independent once we assume a third event.

### Discrete-time probabilistic processes
In all this teory, time is considered discrete.

### Discrete-time Markov processes
A discrete-time probabilistic process is called a Markov process if future is independent of past given the present.

I don't care about what happened yesterday: like in the getting sick or the weather example. It's not the case for the "self-avoiding random walk".

We can attach a matrix $M(n)$ to run the transition from one state to the other. It's a Markov matrix. We call them **Markov matrices**.


## Evolutionary models
**Models**: Simplifications of reality. 
Models are appropiate or not depending on what we want to study.
More complex models does not mean better models.

**Substitution models**: What happens at each step. We have a sequence of genes that is transmited and we want to understand the rule of how the substitution may act.

### Nucleotide substitution models
- Assumption: Biological hereditary information encoded in the DNA
- Code of 4 nucleotides: A, G, C, T
- Double helix structure: pairing A-T, G-C
- The order or sequence determines the information available for building proteins (every 3 is an aminoacid)
- It can make copies of itself.

Let's assume a sequence of nucleotides $S=TCAACTTGATC$ changing through an evolutionary process $$S_{0} = S \rightarrow S_{1}\rightarrow S_{2}\dots$$
Possible changes:
- *Substitutions* (error in duplication):We will focus in this one.
- *Insertions*
- *Deletions*
We won't include insertions or deletions. Not realistic but it's the typical way of modeling.

#### Homogeneous Markov models
Each site follows a discrete-time probabilistic process. We only care if each position is an A, C, G, T

*Hypothesis*
- *iid hypothesis*: Each site of the sequence evolves independently of the other sites and with the same probabilities. It's the same probability of changing in the end of the sequence that in the beginning (homogeneity across sites). *Not realistic*: Also because of the genetic code, substitutions in the 3rd nucletoid of the codon does not always matter.
- The process does not depend on the past given the present (Markov hypothesis)
- From generation to generation the same system of probabilities are ruling. This is not realistic if you consider a big amount of time. It's called homogeneity across lineages.

HOmogeneous Markov model is determined by
1. Transition matrix
2. Ancestral distribution $S_0$.

**How are we estimating them?**
- **Estimation**: With the relative frequency of changes
- **Ancestral distribution**: Count the relative frequencies of $S_0$. If $S_0$ is not available, we take $p_0$ as the [left eigenvector](https://mathworld.wolfram.com/Eigenvector.html#:~:text=is%20square%20is%20known%20as%20the%20eigen%20decomposition%20theorem.&text=which%20means%20the%20right%20eigenvalues%20must%20have%20zero%20determinant%2C%20i.e.%2C&text=%2C%20i.e.%2C%20left%20and%20right%20eigenvalues,is%20not%20true%20for%20eigenvectors.) of eigenvalue 1 of M.

### Jukes-Cantor Model (JC)
Simplest model
1. Distribution of the ancestral sequence is uniform: $p^{0}= (\frac{1}{4}, \frac{1}{4}, \frac{1}{4}, \frac{1}{4})$
2. Probability of obserivng a subsitution is the same (no matter the nucletoid)

### Kimura models
**Biological motivation**
Nucletoids have two groups according to biochemical structure. A substitution within the same type (within purines or within pyrimidines) is a transition, which is more likely. From purine to pyrimidine or the other way around, it's called transitions.

**3 parameter kimura model**
1. Uniform ancestral distribution
2. Particular structure of the matrix. 4 parameters but an extra restriction of the sum of probabilities = 1. 
From a mathematical point of view, the 3-parameter model is very nice to work with.

### Strand symmetric model (SSM)
Exploits the strand symmetric model. 6 free parameters (a,b,c and d fixed py the som to 1 and so on)

QUESTIONS: BUT WE ONLY LOOK INTO ONE STRAND OR NOT?

### General Markov model (GMM)
No assumptions. Most general model

## Stationary process
###### Definition
The nucletoid distribution as m goes to infinity goes to a stationary distribution $\pi = (\pi_{A}, \pi_{C}, \pi_{G}, \pi_{T})$.

In case the process is homogenous and the transition matrix M has only positive entries, because of [[#Theorem Perron-Frobenius]], we can garantee the limit exists. And the vector is the left eigenvector of M with eigenvalue 1. 

>This is related to dynamical systems

## Time reversibility
Time reversible if
- Stationary
- For any pair of nucleotides we need, the probability of getting X times the probability of X changing to Y must be equal to the probability of getting Y times the probability of changing Y to X. The idea of this is
	for $S_{0}= AGCAT$ and $S_{1} = ATCGA$, we do not really know if $S_0$ changed to $S_1$ or the other way around. Or, in other words, we don't know if one species evolved into another one or the other way around.

## Biology vs Maths
1. Time reversibility is assume in almost every paper in evolutionary.
2. It implies "time has no direction".
3. [[Felsenstein]] big guys in the field.
4. It can be shown that most of the models assuming this condition, needs to be multiplicative close. That means,
	If $S_{0}\rightarrow S_{1}$ is governed by $M_1$ and it's a JC model and then $S_{1}\rightarrow S_{2}$ is governed by $M_2$, then $S_{0}\rightarrow S_{2}$ is governed by $M_{1} \cdot M_2$  and should be also a JC model.  

---

[[Projects in Evolutionary models|Projects]]

---

# Recap
Jesus Sánchez
Slide 8: In GM, since the matrix is not necessarily symmetric, there's no time reversability.

### Continous models
Slide 10: Instead of transition probability, we consider the matrix Q, where the entries correspond to the speed of substitutions between nucleotides. You can imagine it like 4 pools (A, C, G, T) and you can imagine the Q matrix as the quantity of water going from one pool to another (and in the diagonal is the water remaining.)

This approach is much more strictive, because there's gonna be positive determinant for M and M will be non-singular (due to thefact that arises from $e^{Qt}$).

### Time reversability
$Q = RD(\pi)$ where $\pi$ is the ancient distribution or the equilibrium distribution. 

#### Felsenstein Hierarchy
You have an organitzation of different substitution models according to how many parameters are there.

### Mutation rate
Since the "time" is difficult to estimate, it's usually measured in terms of "number of expected subtitutions per site" when comparing sequencies. Under the continous-time approach, there's the mutation rate $\mu_{\pi, Q}$ quantity, which is just an estimation of the number of expected substitutions per site from the rate matrix. 

You can normalize Q so you have one substitution per unit of time. To compare Q's is better to take the normalized versions. 

### Evolutionary distances
It's important that they are symmetric (as in JC or the KM - see slides). In the log-det distance we have to define if it's from $S_0$ to $S_1$. It's not symmetric in general. You can get a very different value if you apply the formula in one direction or in the opposite one.

If it's time reversible, the formula is symmetric.

**Remark**
For continous time substitutions processes:
$$-\frac{1}{4}\log{\det{M(t)}} = -tr(D(\pi)Q)t$$
### Phylogenetic trees
*Cherry*: is a couple of neighbouring leaves. 
Remember: in a phylogenetic tree you have labels in the leaves.

To have the same tree, you need a graph isomorphism and you need to preserve the labeling.

It's unfeasible to list all the tree topologies when you have a big number of leaves (even 20 is big enough).

You can use Buneman's theory to define asymmetric difference between **trees**.

### Hidden Markov Models
We assume certain independence (slide 30) of processes. 

**Remark**: HMM and phylogenetic trees look very similar. You could try to use this idea of the forward algorithm to evaluate the probability of nucleotide pattern at the leaves: it's the *Felsenstein algorith*. So this is the same as the *forward algorithm* but applied to phylogenetic tree. And, at the same time, that was the same as the Horner's rule. 