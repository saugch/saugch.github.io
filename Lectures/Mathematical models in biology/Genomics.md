---
aliases: [Introduction to MMiB]
subject: Mathematical models in Biology
lecturer: Jesús Fernández
format: in-person
program: Master in Advanced Mathematics and Mathematical Engineering
dates: 19-10-2022
tags: #mamme #mathmodels #biology
---

# Genomics
## Hidden Markov Models
>*Forward-Viterbi pdf in atenea*

### Decoding HMM
**Decoding** means to find out the sequences of $y$ that maximizes the probability of my observation. 

#### The Viterbi algorithm
The Viterbi algorithm provides a sequence (*path*) that has the highest probability of generating the observed samples.

#### Example
> Forward-Viterbi algorithm example

I'm looking for a minimum since I'm taking the negative logarithm of a probability. 

$v_0(3)$ is the maximum probability (minimum -log) of having A B B and a 0 as the hidden state above the last value. 

You take $e^{-whatever}$ to obtain the maximum probability of obtaining the observed sequences. To know the path, we can check the underlined quantities in the algorithm, which will tell us the path.

You start by the end. You know that $y_{3}= 0$. Then you go back and saw tha tthe minimum was observed for $y_{2} = 0$. And you keep going back. 

### Tropical arithmetics 
We define two new operations 
- Tropical sum $x \oplus y \equiv min(x,y)$
- Tropical product $x \odot y \equiv x + y$

You can express the Viterbi algorithm in this new tropical arithmetics. In the end, what we have is the same as the tropicalization of the forward algorithm.

The Horner rule applied to the tropical polynomial is the Viterbi algorithm. So, both the Viterbi algorithm and the Forward algorithm have the same structure.

#### Example
In Atenea, we have a [[SAGE maths]] workseet on HMM where you can play with HMM, apply the Viterbi algorithm, etc. 

---
*Date: 24-10-2022*
We will see two problems that can be seen as applications of the Hidden Markov Models.
## Sequence alignment
### Pairwise sequence alignment
Assume we have two sequences of nucleotoids,
$$\begin{cases}
\sigma_{1}= \sigma_{1}^{1}, \sigma_{2}^{1} \dots \sigma_{n}^{1} \\
\sigma_{2}= \sigma_{1}^{2}, \sigma_{2}^{2} \dots \sigma_{m}^{1}
\end{cases} $$ which may have different lengths $m$ and $n$ and we want to find a way to alignment.

We will see three ways that are different but equivalent.

#### Method 1
We define new pair of sequences, with alphabet 

#### Method 2
- *Homology*: We had a nucleotoid in both sequences (no matter if they are the same or not).
- *Deletions*
- *Insertions*

You need to impose two conditions on the new sequence formed by $H, D, I$ (eq. 1)

#### Method 3
Three different types of edges:
- Horizontal edges correspond to insertions
- Vertical vedges correspond to deletions
- Diagonal edges are labeled by the homologies

All possible paths correspond to all possible alignemnts
###### Example
(Picture / slides)

#### Scoring scheme
We are looking for good alignments. We need to define what optimal means in a mathematical way. For that, we need a **scoring scheme**

Each weight in $\{w\}_{i,j}$ corresponds to the weight from going from $i$ to $j$. The $4 \times 4$ matrix, corresponds to the homology case.

From biological point of view, once we open the possibility to insertion, an insertion right next to it should not be as penalized. So, all insertions that are consecutive, should all be penalized once.

That's the reason why we may want to use $w'$. The wieghts in $w'$ correspond to the weight $w'_{H, H}$ for a homology after a homology. In a way, it's the penalty for changing the "edit mode" in the alignment (passing from homology to insertions).

Given two sequences, we can define a score for the alignment. 

###### Def: Global alignment problem with scores
Fin the global alignment $h$ with minimal weight among all alignments of $\sigma_1$ and $\sigma_2$. 

This is equivalent to assigning weights to the edges of the aligment graph $G_{n,m}$.  With this notation, the previous problem is equivalent to finding the **shortest path** from node $(0,0)$ to node $(n, m)$. 

#### Needleman–Wunsch algorithm

#### Example
In the paper.

#### Pair Hidden Markov Model
This is essentially the Viterby algorithm. We can consider a Hidden Markov model:
- hidden states $\Sigma' = \{H, I, D\}$
- observable states $\{A, C, G, T, \_ \} ^{2}$

For the emission matrix, we whould have something super big ($25 \times 3$), but there are combinations that do not make sense (check notes)

$\Delta_{16}$: [Probability simplex](https://www.localmaxradio.com/questions/what-is-a-probability-simplex) of dimension 16 (the sixten points must sum 1)

In the end, the Needlman-Wunsch is just an application of the Viterbi algorithm in a conveninent Hidden Markov model (the one defined in the previous slide).

## CpG islands and gene finding
CpG sites are just two nucleotides, which are consecutive and appear in this particular order (C and G). There are regions that have alot of this pairings. 

We have particular regions in the geneome which can suffer this methylated process and when this happens the transition rate for $C\rightarrow T$ mutation is very high. this is why we don't see those many of these paris.

*Consequences*:
In genes, if we observe $C \rightarrow T$, it may be highly detrimental, meaning that the organism may no longer succeed. 

### CpG islands
Consider the following trnasition matrices $\theta$, where $\theta_{AA}$ means that an A follows an A. 

The transition matrices for CpG and non CpG are estimated from data. If the log is positive, it means it's a CpG island, if not, it's not.

### Gene finding
Assume we already know the sequence it's a gene. We want to identify exons and introns. As hidden states:
- $E_1$ the site is the first element of a codon in an exon
- $E_2$ the site is the second element of a codon in an exon
- $E_3$ the site is the last element of a codon in an exon

We can translate the state space diagram into transition matrix:
$$\begin{pmatrix}E_1 & 0 & 1 & 0 & 0 \\ 
E_2 & 0 & 0 & 1 & 0 \\ 
E_3 & * & 0 & 0 & * \\ 
I & * & 0 & 0 & *\end{pmatrix}$$
If we want to decode exons and introns, we'd apply the Viterbi algorithm to this HMM.