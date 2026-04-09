# Grade 2 — Basic Git Workflow

> **Prerequisites:** Grade 1 complete. You have Git installed and configured.

---

## What You'll Learn

- The three areas of Git: Working Directory, Staging Area, and Repository
- How to stage files with `git add`
- How to commit changes with `git commit`
- How to view history with `git log`

---

## The Three Areas

```
Working Directory  →  Staging Area  →  Repository
   (edit files)       (git add)        (git commit)
```

- **Working Directory** — where you edit files normally
- **Staging Area** — a "draft" of your next commit; you choose exactly what goes in
- **Repository** — the permanent, versioned history stored in `.git/`

---

## Exercises

### Exercise 2.1 — Check the Status

Always start by checking where you are:

```bash
git status
```

> `git status` is your most used command. Run it before and after everything.

---

### Exercise 2.2 — Edit a File and Stage It

This repo has a file ready for you to practise with:

```bash
# Open the practice file and add a line of text
echo "My first change" >> grades/grade-2/practice.txt

# Check what changed
git status

# Stage the file
git add grades/grade-2/practice.txt

# Check status again — notice the difference
git status
```

> **Tip:** `git add .` stages *all* changed files at once. Use it carefully — it's easy to accidentally stage files you didn't mean to.

---

### Exercise 2.3 — Commit Your Change

```bash
git commit -m "grade 2: add first practice change"
```

Check the result:

```bash
git status
git log --oneline
```

> **Good commit messages** are short (under 72 chars), use the imperative mood ("add", "fix", "update"), and describe *what* changed and *why* — not *how*.

---

### Exercise 2.4 — Stage Only Part of a File

Make two separate changes to `practice.txt`, then stage only one:

```bash
echo "Change A" >> grades/grade-2/practice.txt
echo "Change B" >> grades/grade-2/practice.txt

# Stage interactively — choose which changes to include
git add -p grades/grade-2/practice.txt
```

> `-p` (patch mode) lets you review each chunk and decide `y` (yes) or `n` (no). This is how professionals stage precise, clean commits.

---

### Exercise 2.5 — Explore Git Log

```bash
# Short one-line view
git log --oneline

# Full detail
git log

# Show changes introduced by each commit
git log -p --oneline
```

> Press `q` to exit the log viewer.

---

### Exercise 2.6 — Unstage a File

Stage a file, then change your mind and unstage it:

```bash
echo "Accidental change" >> grades/grade-2/practice.txt
git add grades/grade-2/practice.txt
git status

# Unstage it (the file change is kept, just removed from staging)
git restore --staged grades/grade-2/practice.txt
git status
```

---

## ✅ Grade 2 Checklist

- [ ] Explain the difference between Working Directory, Staging Area, and Repository
- [ ] Stage a specific file with `git add <file>`
- [ ] Stage changes interactively with `git add -p`
- [ ] Commit with a clear message using `git commit -m`
- [ ] View history with `git log --oneline`
- [ ] Unstage a file with `git restore --staged`

---

## Reset

To get `practice.txt` back to its original state:

```bash
git restore grades/grade-2/practice.txt
```

To undo your practice commits (keeps the file changes):

```bash
git reset HEAD~1
```
