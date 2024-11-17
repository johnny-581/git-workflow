# git-workflow

## Before making any changes
Always pull the latest changes from the remote repository before starting new work. 
git fetch downloads changes, but does not merge:
```
git fetch origin
git log origin/main
```
```
git checkout main
git merge origin/main
```
Equivalently, git pull downloads changes and merges:
```
git checkout main
git pull origin main
```
Then create and swich to a new branch. You must make your changes in this new branch, so that later it can be pushed to the remote, reviewed, and merged into the main branch:
```
git branch <branch-name>
git checkout <branch-name>
```
OR
```
git checkout -b <branch-name>
```

## Regularly stage and commit your changes
```
git add .
git commit -m "Your commit message"
```

## Keeping Your Branch Up-to-Date
If other collaborators are working on the same project, it’s essential to keep your branch up-to-date with the latest changes from the main branch.
Rebase your branch with main if you want a clean, linear commit history. This applies your changes on top of the latest main branch:
```
git checkout <branch-name>
git rebase main
```
Alternatively, use merge if you prefer preserving the history:
```
git merge main
```
Resolve merge conflicts if they occur during rebasing or merging:
```
git status
# Manually resolve conflicts in your editor
git add <conflicted-files>
git rebase --continue  # If using rebase
git commit             # If using merge
```

## Submitting a pull request
push your branch:
```
git push origin <branch-name>
```
Open a Pull Request (PR) on the remote platform (Git). Accept the PR, the feature branch will be deleted in the process.

## Cleaning Up
Delete branches that have been merged:
```
git checkout main
git branch -d <branch-name>
```
Clean up local stale branches:
```
git fetch --prune
```
