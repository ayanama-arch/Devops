# 📓 Notes: Git Basics – Recording Changes to the Repository

## 1. File States in Git

- **Tracked** → files already known to Git (from last commit or staged).

  - States: _unmodified, modified, staged_.

- **Untracked** → new files not in last snapshot and not staged.

👉 After a clone, all files = tracked + unmodified.

---

## 2. Checking File Status

- Command:

  ```bash
  git status
  ```

- Shows:

  - Current branch.
  - Staged changes (ready to commit).
  - Unstaged changes (modified but not staged).
  - Untracked files.

- Short form:

  ```bash
  git status -s
  ```

  - `??` = untracked
  - `A` = added
  - `M` = modified
  - Two columns:

    - Left = staging area
    - Right = working directory

---

## 3. Tracking New Files

- Command:

  ```bash
  git add <file>
  ```

- Example:

  ```bash
  git add README
  ```

- Adds file to **staging area** (snapshot is locked at `git add` time).

---

## 4. Staging Modified Files

- Modified tracked file → not staged until:

  ```bash
  git add <file>
  ```

- Important: If you edit a file **after** staging it, you must re-run `git add` to update the staged version.

---

## 5. Ignoring Files

- Create `.gitignore` to skip unwanted files.
- Example:

  ```
  *.a        # ignore all .a files
  !lib.a     # but not lib.a
  /TODO      # only ignore TODO in root
  build/     # ignore all build dirs
  doc/*.txt  # ignore specific txt files
  doc/**/*.pdf  # ignore pdfs in subdirs
  ```

- Rules:

  - `#` = comments
  - `*` = wildcard
  - `?` = single char
  - `[0-9]` = range
  - `!` = negate pattern

👉 GitHub has examples: [github.com/github/gitignore](https://github.com/github/gitignore)

---

## 6. Viewing Changes

- Unstaged changes:

  ```bash
  git diff
  ```

- Staged changes:

  ```bash
  git diff --staged
  ```

  (`--cached` = same as `--staged`)

- External tools:

  ```bash
  git difftool
  ```

---

## 7. Committing Changes

- Standard:

  ```bash
  git commit
  ```

  → opens editor for commit message.

- Inline message:

  ```bash
  git commit -m "message"
  ```

- Verbose (show diff in editor):

  ```bash
  git commit -v
  ```

- Skip staging (commit all tracked modified files):

  ```bash
  git commit -a -m "msg"
  ```

---

## 8. Removing Files

- Remove from working dir + staging:

  ```bash
  git rm <file>
  ```

- Keep file locally but untrack it:

  ```bash
  git rm --cached <file>
  ```

- Force removal (if modified):

  ```bash
  git rm -f <file>
  ```

---

## 9. Moving/Renaming Files

- Rename with Git:

  ```bash
  git mv old new
  ```

- Equivalent to:

  ```bash
  mv old new
  git rm old
  git add new
  ```

👉 `git mv` = shortcut, Git auto-detects renames.

---

## ⚡ Quick Command Cheat Sheet

- `git status [-s]` → see file states
- `git add <file>` → track or stage file
- `git diff` → show unstaged changes
- `git diff --staged` → show staged changes
- `git commit -m "msg"` → commit staged changes
- `git commit -a -m "msg"` → commit tracked modified files (skip staging)
- `git rm <file>` → remove & untrack file
- `git rm --cached <file>` → untrack only
- `git mv old new` → rename/move file

---
