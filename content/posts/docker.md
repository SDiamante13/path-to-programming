+++ 
draft = true
date = 2018-11-19T23:53:28-06:00
title = "Docker"
slug = "" 
tags = []
categories = []
+++

## Docker Introduction

I gaurantee you that any company you work for nowadays will be utilizing some kind of container for testing and deploying applications. The most popular of the container software is Docker. The main benefit of Docker is that if someone wants to run your application on their computer, they do not have to try to match your software versions just to run it. All they need to do is have Docker installed on their machine and they will be able to run your program in an isolated container that you have given the instructions on which version of software to run and how to launch the program. 

## Docker Terminology

A docker image is a mold that you can use to create containers out of. A docker container is the physical container that you run your program on. So a docker image can have many containers. A Dockerfile is a set of instructions that builds up your customized docker image. Tasks such as downloading specific files, running a linux package manager like apt-get or apk-get, and exposing ports for your application to use can be used to build your custom image.

## Let's Dockerize a Spring Boot App

I am going to show you how to "containerize" a simple Spring Boot App. Start by going to start.spring.io. Name your application and choose Spring Web. I will be using Gradle as the packager manager. Create a package named controller and a file under that package named HomeController. The file should look as such:
![HomeController] ()

Now run the application and see that it binds to port 8000. Open up your favorite web browser and navigate to localhost:8080/home. You will see the application running as normal. We will now create a Dockerfile that will allow us to run our REST API without needing IntelliJ open and our application running. 

## Docker Hub

Docker Hub is a place where you can find base images 

















