# Git Version Control - Concise Notes

## What is Version Control?

- **Definition**: System that records changes to files over time to recall specific versions later
- **Purpose**: Track modifications, compare changes, identify who made changes and when
- **Benefits**:
  - Revert files/projects to previous states
  - Easy recovery from mistakes or lost files
  - Minimal overhead
- **Applications**: Software code, images, layouts, any computer files

## Evolution of Version Control Systems

### 1. Local Version Control Systems (VCS)

- **Method**: Copy files to different directories (often time-stamped)
- **Problems**:
  - Error-prone (wrong directory, accidental overwrites)
  - Easy to forget current location
- **Solution**: Local VCS with simple database tracking file changes
- **Example**: RCS (Revision Control System)
  - Stores patch sets (file differences) on disk
  - Recreates any file version by applying patches

### 2. Centralized Version Control Systems (CVCS)

- **Need**: Collaboration with developers on different systems
- **Structure**: Single server with all versioned files + multiple clients
- **Examples**: CVS, Subversion, Perforce

#### Advantages:

- Everyone knows project status
- Fine-grained administrative control
- Easier to manage than local databases

#### Disadvantages:

- **Single point of failure**: Server downtime stops all collaboration
- **Data loss risk**: Corrupted central database = lost project history
- **Dependency**: All work depends on central server availability

### 3. Distributed Version Control Systems (DVCS)

- **Examples**: Git, Mercurial, Darcs
- **Key Difference**: Clients fully mirror the entire repository + complete history

#### Advantages:

- **No single point of failure**: Any client can restore the server
- **Every clone = full backup** of all project data
- **Multiple remote repositories**: Work with different groups simultaneously
- **Flexible workflows**: Hierarchical models possible
- **Enhanced collaboration**: Different workflow types within same project

## What is Git?

### Snapshots, Not Differences

- **Traditional VCS approach**: Store files + changes over time (delta-based)
- **Git's approach**: Takes snapshots of entire project state at each commit
- **Efficiency**: Unchanged files → stored as links to previous versions
- **Concept**: Git = mini filesystem with powerful tools, not just a VCS

### Nearly Every Operation is Local

- **Speed**: Most operations use only local files (no network latency)
- **Examples**:
  - Browse project history: Read from local database instantly
  - Compare file versions: Local difference calculation
- **Offline capability**: Work without network/VPN connection
  - Can commit to local copy anywhere
  - Upload when network available
- **Comparison**: Other VCS (Perforce, SVN) require server connection

### Git Has Integrity

- **Checksumming**: Everything checksummed before storage
- **Detection**: Impossible to change files without Git knowing
- **SHA-1 Hash**: 40-character hexadecimal string
  - Example: `24b9da6552252987aa493b52f8696cd6d3b00373`
  - Based on file/directory contents
  - Git stores everything by hash value, not filename

### Git Generally Only Adds Data

- **Safety**: Nearly all actions only add data to Git database
- **Difficulty to lose data**: Hard to make Git erase committed data
- **Experimentation**: Safe to try things without fear of data loss
- **Regular pushing**: Further protects against data loss

### The Three States

Files can be in three states:

1. **Modified**: Changed but not committed to database
2. **Staged**: Marked for next commit snapshot
3. **Committed**: Safely stored in local database

### Three Main Sections of Git Project

1. **Working Tree**: Single checkout of one project version
   - Files extracted from Git directory to disk for use/modification
2. **Staging Area** (Index): File storing info about next commit
   - Located in Git directory
3. **Git Directory**: Stores metadata and object database
   - Most important part of Git
   - What gets copied when cloning

### Basic Git Workflow

1. **Modify** files in working tree
2. **Stage** selected changes (adds only those changes to staging area)
3. **Commit** staged files (stores snapshot permanently to Git directory)

### File State Determination

- **In Git directory** → Committed
- **Modified + added to staging area** → Staged
- **Changed since checkout but not staged** → Modified

## First-Time Git Setup

### Git Configuration Tool

- **Command**: `git config` - get and set configuration variables
- **Persistence**: Settings stick around between upgrades
- **Modification**: Can change anytime by re-running commands

### Configuration File Hierarchy (3 Levels)

1. **System Level**: `[path]/etc/gitconfig`

   - Applies to every user and all repositories
   - Access: `git config --system` (requires admin privileges)

2. **Global Level**: `~/.gitconfig` or `~/.config/git/config`

   - User-specific settings for all repositories
   - Access: `git config --global`

3. **Local Level**: `.git/config` (in current repository)
   - Repository-specific settings
   - Access: `git config --local` (default behavior)

**Override Rule**: Local > Global > System (each level overrides previous)

### Windows-Specific Locations

- **User config**: `$HOME` directory (`C:\Users\$USER`)
- **System config**: Relative to MSys root (Git installation location)
- **Git 2.x+ system config**:
  - Windows XP: `C:\Documents and Settings\All Users\Application Data\Git\config`
  - Vista+: `C:\ProgramData\Git\config`
  - Change only via: `git config -f <file>` (as admin)

### Essential Configuration Commands

#### View All Settings

```bash
git config --list --show-origin  # Shows settings and their source files
git config --list                # Lists all current settings
```

#### Your Identity (Required)

```bash
git config --global user.name "John Doe"
git config --global user.email johndoe@example.com
```

- **Importance**: Every commit uses this information (immutably baked in)
- **Global**: Use `--global` for system-wide setting
- **Project-specific**: Run without `--global` in specific repository

#### Your Editor

```bash
git config --global core.editor emacs
```

- **Default**: Uses system's default editor
- **Windows example** (Notepad++):

```bash
git config --global core.editor "'C:/Program Files/Notepad++/notepad++.exe' -multiInst -notabbar -nosession -noPlugin"
```

- **Warning**: Incorrect setup can cause confusing Git states

#### Default Branch Name

```bash
git config --global init.defaultBranch main
```

- **Default**: Git creates "master" branch with `git init`
- **Available**: Git version 2.28+
- **Alternative**: Set "main" as default branch name

### Checking Configuration

#### Check Specific Setting

```bash
git config user.name     # Returns: John Doe
```

#### Find Setting Origin

```bash
git config --show-origin rerere.autoUpdate
# Returns: file:/home/johndoe/.gitconfig    false
```

#### Multiple Values

- Same key may appear multiple times (different config files)
- Git uses **last value** for each unique key
- Use `--show-origin` to trace unexpected values

## Key Concepts Summary

- **Local VCS**: Individual file tracking with patches
- **CVCS**: Central server model with collaboration capabilities
- **DVCS**: Distributed model with full repository mirroring
- **Git's Uniqueness**: Snapshots + local operations + integrity + safety
- **Core Workflow**: Modify → Stage → Commit
- **Setup Priority**: Identity → Editor → Default branch → Verify settings
