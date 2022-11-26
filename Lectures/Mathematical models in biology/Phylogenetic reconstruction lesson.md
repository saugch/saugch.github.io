---
aliases: [Phylogenetic reconstruction]
subject: Mathematical models in Biology
lecturer: Jesús Fernández
format: in-person
program: Master in Advanced Mathematics and Mathematical Engineering
dates: 10-10-2022
tags: #mamme #mathmodels #biology
---
# Phylogenetic reconstruction
## Introduction
Now it's considered there's less than 20,000 genes. For some time, people considered that the number of genes was related to how complex an organism was, but now it's not clear anymore. 

The bond from A to T is weaker (2 hydrogen bonds) than the one from C to G (3 bonds).

mRNA has a copy of a particular region of the DNA and it's able to leave the nucleus. 

### Gene structure
You have a given number of regions called exons, which contain the necessary information to build the aminoacids. Between exons, we have the introns. 

At the beginning of the gene, we may have this particular codon: ATG. There are other possibilities. And in the end we have 3 possibilities of codons to mark its stop. Sometimes we have a TATA box where the RNA starts to stick to begin the translation processes. Why it's TATA? Because these are the weaker links, it's easier to separate the strands.

Two steps:
1. Transcription. Molecule consisting only of the exons, introns and the beggining and end block (pre-mRNA).
2. Splicing: we remove the introns, this is what will be transofrm into aminoacids (mRNA).

### Multiple sequence alignment
We would like to arrange the sequences in a special way so to know the sequences that correspond to each other. 

### Tree
Once we have them aligned, we want a method to obtain a tree. 

#### Distance-based methods
Based ona system of distances *d* computed from DNA sequences
- Jukes-Cantor distance or log-det
- Reduce the sequences to a symmetric table
- d is not a metric.

#### Character-based methods
They try to use all the information contained in the sequences.

#### Quartet based methods
First to contruct trees with 4 leaves (quartets) and then joined them together.

For all the processes, we will get a geneand we can go to a website, get alignments of primates and apply it to get a phylogenetic tree.

---
## Outline
Quartet-based methods is typically based on maximum likelihood, but we could use also as input the branch-length of the interior edge provided by neighbor-joining.

*Note: the professor uses quartet to refer to topology.*

### Distance based methods
The tree metric ($d_T$).

#### UPGMA
Among the ones we've seen is the fastest.

**Molecular clock** is okay(ish) if all the species are close.

UPGMA is a method that is okay when you are analyzing species that are very similar.

They are not using all the possible information on the sequences. It also happens with neighbor-joining.

#### Neighbor-Joining Algortihm
It's one of the important methods for phylogenetic reconstruction.

Outgroup: you add a species that is very different from the others and then the node that connects this to the rest of the group is a root.

###  Character-based methods
Attempt to use all the information in the sequences.

#### Maximum parsimony
The number of non-informative sites is very small compared to the total number of sites.

For some trees, MP is not consistent. For this, MP is no longer very used.

#### Maximum likelihood
The notation of the professor is slightly different. It tries to estimate the tree and parameters that maximize the likelihood. 

It's an optimization problem, which is a big problem in mathematics. There's some numerical methods, like the Newton's method. Probably the most used method to apply ML is the [expectation maximization](https://en.wikipedia.org/wiki/Expectation%E2%80%93maximization_algorithm).  The problem is that the method may not converge. 

Usually, the tree topology is provided by neighbor-joining and the other parameters are found in ML. 

### Quartet-based methods
**Long branch-attraction**: When you have long branches (same tree that gives problems to MP and UPGMA), it tends to put the long branches together.

This is because, as we saw in Proj 2, the maximum number of observable substitutions when comparing two sequences tend to $3/4$. So, the distance between 1 and 3 (the two long branches) cannot grow forever.

The problem of quartet based methods is that they don't know how to use the weights. There's still not a clear way on how to use the weights to build a tree. 