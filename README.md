
Will Contain docker commands that I use


## Set up Ubuntu docker image on windows

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
to save one image using a tag/name use commit using the container id

```sh
docker commit [container id]
```
to save it using a name do the following
```sh
docker tag [sha256 code] rajib-image
```
Check if they were saved properly or not
```sh
docker images [see all the images]
```

Run the saved image to continue your work

```sh
docker run -ti rajib-image bash
```


## Development


## License

MIT
