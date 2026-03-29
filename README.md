# :rocket: Docker Infrastructure : Roboshop Project

* This repository contains the Dockerized setup for the Roboshop microservices application. It utilizes a combination of official database images and custom-built microservices, all services are interconnected through a dedicated Docker network.

# Pre-requisites

* Docker Installation and it should be running.
* A custom docker network roboshop should be created :
```
docker network create roboshop
```

# Database Layer

* The following databases are deployed using official images.

## MongoDB:7.0

```
docker run -d --network roboshop --name mongodb mongodb:1.0.0 
```

## Redis:7

```
docker run -d -network roboshop --name redis redis:7
```

## MySQL:8.0

```
docker run -d --network roboshop -e MYSQL_ROOT_PASSWORD=RoboShop@1 -v "$(pwd)/shipping/db:/tmp/sql_files" --name mysql mysql:8.0
```

## RabbitMQ:3.x

```
docker run -d --network roboshop -p 5672:5672 -p 15672:15672 -e RABBITMQ_DEFAULT_USER=roboshop -e RABBITMQ_DEFAULT_PASS=roboshop123 --name rabbitmq rabbitmq:3-management
```

# Backend Services

* First build and then run each component individually and check their health using interactive terminal.
* Replace component with the specific service name (e.g., catalogue, user, cart, shipping, and payment).

```
docker build -t component:1.0.0 .
```

```
docker run -d --network roboshop --name component component:1.0.0
```

```
docker exec -it componet bash
```

# Frontend Service (Nginx)

* Frontend should be expose to port number 80, so that it can be accessed by public.

```
docker build -t frontend:1.0.0 .
```

```
docker run -d -p 80:80 --network roboshop --name frontend frontend:1.0.0
```

# Health checks and Verification

* All the components are healthy and running. You can verify the status of the containers by using:
```
docker ps
```
* Finally, Roboshop application can be tested.