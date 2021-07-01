
Will Contain docker commands that I use


## Set up Ubuntu docker image on windows

* [Steps from Ubuntu website](https://ubuntu.com/tutorials/windows-ubuntu-hyperv-containers#1-overview)
* [Youtube tutorial](https://www.youtube.com/watch?v=eZpLjKv9xvA)

## After set up
```sh
Docker ps
docker run hello-world
docker images
docker run -ti ubuntu:latest bash
```
Then do stuff inside the ubnutu image


to get out of that image and back to powershell, do 
```sh
exit()
```

to see all the images currently in docker
```sh
docker ps -l
```

The terminal will look something like this

```sh
PS C:\Users\Rajib> docker ps -l
CONTAINER ID   IMAGE           COMMAND   CREATED       STATUS                      PORTS     NAMES
56d90fc15d97   ubuntu:latest   "bash"    5 hours ago   Exited (0) 22 seconds ago             kind_cartwright
```

to save one image using a tag/name use commit using the container id

```sh
docker commit kind_cartwright rajib-image
```

Check if they were saved properly or not
```sh
docker images
```

Run the saved image to continue your work

```sh
docker run -ti rajib-image bash
```

## Running things in docker
```sh
docker run
```
docker containers have names, if you do not give it one it will create one

if you want to destroy a container after you exit
```sh
docker run --rm -ti
```
give it a command --
```sh
docker run -ti ubuntu bash -c "sleep 3;echo all done"
```

leaving things running in a container . -d for detached

```sh
docker run -d -ti ubuntu bash
```
to jump into that container -- do
```sh
docker ps
```
it will give you a name, then if the name of the container is suspicious_williams

```sh
docker attach suspicious_wiliams
```
execute a new process in another container
```sh
docker exec -ti suspicious_williams bash
```



## Running processes in containers

## Manage containers

## Exposing ports

## Container networking

see all the virtual network running
```sh
docker network ls
```

## Development


## Data flow - Jenkins and Docker

Application build by developer ------> commit to GIT --------> Jenkins for CI ------> Jenkins will build JS App and create Docker Image -------> it will push to private Docker Repository -----> Dev Server will pull images
MIT
