# Docker Cheatsheet
---
## 1. Introduction to Docker
What is Docker?
Docker is an open-source platform that automates the deployment, scaling, and management of applications by using containerization technology. Containers are lightweight, portable, and consistent environments that contain everything needed to run a piece of software, including the code, runtime, system tools, libraries, and settings.
Key Concepts
Docker Engine: The core component of Docker, responsible for running containers.
Image: A lightweight, standalone, and executable software package that includes everything needed to run an application.
Container: A runtime instance of a Docker image that shares the host system's kernel.
Dockerfile: A script containing a series of commands to assemble a Docker image.
Registry: A storage and distribution system for Docker images, such as Docker Hub.
Docker Compose: A tool for defining and running multi-container Docker applications using a YAML file.

## 2. Installing Docker
Install Docker on Linux
Install Docker Engine:

sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io
Start Docker Service:

sudo systemctl start docker
sudo systemctl enable docker
Install Docker on macOS
Install Docker Desktop:
Download and install Docker Desktop from Docker's official website.
Install Docker on Windows
Install Docker Desktop:
Download and install Docker Desktop from Docker's official website.
## 3. Basic Docker Operations
Working with Docker Images
Search for an Image:

docker search nginx
Pull an Image from Docker Hub:

docker pull nginx
List All Images:

docker images
Remove an Image:

docker rmi nginx
Working with Docker Containers
Run a Container:

docker run -d -p 80:80 --name mynginx nginx
List Running Containers:

docker ps
List All Containers (including stopped):

docker ps -a
Stop a Running Container:

docker stop mynginx
Remove a Container:

docker rm mynginx
Docker Networks
List All Networks:

docker network ls
Create a New Network:

docker network create mynetwork
Connect a Container to a Network:

docker network connect mynetwork mynginx
Disconnect a Container from a Network:

docker network disconnect mynetwork mynginx

##4. Building Docker Images
Dockerfile Basics
Sample Dockerfile:

# Use an official Node.js runtime as a parent image
FROM node:14

# Set the working directory in the container
WORKDIR /app

# Copy the current directory contents into the container at /app
COPY . /app

# Install any needed packages specified in package.json
RUN npm install

# Make port 8080 available to the world outside this container
EXPOSE 8080

# Define environment variable
ENV NODE_ENV production

# Run app.js using node
CMD ["node", "app.js"]
Building an Image from a Dockerfile
Build the Image:

docker build -t mynodeapp .
Managing Image Tags
Tag an Image:

docker tag mynodeapp myrepo/mynodeapp:v1.0
Push an Image to Docker Hub:

docker push myrepo/mynodeapp:v1.0
5. Docker Compose
Introduction to Docker Compose
Docker Compose is a tool for defining and running multi-container Docker applications. You use a YAML file to configure your application's services, and then use a single command to create and start all the services.
Sample docker-compose.yml File
version: '3'
services:
  web:
    image: nginx
    ports:
      - "8080:80"
  db:
    image: mysql:5.7
    environment:
      MYSQL_ROOT_PASSWORD: example
Docker Compose Commands
Start Services:

docker-compose up
Stop Services:

docker-compose down
Scale Services:

docker-compose up --scale web=3
Managing Volumes with Docker Compose
Defining Volumes:

services:
  web:
    image: nginx
    volumes:
      - ./webdata:/usr/share/nginx/html
6. Docker Volumes and Storage
Understanding Docker Volumes
Volumes are the preferred mechanism for persisting data generated and used by Docker containers.
Managing Volumes
Create a Volume:

docker volume create myvolume
List All Volumes:

docker volume ls
Inspect a Volume:

docker volume inspect myvolume
Remove a Volume:

docker volume rm myvolume
Mounting Volumes
Mount a Volume to a Container:

docker run -d -p 80:80 --name mynginx -v myvolume:/usr/share/nginx/html nginx
Bind Mounts
Use a Bind Mount:

docker run -d -p 80:80 --name mynginx -v /path/to/local/dir:/usr/share/nginx/html nginx
7. Docker Networking
Networking Modes
Bridge Network: The default network driver, which allows containers to communicate on the same host.
Host Network: Removes network isolation between the container and the Docker host.
Overlay Network: Enables networking between multiple Docker hosts in a swarm.
Working with Networks
Create a User-Defined Bridge Network:

docker network create mynetwork
Run a Container in a Network:

docker run -d --name mynginx --network=mynetwork nginx
Inspect a Network:

docker network inspect mynetwork
DNS in Docker
Docker containers can resolve each other's hostnames to IP addresses by using the embedded DNS server.
8. Docker Security
Securing Docker
Least Privileged User: Always run containers as a non-root user.

FROM nginx
USER www-data
Use Trusted Images: Use official images or images from trusted sources.

Keep Docker Updated: Regularly update Docker to the latest version to benefit from security patches.

Docker Content Trust
Enable Docker Content Trust (DCT):

export DOCKER_CONTENT_TRUST=1
Managing Secrets
Create a Secret in Docker Swarm:

echo "mysecretpassword" | docker secret create my_secret -
Use a Secret in a Service:

docker service create --name myservice --secret my_secret nginx
Securing Docker Daemon
Use TLS to Secure Docker API:
Generate TLS certificates and configure the Docker daemon to use them for secure communication.
Limiting Container Resources
Limit Memory:

docker run -d --name mynginx --memory="256m" nginx
Limit CPU:

docker run -d --name mynginx --cpus="1.0" nginx
9. Advanced Docker Features
Docker Swarm
Initialize a Swarm:

docker swarm init
Join a Swarm:

docker swarm join --token SWMTKN-1-xxxx
Deploy a Stack:

docker stack deploy -c docker-compose.yml mystack
Multi-Stage Builds
Example of a Multi-Stage Dockerfile:

# First Stage
FROM golang:1.16 as builder
WORKDIR /app
COPY . .
RUN go build -o myapp

# Second Stage
FROM alpine:latest
WORKDIR /app
COPY --from=builder /app/myapp .
CMD ["./myapp"]
Docker Plugins
List Installed Plugins:

docker plugin ls
**Install a Plugin

**:

docker plugin install vieux/sshfs
Docker Daemon Configuration
Customizing Docker Daemon:

Edit the /etc/docker/daemon.json file to configure the Docker daemon.
{
  "log-driver": "json-file",
  "log-level": "warn",
  "storage-driver": "overlay2"
}
Reload Daemon Configuration:

sudo systemctl reload docker
10. Monitoring and Logging
Docker Logs
View Container Logs:

docker logs mynginx
Follow Logs:

docker logs -f mynginx
Monitoring Containers
Inspect Resource Usage:

docker stats mynginx
Docker Events:

Monitor Docker events in real-time.
docker events
Integrating with Monitoring Tools
Prometheus and Grafana: Use cAdvisor and Prometheus Node Exporter to monitor Docker containers.

docker run -d --name=cadvisor --volume=/:/rootfs:ro --volume=/var/run:/var/run:ro --volume=/sys:/sys:ro --volume=/var/lib/docker/:/var/lib/docker:ro --volume=/dev/disk/:/dev/disk:ro --publish=8080:8080 google/cadvisor:latest
11. Docker Best Practices
Dockerfile Best Practices
Minimize Image Size: Use multi-stage builds and slim base images.
Leverage Build Cache: Organize Dockerfile instructions to maximize the use of cache layers.
Use .dockerignore: Exclude unnecessary files from the build context using a .dockerignore file.
Container Management Best Practices
Immutable Infrastructure: Treat containers as immutable, replace rather than modify running containers.
Keep Containers Stateless: Design containers to be stateless, with external data persistence.
Log to STDOUT/STDERR: Ensure containers log to STDOUT/STDERR for easier aggregation and analysis.
Security Best Practices
Regularly Scan Images: Use tools like trivy to scan images for vulnerabilities.

Use Namespaces: Use namespaces to isolate container resources and enhance security.

Limit Capabilities: Drop unnecessary capabilities from containers.

docker run --cap-drop=ALL --cap-add=NET_BIND_SERVICE nginx
12. Troubleshooting Docker
Common Issues
Container Exits Immediately:

Check the Docker logs for errors.
docker logs <container_id>
Image Build Fails:

Debug using the --no-cache option to rebuild the image without cache.
docker build --no-cache -t myimage .
Networking Issues:

Verify network settings and connectivity.
docker network inspect <network_name>
Useful Docker Commands for Troubleshooting
Inspect a Container:

docker inspect <container_id>
Enter a Running Container:

docker exec -it <container_id> /bin/bash
Check Resource Usage:

docker stats
13. References
Official Documentation
Docker Documentation
Community Resources
Docker Hub
Docker GitHub Repository
Docker Forums
