# Docker Volume Persistance, Docker Compose

In this project, I'll demonstrate how to persist data using Docker Volumes, through Docker Compose.

## Prerequisites

- Docker installed on your local machine
- Basic understanding of Docker

## Objectives

- Writing a `docker-compose.yml` file to define a multi-container application.
- Usage of Docker Compose.
- Understand Docker Volumes for data persistence.
- Run a containerized application with persistent storage.
- Port mapping to access containerized application from the host machine.

## Architecture

![architecture](./architecture.png)

## Steps

### Create a `docker-compose.yml` file

### Start the application

- Run the application using Docker Compose

  ```sh
  docker-compose up -d
  ```

- Since we are using official image Docker pulls it first time only.
- Creates a named volume `blog-data` for SQLite database.
- Installs flask dependencies inside the container.
- Starts the application on port 5000 inside the container and maps it to port 5000 on the host machine.

![Docker Compose Up](image.png)

### Verify Container is running

```sh
docker ps
```

![Running Container](image-1.png)

### Access the application

- Open your web browser and navigate to: `http://localhost:5000`

![Home Page](./home-page.png)

### Test the data persistency

#### Create a new blog post

- Click "Create New Post" button
- Fill in the form:
  - - Title: "My First Docker Post"
  - Author: "Your Name"
  - Content: "Testing Docker volume persistence!"
- Click "Publish Post"

![Blog Post](./blog-post.png)

#### Stop and Remove the container

```sh
docker compose down
```

- This removes the container but keeps the volume data.

#### Restart the Application

```sh
docker compose up -d
```

#### Verify Data Persisted

Visit http://localhost:5000 again - your blog post should still be there!

### Inspect the Volume

```sh
docker volume ls
```

![Volume](image-3.png)

### Check the logs

```sh
docker compose logs -f blog-app
```

![Logs](image-2.png)

### Stop the Application

```sh
docker compose down
```

#### Stop and Remove the Volume and Data

```sh
docker compose down -v
```

## Outcomes

- Writing docker-compose.yml.
- Using Docker Compose to run an application.
- Using Docker volumes for persistent storage.
- Mounting local code into containers for development.
- Port mapping for accessing containerized web applications.
- Debugging containerized applications using logs.
- Understanding the difference between container filesystem and volumes.

## Author

- [K Subramanyeshwara](https://github.com/ksubramanyeshwara) - Devops and Cloud Engineer.
