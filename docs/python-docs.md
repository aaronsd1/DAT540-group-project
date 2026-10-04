# Python Basics — Quick Reference

This is not intended to teach all of Python. It contains the basic syntax we are likely to encounter while working on the DAT540 project.

## Variables and basic values

Python does not require us to explicitly specify the type of a variable.

| Task            | Syntax           | Example                |
| --------------- | ---------------- | ---------------------- |
| Create integer  | `name = value`   | `age = 45`             |
| Create decimal  | `name = value`   | `bmi = 27.5`           |
| Create string   | `name = "text"`  | `name = "Patient A"`   |
| Boolean         | `True` / `False` | `has_gallstone = True` |
| Print something | `print(...)`     | `print(age)`           |
| Check type      | `type(...)`      | `type(age)`            |

```python
age = 45
bmi = 27.5
has_gallstone = True

print(age)
print(type(bmi))
```

## Lists

A list stores multiple values.

| Task            | Syntax               |
| --------------- | -------------------- |
| Create          | `values = [1, 2, 3]` |
| First item      | `values[0]`          |
| Last item       | `values[-1]`         |
| Add item        | `values.append(4)`   |
| Number of items | `len(values)`        |
| Slice           | `values[0:2]`        |

```python
models = [
    "Logistic Regression",
    "Decision Tree",
    "Random Forest"
]

print(models[0])
print(len(models))
```

Remember: Python starts counting at **0**.

## Dictionaries

A dictionary stores `key: value` pairs.

```python
patient = {
    "age": 52,
    "bmi": 28.4,
    "gallstone": True
}
```

Access a value:

```python
patient["age"]
```

Dictionaries appear frequently when configuring machine-learning models and storing results.

## Conditions

```python
if bmi > 30:
    print("BMI above 30")
else:
    print("BMI 30 or below")
```

Comparison operators:

| Meaning       | Python |
| ------------- | ------ |
| Equal         | `==`   |
| Not equal     | `!=`   |
| Greater than  | `>`    |
| Less than     | `<`    |
| Greater/equal | `>=`   |
| Less/equal    | `<=`   |
| AND           | `and`  |
| OR            | `or`   |
| NOT           | `not`  |

Note the difference:

```python
x = 5
```

means **assign 5 to x**.

```python
x == 5
```

means **is x equal to 5?**

## Loops

A `for` loop repeats something.

```python
models = ["Logistic", "Tree", "Forest"]

for model in models:
    print(model)
```

Indentation is significant in Python.

Correct:

```python
for model in models:
    print(model)
```

Incorrect:

```python
for model in models:
print(model)
```

## Functions

Functions allow reusable pieces of logic to be given a name.

```python
def calculate_difference(actual, predicted):
    return actual - predicted
```

Use it:

```python
difference = calculate_difference(10, 8)

print(difference)
```

Machine-learning libraries make extensive use of functions and methods.

## Importing libraries

Whole library:

```python
import pandas
```

With an alias:

```python
import pandas as pd
import numpy as np
```

Import a specific component:

```python
from sklearn.linear_model import LogisticRegression
```

## Methods

A method is a function belonging to an object.

For example:

```python
df.head()
```

Here:

- `df` is an object;
- `head` is a method;
- `()` calls the method.

This pattern appears everywhere:

```python
df.head()
df.describe()
model.fit(...)
model.predict(...)
```

## Comments

```python
# This is a comment
```

Use comments to explain **why** something is being done when the reason is not obvious.

## Useful built-ins

| Function       | Purpose            |
| -------------- | ------------------ |
| `print(x)`     | Display value      |
| `type(x)`      | Find type          |
| `len(x)`       | Number of elements |
| `range(n)`     | Generate sequence  |
| `min(x)`       | Minimum            |
| `max(x)`       | Maximum            |
| `sum(x)`       | Sum                |
| `round(x, 2)`  | Round number       |
| `enumerate(x)` | Loop with index    |

## Important beginner pattern

When you encounter:

```python
model.fit(X_train, y_train)
```

read it approximately as:

> "Call the `fit` method belonging to `model`, and give it `X_train` and `y_train`."

Understanding `object.method(arguments)` will make a large amount of Python data-science code easier to read.
