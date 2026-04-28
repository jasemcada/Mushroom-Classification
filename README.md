# Mushroom-Classification

This repository holds an attempt to apply classification algorithms to mushroom edibility prediction using data from the [UCI Mushroom Dataset](https://www.kaggle.com/datasets/uciml/mushroom-classification) Kaggle challenge.

## Overview
The task, as defined by the Kaggle challenge, is to use 23 categorical physical characteristics of mushrooms such as cap shape, odor, gill color, and habitat to classify each mushroom as either edible or poisonous. The approach in this repository formulates the problem as a binary classification task, comparing the performance of 4 classifiers: Decision Tree, Random Forest, Logistic Regression, and Gaussian Naive Bayes. Our best models (Decision Tree and Random Forest) achieved 100% accuracy on the test set, confirming that the physical features in this dataset provide perfect separation between edible and poisonous mushrooms.

## Summary of Workdone

### Data

- **Type:** Input: CSV file of 23 categorical features (letter-encoded), Output: binary class label (edible or poisonous)
- **Size:** 8,124 samples, 22 features + 1 target column
- **Split:** 6,499 samples for training, 1,625 for testing

### Preprocessing / Cleanup

- Dropped `veil-type` feature as it contained only one unique value across all 8,124 samples, making it completely uninformative for any ML model
- Replaced missing values in `stalk-root` (2,480 entries encoded as `?`) with the most frequent value (mode) as a simple imputation strategy
- Label encoded the target variable (edible=0, poisonous=1)
- One-hot encoded all 21 remaining categorical features, expanding the dataset from 21 columns to 115 binary columns
- Dataset was shuffled before splitting to ensure a representative train/test split

### Data Visualization
