#spans #spaces

## Linear Combinations

A linear combination of vectors is an addition of vectors scaled by some constant
$$
for \space \vec{v_1}, \space \vec{v_2}...\vec{v_n} \in \mathbb{R^n}
\space and \space c_1, \space c_2...c_n \space \in \mathbb{R}
$$
A linear combination is as follows
$$
c_1\vec{v_1}+c_2\vec{v_2}+...+c_n\vec{v_n}
$$

## Spans 

The <b><u>span</u></b> of a vector indicates the possible linear combinations of any group of vectors. For example, $span(\vec{v_1}, \vec{v_2}) = \mathbb{R^2}$ would mean that the linear combination of those vectors could make any vector in the 2-dimensional real number plane; for example $\hat{i}$, and $\hat{j}$ in classical coordinate systems can be linearly combined to make any vector in the 2-D plane. The span is defined as follows
$$
Span(\vec{v_1}, \vec{v_2}...\vec{v_n}) = \left\{ c_1\vec{v_1}+c_2\vec{v_2}+...+c_n\vec{v_n} \vert c_i\in\mathbb{R} \space 1 \leq i \leq n \right\} 
$$
This definition simply states that the *span* of a set of vectors is simply another set of all possible linear scalar combinations of all vectors for all scalar values between 1 and n. 

Not all spans cover all possibilities, the zero vector span is zero, for example. Two collinear vectors can only span along their direction; in this case they are <b><u>linearly dependent</u></b>.  

NB: There are proofs for spans, if it comes up a lot add more notes here
# Linear Independence

A set of vectors can be <b><u>linearly dependent</u></b>, which means that some vector(s) in a set can be represented by some combination of the other vector(s) in a set. For example, three coplanar vectors would be linearly dependent. 

Formally, a set is linearly dependent if and only if some linear combination of them is the zero vector. 
$$
S = \left\{\vec{v_1}, \vec{v_2},...\vec{v_n}\right\} 
$$
$$
c_1\vec{v_1}+c_2\vec{v_2}+...c_n\vec{v_n}=\vec{0}
$$
For some $c_i$ not equal to zero, or for at least one non-zero. One can solve for all c values to find the zero vector and if all are zero, the set is linearly independent.

One can solve for vectors that span a given dimension by setting 
$$
c_1\vec{v_1}+c_2\vec{v_2}+...c_n\vec{v_n}=\vec{a}
$$
where $\vec{a}$ is an arbitrary non-zero vector in that dimensional space. For example, to span $\mathbb{R^3}$, $\vec{a}$ would be a 3-tuple vector. Additionally, one can solve for linear independence by solving the above equation for the zero vector and all constants must be zero. 

NB: If $n$ vectors spans $\mathbb{R^n}$ then those vectors are linearly independent, and vice versa; if $n$ vectors are linearly independent then those vectors span $\mathbb{R^n}$.

# Linear Subspaces

A vector set can be a subspace of $\mathbb{R^n}$, meaning that $\vec{V}$ must follow these conditions:

1. Contain the zero vector; for logical reasons. 
2. For any vector in the subspace, $\vec{a} \in \vec{V}$ it can be multiplied by a real scalar and still be in the subspace ($c\vec{a} \in \vec{V}$), this is called <b><u>closure</u></b> under multiplication. 
3. For any vectors in the subspace, $\vec{a} \in \vec{V}$ and $\vec{b} \in \vec{V}$, $\vec{a}+\vec{b} \in \vec{V}$. This is closure under addition. 

### Example

Define a set, 
$$
\mathbb{S} =\left\{ \begin{bmatrix}
x_1 \\
x_2 \\
\end{bmatrix} \in\mathbb{R^2} \vert x_1 \geq 0 \right\}
$$
Determine if $\mathbb{S}$ is a subspace of $\mathbb{R^2}$

1. Both $x_1$ and $x_2$ can be zero so the space contains the zero vector
2. Adding all only positive values for $x_1$ will close, since they will result in a positive vector and thus be in the set.
3. Multiplying by $-1$ will result in a negative vector which is not in the subspace, and thus does NOT close. 

Thus this is not a subspace of $\mathbb{R^2}$.

However, a span of any vector is a valid subspace
# Basis

If we have a span 
$$
V=Span(\vec{v_1}, \vec{v_2}...\vec{v_n})
$$
such that the set of vectors, $S=\left\{\vec{v_1}, \vec{v_2},...\vec{v_n}\right\}$, are linearly independent, then the set, $S$, is a basis for $V$, meaning that the set is the smallest number of vectors needed to construct every vector in the space. 

