# Git - Create Pull Requests

1. Switch to the master branch
   ```bash
   git checkout master
   ```
1. Update the local repository
   ```bash
   git pull origin master
   ```
1. Create a new feature branch and switch to it
   ```bash
   git checkout -b feature/JIRA-1234-feature-branch-description
   ```
1. Confirm if the new feature branch is ready to be used
   ```bash
   git branch
   git status
   ```
1. Do the stuff you have to do (introduce new features, bug fixes, whatever, etc)...

1. Add modified files to the staging area
   ```bash
   git add -A (to add all modified files)
   Or
   git add <file_name> (to add individual files)
   ```
1. Commit the changes
   ```bash
   git commit -m "JIRA-1234: Add tags to the resources"
   ```
1. Push the changes
   ```bash
   git push origin feature/JIRA-1234-feature-branch-description
   ```
1. Log on to GitHub and create a pull request  
   https://github.com/wozorio/docs/pulls

1. Switch back to the master branch
   ```bash
   git checkout master
   ```
