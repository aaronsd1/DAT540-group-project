# Jupyter Notebook — Quick Reference

Jupyter lets us combine executable Python code, results, plots and written explanations in one notebook.

Our final project notebook should be readable as both **code** and **documentation**.

## Start JupyterLab

With the virtual environment activated:

```bash
jupyter lab
```

## Cell types

The two most important cell types are:

| Type     | Purpose                               |
| -------- | ------------------------------------- |
| Code     | Execute Python                        |
| Markdown | Explanations, headings, documentation |

Example code cell:

```python
import pandas as pd

df = pd.read_csv("../data/gallstone.csv")
df.head()
```

Example Markdown cell:

```text
## Exploratory Data Analysis

We first investigate the distribution of the target variable.
```

## Useful shortcuts

| Action             | Shortcut                 |
| ------------------ | ------------------------ |
| Run cell           | `Shift + Enter`          |
| Run without moving | `Ctrl + Enter`           |
| Add cell below     | `B` in command mode      |
| Add cell above     | `A` in command mode      |
| Delete cell        | `D`, `D` in command mode |
| Code cell          | `Y` in command mode      |
| Markdown cell      | `M` in command mode      |

## Markdown syntax

```text
# Main heading

## Section

### Subsection

**bold**

*italic*

- list item
- another item

1. numbered
2. list
```

## Execution order matters

Jupyter remembers variables that have already been executed.

For example:

```python
x = 10
```

Then later:

```python
print(x)
```

works because `x` exists in memory.

This can cause problems if cells are executed in a strange order.

Before submission, use:

**Restart Kernel → Run All**

The notebook should execute successfully **from top to bottom**.

## Recommended notebook style

Use Markdown before important code:

```text
## Train/Test Split

We separate the dataset so that the final model can be evaluated on observations it has not seen during training.
```

Then the relevant code.

Avoid creating one enormous code cell containing the entire project.

A good notebook tells a story:

```text
Question
   ↓
Code
   ↓
Result
   ↓
Interpretation
   ↓
Next question
```
