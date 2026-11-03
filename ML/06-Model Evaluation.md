# Model Evaluation
Evaluating a model is very important to ensure that it performs well on unseen data as well. 
## Training, validation, and test datasets
Available dataset has to be split into training, validation and test datasets.
**Training Dataset** - A subset of the available dataset which is used to train the model and tune the weights.
**Validation Dataset** - A subset of the original dataset, used to validate the model generally at the end of every epoch. very useful to find overfitting early. weights are not updated during validation.
**Test Dataset** - A subset of the original dataset, used to test the accuracy of the model on unseen data.

## Overfitting and underfitting
Overfitting happens when the model leans completely on training data without generalization. Performance on test dataset will be poor where as the performance will be very good on the training dataset.
Underfitting happens when the model is too simple to learn underlying patterns.

## Generalization
It is the ability of the model to perform well on unseen data. 
L1/L2 Regularization, dropouts, cross validation are some of the techniques to improve generalization.

### L1/L2 Regularization
Regularization applies a penalty term to the loss.
**L1(Lasso) Regularization** - penalty term is the sum of absolute values of weights multiplied by a regularization strength.  
<img width="266" height="82" alt="image" src="https://github.com/user-attachments/assets/e083919c-902a-437c-bd72-82ff447a3894" />  

**L2(Ridge) Regularization** - penalty term is the sum of square of the weights multiplied by a regularization strength.  
<img width="314" height="85" alt="image" src="https://github.com/user-attachments/assets/b8708cf2-ecf6-4135-bb90-281b09f3e239" />  

**Dropout** - randomly disable some neurons during training, which reduces the model relying on particular neurons heavily.

## Bias and Variance
**Bias** is the error caused by a model when it is over simplified on the data.When bias is high, the model fails to understand underlying pattern correctly and causes underfitting.
Bias is the difference between average prediction and actual value.  

Bias = E{ȳ} - y  

  
**Variance** - When the model is highly sensitive about the data it fails to generalize the pattern correctly, which leads to overfitting.
variance measures how much predictions varies from their average prediction.    
Var(X) = E(X<sup>2</sup> - E(X)<sup>2</sup>






