```
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

# unstage all the fields
git reset

# remove all from stash
git stash clear
```
