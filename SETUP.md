# Development Environment

This project uses Python and a small set of data-science libraries.

## Quick Setup

From the project directory:

### 1. Create a virtual environment

```bash
python -m venv .venv
```

### 2. Activate it

**Windows PowerShell**

```powershell
.venv\Scripts\Activate.ps1
```

**macOS/Linux**

```bash
source .venv/bin/activate
```

### 3. Install all project dependencies

```bash
python -m pip install -r requirements.txt
```

### 4. Start JupyterLab

```bash
python -m jupyterlab
```

That's everything needed for normal project work.

---

# requirements.txt

The repository should contain:

```text
jupyterlab
pandas
numpy
openpyxl
matplotlib
seaborn
scikit-learn
scipy
```

`openpyxl` is required because our dataset is stored as an Excel `.xlsx` file.

Optional libraries such as SHAP should only be added when we actually decide to use them.

---

# Tools

| Tool         | Purpose                                     |
| ------------ | ------------------------------------------- |
| Python       | Programming language                        |
| Git/GitHub   | Version control and collaboration           |
| venv         | Isolated Python environment                 |
| JupyterLab   | Run and document the analysis               |
| pandas       | Load and manipulate tabular data            |
| NumPy        | Numerical operations                        |
| Matplotlib   | Basic plotting                              |
| Seaborn      | Statistical visualization / EDA             |
| scikit-learn | Machine learning and evaluation             |
| SciPy        | Additional statistical/scientific functions |
| SHAP         | Optional model explainability               |

---

## Python

Python is the programming language used throughout the project.

Check your installation:

```bash
python --version
python -m pip --version
```

---

## Virtual Environment

A virtual environment keeps the project's Python packages separate from packages used by other projects.

Create it once:

```bash
python -m venv .venv
```

Activate it whenever you work on the project.

You normally know it is active when the terminal begins with:

```text
(.venv)
```

To exit:

```bash
deactivate
```

Do **not** commit `.venv` to Git.

Add this to `.gitignore`:

```text
.venv/
```

---

## JupyterLab

JupyterLab lets us combine Python code, results, plots and written explanations inside `.ipynb` notebooks.

Start it with:

```bash
python -m jupyterlab
```

When creating/opening a notebook, select the Python kernel belonging to the project's `.venv`.

You can verify the active Python environment inside a notebook:

```python
import sys
print(sys.executable)
```

---

## pandas

Used for loading, inspecting and manipulating tabular data.

```python
import pandas as pd
```

Examples:

```python
df = pd.read_excel("data/dataset.xlsx")

df.head()
df.shape
df.columns
df.describe()
df.isna().sum()
df.duplicated().sum()
```

Think of a pandas `DataFrame` as a programmable Excel table.

---

## NumPy

Provides numerical and array operations.

```python
import numpy as np
```

pandas and scikit-learn use NumPy internally, so we probably will not need much direct NumPy code initially.

---

## Matplotlib

Basic plotting library.

```python
import matplotlib.pyplot as plt
```

Example:

```python
plt.hist(df["Age"])
plt.xlabel("Age")
plt.ylabel("Patients")
plt.show()
```

---

## Seaborn

Used primarily for Exploratory Data Analysis.

```python
import seaborn as sns
```

Common plots:

```python
sns.histplot(...)
sns.boxplot(...)
sns.heatmap(...)
```

Use Seaborn to **visualize and understand data**.

It does not train our machine-learning models.

---

## scikit-learn

Our main machine-learning library.

Common imports:

```python
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import StandardScaler
from sklearn.linear_model import LogisticRegression
from sklearn.tree import DecisionTreeClassifier
from sklearn.ensemble import RandomForestClassifier
```

It will handle:

- train/test splitting;
- preprocessing;
- pipelines;
- model training;
- predictions;
- cross-validation;
- evaluation;
- feature importance.

The package is installed as:

```text
scikit-learn
```

but imported through:

```python
import sklearn
```

---

## SciPy

Provides additional statistical and scientific functions.

We probably will not use it directly during the early phases, but other data-science libraries depend on it.

---

# Optional Tools

## SHAP

SHAP can provide more detailed explanations of model predictions.

It may help answer:

- Which features matter most overall?
- Why did the model classify a particular patient this way?

It is optional and should only be introduced after the basic models work.

If needed:

```bash
python -m pip install shap
```

Then add:

```text
shap
```

to `requirements.txt`.

## TensorFlow / Keras

**Not required for the initial project.**

Keras is primarily used for neural networks. Our first models are:

```text
Logistic Regression
Decision Tree
Random Forest
```

All three are available in scikit-learn.

We should only consider an ANN after the core project is complete.

---

# First-Time Setup Checklist

A new group member should only need to do this:

```bash
git clone <repository-url>
cd DAT540-group-project

python -m venv .venv
```

Activate the environment:

```powershell
# Windows
.venv\Scripts\Activate.ps1
```

or:

```bash
# macOS/Linux
source .venv/bin/activate
```

Then:

```bash
python -m pip install -r requirements.txt
python -m jupyterlab
```

After that, open the project notebook and verify that this works:

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
import sklearn

print("Environment is working.")
```
