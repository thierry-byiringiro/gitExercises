# Initializing the environment
```
touch test{1..4}.md
git add test1.md && git commit -m "chore: Create initial file"
git add test2.md && git commit -m "chore: Create another file"
git add test3.md && git commit -m "chore: Create third and fourth files"
```
# Challenge - Part 1
## Refining Git history
### Missing file fix

```
git add test4.md
git commit --amend -m"chore:adding the fourth file"

```
### Editing commit history
```
git rebase -i --root
reword 85b1ced  chore: Create another file
85b1ced  chore: Create second file

```
### Squashing Commits

```
git rebase -i --root
77e247b  chore: Create initial file
squash 85b1ced  chore: Create second file

```
### Splitting commit 
```
git reset HEAD~2
git add test3.md && git commit -m "chore: Create Third file"
git add test4.md && git commit -m "chore: Create fourth file"

```
### Advanced Squashing


```
git rebase -i --root
pick e22aae3 chore: Create fourth file
squash 9ed3190 chore : Create Third file

```
### Dropping a commit 
#### first creating the file , staging it and commiting it
```
touch unwanted.txt
echo "I am the unwanted file" > unwanted.txt
git add unwanted.txt && git commit -m "Unwanted commit"

```
#### Dropping the unwanted commit
```
git rebase -i --root
drop 0e5286c (origin/dev) Unwanted commit  
pick e22aae3 chore : Create fourth file
pick 9ed3190 chore : Create Third file
pick 85b1ced chore: Create second file
pick 77e247b chore: Create initial file

"After putting drop to the commit i want to drop and then after save"

```
### Reordering Commits
#### before
```
"P" pick e22aae3 chore : Create fourth file
"DD" pick 9ed3190 chore : Create Third file
pick 85b1ced chore: Create second file
pick 77e247b chore: Create initial file
```
#### after
```
pick 9ed3190 chore : Create Third file
pick e22aae3 chore : Create fourth file
pick 85b1ced chore: Create second file
pick 77e247b chore: Create initial file
```

### Cherry-Picking Commits
```
git checkout -b ft/branch
touch test5.md 
echo "TEST5 md" > test5.md
git add test5.md && git commit -m "Implemented test 5"

git checkout dev
git cherry-pick --no-commit 9id3180 
```
### Visualizing the commit history
```
git log --graph
```

### Understanding Reflogs
```
git reflog
```


# Challenge - Part 2
## Branching Basics
### Feature Branch Creation
```
git branch -b ft/new-feature
```
### Working on the Feature Branch
```
touch feature.txt
echo "I am the new functionality file created" > feature.txt
git add feature.txt && git commit -m "Implemented core functionality for new feature"

git checkout dev
touch readme.txt
echo "repository for learning git" > readme.txt
git add readme.txt && git commit -m "Updated project readme"
```
#### Next step is merging the new created branch and the base branch which is dev
### Branch Deletion
```
git branch -d ft/new-feature
```

### Create a brach from a commit 
```
git checkout -b ft/new-branch-from-commit 0e5286c
```

### Branch merging
"Merge the ft/new-branch-from-commit branch into the dev branch "

### Branch Rebasing
"Rebasing is another method to integrate changes from a feature branch. It rewrites your branch history by incorporating its commits on top of the latest commit in the target branch"


```
git checkout ft/new-branch-from-commit
git rebase dev
```

### Renaming Branch

```
git branch -m ft/new-branch-from-commit ft/improved-branch-name
```

### Checking Out Detached HEAD
"A Detached HEAD means you’re not on a branch, but directly on a commit.
You can look around safely, but if you commit changes without creating a branch, they may be lost."
```
git checkout 5dabceca9725c1444eb1db2f4f7d9a3bc5d45a31

```

