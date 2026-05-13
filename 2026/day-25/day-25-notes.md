
---

# Task 1: Git Reset — Hands-On


```bash
git commit -m "Added soft reset"

git commit -m "Added mixed reset"

git commit -m "Added hard reset"
```

---

## git reset --soft

```bash
git reset --soft HEAD~1
```

### Observation
- Last commit removed from history
- Changes remain staged
- Files remain unchanged

### Use Case
- Fix commit message
- Squash commits
- Quick recommit

---

## git reset --mixed

```bash
git reset --mixed HEAD~1
```

### Observation
- Last commit removed
- Changes remain in working directory
- Changes become unstaged

### Use Case
- Edit files before recommitting
- Unstage accidental commits

---

## git reset --hard

```bash
git reset --hard HEAD~1
```

### Observation
- Last commit removed
- Changes deleted permanently
- Working directory restored

### Use Case
- Remove unwanted local changes
- Clean repository state

---

# Answers

## Difference between --soft, --mixed, and --hard

| Command | Commit Removed | Changes Staged | Changes Kept |
|---|---|---|---|
| `--soft` | Yes | Yes | Yes |
| `--mixed` | Yes | No | Yes |
| `--hard` | Yes | No | No |

---

## Which one is destructive and why?

`git reset --hard` is destructive because it permanently deletes commits and local changes.

---

## When would you use each one?

### `--soft`
- Fix commits
- Squash commits
- Quick recommit

### `--mixed`
- Modify files before commit
- Unstage changes

### `--hard`
- Delete unwanted changes permanently
- Reset local repository state

---

## Should you use git reset on pushed commits?

Generally no because it rewrites history and may break collaboration for teammates.

---

# Task 2: Git Revert — Hands-On


```bash
git commit -m "Commit X on main branch"

git commit -m "Commit Y on main branch"

git commit -m "Commit Z on main branch"
```

---

## Revert Commit Y

```bash
git log --oneline
git revert <commit-hash>
```

### Observation
- Git creates a new commit
- Original commit Y remains in history
- Changes introduced by Y are reversed safely

---

# Answers

## Difference between git revert and git reset

### git reset
- Moves branch pointer backward
- Can remove commit history

### git revert
- Creates a new undo commit
- Keeps commit history intact

---

## Why is revert safer than reset?

Because revert does not rewrite history, making it safe for shared branches.

---

## When to use revert vs reset?

### Use `revert`
- Shared branches
- Production fixes
- Team collaboration

### Use `reset`
- Local commits
- Cleanup before push
- Personal history changes

---

# Task 3: Reset vs Revert — Summary

| Feature | git reset | git revert |
|---|---|---|
| What it does | Moves HEAD backward | Creates undo commit |
| Removes commit history? | Yes | No |
| Safe for pushed/shared branches? | No | Yes |
| Rewrites history? | Yes | No |
| Best use case | Local cleanup | Shared branch fixes |

---

# Task 4: Branching Strategies

## How it Works
Uses multiple long-lived branches:
- `main`
- `develop`
- `feature/*`
- `release/*`
- `hotfix/*`

## Flow Diagram

```text
main
  └── develop
        ├── feature/login
        ├── feature/payment
        └── release/v1.0
               └── hotfix/critical-bug
```

## Used In
- Large enterprises
- Scheduled release systems

## Pros
- Structured workflow
- Stable production branch
- Good release management

## Cons
- Complex workflow
- Slower development cycle

---

# 2. GitHub Flow

## How it Works
- Single `main` branch
- Create feature branches
- Merge through Pull Requests

## Flow Diagram

```text
main
 ├── feature-ui
 ├── fix-navbar
 └── add-api
```

## Used In
- Startups
- SaaS products
- Continuous deployment systems

## Pros
- Simple workflow
- Fast development
- Easy collaboration

## Cons
- Less release structure
- Requires strong CI/CD

---

# 3. Trunk-Based Development

## How it Works
- Everyone commits frequently to main
- Very short-lived branches
- Heavy automation/testing

## Flow Diagram

```text
main
 ├── small-feature
 ├── quick-fix
 └── merged quickly
```

## Used In
- Google
- Facebook
- Fast engineering teams

## Pros
- Fast integration
- Fewer merge conflicts
- Excellent for CI/CD

## Cons
- Requires excellent testing
- Risky without automation

---

# Answers

## Which strategy would you use for a startup shipping fast?

GitHub Flow or Trunk-Based Development because they allow rapid releases and simpler workflows.

---

## Which strategy would you use for a large team with scheduled releases?

GitFlow because it provides organized release management and stable production branches.

---

## Which strategy does a popular open-source project use?

:contentReference[oaicite:0]{index=0} mainly follows GitHub-style workflows using Pull Requests and feature branches.


