# GitHub Guide for the DAT540 Group Project

## What is GitHub?

GitHub is a platform for hosting and collaborating on **Git repositories**.

Git is a version control system that tracks changes to our code. GitHub stores a shared copy of the repository remotely and gives us tools for collaborating on it.

For the purposes of this project, all you really need to know is that GitHub allows multiple people to work on the same project without constantly overwriting each other's code.

If two people modify the same parts of the same file, Git may not know which version to keep. This results in a **merge conflict**. Merge conflicts have to be manually resolved and can be a pain in the ass.

To reduce the chance of this happening, we use the **Projects** tab on GitHub to create, assign, and track tasks. Before starting something, check the project board and assign the relevant task to yourself.

---

## The basic idea

Each group member has their own **local copy** of the project on their computer.

We also have a **shared copy** of the project on GitHub.

The `main` branch on GitHub should contain the current working version of the project. Instead of making changes directly to `main`, we create separate branches for our tasks.

For example:

- `main` → working version of the project
- `feature/data-cleaning` → someone working on data cleaning
- `feature/visualization` → someone working on visualization

When your work is finished, you create a **Pull Request (PR)** asking for your branch to be reviewed and merged into `main`.

---

## Initial setup

You only need to do this once.

First, open a terminal in the directory where you want the project to be stored and clone the repository:

```bash
git clone https://github.com/YOUR-USERNAME/DAT540-group-project.git
```

Then enter the project directory:

```bash
cd DAT540-group-project
```

You now have a local copy of the repository on your computer.

You **do not** need to run `git init` because cloning the repository already sets everything up and connects your local repository to GitHub.

---

## Starting a new task

### 1. Assign yourself a task

Go to the **Projects** tab on GitHub and choose a task to work on.

Assign the task to yourself and move it to **In Progress**.

This helps everyone see what is currently being worked on.

### 2. Make sure you have the newest code

Before starting a new task, switch back to the `main` branch:

```bash
git checkout main
```

Then download the newest changes:

```bash
git pull
```

This is important because someone else may have added code since the last time you worked on the project.

### 3. Create a branch for your task

Do **not** make your changes directly on `main`.

Instead, create a new branch:

```bash
git checkout -b feature/branch-name
```

For example:

```bash
git checkout -b feature/data-cleaning
```

or:

```bash
git checkout -b feature/pandas-setup
```

This creates a new branch and automatically switches you to it.

Think of a branch as an isolated version of the project where you are free to make changes without immediately affecting the main version.

---

## Working on your task

Implement your changes normally and test them locally.

You can check which files you have modified at any time with:

```bash
git status
```

Once you are happy with your changes, you need to **stage**, **commit**, and **push** them.

### 1. Stage your changes

To stage every modified file:

```bash
git add .
```

Or, if you only want to stage specific files:

```bash
git add filename1 filename2
```

Staging basically means:

> "I want these changes to be included in my next commit."

You can run:

```bash
git status
```

again to verify that you staged the correct files.

### 2. Commit your changes

Create a commit:

```bash
git commit -m "Your commit message"
```

For example:

```bash
git commit -m "Implement initial pandas setup"
```

A commit saves a snapshot of your staged changes **locally**.

Try to use a short message that actually explains what you changed.

Good:

```bash
git commit -m "Add CSV loading functionality"
```

Not very useful:

```bash
git commit -m "stuff"
```

### 3. Push your branch to GitHub

The first time you push a new branch, use:

```bash
git push -u origin feature/branch-name
```

For example:

```bash
git push -u origin feature/data-cleaning
```

The `-u` connects your local branch with the corresponding branch on GitHub.

After doing this once for the branch, future pushes can simply use:

```bash
git push
```

Your code is now on GitHub, but it is still on your **separate branch**. It has **not** been added to `main` yet.

This is intentional. If something is broken or you accidentally added the wrong files, the main version of the project is still unaffected.

---

## Creating a Pull Request

After pushing your branch, go to the GitHub repository.

GitHub will usually show a yellow notification saying that a recently pushed branch has changes and give you a **Compare & pull request** button.

Click it.

Write a short description of:

- What you changed
- Anything the reviewer should know
- How you tested it, if relevant

Then create the Pull Request.

At this point, send the PR to someone else in the group and ask them to review it.

---

## Reviewing and merging

The reviewer should look through the changes and make sure nothing obviously breaks the project.

If something needs to be changed, they can leave comments on the Pull Request.

You can then make the requested changes locally, commit them, and run:

```bash
git push
```

The Pull Request will automatically update with your new commits.

Once the reviewer is happy with the changes, they should **approve the Pull Request on GitHub**.

The branch can then be merged into `main`.

`main` should therefore act as our **source of truth** — the current shared version of the project.

After merging, the feature branch can normally be deleted from GitHub.

---

## Starting your next task

Before starting another task, return to `main`:

```bash
git checkout main
```

Then get the changes that have been merged since you last updated:

```bash
git pull
```

Then create another branch:

```bash
git checkout -b feature/new-task
```

And repeat the process.

The general workflow is therefore:

**Assign task → Pull latest `main` → Create branch → Code → Test → Add → Commit → Push → Pull Request → Review → Merge**

---

## Commands you'll use most often

| Command                          | What it does                                           |
| -------------------------------- | ------------------------------------------------------ |
| `git status`                     | Shows your current branch and which files have changed |
| `git checkout main`              | Switches to the `main` branch                          |
| `git pull`                       | Downloads the latest changes from GitHub               |
| `git checkout -b feature/name`   | Creates a new branch and switches to it                |
| `git add .`                      | Stages all changed files                               |
| `git add filename`               | Stages a specific file                                 |
| `git commit -m "message"`        | Creates a local commit containing your staged changes  |
| `git push`                       | Uploads your commits to GitHub                         |
| `git push -u origin branch-name` | Uploads a new branch to GitHub for the first time      |

---

## Important rules

1. **Don't work directly on `main`.** Create a branch for your task.

2. **Pull before starting a new task.** This makes sure your branch starts from the newest version of the project.

3. **Check the project board before starting something.** Don't accidentally work on something another person is already doing.

4. **Use `git status` if you're unsure.** It is one of the safest and most useful Git commands.

5. **Don't merge your code without review.** Have at least one other group member look at the Pull Request first.

6. **Don't panic if you mess something up.** Git is specifically designed to keep a history of changes. If you're unsure what a Git command will do, ask someone before running random commands from Stack Overflow and accidentally making the situation worse.
