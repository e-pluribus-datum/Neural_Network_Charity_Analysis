# Neural Network Charity Analysis

## Overview

This project used neural networks to create binary classifier to predict whether applicants will be successful if funded by Alphabet Soup.

## Data Preprocessing

The target variable was the binary column "IS_SUCCESSFUL".

Feature variables included Application_Type, Affiliation, Classification, Use_Case, Organization, Income, and Ask_Amt.

Status, Special_Considerations, and EIN were removed from the input data. Names were also removed in v1 of the model.

## Results

v1 dropped the Name column to preclude its use as a feature in the model.

v2 bins all Name's into 4 bins by their frequency in the dataset.

v3 creates a bin for any names that occur only once in the dataset, reducing the number of names from 19,568 to 793. The neural network took a long time (about 30 minutes) to complete training and produces the highest accuracy.

v4 adds an additional bin for names that occur 2 - 5 times. This appeared to affect the model accuracy negatively.

|           | 1 | 2 | 3 | 4 |
| -         | - | - | - | - |
| Loss      | 0.5586 | 0.5581 | 0.6142 | 0.7449 |
| Accuracy  | 0.7256 | 0.7387 | 0.7927 | 0.7874 |

3 layers of neurons were used in all versions. Using additional layers (not shown) did not appear to appreciably improve the model's accuracy.

The models used 2x as many neurons in the first hidden layer as the number of input features. This scaling factor was reduced per layer in even increments, giving scaling factors of 1.33 and 0.67 for the remaining two hidden layers.

An alternate node scaling scheme (not shown) was attempted for each version, where the number of nodes per hidden layer were 2, 1, and 0.5, scaled geometrically. This appeared to affect the model accuracy negatively for every alternate version tested.

## Summary

The best model accuracy was acheived by binning all one-time applicants to the same 'Name' category.

An supervised ML classifier such as RandomForest might be able to acheive similar results without the long training time experienced for v3.
