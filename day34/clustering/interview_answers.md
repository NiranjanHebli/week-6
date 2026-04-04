## Q1: Conceptual

K-Means is called a greedy algorithm because at each iteration it makes the locally best decision: assigning each point to the nearest centroid and then updating centroids to minimize within cluster distance. It does not reconsider earlier assignments globally, so it may converge to a local minimum instead of the best possible clustering.

Yes, K-Means can get stuck in local minima because the final result depends heavily on the initial centroid positions. Different starting points may produce different cluster formations and different objective values.

KMeans++ initialization improves this by choosing initial centroids that are far apart from each other. This reduces poor starting positions, speeds up convergence, and often produces better clustering quality than random initialization.

---

## Q2: Coding

```python
import numpy as np

def kmeans(X, k, max_iter=100):
    np.random.seed(42)

    # Randomly choose initial centroids
    indices = np.random.choice(len(X), k, replace=False)
    centroids = X[indices]

    for _ in range(max_iter):
        # Compute distances
        distances = np.linalg.norm(X[:, np.newaxis] - centroids, axis=2)

        # Assign clusters
        labels = np.argmin(distances, axis=1)

        # Compute new centroids
        new_centroids = np.array([
            X[labels == i].mean(axis=0) if np.any(labels == i) else centroids[i]
            for i in range(k)
        ])

        # Stop if converged
        if np.allclose(centroids, new_centroids):
            break

        centroids = new_centroids

    return labels, centroids
```

---

## Q3: Analyze

A silhouette score of 0.25 suggests weak cluster separation. It means clusters exist, but they overlap considerably and may not represent natural groupings well.

The next step would be to test different values of K and compare silhouette scores to see if another cluster count performs better. I would also inspect feature scaling, visualize clusters if possible, and check whether some features are adding noise.

