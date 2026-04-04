# Day 34 - PM - Clustering: PCA and Week Comparison

## Part A - Concept Application

This task involved building a complete Week 6 ML review notebook covering major supervised, ensemble, unsupervised, and dimensionality reduction techniques. Each section includes a short description, when to use the algorithm, a minimal code example, important hyperparameters, and a practical use case. A text based selection flowchart and Wine dataset validation were also added.

## Key Learnings

- Different algorithms suit different data patterns: linear models for simple boundaries, tree based models for non linearity, and ensemble methods for higher accuracy.

- Hyperparameters such as depth, neighbors, kernels, and learning rate strongly affect model performance and must be tuned carefully.

- Testing multiple algorithms on the same dataset helps compare behavior and choose models more confidently for future ML tasks.

## File:- 

### [`week_review.ipynb`](./week_review.ipynb)

## Part B - Stretch Problem 

In this task, we implemented image compression using PCA by decomposing each RGB channel separately and reconstructing the image using different numbers of principal components. Compared compressed outputs visually and evaluated performance using compression ratio and mean squared error (MSE).

## Key Learnings

- PCA reduces image dimensionality by preserving the most important variance in fewer components.
- Lower n_components increases compression but causes more information loss.
- Higher n_components improves reconstruction quality with lower MSE.
- Compression ratio and MSE together help balance storage efficiency and image fidelity.


## File:- 

### [`image_compression.ipynb`](./image_compression.ipynb) 

## Part C - Interview Ready

### Solutions in :- [interview_answers.md](./interview_answers.md)

## Part D - AI Augmented

### Solutions in :- [ai_augmented.md](./ai_augmented.md)

