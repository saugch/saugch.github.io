---
aliases: [Population dynamics]
subject: Mathematical models in Biology
lecturer: Gemma Huguet
format: in-person
program: Master in Advanced Mathematics and Mathematical Engineering
dates: 26-10-2022, 02-11-2022
tags: #mamme #mathmodels #biology
---
# Population dynamics

1. One dimensional models in ecology. A single species dynamics
	1. Continuous Models
	2. Discrete models
2. Dynamics of interacting populations
	1. Types of species' interactions.


## One dimensional models in ecology:
### Fibonacci sequence
First naive model. Idealised (biologically unrealistic) rabbit population.

###### Model
- $F_n$ : number of pairs of rabbits at month $n$
- $F_{0}$=1 (one male and one female)
- Rabbits are able to mat at one month old (at the end of its second month, a female can produce another pair)
- Rabbits never die and a mating pair always produces one new pair (one male, one female) every month.

*How many rabbits at month $n$*?
$F_{n}$ = # newborn pairs of rabbits + # adult pairs of adults = 
     = # young at month n-1 + 2 (# adults at month $n-1$)
     = $(F_{n-1} - F_{n-2}) + 2(F_{n-1})$ = $F_{n-1}+F_{n-2}$

- \# newborn pairs of rabbits = # pairs that did not exist at the month $n-1$:  $F_{n}- F_{n-1}$
- \# aduult pairs of rabbits = # pairs thatexist at the month $n-1$:  $F_{n-1}$

### Malthusian growth
From [[Thomas Robert Malthus]]
- $N(t)$: population size at time $t$
- $\frac{dN}{dt}$: births - deaths $\pm$ mgration

$\frac{dN}{dt} = bN - dN = (b-d)\cdot N$,  for $b, d>0$

The solution to this is $N(t) = N_{0}e^{(b-d)t} $, with $N_{0} = N(0)$.

This is a pretty good approximation for the population growth during the 18-20th century, but eventually populations need to compare for resources.

Link to population predictions by UN: https://population.un.org/wpp/Graphs/Probabilistic/POP/TOT/

### Logistic model
[[Pierre François Verhulst]]

It includes a negative term, dependent on the population squared:
$$\frac{dN}{dt} = m N - n N^{2}$$
This tends to saturation as the time grows:
$$lim_{t\to \infty} N(t) = \frac{m}{n}=k$$
where $k$ is also known as the **carrying capacity of the system**.

An alternative way of writing this is
$$\frac{dN}{dt} = m N\left(1 - \frac{n}{m}N\right) = rN\left(1-\frac{N}{k}\right)$$
For small $N$ small, $\dot{N} \sim rN$.
For large $N$, $N \sim k$.

#### Simple analysis

$$\frac{dN}{dt}= 0 = f(N) = rN\left(\frac{1-N}{k}\right)= 0$$
We have two equilibrim points, $N=0$, $N=k$.
(photo)

THis also has an analytical solution:
$$N(t) = \frac{kN_{0}}{N_{0}+(k-N_{0})e^{-rt}}, \qquad r>0$$ The limit behavior is:
$$lim_{t\to \infty} N(t) = \frac{kN_{0}}{N_{0}}=k \qquad \textrm{if } N_{0}\neq 0$$
$$N_{0}=0, \quad N(t) = 0 \qquad \forall t\geq0$$
When we do a simulation with $N_{0}$ small, we observe a sigmoid behavior: ![Sigmoid](https://www.google.com/url?sa=i&url=https%3A%2F%2Fwww.researchgate.net%2Ffigure%2FA-Basic-sigmoid-function-with-two-parameters-c1-and-c2-as-commonly-used-for-subitizing_fig2_326355896&psig=AOvVaw3IhUW757s-lD9ucFXiI2MM&ust=1666874827038000&source=images&cd=vfe&ved=0CA0QjRxqFwoTCIieneL2_foCFQAAAAAdAAAAABAM)

$$S(x) = \frac{B}{1+e^{-\frac{x-a}{\mu}}}$$
where $\mu$ is related to the slope of the sigmoid (see pictures)

### Logistic model with predator
##### Example: a model for Spruce Budworm
Most of the time, the population of this insect is under control. But every once in a while (10-15 years), it grows dramatically and destroys large parts of the forest. After the outbreaks, it goes back to original levels. 

Some birds eat this animals. When there's an outbreak, the birds are not able to keep the population of insects under control.

##### Model
Ludwig, Jones and Holling (1978)
$$N(t) \textrm{: population size of budworms}$$

$$\frac{dN}{dt} = r_BN\left(1-\frac{N}{k_{B}}\right)- p(N)$$
where now we account a predator species (birds):
$$p(N) = \frac{BN^{2}}{A^{2} + N^{2}}$$
where $p(n)$ models the mortality of budworms due to the predatory birds. This saturates at a value $B$. So, even if the population of budworm increases, then $p$ is still the same. We call $B$ the maximum predation rate. The parameter $A$ is the value at which the predation rate is the half of its maximum.

#### Adimensionalisation
**Change of variables**

$$u=\frac{N}{a} \quad r=\frac{Ar_{b}}{B} \quad q=\frac{k_{B}}{A} \quad \tau=\frac{Bt}{A}$$
$$\begin{align*}
\frac{du}{d\tau}&=\frac{du}{dt}\frac{dt}{d\tau} = \frac{1}{A}\frac{dN}{dt} \frac{A}{B} = \frac{1}{B} \frac{dN}{dt}\\
& =\frac{1}{B}\left[r_{B}A u\left(1 - \frac{Au}{k_{B}}\right) - \frac{Bu^{2}A^2}{A^{2}+u^{2}A^{2}}\right]\\
u' &= ru\left(1-\frac{u}{q}\right) - \frac{u^{2}}{1+u^{2}}= f(u)\end{align*}
$$
Now we have a new parameter $q = \frac{k_{B}}{A}$. If we consider $A$, $B$, $r_{B}$ fixed,
we can see that for low $q$, there's only one fixed point. If $q$ increases, two more fixed points appear, one of them stable as well. However, if you have a small starting population, you won't reach it. 

If then you keep increasing $q$, you lose the first stable point, and we have a jump to $u^*_3$. Now the birds can no longercontrol the worms populations.

But these worms kill the forest, so $q$ will start decreasing until eventually $q$ is so low that you are back to scenario 1.  (Cusp bifurcation?)

[Example to play with](https://mathinsight.org/spruce_budworm_outbreak_model)

#### Discrete models for a signle species dynamics
$$N_{k} \textrm{ : population size at time } t_{k,}\quad k\in \mathbb{N}$$
This is a sequence: $\{N_k\}_{k\in\mathbb{N}}$ and a quite general expression for them is
$$N_{k}= N_{k-1} f(N_{k-1})$$

For instance, when $f(N_{k}) = r$, we have discrete Malthusian, $N_{k}= N_{k-1} r$. For $r>1$ ,  $N_{k} \to \infty$ for $k\to\infty$ and for $r<1$, $N_{k}\to0$.


## Dynamics of interacting populations. Types of species' interactions.
### Types of interactions
- **Interespecific interactions**: One population affects another species' populations.

| Name                    |     |     |
| ----------------------- | --- | --- |
| Mutualism               | +   | +   |
| Competition            | -   |  -   |
| Predation or parasitism | +   | -   |
| Commensalism            | +   | 0   |
| Amensalism              | -   | 0   |
| Neutralism              | 0   | 0    |

### Kolmogorov systems
$$\begin{cases}
x_{i} &\textrm{ :  density of species }i \qquad i=1\dots n \\
n  & \textrm{:  \# species}
\end{cases}$$
The system are
$$\dot{x}_{i}  = x_{i}f_{i}(\vec{x})$$
with $\vec{x} = (x_{1}, x_{2}, \dots, x_{n})$,
and $f_{i}: \mathbb{R}^{n} \longrightarrow \mathbb{R} \quad \mathcal{C}^1$ which models the interaction with other species as well of self interaction.

We know $x_{i}= 0$ means that $\dot{x}_{i}=0$, so that $x_{i}(t) = 0, \quad \forall t \geq 0$. In other ords, the coordinate axes are invariant subspaces of the system.

### Lotka-Volterra
$$\frac{\dot{x}_{i}}{x_{i}}= r_{i}+ \sum\limits_{j=1}^{n} a_{ij} x_{j}$$
where $r_i$ is the growth rate per individual of species $i$ and $a_{ij}$ is the interactions of species $j$ over species $i$, so that:
- $a_{ij}>0 \quad j \rightarrow i$, then +
- $a_{ij}<0 \quad j \rightarrow i$, then -

For the matrix,
$$\begin{pmatrix}a_{11} & a_{12} & \dots  & \dots\\ \dots & a_22 & \dots & \dots \\ \vdots & & & \vdots \\ a_{n1} & a_n2 & \dots & a_{nn}\end{pmatrix}$$
the diagonal corresponds to the intraspecific interactions.

As an example, we can take $n=2$:
$$\begin{align*}
\dot{x}_{1} &= r_{1}x_{1}\frac{1-x_{1}}{k_{1}}- c_{1}x_{1}x_{2} \quad c_{1}> 0\\
\dot{x}_{2} &= r_{2}x_{2}\frac{1-x_{2}}{k_{2}}- c_{2}x_{1}x_{2} \quad c_{2}> 0
\end{align*}$$
The linear system will be:
$$\begin{pmatrix} \frac{\dot{x}_{1}}{x_{1}} \\ \frac{\dot{x}_{2}}{x_{2}} \end{pmatrix} = \begin{pmatrix} r_1 \\ r_{2}\end{pmatrix} + \begin{pmatrix} - \frac{r_{1}}{k_{1}} & -c_{1} \\ -c_{2} & - r_{2}/k_{2}\end{pmatrix}\begin{pmatrix}x_{1} \\ x_{2}\end{pmatrix}$$
We will perform a change of variables:
$$u = \frac{x_{1}}{k_{1}} \qquad v = \frac{x_{2}}{k_{2}}\qquad \tau = r_{1}t$$so that:
$$ \frac{du}{dt}= \frac{1}{k_{1}}\frac{dx_{1}}{dt} \qquad \frac{dt}{d\tau}=\frac{1}{r_{1}}$$
and then
$$\begin{align*}
{u}' &= \frac{du}{d\tau} = \frac{du}{dt}\frac{dt}{d\tau} = \frac{1}{k_{1}r_{1}}\left(r_{1}uk_{1}\left(\frac{1-uk_{1}}{k_{1}}\right)-c_{1}uk_{1}(vk_{2})\right) = u\left(\frac{1-u-c_{1}k_{2}}{r_{1}}uv\right)
\end{align*}$$
and we define
... (ask for notes)

Unit square $[0, 1] \times [0, 1]$ is invariant by the dynamics:
$$\begin{align*}
\{u = 0\} \quad u'=0 \quad \{u = 0\} \textrm{ invariant}\\
\{v = 0\} \quad v'=0 \quad \{v = 0\} \textrm{ invariant}
\end{align*}$$
and
$$\begin{align*}
\{u = 1\} \quad &u'=- av < 0 \quad &v>0\\
\{v = 1\} \quad &v'=-pbw < 0 &u>0
\end{align*}$$

If I start in the unit square, I cannot leave: they will remain inside the unit square.

From the [[Poincaré-Bendixson theorem]], we can apply it so that we know we only have fixed points or orbits (check slides).

#### Nullclines
- **u-nullclines**: $u'=0 \Rightarrow u(1-u-av) = 0$, so that we have:
	- $u = 0$
	- $u = 1-av$
- **v-nullclines**: $v'=0 \Rightarrow pv(1-v-bu) = 0$, so that we have:
	- $v = 0$
	- $v = 1-bu$

#### Equilibrium points of the system
The equilibrium points of the system are when nullclines cross: $$\begin{align*}
u' = 0\\
v' = 0
\end{align*}$$
so $$(u^{*}, v^{*}) = \begin{cases}
u = 1-av \\
v = 1-bu
\end{cases}$$
This point falls inside the $[0, 1] \times [0, 1]$ if
$$0 \leq u^{*} = \frac{1-a}{1-ab} \leq 1 \qquad 0 \leq v^{*} = \frac{1-b}{1-ab} \leq 1$$or, in other words if $a, b$ are both $> 1$ or $< 1$.

Check picture for both cases.

The **equilibrium point** is a point of coexistence for both species.

#### Linear stability analysis
$J(u, v) = DF(u, v) = \begin{pmatrix}1-2u-av & -au \\ -bpv & \rho(1-2v-bu)\end{pmatrix}$
- For the origin:
	$$J(0, 0) = \begin{pmatrix}1 & 0 \\ 0 & \rho\end{pmatrix} \Longrightarrow \textrm{eigenvalues} \begin{cases}
\lambda_{1}= 1 > 0 \rightarrow e_{1}=(1,0)\\
\lambda_{2}= \rho > 0 \rightarrow e_{1}=(0,1)
\end{cases}$$
	$\Rightarrow (0, 0)$ is a repulsor.
	*If we have some individuals from one (or both species) the population will grow*

- For the points in the axis:
	$$J(1, 0) = \begin{pmatrix}-1  & -a \\ 0 & \rho(1-b)\end{pmatrix} \Longrightarrow \textrm{eigenvalues} \begin{cases}
\lambda_{1}= -1 < 0 \rightarrow e_{1}=(1,0)\\
\lambda_{2}= \rho(1-b)\begin{cases}
> 0 \textrm{ if } b < 1 \\
< 0 \textrm{ if } b > 1
\end{cases}  \rightarrow e_{2}=(0,1)
\end{cases} $$
	$\Rightarrow$ (1, 0) is an **attractor** if $b>1$ and a **saddle point** if $b<0$
	$$J(0, 1) = \begin{pmatrix}1-a  & 0 \\ -b\rho & \rho\end{pmatrix} \Longrightarrow \textrm{eigenvalues} \begin{cases}
\lambda_{1}= 1 -a  &\rightarrow e_{1}=(1,\beta)\\
\lambda_{2}= -\rho &\rightarrow e_{2}=(0,1)
\end{cases} $$
	$\lambda_{1} > 0$ if $a<1$ $\Rightarrow$ **saddle point**
	$\lambda_{1} < 0$ if $a>1$ $\Rightarrow$ **attractor**

- Finally, for the point inside the unit square:
$$J(u^{*}*, v^{*}) = \begin{pmatrix} \dots & \dots \\\dots & \dots\end{pmatrix} \Longrightarrow \begin{cases}
a<1, \; b<1 \Rightarrow \lambda_{1}, \; \lambda_{2} < 0 \quad 
\textrm{attractor} \\
a>1, \; b>1 \Rightarrow \lambda_{1}\cdot \lambda_{2} < 0 \quad 
\textrm{saddle point}
\end{cases}$$
	The resulting system is a **bistable system**: it has two attractors. The orange line is the separatrix: it's the stable manifold of the saddle point and it separates the basin of attraction of each attractor.

In the first situation ($a, b< 1$) both species can coexist. In the other situation, $a, b>1$, one species will lead to the others exclusion. 

> This makes me think of competition for languages: [[Competition in languages]]

### Classical Lotka-Volterra for predator-prey
$$\begin{align*}
N(t): &\textrm{ population of preys}\\
P(t): &\textrm{ population of predators}
\end{align*}$$
$$\begin{pmatrix} \frac{\dot{N}}{N} \\ \frac{\dot{P}}{P}\end{pmatrix} = \begin{pmatrix}a \\ -d\end{pmatrix} + \begin{pmatrix}0 & -b \\ c & 0\end{pmatrix}\begin{pmatrix}N \\ P\end{pmatrix}$$
Notice that in this model, the intraspecific interactions (the diagonal) are 0. And the preys lose from the interaction ($-b$) and the predators gain (c).

In the **absence of predators**, the evolutions of preys is described by the Malthusian growth:
$$\dot{N} = aN \quad N(t) = N_{0}e^{at}$$
However, in the **absence of preys**, the predators go exstinct:
$$\dot{P} = dP \quad P(t) = P_{0}e^{-dt}$$
#### Invariant manifolds and equilibrium points
- $\{N = 0\}$ and $\{P = 0\}$ are **invariant** for the dynamics.
- **Equilibrium points**: $$\begin{cases}
\dot{N} = 0 \quad N(a-bP) = 0 \rightarrow\begin{cases}
N=0 \\
P = \frac{a}{b}> 0
\end{cases}\\
\dot{P} = 0 \quad N(a-bP) = 0 \rightarrow\begin{cases}
N=0 \end{cases}
\end{cases}$$
> Check picture to finish this

#### Stability analysis

$$J(N, P) = \begin{pmatrix}a-bP & -bN \\ cP & cN-d\end{pmatrix}$$
For the **origin**:
$$J(0, 0) = \begin{pmatrix}a & 0  \\ 0 & -d\end{pmatrix} \Longrightarrow \begin{cases}
\lambda_{1}= a> 0 \\
\lambda_{2}= -d < 0
\end{cases}$$
> Èlia

#### The Lyapunov method
[[The Lyapunov method]]
> Put this on a new section

Check slides: The Lyapunov method

If $\dot{V} = 0$ it means that $V(x(t)) = cnt$ and if this happens we say that $V$ is the [[First integral]] of the system

For Lotka-Volterra, we rewrite:
$$\begin{align*}
\frac{1}{N}\frac{dN}{dt}= a-bP\\
\frac{1}{P}\frac{dP}{dt}= cN -d
\end{align*}$$
as
$$\begin{align*}
\frac{dN}{dt}\left(-c + \frac{d}{N}\right)`+ \frac{dP}{dt}\left(\frac{a}{P}-b\right)= 0\\
\frac{d}{dt}\left(cN `bP - d\ln{N} - a\ln{P}\right) = 0
\end{align*}$$> Check pictures

So, $x_{0}$ is **lypapunov stable** and is a center: the rest of the orbits are periodic around it. The place where I am is determined by the initial conditions.

With a suitable change of variables, one can see that this is the [[Hamiltonian]] and that this is not only a local behavior, but also a global. To do so, you introduce the new canonical variables $p$ and $q$. Then we can see that it's a Hamiltonian system. Since the transformation is valid for the whole system, then the behavior is valid for the whole system. 

The number of individuals form each population oscillates over time.

#### Volterra's principle
> Check slide
