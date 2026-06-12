---
title: Your First Commit
type: challenge
---

# Challenge: Your First Commit

Time to put it together. Create a brand-new repository and make your first
commit in it.

## Your task

1. Make a new folder and turn it into a Git repository:
   ```bash
   mkdir hello-git
   cd hello-git
   git init
   ```
2. Create a file called `README.md` with a line of text in it.
3. **Stage** the file.
4. **Commit** it with the message `Initial commit`.
5. Run `git log --oneline` and confirm you see your commit.

## Success looks like

```bash
$ git log --oneline
a1b2c3d Initial commit
```

## Hints

- Forgot how to stage? Revisit *Making Commits*.
- `git status` is your friend — run it between steps to see what Git thinks is
  happening.
- On a fresh install, Git may ask you to set your name and email first:
  ```bash
  git config --global user.name "Your Name"
  git config --global user.email "you@example.com"
  ```

When your `git log` shows the commit, you've completed the challenge — mark it
complete to finish the path. 
