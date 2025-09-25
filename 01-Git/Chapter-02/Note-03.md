# **Git Basics: Viewing Commit History**

## **1. Basic Command**

- `git log` → Shows commit history of the repository.
- Default behavior: **reverse chronological order** (most recent commits first).
- Each commit shows:

  - SHA-1 hash
  - Author name & email
  - Date
  - Commit message

**Example:**

```bash
$ git log
commit a11bef06...
Author: Scott Chacon <schacon@gee-mail.com>
Date: Sat Mar 15 10:31:28 2008 -0700
Initial commit
```

---

## **2. Useful Output Options**

### **2.1 Show changes introduced (diff)**

- `-p` or `--patch` → shows code changes for each commit.
- Limit entries: `-2` → last 2 commits.

```bash
$ git log -p -2
```

### **2.2 Show stats summary**

- `--stat` → lists modified files + lines added/deleted per commit.
- `--shortstat` → only summary line (changes, insertions, deletions).

```bash
$ git log --stat
```

### **2.3 Format output**

- `--pretty` → formats log output in different styles:

  - `oneline` → each commit on 1 line
  - `short`, `full`, `fuller` → varying levels of detail
  - `format:"..."` → custom output

**Example:**

```bash
$ git log --pretty=format:"%h - %an, %ar : %s"
```

- `%h` → short commit hash

- `%an` → author name

- `%ar` → relative date

- `%s` → commit message

- Useful for machine-readable output.

---

### **2.4 Graphical view**

- `--graph` → ASCII graph showing branch/merge history

```bash
$ git log --pretty=format:"%h %s" --graph
```

---

## **3. Limiting Log Output**

| Option                 | Description                                    |
| ---------------------- | ---------------------------------------------- |
| `-<n>`                 | Show last n commits                            |
| `--since` / `--after`  | Commits after a date                           |
| `--until` / `--before` | Commits before a date                          |
| `--author`             | Filter commits by author                       |
| `--committer`          | Filter commits by committer                    |
| `--grep`               | Search commit messages for string              |
| `-S`                   | Show commits adding/removing a specific string |
| `-- path/to/file`      | Limit commits to specific file(s)              |

**Example:**

```bash
$ git log --pretty="%h - %s" --author='Junio C Hamano' --since="2008-10-01" --before="2008-11-01" --no-merges -- t/
```

---

## **4. Other Handy Options**

- `--name-only` → list files modified (names only)
- `--name-status` → list files with added/modified/deleted info
- `--abbrev-commit` → short SHA-1 hash
- `--relative-date` → show relative date (e.g., “2 weeks ago”)
- `--oneline` → shorthand for `--pretty=oneline --abbrev-commit`
- `--no-merges` → skip merge commits

---

### **5. Author vs Committer**

- **Author** → originally wrote the work
- **Committer** → last applied the work
  Useful when a contributor sends a patch that a core member applies.

---
