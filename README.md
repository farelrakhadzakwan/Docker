# Docker
Documentation of me using docker in my project, so that i can remember the commands i've been using before. My memory quite the short term they are.

## Docker Hub
Official website from docker that has many images to use in most of the projects [Docker Hub](https://hub.docker.com).

## Segmentation Chapter
### Docker Image
```
docker pull {image:tag}
docker images
docker ps
docker ps -a
docker image rm {image:tag}
docker image rmi {image:tag}
```
### Docker Container 
```
docker run -d {image:tag}
docker run -d --name {new_name} {image:tag}
docker logs {containerId / containerName}
docker logs -f {containerId / containerName}
docker stop {containerId / containerName}
docker rm {containerId / containerName}
```
### Docker Port Forwarding
```
docker run -d --name {newNameContainer} -p {hostPort:containerPort} {image:tag}
```
### Docker Exec
```
docker exec {containerName} {commandLine}
docker exec {containerName} ls -lh
docker exec {containerName} whoami
docker exec {containerName} pwd
docker exec -it {containerName} {pathCommand}
docker exec -it {containerName} /bin/sh
```
### Docker Stats
```
docker stats
```
### Environment Variable
```
docker run -d --name {newNameContainer} -p {hostPort:containerPort} -e {key=value} {image:tag}
docker run -d --name mysql-ku -p 3306:3306 -e MYSQL_ROOT_PASSWORD=mantap mysql:latest
```
### Docker Volume
```
docker volume create {nameVolume}
docker volume create vlm-mysql
docker volume ls
docker run -d --name {newNameContainer} -p {hostPort:containerPort} -e {key=value} -v {nameVolume:pathStoreData} {image:tag}
docker run -d --name mysql-ku -p 3306:3306 -e MYSQL_ALLOW_EMPTY_PASSWORD=yes -v vlm-mysql:/var/lib/mysql mysql:latest
mysql -u root -h 127.0.0.1 -p
docker volume rm {nameVolume}
cd /tmp && mkdir vlm-dir && cd vlm-dir && pwd
docker run -d --name {newNameContainer} -p {hostPort:containerPort} -e {key=value} -v ${pwd} {image:tag}
mysql -u root -h 127.0.0.1 -p
```
### Docker Network
```
docker network ls
docker network create {nameNetwork}
docker network connect {nameNetwork} {nameConnection}
docker run --rm -d --name {nameContainer} --network {nameNetwork} {image:tag}
docker exec -it {nameContainer} {/bin/sh}
apk add curl
curl {command}
docker network disconnect {nameNetwork} {nameContainer}
docker network rm {nameNetwork} 
```
### Docker Inspect
```
docker inspect {nameImage/nameContainer/nameNetwork:tag} / {id/name}
```
### Docker Limit
```
docker run --rm -d --name {nameContainer} --cpus="0.1" --memory="10m" -p {hostPort:containerPort} {image:tag}
```










