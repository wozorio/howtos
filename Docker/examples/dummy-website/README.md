# Docker: Dummy website

## Build the image

```bash
docker build --no-cache -t wozorio/dummy-website:1.0.0 .
```

## Push the image to Docker Hub

```bash
docker login
docker image push wozorio/dummy-website:1.0.0
```

## Run container in background mode on Docker

```bash
docker run --name dummy-website -d -p 80:80 wozorio/dummy-website:1.0.0
```
