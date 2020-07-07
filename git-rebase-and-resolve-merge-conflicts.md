# Git - Rebase/Resolve Merge Conflicts

1. Checkout to the feature branch\
`git checkout feature/branch`

1. Pull the latest changes from the remote feature branch\
`git pull origin feature/branch`

1. Pull the latest changes from the remote master branch\
`git pull origin master`

1. Resolve conflicts if any\
`git add -A`\
`git commit -m "Fix merge conflicts"`

1. Now push\
`git push origin feature/branch`
