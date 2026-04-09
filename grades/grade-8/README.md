# Grade 8 — Git in Real-World Scenarios

> **Prerequisites:** Grades 1–7 complete. You have a solid foundation in Git.

---

## What You'll Learn

- How to use Gitflow as a branching strategy
- How to use pull requests for code review
- How to set up a basic GitHub Actions CI workflow
- How to handle sensitive data and `.gitignore`
- How to sign commits with GPG

---

## Exercises

### Exercise 8.1 — Gitflow Branching Strategy

Gitflow organises your repo around these long-lived branches:

| Branch | Purpose |
|--------|---------|
| `main` | Production-ready code only |
| `develop` | Integration branch for features |
| `feature/*` | Individual features branched from `develop` |
| `release/*` | Release preparation branched from `develop` |
| `hotfix/*` | Emergency fixes branched from `main` |

Simulate a Gitflow feature cycle:

```bash
# Create develop branch (base for features)
git checkout -b develop main

# Create a feature branch
git checkout -b feature/user-profile develop

# Do some work
echo "user profile feature" >> grades/grade-8/practice.txt
git add . && git commit -m "feat: add user profile page"

# Merge feature into develop (no fast-forward — preserves history)
git checkout develop
git merge --no-ff feature/user-profile -m "merge: user profile feature"

# Clean up
git branch -d feature/user-profile

git log --oneline --graph
```

---

### Exercise 8.2 — Pull Requests

Pull Requests (PRs) are GitHub's mechanism for code review before merging. This isn't a Git command — it's a GitHub workflow.

**Practice:**

1. Create a new branch:
   ```bash
   git checkout -b grade8/my-pr-practice
   echo "PR practice" >> grades/grade-8/practice.txt
   git add . && git commit -m "grade 8: add pr practice content"
   git push origin grade8/my-pr-practice
   ```

2. Go to your GitHub repo — you'll see a prompt to **Compare & pull request**

3. Fill in the PR template (this repo has one at `.github/PULL_REQUEST_TEMPLATE/`)

4. Merge the PR on GitHub

5. Pull the merged changes locally:
   ```bash
   git checkout main
   git pull origin main
   ```

---

### Exercise 8.3 — GitHub Actions: Basic CI

This repo includes a starter CI workflow. Inspect it:

```bash
cat .github/workflows/ci.yml
```

The workflow runs on every push and pull request to `main`. It:
1. Checks out the code
2. Validates that all `.txt` practice files exist
3. Reports pass/fail

**To trigger it:** push any commit to your fork and check the **Actions** tab on GitHub.

---

### Exercise 8.4 — Sensitive Data and .gitignore

**This is critical. Accidentally committing secrets (API keys, passwords) is one of the most common real-world Git mistakes.**

```bash
# Simulate accidentally creating a secrets file
echo "DB_PASSWORD=supersecret123" > .env

git status    # it appears as untracked

# BEFORE staging it — add it to .gitignore
echo ".env" >> .gitignore
git status    # now it's ignored

# Commit the .gitignore update
git add .gitignore
git commit -m "chore: ignore .env files"
```

**If you accidentally commit a secret:**

```bash
# Remove the file from the last commit (before pushing)
git rm --cached .env
git commit --amend --no-edit

# If it was already pushed — rotate the secret immediately.
# Then use: https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/removing-sensitive-data-from-a-repository
```

> ⚠️ Even after removing a secret from history, assume it is compromised. **Always rotate credentials immediately.**

---

### Exercise 8.5 — Sign Commits with GPG

Signed commits prove the commit genuinely came from you.

```bash
# Generate a GPG key (if you don't have one)
gpg --full-generate-key
# Choose RSA 4096, set expiry, use your GitHub email

# List your keys
gpg --list-secret-keys --keyid-format=long

# Copy the key ID (the long hex after "sec rsa4096/")
# Configure Git to use it
git config --global user.signingkey YOUR_KEY_ID
git config --global commit.gpgsign true

# Make a signed commit
git commit -S -m "grade 8: signed commit"

# Verify the signature
git log --show-signature -1
```

Add the public key to GitHub: **Settings → SSH and GPG Keys → New GPG Key**

---

## ✅ Grade 8 Checklist

- [ ] Describe the Gitflow branches and their purposes
- [ ] Simulate a Gitflow feature cycle from branch to merge
- [ ] Open and merge a Pull Request on GitHub
- [ ] Locate and explain the GitHub Actions workflow in this repo
- [ ] Prevent a `.env` file from being committed using `.gitignore`
- [ ] Explain what to do if a secret is accidentally pushed
- [ ] Sign a commit with GPG and verify the signature

---

## 🎓 Course Complete!

You've worked through all 8 grades. You can now:

- Manage a complete Git workflow from init to production
- Collaborate safely with others using branches and PRs
- Recover from mistakes confidently
- Apply real-world strategies like Gitflow and signed commits

Keep practising — the best way to get faster at Git is to use it every day.

---

## Reset

```bash
git checkout main
git branch -d develop 2>/dev/null || true
git branch -d grade8/my-pr-practice 2>/dev/null || true
git restore grades/grade-8/practice.txt 2>/dev/null || true
rm -f .env
git config --global commit.gpgsign false 2>/dev/null || true
```
