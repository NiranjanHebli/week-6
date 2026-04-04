# Day 34 - AM - Clustering: K-Means and DBSCAN

## Part A - Concept Application

This task perform unsupervised clustering on the Iris dataset by removing target labels and identifying natural groupings using K-Means and DBSCAN. Scale the feature values, apply K-Means with three clusters, compare cluster assignments with actual species labels, evaluate clustering quality using ARI and NMI, and visualize true labels against predicted clusters to understand how well unsupervised methods recover known classes.

## Key Learnings

- K-Means can closely approximate actual class structure when the dataset has clear separable patterns.
- Cluster labels must be evaluated using external metrics because label numbering is arbitrary.
- ARI and NMI help measure true clustering agreement with known classes.
- Some species overlap in feature space, which causes partial cluster confusion.
- DBSCAN may not always detect the same number of groups because it depends on density distribution.
- Strong clustering agreement suggests meaningful inherent structure in the dataset.

## File:- 

### [`iris_clustering.ipynb`](./iris_clustering.ipynb)

## Part B - Stretch Problem 

## Key Learnings

## File:- 

### [``](./)  (Scroll Down)


## Part C - Interview Ready

### Solutions in :- [interview_answers.md](./interview_answers.md)

## Part D - AI Augmented

### Solutions in :- [ai_augmented.md](./ai_augmented.md)

