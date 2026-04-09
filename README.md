# Git 101 — Practice Repo

> The companion repository for the [Git 101 course](https://fynesforge.dev/git_101/intro) by Fynes Forge.

[![Support me on Ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/tomfynes)

---

<div align="center">

![Status](https://img.shields.io/badge/status-active-63C5EA?style=flat-square&labelColor=404E5C)
![License](https://img.shields.io/badge/license-MIT-9F7EBE?style=flat-square&labelColor=404E5C)
![Org](https://img.shields.io/badge/org-fynes--forge-ECDA90?style=flat-square&labelColor=404E5C)

</div>

---

## How This Repo Works

Unlike a course where you write answers into files, Git is learned by **doing**. This repo gives you a real environment to practise in — branches to switch between, a commit history to inspect, conflicts to resolve, and files to stage, stash, and reset.

> **This repo is your playground. Break things. That's the point.**

---

## Getting Started

### 1. Fork this repo

Click **Fork** in the top-right corner of GitHub. This creates your own personal copy.

### 2. Clone your fork

```bash
git clone git@github.com:<your-username>/git-101.git
cd git-101
```

> **No SSH key yet?** Grade 3 covers exactly this. For now you can clone with HTTPS:
> ```bash
> git clone https://github.com/<your-username>/git-101.git
> ```

### 3. Work through the grades in order

Each grade has its own folder with a `README.md` containing your exercises.

```
grades/
├── grade-1/   ← Start here
├── grade-2/
├── grade-3/
...
└── grade-8/
```

---

## Grades Overview

| Grade | Topic | Key Commands |
|-------|-------|-------------|
| 1 | Getting Started | `git init`, `git clone`, `git config` |
| 2 | Basic Workflow | `git add`, `git commit`, `git log` |
| 3 | Collaborating with GitHub | `git remote`, `git push`, `git pull`, `git fetch` |
| 4 | Branching & Merging | `git branch`, `git checkout`, `git merge` |
| 5 | Inspecting & Comparing | `git diff`, `git revert`, `git reset`, `HEAD` |
| 6 | Advanced Techniques | `git stash`, `git tag`, `git rebase`, `.gitignore` |
| 7 | Troubleshooting & Optimisation | `git clean`, `git prune`, `git gc`, `git fsck` |
| 8 | Real-World Scenarios | Gitflow, pull requests, GitHub Actions, GPG signing |

---

## Pre-built Practice Branches

This repo comes with several branches ready for you to use in the exercises:

| Branch | Purpose |
|--------|---------|
| `main` | The stable base branch |
| `practice/feature-login` | A feature branch to merge into main (Grade 4) |
| `practice/conflict-a` | One side of a merge conflict (Grade 4) |
| `practice/conflict-b` | Other side of a merge conflict (Grade 4) |
| `practice/rebase-me` | A branch to practise rebasing (Grade 6) |
| `practice/stash-demo` | A branch with uncommitted-style work to practise stashing (Grade 6) |

---

## Tips

- Run `git status` constantly — it tells you exactly where you are.
- Run `git log --oneline --graph --all` to visualise the full branch history.
- Made a mess? Every grade's `README.md` has a **Reset** section to get back to a clean state.
- Check `tips/cheatsheet.md` for a quick command reference.

---

## Contributing

See [CONTRIBUTING.md](./CONTRIBUTING.md) for how to report issues or suggest improvements.

