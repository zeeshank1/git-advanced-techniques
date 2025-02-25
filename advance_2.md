advance and complex git commands list 
ChatGPT said:
Here's a list of advanced and complex Git commands that are often used in scenarios like debugging, repository management, rewriting history, and collaboration:

Branch Management
List remote branches:
bash
Copy
Edit
git branch -r
Create and track a remote branch:
bash
Copy
Edit
git checkout -b <branch-name> origin/<branch-name>
Delete a remote branch:
bash
Copy
Edit
git push origin --delete <branch-name>
Staging and Commit Management
Amend the last commit without changing the message:
bash
Copy
Edit
git commit --amend --no-edit
Change the commit message of the last commit:
bash
Copy
Edit
git commit --amend -m "New commit message"
Undo the last commit but keep changes:
bash
Copy
Edit
git reset --soft HEAD~1
Rebasing and Cherry-Picking
Rebase interactively:
bash
Copy
Edit
git rebase -i HEAD~<n>
Continue rebase after resolving conflicts:
bash
Copy
Edit
git rebase --continue
Abort a rebase:
bash
Copy
Edit
git rebase --abort
Cherry-pick a specific commit:
bash
Copy
Edit
git cherry-pick <commit-hash>
Reset and Revert
Reset a file to the latest commit:
bash
Copy
Edit
git checkout HEAD -- <file>
Revert a specific commit:
bash
Copy
Edit
git revert <commit-hash>
Stash Management
Stash with a custom message:
bash
Copy
Edit
git stash push -m "Message"
Apply a specific stash:
bash
Copy
Edit
git stash apply stash@{<index>}
Pop a stash and remove it from stash list:
bash
Copy
Edit
git stash pop
Logging and Debugging
View detailed log with diffs:
bash
Copy
Edit
git log -p
Show a specific commit:
bash
Copy
Edit
git show <commit-hash>
Find a commit that introduced a bug (binary search):
bash
Copy
Edit
git bisect start
git bisect bad
git bisect good <commit-hash>
Remote and Submodules
Add a submodule:
bash
Copy
Edit
git submodule add <repository-url>
Update all submodules:
bash
Copy
Edit
git submodule update --init --recursive
Remove a submodule:
bash
Copy
Edit
git rm --cached <submodule-path>
rm -rf .git/modules/<submodule-path>
History Rewriting
Squash commits during a rebase:
bash
Copy
Edit
git rebase -i HEAD~<n>
(Mark commits as squash or s during rebase.)
Remove a file from history:
bash
Copy
Edit
git filter-branch --tree-filter 'rm -f <file>' HEAD
Advanced Merging
Perform a merge without auto-committing:
bash
Copy
Edit
git merge --no-commit <branch-name>
Resolve conflicts and continue merge:
bash
Copy
Edit
git add <conflicted-file>
git merge --continue
Patch Management
Create a patch from a commit:
bash
Copy
Edit
git format-patch -1 <commit-hash>
Apply a patch:
bash
Copy
Edit
git apply <patch-file>
Other Advanced Commands
Squash all commits into one:
bash
Copy
Edit
git reset --soft $(git rev-list --max-parents=0 HEAD)
git commit --amend
Clean untracked files and directories:
bash
Copy
Edit
git clean -fd
List all aliases configured:
bash
Copy
Edit
git config --get-regexp alias
Let me know if you need detailed explanations or examples for any of these commands!







You said:
more
ChatGPT said:
Here are additional advanced and complex Git commands and scenarios to enhance your Git mastery:

Advanced Logging
Graphical log with branches and commits:
bash
Copy
Edit
git log --oneline --graph --all --decorate
Log of a specific file:
bash
Copy
Edit
git log -- <file>
Find commits by author:
bash
Copy
Edit
git log --author="Author Name"
Find commits by a keyword in the message:
bash
Copy
Edit
git log --grep="<keyword>"
Show only merge commits:
bash
Copy
Edit
git log --merges
Advanced Diffing
Diff between two commits:
bash
Copy
Edit
git diff <commit1> <commit2>
Diff with ignored whitespace changes:
bash
Copy
Edit
git diff -w
Diff for a specific file between branches:
bash
Copy
Edit
git diff <branch1>..<branch2> -- <file>
Git Configuration
Set a global ignore file:
bash
Copy
Edit
git config --global core.excludesfile ~/.gitignore_global
Show current configuration:
bash
Copy
Edit
git config --list
Change the default text editor for Git:
bash
Copy
Edit
git config --global core.editor "vim"
Advanced Tagging
Create a lightweight tag:
bash
Copy
Edit
git tag <tag-name>
Create an annotated tag:
bash
Copy
Edit
git tag -a <tag-name> -m "Message"
Push tags to the remote:
bash
Copy
Edit
git push origin --tags
Delete a tag locally and remotely:
bash
Copy
Edit
git tag -d <tag-name>
git push origin :refs/tags/<tag-name>
Collaboration and Remote Management
Prune stale branches from remotes:
bash
Copy
Edit
git fetch --prune
Fetch and rebase automatically:
bash
Copy
Edit
git pull --rebase
Show URLs of remote repositories:
bash
Copy
Edit
git remote -v
Set a new remote URL:
bash
Copy
Edit
git remote set-url origin <new-url>
Clone only the latest commit:
bash
Copy
Edit
git clone --depth 1 <repository-url>
Bisect and Debugging
Start bisect with a specific range:
bash
Copy
Edit
git bisect start <bad-commit> <good-commit>
Skip a commit during bisect:
bash
Copy
Edit
git bisect skip
History Rewriting and Cleanup
Remove all local branches except main/master:
bash
Copy
Edit
git branch | grep -v "main" | xargs git branch -d
Prune unreachable commits (garbage collection):
bash
Copy
Edit
git gc --prune=now --aggressive
Revert multiple commits interactively:
bash
Copy
Edit
git rebase -i <base-commit>
Powerful Aliases
Alias for a one-line log graph:
bash
Copy
Edit
git config --global alias.graph "log --oneline --graph --all --decorate"
Alias for checking modified files:
bash
Copy
Edit
git config --global alias.changed "diff --name-only"
Advanced Stash
Stash only specific files:
bash
Copy
Edit
git stash push <file1> <file2>
Create a branch from a stash:
bash
Copy
Edit
git stash branch <branch-name> stash@{<index>}
Advanced Submodules
Clone a repository with submodules:
bash
Copy
Edit
git clone --recurse-submodules <repository-url>
Deinitialize a submodule:
bash
Copy
Edit
git submodule deinit -f <submodule-path>
Update submodules to their latest commit:
bash
Copy
Edit
git submodule update --remote
Temporary Work with Detached HEAD
Checkout a specific commit temporarily:
bash
Copy
Edit
git checkout <commit-hash>
Create a branch from a detached HEAD:
bash
Copy
Edit
git checkout -b <new-branch-name>
Advanced Fetching
Fetch a specific branch only:
bash
Copy
Edit
git fetch origin <branch-name>
Fetch and checkout a remote branch:
bash
Copy
Edit
git fetch origin <branch-name> && git checkout <branch-name>
Miscellaneous Advanced Commands
Show files ignored by .gitignore:
bash
Copy
Edit
git status --ignored
Find the root directory of the repository:
bash
Copy
Edit
git rev-parse --show-toplevel
Create a bare repository:
bash
Copy
Edit
git init --bare
View tree structure of a commit:
bash
Copy
Edit
git ls-tree -r <commit-hash>
