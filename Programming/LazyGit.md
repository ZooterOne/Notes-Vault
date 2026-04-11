# LazyGit Tutorial

## Initialize the repo on the "server"

```
mkdir -p ./GitServer/ZootRepo.git
cd ./GitServer/ZootRepo.git
git init --bare
```

## Clone the repo

```
cd ~/Documents
git clone ~/Documents/GitServer/ZootRepo.git
```

## Run lazygit

```
cd ZootRepo
git config user.name ZooterOne
git config user.email ZooterOne@Zoot.com
lazygit
```

## Basic commands

 - `<-`, `->`, `tab` or `1`-`5` to change tabs.
 - `[` and `]` to change tab within a section.
 - Mouse to navigate.
 - `p` to pull.
 - `?` for help.
 - `q` to quit.

## Make initial commit

```
echo "This is the first file." > FirstFile.txt
```

Under **Section [2]** (files) `space` to stage changes or `a` to stage all. `c` to commit with message `Initial commit.`. `P` to push.

## Create branch

Under **Section [3]** (branches) `n` to create a new branch `T123-NewFeature`.

## Make changes and push

```
echo "This is the second file." > SecondFile.txt
lazygit
```

Under **Section [2]** (files) `space` to stage changes or `a` to stage all. `c` to commit with message `T123: New feature.`. `P` to push.

## Switch branch

Under **Section [3]** (branches) `c` to checkout branch `master`.

## Merge branch

Under **Section [3]** (branches) highlight branch `T123-NewFeature` and `M` to merge to current branch. Select appropriate merge method. `ls` on terminal to check changes are there. `P` to pull.

## Delete branch

Under **Section [3]** (branches) highlight branch `T123-NewFeature` and `d` to delete the branch. Select `local and remote`.

## Discard changes

```
echo "More stuffs." >> SecondFile.txt
```

Check state with `more SecondFile.txt`. Under **Section [2]** (files) `d` to discard changes. Check state with `more SecondFile.txt`.

## Revert commit

```
echo "Do not commit." >> SecondFile.txt
```

Under **Section [2]** (files) `space` to stage changes and `c` to commit with message `I said to not commit.`. Under **Section [4]** (commits) highlight the last commit and `z` to undo commit. Under **Section [2]** (files) `d` to discard changes.

## Cherry pick

Under **Section [3]** (branches) `n` to create a new branch `T234-NewFeature`.

```
echo "T234: New line." >> SecondFile.txt
```

Under **Section [2]** (files) `space` to stage changes and `c` to commit with message `T234: New feature.` then `P` to push.

Back to `master` with `c`.

Under **Section [3]** (branches) go inside `T234-NewFeature` and highlight the commit to cherry pick. `C` to copy the commit.

Under **Section [4]** (commits) `V` to paste the commit and `P` to pull.

## Cherry pick with conflicts

Under **Section [3]** (branches) `n` to create a new branch `T345-ConflictingFeature`.

```
echo "T345: New line." >> SecondFile.txt
```

Under **Section [2]** (files) `space` to stage changes and `c` to commit with message `T345: New feature.`.

Back to `master` with `c`.

```
echo "New line." >> SecondFile.txt
```

Check state with `more SecondFile.txt`.

Under **Section [3]** (branches) go inside `T345-ConflictingFeature` and highlight the commit to cherry pick. `C` to copy the commit.

Under **Section [4]** (commits) `V` to paste the commit. Fix the conflicts. Approve and `P` to pull.

## Stash changes

```
echo "Some new stuffs." >> SecondFile.txt
```

Under **Section [2]** (files) `s` to stash changes. Under **Section [5]** (stash) `Enter` to apply the stash, `d` to delete the stash (drop) and `g` to apply the changes & delete the stash (pop).
