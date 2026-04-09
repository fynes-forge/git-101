# Grade 4 — Branching and Merging

> **Prerequisites:** Grade 3 complete. You can push and pull from GitHub.

---

## What You'll Learn

- How to create and switch branches
- How to merge branches together
- How to resolve merge conflicts
- Branch naming best practices

---

## Pre-built Practice Branches

This repo has branches ready for the exercises below. After forking and cloning, run:

```bash
git fetch origin
git branch -a   # list all branches including remote ones
```

You should see:
- `practice/feature-login` — a finished feature to merge
- `practice/conflict-a` — one side of a conflict
- `practice/conflict-b` — other side of a conflict

---

## Exercises

### Exercise 4.1 — Create a Branch

```bash
# Create and switch to a new branch in one command
git checkout -b my-feature

# Check which branch you're on
git branch
```

> **Tip:** The `*` next to a branch name shows your current branch.

---

### Exercise 4.2 — Make a Commit on Your Branch

```bash
echo "Feature work" >> grades/grade-4/feature.txt
git add grades/grade-4/feature.txt
git commit -m "grade 4: add feature work on branch"

# View the branch graph
git log --oneline --graph --all
```

---

### Exercise 4.3 — Merge a Feature Branch

Merge the pre-built feature branch into main:

```bash
# Switch back to main
git checkout main

# Merge the practice feature branch
git merge practice/feature-login

# Check the result
git log --oneline --graph
```

---

### Exercise 4.4 — Resolve a Merge Conflict

This is the most important skill in this grade. The repo has two branches (`practice/conflict-a` and `practice/conflict-b`) that both edit the same line — merging them will cause a conflict.

```bash
# Start from a clean branch
git checkout -b conflict-practice

# Merge the first side (this will work fine)
git merge practice/conflict-a

# Merge the second side (this will CONFLICT)
git merge practice/conflict-b
```

Git will tell you there's a conflict. Open the conflicting file:

```bash
git status    # shows which files are conflicted
```

Inside the file you'll see conflict markers:

```
<<<<<<< HEAD
This is the version from conflict-a
=======
This is the version from conflict-b
>>>>>>> practice/conflict-b
```

**To resolve:**
1. Edit the file — keep what you want, delete the markers (`<<<<<<<`, `=======`, `>>>>>>>`)
2. Stage the resolved file: `git add <filename>`
3. Complete the merge: `git commit`

> **Tip:** VS Code, IntelliJ, and most editors have built-in merge conflict UI that highlights the markers and gives you one-click "Accept Current / Accept Incoming / Accept Both" buttons.

---

### Exercise 4.5 — Delete a Branch

After merging, clean up:

```bash
# Delete a local branch (safe — only works if already merged)
git branch -d my-feature

# List branches to confirm it's gone
git branch
```

---

### Exercise 4.6 — Branch Naming

Rename your current branch to follow a convention:

```bash
git branch -m conflict-practice grade4/conflict-practice
git branch
```

> **Common naming conventions:**
> - `feature/short-description`
> - `fix/bug-description`
> - `chore/task-description`
> - `grade4/exercise-name` (used in this course)

---

## ✅ Grade 4 Checklist

- [ ] Create a branch with `git checkout -b`
- [ ] Merge a branch with `git merge`
- [ ] Identify a merge conflict from `git status` output
- [ ] Manually resolve a conflict by editing the markers
- [ ] Complete a merge after resolving with `git add` + `git commit`
- [ ] Delete a merged branch with `git branch -d`

---

## Reset

```bash
# Return to main
git checkout main

# Delete any practice branches you created
git branch -d my-feature 2>/dev/null || true
git branch -d conflict-practice 2>/dev/null || true
git branch -d grade4/conflict-practice 2>/dev/null || true

# Restore practice file
git restore grades/grade-4/feature.txt 2>/dev/null || true
```
