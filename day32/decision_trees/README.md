# Day 32 - AM - Decision Tree And Random Forest

## Part A - Concept Application

This task predicts loan approval using Decision Tree and Random Forest on synthetic banking data. The synthetic data is generated using a combination of random and logical operations to create a dataset with 2000 samples and 7 features. The task trains a Decision Tree and Random Forest model on the data and evaluates their performance using accuracy, F1 score, and ROC-AUC score.

## Key Learnings

- Decision Tree provides clear and explainable approval rules.
- Random Forest improves accuracy and reduces overfitting.
- RandomizedSearchCV helps find better model parameters.
- F1-score and ROC-AUC give better evaluation than accuracy alone.
= Permutation importance explains feature impact more reliably than default feature importance.
- In banking, balancing interpretability and accuracy is important for deployment.

## File

### [`loan_approval.ipynb`](./loan_approval.ipynb)


## Part B - Stretch Problem 
wThis task compares ExtraTreesClassifier and RandomForestClassifier on the loan approval dataset. 

## Key Learnings

- Extra Trees uses random split thresholds, while Random Forest searches for the best split.
- Extra Trees usually trains faster because split calculation is simpler.
Random Forest often gives more stable predictions on small datasets.
- Extra Trees can reduce overfitting through additional randomness.
Both models perform similarly well for loan approval classification.

## Files:- 

- ### [`loan_approval.ipynb`](./loan_approval.ipynb) (Scroll Down)

For Comparison:-
- ### [`extra_trees_comparison.md`](./extra_trees_comparison.md)

## Part C - Interview Ready

### Solutions in :- [interview_answers.md](./interview_answers.md)

## Part D - AI Augmented

### Solutions in :- [ai_augmented.md](./ai_augmented.md)

