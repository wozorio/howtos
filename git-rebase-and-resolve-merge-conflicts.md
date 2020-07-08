# Git - Rebase/Resolve Merge Conflicts

1. Checkout to the feature branch
```bash
git checkout feature/branch
```
1. Pull the latest changes from the remote feature branch
```bash
git pull origin feature/branch
```
1. Pull the latest changes from the master branch
```bash
git pull origin master
```
1. Resolve conflicts if any
```bash
git add -A
git commit -m "Fix merge conflicts"
```
1. Now push the changes to the remote feature branch
```bash
git push origin feature/branch
```
