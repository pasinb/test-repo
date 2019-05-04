# Terminology
**remote**: A central server where all team members push and pull codes from. Github is an example of remote hosting service. When you cloned a repo, there will be one default remote named **origin**

**branch**: A different versions of development. When a repo is created there will be one branch named **master**. We often have multiple branch like "master", "develop", "test-some-potentially-breaking-shits". Branch can be local (existing only on user's computer) or you set its upstream branch to sync with specific remote branch.

**commit**: A version of the code. A commit is created after some changes to the code, it often have meaningful names like "Add x feature", "Delete unused file"

# Commonly used commands

## git status

Show working tree status

## git add

Add files to be staged for next commit

Example usage:
```
git add .
```
Add all files in current folder + subfolders, usually run on repository's root folder

## git commit

Create a new commit

Example usage:
```
git commit -m "commit msg"
```
Create new commit named "commit msg"
```
git commit --amend
```
Modify the last commit

## git push [remote] [branch]

Push code to remote

Example usage:
```
git push
```
Push all branches to its upstream breanch
```
git push origin master
```
Push current branch to master branch in origin

## git fetch

Download code from remote

## git merge

MERGE

## git rebase

REBASE

## git pull

Shorthand for `git fetch` then `git merge`

## git branch

See available branches

## git checkout

Switch to new branch

Example usage:
```
git checkout develop
```
Switch to a new branch named "develop"
```
git checkout -b develop
```
Creates a new local branch named "develop" based on current branch then switch to that branch

# Common workflow

## Clone new repo then modify stuff then push

```
git clone git@github.com:pasinb/test-repo.git
cd test-repo
<modify some shit>
git add .
git commit -m "New commit message"
git push
```

## Fetch then merge conflicts before pushing

Sometimes when pushing, git will show some "fetch first" error because someone pushed their shit before you did
```
git fetch
git merge
```
Usually merge can be done automatically, if automatic merge is successful, a new commit will be created and you can just `git push` - otherwise, see below

```
git status
```
git status will show list of files with conflict(s)

git will mark the conflicted part of the file with a conflict marker

for example, if you change a line `Member list: A, B, C` to `Member list: A, B, C, D` and someone modified the exact same line to `Member list: A, B, C, H`, git will mark the file like this:
```
<<<<<<< HEAD
Member list: A, B, C, D
=======
Member list: A, B, C, H
>>>>>>> refs/remotes/origin/master
```
in this example this chunk of code can be changed to
```
Member list: A, B, C, D, H
```

Once all conflicts are fixed:
```
git add .
git commit -m "Resolve merge conflicts by combining added members from both commits"
git push
```

## Create a new local branch named "newbranch" then push this branch to remote
```
git checkout -b newbranch
git push -u origin newbranch
```

## Merge branch "branchB" into branch "branchA"

```
<fetch / pull from remote as necessary>
git checkout branchA
git merge branchB
git push
```

## Rebase

TODO