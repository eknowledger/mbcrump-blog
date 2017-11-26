---
layout: post
title: "Azure Tips and Tricks Part 57 - Docker Registry vs. Docker Repository"
excerpt: "Learn the difference between a docker registry and docker repository"
tags: [azure, windows, portal, cloud, developers, tipsandtricks]
share: true
comments: true
---

## Intro

Most folks aren't aware of how powerful the [Azure](http://www.azure.com) platform really is. As I've been presenting topics on Azure, I've had many people say, "How did you do that?" So I'll be documenting my tips and tricks for Azure in these posts.

## The Complete List of Azure Tips and Tricks

[Available Now!](https://michaelcrump.net/azure-tips-and-tricks-complete-list/){: .btn .btn--success} 

## Docker Registry vs. Docker Repository

Last week, we used [Docker Compose](http://www.michaelcrump.net/azure-tips-and-tricks55/) to create an image using our existing [ASP.NET WebAPI project](http://www.michaelcrump.net/azure-tips-and-tricks54/) and push it to Docker Cloud. I also covered deploying it to Azure using [Web App for Containers](http://www.michaelcrump.net/azure-tips-and-tricks56/). The bit of feedback that I feel that I didn't drive home was the difference between Docker Registry and Docker Repository. I wanted to cover that today. 

## Docker Registry

Docker Registry is a service that **stores** your docker images, but it could be hosted by a third party and even private if you need so. A couple of examples are:

* [Azure Container Registry](https://azure.microsoft.com/en-us/services/container-registry/)
* [Docker Hub](https://hub.docker.com/)
* [Quay Enterprise](https://coreos.com/quay-enterprise/docs/latest/)

There are also other choices such as Google or AWS Container Registry. 

## Docker Repository

A Docker Repository is a **collection** of related images with same name, that have different tags. Tags are an alphanumeric identifier attached to images within a repository (e.g., 1.1 or latest).

So the command docker `pull microsoft/aspnetcore:latest` will download the image tagged `latest` within the `microsoft/aspnetcore` repository from the Docker Hub registry.

To wrap it up. Look at the image below. We have a Docker Repository named `microsoft/aspnetcore` that is stored in a Docker Registry using Docker Hub. 

<img style="border:3px solid #021a40" src="/files/explaindocker1.png">

We could click on `tags` and pull the latest version with `pull microsoft/aspnetcore:latest` or version 1.1 with `pull microsoft/aspnetcore:1.1`

<img style="border:3px solid #021a40" src="/files/explaindocker2.png">

This is very confusing for me, so I hope this helps make sense of it all. 

## Want more Azure Tips and Tricks?

If you'd like to learn more Azure Tips and Tricks, then follow me on [twitter](http://twitter.com/mbcrump){: .btn .btn--success} or stay tuned to this blog! I'd also love to hear your tips and tricks for working in Azure, just leave a comment below. 