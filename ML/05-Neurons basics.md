### Linear regression and neurons

A neuron basically does the linear regression and apply an activation function to the result.

**Why an activation function :** All neurons typically does linear regression, results nothing but a linear regression calculation, using which it cannot solve complex problems like identifying languages, work with images and sounds etc. An activation function introduces non-linearity and helps the neuron learn complex patterns.

**RELU (Rectified Linear Unit)** 
Relu is such a loss function which eliminates negative values. 
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

dL/dA = d(A - Z)<sup>2</sup>/dA = 2(A - Z)

dZ/dw = d(wx + b)/dw = x

so **dL/dw** = 2(A - Z) * (0 or 1 ) * x

similarly 
dL/db = dL/dA x dA/dZ x dZ/db

dZ/dw = d(wx + b)/db = 1

so **dL/db** = 2(A - Z)

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

W1,W2 -> Z1,Z2 -> A1,A2 -> Z<sub>out</sub> -> A<sub>out</sub> -> L

by applying chain rule



##### Backward pass

L -> A<sub>out</sub> -> Z<sub>out</sub> -> A1,A2 -> Z1, Z2 -> W1,W2






