# Day 33 - AM - SVM and KNN

## Part A - Concept Application

This task deals with building a handwritten digit classifier using the scikit-learn digits dataset and compared SVM (RBF) with KNN after feature scaling. Used GridSearchCV for SVM tuning and evaluated both models using accuracy, confusion matrix, and F1-score. Also found out confusing pairs in the same.

## Key Learnings

- Working of KNN and SVM algorithm.
- Learned preprocessing with feature scaling.
- Tuning SVM hyperparameters using GridSearchCV.

## File:- 

### [`digit_classifier_svm_knn.ipynb`](./digit_classifier_svm_knn.ipynb)


## Part B - Stretch Problem 

This task deals with implementing approximate nearest neighbor search using FAISS on the scikit-learn digits dataset and compared its query speed with sklearn KNN. Measured retrieval time for multiple queries to understand how FAISS performs for similarity search.

## Key Learnings

- FAISS performs faster than sklearn, however its advantage is more visible when comparing on large dataset.
- On smaller dataset like digits dataset, the speed difference between FAISS and k-means is smaller

```
sklearn KNN time: 0.006618 sec
FAISS time: 0.003293 sec
```


## File:- 

### [`digit_classifier_svm_knn.ipynb`](./digit_classifier_svm_knn.ipynb)  (Scroll Down)


## Part C - Interview Ready

### Solutions in :- [interview_answers.md](./interview_answers.md)

## Part D - AI Augmented

### Solutions in :- [ai_augmented.md](./ai_augmented.md)

