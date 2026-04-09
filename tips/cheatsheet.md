# Git 101 — Command Cheatsheet

A quick reference to keep open while working through the exercises.

---

## Setup

| Command | What it does |
|---------|-------------|
| `git config --global user.name "Name"` | Set your name |
| `git config --global user.email "you@example.com"` | Set your email |
| `git config --list` | View all config |
| `git init` | Initialise a new repo |
| `git clone <url>` | Clone a remote repo |

---

## Daily Workflow

| Command | What it does |
|---------|-------------|
| `git status` | Show what's changed |
| `git add <file>` | Stage a file |
| `git add .` | Stage all changes |
| `git add -p` | Stage changes interactively (chunk by chunk) |
| `git commit -m "message"` | Commit staged changes |
| `git commit --amend` | Edit the last commit message (before pushing) |

---

## Viewing History

| Command | What it does |
|---------|-------------|
| `git log --oneline` | Compact history |
| `git log --oneline --graph --all` | Visual branch graph |
| `git log -p` | Show changes in each commit |
| `git show <hash>` | Inspect a specific commit |
| `git diff` | Unstaged changes vs last commit |
| `git diff --staged` | Staged changes vs last commit |
| `git diff branch-a branch-b` | Compare two branches |

---

## Branches

| Command | What it does |
|---------|-------------|
| `git branch` | List local branches |
| `git branch -a` | List all branches (including remote) |
| `git checkout -b <name>` | Create and switch to a new branch |
| `git checkout <name>` | Switch to an existing branch |
| `git merge <branch>` | Merge a branch into current |
| `git merge --no-ff <branch>` | Merge without fast-forward |
| `git branch -d <name>` | Delete a merged branch |
| `git branch -m <old> <new>` | Rename a branch |

---

## Remote

| Command | What it does |
|---------|-------------|
| `git remote -v` | List remotes |
| `git remote add <name> <url>` | Add a remote |
| `git push origin <branch>` | Push a branch |
| `git push --tags` | Push all tags |
| `git fetch origin` | Download remote changes (no merge) |
| `git pull origin <branch>` | Fetch + merge |
| `git remote prune origin` | Remove stale remote references |

---

## Undoing Things

| Command | What it does |
|---------|-------------|
| `git restore <file>` | Discard working directory changes |
| `git restore --staged <file>` | Unstage a file |
| `git revert HEAD` | Undo last commit (safe — creates new commit) |
| `git reset --soft HEAD~1` | Undo commit, keep changes staged |
| `git reset HEAD~1` | Undo commit, unstage changes |
| `git reset --hard HEAD~1` | Undo commit, discard changes ⚠️ |
| `git clean -n` | Preview untracked files to delete |
| `git clean -fd` | Delete untracked files and dirs ⚠️ |

---

## Stash

| Command | What it does |
|---------|-------------|
| `git stash` | Save work in progress |
| `git stash save "message"` | Save with a label |
| `git stash list` | List all stashes |
| `git stash pop` | Apply latest stash and remove it |
| `git stash apply stash@{n}` | Apply a specific stash |
| `git stash drop stash@{n}` | Delete a stash entry |
| `git stash clear` | Delete all stashes |

---

## Advanced

| Command | What it does |
|---------|-------------|
| `git rebase <branch>` | Rebase current branch onto another |
| `git cherry-pick <hash>` | Apply a specific commit to current branch |
| `git tag -a v1.0.0 -m "msg"` | Create an annotated tag |
| `git gc` | Compress and clean the repo |
| `git fsck` | Check repo integrity |

---

## Useful Aliases (Optional)

Add these to your `~/.gitconfig` to speed up common commands:

```ini
[alias]
  st = status
  co = checkout
  br = branch
  lg = log --oneline --graph --all
  unstage = restore --staged
```

---

## The HEAD Reference

| Expression | Meaning |
|------------|---------|
| `HEAD` | Current commit |
| `HEAD~1` | One commit before HEAD |
| `HEAD~3` | Three commits before HEAD |
| `HEAD^` | Parent of HEAD (same as `HEAD~1` for non-merge commits) |
