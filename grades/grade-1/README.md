# Grade 1 — Getting Started with Git

> **Prerequisites:** None. This is the beginning.

---

## What You'll Learn

- What Git is and why it exists
- How to install Git on your machine
- How to configure Git with your identity
- How to initialise a new repo and clone an existing one

---

## Exercises

### Exercise 1.1 — Check Your Installation

Verify Git is installed and check the version:

```bash
git --version
```

> **Expected output:** something like `git version 2.x.x`
> If you see `command not found`, head to the [installation guide](https://git-scm.com/downloads) for your OS.

---

### Exercise 1.2 — Configure Your Identity

Git stamps every commit with your name and email. Set them now:

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

Verify the config was saved:

```bash
git config --list
```

> **Tip:** `--global` sets this for all repos on your machine. You can override it per-repo by running the same command without `--global` inside a repo folder.

---

### Exercise 1.3 — Initialise a New Repository

Create a brand new repo from scratch:

```bash
mkdir my-first-repo
cd my-first-repo
git init
```

Check what Git created:

```bash
ls -la
```

> You should see a hidden `.git/` folder. That folder **is** your repository — it stores the entire history. Never manually edit files inside it.

---

### Exercise 1.4 — Clone This Repo

You already cloned this repo to get here — but practise it again with a fresh location:

```bash
cd ~
git clone https://github.com/<your-username>/git-101.git git-101-clone
cd git-101-clone
ls
```

> **Note:** Cloning copies the entire repository history, not just the latest files.

---

### Exercise 1.5 — Explore the .git Directory

Peek inside the `.git` folder (read only — don't edit anything):

```bash
ls .git/
cat .git/HEAD
```

> `HEAD` is a pointer to the branch you're currently on. You'll learn more about this in Grade 5.

---

## ✅ Grade 1 Checklist

Before moving to Grade 2, confirm you can:

- [ ] Run `git --version` and see a version number
- [ ] Set `user.name` and `user.email` with `git config`
- [ ] Run `git init` to create a new repo
- [ ] Run `git clone` to copy an existing repo
- [ ] Locate and describe the `.git/` folder

---

## Reset

If something went wrong, clean up any test repos you created:

```bash
cd ~
rm -rf my-first-repo
rm -rf git-101-clone
```

Your main `git-101` clone is unaffected.
