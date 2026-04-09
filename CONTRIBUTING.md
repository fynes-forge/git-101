# Contributing to Git 101

Thank you for helping improve this course! Contributions of all sizes are welcome — from fixing a typo to suggesting a new exercise.

---

## Ways to Contribute

- 🐛 **Bug report** — a command doesn't work, output doesn't match, or a step is missing
- ✏️ **Wording fix** — something is unclear or incorrectly explained
- 💡 **Exercise suggestion** — a good hands-on task for a grade
- 🖥️ **OS / platform note** — a command behaves differently on Windows, macOS, or Linux
- 📄 **Docs improvement** — README, cheatsheet, or setup clarifications

---

## Before You Start

1. **Check existing issues** — your bug or idea may already be logged.
2. **One change per PR** — keeps reviews focused and fast.
3. **Test your commands** — run any Git commands you add before submitting.

---

## How to Contribute

### 1. Fork & Clone

```bash
git clone https://github.com/<your-username>/git-101.git
cd git-101
```

### 2. Create a Branch

```bash
git checkout -b fix/grade4-conflict-instructions
git checkout -b feat/grade6-new-rebase-exercise
git checkout -b docs/add-windows-note-grade1
```

### 3. Make Your Changes

- **Grade exercises** live in `grades/grade-X/README.md`
- **Practice files** live in `grades/grade-X/practice.txt` (keep them simple)
- **Cheatsheet** lives in `tips/cheatsheet.md`
- **CI workflow** lives in `.github/workflows/ci.yml`

### 4. Commit with a Clear Message

```bash
git commit -m "fix: correct git reset flag table in grade 5"
git commit -m "feat: add interactive rebase exercise to grade 6"
git commit -m "docs: add Windows path note to grade 1 config step"
```

### 5. Push & Open a PR

```bash
git push origin your-branch-name
```

Open a Pull Request on GitHub and fill in the PR template.

---

## Exercise Contribution Guidelines

When adding or editing exercises, follow the existing style:

- **Use a numbered heading** (`### Exercise X.Y — Short Title`)
- **Show the exact commands** in fenced code blocks with `bash` syntax highlighting
- **Explain the output** students should expect with a `> **Expected:**` or `> **Tip:**` blockquote
- **Include a Reset section** if the exercise leaves behind files or branches
- **Keep it focused** — each exercise should cover one concept clearly

---

## Platform Notes

Git behaves slightly differently across operating systems. If you're adding a platform-specific note, format it like this:

> **Windows note:** On Windows, use `Get-Content .git/HEAD` instead of `cat .git/HEAD`.

---

## Reporting Issues

Use the issue templates:
- **Bug report** — command errors, wrong output, broken steps
- **Exercise suggestion** — new practice tasks
- **Documentation** — typos, unclear wording, missing context

---

## Code of Conduct

Be constructive and kind. This course welcomes learners at all levels — feedback should help people improve, not discourage them.
