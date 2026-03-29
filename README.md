# Docker Infrastructure : Roboshop Project

* This repository contains the Dockerized setup for the Roboshop microservices application. It utilizes a combination of official database images and custom-built microservices, all services are interconnected through a dedicated Docker network.

## Pre-requisites

* Docker Installation and should be running.
* A custom docker network roboshop should be created: docker network create roboshop

# Database Layer

* The following databases are deployed using official images.

## MongoDB:7.0

``` docker run -d --network roboshop --name mongodb mongodb:1.0.0 ```