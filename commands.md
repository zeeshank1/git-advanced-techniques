GIT :


git branch : local available branches
git branch -r : remote availanle branches
git commit --all = git add + git commit
git checkout branch = git reset + git reset HEAD

folders :
.git > logs > Head : conatins commit msg with commit info
.git > logs > nefs > remote > origin > master : contains pull/push info
.git > config > : basic configuration

git log --follow -p -- file  :: This will show the entire history of the file (including history beyond renames and with diffs for each change).



gitk path/to/file

gitk [filename]


GIT

Alias :

git config --global alias.add-commit '!git add -A && git commit'

git add-commit -m 'My commit message'

git add -i :: To add untracked files and have other options as well.

git add -u :: To add deleted files for commit.


    

git reset HEAD-1  :: SOFT deleting one commit from remote only

git reset --hard HEAD-1  :: HARD deleting one commit from remote and local


git push origin <branch> -f :: forcefully pushing local branch commits to the Remote branch after commit delete since you are diverted from remote branch and now you have only local branch.


git push origin --delete <branch name>  :: Delete remote branch

git stash show -p        	:: Shows diff of stashed files.
git stash show -p stash@{1}  :: To see an arbitrary stash
git diff stash@{0} master	:: use git diff to compare the stash with any branch.
git diff --name-only stash@{0} master :: To easy find only changed file names.
git diff stash@{0}^!     	:: This compares the stash against the commit it is based on.
