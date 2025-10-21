# 🛠 Common Docker Commands

```bash
docker [COMMAND] [OPTIONS] [ARGUMENTS]
```

## 🔹 General
```bash
docker -v "--version"  # Show Docker version
docker info  # Show system-wide Docker info
docker help  # List available commands
docker login  # Log in to Docker Hub
docker logout  # Log out of Docker Hub
```
## 🔹 Working with Images
```bash
docker pull IMAGE_NAME:TAG  # Download image from Docker Hub
docker images  # List images
docker image ls  # List images
docker history IMAGE_ID|IMAGE_NAME  # Show history of an image
docker rmi IMAGE_ID|IMAGE_NAME  # Remove an image
docker rmi -f IMAGE_ID|IMAGE_NAME  # Remove an image that has container running
```
## 🔹 Working with Containers
```bash
docker ps  # List running containers
docker container ls  # List running containers
docker ps -a  # List all containers (running + stopped)
docker container ls -a  # List all containers (running + stopped)
docker run hello-world  # Run a container from image, and if not exist, download then run container
docker run -it ubuntu sh|bash  # Run with interactive shell
docker run -d -p 8080:80 nginx  # Run in detached mode, map port 8080 → 80
docker stop CONTAINER_ID|CONTAINER_NAME  # Stop a running container
docker start CONTAINER_ID|CONTAINER_NAME  # Start a stopped container
docker rm CONTAINER_ID|CONTAINER_NAME  # Remove a container
docker rm -f CONTAINER_ID|CONTAINER_NAME  # Remove a container is running
docker inspect CONTAINER_ID|CONTAINER_NAME  # Inspect container
docker logs CONTAINER_ID|CONTAINER_NAME  # Show logs
docker stats CONTAINER_ID|CONTAINER_NAME  # Show stats
docker exec -it CONTAINER_ID|CONTAINER_NAME bash|sh  # Run container then exec shell
docker container --format "{{range.SettingNetwork.Networks}}{{.IPAddress}}{{end}}"  # know ip address
```
## 🔹 Options
```bash
-d = --detach  # Run in detached mode (running on background)
docker run -d nginx

-p = --publish  # Publish a port mapping(host:container port)
docker run -p 8080:80 nginx  #(8080 => host port & 80 => container port)

-P  # Publish all ports (randmonly)
docker run -P nginx

# before expose port, you must know which ports is available, run `docker inspect <image_id>|<image_name>`

-it = --interactive  # Run with interactive shell
docker run -it ubuntu sh|bash

--rm = --remove = --auto-remove  # Remove container on exit
docker run --rm nginx

--name  # Set container name
docker run --name my-app nginx 

-v = --volume  # Mount a volume
docker run -v /mydata:/app/data nginx

-w = --workdir  # Set working directory
docker run -w /app -v /mydata:/app/data nginx

-u = --user  # Set user
docker run -u root -v /mydata:/app/data nginx

-e = --env  # Set environment variable
docker run -e MYSQL_ROOT_PASSWORD=secret mysql

--entrypoint  # Set entrypoint
docker run --entrypoint /bin/sh mysql

--label  # Set metadata for an image
docker run --label version=1.0 mysql

sleep (seconds, infinity) # make container is running
docker run busybox sleep 5  # Sleep for 5 seconds
docker run busybox sleep infinity  # Sleep forever
```
## 🔹 Building Images
```bash
docker build -t my-app .  # Build image from Dockerfile in current folder
docker run my-app         # Run container from your image
```
## 🔹 Volumes (Data Persistence)
```bash
docker volume create mydata           # Create volume
docker run -v mydata:/app/data my-app # Attach volume to container
docker volume ls                      # List volumes
docker volume rm mydata               # Remove volume
docker rm -v mydata                   # Remove volume
docker volume inspect mydata          # Display detailed information on one or more volumes
docker volume prune                   # Remove unused volumes
```
## 🔹 Networks
```bash
docker network ls                     # List networks
docker network create mynetwork       # Create a network
docker run --network=mynetwork my-app # Connect container to network
```
