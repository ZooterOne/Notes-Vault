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
git status
```

display the state of the working directory.

```
git log
```

display the commit history.

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