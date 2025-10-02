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


