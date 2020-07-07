# Create a custom Docker image without using a Dockerfile
This is a quick reference guide on how to create custom Docker images without using Dockerfiles.

1. Create a container with the desired base OS image and run it in interactive mode\
`docker run -it ubuntu:xenial /bin/bash`

1. Update the local repository, install the app of your choice and clear the cache\
`apt update && apt install -y apache2 && apt clean`

1. Exit the running container\
`exit`

1. List the containers (including stopped ones) and copy the ID of the container you are working with\
`docker ps -a`

1. Commit the changes made to the running container. This will actually generate a new image\
`docker commit -m "Install Apache" 4266c1e82301`

1. Check if the new image was properly created and copy its ID\
`docker images`

1. Tag the new image with the target repository and image name\
`docker image tag 22c3fac57415 wozorio/sandbox:apache2-1.0-ubuntu`

1. Log on to Dokcer Hub\
`docker login`

1. Push the new image to Docker Hub\
`docker image push wozorio/sandbox:apache2-1.0-ubuntu`
