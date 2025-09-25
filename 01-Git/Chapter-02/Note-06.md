# 📓 Git Basics – Tagging

## 1. What is Tagging

- Tags mark specific points in Git history (important commits, e.g., releases).
- Typical use: release versions like `v1.0`, `v2.0`.

---

## 2. Listing Tags

- Command:

  ```bash
  git tag
  ```

  - Lists all tags **alphabetically**.

- Using pattern/wildcards:

  ```bash
  git tag -l "v1.8.5*"
  ```

  - **`-l` or `--list` is mandatory** when using wildcards.

---

## 3. Types of Tags

### 3.1 Annotated Tags

- Stored as full objects in Git database.
- Includes:

  - Tagger name & email
  - Date
  - Tag message
  - Can be GPG-signed and verified

- Recommended for official releases.
- Create annotated tag:

  ```bash
  git tag -a v1.4 -m "my version 1.4"
  ```

- View tag info:

  ```bash
  git show v1.4
  ```

  Shows tagger info + commit details.

### 3.2 Lightweight Tags

- Simple pointer to a commit (no metadata).
- Like a fixed branch that doesn’t move.
- Create lightweight tag:

  ```bash
  git tag v1.4-lw
  ```

- View tag:

  ```bash
  git show v1.4-lw
  ```

  Shows only the commit info, no tagger info.

---

## 4. Tagging Past Commits

- You can tag old commits using SHA:

  ```bash
  git tag -a v1.2 <commit-hash>
  ```

- Verify:

  ```bash
  git tag
  git show v1.2
  ```

---

## 5. Sharing Tags

- Tags are **not pushed by default**.
- Push a single tag:

  ```bash
  git push origin v1.5
  ```

- Push all tags:

  ```bash
  git push origin --tags
  ```

- Only annotated tags:

  ```bash
  git push origin --follow-tags
  ```

---

## 6. Deleting Tags

### 6.1 Local

```bash
git tag -d <tagname>
```

- Example:

  ```bash
  git tag -d v1.4-lw
  ```

### 6.2 Remote

- Option 1 (older syntax):

  ```bash
  git push origin :refs/tags/<tagname>
  ```

- Option 2 (modern):

  ```bash
  git push origin --delete <tagname>
  ```

---

## 7. Checking Out Tags

- Checkout a tag:

  ```bash
  git checkout v2.0.0
  ```

- **Detached HEAD state**:

  - HEAD points to tag commit, not a branch.
  - Any commits here are **unreachable from branches** unless you create one.

- To create a branch from a tag:

  ```bash
  git checkout -b <branch-name> <tag-name>
  ```

  - Safe way to make changes on a past release.

---

## ⚡ Key Tips

- Annotated tags = metadata + GPG signing (preferred).
- Lightweight tags = simple pointer, no metadata.
- Push tags explicitly, otherwise they stay local.
- Detached HEAD: create branch if making new commits.

---
