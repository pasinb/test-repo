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

## git push

Push code to remote

## git fetch

Download code from remote

## git merge

MERGE

## git rebase

REBASE

## git pull

Shorthand for git fetch and git merge

## git branch

See available branches

## git checkout

Switch to new branch

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

## Fetch then merge conflicts before pushing - me

```
git push
<some fancy "fetch first" error because someone pushed their shit before you did>
git fetch
git merge
```
Usually merge can be done automatically (no one is modifying the same file or people modify different section in the same file).
If automatic merge is successful, a new commit will be created and you and just `git push` - otherwise, see below

```
git status
```
git status will show list of files with conflicts

```
<manually fix the conflicted files>



git add .
git commit -m "Resolve merge conflicts"
git push
```