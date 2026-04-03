

# Q1: Conceptual

## Fundamental Difference

Support Vector Machine SVM finds the boundary that maximizes the margin between classes, focusing mainly on support vectors (closest points).

Logistic Regression finds the boundary by minimizing prediction error and estimating class probabilities.

## When to prefer which

- Prefer SVM when classes are clearly separable and high dimensional data is involved.

- Prefer Logistic Regression when probability outputs and interpretability are important.

---

# Q2: Coding 
## KNN from Scratch using NumPy

```python
import numpy as np

def knn_from_scratch(X_train, y_train, X_test, k):
    predictions = []

    for test_point in X_test:
        distances = np.sqrt(np.sum((X_train - test_point) ** 2, axis=1))

        k_indices = np.argsort(distances)[:k]
        k_labels = y_train[k_indices]

        values, counts = np.unique(k_labels, return_counts=True)
        prediction = values[np.argmax(counts)]

        predictions.append(prediction)

    return np.array(predictions)
```

---

# Q3: Debug

## Why SVM gives 0.50 Accuracy ?

### Likely Issue: 
- Features are not scaled

The biggest problem is that Support Vector Machine SVM is very sensitive to feature magnitude.

Here:

- salary = 50,000 to 200,000
- age = 20 to 60

Salary dominates distance calculations, so age contributes very little to the decision boundary.


The RBF kernel relies on distance between points. If one feature is much larger, the kernel becomes distorted and classification behaves almost randomly.

## Fix

```python
from sklearn.preprocessing import StandardScaler

scaler = StandardScaler()

X_train_scaled = scaler.fit_transform(X_train)
X_test_scaled = scaler.transform(X_test)

svm = SVC(kernel='rbf', C=1.0)
svm.fit(X_train_scaled, y_train)

print(svm.score(X_test_scaled, y_test))
```

Accuracy usually improves significantly after scaling because both features contribute equally.
