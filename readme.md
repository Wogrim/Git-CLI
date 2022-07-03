# Initial Setup

## download and install git

yeah it takes a bit; it installs some other things to compile git or something

## one-time git configuration

`git config --global user.name "Your Name"`  
`git config --global user.email "YourEmail"`

to print it out to make sure it worked,  
`git config --global -l`

## create repository on GitHub

make a new repository, and copy the URL given  
should be something like  
`https://github.com/UserName/RepositoryName.git`

## "clone" the remote (GitHub) repository (make a copy of it on your computer)

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
something called HEAD keeps track of which local branch you're on (you will see HEAD mentioned in some documentation)

## creating branches and switching to them

to see the branches in your local repository, use  
`git branch`

to create a new branch  
`git branch branchname`

to switch to a branch  
`git checkout branchname`

to create a new branch and switch to it in one command,  
`git checkout -b branchname`

## merging a branch

make your commits first and hopefully you tested your changes...  
then switch to the branch you are merging into, and merge the other branch:  
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

# Commit History

## view commit history

to see commit list for current branch  
`git log`  
for a different branch:  
`git log branchname`
