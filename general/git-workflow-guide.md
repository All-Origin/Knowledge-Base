

### 📘 `git-workflow-guide.md` – Junior Git Workflow & Push Guide

````md
# 🚀 Junior Git Workflow & Branching Guide

This document provides best practices and tips for working with Git in the Junior organization — especially across teams like Java Backend, LLM Core, DevOps, and Frontend.

---

## 🔱 Branch Naming Convention

| Type | Prefix | Example |
|------|--------|---------|
| Feature | `feat/` | `feat/auth-oauth2` |
| Fix | `fix/` | `fix/login-null-crash` |
| Docs | `docs/` | `docs/update-readme` |
| Refactor | `refactor/` | `refactor/token-refresh-flow` |
| Test | `test/` | `test/unit-auth` |
| Chore | `chore/` | `chore/remove-logs` |

---

## 🔁 Local Branch Creation

```bash
# Create and switch to new branch
git checkout -b feat/add-oauth-support
````

---

## 📤 First Time Push of a New Branch

```bash
# Push your local branch and set it to track the same remote branch
git push --set-upstream origin feat/add-oauth-support
```

After that, you can just use:

```bash
git push   # To push changes
git pull   # To pull latest changes
```

---

## ⚠️ Common Push Errors & Fixes

### 1. `fatal: no upstream branch`

You tried pushing a branch that’s not tracking a remote. Use:

```bash
git push --set-upstream origin your-branch-name
```

---

### 2. `fatal: current branch does not match remote`

Git is unsure whether to push to `main` or same-named branch. Choose:

```bash
# Push to same branch name on remote
git push origin HEAD

# OR push to a specific branch like main (be careful!)
git push origin HEAD:main
```

---

## 🔐 Avoid Accidental Push to `main`

> ✅ Only maintainers/admins should push directly to `main`.

Use GitHub’s **branch protection rules**:

* Require pull requests
* Require code reviews
* Allow only selected people to merge
* Disallow direct push to `main`

---

## 🧹 Cleaning Up

### Delete a local branch after merging:

```bash
git branch -d branch-name
```

### Delete a remote branch:

```bash
git push origin --delete branch-name
```

---

## 🧪 Git Checkpoints

```bash
git status             # What has changed?
git log                # What commits were made?
git branch -vv         # What are you tracking?
git remote -v          # Check remote URL
```

---

## 🌐 Set Remote URL

```bash
# If remote not set
git remote add origin https://github.com/All-Origin/YourRepoName.git
```

---

## ✅ Commit Messages Format

```bash
type(scope): short description

# Example:
feat(auth): add Google OAuth login support
fix(otp): handle resend timeout bug
docs(readme): update setup section
```

---

## 🧠 Summary

| Command                                        | Description                                     |
| ---------------------------------------------- | ----------------------------------------------- |
| `git push --set-upstream origin <branch>`      | Push + track remote                             |
| `git push origin HEAD`                         | Push to same name on remote                     |
| `git push origin HEAD:main`                    | Push current branch into main (not recommended) |
| `git branch --set-upstream-to=origin/<branch>` | Set upstream for existing branch                |
| `git remote -v`                                | See remotes                                     |
| `git status`                                   | See current repo state                          |

---

### ✨ work responsibly, push mindfully, and code confidently.

*– Junior Ai Engineering Team*



