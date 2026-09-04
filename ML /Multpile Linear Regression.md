# Multiple Linear Regression

We have for linear regression 

 ȳ = wx + b

 this is when we have a single feature like hours of study to predict exam score. But in real world there could be multiple features which effects the output.
 eg: hours of study, IQ, class, school predicts exam score

 so ȳ = w1x1+ w2x2 + w3x3 + .... + b

 where w1 , w2 .. are the weights of features x1, x2 ....

 Similar to linear regression,
 Gradient of x1 -> 2 * x1 * (ȳ - y)
             x2 -> 2 * x2 * (ȳ -y)

We don't calculate gradient from just one training sample, instead it is the average of all training data

ie, ***​∂MSE/∂wj​= 1∑n ​2(y^​i​−yi​)xij***

## Scaling dataset 
Larger x values tend to have higher gradient value for the variable and it results in larger jump for one variable. It causes the training to be unstable.
scaling the data helps reduce this issue.

Commons ways to scale the data are,

### Standardization

x̄ = (x - μ)/σ   [ it produces approximate mean 0 and SD 1 ]

### Min Max Scaling
x̄ = (x - xmin)/ (xmax - xmin)

it puts value between 0 and 1


​
