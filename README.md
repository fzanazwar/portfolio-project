# Predicting Machine Type Failure

This project is about predicting the type of machine failure based on certain environmental factors and operational settings of the machine using a machine learning model. The machine learning model with its optimised hyperparameters was successful in producing a high accuracy result and low number of false negatives.

## DATA
The dataset is called Machine Predictive Maintenance Classification and can be found and downloaded in [Kaggle](https://www.kaggle.com/datasets/shivamb/machine-predictive-maintenance-classification)

There are 10 000 instances in the dataset which comprises of:

1. UID: unique identifier ranging from 1 to 10000
2. Product ID: a variant-specific serial number
3. Type : consists of a letter L, M, or H for low (50% of all products), medium (30%), and high (20%) as product quality variants
4. Air temperature [K]: generated using a random walk process normalized to a standard deviation of 2 K around 300 K
5. Process temperature [K]: generated using a random walk process normalized to a standard deviation of 1 K, added to the air temperature plus 10 K.
6. Rotational speed [rpm]: calculated from power of 2860 W, overlaid with a normally distributed noise
7. Torque [Nm]: torque values are normally distributed around 40 Nm with an Ïƒ = 10 Nm and no negative values.
8. Tool wear [min]: The quality variants H/M/L add 5/3/2 minutes of tool wear to the used tool in the process.
9. Target : Indicates whether the machine has failed in this particular data point where 1 means Failure and 0 means No Failure
10. Failure Type : The type of machine failure experienced which includes No Failure, Heat Dissipation Failure, Power Failure, Overstrain Failure,Tool Wear Failure and Random Failures.

## MODEL 
The model used is the k-nearest neighbor model. The reason for choosing this is that it is easy to implement for multi-class classification problems which is the case for this project. Moreover, although it will have problems if the datasets have high dimensionality, the dimensionality of the dataset used was low enough to not cause any problems.

## HYPERPARAMETER OPTIMSATION
The hyperparameters I chose to optimise were 

1. the number of neighbors (n_neighbors) : 1 - 20
2. the leaf size (leaf_size) : 15 - 45
3. the algorithm used to compute the nearest neighbors : 'auto', 'ball_tree', 'kd_tree', 'brute'

These hyperparameters were optimised using GridSearch.

## RESULTS
The accuracy of the model was 97.5% with very low number of false negatives which can be seen in the confusion matrix below. However, it should be noted that 'Random Failure' and 'Tool Wear Failure' have no correct predictions while the other type of failures have low number of predictions. Unfortunately, this is the cause of imbalance data from the dataset used where there is a large percentage of 'No Failure' instances while 'Random Failure' and 'Tool Wear Failure' have the lowest percentage of instances in the dataset. As a result, the model have a strong preference in 'No Failure' predictions.

![confusion_matrix](conf_matrix2.png) ![failure_types](failure_types.png)
