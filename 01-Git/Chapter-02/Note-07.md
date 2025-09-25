# 📓 Git Basics – Git Aliases

## 1. What are Git Aliases

- Aliases let you create **shortcuts** for Git commands.
- They simplify typing and improve workflow.
- Set using `git config`.

---

## 2. Creating Simple Aliases

- Syntax:

  ```bash
  git config --global alias.<alias-name> '<git-command>'
  ```

- Examples:

  ```bash
  git config --global alias.co checkout
  git config --global alias.br branch
  git config --global alias.ci commit
  git config --global alias.st status
  ```

- Usage:

  ```bash
  git ci    # instead of git commit
  git st    # instead of git status
  ```

---

## 3. Custom Aliases

- Create aliases for commands that don’t exist:

  ```bash
  git config --global alias.unstage 'reset HEAD --'
  ```

- Equivalent commands:

  ```bash
  git unstage fileA
  git reset HEAD -- fileA
  ```

- Alias for last commit:

  ```bash
  git config --global alias.last 'log -1 HEAD'
  git last   # shows last commit
  ```

---

## 4. Aliases for External Commands

- Prefix with `!` to run external commands:

  ```bash
  git config --global alias.visual '!gitk'
  ```

- Usage:

  ```bash
  git visual   # runs gitk GUI
  ```

---

## ⚡ Key Tips

- Aliases **replace the command** with your shortcut.
- Useful for frequently used commands or multi-step commands.
- Can improve workflow efficiency.

---
