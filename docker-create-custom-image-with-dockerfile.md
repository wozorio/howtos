# Create a custom Docker image using a Dockerfile
This is a quick reference guide on how to create custom Docker images using Dockerfiles.

1. Create a file called Dockerfile with the following contents
    ```dockerfile
    # Base OS image to be used
    FROM ubuntu:xenial

    # File Author / Maintainer
    LABEL author="Wellington Ozorio"
    LABEL version="1.0.0"

    # Update the repository sources list
    RUN apt update \
        && apt install -y apache2 \
        && apt clean

    # Copy custom index.html file
    COPY index.html /var/www/html/

    # Expose Apache on port 80
    EXPOSE 80

    # Start Apache as a daemon in foreground mode
    CMD ["apachectl", "-D", "FOREGROUND"]
    ```
1. Build the image\
`docker build -t wozorio/sandbox:apache2-1.0-ubuntu .`

1. Check if the new image was properly created and copy its ID\
`docker images`

1. Verify if a container is successfully created from the new image\
`docker run -d wozorio/sandbox:apache2-1.0-ubuntu`

1. Log on to Dokcer Hub\
`docker login`

1. Push the new image to Docker Hub\
`docker image push wozorio/sandbox:apache2-1.0-ubuntu`
