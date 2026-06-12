---
title: Making Commits
type: lesson
---

# Making Commits

A **commit** is a snapshot of your project. Creating one is a two-step process:
first you choose *what* to save, then you save it with a message.

## 1. Stage your changes

`git add` moves changes into the **staging area** — a list of what will go into
the next commit:

```bash
git add index.html        # stage one file
git add .                 # stage everything you changed
```

## 2. Commit them

`git commit` saves the staged changes as a permanent snapshot. The `-m` flag
attaches a short message:

```bash
git commit -m "Fix the broken navigation link"
```

## Writing good messages

A commit message should finish the sentence *"This commit will…"*:

- ✅ `Add dark mode toggle to settings`
- ❌ `stuff` / `asdf` / `final fixes (for real this time)`

## Checking your work

`git status` shows what's staged, changed, or untracked, and `git log` shows the
history of commits:

```bash
git status
git log --oneline
```

Now it's your turn — the next node is a hands-on challenge.
