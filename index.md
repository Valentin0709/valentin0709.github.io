---
layout: default
---
Since a certain RNA related topic has gone viral in last couple of months, I propose we have a quick look at a biochemistry puzzle about this strange molecule. Who doesn’t like some recreational maths during quarantine anyways?
### What is RNA and what can we use it for?
At a chemical level, RNA is a continuous chain of 4 alternating blocks: adenine (A), uracil (U), guanine (G) and cytosine (C). They are conventionally called nucleotides or bases. Despite what you may think, RNA is not limited to encoding the genetic information of nasty bugs, in fact it can carry numerous tasks inside the cell by folding into complex three-dimensional structures. For example, protein synthesis is directed by different types of RNA! The folding occurs mainly due the formation of hydrogen bonds between the nucleotides – or, simply put, adenine and uracil like to pair up with one another whereas cytosine is complementary to guanine. This results in the RNA bending over and attaching to itself at different points, creating loops and double-stranded regions.

Researchers are trying to employ the geometry of these versatile molecules and develop short RNAs which can bind to particular targets inside the body. These so-called aptamers could be used to specifically deliver drugs only to affected tissues and thus decrease the adverse effects of treatments such as chemotherapy.

<p style="text-align: center; display:block;">
   <img src="/Images/rna1.jpg" alt="RNA Structure" width="45%" style="display:inline-block; margin-right: auto; margin-left: auto;"/>   
   <img src="/Images/rna2.jpg" alt="RNA Structure" width="45%" style="display:inline-block; margin-right: auto; margin-left: auto;"/>   
</p>

### The folding problem
Given a sample of all possible RNA aptamers made up of 30 nucleotides, how many folding patterns do we expect to find? To simply things, we are only looking at the shape of the molecule, so if two different sequences of nucleotides give the same type of folding, they are counted together. We’ll also keep in mind that the RNA backbone doesn’t cross itself during folding, so we can model it as a collection of points joined by non-intersecting edges.

### Matching parentheses 
Let’s begin by “reading” an RNA strand from one end to another. As we encounter a couple of hydrogen bonds along the way, we see that the nucleotides can be classified into 3 categories:

* fillers – they keep to themselves and don’t interact with other nucleotides 
* heads – the first nucleotide we reach when we encounter a new base pair
* tails – the complementary nucleotide to one of the heads met earlier

Of course, this relative to the way we look at the molecule, if we were to read the strand from the opposite end, all heads and tails would switch places. 

From this observation we can deduce the following two rules which are fulfilled for any valid folding pattern: (1) the sequence contains an equal number of heads and tail and (2) at any point, the number of heads is equal or grater than the number of tails, i.e. we can’t reach the tail of a base pair before its head

Does this sound familiar? These are the same rules we use for matching parentheses in an algebraic equation: the number of open parentheses must be equal to the number of close parentheses and you can’t close more parentheses that you’ve already opened. 

<p style="text-align: center; display:block;">
  $$((maths + maths) * mathematics) ^ 2 = more maths$$
</p>

So, if we know that our RNA molecule contains 5 base pairs, then then number of ways in which these bonds can exist relative to one another is the same as the number of valid parentheses sequences made up of 5 parentheses pairs.

<p style="text-align: center; display:block;">
   <img src="/Images/rna_animation.gif" width="75%" style="display:inline-block; margin-right: auto; margin-left: auto;"/>     
</p>

<img src="/Images/rna_diagram.gif" width="100%" style="display:inline-block; margin-right: auto; margin-left: auto;"/>     






