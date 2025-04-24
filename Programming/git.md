## Setup

[https://github.com/github/gitignore](https://github.com/github/gitignore)

repository of various gitignore files.

```
gh auth login
```

login to github.

```
git config user.name <username>
```

define author's name for current repository.

```
git config user.email <email>
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
git diff HEAD [<file>]
```

show differences between working directory and last commit.

```
git restore <file>
```

discard changes.

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