## On github.com : First play on Github.com to understand the need for version control


### Remote: Step-01 : Setup : (central repository on Github.com) 
* Lets go to github.com
* Create an account
* Create a repository with name : mygitplay
* Update readme.md (https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)
* Add the person next to you in the class to be your collaborator (click on setting).
### Remote: Step-02: First file (central repository on Github.com) 
* Create a new file file1.txt
* Commit it.
* Remote: Step-03: Play around : (central repository on Github.com)
* Create a new branch
* Change file1.txt.
* Add a new file file2.txt in this branch.
* Create a PR request to merge it in.
* See the changes in master branch.
* Click on following buttons to see functionality
  * Branches
  * Commits
  * Download URL
  * Collaborators
  * History of files
  * master branch → the goal!
  * Remove the branch you created.










## Local Git on your laptops/computers to see similar functionality as GitHub.com and learn interactions between  local/remote.

### Local: Step-04: Setup
* git --version
* git config --global user.name "your name"
* git config --global  user.email "your email"
* git config --list
### Local: Step-05: Initialize a local repo on your laptop using one of the following
* **Using git clone (day1)**
  * Create a new directory
  * git clone <your_url>
* **Or Initialize a local repo on your laptop using git init (we will do it on day-2)**
  * Create a directory “mygitplay”
  * git init
  * git remote add origin <your-url> ( copy the download URL of your repo above)
  * git pull origin master
  * Check your folder to see if you got all files from central repository.
  * See .git created.
### ## Local: Step-06: Learn to make first local change using (git add, git commit, git status) i the local repositories.
* create a new text file “file3.txt” in the folder.
* git status; git add file3.txt; git status; git commit -m “my first file” file3.txt
* git log -oneline --decorate --graph
* Repeat the process by changing an existing file
* Change file1.txt
* Repeat status/add/commit/log to commit the file1.txt
* git log --oneline --decorate --graph
### ## Local:Step-07: Push these changes to remote github.com repository
* git push origin master
* Go to your github repo and check the new pushed changes.
* Local:Step-08: Local Branches
* git checkout master
* git pull origin master
* git branch “firstlocalbranch”
* git checkout firstlocalbranch
* create file5.txt in firstlocalbranch (use git status, add, commit, status, log commands)
* git checkout master (note file5.txt is not there).
* git checkout firstlocalbranch (file5.txt is there).
### Local:Step-09: Merging local branches (merge firstlocalbranch to master)
* git checkout master
* git pull origin master
* git merge firstlocalbranch (check that file5.txt is in “master” branch now. Yay!!
* Repeat merge::
  * git branch (what branch are you on?)
  * git checkout firstlocalbranch (Go back to first branch)
  * edit file5.txt ((use git status, add, commit, status, log commands)
  * git checkout master (check that edits for file5.txt are not there).
  * git merge firstlocalbranch (check that edits are there for file5.txt)
  * git push origin master
  * git branch -d firstlocalbranch (delete the branch)
## Local:Step-09: Linear development (rebasing : simultaneous changes in multiple branches : master and secondlocalbranch )
* git branch (what branch are you on?)
* git checkout master
* git pull origin master
* git branch secondlocalbranch
* git checkout secondlocalbranch
* Make changes in file5.txt in this new branch (use status, add, commit, status, log commands)
* git checkout master
* Make changes in file4.txt in master (use status, add, commit, status, log commands)
* git checkout secondlocalbranch
* git rebase master (get changes from master in secondlocalbranch).
* git log --oneline --decorate --graph ( to see that commits for secondlocalbranch are in the end)
### Local:Step-09: Push branch to remote
* Git push origin secondlocalbranch:master
* Local:Step-10: Keep local branches always in sync with remote master
* git checkout secondlocalbranch
* git pull --rebase origin master
## Local: Step-11: Resets to discard current changes made locally!
* Various reset options : we use reset to move the local repository and/or staging and/or working directory to a previous commit#
* git checkout master
* git pull origin master
* create a branch “thirdlocalbranch” : git checkout -b “thirdlocalbranch”
* edit file1.txt
* git reset --hard origin/master
* Stage the file1.txt changes by (git add) and repeat the reset command
* Commit the file1.txt (git commit) and repeat the reset command.
* Bonus Points : Try the behavior using “soft” reset. Google search 
### Local: Step-12: Revert a file to a revision
* git log README.md
* git reset <commit-sha> README.md
* Commit and push.
### Local Step-13: Remove a commit from the history (i.e. given commit-sha1, commit-sha2, commit-sha3, remove commit-sha2)
* git checkout master
* git pull --rebase origin master
* git checkout -b branchToRemoveACommit
* git reset --hard <commit-sha1>
* git cherry-pick <commit-sha3>
* git push -f origin <branch>
