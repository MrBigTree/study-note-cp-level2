# GIT and GITHUB

## …or create a new repository on the command line
echo "# personal-portfolio" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin git@github.com:MrBigTree/personal-portfolio.git
git push -u origin main

## …or push an existing repository from the command line
git remote add origin git@github.com:MrBigTree/personal-portfolio.git
git branch -M main
git push -u origin main


## Commands related to a remote repository:
git clone git@github.com:USER-NAME/REPOSITORY-NAME.git
git push or git push origin main (Both accomplish the same goal in this context)

## Commands related to the workflow:
git add .
git commit -m "A message describing what you have done to make this snapshot different"

## Commands related to checking status or log history
git status
git log

## The basic Git syntax is program | action | destination.
git add . is read as git | add | ., where the period represents everything in the current directory;
git commit -m "message" is read as git | commit -m | "message"; and
git status is read as git | status | (no destination)

