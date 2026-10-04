# Seaborn — Quick Reference

Seaborn makes statistical visualizations easier to create.

We will use it mainly during Exploratory Data Analysis (EDA).

```python
import seaborn as sns
import matplotlib.pyplot as plt
```

## Useful plots

| Plot         | Command             | Useful for                     |
| ------------ | ------------------- | ------------------------------ |
| Histogram    | `sns.histplot()`    | Distribution                   |
| Boxplot      | `sns.boxplot()`     | Distribution + outliers        |
| Violin plot  | `sns.violinplot()`  | Comparing distributions        |
| Scatter plot | `sns.scatterplot()` | Relationship between variables |
| Count plot   | `sns.countplot()`   | Category counts                |
| Heatmap      | `sns.heatmap()`     | Correlations                   |
| Pair plot    | `sns.pairplot()`    | Several relationships          |

## Histogram

```python
sns.histplot(
    data=df,
    x="Age"
)

plt.show()
```

## Compare groups

```python
sns.histplot(
    data=df,
    x="Age",
    hue="target"
)

plt.show()
```

`hue` separates the observations according to another variable.

This can help compare gallstone and non-gallstone patients.

## Boxplot

```python
sns.boxplot(
    data=df,
    x="target",
    y="BMI"
)

plt.show()
```

This asks approximately:

> Does the BMI distribution differ between the two classes?

## Count plot

```python
sns.countplot(
    data=df,
    x="target"
)

plt.show()
```

Useful for checking the target class distribution.

## Scatter plot

```python
sns.scatterplot(
    data=df,
    x="Age",
    y="BMI",
    hue="target"
)

plt.show()
```

Useful for examining relationships between two numerical variables.

## Correlation heatmap

First calculate correlations:

```python
correlation = df.corr(numeric_only=True)
```

Then visualize them:

```python
sns.heatmap(correlation)

plt.show()
```

For readability:

```python
plt.figure(figsize=(12, 10))

sns.heatmap(
    correlation,
    cmap="coolwarm"
)

plt.show()
```

## Common parameters

| Parameter      | Meaning              |
| -------------- | -------------------- |
| `data=df`      | DataFrame to use     |
| `x="Age"`      | X-axis variable      |
| `y="BMI"`      | Y-axis variable      |
| `hue="target"` | Separate by category |
| `annot=True`   | Display values       |
| `cmap=...`     | Color mapping        |

## The general Seaborn pattern

Most Seaborn code looks approximately like:

```python
sns.some_plot(
    data=df,
    x="some_column",
    y="another_column",
    hue="target"
)

plt.show()
```

Don't try to memorize every plotting function.

Learn how to read this general structure and consult the documentation when you need a particular visualization.
