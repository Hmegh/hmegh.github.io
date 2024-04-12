---
title: Linear Algebra Companion
math: true
date: 
---
{{< toc >}}

<!-- \( \def\x{{\mathbf{\x} }} \) -->

$
   \def\x{{\mathbf{x}}}
   \def\bold#1{{\bf #1}}
$

:warning: This is work in progress. 


## Definitions: 


## Theorems:


## Conceptual questions: 



TF: If $A$ is invertible, then its inverse is unique? 
{{< spoiler text="Answer" >}}
True. If there are two matrices $B$ and $C$ such that $$AB=BA=I_n\qquad\text{and }\qquad AC=CA=I_n$$
Then $AB=AC$, multiply both sides by $C$ from the left and use $CA=I_n$ to obtain $B=C$. 
{{< /spoiler >}}

TF: If $A$ and $B$ are invertible $n\times n$ matrices, then $A+B$ is invertible. 
{{< spoiler text="Answer" >}}
False. Take $A=I_n$ and $B=-I_n$. Both matrices are invertible but $A+B$ is the zero matrix (not invertible). 
{{< /spoiler >}}


TF: If $A$ and $B$ are two invertible $n\times n$ matrices, then $AB$ is invertible? 
{{< spoiler text="Answer" >}}
Yes, the product of two invertible matrices (of the same size) is an invertible matrix. 
Here are two ways to see this:  
1) Consider $C=B^{-1}A^{-1}$, then 
$$C(AB)=(B^{-1}A^{-1})(AB)= B^{-1}(A^{-1}A)B=B^{-1}B=I_n.$$
Therefore, $AB$ is invertible and its inverse is $C=B^{-1}A^{-1}$. 

2) Since, $A$ and $B$ are invertible, we have $\det(A)\ne 0$ and $\det(B)\ne 0$. Therefore
$$\det(AB)=\det(A)\det(B)\ne 0$$ 
Recall that the product of two non-zero numbers is non-zero. 
{{< /spoiler >}}

TF: The system $A\x=\lambda \x$ has a solution if and only if $\lambda$ is an eigenvalue.
{{< spoiler text="Answer" >}}
False. This system always has a solution (the trivial solution). A correct version of this statement is

The system $A\x=\lambda \x$ has a **nontrivial** solution if and only if $\lambda$ is an eigenvalue.
{{< /spoiler >}}


