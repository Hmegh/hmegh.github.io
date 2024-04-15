---
title: Linear Algebra Companion
math: true
date:

# design:
#    spacing:
#       padding: [0, 0, 0, 0]
#       margin: [0, 0, 0, 0]
---
{{< toc >}}

<!-- \( \def\x{{\mathbf{\x} }} \) -->

$
   \def\x{{\mathbf{x}}}
   \def\col{{\operatorname{col}}}
   \def\rank{{\operatorname{rank}}}
   \def\row{{\operatorname{row}}}
   \def\null{{\operatorname{null}}}
   \def\R{{\mathbb{R}}}
   \def\zero{{\mathbf{0}}}
    \def\B{{\mathcal{B}}}
   \def\b{{\mathbf{b}}}
   \def\bold#1{{\bf #1}}
$

:warning: This is work in progress. Also, this is not a replacement for the notes and the textbook.


# :ledger: Definitions: 

**Column space:**  The column space of an $m\times n$ matrix $A$, denoted $\col(A)$, is the span of the columns of $A$.

{{% callout note %}}
$\col(A)$ is a subspace of $\mathbb{R}^m$, where $m$ is the number of rows of $A$, because every column has $m$ components.

{{% /callout %}}

---
**Row space:**  The row space of an $m\times n$ matrix $A$, denoted $\row(A)$, is the span of the rows of $A$.

{{% callout note %}}
$\row(A)$ is a subspace of $\mathbb{R}^n$, where $n$ is the number of columns of $A$. 
{{% /callout %}}



---

**Null space:**  The null space of a $m\times n$ matrix $A$, denoted $\null(A)$, is the set of solutions to $[A\mid \zero]$.


{{% callout note %}}
$\null(A)$ is a subspace of $\mathbb{R}^n$, since it contains all $\x \in \R^n$ such that $A\x=\zero$.  
{{% /callout %}}


---

**Dimension:** Let $V$ be a subspace of $\R^n$ and let $\B$ be a basis for $V$. The dimension of $V$ is the number of vectors in $\B$. 
{{% callout note %}}
The dimension does not depend on the choice of the basis. 
{{% /callout %}}

---

**Rank:** Let $A$ be an $m\times n$ matrix. $\rank(A)$ is the dimension of $\col(A)$.

---

**Nullity:** Let $A$ be an $m\times n$ matrix. $\text{nullity}(A)$ is the dimension of $\null(A)$.

{{% callout note %}}
The nullity of $A$ is the number of free variables in the system $[A\mid \zero]$. 
{{% /callout %}}

---
**Invertible matrix:** An $n\times n$ matrix is said to be invertible if there is a matrix $B$ such that $AB=BA=I_n$. 

{{% callout note %}}
Only square matrices can be invertible. 
{{% /callout %}}


--- 


# :pencil: Theorems:
---
**The rank nullity theorem:** Let $A$ be an $m\times n$ matrix. Then, $\rank(A)+\text{nullity}(A)=n$. 

---
**The invertible matrix theorem:** 
Let $A$ be an $n\times n$ matrix, then the following statements are equivalent: 

1) $A$ is invertible. 
2) Every row of $A$ has a pivot. 
3) Every column of $A$ is a pivot column.
4) $\rank(A)=n$.
5) $\text{nullity}(A)=0$. 
6) $\col(A)=\mathbf{R}^n$.
7) $\row(A)=\R^n$.
8) $\det(A)\ne 0$.
9) Given any $\b\in \mathbb{R}^n$, the system $A\x=\b$ has a unique solution. 
10) The only solution to $A\x=\zero$ is the trivial solution. 
11) $\det(A)\ne 0$. 
12) The transformation $T_A:\R^n\to \R^n$ is $1-1$. 
13) The transformation $T_A:\R^n\to \R^n$ is onto. 



---

## ❓ Conceptual questions: 
---


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


