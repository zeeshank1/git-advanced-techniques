# Advanced and Complex Git Commands

This document lists advanced and complex Git commands used for debugging, repository management, rewriting history, and collaboration.

## Branch Management
- **List remote branches:**  
  ```bash
  git branch -r
  ```
- **Create and track a remote branch:**  
  ```bash
  git checkout -b <branch_name> origin/<branch_name>
  ```
- **Delete a remote branch:**  
  ```bash
  git push origin --delete <branch_name>
  ```

## Staging and Commit Management
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

## Rebasing and Cherry-Picking
- **Rebase interactively:**  
  ```bash
  git rebase -i HEAD~<num>
  ```
- **Continue rebase after resolving conflicts:**  
  ```bash
  git rebase --continue
  ```
- **Abort a rebase:**  
  ```bash
  git rebase --abort
  ```
- **Cherry-pick a specific commit:**  
  ```bash
  git cherry-pick <commit_hash>
  ```

## Reset and Revert
- **Reset a file to the latest commit:**  
  ```bash
  git checkout HEAD -- <file>
  ```
- **Revert a specific commit:**  
  ```bash
  git revert <commit_hash>
  ```

## Stash Management
- **Stash with a custom message:**  
  ```bash
  git stash push -m "Message"
  ```
- **Apply a specific stash:**  
  ```bash
  git stash apply stash@{<num>}
  ```
- **Pop a stash and remove it from stash list:**  
  ```bash
  git stash pop
  ```

## Logging and Debugging
- **View detailed log with diffs:**  
  ```bash
  git log -p
  ```
- **Show a specific commit:**  
  ```bash
  git show <commit_hash>
  ```
- **Find a commit that introduced a bug (binary search):**  
  ```bash
  git bisect start
  git bisect bad
  git bisect good
  ```

## Remote and Submodules
- **Add a submodule:**  
  ```bash
  git submodule add <repository_url>
  ```
- **Update all submodules:**  
  ```bash
  git submodule update --init --recursive
  ```
- **Remove a submodule:**  
  ```bash
  git rm --cached <submodule>
  rm -rf .git/modules/<submodule>
  ```

## History Rewriting
- **Squash commits during a rebase:**  
  ```bash
  git rebase -i HEAD~<num>
  ```
  (Mark commits as `squash` or `s`)
- **Remove a file from history:**  
  ```bash
  git filter-branch --tree-filter 'rm -f <file>' HEAD
  ```

## Advanced Merging
- **Perform a merge without auto-committing:**  
  ```bash
  git merge --no-commit <branch>
  ```
- **Resolve conflicts and continue merge:**  
  ```bash
  git add <file>
  git merge --continue
  ```

## Patch Management
- **Create a patch from a commit:**  
  ```bash
  git format-patch -1 <commit_hash>
  ```
- **Apply a patch:**  
  ```bash
  git apply <patch_file>
  ```

## Other Advanced Commands
- **Squash all commits into one:**  
  ```bash
  git reset --soft $(git rev-list --max-parents=0 HEAD)
  git commit --amend
  ```
- **Clean untracked files and directories:**  
  ```bash
  git clean -fd
  ```
- **List all aliases configured:**  
  ```bash
  git config --get-regexp alias
  ```

## Additional Advanced Git Commands

### Advanced Logging
- **Graphical log with branches and commits:**  
  ```bash
  git log --oneline --graph --all --decorate
  ```
- **Log of a specific file:**  
  ```bash
  git log -- <file>
  ```
- **Find commits by author:**  
  ```bash
  git log --author="Author Name"
  ```
- **Find commits by a keyword in the message:**  
  ```bash
  git log --grep="keyword"
  ```
- **Show only merge commits:**  
  ```bash
  git log --merges
  ```

### Advanced Diffing
- **Diff between two commits:**  
  ```bash
  git diff <commit1> <commit2>
  ```
- **Diff with ignored whitespace changes:**  
  ```bash
  git diff -w
  ```
- **Diff for a specific file between branches:**  
  ```bash
  git diff <branch1>..<branch2> -- <file>
  ```

### Git Configuration
- **Set a global ignore file:**  
  ```bash
  git config --global core.excludesfile ~/.gitignore_global
  ```
- **Show current configuration:**  
  ```bash
  git config --list
  ```
- **Change the default text editor for Git:**  
  ```bash
  git config --global core.editor "vim"
  ```

### Advanced Tagging
- **Create a lightweight tag:**  
  ```bash
  git tag <tag_name>
  ```
- **Create an annotated tag:**  
  ```bash
  git tag -a <tag_name> -m "Message"
  ```
- **Push tags to the remote:**  
  ```bash
  git push origin --tags
  ```
- **Delete a tag locally and remotely:**  
  ```bash
  git tag -d <tag_name>
  git push origin :refs/tags/<tag_name>
  ```

### Collaboration and Remote Management
- **Prune stale branches from remotes:**  
  ```bash
  git fetch --prune
  ```
- **Fetch and rebase automatically:**  
  ```bash
  git pull --rebase
  ```
- **Show URLs of remote repositories:**  
  ```bash
  git remote -v
  ```
- **Set a new remote URL:**  
  ```bash
  git remote set-url origin <new_url>
  ```
- **Clone only the latest commit:**  
  ```bash
  git clone --depth 1 <repository_url>
  ```

### History Rewriting and Cleanup
- **Remove all local branches except main/master:**  
  ```bash
  git branch | grep -v "main" | xargs git branch -d
  ```
- **Prune unreachable commits (garbage collection):**  
  ```bash
  git gc --prune=now --aggressive
  ```
- **Revert multiple commits interactively:**  
  ```bash
  git rebase -i <commit_hash>
  ```

### Powerful Aliases
- **Alias for a one-line log graph:**  
  ```bash
  git config --global alias.graph "log --oneline --graph --all --decorate"
  ```
- **Alias for checking modified files:**  
  ```bash
  git config --global alias.changed "diff --name-only"
  ```

### Miscellaneous Advanced Commands
- **Show files ignored by `.gitignore`:**  
  ```bash
  git status --ignored
  ```
- **Find the root directory of the repository:**  
  ```bash
  git rev-parse --show-toplevel
  ```
- **Create a bare repository:**  
  ```bash
  git init --bare
  ```
- **View tree structure of a commit:**  
  ```bash
  git ls-tree -r <commit_hash>
  ```
