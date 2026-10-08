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

Ŷ​=W<sup>T</sup>X+b​

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
  = 6128

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
w<sub>3</sub>
\end{bmatrix} 
 + b
```

or Ŷ = XW + b

 X = (n, 3)
 W = (3, 1)

 so 
The order of the resulting vector is  (n * 3) * (3 * 1) = (n, 1) 

### Linear regression and neurons

A neuron does the linear regression and apply an activation function to the result.

**Why an activation function :** All neurons typically does linear regression results nothing but a linear regression calculation, using which it cannot solve complex problems like identifying languages, work with images and sounds etc. An activation function introduces non-linearity and helps the neuron learn complex patterns.

**RELU (Rectified Linear Unit)** 
Relu is such a loss function which eliminates negative values. 
Relu(x) -> x = x , if > 0 else outputs 0.
eg: Relu(5) = 5 , Relu(-5) = 0.











 
