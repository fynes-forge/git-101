# Grade 3 — Collaborating with GitHub

> **Prerequisites:** Grade 2 complete. You can stage and commit changes.

---

## What You'll Learn

- How to generate SSH keys and add them to GitHub
- How to connect a local repo to a remote
- How to push, fetch, and pull changes
- How to manage multiple remotes

---

## Exercises

### Exercise 3.1 — Generate an SSH Key

SSH keys let you authenticate with GitHub without a password every time.

```bash
# Generate a new ED25519 key (recommended)
ssh-keygen -t ed25519 -C "you@example.com"

# Accept the default file location, add a passphrase if you like
# Your keys are now at:
#   ~/.ssh/id_ed25519       (private key — never share this)
#   ~/.ssh/id_ed25519.pub   (public key — this goes on GitHub)
```

Copy your public key:

```bash
cat ~/.ssh/id_ed25519.pub
```

> Go to **GitHub → Settings → SSH and GPG Keys → New SSH Key**, paste it in, and save.

---

### Exercise 3.2 — Test Your SSH Connection

```bash
ssh -T git@github.com
```

> **Expected:** `Hi <username>! You've successfully authenticated...`

---

### Exercise 3.3 — Inspect Your Remote

You already have a remote set up from when you cloned:

```bash
git remote -v
```

> You should see `origin` pointing to your fork. `origin` is just a conventional name — you can rename it or have multiple remotes.

---

### Exercise 3.4 — Push a Change to GitHub

Make a change, commit it, and push it:

```bash
echo "Pushed from local" >> grades/grade-3/practice.txt
git add grades/grade-3/practice.txt
git commit -m "grade 3: practise pushing to remote"
git push origin main
```

Go to your GitHub repo in a browser and confirm the change is there.

---

### Exercise 3.5 — Fetch vs Pull

```bash
# Fetch downloads changes from the remote but does NOT merge them
git fetch origin

# Check what came down
git log origin/main --oneline

# Pull fetches AND merges in one step
git pull origin main
```

> **Best practice:** Use `git fetch` + `git log` to inspect what's coming before you merge it into your working branch.

---

### Exercise 3.6 — Add a Second Remote

Point a second remote at the original course repo (upstream):

```bash
git remote add upstream https://github.com/Tom-Fynes/git-101.git
git remote -v
```

Fetch from it (you won't push to it — that's the author's repo):

```bash
git fetch upstream
git log upstream/main --oneline
```

> This upstream pattern is how open-source contribution works: you fork → clone → add upstream → keep your fork in sync.

---

## ✅ Grade 3 Checklist

- [ ] Generate an SSH key and add it to GitHub
- [ ] Verify SSH connection with `ssh -T git@github.com`
- [ ] Push a commit to your remote with `git push`
- [ ] Explain the difference between `git fetch` and `git pull`
- [ ] Add a second remote with `git remote add`

---

## Reset

```bash
# Remove the upstream remote if you added it
git remote remove upstream

# Restore the practice file
git restore grades/grade-3/practice.txt
```
