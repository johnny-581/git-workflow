# git-workflow

## fetch then merge is equivalent to pull
### git fetch downloads changes, but does not merge
```
git fetch origin
git log origin/main
```
```
git checkout main
git merge origin/main
```
### git pull downloads changes and merges
```
git pull origin main
```


## Before you make any changes:
make sure you pull the latest changes from the remote repository:  
```
git fetch origin main
git checkout main
git pull origin main
```
Then create and swich to a new branch. You must make your changes in this new branch, so that later it can be reviewed and merged into the main branch:
```
git branch <your_branch>
git checkout <your_branch>
``` 
merge the local main with your branch:
```
git merge main
```

## Regularly stage, commit, and push your changes
```
git add .
git commit -m "Your commit message"
git push origin <your_branch>
```
Replace "Your commit message" with a brief, informative description of the changes included in the commit.
