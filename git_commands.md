# Advanced Git Commands for Power Users

This document contains advanced Git commands categorized by usage, ordered from most to least frequently used by power users. These commands are useful for managing commits, patches, logs, and repositories effectively.

---

## 1. Using Reflog to Recover Lost Commits
Reflog records all actions in your Git repository.  
```bash
git reflog
```

---

## 2. Staging and Commit Management
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

## 3. Patch Management
- **Create a patch from a commit:**  
  ```bash
  git format-patch -1 <commit-hash>
  ```
- **Apply a patch:**  
  ```bash
  git apply <patch-file>
  ```

---

## 4. Squash All Commits into One
Combine all commits into a single commit.  
```bash
git reset --soft $(git rev-list --max-parents=0 HEAD)
git commit --amend
```

---

## 5. Clean Untracked Files and Directories
Remove untracked files and directories.  
```bash
git clean -fd
```

---

## 6. Aliases and Graphical Logs
- **List all configured aliases:**  
  ```bash
  git config --get-regexp alias
  ```
- **Graphical log with branches and commits:**  
  ```bash
  git log --oneline --graph --all --decorate
  ```

---

## 7. Bare Repository
Create a bare repository (used for remote repositories or central storage).  
```bash
git init --bare
```

---

## 8. View Tree Structure of a Commit
See the file tree of a specific commit.  
```bash
git ls-tree -r <commit-hash>
```

---

## 9. Cherry-Pick a Commit
Apply a specific commit from one branch to another.  
```bash
git cherry-pick <commit-hash>
```

---

## 10. Stash Specific Files
Stash only specific files instead of all changes.  
```bash
git stash push -m "message" <file-path>
```

---

## 11. Bisect
Find the commit that introduced a bug using binary search.  
```bash
git bisect start
git bisect bad
git bisect good <commit-hash>
```

---

## 12. Show Only Merge Commits
List all merge commits in the repository.  
```bash
git log --merges
```

---

## 13. Blame with Line Range
Show who last modified specific lines of a file.  
```bash
git blame -L <start>,<end> <file-path>
```

---

## 14. Prune Remote Tracking Branches
Remove references to branches that no longer exist on the remote.  
```bash
git remote prune origin
```

---

## 15. Sparse Checkout
Checkout only specific files or directories from a repository.  
```bash
git sparse-checkout init
git sparse-checkout set <file-or-directory>
```

---

## 16. Patch Staging
Stage specific parts of a file interactively.  
```bash
git add -p
```

---

## 17. Show Commit Content
Show the content of a commit in a detailed format.  
```bash
git show <commit-hash>
```

---

## 18. Worktree
Work with multiple working directories from a single repository.  
```bash
git worktree add <path> <branch>
```

---

## 19. Squash Commits During Merge
Combine commits into one during a merge.  
```bash
git merge --squash <branch>
```

---

## 20. Undo Last Push
Undo the last push without removing changes locally.  
```bash
git push -f origin HEAD^
```

---

## 21. Detect and Fix Whitespace Issues
Show and remove whitespace errors in files.  
```bash
git diff --check
git apply --whitespace=fix
```

---

## 22. Archive Repository
Create a tar or zip archive of the repository.  
```bash
git archive --format=tar HEAD > repo.tar
```

---

## 23. Rename a Branch Locally and Remotely
Rename a branch and update the remote repository.  
```bash
git branch -m <old-name> <new-name>
git push origin --delete <old-name>
git push origin <new-name>
```

---

## 24. Track Down Corrupted Objects
Find and fix corrupted objects in the repository.  
```bash
git fsck
```

---

## 25. Filter Branch (Rewrite History)
Remove sensitive data or modify commits in history.  
```bash
git filter-branch --force --index-filter \
'git rm --cached --ignore-unmatch <file>' \
--prune-empty --tag-name-filter cat -- --all
```

---

## 26. Restore File Permissions
Ensure file permissions are correctly restored in the repository.  
```bash
git update-index --chmod=+x <file-path>
```

---

## 27. Git Credentials
Store and manage Git credentials.  
```bash
git config credential.helper store
```

---

## 28. Dry Run Push
Simulate a push without actually performing it.  
```bash
git push --dry-run
```

---

## 29. List Stash Details
View detailed information about stash entries.  
```bash
git stash list
git stash show -p <stash@{n}>
```

---

### Notes:
- Replace `<file-path>` with the actual path of the file.
- Replace `<commit-hash>` with the SHA of the commit.
- Use these commands cautiously, especially `git clean`, `git reset`, or `git push -f`, as they may cause irreversible changes.

This guide helps advanced users navigate Git's powerful commands efficiently.


# Advanced Git Commands for Power Users  

This document lists advanced Git commands, ordered by usage, categorized for better understanding.  
Apologies for the earlier formatting errors; this version is now properly structured.  

---

## 📋 Copy All Commands  

Click the button below to copy all Git commands at once.  

```bash
# 1. Using Reflog to Recover Lost Commits
git reflog

# 2. Staging and Commit Management
## a. Amend the Last Commit Without Changing the Message
git commit --amend --no-edit

## b. Change the Commit Message of the Last Commit
git commit --amend -m "New commit message"

## c. Undo the Last Commit but Keep Changes
git reset --soft HEAD~1

# 3. Patch Management
## a. Create a Patch from a Commit
git format-patch -1 <commit-hash>

## b. Apply a Patch
git apply <patch-file>

# 4. Squash All Commits into One
git reset --soft $(git rev-list --max-parents=0 HEAD)
git commit --amend

# 5. Clean Untracked Files and Directories
git clean -fd

# 6. List All Configured Aliases
git config --get-regexp alias

# 7. Graphical Log with Branches and Commits
git log --oneline --graph --all --decorate

# 8. Create a Bare Repository
git init --bare

# 9. View Tree Structure of a Commit
git ls-tree -r <commit-hash>

# 10. Interactive Rebase to Squash or Edit Commits
git rebase -i HEAD~<number-of-commits>

# 11. Show the Author of Each Line in a File
git blame <file-name>

# 12. Rename a Branch
git branch -m <new-branch-name>

# 13. Cherry-Pick a Commit
git cherry-pick <commit-hash>

# 14. Stash Changes and Apply Them Later
git stash
git stash


Here are additional advanced and complex Git commands and scenarios to enhance your Git mastery:

---

### **Advanced Logging**
31. **Graphical log with branches and commits:**
    ```bash
    git log --oneline --graph --all --decorate
    ```
32. **Log of a specific file:**
    ```bash
    git log -- <file>
    ```
33. **Find commits by author:**
    ```bash
    git log --author="Author Name"
    ```
34. **Find commits by a keyword in the message:**
    ```bash
    git log --grep="<keyword>"
    ```
35. **Show only merge commits:**
    ```bash
    git log --merges
    ```

---

### **Advanced Diffing**
36. **Diff between two commits:**
    ```bash
    git diff <commit1> <commit2>
    ```
37. **Diff with ignored whitespace changes:**
    ```bash
    git diff -w
    ```
38. **Diff for a specific file between branches:**
    ```bash
    git diff <branch1>..<branch2> -- <file>
    ```

---

### **Git Configuration**
39. **Set a global ignore file:**
    ```bash
    git config --global core.excludesfile ~/.gitignore_global
    ```
40. **Show current configuration:**
    ```bash
    git config --list
    ```
41. **Change the default text editor for Git:**
    ```bash
    git config --global core.editor "vim"
    ```

---

### **Advanced Tagging**
42. **Create a lightweight tag:**
    ```bash
    git tag <tag-name>
    ```
43. **Create an annotated tag:**
    ```bash
    git tag -a <tag-name> -m "Message"
    ```
44. **Push tags to the remote:**
    ```bash
    git push origin --tags
    ```
45. **Delete a tag locally and remotely:**
    ```bash
    git tag -d <tag-name>
    git push origin :refs/tags/<tag-name>
    ```

---

### **Collaboration and Remote Management**
46. **Prune stale branches from remotes:**
    ```bash
    git fetch --prune
    ```
47. **Fetch and rebase automatically:**
    ```bash
    git pull --rebase
    ```
48. **Show URLs of remote repositories:**
    ```bash
    git remote -v
    ```
49. **Set a new remote URL:**
    ```bash
    git remote set-url origin <new-url>
    ```
50. **Clone only the latest commit:**
    ```bash
    git clone --depth 1 <repository-url>
    ```

---

### **Bisect and Debugging**
51. **Start bisect with a specific range:**
    ```bash
    git bisect start <bad-commit> <good-commit>
    ```
52. **Skip a commit during bisect:**
    ```bash
    git bisect skip
    ```

---

### **History Rewriting and Cleanup**
53. **Remove all local branches except main/master:**
    ```bash
    git branch | grep -v "main" | xargs git branch -d
    ```
54. **Prune unreachable commits (garbage collection):**
    ```bash
    git gc --prune=now --aggressive
    ```
55. **Revert multiple commits interactively:**
    ```bash
    git rebase -i <base-commit>
    ```

---

### **Powerful Aliases**
56. **Alias for a one-line log graph:**
    ```bash
    git config --global alias.graph "log --oneline --graph --all --decorate"
    ```
57. **Alias for checking modified files:**
    ```bash
    git config --global alias.changed "diff --name-only"
    ```

---

### **Advanced Stash**
58. **Stash only specific files:**
    ```bash
    git stash push <file1> <file2>
    ```
59. **Create a branch from a stash:**
    ```bash
    git stash branch <branch-name> stash@{<index>}
    ```

---

### **Advanced Submodules**
60. **Clone a repository with submodules:**
    ```bash
    git clone --recurse-submodules <repository-url>
    ```
61. **Deinitialize a submodule:**
    ```bash
    git submodule deinit -f <submodule-path>
    ```
62. **Update submodules to their latest commit:**
    ```bash
    git submodule update --remote
    ```

---

### **Temporary Work with Detached HEAD**
63. **Checkout a specific commit temporarily:**
    ```bash
    git checkout <commit-hash>
    ```
64. **Create a branch from a detached HEAD:**
    ```bash
    git checkout -b <new-branch-name>
    ```

---

### **Advanced Fetching**
65. **Fetch a specific branch only:**
    ```bash
    git fetch origin <branch-name>
    ```
66. **Fetch and checkout a remote branch:**
    ```bash
    git fetch origin <branch-name> && git checkout <branch-name>
    ```

---

### **Miscellaneous Advanced Commands**
67. **Show files ignored by `.gitignore`:**
    ```bash
    git status --ignored
    ```
68. **Find the root directory of the repository:**
    ```bash
    git rev-parse --show-toplevel
    ```
69. **Create a bare repository:**
    ```bash
    git init --bare
    ```
70. **View tree structure of a commit:**
    ```bash
    git ls-tree -r <commit-hash>
    ```

---

These commands cover a variety of advanced Git scenarios. Let me know if you need details or specific use cases for any of them!
