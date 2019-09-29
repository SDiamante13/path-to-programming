---
title: "Api Security"
date: 2019-07-15T16:01:29-05:00
tags: [spring, security, api, springboot, rest]
featured_image: '/images/spring-security.png'
description: "A guide to securing a REST API using Spring Security and JWT token authentication."
draft: true
---

## Overview -- Securing the API 

Today we are going to explore securing an endpoint using JWT token authentication. All the code can be found on my [github](https://github.com/SDiamante13/ordering-system). The endpoint we are securing is for the backend of an E-Commerce website. There are currently 3 controllers that all interact with a PostgreSQL database using all the CRUD operations. The goal we have is to only allow read-only calls to unauthenticated users. Users must have an admin role to be able to create, update, and delete resources.

## Basic Assumptions

Since we are diving into a project that has already been started, I am assuming you have some knowledge of Spring Boot and how to write a rest controller.

## Overview -- Current State

To simplify things, let's just focus in on one of the controllers for now. This is the customer controller.


[gist]()

[Insomnia screenshot of POST create customer]

## Project dependencies

##### Add the following gradle dependencies:
```
implementation 'org.springframework.boot:spring-boot-starter-security'
implementation 'io.jsonwebtoken:jjwt:0.9.1'

testImplementation 'org.springframework.security:spring-security-test:5.1.5.RELEASE'
```

## Entity

Let's create an entity that we will use to store user credentials.

[Gist of User]

## Repository

[Gist of UserRepository]

## Service

[Gist of CustomUserDetailsService]

## JwtTokenProvider

[Gist of JwtTokenProvider]

## JwtTokenFilter

Explain what each is doing

[Gist of JwtTokenFilter]

## JwtConfigurer

[Gist of JwtConfigurer]


## WebSecurityConfigurerAdapter

[Gist of SecurityConfiguration]




