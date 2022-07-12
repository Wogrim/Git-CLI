# Initial Setup

## download and install git

yeah it takes a bit; it installs some other things to compile git or something

## one-time git configuration

`git config --global user.name "Your Name"`  
`git config --global user.email "YourEmail"`

to print it out to make sure it worked,  
`git config --global -l`

## create repository on GitHub

(must do this on the GitHub website) make a new repository, and copy the URL given  
should be something like  
`https://github.com/UserName/RepositoryName.git`

## clone the remote (GitHub) repository (grabs the main branch)

open PowerShell in the soon-to-be parent folder of where you want your local repository placed, then  
`git clone https://github.com/UserName/RepositoryName.git RepositoryName`

you should now have a folder for your local repository at *RepositoryName*  
git commands relating to this repository need to be done from inside that folder

## alternatively, you can create a local git repository without cloning a remote repository

create the folder for your local repository and open powershell from within that folder  
`git init`  
will initialize the repository; you will need to use  
`git remote add origin https://github.com/UserName/RepositoryName.git`  
to save the reference to the remote repository as *origin*

## make initial commit

if you didn't initially put anything in your repository on GitHub, you can't do much until you make an initial commit

so create a file in your folder: **readme.md** is a good choice because GitHub will show it with formatting on your repository's page (see [Basic Syntax](https://www.markdownguide.org/cheat-sheet/) for formatting)

to add changed files to a commit, use  
`git add .`  
for all files, or  
`git add readme.md`  
just for that specific file

then to make the commit do  
`git commit -m "initial commit"`

and last, push your commit back to the remote repository's main branch  
`git push origin main`

# Branches

the main reason for branches is collaboration, but it's good to practice on solo projects  
something called HEAD keeps track of which local branch you're on  
generally what we want are **tracking branches**, which keep track of which remote branch they correspond to

## using local branches

to see the branches in your local repository, use  
`git branch`

to create a new branch and switch to it (*basebranch* can be omitted to use current branch):  
`git branch branchname basebranch`  
`git switch branchname`  
OR  
`git checkout -b branchname basebranch`

if you have uncommitted changes to a file which you want to undo:    
`git checkout HEAD -- filename`

## merging local branches

(after you've made your commits)  
switch to the branch you are merging into, and merge the other branch:  
`git merge branchname`  

if main had no commits to it after the branch was created, it is an easy **fast-forward** merge  
otherwise it compares changed files for **merge conflicts** (we don't want those)  
ideally there are no conflicts and it advances the master branch automatically to a new **merge commit**  
`git status` to see which files are causing the merge conflict

to fix the merge conflict you open the files and see where the differences are; pick what you want to keep and delete the rest; add the file to the (merge) commit and then  
`git commit`  
(there will be a default commit message for the merge)

you can also try to resolve conflicts with a merge tool  
`git mergetool`

if you're not ready to deal with merge conflicts, you can cancel the merge:
`git merge --abort`

if you merged your branch and don't need it anymore, you can delete it with  
`git branch -d branchname`

## using tracking branches

since we generally want tracking branches, check which of your branches are tracking using  
`git branch -vv`  
(there will be something like *\[origin/branchname]* next to tracking branches; you should have one if you cloned the remote repository or did a checkout)  
if you only have one remote repository, grab another (and set it up for tracking) with  
`git checkout branchname`  
OR  
`git checkout -t origin/branchname`

if you have a local branch that isn't set to track the remote branch it should be in sync with, use  
`git branch -u origin/branchname`

to update your local commit list for remote branches  
`git fetch origin`  
if your local branch's files are not up to date, you must merge them or rebase (which can have conflicts)  
*TODO: GIT MERGE*  
`git rebase origin/branchname`  
OR combine these steps with a pull (it will merge or rebase depending on settings)  
`git pull`

to push your changes on a branch back to the remote branch of the same name  
`git push origin`  
just like we did for our initial commit, or to push to a different branch name  
`git push origin localbranchname:remotebranchname`

# Commit History

## view commit history

to see commit list for current branch  
`git log`  
for a different branch:  
`git log branchname`
