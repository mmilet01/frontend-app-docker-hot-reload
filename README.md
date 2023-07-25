# Dockerized React Application with Hot Reloading

This project demonstrates how to set up a development environment using Docker that supports hot reloading. We leverage Docker's bind mounts to achieve this. 

## Project description

- Linux OS

Two main lines are inside the docker-compose.yml file.
## The volumes section
- .:/app line creates a bind mount, which syncs the current directory on the host machine with the /app directory inside the Docker container (can be thought of as bidirectional communication).
This means any changes made to the source code on the host machine are immediately reflected inside the Docker container and the application running inside the container can then react to those changes (e.g., by hot-reloading).

- /app/node_modules line which creates a separate, Docker-managed volume for the node_modules directory inside the container.
By specifying /app/node_modules as a Docker volume, we tell Docker to keep the node_modules directory inside the container separate from the bind mount.  
This means when Docker is setting up the bind mount, it won't try to copy the host's node_modules into the container. Instead, the node_modules directory inside the container will remain as it was when the Docker image was built, with all packages installed correctly for the Docker environment.
This is to ensure that the node_modules on the host doesn't overwrite the node_modules inside the Docker container, which may be structured differently depending on the operating system and architecture.
