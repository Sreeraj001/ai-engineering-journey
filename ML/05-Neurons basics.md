### Linear regression and neurons

A neuron basically does the linear regression and apply an activation function to the result.

**Why an activation function :** All neurons typically does linear regression, results nothing but a linear regression calculation, using which it cannot solve complex problems like identifying languages, work with images and sounds etc. An activation function introduces non-linearity and helps the neuron learn complex patterns.

**RELU (Rectified Linear Unit)** 
Relu is such a loss function which eliminates negative values. 
Relu(x) -> x = x , if > 0 else outputs 0.
eg: Relu(5) = 5 , Relu(-5) = 0.

### Forward and Backward propagation in neurons

Forward pass predicts the output, which is used to calculate loss. The loss is passed backwards in backward pass as gradients and it is used to update weights. This cycle repeats to fine tune the weights to get accurate predictions.

