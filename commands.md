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
