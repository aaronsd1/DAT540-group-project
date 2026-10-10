# Project Workflow & Responsibilities

## Overview

The project is divided into five individual responsibilities. Each member is responsible for researching, implementing, testing, and documenting their assigned part.

**The goal is to establish a shared foundation so everyone can work independently without duplicating work.**

## 1. Project Flow

```text
Dataset
   │
   ▼
[Aaron] Dataset Exploration & Setup
   │
   ├── Load and inspect dataset
   ├── Clean data if necessary
   ├── Create 3+ meaningful visualizations
   └── Prepare shared training/test data
   │
   ▼
   HANDOVER: X_train, X_test, y_train, y_test
   │
   ├── [Member 2] Logistic Regression
   │
   ├── [Member 3] Decision Tree
   │
   └── [Member 4] Random Forest
   │
   ▼
[Member 5] Model Comparison & Explainability
   │
   ▼
[Everyone] Report, Presentation & Submission
```

## 2. Initial Setup & Handover

**Aaron establishes the common starting point.**

This includes loading the dataset, exploring its contents, checking data quality, and creating a shared, reproducible train/test split.

The handover should provide:

| Variable  | Purpose                             |
| --------- | ----------------------------------- |
| `X_train` | Features used for model training    |
| `X_test`  | Features reserved for final testing |
| `y_train` | Correct diagnoses for training      |
| `y_test`  | Correct diagnoses for testing       |

These variables should be generated through shared data-preparation code so every member gets the same data.

**Once this foundation is available, Members 2, 3 and 4 can start implementing their models simultaneously.**

They do not need to wait for all EDA visualizations or report writing to be finished.

## 3. Individual Responsibilities

### Aaron — Dataset & EDA

- Load, inspect, and prepare the dataset.
- Create at least three meaningful visualizations.
- Document observations and findings.
- Establish the shared train/test split.
- Write the dataset and EDA report sections.

**Done when:** Everyone can access the same training/test data, and the dataset exploration is documented.

### Members 2–4 — Machine Learning Models

Each member owns one model:

- Member 2: Logistic Regression
- Member 3: Decision Tree
- Member 4: Random Forest

Each is responsible for:

- Researching and understanding the assigned model.
- Implementing it using scikit-learn.
- Training it using the shared data.
- Evaluating accuracy, precision, recall, F1, and ROC-AUC.
- Performing cross-validation.
- Explaining results, strengths, and limitations.
- Writing the corresponding report section.

**Done when:** The model runs successfully, results are reproducible, and the member can explain the implementation and findings.

### Member 5 — Comparison & Explainability

- Agree on evaluation metrics with model owners.
- Compare the three models using consistent results.
- Investigate which clinical features influence predictions.
- Summarize findings and limitations.
- Write the comparison, explainability, and discussion sections.

**Done when:** The models have been fairly compared and the main findings can be explained.

Member 5 can research evaluation methods while the models are being developed, but final comparisons depend on the model results.

## 4. Parallel Work & GitHub

Use separate notebooks to avoid merge conflicts:

```text
notebooks/
├── 01_exploration.ipynb
├── 02_logistic_regression.ipynb
├── 03_decision_tree.ipynb
├── 04_random_forest.ipynb
└── 05_comparison.ipynb

src/
└── data_preparation.py
```

The shared preparation module provides consistent training/test data to all model notebooks.

Each member should:

1. Work on their own Git branch.
2. Keep their assigned notebook documented.
3. Commit and push changes regularly.
4. Open a Pull Request when their work is ready.
5. Have another member review the changes before merging.

**Important:** Model owners should use the same split, evaluation conventions, and cross-validation strategy. Any model-specific preprocessing must be fitted using training data only.

## 5. Shared Responsibilities

All five members participate in:

- Finalizing the research question.
- Reviewing and understanding each other's work.
- Interpreting the overall findings.
- Combining the notebook and IEEE report.
- Preparing the 10-minute presentation.
- Testing and packaging the final submission.

Each member should be able to explain their own work and understand the overall workflow.

## 6. Key Milestones

| Milestone        | Expected result                                        |
| ---------------- | ------------------------------------------------------ |
| Foundation ready | Shared data preparation and train/test split available |
| Models ready     | All three models trained and evaluated                 |
| Analysis ready   | Model comparison and explainability completed          |
| Report ready     | Individual contributions combined into IEEE format     |
| Submission ready | Runnable notebook, report PDF, and PowerPoint packaged |

**Final deadline: November 20, 23:59.**

The most important principle is that **the initial setup enables parallel work**. Once the shared dataset preparation is ready, the three model owners can work independently while EDA documentation and evaluation research continue in parallel.

All submitted code must be written and understood by the group, following the course's restrictions on generative AI.
