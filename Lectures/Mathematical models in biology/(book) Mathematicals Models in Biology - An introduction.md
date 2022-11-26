---
title: Mathematicals Models in Biology - An introduction
authors: Allman, Elizabeth Sand Rhodes, John A
edition:
publishing date: December 2003
editorial: Cambridge University Press
ISBN: 9780521819800
tags: #mathematicalmodeling #biology #books
subject: Mathematical models in Biology (MAMME)

---
# Mathematicals Models in Biology - An introduction
### Preface
*Chapters summary*
1. **Dynamic Modeling with Difference Equations:** Concepts of dynamic modeling through one-variable difference equations. Notions of equilibria, linearization and stability
2. **Linear Models of Structured Populations**: Matrix algebra and eigenvector analysis (two-variable linear models)
3. **Nonlinear models of interactions**: Models of interacting populations
4. **Modeling molecular evolution**: Introduction to probability to model molecular evolution
5. **Constructing Phylogenetic Trees**: Algorithmic flavor (uses distance formulas from 4)
6. **Genetics**: Genetics applications (extended probability)
7. **Infectious disease modeling**: Tratement of infectious disease models
8. **Curve fitting and biological modeling**

*Full index*
1. Dynamic Modeling with Difference Equations 
	1. The Malthusian Model
	2. Nonlinear Models
	3. Analyzing Nonlinear Models
	4. Variations on the Logistic Model
	5. Comments on Discrete and Continuous Models
2. Linear Models of Structured Populations
	1. Linear Models and Matrix Algebra
	2. Projection Matrices for Structured Models
	3. Eigenvectors and Eigenvalues
	4. Computing Eigenvectors and Eigenvalues
3. Nonlinear Models of Interactions
	1. A Simple Predator–Prey Model
	2. Equilibria of Multipopulation Models
	3. Linearization and Stability
	4. Positive and Negative Interactions
4. Modeling Molecular Evolution
	1. Background on DNA
	2. An Introduction to Probability
	3. Conditional Probabilities
	4. Matrix Models of Base Substitution
	5. Phylogenetic Distances 
5. Constructing Phylogenetic Trees
	1. Phylogenetic Trees
	2. Tree Construction: Distance Methods – Basics
	3. Tree Construction: Distance Methods – Neighbor Joining 
	4. Tree Construction: Maximum Parsimony
	5. Other Methods
	6. Applications and Further Reading
6. Genetics
	1. Mendelian Genetics
	2. Probability Distributions in Genetics
	3. Linkage
	4. Gene Frequency in Populations
7. Infectious Disease Modeling
	1. Elementary Epidemic Models
	2. Threshold Values and Critical Parameters
	3. Variations on a Theme
	4. Multiple Populations and Differentiated Infectivity
8. Curve Fitting and Biological Modeling
	1. Fitting Curves to Data
	2. The Method of Least Squares
	3. Polynomial Curve Fitting
A. Basic Analysis of Numerical Data
	1. The Meaning of a Measurement
	2. Understanding Variable Data – Histograms and Distributions
	3. Mean, Median, and Mode
	4. The Spread of Data
	5. Populations and Samples
	6. Practice

# 4. Modeling Molecular Evolution
**Natural selection**
- Fundamental mechanism through which evolutions occurs. It acts to reduce variability.
- Needs some underlying genetic variability.

**Evolution**
Many of the molecular changes are belived to be selectively neutral, and so are passed on to further descendents and preserved. The DNA within a gene may continue to mutate from generatijon to generatijon and acumulate differences. Similarities between species will hint at common ancestors, while differences point to the evolutionary divergence. 

**Questions**
- Can we reconstruct evolutionary relationships between several modern species by comparing the DNA sequences of their verisons of a certain gene?
- What do we might mean by "degree of similarity"?

**Goal**
- Study *molecular evolution*
- Define *phylogenetic distance*: measure of sequence similarity

## 1. Background on DNA
DNA molecule forms a double helix, a twisted ladder-like structure. Each point corresponds to a molecular subunit, called *nucleotides* or *bases*:
- **A**denine: *purine*.
- **G**uanine: *purine*.
- **C**yosine: *pyrimidne*.
- **T**hymine: *pyrimidne*

| Molecule | Complement |
| -------- | ---------- |
| A        | T          |
| G        | C          |

DNA has a directional sense.

Sections of DNA form genes, with the encoded instruction to manufacture propeins (through RNA). Triplets of consecutives bases form *codons* and each specifies a particular amino acid for the protein chain. Certain codons signal the end of the protein sequence. There's some redundancy in the genetic code:  $4^{3}= 64$ different codons, only 20 aminoacids and one stop command. *N many codons, the third base has no affect on the paricular aminoacid the codon specifies.*

Not all genes encode proteins via mRNA, some genes encode for the production of other types of RNA, which are the "final products". About 97% of human DNA is believed to be noncoding (*junkDNA*).

### Mutations
Most common:
- *Base substitution*: replacement of one base for another at a certain site n the sequence.
	- *Transition*: Interchanges a purine with a purine or a pyrimidine with a pyrimidine. This are more frequent.
	- *Transversion*: Interchange of classes
- *Delation* of a base or consecutive one
- *Insertion of a base*

Let's focus only on base substitution.

#### Example
(Assuming sequences have been aligned)
$$\begin{aligned}
S_{0} &= AC\mathbf{C}TGC\mathbf{C}CTA...\\
S_{1} &= AC\mathbf{G}TGC\mathbf{A}CTA...\\
S_{2} &= AC\mathbf{G}TGC\mathbf{G}CTA...
\end{aligned}$$
From $S_0$ to $S_2$, we notice only one base substitution, but we know $S_1$, which shows a change from $G \rightarrow A \rightarrow G$, which has been *hidden* due to a *back mutation*. We can also have consecutive substitutions, which are counted only once when looking at $S_2$ directly.

A simple ratio of mutations per site obtained rom comparing the first and last equences may give too low an estimate of the amount of mutations that acutally occured.

## 2. An introduction to probability