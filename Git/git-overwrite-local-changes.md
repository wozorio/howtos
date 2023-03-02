# Git - Force pull (overwrite local changes)

1. Download the latest from remote without trying to merge or rebase anything
    ```bash
    git fetch --all
    ```

1. Reset the master branch to what you just fetched. The --hard option changes all the files in your working tree to match the files in origin/master
    ```bash
    git reset --hard origin/master
    ```

1. Pull from the remote repository over to the local copy
    ```bash
    git pull origin master
    ```
