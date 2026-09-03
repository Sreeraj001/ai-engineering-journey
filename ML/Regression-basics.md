# Regression
It is a type of ML comes under supervised learning. Model is trained in labelled training data and produces continuous number as output

## Idea
Consider the example 
| Student | Hr of study | Score |
| --- | --- | --- |
| St 1 | 10 | 50 |
| St 2  | 40 | 98 |
| St 3  | 25 | 70 |
| St 4  | 5 | 25 |

the more the student study greater is the score. There is a direct relationship for the score with the hour of study.
score is proportional to hr of study

let **S** be the score and **H** be the hr of study

a linear regression can calculate approximate S based on H using 

S = wH + b
where w is the weight for H and b bias/ y interceptor.

In general we can calculate the out put as 

Y = wX + b

A models job is all about figuring out most accurate value for w and b using which it can predict the Y more accurately.

###  Error

Error is the difference between predicted output vs the actual output.

e = ȳ - y 

### Loss

Loss function is used to adjust the weight and bias. it is derived from error.

Error can be -ve of +ve . There is a high chance errors cancels out each other. 
eg : errors are -10, 3, 5, -2 . sum of errors is 0. 

So sum of errors cannot be used as a loss function. instead we can use Mean Absolute Error (MAE) or Mean Squared Error (MSE).

since MSE has some mathematical advantage over MAE for linear regression like it can penalize large errors, let us use MSE as a Loss function for Linear Regression.

### Gradient Descent 
The key idea is to adjust the value of w and b to produce closest prediction (ȳ). 

for a linear regression 
Y = wX + b
a change in w and b can change Y. the direction and amount of the change ( increase or decrease) can be determined by the derivative of Y with respect to w.

Gradient descent uses the gradient of the loss with respect to each parameter to determine how that parameter should be updated to reduce the loss.

#### Finding the gradient for w

we have 
a change in w result in the change in error which results the loss which results the predicted value
that is 

change in w
    |
change in error
    | 
change in Loss
    |
change in prediction

By applying chain rule in derivation,

dL/dw = dL/de * de/dȳ * dȳ/dw

dL/de = de^2/de 
      = 2e

de/dȳ = d(ȳ - y)/dȳ 
      = 1

dȳ/dw = d(xw+b)/dw
      = x

ie dL/dw = 2e * 1 * x
         = 2x(ȳ - y)

**new w = w - α*2x(ȳ - y)**

note: we apply a learning rate **α** which helps to reduce overshoot 

#### Finding the Gradient for b

Using similar logic ,

change in b
    |
change in error
    | 
change in Loss
    |
change in prediction


dL/db = dL/de * de/dȳ * dȳ/db

dȳ/db = d(wx + b)/db
      = 1

ie dL/db = 2e
         = 2(ȳ - y)

**new b = b - α*2x(ȳ - y)**


note: when we have multiple examples, we minimize MSE:

<img width="711" height="435" alt="image" src="https://github.com/user-attachments/assets/ca2e708f-0234-448e-99bd-5032ef35d836" />


         

