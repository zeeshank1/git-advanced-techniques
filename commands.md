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
```

---

## 11. Show the Author of Each Line in a File  
Display the author and commit details for each line in a file.  
```bash
git blame <file-name>
```

---

## 12. Rename a Branch  
Rename the current branch or a specific branch.  
```bash
git branch -m <new-branch-name>
```

---

## 13. Cherry-Pick a Commit  
Apply changes from a specific commit to your current branch.  
```bash
git cherry-pick <commit-hash>
```

---

## 14. Stash Changes and Apply Them Later  
Temporarily store changes and reapply them later.  
```bash
git stash
git stash apply
```

---

## 15. Find a Specific Commit that Introduced a Bug  
Use binary search to find the commit that introduced an issue.  
```bash
git bisect start
git bisect bad
git bisect good <commit-hash>
```

---

## 16. Create a Tag for a Commit  
Add a tag to a specific commit for easier reference.  
```bash
git tag -a <tag-name> -m "Tag message" <commit-hash>
```

---

## 17. Push Tags to Remote  
Share local tags with the remote repository.  
```bash
git push origin --tags
```

---

## 18. Remove a Remote Branch  
Delete a branch from the remote repository.  
```bash
git push origin --delete <branch-name>
```

---

## 19. Check for Conflicts Before Merging  
Simulate a merge to check for potential conflicts.  
```bash
git merge --no-commit --no-ff <branch-name>
```

---

## 20. Archive a Repository  
Create an archive of the repository for distribution.  
```bash
git archive --format=tar --output=<file-name>.tar <branch-name>


