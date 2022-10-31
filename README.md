## :scroll: Project description

This project was created to:
 - Apply multistage building using Nginx as a reverse proxy;
 - Use docker-compose to build images
 - Create Mysql database with NodeJS
 - Dependencies between two containers
 - Use Dockerize to wait dependecies


## :hammer: Technologies
The following technologies was used to made this project:

-  [Docker](https://www.docker.com/)
-  [Docker-Compose](https://docs.docker.com/engine/reference/commandline/compose/)
-  [Dockerize](https://github.com/jwilder/dockerize)
-  [Laravel Nginx config](https://laravel.com/docs/9.x/deployment#nginx)

## :iphone: Running the application

Doing it manually
```bash
To run the application please follow the next steps:

# Clone this repository
git clone https://github.com/victorhugoaraujo/docker.git

# Go into the repository
$ cd docker

# Create a network
$ docker network create <name>

# Build laravel container
$ docker build -t victorhugoaraujo/laravel:prod laravel -f laravel/Dockerfile.prod

# Go into nginx directory
$ cd nginx

# Build nginx container
$ docker build -t victorhugoaraujo/nginx:prod . -f Dockerfile.prod

# Run laravel container
$ docker run -d --network <network-name> --name laravel victorhugoaraujo/laravel:prod

# Run nginx container
$ docker run -d --network <network-name> --name nginx -p 8080:80 victorhugoaraujo/nginx:prod

# Go to your browser
localhost:8080
```

Using docker-compose

```bash
$ docker-compose up

# Go to your browser
localhost:8080
```

```bash
Running node and mysql using docker-compose

# building containers
$  docker-compose up -d --build

First terminal
# checking mysql database
$ docker exec -it db bash

$ mysql -uroot -p
password: root

# check database nodedb
$ show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| nodedb             |
| performance_schema |
| sys                |
+--------------------+

$ use nodedb;

# Create table
$ create table people(id int not null auto_increment, name varchar(255), primary key(id));

# Check table
$ desc people;
+-------+--------------+------+-----+---------+----------------+
| Field | Type         | Null | Key | Default | Extra          |
+-------+--------------+------+-----+---------+----------------+
| id    | int(11)      | NO   | PRI | NULL    | auto_increment |
| name  | varchar(255) | YES  |     | NULL    |                |
+-------+--------------+------+-----+---------+----------------+

First terminal ends

Second teriminal
# Running node (Insert data in people)
$docker exec -it app bash
$ node index.js

Second teriminal ends

First terminal 
# Check data in mysql
$ select * from people;
result:
+----+--------+
| id | name   |
+----+--------+
|  1 | Victor |
+----+--------+
```

Made with ♥ by Victor Hugo :wave: [Get in touch!](https://www.linkedin.com/in/victor-hugo-araujo-a73964115/)