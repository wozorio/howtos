# Git - Create Pull Requests

1. Switch to the master branch\
`git checkout master`

1. Update the local repository\
`git pull origin master`

1. Create a new feature branch and switch to it\
`git checkout -b feature/JIRA-1234-feature-branch-description`

1. Confirm if the new feature branch is ready to be used\
`git branch`\
`git status`

1. Do the stuff you have to do (introduce features, modify existing stuff, whatever, etc)...

1. Add modified files to the staging area\
`git add -A` (to add all modified files)\
Or\
`git add <file_name>` (to add individual files)

1. Commit the changes\
git commit -m "JIRA-1234: Add tags to the resources"

1. Push the changes\
git push origin feature/JIRA-1234-feature-branch-description

1. Log on to GitHub and create a pull request\
https://github.com/wozorio/docs/pulls

1. Switch back to the master branch\
git checkout master
