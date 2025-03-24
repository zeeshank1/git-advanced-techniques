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
