## Q1: Conceptual

When a dataset has 100 features and only 50 samples, it becomes a high-dimensional problem where models that control complexity usually perform best. Linear SVM and Logistic Regression with regularization are strong choices because they handle many features well and reduce overfitting through margin control or regularization. Naive Bayes can also work because its simple assumptions keep the model stable even with limited data.

Algorithms such as KNN often struggle because distance becomes less meaningful in high dimensions, while Decision Trees and Random Forests may overfit because there are too few samples to support many splits. RBF SVM can also fail if hyperparameters are not tuned carefully, since it may create an overly complex boundary.

---

## Q2: Coding — `model_selection_report(X, y, models_dict)`

```python 
import numpy as np
import pandas as pd
from scipy.stats import ttest_rel
from sklearn.model_selection import StratifiedKFold, cross_val_score
from sklearn.pipeline import Pipeline
from sklearn.preprocessing import StandardScaler

def model_selection_report(X, y, models_dict):
    results = {}
    cv = StratifiedKFold(n_splits=5, shuffle=True, random_state=42)

    for name, model in models_dict.items():
        pipeline = Pipeline([
            ('scaler', StandardScaler()),
            ('model', model)
        ])

        scores = cross_val_score(pipeline, X, y, cv=cv, scoring='accuracy')

        results[name] = {
            'mean': scores.mean(),
            'std': scores.std(),
            'scores': scores
        }

    df = pd.DataFrame({
        model: {
            'Mean Accuracy': vals['mean'],
            'Std Dev': vals['std']
        }
        for model, vals in results.items()
    }).T

    best_model = max(results, key=lambda x: results[x]['mean'])
    best_scores = results[best_model]['scores']

    p_values = {}
    for model, vals in results.items():
        if model != best_model:
            _, p = ttest_rel(best_scores, vals['scores'])
            p_values[model] = p

    df['Rank'] = df['Mean Accuracy'].rank(ascending=False)

    return df.sort_values('Rank'), best_model, p_values
```

---

## Q3: Analyze

If RBF SVM gives train accuracy 1.0 and test accuracy 0.52, the model is overfitting. It has learned the training data too closely but fails to generalize to new data. This usually happens when C or gamma is too high, making the decision boundary too complex.

Reducing gamma makes the boundary smoother, lowering C allows a softer margin, and applying proper feature scaling or PCA helps remove noise. In practice, tuning C and gamma together with GridSearchCV is the most reliable fix.
