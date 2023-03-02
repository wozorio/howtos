# Git - Commit your changes or stash them before you can merge

You can't merge with local modifications. Git protects you from losing potentially important changes. To resolve this, follow the setps below:

1. Store your changes temporarily in the stash and removes them from the working directory
    ```
    git commit -m "My message"
    git stash
    ```
1. Restore the changes which you have stored in the stash (the --index option is useful to make sure that staged files are still staged)
    ```
    git pull <remote name> <remote branch name> (or) switch branch (git checkout)
    git stash apply --index
    ```
