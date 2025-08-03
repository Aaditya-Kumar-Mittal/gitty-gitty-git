# Git Workflow Guide - README

## Table of Contents

- [Git Workflow Guide - README](#git-workflow-guide---readme)
  - [Table of Contents](#table-of-contents)
  - [Introduction](#introduction)
  - [Project Setup](#project-setup)
    - [Creating Directories and Files](#creating-directories-and-files)
    - [Initializing Git](#initializing-git)
  - [Working with Git](#working-with-git)
    - [Basic Commands](#basic-commands)
    - [Staging and Committing](#staging-and-committing)
    - [Undoing and Restoring](#undoing-and-restoring)
    - [Working with Stash](#working-with-stash)
  - [Remote Repositories](#remote-repositories)
    - [Adding Origin and Upstream](#adding-origin-and-upstream)
    - [Branching and HEAD](#branching-and-head)
  - [Best Practices for Branches and Pull Requests](#best-practices-for-branches-and-pull-requests)
    - [Example Workflow](#example-workflow)
  - [Syncing Fork with Upstream](#syncing-fork-with-upstream)
    - [Step-by-Step](#step-by-step)
  - [Summary Table](#summary-table)

## Introduction

This guide serves as a comprehensive README for managing a Git-based project from initialization to remote collaboration using branches and pull requests. It is structured for beginner and intermediate users working with both local and remote repositories.

---

## Project Setup

### Creating Directories and Files

```bash
mkdir project
cd project
touch name.txt
```

- Create and enter a project directory.
- Generate a text file for practice.

### Initializing Git

```bash
git init
```

- Initializes a new Git repository in the current folder.

---

## Working with Git

### Basic Commands

```bash
ls        # List files
ls -a     # Show all files including hidden (.git)
ls .git   # View Git's internal files
cat name.txt  # View file content
```

### Staging and Committing

```bash
git status           # Show changes

# Stage changes
  git add .          # Stage everything
  git add name.txt   # Stage specific file

# Commit staged changes
git commit -m "modified: name.txt"

# View commit history
git log
```

### Undoing and Restoring

```bash
git restore --staged name.txt   # Unstage a file
git reset <commit_hash>         # Reset to a specific commit
rm -rf name.txt                 # Force delete a file
```

### Working with Stash

```bash
git stash               # Save uncommitted changes temporarily
git stash pop           # Restore the latest stash
git stash list          # View stashed entries
git stash clear         # Delete all stashes (cannot recover)
```

> ✅ You do **not** need to stage files before using `git stash`. It saves all tracked file changes.

---

## Remote Repositories

### Adding Origin and Upstream

```bash
git remote add origin <your-remote-url>
git remote add upstream <upstream-remote-url>
```

- **Origin** is your personal fork.
- **Upstream** is the main/original repository.

> You can only push to `origin`. For contributing to the main project, create a pull request to `upstream`.

### Branching and HEAD

```bash
git branch            # List branches
git checkout -b feature-x   # Create and switch to new branch
```

- `HEAD` points to the current active branch.
- All new changes are made on the branch `HEAD` points to.

---

## Best Practices for Branches and Pull Requests

- 🔴 **Do not commit directly on main/master**.
- ✅ Create a **new branch for each feature**.
- ✅ One branch = One pull request.
- ✅ Helps with reviewing, testing, and managing failures.

### Example Workflow

```bash
git checkout -b feature-login
# make changes
git add .
git commit -m "Added login functionality"
git push origin feature-login
```

Then go to GitHub and open a pull request from `feature-login` to `upstream/main`.

---

## Syncing Fork with Upstream

### Step-by-Step

```bash
git fetch --all --prune              # Clean and update all remotes

# Sync local main with upstream
  git checkout main
  git reset --hard upstream/main
  git pull upstream main             # Optional if reset not used
  git push origin main               # Push updates to your fork
```

---

## Summary Table

| Task                       | Command                          |
| -------------------------- | -------------------------------- |
| Initialize repo            | `git init`                       |
| Add origin                 | `git remote add origin <url>`    |
| Add upstream               | `git remote add upstream <url>`  |
| Create new branch          | `git checkout -b feature-x`      |
| View branch list           | `git branch`                     |
| View changes               | `git status`                     |
| Stage all changes          | `git add .`                      |
| Commit changes             | `git commit -m "message"`        |
| View commit history        | `git log`                        |
| Unstage file               | `git restore --staged <file>`    |
| Reset to previous commit   | `git reset <commit_hash>`        |
| Force delete file          | `rm -rf <file>`                  |
| Save progress temporarily  | `git stash`                      |
| Restore stash              | `git stash pop`                  |
| Clear all stashes          | `git stash clear`                |
| Fetch all & clean branches | `git fetch --all --prune`        |
| Sync local with upstream   | `git reset --hard upstream/main` |
| Push updates to origin     | `git push origin main`           |

---

This README.md provides a full guide for local Git usage, remote syncing, and collaboration workflow. Perfect for individual or team projects using pull requests.

> **Note:** This guide is a work in progress. Contributions are welcome!
