# Initial Setup

## download and install git

yeah it takes a bit; it like installs some other things to compile git or something

## one-time git configuration

`git config --global user.name "Your Name"`
`git config --global user.email "YourEmail"`

to print it out to make sure it worked,

`git config --global -l`

## create repository on GitHub

make a new repository, and copy the URL given  
should be something like
- **https://github.com/***UserName***/***RepositoryName***.git**

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

# Common 