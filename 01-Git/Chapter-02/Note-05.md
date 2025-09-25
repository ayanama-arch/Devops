# **Git Basics: Working with Remotes**

Remote repositories are versions of your project hosted elsewhere (Internet, network, or even locally). Remotes let you **collaborate**, **fetch**, **push**, and **manage branches** with others.

---

## **1. Viewing Remotes**

- `git remote` → lists shortnames of remotes.
- `git remote -v` → shows fetch/push URLs for each remote.
- Example after cloning:

```bash
$ git remote
origin

$ git remote -v
origin https://github.com/user/repo (fetch)
origin https://github.com/user/repo (push)
```

- Multiple remotes can exist for different collaborators.

---

## **2. Adding a Remote**

- Add new remote:

```bash
$ git remote add <shortname> <url>
```

- Example:

```bash
$ git remote add pb https://github.com/paulboone/ticgit
```

- Fetch data from new remote:

```bash
$ git fetch pb
# Now pb/master and pb/ticgit are accessible locally
```

---

## **3. Fetching & Pulling**

- `git fetch <remote>` → downloads all data from remote (branches, commits) but **does not merge**.
- `git pull` → fetches + merges remote branch into your current branch.
- Default behavior: local branch tracks remote branch (usually master).

**Git pull options**:

- Default (merge if necessary):

```bash
$ git config --global pull.rebase "false"
```

- Rebase on pull:

```bash
$ git config --global pull.rebase "true"
```

---

## **4. Pushing**

- `git push <remote> <branch>` → push commits to remote branch.
- Example:

```bash
$ git push origin master
```

- **Note:** Push rejected if others pushed first; must fetch and merge first.

---

## **5. Inspecting Remotes**

- `git remote show <remote>` → detailed info:

  - Fetch/Push URLs
  - Remote branches (tracked, new, or stale)
  - Local branches tracking remote branches

- Example:

```bash
$ git remote show origin
* remote origin
  Fetch URL: ...
  Push URL: ...
  HEAD branch: master
  Remote branches:
    master tracked
    dev-branch tracked
  Local branch configured for 'git pull':
    master merges with remote master
  Local ref configured for 'git push':
    master pushes to master (up to date)
```

---

## **6. Renaming & Removing Remotes**

- Rename remote:

```bash
$ git remote rename <old> <new>
# e.g., git remote rename pb paul
```

- Remove remote:

```bash
$ git remote remove <remote>
# e.g., git remote remove paul
```

- **Effect:** Remote-tracking branches and configuration for that remote are deleted.

---

## **7. Notes / Tips**

- Remotes can be local or on a network; “remote” just means “elsewhere.”
- Tracking branches make `git pull` and `git push` easier.
- After adding a new remote, always `fetch` to get its branches.
- Use `git remote show` to check branch tracking and remote status.

---
