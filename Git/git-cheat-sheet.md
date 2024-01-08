# Git Cheat Sheet

1. Set Name & E-mail address in Git config
   ```bash
   git config --global user.name "Wellington Ozorio"
   git config --global user.email "well.ozorio@gmail.com"
   git config --list
   ```
1. Initialize the working directory for a new repository
   ```bash
   git init
   ```
1. Clone a repository to the local machine
   ```bash
   git clone "https://github.com/wozorio/howtos.git"
   ```
1. See which files were modified before being added to the staging area
   ```bash
   git status
   ```
1. Add a specific file to the staging area
   ```bash
   git add <file_name>
   ```
1. Add all modified files to the staging area
   ```bash
   git add -A
   ```
1. Commit changes in the working directory
   ```bash
   git commit -m "Add new module for resource groups"
   ```
1. Push committed changes to the remote repository (origin vs. the branch where your code will be pushed to)
   ```bash
   git pull
   git push -u origin master
   ```
1. View all commits history
   ```bash
   git log
   git log --author="Wellington"
   ```
1. Show the differences between the working directory and the remote repository
   ```bash
   git diff
   ```
1. Show the differences between the working directory and the remote repository (staged files)
   ```bash
   git diff --staged
   ```
1. Ensure the local repository is in sync with the remote repository
   ```bash
   git pull
   ```
