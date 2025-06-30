#tuple #vector #unitvector #LinarAlgebra 
# Overview

A vector is a mathematical representation of something that has magnitude and direction. Generally is a type of <b><u>tuple</u></b>, which is just an ordered list of elements. 

Vectors can be parameterized in a number of different coordinate spaces, be it all real numbers, complex, etc. For example
$$
\vec{v} \in \mathbb{R}^2
$$
The above would define some two-tuple, or vector in the real number coordinate space. 

To add vectors, simply add them. Subtracting them is similar. They must be the same dimension, and you might see something like $\vec{a}, \vec{b} \in \mathbb{R}^n$. Of note- if the order of subtraction is switched for two vectors the resulting vector is the negative such that
$$
\vec{v} - \vec{u} = \vec{t} \space \Rightarrow \space \vec{v} - \vec{u} = -\vec{t}
$$

coplanar
scalar multiplication

## Unit Vectors

Unit vectors indicate the direction a vector is oriented. Often denoted with $\hat{i}, \hat{j}, \hat{k}$ corresponding to x, y, z, respectively. In simple terms,  
$$
\hat{i}, \hat{j} \in \mathbb{R}^2
$$
$$
\hat{i} = \begin{bmatrix}   
 1 \\
 0
\end{bmatrix},   
\hat{j} = \begin{bmatrix}   
 0 \\
 1
\end{bmatrix}
$$
For example, a vector, $\vec{v} \in \mathbb{R}^2$ could be described as 

$$
\vec{v} = 1\hat{i} -2\hat{j}
$$

Indicating it has 1 unit of _something_ in the x-direction, and -2 units in the y-direction.
## Lines 

Up-front, parametric equations are the only way to describe lines in all dimensions. Note that these are not always linear lines, such as a fly's flightpath. A <b><u>parametric equation</u></b> is a set of equations with a distinct independent variable used to find all equation solutions for a given form of that independent variable. 

We can describe a set of vectors as well. Consider the set of all <b><u>collinear</u></b> vectors, or vectors in identical orientations, for a given vector, $\vec{v}$:
$$
S = \{c\vec{v}|c \in \mathbb{R}\}
$$
Note that this is a really formal way of saying that S is a set of vector cv, where v is our vector and c could be a constant anywhere in real numbers. If drawn in their <b><u>standard form</u></b>, originating at the origin, this will just look like a line with v acting as the slope. 

Now imagine another set, L, with an arbitrary vector, $\vec{x}$
$$
L = \{\vec{x} + t\vec{v}|t, x \in \mathbb{R}\}
$$
This is a general way of writing a line in higher dimensions than just $\mathbb{R}^2$ . It follows that one can determine the vector, $\vec{v}$ as described above, from two vectors that point on a line, $\vec{a}, \vec{b}$. If we assume to want the vector that runs from $\vec{a}$ to $\vec{b}$, then we can simply do:
$$
\vec{v}=\vec{b}-\vec{a}
$$
And so we can create a line 
$$
L = \{\vec{x} + t\vec{v}|t \in \mathbb{R}\};\vec{x} = \vec{b} \cup \vec{a}
$$
Note here that x could be b or a. This works for *n* dimensions. 

