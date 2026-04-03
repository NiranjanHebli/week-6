## Prompt:- 

Generate a clear decision tree for machine learning algorithm selection based on dataset characteristics. Start from questions such as dataset size, number of features, whether the data is linear or non-linear, labeled or unlabeled, and whether interpretability is important. Include common algorithms such as Linear Regression, Logistic Regression, KNN, Decision Tree, Random Forest, SVM, Naive Bayes, and K-Means, and show when each should be chosen. Present it as a simple tree or flowchart with brief reasoning at each branch.


## AI - Generated Output:-

[`ChatGPT Output`](https://chatgpt.com/s/t_69cfb32bcbbc8191bec189285fcc8472)


### Verify each recommendation against practical experience

Although KNN may work well on small datasets, it becomes slow when data grows. SVM often performs strongly on high-dimensional data, but training time increases on larger datasets. Random Forest is usually a strong default for tabular data because it handles noise well and needs less feature tuning.

### Identify edge cases the AI missed

The tree simplifies decision-making, so some cases need extra judgment. For instance:

Logistic Regression can still work on non-linear problems if features are engineered well.
Naive Bayes may perform surprisingly well even when feature independence is unrealistic.
Decision Trees can overfit badly on very small noisy datasets.
K-Means fails when clusters are not spherical or have unequal sizes.
SVM becomes expensive when sample size is very large.