---
aliases: [Phylogenetics and Genomics]
subject: Mathematical models in Biology
lecturer: Jesús Fernández
format: in-person
program: Master in Advanced Mathematics and Mathematical Engineering
dates: 12-09-2022
tags: #mamme #mathmodels #biology
---
# Phylogenetics and Genomics
## Outline
## Plan
- **[[Evolutionary models lessons|Evolutionary models]]**: Understand evolution: define and design *substitution models* and *evolutionary models on trees* (this mainly for the project). *2 weeks*
	- [[Projects in Evolutionary models|Projects]]
- **[[Phylogenetic reconstruction lesson|Phylogenetic reconstruction]]** Up to 4 methods to see the phylogenetic tree. Different methods do not necessarily give the same tree and we don't know the right tree. We can only guess. *2 weeks*
	- [[Projects in Phylogenetic Reconstruction|Projects]]
- **[[Genomics]]**: How to find the best alignment and how to find genes in all the genome. *2 weeks*


## Introduction
Phylogenetic tree:
- Where does the virus comes from.
- It describes the evolutionary history.
- How can we obtain this tree? From the genetic information in the DNA molecule. 

DNA
- Most of the DNA is sequences of DNA with no known meaning (junk DNA). We don't know if they're responsible of some function or not.
- Different species have different number of chromosomes and different length.

### Geneomics: Gene prediction
- How to find the genes inside the genome?
Using maths we can propose statisical models to detect possible genes and compare them to other species. The problem is that different species have different number of chromosomes and different lengths. This leads to the problem of **multiple sequence alignment**

#### Multiple sequence alignment
Define a criterium to define which sequences are close to another: minimize the number of differences.

#### Evoutionary models
Matrix where each element corresponds to the probability of a nucleitaid A changes to C, for instance. 

#### Phylogenetic reconstruction
We will see different methods to find trees that lead to certain species.

#### Blocks
1st block
- Evolutionary models
- Phylogenetic reconstruction
- Genomics (gene prediction: how to establish a pattern for the structure of a gene, multiple alignment of sequences)
We will do projects for the first and second part (20 and 20%).

#### Mathematical approach
- Stochastic models
- (Hidden) Markov processes
- Algortihmics
- Algebraic tools: eigenvalues, eigenvectors... (linear algebra)

#### Bibliography
- Mathametical models in biology: Nice book, very easy and pleasant to read. Focus on Ch 4-5. It can be used also for neuroscience.
- Algebraic statistics for computational biology: Not as easy, but full of ideas. Some technical points of the project appear in this book.
- Biological sequence analysis: They solve the same problems but from a biologists perspective. 
- Phylogeny: Discrete and Random Processes in Evolution -> for further reading

## The Tree of Life GAME
- Nodes: represent
	- Leaves: current species
	- Interior nodes: ancestral species
- Edges: represent evolutionary processes
- Root: common ancestor

> We will get 10 questions to prepare for the final exam and only 2 will be selected. 