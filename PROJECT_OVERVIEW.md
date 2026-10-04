# Project Overview

## Objective

This project uses clinical data from **319 patients with 38 features** to investigate gallstone disease.

The project has two objectives:

1. Build a machine-learning model that distinguishes patients with and without gallstone disease.
2. Investigate which clinical characteristics contribute most to the predictions.

The dataset is approximately balanced:

- 161 patients with gallstones
- 158 patients without gallstones

## Research Question

> **How accurately can machine-learning models classify gallstone disease using demographic, body-composition and laboratory measurements, and which clinical characteristics contribute most strongly to their predictions?**

This gives us two questions:

**Prediction:** How well can we classify gallstone disease?

**Explainability:** Which characteristics appear most important to the models?

---

# Project Workflow

```text
Dataset
   ↓
Initial inspection
   ↓
Exploratory Data Analysis
   ↓
Preprocessing
   ↓
Model training
   ↓
Model evaluation
   ↓
Explainability
   ↓
Interpretation
```

## Phase 1 — Understand the Dataset

Before modeling, understand what the data represents.

Tasks:

- Load the dataset with pandas.
- Check rows and columns.
- Identify the target.
- Understand the features.
- Inspect data types.
- Check missing values.
- Check duplicates.
- Check class distribution.
- Look for invalid or unusual values.
- Create a small data dictionary.
- Finalize the research question.

Everyone should be able to explain:

- What does one row represent?
- What does one column represent?
- What are the features?
- What is the target?
- Are there missing values?
- Is the target balanced?

---

# Phase 2 — Exploratory Data Analysis (EDA)

EDA helps us understand the data before training models.

We need at least **three meaningful visualizations with written interpretations**.

Possible questions include:

### Class Distribution

How many patients have and do not have gallstones?

### Feature Distributions

Do variables such as BMI, age, glucose or visceral fat differ between the two groups?

Useful plots:

```python
sns.histplot(...)
sns.boxplot(...)
sns.violinplot(...)
```

### Correlation

Which numerical features are strongly related?

```python
sns.heatmap(...)
```

Remember:

> **Correlation does not imply causation.**

### Outliers

Look for unusual observations, but do not automatically remove them. An outlier may be a valid patient rather than an error.

---

# Phase 3 — Preprocessing

Separate the input features from the target and create training/test data.

Conceptually:

```text
Dataset
   ↓
Features (X) + Target (y)
   ↓
Train/Test split
   ↓
Preprocessing
   ↓
Model
```

A typical split is approximately:

```text
80% training
20% testing
```

Use a **stratified split** so both sets contain approximately the same proportion of gallstone/no-gallstone patients.

## Scaling

Some algorithms work better when numerical features are on comparable scales.

`StandardScaler` is particularly relevant for Logistic Regression.

Decision Trees and Random Forests generally do not require scaling.

## Pipelines

scikit-learn `Pipeline` can connect preprocessing and model training:

```text
Data → Scaling → Model → Prediction
```

Pipelines make experiments easier to reproduce and help prevent data leakage.

---

# Phase 4 — Train Three Models

We will initially compare three classification models.

## 1. Logistic Regression

A simple and interpretable baseline.

It estimates the probability that a patient belongs to a class:

```text
Patient features
      ↓
Logistic Regression
      ↓
P(gallstone) = 0.82
```

Despite its name, Logistic Regression is commonly used for **classification**.

Its coefficients can also help with explainability.

## 2. Decision Tree

A Decision Tree makes a sequence of decisions based on feature values.

Simplified example:

```text
BMI > 28?
   /    \
 Yes     No
  |
Age > 55?
```

Advantages:

- Easy to understand.
- Easy to visualize.
- Handles nonlinear relationships.
- Does not require scaling.

Main disadvantage:

- Can easily **overfit**.

## 3. Random Forest

A Random Forest combines predictions from many Decision Trees.

```text
Tree 1 ─┐
Tree 2 ─┤
Tree 3 ─┼─→ Combined prediction
Tree 4 ─┤
Tree 5 ─┘
```

It is generally more robust than a single Decision Tree but less directly interpretable.

---

# Phase 5 — Model Evaluation

Do not compare models using accuracy alone.

We will consider:

| Metric    | Question                                                 |
| --------- | -------------------------------------------------------- |
| Accuracy  | How many predictions were correct?                       |
| Precision | When we predicted gallstones, how often were we correct? |
| Recall    | How many actual gallstone patients did we identify?      |
| F1        | How well do precision and recall balance?                |
| ROC-AUC   | How well does the model separate the two classes?        |

We should also use a **confusion matrix** to understand the types of mistakes each model makes.

## Cross-Validation

Because the dataset is relatively small, one train/test split may give unusually good or bad results.

Use **stratified 5-fold cross-validation** to get a more reliable estimate of model performance.

---

# Phase 6 — Explainability

This phase addresses the second project objective:

> Which clinical characteristics contribute most to the predictions?

We can investigate this using:

### Logistic Regression

Inspect model coefficients.

### Decision Tree

Visualize the tree and inspect important splits.

### Random Forest

Inspect feature importance.

### Permutation Importance

Shuffle one feature and measure how much model performance decreases.

If destroying the information in a feature significantly hurts performance, the model was relying on that feature.

### SHAP — Optional

If the core project is complete, SHAP can provide more detailed explanations.

It can answer:

**Global:** Which features matter most overall?

**Local:** Why was this particular patient classified this way?

---

# Phase 7 — Interpret the Results

The final analysis should answer more than:

> "Random Forest achieved X% accuracy."

Discuss:

- Which model performed best?
- Were the differences meaningful?
- Which model was most consistent?
- Which features appeared important?
- Did different models identify similar features?
- What kinds of mistakes did the models make?
- What limitations result from having only 319 patients?

Most importantly:

> **Feature importance does not demonstrate medical causation.**

If BMI is important to the model, we can say BMI was an important **predictive feature**.

We cannot conclude that BMI causes gallstone disease.

---

# Final Deliverables

## Jupyter Notebook

Suggested structure:

```text
1. Introduction and Research Question
2. Dataset
3. Initial Data Review
4. Exploratory Data Analysis
5. Preprocessing
6. Model Training
7. Model Evaluation
8. Explainability
9. Discussion
10. Conclusion
```

The notebook should explain both **what we did and why we did it**.

## Report

IEEE conference format covering:

- problem;
- dataset;
- methodology;
- models;
- results;
- explainability;
- limitations;
- conclusions;
- individual contributions.

## Presentation

10 minutes total.

With five members:

```text
Person 1 — Problem + research question
Person 2 — Dataset + EDA
Person 3 — Preprocessing + Logistic Regression
Person 4 — Decision Tree + Random Forest + evaluation
Person 5 — Explainability + conclusion
```

Everyone should still understand the entire project.

---

# Suggested Timeline

| Week | Focus           | Milestone                                                             |
| ---- | --------------- | --------------------------------------------------------------------- |
| 1    | Setup + dataset | Everyone can run the notebook and explain the dataset                 |
| 2    | EDA             | At least 3 meaningful plots with interpretations                      |
| 3    | Modeling        | Logistic Regression, Decision Tree and Random Forest run successfully |
| 4    | Evaluation      | Models compared using appropriate metrics and cross-validation        |
| 5    | Explainability  | Important predictive features investigated                            |
| 6    | Finalization    | Notebook, report and presentation ready                               |

## Working Principle

```text
Understand
    ↓
Implement
    ↓
Test
    ↓
Explain
```

Every important piece of code in the final notebook should be understood by the group.

A simple model that we can correctly train, evaluate and explain is more useful for this project than a complicated model we cannot defend during the oral examination.
