## Setup

[https://github.com/github/gitignore](https://github.com/github/gitignore)

repository of various gitignore files.

```
gh auth login
```

login to github.

```
git config [--global] user.name <username>
```

define author's name for current repository.

```
git config [--global] user.email <email>
```

define author's email for current repository.

```
git config --list
```

list configuration

```
git clone <url>
```

clone the repository at url.

___

## Status

```
git status [--short]
```

display the state of the working directory.

```
git log
```

display the commit history.

```
git log -<n>
```

display the last n commit.

```
git log --stat
```

display the commit history with a list of modified files.

```
git log --pretty=oneline
```

display the commit history as one single line per commit.

```
git log --pretty=format:"%H - %an - %ar : %s"
```

display the commit history with a specific format.
 - *%H*: _Commit hash_
 - *%an*: _Author name_
 - *%ar*: _Author relative date_
 - *%s*: _Subject_

```
git log --graph
```

display the commit history as a graph.
 
```
git log --grep="<string>"
```

display the history filtering using string search.

```
git log --author="<string>"
```

display the history filtering using author search.

```
git log --follow <file>
```

show the commits that changed the file.

```
git log branch1...branch2
```

show the commits on branch2 that are not on branch1.

```
git diff branch1...branch2
```

show the diff of what is in branch2 that is not in branch1.

___

## Manage files

```
git add <directory>|<file>
```

stage all changes in a directory or a file.

```
git commit -m "<message>"
```

commit staged changes.

```
git commit --amend
```

commit additional changes to last local commit, replacing the previous commit with a new one.

```
git pull origin
```

fetch current branch and merge it into the local copy.

```
git push origin main
```

push commit to main branch.

```
git diff
```

show unstaged changes.

```
git diff --staged
```

show staged changes.

```
git diff HEAD [<file>]
```

show differences between working directory and last commit.

```
git reset HEAD <file>
```

unstage a staged file.

```
git restore <file>
```

discard changes.

```
git reset <file>
```

unstage file while keeping the changes.

```
git rm <file>
```

delete the file and stage removal.

```
git mv <file> <newfile>
```

move the file to a new location/rename the file.

___

## Branches

```
git branch
```

list all the branches.

```
git checkout -b <branch>
```

create and checkout a new branch.

```
git checkout <branch>
```

checkout a branch.

```
git merge <branch>
```

merge branch into the current branch.

```
git push origin <branch>
```

push commit to branch.

```
git rebase <branch>
```

rebase _branch_ with the current branch, replaying commits from the current branch on top of _branch_. The current branch still needs to be merged to apply changes with `git checkout <branch>` and `git merge <rebased>`.

___

## Remotes

```
git remote show origin
```

show origin remote information.
