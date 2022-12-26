# Git
This repository is created for practicing the git commands
cmd  prompt - Traditional Command line interface for windows machine.



git log
git checkout <commit#>

git branch
git branch <branch_name>
git checkout -b <new branch>

did some changes in third branch and committed there
git log

compared the branch commits.

Standing on the master branch : git merge <third branch>
git log

we can check out into specific commits as well.

git checkout <commit#>
Head is detached from your lates commit.
git branch

switch branches and create new branches:
git switch <branch_name>
git switch -c <new branch>


git ls-files
Simply deleting from the working dir will not remove the file from the staging file
git rm <file_name> to remove the files from the staging area.

git checkout <file_name>  --> Undoing unstaged changes. Take you last committed status for the file.
git checkout .

git restore .  --> Same as the git checkout . to restore unstaged changes from git 2.23 onwards

git clean -dn --> to remove all the unstaged changes.

after staging the changes : - 
lets try : - 
git reset filename
git checkout filename


git restore --staged <file_name.txt>
git checkout <file_name.txt>
git status

git reset help us to reset the head of our branch
git reset --soft HEAD~1  --> Soft reset to last committed
git log

git reset HEAD~1 --> BY default --> It will change the HEAD to last commit , remove from the stage

The change is still staged.
git ls-files


git reset --hard HEAD~1
git ls-files
git log


##Deleting branches

git branch -D <branch_name> --> force deletion of branches no matters merged or un-merged.
git branch -d <branch_name>





## .gitignore file
We need to mention the filenames which we don't want to track inside this file
However changes made in the .gitignore file is tracked.

*.log
!test.log

foldername/*

git clean -df


##git deep dive

To save uncommitted /unstaged changes and come back to previous commit --> git stash
git stash apply
git stash list --> All the unstaged saved changes
git stash push -m "third feature added" --> It will help us identify the changes with a message
git stash pop 0
git stash drop 0
git stash clear

++ Bringing lost data back using git reflog.

How to remove the latest committed change in a hard way ? --> git reset --hard HEAD~1 , we will move back to one committed change.

git reflog --> rolling back 30 days storage logic 

git reset --hard <ref# from reflog>

Another UC : 
Created a new branch --> Added some change --> Committed there --> Move back to master --> Deleted that branch --> git reflog --> Git checkout to the hash# --> Branch with detached head --> git switch -c feature

In FF merge we are not doing any commit directly in the master branch just moving the head of the master branch .

How to undo the merge..

git reset --hard HEAD~2
Validate with  : git log


Now suppose, there are two commits in feature brach, and when we merge those commits to master we will see 2 diff commits.
To make them into a single commit we can use : git merge -squash feature followed by git commit in the master branch.


++ Not fast forward merge
git merge --no-ff <feature>


++ git rebase

m1 and m2 commit in master --> copied to feature --> f1 and f2 commit in feature --> back to master --> m3 commit in master -->back to feature --> git rebase master

git rebase master

**** Rebasing creates new commits. It can cause sever problems in real world projects.


++ Dealing with merge conflicts
Be in master --> Change the f1 file --> commit it in master --> Go back to feature --> Change the f1 file --> commit it in feature --> go back to master --> git merge feature

git merge --abort
git log --merge
git diff


++ Merge rebase and cherrypick


++ Cherrypick

In master branch --> Do a change in m1 file --> commit this change in master branch --> git checkout -b feature-2 --> create a new feature folder and add file --. commit it in new feature branch --> corrected the m1 file --> do further development in new feature --> commit it --> git log --> switch back to master --> git cherry-pick commit# in newfeaturebranch --> git log --> commit# is different.


++Tags

Lightweight tags
Annotaded tags

git tag --> tag list
git tag <1.0> <commit#>
git show 1.0

git checkout 1.0

git tag -d 1.0 -> Delete a tag

git tag -a 2.0 -m "This is the latest version"




++ Git hub 

git remote add origin <url>
git push origin master

git branch --> Local branch.
git branch -a --> Local and remote tracking branches.
git branch -r --> Remote tracking branhes.

git push origin feature
git branch -a

git ls-remote

Create a new branch in git hub --> Add a file there --> Go to git local console --> git branch -a --> will not see all the remote branches --> git fetch --> Upadate the remote tracking branch w/o merging the local repository. --> git branch -a 


git pull origin master.

in fetaure remote branch  --> Another file added -->  

++Creating local tracking branch
git branch --track feature-remote-local origin/feature-remote
git branch -a


git branch -vv


git remote --> Show remote servers

git branch --delete --remote origin/feature

git push origin --delete feature

Delete remote branch --> Also deletes remote traking branch as well.


git reset --hard HEAD~1
git push origin master
git push --force origin master.
git pull origin master















