## 📓 Notes: Git Basics – Getting a Git Repository

### Two ways to get a Git repo

1. **Initialize in an existing directory** → `git init`

   - Turns a folder into a Git repo by creating a hidden `.git` directory.
   - At this point, files are _not yet tracked_.
   - To start tracking and commit:

     ```bash
     git add <files>
     git commit -m "Initial project version"
     ```

   - Example:

     ```bash
     git add *.c
     git add LICENSE
     git commit -m "Initial project version"
     ```

2. **Clone an existing repository** → `git clone <url> [dir-name]`

   - Downloads the entire history, not just a working copy.
   - Example:

     ```bash
     git clone https://github.com/libgit2/libgit2
     ```

     → creates a directory `libgit2` with `.git` inside.

   - To clone into a custom folder name:

     ```bash
     git clone https://github.com/libgit2/libgit2 mylibgit
     ```

   - Supports multiple protocols: `https://`, `git://`, `ssh://` (`user@server:path/to/repo.git`).

---

### Key points to remember

- `git init` → create a brand-new repo.
- `git clone` → copy an existing repo (with full history).
- The `.git` folder is the **repository skeleton**, holds all version control data.
- Tracking starts after you explicitly `git add`.
- A commit (`git commit -m "msg"`) records the snapshot permanently.
- Git clone = full backup (can even restore server if it breaks).

---

Think of it like this:

- **`git init`** = “Hey Git, start watching this folder.”
- **`git clone`** = “Give me a copy of the whole project’s history, not just the files.”

---
