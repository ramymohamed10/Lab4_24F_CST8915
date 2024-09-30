# Lab 4 - CST8915 Full-stack Cloud-native Development: Introduction to Docker

Welcome to Lab 4 of the **CST8915 Full-stack Cloud-native Development** course. This lab will serve as an introduction to Docker to prepare you for containerizing applications in future labs. By the end of this lab, you will be familiar with Docker’s key concepts and basic commands, as well as able to create and run a simple containerized application.

## Lab Objectives:
- Understand the basics of Docker containers, images, and Dockerfiles.
- Learn how to build and run a Docker container.
- Use Docker commands to manage images and containers.

## Introduction to Docker
### What is Docker?
Docker is an open-source platform that enables developers to automate the deployment of applications inside lightweight, portable containers. These containers bundle the application with all of its dependencies and configurations, ensuring that the application runs consistently across different environments.

Key Concepts of Docker:

- **Containers:** Containers are lightweight, standalone executable packages of software that include everything needed to run the application: code, runtime, system tools, libraries, and settings.
- **Images:** An image is a read-only template used to create Docker containers. It contains everything needed to run an application. When you run a container, Docker uses an image as the base.
- **Dockerfile:** A text file that contains instructions on how to build a Docker image. The Dockerfile defines what goes into the image, including the base operating system, dependencies, environment variables, and the application code.
- **Docker Hub:** A cloud-based registry where Docker images can be stored and shared. You can push images to Docker Hub and pull them from there on different systems or cloud platforms.

**Docker Documentation:** The official Docker documentation is a comprehensive resource that provides detailed explanations, tutorials, and examples: [Docker Documentation](https://docs.docker.com/).

**Docker CLI Cheat Sheet:** This cheat sheet provides a quick reference for frequently used Docker commands: [Docker CLI Cheat Sheet](https://docs.docker.com/get-started/docker_cheatsheet.pdf)

## Install Docker:
### Get Docker Desktop
Docker Desktop is the all-in-one package to build images, run containers, and so much more. Install Docker Desktop using [Get Docker Desktop](https://docs.docker.com/get-started/introduction/get-docker-desktop/) guide which will walk you through the installation process.

If you are using WSL, make sure to integrate Docker Desktop with your WSL environment. Steps:
  - Open Docker Desktop Settings
  - Go to the Resources section, then click on WSL Integration.
  - Ensure that Enable integration with my default WSL distro is checked.
  - Also, make sure Ubuntu (or any other WSL distribution you want Docker to integrate with) is selected.
  - Apply and Restart Docker.
  
  Now that Docker Desktop is integrated with WSL 2, you can manage and run Docker containers in your Ubuntu WSL environment seamlessly. You don’t need to manually install Docker inside Ubuntu, as Docker Desktop takes care of that through WSL 2. You can continue using Docker commands as you would on a native Linux system, but with the performance and convenience of using Docker Desktop on Windows. Read more here: [Docker Desktop WSL 2 backend on Windows](https://docs.docker.com/desktop/wsl/)

## Lab Steps:

### Step 1: Docker Desktop
Complete [Get Docker Desktop Guide (Video Included)](https://docs.docker.com/get-started/introduction/get-docker-desktop/)

### Step 2: Develop with containers
Complete [Develop with containers Guide (Video Included)](https://docs.docker.com/get-started/introduction/develop-with-containers/)

### Step 3: Build and push your first image
Complete [Build and push your first image (Video Included)](https://docs.docker.com/get-started/introduction/build-and-push-first-image/)

### Step 4: Familiarizing with Key Docker Commands
To help you get started with Docker, here is a breakdown of some important commands from the Docker CLI Cheat Sheet that you will use frequently. These commands will help you manage Docker images, containers, and other aspects of your Docker environment. Make sure you try out these commands as you proceed through the lab.

#### Image Management Commands
- Build an Image from a Dockerfile:
  ```
  docker build -t <image_name> .
  ```
  This command creates a Docker image from a Dockerfile in your working directory, and the -t flag is used to name the image.

- Build an Image from a Dockerfile without Cache:
  ```
  docker build -t <image_name> . –no-cache
  ```
  This command builds an image without using the Docker cache. It's useful when you want to ensure a fresh build, especially when dealing with changes in dependencies or code.

- List Local Images:
  ```
  docker images
  ```
  Lists all images available in your local Docker environment.

- Delete an Image:
  ```
  docker rmi <image_name>
  ```
  Removes a Docker image by name or ID from your local repository.

- Search Hub for an Image:
  ```
  docker search <image_name>
  ```
  Searches Docker Hub for publicly available images.

- Pull an Image from Docker Hub:
  ```
  docker pull <image_name>
  ```
  Downloads a Docker image from Docker Hub.

#### Docker Hub Commands
Docker Hub is a cloud-based registry that allows you to store, share, and distribute Docker images. You can push images you’ve built locally to Docker Hub and pull them on other machines or environments.

- Login to Docker Hub:
  ```
  docker login -u <username>
  ```
  Logs you into Docker Hub using your username and password.

- Publish an Image to Docker Hub:
  ```
  docker push <username>/<image_name>
  ```
  Pushes an image from your local repository to Docker Hub.


#### Container Management Commands
- Create and Run a Container:
  ```
  docker run --name <container_name> <image_name>
  ```
  This command creates and starts a container from an image. The --name flag allows you to name your container for easier management.

- Publish a Container’s Ports to the Host:
  ```
  docker run -p <host_port>:<container_port> <image_name>
  ```
  Maps a port from the host to the container, allowing access to the containerized application through the host machine.

- Run a Container in the Background:
  ```
  docker run -d <image_name>
  ```
  Starts the container in detached mode, allowing it to run in the background.

- Start or Stop a Container:
  ```
  docker start <container_name>
  docker stop <container_name>
  ```
  These commands start or stop a container that was created previously.

- Remove a Stopped Container:
  ```
  docker rm <container_name>
  ```
  Deletes a stopped container from your system.

- Open a Shell Inside a Running Container:
  ```
  docker exec -it <container_name> sh
  ```
  Opens a shell (like Bash or SH) inside a running container, allowing you to interact with the container's file system and processes.


#### Inspecting and Monitoring Containers
- List Running Containers:
  ```
  docker ps
  ```
  Displays a list of currently running containers.

- List All Containers (Running and Stopped):
  ```
  docker ps --all
  ```
  Displays all containers, including those that have stopped.

- Inspect a Container:
  ```
  docker inspect <container_name>
  ```
  Provides detailed information about a container, including its configuration and state.

- View Logs of a Container:
  ```
  docker logs -f <container_name>
  ```
  Fetches and follows the logs of a container to monitor its output in real-time.

- View Resource Usage Stats:
  ```
  docker container stats
  ```
  Displays real-time resource usage statistics of your containers.

#### System Commands
- View Docker System Information:
  ```
  docker info
  ```
  Displays system-wide information about Docker, including version, storage, and number of running containers.

- Get Help for Docker Commands:
  ```
  docker --help
  ```
  Displays help for the Docker CLI and subcommands. You can also append `--help` to any Docker command to learn more about it.

- Prune Unused Docker Images:
  ```
  docker image prune
  ```
  Removes all unused images to free up disk space.

- Prune All Unused Docker Objects (Containers, Images, Networks, and Volumes):
  ```
  docker system prune -a
  ```
  This command removes all stopped containers, unused networks, dangling images, and optionally, volumes, to free up space on your system. Use this command with caution as it will remove a lot of Docker resources that are no longer in use but might still be needed.

## Lab Task: Redo Using CLI Commands
After completing the following guides:
- [Get Docker Desktop Guide (Video Included)](https://docs.docker.com/get-started/introduction/get-docker-desktop/)
- [Develop with containers Guide (Video Included)](https://docs.docker.com/get-started/introduction/develop-with-containers/)
- [Build and push your first image (Video Included)](https://docs.docker.com/get-started/introduction/build-and-push-first-image/)

Reinforce your learning by repeating the tasks in these guides, but this time using the Docker CLI commands provided above. This exercise will give you hands-on experience with Docker's command-line interface.
