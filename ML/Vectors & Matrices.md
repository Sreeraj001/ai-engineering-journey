# Vectors & Matrices
This is an inline vector: $\bigl( \begin{smallmatrix} a \\ b \end{smallmatrix} \bigr)$
We have according to multiple linear regression,
  Ŷ = w<sub>1</sub>x<sub>1</sub>+w<sub>2</sub>x<sub>2</sub>​+w<sub>3</sub>x<sub>3</sub>+b

  this can re written in vector form as

```math
 Ŷ =
\begin{bmatrix}
x<sub>1</sub> \\\
x<sub>2</sub>  \\\
x<sub>3</sub> 
\end{bmatrix}
.
\begin{bmatrix}
  w<sub>1</sub> &  w<sub>2</sub> & w<sub>2</sub>
\end{bmatrix} 

 + b
```

in General 

Ŷ​=X<sup>T</sup>W+b​

eg: let features like ram, memory, and cpu predicts laptop price

let regression be 
    Ŷ = 5x<sub>1</sub> +  6x<sub>2</sub> +  4x<sub>3</sub> + 10 

here weights are [ 5  6 4]
let a training data is [16 1000 7]

then

```math
Ŷ = 
\begin{bmatrix}
   5 &  6  & 4 
\end{bmatrix} 
.
\begin{bmatrix}
16 \\\
1000 \\\
7
\end{bmatrix}
 + 10
```
Ŷ = 5*16 + 6*1000 + 4*7 + 10
  = 6118

similarly if we have n number of training rows 

```math
 Ŷ = 

\begin{bmatrix}
x<sub>11</sub> & x<sub>12</sub> &. & x<sub>1n</sub> \\\
x<sub>21</sub> & x<sub>22</sub> &. & x<sub>2n</sub>  \\\
. & . &. & .  \\\
x<sub>n1</sub> & x<sub>n2</sub> &. & x<sub>nn</sub>
\end{bmatrix}
.
\begin{bmatrix}
w<sub>1</sub> \\\
w<sub>2</sub> \\\
w<sub>2</sub>
\end{bmatrix} 
 + b
```

The order of the resulting vector is  (n * 3) * (3 * 1) = (n, 1) 

### Linear regression and neurons











 
