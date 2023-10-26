# Docker Volume:
Docker Volume allows you to share and manage data between containers, as well as between the host machine and containers. 

### Now we'll create and use different types of volumes.

### 1) Named Volume

#### We create named volume named is myvolume:
```sh
root@DevOps:~# docker volume create myvolume
```

#### listing Volume check my create volume
```sh
root@DevOps:~# docker volume ls
```

#### OUtput
root@DevOps:~# docker volume ls
local     myvolume
root@DevOps:~#

#### Now We runs an Nginx container and mounts the myvolume volume to the /data directory in the container
```sh
root@DevOps:~# docker run -d -v myvolume:/data --name vol-container nginx
```

#### all information about the volume, such as its mount point on the host machine.
```sh
root@DevOps:~# docker volume inspect myvolume
```
#### Output
root@DevOps:~# docker volume inspect myvolume

[
    {
        "CreatedAt": "2023-10-26T12:51:05+05:00",
        "Driver": "local",
        "Labels": null,
        "Mountpoint": "/var/snap/docker/common/var-lib-docker/volumes/myvolume/_data",
        "Name": "myvolume",
        "Options": null,
        "Scope": "local"
    }
]
root@DevOps:~# 

#### stop and remove container
```sh
root@DevOps:~# docker stop vol-container
root@DevOps:~# docker rm vol-container
```
#### delete volume
```sh
root@DevOps:~# docker volume rm myvolume
```

### 2) Bind Mounts

#### Create Simple File on the Host Machine For Volume:
```sh
root@DevOps:~# echo "hi volume" > volume.txt
```

#### Run Container with Bind Mount:
```sh
root@DevOps:~# docker run -d -v /root/volume.txt:/etc/nginx/config.txt --name bind-mount-container nginx
```

#### check details information container and see Volume Mount details 
```sh
root@DevOps:~# docker inspect bind-mount-container
```
here are some like this Output
"Mounts": [
            {
                "Type": "bind",
                "Source": "/root/volume.txt",
                "Destination": "/etc/nginx/config.txt",
                "Mode": "",
                "RW": true,
                "Propagation": "rprivate"
            }
        ],

#### only mount details of container command we use grep command and use -A flag mean all and 10 lines
```sh
root@DevOps:~# docker inspect bind-mount-container | grep -A 10 "Mounts" 
```
#### Output
root@DevOps:~# docker inspect bind-mount-container | grep -A 10 "Mounts" 
here are some like this Output
    "Mounts": [
            {
                "Type": "bind",
                "Source": "/root/volume.txt",
                "Destination": "/etc/nginx/config.txt",
                "Mode": "",
                "RW": true,
                "Propagation": "rprivate"
            }
        ],
        "Config": {

root@DevOps:~# 

#### stop and delete/remove container
```sh
root@DevOps:~# docker stop bind-mount-container
root@DevOps:~# docker rm bind-mount-container
```

### 3) tmpfs Mount

#### Run Container with tmpfs Mount:
```sh
root@DevOps:~# docker run -d --tmpfs /tmp/data --name tmpfs-container busybox
```
#### Stop and Remove/delete the Container
```sh
root@DevOps:~# docker stop tmpfs-container
root@DevOps:~# docker rm tmpfs-container
```

Now we setup different types of Docker volumes in various scenarios. 
And Now we can observe how data persists, or in the case of tmpfs, how it exists only in memory.
Thanks For Support 
GOOD LUCK 
