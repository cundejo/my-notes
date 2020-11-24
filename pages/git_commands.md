---
title: GIT Commands
---

##
```
git checkout -b HCM- upstream/release
git checkout -b HCM- upstream/master

# create branch from master
git checkout -b branch_name master

# delete a branch
git branch -D branch_name
git push origin :branch_name
git fetch --all --prune

# checkout remote branch to local
git checkout -b branch_name origin/branch_name

# merge
git merge origin/master

# rebase
git rebase origin/master

# delete untracked files and directories
git clean -fd

# unstage all the fields
git reset --hard

# remove all from stash
git stash clear

# force to ask password again
git config credential.helper store

# define user and email globally
git config --global user.name "Oliver Sosa"
git config --global user.email "cundejo85@gmail.com"

# Rename remote and add new one
git remote rename origin upstream
git remote add origin URL_DE_TU_FORK
git remote set-url --push upstream no_push
```
