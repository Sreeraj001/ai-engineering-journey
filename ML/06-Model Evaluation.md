# Model Evaluation
Evaluating a model is very important to ensure that it performs well on unseen data as well. 
## Training, validation, and test datasets
Available dataset has to be split into training, validation and test datasets.  
**Training Dataset** - Used to calculate the loss and to update weights through back propagation.
**Validation Dataset** - Used to validate the model during training. very useful to find overfitting early. weights are not updated during validation.
if validation error increases after decreasing over epoches. it is the point where **early stop** has to be considered. 
**Test Dataset** - Used for the final evaluation of the model after training is completed.

## Overfitting and underfitting
Overfitting happens when the model leans completely on training data without generalization. Performance on test dataset will be poor where as the performance will be very good on the training dataset.
Underfitting happens when the model is too simple to learn underlying patterns.

## Generalization
It is the ability of the model to perform well on unseen data. 
L1/L2 Regularization and dropouts are some of the techniques to improve generalization. also cross validation can indirectly helps generalization by helping to tune hyper parameters.

## Early stopping

| Condition |	Training performance |	Validation performance |  
| --- | --- | --- |
| Overfitting |	Good |	Poor |  
| Underfitting |	Poor |	Poor |  
| Good | fit |	Good |  Good |  

### L1/L2 Regularization
Regularization applies a penalty term to the loss.
**L1(Lasso) Regularization** - penalty term is the sum of absolute values of weights multiplied by a regularization strength.  

<img width="266" height="82" alt="image" src="https://github.com/user-attachments/assets/e083919c-902a-437c-bd72-82ff447a3894" />  

this encourages sparse weights and can make some weights nearly zero.
**L2(Ridge) Regularization** - penalty term is the sum of square of the weights multiplied by a regularization strength.  
<img width="314" height="85" alt="image" src="https://github.com/user-attachments/assets/b8708cf2-ecf6-4135-bb90-281b09f3e239" />  

This penalizes large weights.

**Dropout** - randomly disable some neurons during training, which reduces the model relying on particular neurons heavily.

### Cross validation
Cross validation helps to check how well a model generalizes. when the dataset is small there is a chance the model tune parameters towards the train split. in cross validation, instead of just one train - test split the dataset is split differently and model is trained on each split.  
K-Fold cross validation is the common cross validation technique, in which the dataset is partitioned into n portions and test dataset is changed in each training session.  
<img width="800" height="466" alt="image" src="https://github.com/user-attachments/assets/91a6c7ef-0f22-4a2c-be77-65d5c04b0207" />  

Note: cross validation may become expensive in the case of large datasets.


## Bias and Variance
**Bias** is the error caused by a model when it is over simplified on the data.When bias is high, the model fails to understand underlying pattern correctly and causes underfitting.
Bias is the difference between average prediction and actual value.  


Bias = E{ȳ} - y  

  
**Variance** - When the model is highly sensitive about the data it fails to generalize the pattern correctly, which leads to overfitting.
variance measures how much predictions varies from their average prediction.    
Var(X) = E[X]<sup>2</sup> - [E(X)]<sup>2</sup>

increasing model complexity is a way to lower the bias, but that may lead to increase in variance. finding a lower bias variance sweet spot the key to improve model performance.


