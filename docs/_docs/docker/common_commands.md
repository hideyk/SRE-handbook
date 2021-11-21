---
title: Common commands
tags: 
 - docker
description: Docker Common Commands
---

# Docker Commands

## Managing images

<br>

### Build an image
```bash
docker build -t <USER_REPO>/<IMAGE_NAME>:<TAG> <DOCKERFILE>
```


### Pull images from DockerHub
```bash
docker pull <IMAGE_NAME>:<TAG>
```

### Push images to DockerHub
```bash
docker push <USER>/<IMAGE+NAME>
```

### Create new image of an edited local container
```bash
docker commit <CONTAINER> <USER>/<IMAGE_NAME>
```


### View image's intermediate images with sizes and creation details
```bash
docker image history <IMAGE_NAME>
```

<br><br>

---

## Container lifecycle

<br>

### Start a Docker container
```bash
docker run -d --name=<CONTAINER_NAME> -p <HOST_PORT>:<CONTAINER_PORT> --rm <IMAGE_NAME>
```

### Show all containers
```bash
docker ps -a
```

### Start shell within running container
```bash
docker exec -it <CONTAINER_ID> /bin/bash
```

### Kill all running containers
```bash
docker container kill $(docker ps -q)
```

### Delete all running containers
```bash
docker container rm $(docker ps -a -q)
```

<br><br>

---
## Managing containers

<br>

### View Docker resource usage
```bash
docker system df
```

### Inspect a container
```bash
docker container inspect <CONTAINER_NAME>
```

### Print a container's logs
```bash
docker container log <CONTAINER_NAME>
```

<br><br>

---

# Acknowledgements

- [Top 15 Docker Commands - edureka](https://www.edureka.co/blog/docker-commands/)
- [15 Docker commands you should know - towardsdatascience](https://towardsdatascience.com/15-docker-commands-you-should-know-970ea5203421)