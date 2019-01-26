---
date: 2019-01-21T23:53:28-06:00
title: "Docker + MongoDB"
description: "A useful guide to Docker basics"
featured_image: '/images/docker_cover.jpg'
tags: [docker, springboot, rest, mongodb]
draft: false
---

## Docker Introduction

I gaurantee you that any company you work for nowadays will be utilizing some kind of container for testing and deploying applications. The most popular of the container softwares is Docker. The main benefit of Docker is that if someone wants to run your application on their computer, they do not have to try to match your software versions just to run it. All they need to do is have Docker installed on their machine and they will be able to run your program in an isolated container that you have given the instructions on which version of software to run and how to launch the program. 

## Docker Terminology

A docker image is a mold that you can use to create containers out of. A docker container is the physical container that you run your program on. So a docker image can have many containers. A Dockerfile is a set of instructions that builds up your customized docker image. Tasks such as downloading specific files, running a linux package manager like apt-get or apk-get, and exposing ports for your application can all be used to build your custom image.

## Let's Dockerize a Spring Boot App

I am going to show you how to dockerize a Spring Boot application and link it to a MongoDB instance running in another container. Navigate to the [Spring Initialzr](https://start.spring.io/) and pick Web, MongoDB, and Lombok.

![alt text](/images/spring_initializr_mongo.png)

Now download the zip and import it into IntelliJ or your preferred IDE. 

## Entity Class

This will be a simple Mongo JPA Data example as to focus more so on the dockerizing of the application. 

{{< gist SDiamante13 df993fe4b206bd6dd79796eecd1d5423 >}}

## Repository Class

Now create a repository interface so we can interact with MongoDB. This will extend MongoRepository

{{< gist SDiamante13 21ba1771c74c16f7b7d91d434a3f59dc >}}

## Service Class

Now let's create a service class as to further extract the repository.

{{< gist SDiamante13 2046cf4c2158ac7a27c19e5973b6a252 >}}

## Controller Class

{{< gist SDiamante13 5f09ab49ef5751463a97807235094b0d >}}

## MongoDb Initial Loader Class

{{< gist SDiamante13 29e2b1291c8f43554fb5e43c51e5622a >}}

## Change the port if you wish

In application.properties we can change the port (optional) by adding this line: 

`server.port=8085`

## Download and run mongoDb container

Instead of downloading MongoDB on our laptop, we can run an instance of MongoDB in a docker container and link our Spring Boot project to it.

The image we will be using is named [mongo](https://hub.docker.com/_/mongo) and is hosted on Docker Hub which is Docker's version of GitHub.

```
docker run -d -p 27017:27017 --name mongo mongo
```

This command will download the mongo image from Docker Hub and run a container based off of that image. By default, Docker names all container with random names, but using --name we can give the container a fixed name. Doing this makes it easier to interact with later and it is easier to remember than focused_lamarr.

By providing the flag -d this tells the container to be run in the background. The flag -p exposes and binds the port of the container to the port of the local machine.

## Basic Commands

#### List all images
```
docker images

REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE    
springboot-mongo    latest              52855cc58fb2        6 days ago          124MB   
mongo               latest              7177e01e8c01        4 weeks ago         393MB   
openjdk             8-jdk-alpine        97bc1352afde        3 months ago        103MB   
```

#### List all containers
```
docker ps -a

CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                      NAMES                           
6898625112f3        mongo               "docker-entrypoint.s…"   4 minutes ago       Up 4 minutes        0.0.0.0:27017->27017/tcp   mongo                             
```

#### Stop container
```
docker stop mongo
```

#### Start container
```
docker start mongo
```

#### Remove container
```
docker rm mongo
```

#### Remove image
```
docker rmi {IMAGE ID}
```

## Dockerfile

There are many images that are avilable for you to use on Docker Hub, however most times we need to design a custom image instead. That is where the Dockerfile comes into play.

{{< gist SDiamante13 50a3d0fd56ce66fa1ee0c4cf87add0ae >}}

This is a specific set of instructions on how to build the image and what commands to run once a container is built from this image.

Our Dockerfile is simple. The container will run the jar and give it a mongodb related property.

## Build the image

Before building our image, let's build an application jar using gradle:

```
./gradlew clean build -x test
```

Now build the image:

```
docker build -t springboot-mongo .
```

This command is building an image off of the Dockerfile in the current directory. The image will be tagged with the name springboot-mongo.

## Run a container and link it to the already running mongo container

```
docker run -d -p 8085:8085 --name springboot-mongo --link=mongo  springboot-mongo
```

## Test out the Rest API

Open up Chrome or an API development enviroment like Postman or Insomnia and try it out!

I'll be using Postman to show that the Rest Controller is operating as expected.

#### Get all employees

![alt text](/images/postman_mongo.png)

#### Create new employee

![alt text](/images/postman_mongo_create.png)

#### Update existing employee

![alt text](/images/postman_mongo_update.png)

#### Delete an employee

![alt text](/images/postman_mongo_delete.png)

#### Now Bobby is gone

![alt text](/images/postman_mongo_getAll.png)

## Conclusion

Docker is a fantastic tool that is utilized in all environments. If you are just testing an application or you are deploying it through a CI/CD pipeline you'll want to get the help of containers.

When I rotated onto the Android team at my job I utilized Docker right away. We were using a sandbox application to mock our server. We would have IntelliJ running the sandbox application and hit it with the emulator in Android Studio. We spent so much time waiting because two huge IDEs were running at the same time.

{{< gist SDiamante13 a15fdcd637cb32ccdf9ba6e75e7ca307 >}}

I took the initiative and built the sandbox a docker container. I also wrote a bash script to quickly run all the commands neccessary and restart the sandbox whenever necessary. The team loved it and continues to see the time saved every day.

































