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

Feature distributions were compared between edible and poisonous classes using bar charts and count tables for all 22 features. Key findings:

- **odor** is the strongest separator with poisonous mushrooms concentrating in foul, creosote, and pungent odors while edible mushrooms are mostly odorless or almond/anise scented
- **spore-print-color**, **gill-color**, and **ring-type** also show strong class separation
- **bruises**, **stalk-surface-above-ring**, and **stalk-surface-below-ring** show moderate separation
- **gill-attachment** and **gill-spacing** show minimal differences between classes
- No numerical outliers exist as all features are categorical
- Class balance is close to even — 51.8% edible and 48.2% poisonous

**Odor Feature — Count Table:**

<img src="odor_table.png" width="300"/>

**Odor Feature — Distribution:**

<img src="odor_distribution.png" width="500"/>

