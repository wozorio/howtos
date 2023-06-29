# Git - Delete all local branches

First, switch to the branch you want to keep, ex: master:

```
git checkout master
```

## Bash

```bash
git branch -D $(git branch)
```

## PowerShell

```powershell
git branch -D $(git branch).Trim()
```
