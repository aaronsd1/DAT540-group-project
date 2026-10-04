# pandas — Quick Reference

pandas is our main library for working with the gallstone dataset.

A pandas `DataFrame` can be thought of as a programmable table.

```python
import pandas as pd
```

## Loading data

| Task  | Command                      |
| ----- | ---------------------------- |
| CSV   | `pd.read_csv("file.csv")`    |
| Excel | `pd.read_excel("file.xlsx")` |

```python
df = pd.read_csv("../data/gallstone.csv")
```

We commonly use `df` as shorthand for **DataFrame**.

## First inspection

These commands will be among the first things we run on the dataset.

| Question         | Command         |
| ---------------- | --------------- |
| First 5 rows     | `df.head()`     |
| First 10 rows    | `df.head(10)`   |
| Last rows        | `df.tail()`     |
| Rows × columns   | `df.shape`      |
| Column names     | `df.columns`    |
| Data types       | `df.dtypes`     |
| General overview | `df.info()`     |
| Statistics       | `df.describe()` |

A useful initial sequence is:

```python
df.head()
df.shape
df.info()
df.describe()
```

## Selecting columns

One column:

```python
df["Age"]
```

Several columns:

```python
df[["Age", "BMI", "Glucose"]]
```

## Selecting rows

First row:

```python
df.iloc[0]
```

First five rows:

```python
df.iloc[0:5]
```

## Filtering

Patients older than 50:

```python
df[df["Age"] > 50]
```

Multiple conditions:

```python
df[
    (df["Age"] > 50) &
    (df["BMI"] > 30)
]
```

Use:

- `&` for AND;
- `|` for OR.

## Missing values

| Task                        | Command                   |
| --------------------------- | ------------------------- |
| Find nulls                  | `df.isnull()`             |
| Count per column            | `df.isnull().sum()`       |
| Total missing               | `df.isnull().sum().sum()` |
| Remove rows containing null | `df.dropna()`             |
| Fill nulls                  | `df.fillna(...)`          |

For this project, an important verification is:

```python
df.isnull().sum()
```

## Duplicates

Count duplicate rows:

```python
df.duplicated().sum()
```

Inspect duplicates:

```python
df[df.duplicated()]
```

Remove:

```python
df = df.drop_duplicates()
```

Do not remove observations automatically without understanding why.

## Unique values

```python
df["target"].unique()
```

Count each value:

```python
df["target"].value_counts()
```

Proportions:

```python
df["target"].value_counts(normalize=True)
```

This is particularly useful for checking class balance.

## Statistics for one column

| Statistic          | Command              |
| ------------------ | -------------------- |
| Mean               | `df["Age"].mean()`   |
| Median             | `df["Age"].median()` |
| Minimum            | `df["Age"].min()`    |
| Maximum            | `df["Age"].max()`    |
| Standard deviation | `df["Age"].std()`    |
| Number of values   | `df["Age"].count()`  |

## Grouping

Compare average BMI by target:

```python
df.groupby("target")["BMI"].mean()
```

Several variables:

```python
df.groupby("target")[["Age", "BMI", "Glucose"]].mean()
```

This will be useful during EDA.

## Correlation

```python
df.corr(numeric_only=True)
```

Specific columns:

```python
df[["Age", "BMI", "Glucose"]].corr()
```

Remember:

> Correlation indicates association, not causation.

## Sorting

```python
df.sort_values("Age")
```

Descending:

```python
df.sort_values("Age", ascending=False)
```

## Copying a DataFrame

```python
clean_df = df.copy()
```

This is useful when we want to preserve the original dataset while experimenting with preprocessing.

## Very useful project commands

```python
df.shape
df.head()
df.info()
df.describe()
df.isnull().sum()
df.duplicated().sum()
df["target"].value_counts()
df.corr(numeric_only=True)
```

These commands alone answer a large part of the project's **initial data review** requirements.
