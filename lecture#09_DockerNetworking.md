# Docker Networking:
Docker networking is a powerful feature that facilitates communication between containers and external systems 
while providing flexibility and isolation and allows containers to communicate with each other and the outside world. 

### lets We'll cover docker networking types the default bridge network, host network, and a custom user-defined bridge network.
### 1) Default Bridge Network

### Run container used the default bridge network No need attach this network by default Network 
```sh
root@DevOps:~# docker run -d --name=webserver1 nginx
```

### Use docker inspect command to check the network details
```sh
root@DevOps:~# docker inspect -f webserver1
```

### Use docker inspect command to check only the network name
```sh
root@DevOps:~# docker inspect -f '{{ .HostConfig.NetworkMode }}' webserver1
```
### OUtput
default

### stop and delete container 
```sh
root@DevOps:~# docker rm webserver1
```

### 2) Host Network

### Run container used the Host network attach --network=host

### Use docker inspect command to check the network details
```sh
root@DevOps:~# docker inspect -f webserver2
```

### Use docker inspect command to check only the network name
```sh
root@DevOps:~# docker inspect -f '{{ .HostConfig.NetworkMode }}' webserver2
```
### OUtput
host

### stop and delete container 
```sh
root@DevOps:~# docker rm webserver2
```


### 3) Custom User-Defined Bridge Network

### Create custom bridge network
```sh
root@DevOps:~# docker network create mynetwork
```

### Run container used the Host network attach --network=network-name

### Use docker inspect command to check the network details
```sh
root@DevOps:~# docker inspect -f webserver3
```

### Use docker inspect command to check only the network name
```sh
root@DevOps:~# docker inspect -f '{{ .HostConfig.NetworkMode }}' webserver3
```
### OUtput
mynetwork

### Stop and delete container 
```sh
root@DevOps:~# docker rm webserver3
```
### delete network command 
```sh
root@DevOps:~# docker network rm mynetwork
```

Now We explore different Docker networking types. 
The default bridge network provides basic isolation, 
the host network shares the host's network namespace, 
and a custom user-defined bridge network allows to create isolated networks for our containers.
Thanks For supporting Good luck.

