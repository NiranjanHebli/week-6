# ExtraTreesClassifier vs RandomForest on Loan Approval Dataset

## Overview

`ExtraTreesClassifier` (Extremely Randomized Trees) is an ensemble learning algorithm available in scikit-learn that builds multiple decision trees and combines their predictions. It is similar to Random Forest but introduces more randomness during split selection, which often reduces variance and speeds up training.

## (a) How splitting differs

### Random Forest

 Random Forest selects a random subset of features at each node.
 For those selected features, it searches for the best split threshold using impurity reduction (Gini or entropy).

### Extra Trees

 Extra Trees also selects a random subset of features.
 Instead of searching for the best threshold, it generates random split thresholds and then chooses the best among those random candidates.

### Key Difference

Random Forest performs optimal split search, while Extra Trees uses randomized split search, making Extra Trees more stochastic.

## (b) Speed comparison

 Extra Trees is generally faster because it does not evaluate all possible split thresholds.
 Random Forest is slower because each split requires optimization over candidate thresholds.

### On the loan dataset

Extra Trees typically trains faster, especially when the dataset size increases.

## (c) Performance comparison on loan dataset

### Random Forest

 Usually gives slightly more stable predictions.
 May achieve marginally higher accuracy when the dataset is small.

### Extra Trees

 Often performs similarly or slightly better because additional randomness reduces overfitting.
 Works well when many features interact nonlinearly.

## Observed practical result

For synthetic loan approval data:

 Random Forest offers strong accuracy and interpretability through feature importance.
 Extra Trees often reaches comparable accuracy with lower training time.
