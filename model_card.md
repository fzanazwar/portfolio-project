# Model Card

## Model Description

**Input:** 

1. Air temperature [K]: generated using a random walk process normalized to a standard deviation of 2 K around 300 K
2. Process temperature [K]: generated using a random walk process normalized to a standard deviation of 1 K, added to the air temperature plus 10 K.
3. Rotational speed [rpm]: calculated from powepower of 2860 W, overlaid with a normally distributed noise
4. Torque [Nm]: torque values are normally distributed around 40 Nm with an Ïƒ = 10 Nm and no negative values.
5. Tool wear [min]: the quality variants H/M/L add 5/3/2 minutes of tool wear to the used tool in the process.

**Output:** 

- Failure Type : The type of machine failure experienced

**Model Architecture:**

The model used was k-nearest neighbor with GridSearch for hyperparameter tuning.

## Performance

In order to evaluate the performance, the accuracy and the confusion matrix of the model were generated and presented. The accuracy of the model was 96.85%. Other than that, the confusion matrix showed that the model was able to have a low number of false negatives which in this case was predicting failures as 'No Failure'

![confusion_matrix](conf_matrix.png)

## Limitations

- All of the features are continuous numeric variables while the categorical feature ('Type') has been removed to reduce the complexity of the model.

- The dataset used is a reflection of a real predictive maintenance dataset and therefore, it is not a 100% real dataset. The model used in this project may react differently if a real industry dataset was used.

- The dataset has an imbalance of data between 'No Failure' and the other type of failures. This resulted in the model having a strong preference for 'No Failure' predictions. This can be avoided with dataset with balance data for each type of machine failure

## Trade-offs

Removing one of the features may result in missing out on an underlying relationship between that removed feature and the rest of the dataset used.
