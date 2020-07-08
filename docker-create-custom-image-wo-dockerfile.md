# Create a custom Docker image without using a Dockerfile

1. Create a container with the desired base OS image and run it in interactive mode
    ```bash
    docker run -it ubuntu:xenial /bin/bash
    ```
1. Update the local repository, install the app of your choice and clear the cache
    ```bash
    apt update && apt install -y apache2 && apt clean
    ```
1. Exit the running container
    ```bash
    exit
    ```
1. List the containers (including stopped ones) and copy the ID of the container you are working with
    ```bash
    docker ps -a
    ```
1. Commit the changes made to the running container. This will actually generate a new image
    ```bash
    docker commit -m "Install Apache" 4266c1e82301
    ```
1. Check if the new image was properly created and copy its ID
    ```bash
    docker images
    ```
1. Tag the new image with the target repository and image name
    ```bash
    docker image tag 22c3fac57415 wozorio/sandbox:apache2-1.0-ubuntu
    ```
1. Log on to Dokcer Hub
    ```bash
    docker login
    ```
1. Push the new image to Docker Hub
    ```bash
    docker image push wozorio/sandbox:apache2-1.0-ubuntu
    ```
