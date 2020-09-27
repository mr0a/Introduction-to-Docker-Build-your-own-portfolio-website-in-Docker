# Introduction-to-Docker-Build-your-own-portfolio-website-in-Docker

### Basic Docker commands:
- `docker start app-name` - To start the docker container running
- `docker stop app-name` - To stop the docker container
- `docker ps` - To view the list of running docker container  

### Docker Architecture:
![](https://raw.githubusercontent.com/mr0a/Introduction-to-Docker-Build-your-own-portfolio-website-in-Docker/master/docker_architecture.svg)

### Docker Hub:
- [Docker Hub](hub.docker.com) contains images of many frameworks and technologies like nginx, nodejs, python, etc.
- Search for image from docker hub and use `docker pull image-name` to download the image locally.
- `docker images` - To see the list of images available locally
- If you run the nginx docker now with `docker run nginx`, the webserver would have not been available from our localhost because we haven't setup port forwarding in the container, and we would be hanging in the nginx container running
- `docker run -d nginx` - To run container in ***detached mode***

### Getting into the docker container:
- We use `exec` command in docker to see get into the container running with `-it` flags to get in ***interactive mode***
- `docker exec -it container-id bash` - To get into the process in the container (here it is bash `/bin/bash`). Get container id from `docker ps`
- `ctrl + d` - Shortcut to exit any process

### Publishing a PORT to the host:
- We can use `--publish` or `-p` To ***publish*** a exposed PORT from container
- `docker run -dp [host-port]:[exposed-container-port]` - To map a exposed port to host port.
- Now check the host port to see the nginx welcome page from docker. If you get the nginx page then we have mapped the port successfully.
- We can also check the mapping of ports from `docker ps`

### Stopping Containers:
- `docker stop container-id` - To stop a running container
- We can start the stopped container using `docker start container-id`

### List of running and stopped containers:
- `docker ps -a` - To see the list of containers currently running or stopped earlier
- `docker ps -aq` - To get only the container id's of all the containers which are either running or stopped
- `docker rm -f $(docker ps -aq)` - To remove all the containers

### Remove a container from list:
- `docker rm container-id` - To ***remove*** a container (so that we cannot start the same container again). We need to stop the container before removing it
- `docker rm -f container-id` - To ***force*** remove a container (even when the container is running)

### Naming and Renaming a container:
- `docker run --name container_name app_name` -  To name our app ***container***
- `docker run -d -p --name test_site nginx` - To run nginx app with detached mode, port mapping and container name test_site
- `docker rename test_site new_site` - To rename a named container

*** Till now we have learnt to pull and start a container, stop a container, map a port from container to host, execute process from a container(bash), removing a container and also to name and rename a container.***
