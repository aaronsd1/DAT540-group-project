# NumPy — Quick Reference

NumPy provides numerical arrays and mathematical operations.

We will probably use pandas more directly than NumPy, but NumPy appears frequently in machine-learning code and is used internally by pandas and scikit-learn.

```python
import numpy as np
```

## Arrays

Create:

```python
values = np.array([10, 20, 30, 40])
```

| Task                 | Command             |
| -------------------- | ------------------- |
| Create array         | `np.array([...])`   |
| Shape                | `values.shape`      |
| Number of dimensions | `values.ndim`       |
| Mean                 | `np.mean(values)`   |
| Median               | `np.median(values)` |
| Standard deviation   | `np.std(values)`    |
| Minimum              | `np.min(values)`    |
| Maximum              | `np.max(values)`    |

## Indexing

```python
values[0]
```

returns the first value.

```python
values[-1]
```

returns the last.

## Slicing

```python
values[0:3]
```

means:

> Start at index 0 and stop before index 3.

## Vector operations

NumPy can perform operations on entire arrays.

```python
values * 2
```

produces:

```text
[20, 40, 60, 80]
```

Instead of manually looping over every value.

## Useful creation functions

| Command                | Result                  |
| ---------------------- | ----------------------- |
| `np.zeros(5)`          | Five zeros              |
| `np.ones(5)`           | Five ones               |
| `np.arange(5)`         | `0,1,2,3,4`             |
| `np.arange(1, 10)`     | `1` through `9`         |
| `np.linspace(0, 1, 5)` | 5 equally spaced values |

## Missing numerical values

NumPy represents a common missing numerical value as:

```python
np.nan
```

You may encounter `NaN` when inspecting datasets.

## Why learn NumPy?

You don't need to master NumPy before starting this project.

The important thing initially is recognizing:

```python
np.array(...)
np.mean(...)
np.median(...)
np.nan
```

and understanding that scikit-learn often converts pandas data into numerical arrays internally.
