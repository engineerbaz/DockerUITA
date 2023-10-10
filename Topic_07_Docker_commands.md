# Docker Basic Commands

### check install docker
```sh
docker version
```
### adding a user to the docker group allows that user to run Docker commands without needing to use sudo we use -a mean append -G mean Group
```sh
sudo usermod -aG docker $USER
```

### List All Running Docker Containers 
```sh
docker ps 
```
### List All Docker Containers 
docker ps -a 

### Start a Docker Container 
```sh
docker start <container name> 
```
### For Example:
```sh
docker start mycontainer #mycontainer is container name
```

### Stop a Docker Container 
```sh
docker stop <container name> 
```

### For Example:
```sh
docker stop mycontainer #mycontainer is container name
```

### kill All Running Containers 
```sh
docker kill $(docker ps -q) 
```

### View the logs of a Running Docker Container 
```sh
docker logs <container name>
```

### For Example:
```sh
docker logs mycontainer #mycontainer is container name
```

## Delete All Stopped Docker Containers 
### Use -f option to nuke the running containers too. 
```sh
docker rm $(docker ps -a -q) 
```
### show complete information all details docker container
```sh
docker inspect <container name>
```
### For Example
```sh
docker inspect mycontainer #mycontainer is container name
```

### Remove a Docker Image 
```sh
docker rmi <image name> 
```

### For Example 
```sh
docker rmi ubuntu #ubuntu is image name
```

### Delete All Docker Images 
```sh
docker rmi $(docker images -q) 
```

### Delete All Images 
```sh
docker rmi $(docker images -q) 
```

### SSH Into a Running Docker Container Okay not technically SSH, but this will give we a bash shell in the container. 
```sh
sudo docker exec -it <container name> /bin/bash
```
### For Example 
```sh
docker exec -it mycontainer /bin/bash  #mycontainer is container name
```
