## Q1 — What is Logistic Regression? Is it classification or regression?

Logistic Regression is a supervised learning algorithm used to predict categorical outcomes, especially binary classes such as Yes/No or 0/1. Although called regression, it is mainly used for classification because it predicts probabilities and assigns classes.

## Q2 — Coding — Perform train-test split and scaling

```python
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import StandardScaler

# Train-test split
X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.2, random_state=42
)

# Feature scaling
scaler = StandardScaler()
X_train = scaler.fit_transform(X_train)
X_test = scaler.transform(X_test)

```
## Q3 — What is a confusion matrix? What does it represent?

A confusion matrix is a performance evaluation table used in classification to compare actual values with predicted values. It helps identify how many predictions are correct and where the model makes mistakes.

It contains True Positive (TP), True Negative (TN), False Positive (FP), and False Negative (FN), which show correct positive predictions, correct negative predictions, incorrect positive predictions, and incorrect negative predictions respectively.

From the confusion matrix, important metrics such as accuracy, precision, recall, and F1-score can also be calculated.