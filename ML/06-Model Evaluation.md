# Model Evaluation
Evaluating a model is very important to ensure that it performs well on unseen data as well. 
## Training, validation, and test datasets
Available dataset has to be split into training, validation and test datasets.
**Training Dataset** - A subset of the available dataset which is used to train the model and tune the weights.
**Validation Dataset** - A subset of the original dataset, used to validate the model generally at the end of every epoch. very useful to find overfitting early. weights are not updated during validation.
**Test Dataset** - A subset of the original dataset, used to test the accuracy of the model on unseen data.

## Overfitting and underfitting
Overfitting happens when the model leans completely on training data without generalization. Performance on test dataset will be poor where as the performance will be very good on the training dataset.


