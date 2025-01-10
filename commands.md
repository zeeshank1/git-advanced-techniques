##Using reflog to recover lost commits. <br/>
#Reflog records all actions in your Git repository.<br/>
#git reflog<br/>

Staging and Commit Management
Amend the last commit without changing the message: git commit --amend --no-edit

Change the commit message of the last commit: git commit --amend -m "New commit message"

Undo the last commit but keep changes: git reset --soft HEAD~1


Patch Management
Create a patch from a commit:
git format-patch -1 <commit-hash>

Apply a patch:
git apply <patch-file>


Squash all commits into one:

git reset --soft $(git rev-list --max-parents=0 HEAD)
git commit --amend
Clean untracked files and directories:

git clean -fd
List all aliases configured:
git config --get-regexp alias

Graphical log with branches and commits:
git log --oneline --graph --all --decorate
