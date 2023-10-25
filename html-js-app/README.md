# To containerize this app, follow these steps

This repo contain basic web application to use for practicing Dockers for containerizing app

## Follow the following steps

### If you don't have git installed on your system, follow the following steps in Terminal/Shell
```
sudo apt-get update
```
```
sudo apt-get upgrade
```
```
sudo apt-get install git
```
### Once you have installed Git, follow the following steps

```
git clone https://github.com/engineerbaz/DockerUITA.git
```
```
ls
```
```


### Make sure you are in html-js-app folder on your system

```
docker build -t first-docker-app .
```
```
docker container run --name=first-docker-cont -d -p 8500:80 first-docker-app

```
## That's it!!! now click on following 

http://localhost:8500
