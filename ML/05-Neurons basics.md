### Linear regression and neurons

A neuron basically does the linear regression and apply an activation function to the result.

**Why an activation function :** All neurons typically does linear regression, results nothing but a linear regression calculation, using which it cannot solve complex problems like identifying languages, work with images and sounds etc. An activation function introduces non-linearity and helps the neuron learn complex patterns.

**RELU (Rectified Linear Unit)** 
Relu is such a activation function which eliminates negative values. 
Relu(x) -> x = x , if > 0 else outputs 0.
eg: Relu(5) = 5 , Relu(-5) = 0.

### Forward and Backward propagation in neurons

Forward pass predicts the output, which is used to calculate loss. The loss is passed backwards in backward pass as gradients and it is used to update weights. This cycle repeats to fine tune the weights to get accurate predictions.

#### Single neuron in hidden layer
##### Forward pass

Weight -> Prediction -> Output -> Loss

eg: let x = 3 , w = 2 , b = 5 ,  Y = 15

Prediction Z = 3 x 2 + 5 = 11
Output A = Relu(11) = 11
Loss L = (A - Y)<sup>2</sup> = (11 - 15)<sup>2</sup> = 16


##### Backward pass

Loss -> Output -> Prediction -> Weight
L -> A -> Z -> W

###### Finding gradient
by applying chain rule we have,

dL/dw = dL/dA x dA/dZ x dZ/dw 

dA/dZ is 0 if A is 0 or 1 otherwise. since Relu(Z) = Max(0, Z)

dL/dA = d(A - Y)<sup>2</sup>/dA = 2(A - Y)

dZ/dw = d(wx + b)/dw = x

so **dL/dw** = 2(A - Y) * (0 or 1 ) * x

similarly 
dL/db = dL/dA x dA/dZ x dZ/db

dZ/db = d(wx + b)/db = 1

so **dL/db** = 2(A - Y)

**Dying Relu**
gradient becomes 0 for relu as activation function for a -ve prediction, which prevents updating weights further.

eg: let Y = 15 , A = 11 , x = 3 , w = 2 , b = 5 

dL/dw = 2(11 - 15) * 1 * 3 = -24 

dL/db = 2(11 - 15) = -8

w<sub>new</sub> = w<sub>old</sub> - α * gradient of w

where α is the learning rate. let α = 0.1
w<sub>new</sub> = 2 - (-24*0.1) = 2 + 2.4 = 4.4 

similarly 
b<sub>new</sub> = b<sub>old</sub> - α * gradient of b

b<sub>new</sub> = 5 - (-8 * 0.1) = 5 + 0.8 = 5.8

new Z = 4.4 * 3 + 5.8 = 19 
A = relu(19) = 19

##### Multiple neurons in hidden layer
##### Forward pass
Loss will be calculated in foward pass

W1,W2 -> Z1,Z2 -> A1,A2 -> Z<sub>out</sub> -> A<sub>out</sub> -> L

eg: Consider a network with 2 hidden neuron and 1 output neuron

let x<sub>1</sub>  = 2 , w<sub>1</sub> = 5,  b<sub>1</sub> = 3,
x<sub>2</sub>  = 3 , w<sub>2</sub> = 4,  b<sub>2</sub> = 6,
 w<sub>out1</sub> = 5,  w<sub>out2</sub> = 4,  b<sub>out</sub> = 2
 and Y = 150

Z<sub>1</sub> = x<sub>1</sub>w<sub>1</sub> + b<sub>1</sub>
= 2 x 5 + 3 = 13

A<sub>1</sub> = ReLU(13) = 13

Z<sub>2</sub> = x<sub>2</sub>w<sub>2</sub> + b<sub>2</sub>
= 3 x 4 + 6 = 18
A<sub>2</sub> = ReLU(18) = 18

Z<sub>out</sub> =  A<sub>1</sub>w<sub>out1</sub>  + A<sub>2</sub>w<sub>out2</sub> + b<sub>out</sub>

= 13 x 5 + 18 x 4 + 2 = 65 + 72 + 2 = 139

A<sub>out</sub> = ReLU(139) = 139

Loss L = (A<sub>out</sub> - Y)<sup>2</sup>
= (139 - 150) <sup>2</sup>  = 121

##### Backward pass
Loss calculated in forward pass will be used to calculate gradient for weights and biases in backward pass,

for output neuron,

L -> A<sub>out</sub> -> Z<sub>out</sub>  -> W<sub>out</sub>

gradient for W<sub>out</sub>  = dL / dW<sub>out</sub>
by applying chain rule,

dL/dW<sub>out</sub> = dL / dA<sub>out</sub> x dA<sub>out</sub> / Z<sub>out</sub> x dZ<sub>out</sub>/dW<sub>out</sub>

dL / dA<sub>out</sub> = 2(A - Y)

dA<sub>out</sub> / Z<sub>out</sub> = 1 if Z > 0,  or 0

dZ<sub>out</sub>/dW<sub>outi</sub> = A<sub>i</sub>

so dL/dW<sub>out</sub> = 2(A <sub>out</sub>- Y) x A<sub>i</sub>

similarly,
dL/db<sub>out</sub> = dL / dA<sub>out</sub> x dA<sub>out</sub> / Z<sub>out</sub> x dZ<sub>out</sub>/db<sub>out</sub>


dZ<sub>out</sub>/db<sub>out</sub> = 1

so dL/db<sub>out</sub>  = 2(A<sub>out</sub> - Y)


for neorons in hidden layer,

L -> A<sub>out</sub> -> Z<sub>out</sub> -> A<sub>1</sub>,A<sub>2</sub> -> Z<sub>1</sub>, Z<sub>2</sub> -> W<sub>1</sub>,W<sub>2</sub>


by applying chain rule ,

dL / dW<sub>1</sub> =   = dL / dA<sub>out</sub> x dA<sub>out</sub> / Z<sub>out</sub> x dZ<sub>out</sub>/dA<sub>1</sub> x dA<sub>1</sub>/dZ<sub>1</sub> x dZ<sub>1</sub>/dW<sub>1</sub>

we have dL / dA<sub>out</sub> x dA<sub> out</sub> / Z<sub>out </sub> = 2(A<sub>out</sub> - Y)

dZ<sub>out</sub>/dA<sub>1</sub>= d(w<sub>out1</sub>A<sub>1</sub> + w<sub>out2</sub>A<sub>2</sub> + b<sub>out</sub>) / dA<sub>1</sub> = w<sub>out1</sub>

dA<sub>1</sub>/dZ<sub>1</sub> = 1 if Z<sub>1</sub> > 0, else 0

dZ<sub>1</sub>/dW<sub>1</sub> = x<sub>1</sub>

so 
dL / dW<sub>1</sub> = 2(A<sub>out</sub> - Y). w<sub>out1</sub> .  x<sub>1</sub>

dL / db<sub>1</sub> =   = dL / dA<sub>out</sub> x dA<sub>out</sub> / Z<sub>out</sub> x dZ<sub>out</sub>/dA<sub>1</sub> x dA<sub>1</sub>/dZ<sub>1</sub> x dZ<sub>1</sub>/db<sub>1</sub>

= 2(A<sub>out</sub> - Y). w<sub>out1</sub> 
