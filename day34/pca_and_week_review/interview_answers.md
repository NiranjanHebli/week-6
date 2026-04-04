
## Q1: Conceptual - Complete ML Pipeline (1000 samples, 200 features)


A complete ML pipeline starts with data understanding and preprocessing:

1. Raw Data Inspection

   - Check missing values, duplicates, feature types, and class imbalance.
   - Since there are 200 features, I would also inspect correlations and feature distributions.

2. Preprocessing

   - Handle missing values using imputation.
   - Scale numeric features using StandardScaler because algorithms like SVM and Logistic Regression are sensitive to feature scale.
   - Encode categorical variables if present.

3. Feature Reduction / Selection

   - Apply PCA to reduce dimensionality if many features are correlated.
   - This helps reduce noise and training time.

4. Model Selection

   - Logistic Regression (LR): Good baseline because it is fast, interpretable, and works well for linearly separable patterns.
   - Random Forest (RF): Handles nonlinear relationships, robust to noise, and gives feature importance.
   - XGBoost: Chosen when higher predictive performance is needed because boosting captures difficult patterns better than bagging.

5. Validation

   - Use 5 fold cross validation for stable evaluation.
   - Compare models using accuracy, F1 score, or ROC AUC depending on task.

6. Hyperparameter Tuning

   - Tune parameters using GridSearchCV or RandomizedSearchCV.

7. Deployment

   - Save pipeline using pickle/joblib.
   - Deploy through API or web service.

8. Monitoring

   - Track drift and retrain when performance drops.

---

## Q2: Coding - weekly_model_comparison(X, y)

```python
import pandas as pd
from sklearn.model_selection import cross_val_score
from sklearn.pipeline import Pipeline
from sklearn.preprocessing import StandardScaler
from sklearn.decomposition import PCA
from sklearn.linear_model import LogisticRegression
from sklearn.ensemble import RandomForestClassifier
from sklearn.svm import SVC
from sklearn.neighbors import KNeighborsClassifier
from xgboost import XGBClassifier


def weekly_model_comparison(X, y, use_pca=False, n_components=0.95):
    models = {
        "Logistic Regression": LogisticRegression(max_iter=1000),
        "Random Forest": RandomForestClassifier(),
        "XGBoost": XGBClassifier(eval_metric='logloss'),
        "SVM": SVC(),
        "KNN": KNeighborsClassifier()
    }

    results = []

    for name, model in models.items():
        steps = [('scaler', StandardScaler())]

        if use_pca:
            steps.append(('pca', PCA(n_components=n_components)))

        steps.append(('model', model))

        pipeline = Pipeline(steps)

        scores = cross_val_score(pipeline, X, y, cv=5, scoring='accuracy')

        results.append({
            'Model': name,
            'Mean Accuracy': scores.mean(),
            'Std Dev': scores.std()
        })

    df = pd.DataFrame(results)
    return df.sort_values(by='Mean Accuracy', ascending=False)
```

---

## Q3: Analyze - Why accuracy drops after PCA (0.92 -> 0.85)


Even though PCA keeps 95% variance, accuracy can still drop for several reasons:

1. Variance != Predictive Information

  - PCA preserves maximum variance, but high variance directions may not be the most useful for classification.

2. Loss of Important Low Variance Features

  - Some features with low variance may contain strong class-separating information, which PCA may discard.

3. Transformation Reduces Interpretability of Feature Relationships

  - PCA creates linear combinations of features, which may weaken patterns some models rely on.

