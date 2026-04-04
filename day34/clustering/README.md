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

This task explored hierarchical clustering using AgglomerativeClustering from scikit-learn and applied it to the Iris dataset with n_clusters=3. A dendrogram was generated using SciPy to visualize how samples merge step by step. The clustering results were then evaluated using ARI and compared with K-Means clustering to understand which method better matched the true species groups

## Key Learnings

- Agglomerative clustering builds clusters bottom up by merging nearest samples or groups iteratively.
- Dendrograms help visualize hierarchical relationships and cluster formation clearly.
- Unlike K-Means, hierarchical clustering does not depend on centroid initialization.
- ARI comparison showed how different clustering strategies affect alignment with true labels.
- On the Iris dataset, Agglomerative Clustering can sometimes produce slightly better ARI than K-Means depending on linkage choice.

## File:- 

### [`iris_clustering.ipynb`](./iris_clustering.ipynb) (Scroll Down)

## Part C - Interview Ready

### Solutions in :- [interview_answers.md](./interview_answers.md)

## Part D - AI Augmented

### Solutions in :- [ai_augmented.md](./ai_augmented.md)

