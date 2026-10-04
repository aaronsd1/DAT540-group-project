# DAT540 — Gallstone Disease Classification

DAT540 group project using machine learning to classify patients with and without gallstone disease and investigate which clinical characteristics contribute most to the predictions.

## Quick Start

### 1. Clone the repository

```bash
git clone <repository-url>
cd DAT540-group-project
```

### 2. Create a virtual environment

```bash
python -m venv .venv
```

Activate it:

**Windows PowerShell**

```powershell
.venv\Scripts\Activate.ps1
```

**macOS/Linux**

```bash
source .venv/bin/activate
```

### 3. Install everything

```bash
python -m pip install -r requirements.txt
```

### 4. Start JupyterLab

```bash
python -m jupyterlab
```

Open the project notebook and select the Python kernel belonging to `.venv`.

## Project Objectives

1. Develop a machine-learning model that distinguishes patients with and without gallstone disease.
2. Investigate which clinical characteristics contribute most to the model's predictions.

## Research Question

> How accurately can machine-learning models classify gallstone disease using demographic, body-composition and laboratory measurements, and which clinical characteristics contribute most strongly to their predictions?

## Main Models

We will initially compare:

- Logistic Regression
- Decision Tree
- Random Forest

The goal is not to build the most complicated model possible. We should be able to understand, explain and defend every important part of the final solution.

## Documentation

- `docs/PROJECT_OVERVIEW.md` — project phases, ML concepts, models and timeline.
- `docs/SETUP.md` — development environment and required tools.
- `docs/GITHUB.md` — Git/GitHub workflow for the group.

## Basic Git Workflow

Before starting a task:

```bash
git checkout main
git pull
git checkout -b feature/task-name
```

After making changes:

```bash
git status
git add .
git commit -m "Describe the change"
git push -u origin feature/task-name
```

Then create a Pull Request on GitHub and have another group member review it before merging.

**Do not work directly on `main`.**
