# Docker Volumes

## Problem Statement

It is a very common requirement to persist the data in a Docker container beyond the lifetime of the container. However, the file system
of a Docker container is deleted/removed when the container dies. 

## Solution

There are 2 different ways how docker solves this problem.

1. Volumes
2. Bind Directory on a host as a Mount


# Note - bind mounts are not much used now a days so we will implement only volume and mount volumes to container

### Volumes and Volumes implementation 

Volumes aims to solve the same problem by providing a way to store data on the host file system, separate from the container's file system, 
so that the data can persist even if the container is deleted and recreated.

![image](https://user-images.githubusercontent.com/43399466/218018334-286d8949-d155-4d55-80bc-24827b02f9b1.png)


Volumes can be created and managed using the docker volume command. You can create a new volume using the following command:

```
docker volume create <volume_name>
```

Once a volume is created, you can mount it to a container using the -v or --mount option when running a docker run command. 

For example:

```
docker run -itd --mount source=<volume-name> ,target=/app  <image-name>:<tag>
```


## Key Differences between Volumes and Bind Directory on a host as a Mount

Volumes are managed, created, mounted and deleted using the Docker API. However, Volumes are more flexible than bind mounts, as 
they can be managed and backed up separately from the host file system, and can be moved between containers and hosts.

In a nutshell, Bind Directory on a host as a Mount are appropriate for simple use cases where you need to mount a directory from the host file system into
a container, while volumes are better suited for more complex use cases where you need more control over the data being persisted
in the container.
