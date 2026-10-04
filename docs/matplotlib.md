# Matplotlib — Quick Reference

Matplotlib is the fundamental plotting library used by Python's data-science ecosystem.

Seaborn builds on Matplotlib, so we often use both together.

```python
import matplotlib.pyplot as plt
```

## Basic plot

```python
plt.plot(x, y)
plt.show()
```

## Common plots

| Plot      | Command             | Typical use                    |
| --------- | ------------------- | ------------------------------ |
| Line      | `plt.plot(x, y)`    | Trends                         |
| Scatter   | `plt.scatter(x, y)` | Relationship between variables |
| Histogram | `plt.hist(x)`       | Distribution                   |
| Bar       | `plt.bar(x, y)`     | Category comparison            |

## Histogram

```python
plt.hist(df["Age"])
plt.show()
```

This shows the distribution of patient ages.

## Scatter plot

```python
plt.scatter(df["Age"], df["BMI"])
plt.show()
```

This can help investigate whether two numerical variables appear related.

## Labels

```python
plt.xlabel("Age")
plt.ylabel("BMI")
plt.title("Age vs BMI")
```

## Figure size

```python
plt.figure(figsize=(10, 6))
```

## Complete pattern

```python
plt.figure(figsize=(10, 6))

plt.hist(df["Age"])

plt.title("Distribution of Patient Age")
plt.xlabel("Age")
plt.ylabel("Number of Patients")

plt.show()
```

## Saving figures

```python
plt.savefig(
    "../figures/age_distribution.png",
    bbox_inches="tight"
)
```

Useful figures can then be reused in the report or presentation.

## Important principle

Every final project plot should ideally answer a question.

Don't just produce:

> "Here is a histogram."

Explain:

> "The histogram shows ..., which suggests ..."

The **interpretation** is more important than the plotting syntax.
