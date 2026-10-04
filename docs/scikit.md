# scikit-learn — Quick Reference

scikit-learn (`sklearn`) is our main machine-learning library.

We will use it for preprocessing, training, prediction, cross-validation and evaluation.

## Common imports

```python
from sklearn.model_selection import train_test_split

from sklearn.preprocessing import StandardScaler

from sklearn.linear_model import LogisticRegression
from sklearn.tree import DecisionTreeClassifier
from sklearn.ensemble import RandomForestClassifier

from sklearn.metrics import (
    accuracy_score,
    precision_score,
    recall_score,
    f1_score,
    confusion_matrix,
    roc_auc_score
)
```

Do not worry about memorizing these imports. Look them up when needed.

---

# Features and target

Machine-learning examples commonly use:

```text
X = features
y = target
```

For example:

```python
X = df.drop(columns=["target"])
y = df["target"]
```

Conceptually:

```text
X

Age | BMI | Glucose | ...
-------------------------
45  | 27  | 95      | ...
62  | 31  | 121     | ...
...


y

Gallstone
---------
0
1
...
```

---

# Train/test split

```python
X_train, X_test, y_train, y_test = train_test_split(
    X,
    y,
    test_size=0.2,
    stratify=y,
    random_state=42
)
```

Important parameters:

| Parameter         | Meaning                    |
| ----------------- | -------------------------- |
| `test_size=0.2`   | Reserve 20% for testing    |
| `stratify=y`      | Preserve class proportions |
| `random_state=42` | Make split reproducible    |

The number `42` is not special. Using a fixed value simply means we get the same random split when rerunning the notebook.

---

# The most important scikit-learn pattern

Almost every model follows the same API:

```text
Create
  ↓
Fit
  ↓
Predict
  ↓
Evaluate
```

Or in Python:

```python
model = SomeModel()

model.fit(X_train, y_train)

predictions = model.predict(X_test)
```

Once you understand this pattern, learning new scikit-learn models becomes much easier.

---

# Logistic Regression

```python
model = LogisticRegression()

model.fit(X_train, y_train)

predictions = model.predict(X_test)
```

Probability predictions:

```python
probabilities = model.predict_proba(X_test)
```

---

# Decision Tree

```python
model = DecisionTreeClassifier(
    random_state=42
)

model.fit(X_train, y_train)

predictions = model.predict(X_test)
```

Possible configuration:

```python
model = DecisionTreeClassifier(
    max_depth=4,
    random_state=42
)
```

---

# Random Forest

```python
model = RandomForestClassifier(
    random_state=42
)

model.fit(X_train, y_train)

predictions = model.predict(X_test)
```

Possible configuration:

```python
model = RandomForestClassifier(
    n_estimators=200,
    max_depth=5,
    random_state=42
)
```

---

# Scaling

```python
scaler = StandardScaler()

X_train_scaled = scaler.fit_transform(X_train)
X_test_scaled = scaler.transform(X_test)
```

Notice the important difference:

```python
fit_transform(X_train)
```

versus:

```python
transform(X_test)
```

The scaler **learns only from training data**.

We do not want information from the test set leaking into training.

---

# Pipelines

A pipeline connects preprocessing and modeling.

```python
from sklearn.pipeline import Pipeline
```

Conceptually:

```text
Raw features
     ↓
StandardScaler
     ↓
LogisticRegression
     ↓
Prediction
```

Pipelines help prevent mistakes and make experiments easier to reproduce.

---

# Evaluation metrics

After:

```python
predictions = model.predict(X_test)
```

we can calculate metrics.

| Metric           | Command                                 |
| ---------------- | --------------------------------------- |
| Accuracy         | `accuracy_score(y_test, predictions)`   |
| Precision        | `precision_score(y_test, predictions)`  |
| Recall           | `recall_score(y_test, predictions)`     |
| F1               | `f1_score(y_test, predictions)`         |
| Confusion matrix | `confusion_matrix(y_test, predictions)` |

Example:

```python
accuracy = accuracy_score(
    y_test,
    predictions
)

print(accuracy)
```

---

# Confusion matrix

```python
cm = confusion_matrix(
    y_test,
    predictions
)

print(cm)
```

The matrix helps us understand what types of mistakes the model makes rather than only how many predictions were correct.

---

# Cross-validation

```python
from sklearn.model_selection import cross_val_score
```

Example:

```python
scores = cross_val_score(
    model,
    X,
    y,
    cv=5
)
```

Then:

```python
scores.mean()
```

Cross-validation evaluates the model across multiple different subsets of the dataset instead of relying entirely on one train/test split.

For our classification project, we will eventually use **stratified** cross-validation.

---

# Model parameters

See a model's parameters:

```python
model.get_params()
```

Examples include:

```text
Decision Tree:
    max_depth
    min_samples_split
    min_samples_leaf

Random Forest:
    n_estimators
    max_depth
    min_samples_leaf
    max_features
```

These are called **hyperparameters**.

They control how the algorithm behaves.

---

# Feature importance

Random Forest:

```python
model.feature_importances_
```

Logistic Regression coefficients:

```python
model.coef_
```

These require careful interpretation and should not automatically be interpreted as medical causation.

---

# Useful commands summary

| Task                  | Command                       |
| --------------------- | ----------------------------- |
| Split data            | `train_test_split(...)`       |
| Scale                 | `StandardScaler()`            |
| Train                 | `model.fit(X_train, y_train)` |
| Predict class         | `model.predict(X_test)`       |
| Predict probabilities | `model.predict_proba(X_test)` |
| Parameters            | `model.get_params()`          |
| Accuracy              | `accuracy_score(...)`         |
| Precision             | `precision_score(...)`        |
| Recall                | `recall_score(...)`           |
| F1                    | `f1_score(...)`               |
| Confusion matrix      | `confusion_matrix(...)`       |
| Cross-validation      | `cross_val_score(...)`        |

## The pattern to remember

Don't memorize hundreds of scikit-learn commands.

Remember:

```python
model = Model(...)

model.fit(X_train, y_train)

predictions = model.predict(X_test)

metric = some_metric(y_test, predictions)
```

A large part of the machine-learning code in this project will follow this same pattern.
