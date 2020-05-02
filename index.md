---
layout: default
---
Since a certain RNA related topic has gone viral in last couple of months, I propose we have a quick look at a biochemistry puzzle about this strange molecule. Who doesn’t like some recreational maths during quarantine anyways?
### What is RNA and what can we use it for?
At a chemical level, RNA is a continuous chain of 4 alternating blocks: adenine (A), uracil (U), guanine (G) and cytosine (C). They are conventionally called nucleotides or bases. Despite what you may think, RNA is not limited to encoding the genetic information of nasty bugs, in fact it can carry numerous tasks inside the cell by folding into complex three-dimensional structures. For example, protein synthesis is directed by different types of RNA! The folding occurs mainly due the formation of hydrogen bonds between the nucleotides – or, simply put, adenine and uracil like to pair up with one another whereas cytosine is complementary to guanine. This results in the RNA bending over and attaching to itself at different points, creating loops and double-stranded regions.

Researchers are trying to employ the geometry of these versatile molecules and develop short RNAs which can bind to particular targets inside the body. These so-called aptamers could be used to specifically deliver drugs only to affected tissues and thus decrease the adverse effects of treatments such as chemotherapy.

 <div>
<figure  
    style="float:left;
    width:49%;
    margin:0;
    padding:0;
    vertical-align: top;
    text-align: center;">
  <img src="/Images/rna1.jpg" height="100%" width="100%" />
  <span>Folded RNA with nested loops</span>
  </figure >
   <figure  
    style="float:right;
    margin:0;
    padding:0;
    width:49%;
    vertical-align: top;
    text-align: center;">
  <img src="/Images/rna4.jpg" height="100%" width="100%" />
  <span>RNA molecule with a double-stranded region</span>
   </figure >
<div style="clear:both;"></div>
</div>

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
  $$((maths + maths) \times (more \; maths)) ^ 2 = result$$
</p>

So, if we know that our RNA molecule contains 5 base pairs, then then number of ways in which these bonds can exist relative to one another is the same as the number of valid parentheses sequences made up of 5 parentheses pairs.

<figure style="text-align: center; display:block;">
  <img src="/Images/rna_animation.gif" width="75%" />   
  <figcaption style="display:inline-block; margin-right: auto; margin-left: auto;">Converting the RNA strand into an equivalent paranthesis sequence</figcaption>
</figure>

<figure style="text-align: center; display:block;">
  <img src="/Images/rna_diagram.png" width="100%"/>   
  <figcaption style="display:inline-block; margin-right: auto; margin-left: auto;">Nucleotide pairs on an unfolded RNA molecule</figcaption>
</figure>

### The hungry rabbit

René Descartes has divided his garden into 5 x 5 equal grass patches and built a wooden fence which runs across the diagonal, from south-west to north-east. As he is a coordinate systems enthusiast, Descartes assigned two values to each corner based on their horizontal and vertical distance from the lower-left corner which has the coordinates (0, 0). In the upper-right corner of the garden (5, 5), Descartes has cultivated carrots. A hungry rabbit which enters the garden at point (0, 0) asks the mathematician if he can share any of his delicious carrots. Descartes tells the rabbit that he can take one if he calculates the number of paths of minimum length he can take from (0, 0) to (5, 5), walking only along the edges of the grass patches and without crossing the fence.

<figure style="text-align: center; display:block;">
  <img src="/Images/rabbit.jpg" width="75%" />   
  <figcaption style="display:inline-block; margin-right: auto; margin-left: auto;">Bird's-eye view of the garden</figcaption>
</figure>

One way to approach this problem is to work out first the total numbers of possible walks from (0, 0) to (5, 5) and then subtract the number of bad paths which cross the diagonal at least once – this leaves us with the answer we are looking for!

Since we are searching for paths of minimum length between the two corners, the first comment we can make is that such paths must have length 10 and are made up of 5 steps to east and 5 steps to north. Our first task is to calculate in how many unique ways we can arrange a sequence of these 10 alternating moves. To solve this, imagine that we begin with a sequence consisting of 10 steps to north.

<p style="text-align: center; display:block;">
  $$north \; north \; north \; north \; north \; north \; north \; north \; north \; north$$
</p>

Now we can change 5 of those norths into easts. We have 10 choices for picking the first north to convert. And 9 for the second, 8 for the third, 7 for the fourth and 6 for the fifth. Overall, there are $10 \times 9 \times 8 \times 7 \times 6$ paths we can construct using this method. 

<p style="text-align: center; display:block;">
 $$swapping \; the \; norths \; on \; positions \; 1, 5, 7, 8, and \; 10 \; for \; easts \; results \; in \; the \; following \; path$$
  $$east \; north \; north \; north \; east \; north \; east \; east \; north \; east$$
</p>

However, we counted some paths multiple times – converting positions 1, 5, 7, 8 and 10  generates the same sequence of steps as converting postions 5, 1, 10, 7, 8. There are $5 \times 4 \times 3 \times 2 \times 1$ ways to rearrange the order in which we make our picks, so the final number of valid paths is:

<p style="text-align: center; display:block;">
  $$(10 \times 9 \times 8 \times 7 \times 6) / (5 \times 4\times 3 \times 2 \times 1) = 42$$
</p>

Using the factorial notations, $a! = 1 \times 2 \times 3 \times \; … \; \times a$, we can rewrite this a $\smash{\frac{10!}{5! \times !5}}$. These are formally referred to as 5-combinations of 10 or $$
    \begin{pmatrix}
    10  \\
    5 \\
    \end{pmatrix}$$

<figure style="text-align: center; display:block;">
  <img src="/Images/rabbit_animation.gif" width="75%" />   
  <figcaption style="display:inline-block; margin-right: auto; margin-left: auto;">Simulation of all the possible paths</figcaption>
</figure>





