# Grade 7 — Troubleshooting and Optimisation

> **Prerequisites:** Grade 6 complete. You're comfortable with advanced Git techniques.

---

## What You'll Learn

- How to resolve complex merge conflicts with `git mergetool`
- How to clean up untracked files with `git clean`
- How to prune stale remote references with `git prune`
- How to compress and verify your repository with `git gc` and `git fsck`

---

## Exercises

### Exercise 7.1 — Advanced Merge Conflicts

Conflicts in binary files or many files at once require a methodical approach.

```bash
# Simulate a multi-file conflict
git checkout -b grade7/conflict-practice

echo "Team A version" > grades/grade-7/config-a.txt
git add . && git commit -m "grade 7: team A changes"

git checkout main
echo "Team B version" > grades/grade-7/config-a.txt
git add . && git commit -m "grade 7: team B changes"

# Now merge — expect a conflict
git merge grade7/conflict-practice
```

When you have multiple conflicted files, triage them:

```bash
git status              # lists all conflicted files
git diff --name-only --diff-filter=U   # another way to list only unresolved
```

Resolve each file, then:

```bash
git add grades/grade-7/config-a.txt
git commit
```

---

### Exercise 7.2 — Git Mergetool

Configure a merge tool (VS Code shown here — adjust for your editor):

```bash
git config --global merge.tool vscode
git config --global mergetool.vscode.cmd 'code --wait $MERGED'

# During a conflict, launch the tool
git mergetool
```

> Other popular tools: `vimdiff`, `meld`, `kdiff3`, `IntelliJ IDEA`

---

### Exercise 7.3 — Git Clean: Remove Untracked Files

```bash
# Create some untracked mess
echo "junk" > grades/grade-7/junk1.txt
echo "more junk" > grades/grade-7/junk2.txt
mkdir grades/grade-7/temp-dir

git status    # shows untracked files

# Preview what would be deleted (dry run — nothing is deleted yet)
git clean -n

# Delete untracked files
git clean -f

# Delete untracked files AND untracked directories
git clean -fd

git status    # clean
```

> ⚠️ `git clean` is **permanent** — there's no undo. Always run `-n` first.

---

### Exercise 7.4 — Git Prune: Clean Up Stale Remote References

Over time, remote branches that have been deleted still appear in your local list:

```bash
# See all remote-tracking branches
git branch -r

# Remove references to remote branches that no longer exist
git remote prune origin

# Or combine with fetch
git fetch --prune origin
```

> Set this automatically: `git config --global fetch.prune true`

---

### Exercise 7.5 — Git GC: Compress the Repository

```bash
# Run garbage collection manually (Git does this automatically too)
git gc

# More aggressive version (for very large repos)
git gc --aggressive
```

> `git gc` packs loose objects, removes dangling commits, and compresses the repo. You'll rarely need to run this manually — Git triggers it automatically.

---

### Exercise 7.6 — Git Fsck: Verify Repository Integrity

```bash
# Check for corrupt or dangling objects
git fsck

# Show only dangling commits (useful for recovering "lost" work)
git fsck --lost-found
```

> If you accidentally dropped a stash or reset --hard past something important, `git fsck --lost-found` can sometimes recover it. Objects appear in `.git/lost-found/`.

---

## ✅ Grade 7 Checklist

- [ ] Identify all conflicted files during a merge using `git status`
- [ ] Configure and use `git mergetool`
- [ ] Use `git clean -n` (dry run) before `git clean -f`
- [ ] Prune stale remote references with `git remote prune origin`
- [ ] Run `git gc` and explain what it does
- [ ] Use `git fsck` to check repo integrity

---

## Reset

```bash
git checkout main
git branch -d grade7/conflict-practice 2>/dev/null || true
git restore grades/grade-7/ 2>/dev/null || true
git clean -fd grades/grade-7/
```
