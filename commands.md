## 1. Using Reflog to Recover Lost Commits  
Reflog records all actions in your Git repository.  
```bash
git reflog
```

---

## 2. Staging and Commit Management  

### a. Amend the Last Commit Without Changing the Message  
Modify the last commit without altering its message.  
```bash
git commit --amend --no-edit
```

### b. Change the Commit Message of the Last Commit  
Edit the last commit's message.  
```bash
git commit --amend -m "New commit message"
```

### c. Undo the Last Commit but Keep Changes  
Remove the last commit, preserving changes in the staging area.  
```bash
git reset --soft HEAD~1
```

---

## 3. Patch Management  

### a. Create a Patch from a Commit  
Generate a patch file for a specific commit.  
```bash
git format-patch -1 <commit-hash>
```

### b. Apply a Patch  
Apply changes from a patch file.  
```bash
git apply <patch-file>
```

---

## 4. Squash All Commits into One  
Combine all commits in the branch into a single commit.  
```bash
git reset --soft $(git rev-list --max-parents=0 HEAD)
git commit --amend
```

---

## 5. Clean Untracked Files and Directories  
Remove untracked files and directories from your working directory.  
```bash
git clean -fd
```

---

## 6. List All Configured Aliases  
See all configured aliases in your Git environment.  
```bash
git config --get-regexp alias
```

---

## 7. Graphical Log with Branches and Commits  
View a graphical log of your repository.  
```bash
git log --oneline --graph --all --decorate
```

---

## 8. Create a Bare Repository  
Set up a bare repository for remote sharing or storage.  
```bash
git init --bare
```

---

## 9. View Tree Structure of a Commit  
Display the file tree structure of a specific commit.  
```bash
git ls-tree -r <commit-hash>
```

---

## 10. Interactive Rebase to Squash or Edit Commits  
Interactively squash, edit, or reorder commits.  
```bash
git rebase -i HEAD~<number-of-commits>
