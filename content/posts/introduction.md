---
title: "Introduction"
date: 2018-09-26T23:46:19-05:00
featured_image: '/images/road_beginning.jpeg'
draft: false
---

## What I do
I work in an Extreme Programming (XP) environment. XP is an agile methology that mainly consists of pair programming and test driven development (TDD). Pair programming has been very good to me as a new developer. I have gotten to work with very talented and experienced devs. I will go more in depth about XP practices in a future post.
___
## What I've learned 

* Linux
* Concourse (CI/CD)
* Docker
* Vim
* Sublime
* Git
* Gemfire
* Spring Integration
* TDD
* Android development
* IntelliJ Shortcuts

#### Linux
My first day on the job I learned that Linux is amazing! I had been avoiding it for a long time. I have never had a Mac or used any Linux environment on any of my PCs. I quickly learned outside of work the most common commands. One guy on my API team was a Linux Admin and has been programming for over 20 years. I was amazed at all of the cool things he was doing right from the bash shell.

I will talk much more about the other things I've learned in future posts.

![Linux] (/images/linux_lolcat.png)

___
## When are we going to program?

A major part of the XP methodology is automation. When we have written all of our tests and implemented the logic in our code, integrating these changes into existing code should be smooth and automatic. 

That is where a CI/CD pipeline comes into play.

![Concourse] (/images/concourse_deploy.png)

For our team to get to the point where deploying code is as simple as clicking a button, we must first put the work in first.

Much of my first few weeks were spent on designing Concourse pipelines, exploring the magical world of Docker, and fighting with network issues.

```
resources:
- name: concourse-pipeline-samples
  type: git
  source:
    branch: master
    uri: https://github.com/pivotalservices/concourse-pipeline-samples.git

- name: pks-release
  type: pivnet
  source:
    api_token: ((pivnet_token))
    product_slug: ((pks_product_slug))
    product_version: ((pks_product_version))
    sort_by: semver

- name: my-docker-image
  type: docker-image
  source:
    repository: pivotalservices/pks-kubectl
    username: ((dockerhub-username))
    password: ((dockerhub-password))
```

I quickly found myself wondering, "When am I going to actually program something in **Java**?


