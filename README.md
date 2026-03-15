# Git Commit Messages & Branching Guide

## 1. Writing Commit Messages

A commit message should clearly describe **what change was made and why**.

### Basic Commit
```bash
git commit -m "Modified the Signup functionality"

Amend the Last Commit Message

Use this when you want to modify the previous commit message.

git commit --amend -m "Modified the Login & Signup functionality"

```

### Standard Commit Message Types (Conventional Commits)

Using standard prefixes helps maintain clean commit history and easier collaboration.

Type	Purpose	Example
feat	Adding a new feature	feat: Added Cart functionality
fix	Bug fix	fix: Fixed issue in Add to Cart functionality
docs	Documentation updates	docs: Added technical design document
refactor	Code restructuring without changing functionality	refactor: Improved checkout module structure
test	Adding or updating tests	test: Added unit tests for Cart service
perf	Performance improvements	perf: Optimized product search query
chore	Maintenance tasks	chore: Updated dependencies
style	Code formatting changes	style: Fixed indentation in Cart controller

### Git Branches

Branches allow developers to work on features independently without affecting the main codebase.

Main Branch

main / master

This is the stable production branch.

### List All Branches

git branch

### Create a New Branch

Step 1 – Create Branch

git branch <branch-name>

Create a branch from another branch:

git branch <branch-name> <source-branch>

Example:

git branch feature-cart main

Step 2 – Switch to Branch

git checkout <branch-name>

Example:

git checkout feature-cart

### Create and Switch Branch (Single Command)

git checkout -b <branch-name>

Example:

git checkout -b feature-cart

Create from a specific branch:

git checkout -b <branch-name> <source-branch>

Example:

git checkout -b feature-cart develop


### Modern Way (Recommended)

Git now recommends git switch instead of checkout.

Switch to Existing Branch

git switch <branch-name>

Example:

git switch feature-cart

Create and Switch Branch

git switch -c <branch-name>

Example:

git switch -c feature-cart

Create from another branch:

git switch -c <branch-name> <source-branch>

Example:

git switch -c feature-cart develop

### Best Practice Branch Naming

Common naming conventions:

feature/cart-functionality
bugfix/cart-issue
hotfix/payment-error
release/v1.2

Examples:

feature/user-authentication
bugfix/login-validation
feature/product-search

### Example Git Workflow

git switch main
git pull origin main

git switch -c feature/cart

# Make code changes

git add .
git commit -m "feat: Added Cart functionality"

git push origin feature/cart


Here is a separate Markdown file you can use specifically for Git Cherry-Pick documentation.

File Name

git-cherry-pick.md

# Git Cherry-Pick Guide

## What is Git Cherry-Pick?

`git cherry-pick` allows you to **apply a specific commit from one branch to another branch**.

It is useful when you want to **move only a particular fix or feature** without merging the entire branch.

---

# Basic Syntax

```bash
git cherry-pick <commit-hash>

Example:

git cherry-pick a1b2c3d

This will apply the changes from commit a1b2c3d to the current branch.

⸻

Example Scenario

Suppose you fixed a bug in the develop branch but want the same fix in main.

Step 1 – Switch to target branch

git switch main

Step 2 – Cherry-pick the commit

git cherry-pick <commit-hash>

Example:

git cherry-pick 9f8d7a2

Now the commit from develop will also exist in main.

⸻

Cherry Pick Multiple Commits

git cherry-pick <commit1> <commit2> <commit3>

Example:

git cherry-pick a1b2c3 d4e5f6 g7h8i9


⸻

Cherry Pick a Range of Commits

git cherry-pick <start-commit>..<end-commit>

Example:

git cherry-pick a1b2c3..d4e5f6


⸻

Handling Merge Conflicts

If a conflict occurs during cherry-pick:

Resolve conflicts manually

Then run:

git add .
git cherry-pick --continue


⸻

Abort Cherry Pick

If you want to cancel the cherry-pick operation:

git cherry-pick --abort


⸻

Best Use Cases

Cherry-pick is commonly used for:
	•	Applying hotfixes to production branches
	•	Copying specific commits without merging full branches
	•	Moving small bug fixes between branches

⸻

Example Workflow

git switch main
git cherry-pick 5a3c9b1
git push origin main

This applies the commit from another branch into main.
