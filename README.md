# docker_ROS
follow This repo to setup ROS in docker
-Container, networks, images, and the build cache can be cleaned up by executing:
```
docker system prune -a
docker volumes prune
```

-List your images.

```docker image ls```

    -Delete a specific image.

```docker image rm [image name]```

    -Delete all existing images.

```docker image rm $(docker images -a -q)```

    List all existing containers (running and not running).

$ docker ps -a

    Stop a specific container.

$ docker stop [container name]

    Stop all running containers.

$ docker stop $(docker ps -a -q)

    Delete a specific container (only if stopped).

$ docker rm [container name]

    Delete all containers (only if stopped).

$ docker rm $(docker ps -a -q)

    Display logs of a container.

$ docker logs [container name]


# Docker Commands


## IMAGES
- Downloading Images
```
docker pull <image name>
```
- List all images
```
docker images -a
```
- Delete single Image
```
docker rmi <image id>
```
- All images delete
```
docker rmi $(docker images  -q)
```
- Dangling images delete
```
docker rmi $(docker images --filter "dangling=true" -q --no-trunc)
```



## CONTAINERS
- Creating a interactive container  from image
```
docker run -it <image name>
```
- Giving Name to a container while creating
```
docker run --name <container name> <image name>
```
- Start a stopped Container
```
docker start (container_id)
```
- Stop all containers
```
sudo docker kill $(sudo docker ps -a)
```
- Connect shell to running container
```
docker exec -it (container_id) bash
```
- Delete single Container
```
docker rm <container id or container name>
```
- Delete all containers
```
docker rm $(docker ps -a -q)
```
## Building Image from Docker File
- Terminal from same directory
```
docker built -t <image name > .
```

## GUI arguments
### Windows

## Complete Examples
- Running a container with GUI enabled for Windows
```
docker run -it --name r2_pathplanning_container -e DISPLAY=host.docker.internal:0.0 -e haiderabbasi333/ros2-pathplanning-course:1 bash

```

## Mistakes
- Mixing options
```
docker run --name -it <container name> <image name>
```
here you should have provided name for **--name** before giving another option **-it**
docker rmi removes images by their ID docker by running 
images -a or docker images.
docker rmi <your-image-id>
  Remove multiple images
 docker rmi <your-image-id> <your-image-id> ...
  Remove all images at once
  docker rmi
  docker rmi $(docker images -q)
  
      docker ps list containers
    -a the option to list all containers, even stopped ones. Without this, it defaults to only listing running containers
    -q the quiet option to provide only container numeric IDs, rather than a whole table of information about containers
  
  
  docker rm removes containers by their name or ID.

When you have Docker containers running, you first need to stop them before deleting them.

    Stop all running containers: docker stop $(docker ps -a -q)
    Delete all stopped containers: docker rm $(docker ps -a -q)
