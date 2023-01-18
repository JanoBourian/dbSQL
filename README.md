# Fast query examples

## Creating a Docker container

For this application we going to work with **MySQL**. The official image is in: https://hub.docker.com/_/mysql
But the steps about the configuration are in: https://platzi.com/tutoriales/1432-docker/3268-como-crear-un-contenedor-con-docker-mysql-y-persistir-la-informacion/

### Steps:

- Review docker state

```cmd
docker --version
docker image
docker ps
docker ps -a
```

- Download the official image.

```cmd
docker pull mysql
```

- Started a MySQL instance:
    - **some-mysql**: is the container name- it : interactive mode and terminal
    - **my-secret-pw**: password
    - **tag**: the specific version of mysql
    - **d**: Deatached mode (Running in background)
    - **p**: Port 
    - **name**: indicate that the next command will be the container name
    - **e**: environment for the password

By documentation
```cmd
docker run --name some-mysql -e MYSQL_ROOT_PASSWORD=my-secret-pw -d mysql:tag
docker run --name mysqlcourse -e MYSQL_ROOT_PASSWORD=simplepassword -d mysql:latest
```

By Platzi
```cmd
docker run -d -p 33060:3306 --name mysqlcontainer -e MYSQL_ROOT_PASSWORD=simplepassword mysql:latest
```

### To into the container

- **exec**: we will pass a command
- **-it**: Interactive mode
- **mysql -p**: To into with root user

```cmd
docker exec -it mysqlcontainer mysql -p
```

## Conecting and store the information with the DataBase Manager

For more information you can check this: https://earthly.dev/blog/docker-mysql/

- Delete the last process
```cmd
docker rm -f mysqlcontainer
```

- Delete all volumes:
```cmd
docker volume prune
```

- Create a volume
```cmd
docker volume create mysqlcourse
docker volume ls
```

- Start again docker 
```cmd
docker run -d -p 33060:3306 --name mysqlcontainer -e MYSQL_ROOT_PASSWORD=simplepassword -v mysqlcourse=/var/lib/mysql mysql:latest
```

```cmd
docker exec -it mysqlcontainer mysql -p
```

## Introduction


## Environment


## Normalization


## Design and Creation


## Manipulation using SQL queries


## Aditional Functions


## Group Tables


## Store Procedures, Funtioncs, Triggers, Index


## Access and Backup

