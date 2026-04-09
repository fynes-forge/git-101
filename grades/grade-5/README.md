# Grade 5 — Inspecting and Comparing Changes

> **Prerequisites:** Grade 4 complete. You're comfortable with branches and merging.

---

## What You'll Learn

- How to compare changes with `git diff`
- What `HEAD` is and how to navigate with it
- How to safely undo commits with `git revert`
- How to unstage or reset changes with `git reset`

---

## Exercises

### Exercise 5.1 — Git Diff: Working Directory Changes

Make a change and inspect it before staging:

```bash
echo "Inspecting changes" >> grades/grade-5/practice.txt

# Compare working directory to last commit
git diff
```

> `git diff` with no arguments shows **unstaged** changes. Once staged, those changes no longer show here.

---

### Exercise 5.2 — Git Diff: Staged Changes

```bash
git add grades/grade-5/practice.txt

# Now diff shows nothing (changes are staged, not unstaged)
git diff

# To see staged changes vs last commit:
git diff --staged
```

---

### Exercise 5.3 — Compare Two Branches

```bash
# See what's different between main and a practice branch
git diff main practice/feature-login

# Just see which files differ (not the full diff)
git diff --name-only main practice/feature-login
```

---

### Exercise 5.4 — Understand HEAD

```bash
# HEAD points to your current position
cat .git/HEAD

# See the commit HEAD points to
git log -1 HEAD --oneline

# HEAD~1 means "one commit before HEAD"
git log -3 --oneline          # look at last 3 commits
git show HEAD~1               # inspect the commit before HEAD
```

---

### Exercise 5.5 — Navigate with Checkout

```bash
# Get the hash of an older commit from your log
git log --oneline

# Detach HEAD and go back in time (replace abc1234 with a real hash)
git checkout abc1234

git log --oneline    # you're now in the past
git status           # notice "HEAD detached at..."

# Come back to main
git checkout main
```

> **Detached HEAD** means HEAD points directly to a commit, not a branch. It's safe for looking around — just don't make commits here without creating a branch first.

---

### Exercise 5.6 — Undo a Commit Safely with Git Revert

`git revert` creates a **new commit** that undoes a previous one. The history is preserved — safe for shared branches.

```bash
# Make a commit to undo
echo "I will regret this" >> grades/grade-5/practice.txt
git add grades/grade-5/practice.txt
git commit -m "grade 5: commit to be reverted"

git log --oneline   # note the hash of this commit

# Revert it (creates a new "undo" commit)
git revert HEAD

git log --oneline   # the original commit is still there, but undone
```

---

### Exercise 5.7 — Unstage and Reset with Git Reset

> ⚠️ `git reset` rewrites history. **Never use it on commits that have been pushed to a shared branch.**

```bash
# Make two commits
echo "First" >> grades/grade-5/practice.txt && git add . && git commit -m "first"
echo "Second" >> grades/grade-5/practice.txt && git add . && git commit -m "second"

git log --oneline

# Soft reset: undo the last commit, keep changes staged
git reset --soft HEAD~1
git status    # changes are staged, ready to re-commit

# Mixed reset (default): undo the last commit, unstage changes
git reset HEAD~1
git status    # changes are in working directory

# Hard reset: undo the last commit AND discard changes
git reset --hard HEAD~1
git status    # working directory is clean
```

| Flag | Commit undone? | Staged changes | Working dir changes |
|------|---------------|----------------|-------------------|
| `--soft` | ✅ | Kept staged | Kept |
| `--mixed` (default) | ✅ | Unstaged | Kept |
| `--hard` | ✅ | Discarded | Discarded |

---

## ✅ Grade 5 Checklist

- [ ] Use `git diff` to view unstaged changes
- [ ] Use `git diff --staged` to view staged changes
- [ ] Compare two branches with `git diff branch-a branch-b`
- [ ] Explain what `HEAD` and `HEAD~1` mean
- [ ] Navigate to a past commit and return with `git checkout`
- [ ] Undo a commit safely with `git revert`
- [ ] Explain the difference between `--soft`, `--mixed`, and `--hard` reset

---

## Reset

```bash
git restore grades/grade-5/practice.txt
```

If you've made commits you want to clean up:

```bash
git reset --hard origin/main
```
