# 🚀 Day 24 – Advanced Git: Merge, Rebase, Stash & Cherry Pick

---

## Task 1: Git Merge

### Commands Used

```bash
git checkout -b feature-login

git checkout main
git merge feature-login
```

```bash
git checkout -b feature-signup
echo "signup feature" >> file.txt
git add .
git commit -m "added signup feature"

git checkout main
echo "update in main" >> file.txt
git add .
git commit -m "updated main branch"

git merge feature-signup
```

---

### ✅ Observations

* First merge → fast-forward
* Second merge → merge commit
* Conflict occurred when same line edited

---

### Answers

#### What is a fast-forward merge?

When no new commits exist in `main`, Git simply moves the pointer forward.

#### When does Git create a merge commit?

When both branches have new commits and diverged.

#### What is a merge conflict?

When the same part of a file is modified in both branches and Git cannot auto-merge.

---

## Task 2: Git Rebase

### Commands Used

```bash
git checkout -b feature-dashboard

git checkout main

git checkout feature-dashboard
git rebase main
```

### Conflict Handling

```bash
git add .
git rebase --continue
# OR
git rebase --abort
```

---

### Observations

* Commits replayed on top of main
* History became linear

---

### Answers

#### 🔸 What does rebase do?

Re-applies commits on top of another branch.

#### 🔸 Difference from merge?

Merge → non-linear history
Rebase → linear history

#### 🔸 Why avoid rebasing shared commits?

Because it rewrites history and breaks collaboration.

#### 🔸 When to use?

Rebase → local cleanup
Merge → shared branches

---

## Task 3: Squash vs Merge

### Commands Used

```bash
git checkout -b feature-profile
git commit -m "fix 1"
git commit -m "fix 2"
git commit -m "fix 3"

git checkout main
git merge --squash feature-profile
git commit -m "profile feature "
```

```bash
git checkout -b feature-settings
git commit -m "setting 1"
git commit -m "setting 2"

git checkout main
git merge feature-settings
```

---

### Observations

* Squash → 1 commit
* Merge → multiple commits

---

### Answers

#### What is squash merge?

Combines multiple commits into one.

#### When to use?

For cleaning messy commits.

#### Trade-off?

Lose detailed history.

---

## Task 4: Git Stash

### Commands Used

```bash
echo "work in progress" >> file.txt

git stash
git stash push -m "WIP work"

git stash list
git stash apply
git stash pop
git stash apply stash@{0}
```

---

### Observations

* Work saved temporarily
* Can switch branches safely

---

### Answers

#### pop vs apply?

pop → apply + delete
apply → only apply

#### When to use stash?

When switching tasks without committing incomplete work.

---

## Task 5: Cherry Pick

### Commands Used

```bash
git checkout -b feature-hotfix
git commit -m "fix 1"
git commit -m "fix 2"
git commit -m "fix 3"

git checkout main
git log --oneline

git cherry-pick <commit-hash>
```

### Conflict Handling

```bash
git add .
git cherry-pick --continue
# OR
git cherry-pick --abort
```

---

### Observations

* Only selected commit applied

---

### Answers

#### What is cherry-pick?

Applies a specific commit from one branch to another.

#### When to use?

Hotfix or selective changes.

#### Risks?

Conflicts, duplicate commits, messy history.

---

## Key Takeaways

* Merge → safe, keeps history
* Rebase → clean but risky
* Squash → cleaner PR
* Stash → temporary save
* Cherry-pick → selective commit

---




