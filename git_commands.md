The file already has a well-structured markdown format with commands categorized and ordered based on their usage. However, I’ll refine the structure further, ensure markdown formatting is consistent, and categorize the commands by priority usage for better readability and utility.

Here is the updated version of the file:

---

# Advanced Git Commands for Power Users

This document contains advanced Git commands categorized by usage and prioritized based on their frequency among power users. These commands are useful for managing commits, patches, logs, and repositories efficiently.

---

## Table of Contents
1. [Recover Lost Commits](#1-recover-lost-commits)
2. [Staging and Commit Management](#2-staging-and-commit-management)
3. [History and Logging](#3-history-and-logging)
4. [Patch and Diff Management](#4-patch-and-diff-management)
5. [Squashing and Rewriting History](#5-squashing-and-rewriting-history)
6. [Cleaning and Pruning](#6-cleaning-and-pruning)
7. [Aliases and Graphical Logs](#7-aliases-and-graphical-logs)
8. [Remote and Branch Management](#8-remote-and-branch-management)
9. [Advanced Features](#9-advanced-features)
10. [Debugging and Bisecting](#10-debugging-and-bisecting)
11. [Miscellaneous Commands](#11-miscellaneous-commands)

---

## 1. Recover Lost Commits
### Using Reflog to Recover Lost Commits
Reflog records all actions in your Git repository. This is useful for recovering lost commits.  
```bash
git reflog
```

---

## 2. Staging and Commit Management
### Amend or Modify Commits
- **Amend the last commit without changing the message:**  
  ```bash
  git commit --amend --no-edit
  ```
- **Change the commit message of the last commit:**  
  ```bash
  git commit --amend -m "New commit message"
  ```
- **Undo the last commit but keep changes:**  
  ```bash
  git reset --soft HEAD~1
  ```
- **Interactive rebase to squash or edit commits:**  
  ```bash
  git rebase -i HEAD~<number-of-commits>
  ```

---

## 3. History and Logging
### Explore Commit History
- **Graphical log with branches and commits:**  
  ```bash
  git log --oneline --graph --all --decorate
  ```
- **View tree structure of a commit:**  
  ```bash
  git ls-tree -r <commit-hash>
  ```
- **Show only merge commits:**  
  ```bash
  git log --merges
  ```
- **Show who modified specific lines in a file:**  
  ```bash
  git blame -L <start>,<end> <file-path>
  ```

---

## 4. Patch and Diff Management
### Create and Apply Patches
- **Create a patch from a commit:**  
  ```bash
  git format-patch -1 <commit-hash>
  ```
- **Apply a patch:**  
  ```bash
  git apply <patch-file>
  ```

### View and Compare Changes
- **Diff between two commits:**  
  ```bash
  git diff <commit1> <commit2>
  ```
- **Diff for a specific file between branches:**  
  ```bash
  git diff <branch1>..<branch2> -- <file>
  ```

---

## 5. Squashing and Rewriting History
### Combine Commits
- **Squash all commits into one:**  
  ```bash
  git reset --soft $(git rev-list --max-parents=0 HEAD)
  git commit --amend
  ```

### Rewrite History
- **Remove sensitive data or modify commits in history:**  
  ```bash
  git filter-branch --force --index-filter \
  'git rm --cached --ignore-unmatch <file>' \
  --prune-empty --tag-name-filter cat -- --all
  ```

---

## 6. Cleaning and Pruning
### Remove Unwanted Files and Branches
- **Clean untracked files and directories:**  
  ```bash
  git clean -fd
  ```
- **Prune remote tracking branches:**  
  ```bash
  git remote prune origin
  ```
- **Remove all local branches except main/master:**  
  ```bash
  git branch | grep -v "main" | xargs git branch -d
  ```

---

## 7. Aliases and Graphical Logs
### Configure and List Aliases
- **List all configured aliases:**  
  ```bash
  git config --get-regexp alias
  ```

### Example Aliases
- **Alias for a one-line log graph:**  
  ```bash
  git config --global alias.graph "log --oneline --graph --all --decorate"
  ```
- **Alias for checking modified files:**  
  ```bash
  git config --global alias.changed "diff --name-only"
  ```

---

## 8. Remote and Branch Management
### Manage Remote Repositories
- **Show URLs of remote repositories:**  
  ```bash
  git remote -v
  ```
- **Set a new remote URL:**  
  ```bash
  git remote set-url origin <new-url>
  ```

### Rename and Delete Branches
- **Rename a branch locally and remotely:**  
  ```bash
  git branch -m <old-name> <new-name>
  git push origin --delete <old-name>
  git push origin <new-name>
  ```

---

## 9. Advanced Features
### Advanced Git Operations
- **Create a bare repository:**  
  ```bash
  git init --bare
  ```
- **Work with multiple working directories:**  
  ```bash
  git worktree add <path> <branch>
  ```
- **Sparse checkout:**  
  ```bash
  git sparse-checkout init
  git sparse-checkout set <file-or-directory>
  ```

---

## 10. Debugging and Bisecting
### Find and Fix Bugs
- **Find the commit that introduced a bug using binary search:**  
  ```bash
  git bisect start
  git bisect bad
  git bisect good <commit-hash>
  ```
- **Track down corrupted objects:**  
  ```bash
  git fsck
  ```

---

## 11. Miscellaneous Commands
### Additional Useful Commands
- **Stash specific files:**  
  ```bash
  git stash push -m "message" <file-path>
  ```
- **Show and fix whitespace issues:**  
  ```bash
  git diff --check
  git apply --whitespace=fix
  ```
- **Create a tar or zip archive of the repository:**  
  ```bash
  git archive --format=tar HEAD > repo.tar
  ```
- **Simulate a push without performing it:**  
  ```bash
  git push --dry-run
  ```

---

### Notes:
- Replace `<file-path>` with the actual path of the file.
- Replace `<commit-hash>` with the SHA of the commit.
- Use these commands cautiously, especially `git clean`, `git reset`, or `git push -f`, as they may cause irreversible changes.

This updated structure ensures consistency, readability, and optimal organization for advanced Git users. Let me know if you'd like further adjustments!
