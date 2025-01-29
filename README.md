# Git Workflow

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
git checkout -b <branch-name>
```
Connect a upstream (remote) branch while pushing the new branch for the first time:
```
git push -u origin <branch-name>
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

## Remote Tracking
To see all local and remote branches:
```
git branch -a
```
To see which branch your current branch is tracking, use:
```
git branch -vv
```
To set an upstream (remote) branch:
```
git push -u origin <branch-name>
OR
git branch -u origin/<branch-name> <branch-name>
OR
git branch -u origin/<branch-name>
```
To update your local Git configuration to reflect the default branch in the remote:
```
git remote set-head origin -a
```
To remove a remote:
```
git remote remove origin
```
To add a remote (connect local repository to the remote - github account):
```
git remote add origin <yourRemoteUrl>
git push -u origin main
```
To force replace a local branch with its remote branch:
```
git reset --hard origin/<branch-name>
```

\
\
\
The following workflow is from https://stackoverflow.com/questions/457927/git-workflow-and-rebase-vs-merge-questions:
```
clone the remote repository
git checkout -b my_new_feature
..work and commit some stuff
git rebase master
..work and commit some stuff
git rebase master
..finish the feature, commit
git rebase master
git push # May need to force push
...submit PR, wait for a review, make any changes requested for the PR
git rebase master
git push # Will probably need to force push (-f), due to previous rebases from master
...accept the PR, most likely also deleting the feature branch in the process
git checkout master
git branch -d my_new_feature
git remote prune origin
```
