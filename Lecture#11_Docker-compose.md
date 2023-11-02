# Docker Compose & yaml Labs
Docker Compose is a tool for defining and running multi-container Docker applications. 
It allows you to define a multi-container environment in a single file, 
usually named **docker-compose.yml**

# yaml 
YAML stands for "YAML Ain't Markup Language" or sometimes "Yet Another Markup Language,"
is a human-readable data serialization format.

### below yaml file create yaml file using nano command 
```sh
root@DevOps:~# nano docker-compose.yml
```
### Yaml file:
```sh
services:
  web:
    image: nginx:latest
  db:
    image: postgres:latest
```
There are two **services:** **web** and **db,** each running a different Docker image.
### services
These are the building blocks of our application

### Start services defined in the docker-compose.yml file and using -d flage deattach
```sh
root@DevOps:~# docker-compose up -d
``` 

### List the services and their status.
```sh
root@DevOps:~# docker-compose ps
```

### Stop and remove the containers
```sh
root@DevOps:~# docker-compose down
```

Now we have setup  two services: web and db. 
The web service uses the latest Nginx image and maps port 8080 on the host to port 80 on the container. 
The db service uses the latest PostgreSQL databasse image.
Good luck 



