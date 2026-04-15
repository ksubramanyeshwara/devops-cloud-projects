# Dockerizing a Static Site

In this project, I'll create a docker image of a static website, run the container locally and push the image to Docker Hub.

## Prerequisites

- Docker installed on your local machine
- Basic understanding of Docker

## Objectives

- Create a Docker image using static site
- Run the container locally
- Push the image to Docker Hub

## Architecture

![architecture](image.png)

## Steps to Run the Project

### Create a Dockerfile

```
# Use official Nginx image as the base image
# Use alpine variant for a smaller image size
FROM nginx:alpine

# Copy the static website files to the Nginx HTML directory
COPY . /usr/share/nginx/html

# Expose port 80 to allow web traffic to the container
EXPOSE 80
```

### Build the Docker Image

Build the image with a custom tag name

```sh
docker build -t ks-portfolio:latest .
```

### Run the Container Locally

Run the container from the image you created.

```sh
docker run -d -p 8080:80 --name ks-portfolio ks-portfolio:latest
```

### Access the Static Site

Open your browser and navigate to:

```sh
http://localhost:8080
```

### Push the Image to Docker Hub

Retag the docker image before push because Docker Hub expect the tagging in `<username>/<repo>:<tag>` this way.

```
docker tag ks-portfolio:latest ksubramanyeshwara/ks-portfolio:1.0.0
```

After retag push the image to the docker hub

```sh
# Enter username and password when prompted
docker login

docker push ksubramanyeshwara/ks-portfolio:1.0.0

# verify it in docker hub
```

### Pull the Image from Docker Hub

```sh
docker pull ksubramanyeshwara/ks-portfolio:1.0.0
```

### Run the Container Locally

Run the container from the image you pulled from Docker Hub.

```sh
docker run -d -p 8080:80 --name ks-portfolio ksubramanyeshwara/ks-portfolio:1.0.0
```

### Access the Static Site

Open your browser and navigate to:

```sh
http://localhost:8080
```

## Outcome

- Created the docker image for the static website.
- Run the container locally and access the website.
- Successfully pushed the image to Docker Hub.
- Verified the image by pulling it and running it locally and accessing it.

## Key Learnings

- Creating Dockerfile for static site using Nginx
- Building and running the docker container locally
- Tagging the image before pushing to Docker Hub
- Pushing the image to Docker Hub
- Pulling the image from Docker Hub

## Resources

- [Docker Documentation](https://docs.docker.com/)
- [Nginx Documentation](https://nginx.org/en/docs/)

## Author

- [K Subramanyeshwara](https://github.com/ksubramanyeshwara) - Devops and Cloud Engineer.
