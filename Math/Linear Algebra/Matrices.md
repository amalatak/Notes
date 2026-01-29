
## Basics

A system of linear equations can generally be boiled down to 

$$
\matrix{A}x=b
$$
A basic version can be solved in "row form" by solving the equations the old school algebra way. In column form, for a system, A, where
$$
\matrix{A} \in \mathbb{R}^2
$$
We can write the equations as
$$
x\begin{bmatrix}   
 A_{1,1} \\
 A_{2,1}
\end{bmatrix} + 
y\begin{bmatrix}   
 A_{1,2} \\
 A_{2,2}
\end{bmatrix} = \vec{b}
$$
This is a linear combination of columns, or vectors, and we try to find an amount (a combination) to multiply each by to achieve the solution. 

**Note:** this is a good way to solve for $\vec{b}$ given the values for $\vec{x}$: to perform column multiplication. 

Absent the solution for $\vec{b}$, the linear combination of all 2-columns is $\mathbb{R}^2$, the whole plane. 

## Matrix Multiplication

$$
\matrix{A}\matrix{B}\not = \matrix{B}\matrix{A}
$$
And multiplication from the left is row operations, from the right is column operations. 

Multiplication is carried out like so for a $mn$ matrix $A$ and a $np$ matrix B
$$
\matrix{A}\matrix{B} = C \ | \ \matrix{C_{ij}}=\matrix{A_{i}}\cdot\matrix{B_{j}}
$$
Such that
$$
\matrix{C_{ij}} = \sum^{n}_{k}a_{ik}b_{kj}
$$
where ${i}$ is the row of the matrix, ${j}$ is the column, and $n$ is the inner dimensions of the matrices. Hence the number of columns of A must equal the number of rows of B. 

#### Blocking

Matrices can be multiplied in smaller blocks. 
## Inverse

An inverse of matrix **A**, $\matrix{A^{-1}}$ is defined for  such that

$$\matrix{A^{-1}}\matrix{A}=\matrix{I}$$
For square matrices, 
$$\matrix{A^{-1}}\matrix{A}=\matrix{I} = \matrix{A}\matrix{A^{-1}}$$
And for rectangular matrices the inverse on the right may not be the same as the inverse on the left.

Matrices must first actually be invertible (non-singular). Singular matrices have no inverse, meaning that it cannot be multiplied by anything to obtain the identity matrix. This would be because the rows or columns are linearly dependent. In other words, one can find a vector $x$ such that

$$
Ax=0
$$
To invert matrix multiplication, inverses must be taken in reverse order
$$
(\matrix{A}\matrix{B})^{-1}=\matrix{B^{-1}}\matrix{A^{-1}}
$$
Such that
$$
\matrix{A}\matrix{B}\matrix{B^{-1}}\matrix{A^{-1}}=I
$$
In addition, the transpose of an inverse is the inverse of a transpose such that
$$
(\matrix{A^{-1}})^T = (\matrix{A^T})^{-1}
$$
### Notes

A matrix can be commuted (rows switched around) by doing $\matrix{I^*}\matrix{A}$ where $\matrix{I^*}$ is the identity matrix with its rows changed to reflect the desired change in rows of **A**. For example
$$
\begin{bmatrix}   
 0 \ 1 \ 0 \\
 1\ 0 \ 0 \\
 0 \ 0 \ 1
\end{bmatrix}
\matrix{A}
$$
Would switch the first and second rows. 
A 3-vector solution, e.g. $ax + by + cz = n$ is a plane
A 3-vector solution of two equations gives us a line
A 3-vector solution of three equations gives us a point

## Optional

Matrices can be factored into upper matrices to make them easier to solve algorithmically. This is done by modifying the identity matrix and multiplying the original matrix (and then corresponding solution vector). Usually this would be done n-1 times, where n is the number of rows in a matrix.

Also algorithmically we can solve matrix multiplication and inverses with $LU$ factorization via elimination matrices. 
