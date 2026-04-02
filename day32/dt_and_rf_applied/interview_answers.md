## Q1: Conceptual

If a Random Forest with 1000 trees gives the same accuracy as 100 trees, using 1000 trees is usually unnecessary because the extra trees increase training cost, memory usage, and prediction latency without meaningful performance gain. 

After a certain point, Random Forest reaches diminishing returns, where additional trees only provide marginal stability improvement. In production, 100 trees is often preferred because it is faster, cheaper, and easier to deploy while maintaining similar accuracy.

 A larger forest is only useful if you need slightly more stable predictions or lower variance in highly sensitive applications.

---

## Q2: Coding

```python id="b4m7zt"
import pandas as pd
import numpy as np
import time

from sklearn.model_selection import cross_validate

def compare_models(X, y, models_dict):
    results = []

    scoring = ['accuracy', 'f1']

    for name, model in models_dict.items():
        start = time.time()

        scores = cross_validate(
            model,
            X,
            y,
            cv=5,
            scoring=scoring,
            return_train_score=False
        )

        end = time.time()

        results.append({
            'Model': name,
            'Accuracy Mean': np.mean(scores['test_accuracy']),
            'Accuracy Std': np.std(scores['test_accuracy']),
            'F1 Mean': np.mean(scores['test_f1']),
            'F1 Std': np.std(scores['test_f1']),
            'Training Time (sec)': end - start
        })

    return pd.DataFrame(results)
```

---

## Q3: Debug

The feature importance ranking changes because Random Forest uses randomness in bootstrap sampling and feature selection for each tree. If `random_state` is not fixed, each run creates different trees, leading to different importance scores. To make results reproducible, set a fixed `random_state` when creating the model.
