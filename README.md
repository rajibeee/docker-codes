
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

--- 


make a new network

```sh
docker network create learning
```
put a machine in that network

docker run -rm -ti --net learning --name catserver ubuntu:14.04 bash

test it using 

ping catserver

crate a dog-server

docker run -rm -ti --net learning --name dogserver ubuntu:14.04 bash

now you can ping between dogserver and catserver


docker network create catsonly

put cat machine into cat network
docker network connect catsonly catserver

## Managing images
see all the images

docker images

remove image by image id
docker rmi bd717kg23442

remove image by name

docker rmi my-image


## Docker registries

search for docker images

```sh
docker search ubuntu

```

log in on docker

```sh
docker login
```

pull an image

```sh
docker pull ubuntu
```

push an existing image to docker huh. Need to tag it first
Here, tagging the image "rajib-latest" to username "rajibdey" and folder "test"
```sh
docker tag rajib-image:latest rajibdey/test:first
```
then push using
```sh
docker push rajibdey/test:first
```
It is available here
https://hub.docker.com/repository/docker/rajibdey/test

## Docker file

create a docker file 

create a new file
nano dockerfile

write this inside

FROM busybox
RUN echo "buliding simple docker image."
CMD echo "hello container"


build it

docker build -t hello .


run it

docker run --rm hello


example 2 of docker file

write this in dockerfile


FROM debian:sid
RUN apt-get -y update
RUN apt-get install nano
CMD ["/bin/nano", "/tmp/notes"]

build it

docker build -t example/nanoern .


run it . ti stands for interactive mode

docker run --rm -ti example/nanoer

example 3 of docker file. Starts from the previous example

write this in docker file

FROM example/nanoer
ADD notes.txt /notes.txt
CMD "/bin/nano" "/notex.txt"


build it 
docker build -t example/notes .

run it

docker run --rm -ti example/notes

more reference > https://docs.docker.com/engine/reference/builder/



## Development


## Data flow - Jenkins and Docker

Application build by developer ------> commit to GIT --------> Jenkins for CI ------> Jenkins will build JS App and create Docker Image -------> it will push to private Docker Repository -----> Dev Server will pull images
MIT
