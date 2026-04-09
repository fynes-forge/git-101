# Grade 6 — Advanced Git Techniques

> **Prerequisites:** Grade 5 complete. You understand HEAD, diff, and reset.

---

## What You'll Learn

- How to save work-in-progress with `git stash`
- How to tag releases
- How to apply specific commits with `git cherry-pick`
- How to rewrite history cleanly with `git rebase`
- How to ignore files with `.gitignore`

---

## Exercises

### Exercise 6.1 — Git Stash: Save Your Work in Progress

You're mid-way through a change when you need to switch branches urgently.

```bash
# Start some work you're not ready to commit
echo "Half-finished idea" >> grades/grade-6/practice.txt
git status    # shows modified file

# Stash it away (working directory becomes clean)
git stash
git status    # clean

# Switch to another branch, do some work, come back...
git checkout practice/feature-login
git checkout main

# Retrieve your stashed work
git stash pop
git status    # your change is back
```

---

### Exercise 6.2 — Managing Multiple Stashes

```bash
echo "Stash entry one" >> grades/grade-6/practice.txt
git stash save "wip: first idea"

echo "Stash entry two" >> grades/grade-6/practice.txt
git stash save "wip: second idea"

# List all stashes
git stash list

# Apply a specific stash (without removing it)
git stash apply stash@{1}

# Drop a stash entry
git stash drop stash@{0}

# Apply and remove in one step
git stash pop
```

---

### Exercise 6.3 — Git Tag: Mark a Release

```bash
# Lightweight tag (just a name)
git tag v0.1

# Annotated tag (recommended — includes message, author, date)
git tag -a v1.0.0 -m "Release version 1.0.0"

# List tags
git tag

# View tag details
git show v1.0.0

# Push tags to remote (tags are NOT pushed by default)
git push origin v1.0.0
git push origin --tags    # push all tags at once
```

---

### Exercise 6.4 — Git Cherry-Pick: Apply One Specific Commit

Find a commit hash from the `practice/feature-login` branch and apply just that one commit to your current branch:

```bash
# See commits on the practice branch
git log practice/feature-login --oneline

# Copy a commit hash (e.g. abc1234) and apply it to your current branch
git cherry-pick abc1234

git log --oneline    # the commit now appears on your branch
```

> **When to use it:** Hotfixes — a bug fix committed on a feature branch needs to go to `main` without merging the entire feature.

---

### Exercise 6.5 — Git Rebase: Rewrite History Cleanly

The `practice/rebase-me` branch has commits that branch off an old version of main. Rebase them onto the current main:

```bash
git checkout practice/rebase-me
git log --oneline --graph --all    # see how it diverges

# Rebase onto main
git rebase main

git log --oneline --graph --all    # now it's linear
```

> **Rebase vs Merge:**
> - `merge` preserves history exactly, creates a merge commit
> - `rebase` rewrites commits to sit on top of the target — cleaner history, but rewrites SHAs
> - **Never rebase commits already pushed to a shared branch**

---

### Exercise 6.6 — .gitignore

This repo has a `.gitignore`. Inspect it and then add your own rules:

```bash
cat .gitignore

# Create a file that should be ignored
echo "my secret" > grades/grade-6/secret.env

git status    # it should NOT appear if the rule is set correctly

# If it does appear, add the rule:
echo "*.env" >> .gitignore
git status    # now it's ignored
```

> **Tip:** Use [gitignore.io](https://www.toptal.com/developers/gitignore) to generate `.gitignore` files for your language and OS.

---

## ✅ Grade 6 Checklist

- [ ] Stash changes and restore them with `git stash` / `git stash pop`
- [ ] List and manage multiple stashes
- [ ] Create an annotated tag with `git tag -a`
- [ ] Push tags to a remote
- [ ] Apply a specific commit with `git cherry-pick`
- [ ] Rebase a branch onto main with `git rebase`
- [ ] Add rules to `.gitignore` and verify files are ignored

---

## Reset

```bash
git restore grades/grade-6/practice.txt
git stash clear
git tag -d v0.1 v1.0.0 2>/dev/null || true
rm -f grades/grade-6/secret.env
```
