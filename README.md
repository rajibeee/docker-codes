
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



## Development


## Data flow - Jenkins and Docker

Application build by developer ------> commit to GIT --------> Jenkins for CI ------> Jenkins will build JS App and create Docker Image -------> it will push to private Docker Repository -----> Dev Server will pull images
MIT
