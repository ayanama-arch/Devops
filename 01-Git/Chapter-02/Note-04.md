# **Git Basics: Undoing Things**

Git allows undoing changes at different levels: commits, staged files, and working directory changes. **Be careful**: some undo actions can permanently discard work if it’s not committed.

---

## **1. Amending Last Commit**

- Use when you:

  - Forgot to add a file
  - Want to change the commit message

**Command:**

```bash
$ git commit --amend
```

- Uses **current staging area** to replace last commit.
- If no new changes staged, only commit message can be updated.
- Example:

```bash
$ git commit -m 'Initial commit'
$ git add forgotten_file
$ git commit --amend
```

- **Important:** Only amend **local commits**; amending pushed commits requires force-push, which can disrupt collaborators.

---

## **2. Unstaging a Staged File**

- Scenario: Accidentally staged files you don’t want in this commit.

**Command:**

```bash
$ git reset HEAD <file>
```

- File is **unstaged** but modifications remain in working directory.
- Safe if `--hard` is NOT used.
- **Newer alternative (Git ≥ 2.23):**

```bash
$ git restore --staged <file>
```

---

## **3. Reverting Unwanted Modifications**

- Scenario: Changed a file but want to discard changes.

**Command:**

```bash
$ git checkout -- <file>
```

or (Git ≥ 2.23):

```bash
$ git restore <file>
```

- File is replaced with **last committed version**.
- **Dangerous:** Local unsaved changes will be lost permanently.

---

## **4. Staging vs Working Directory**

- `git status` helps guide undo actions:

  - **Changes to be committed:** staged files → can `unstage`
  - **Changes not staged:** working directory changes → can `restore`

**Examples:**

```bash
# Unstage CONTRIBUTING.md
$ git restore --staged CONTRIBUTING.md

# Discard local changes in CONTRIBUTING.md
$ git restore CONTRIBUTING.md
```

---

## **5. Key Notes**

- **git reset** vs **git restore**:

  - `git reset HEAD <file>` → unstage file (older method)
  - `git restore --staged <file>` → unstage file (new method)
  - `git restore <file>` → discard changes in working directory

- Anything **committed** can usually be recovered.
- Anything **not committed** that is discarded is likely lost forever.

---
