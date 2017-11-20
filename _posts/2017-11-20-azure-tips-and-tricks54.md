---
layout: post
title: "Azure Tips and Tricks Part 54 - Getting a .NET Core WebAPI Project Ready for Docker"
excerpt: "Learn how to get a .NET Core WebAPI Project ready for docker"
tags: [azure, windows, portal, cloud, developers, tipsandtricks]
share: true
comments: true
---

## Intro

Most folks aren't aware of how powerful the [Azure](http://www.azure.com) platform really is. As I've been presenting topics on Azure, I've had many people say, "How did you do that?" So I'll be documenting my tips and tricks for Azure in these posts.

## The Complete List of Azure Tips and Tricks

[Available Now!](https://michaelcrump.net/azure-tips-and-tricks-complete-list/){: .btn .btn--success} 

## Getting a .NET Core WebAPI Project Ready for Docker

How hard do you think it is to:

* [Today - Create and Publish a .NET Core WebAPI project](http://www.michaelcrump.net/azure-tips-and-tricks54/)
* Add it to a Docker Container using Docker Compose and push it to a Docker Hub
* Use it in Azure with Web App for Containers

In this mini-series, we'll cover each part starting with creating and publishing a .NET Core WebAPI project. Tomorrow, we'll use Docker Compose to create an image and push it to Docker Hub and we'll wrap up by deploying it to Azure using Web App for Containers. 

## Create a .NET Core WebAPI Project

Ensure [.NET Core](https://www.microsoft.com/net/learn/get-started/windows) is installed and then follow the direction below: 

Create a directory on your HDD `mkdir mbcwebapi`. Now `cd mbcwebapi` into it. 
Create another directory inside your mbcwebapi folder `mkdir mbcwebapi`. Now `cd mbcwebapi` into it. 
Run `dotnet new webapi` to scaffold a new ASP.NET WebAPI Project. 

```text
Michaels-MacBook-Pro:mbcwebapi mbcrump$ dotnet new webapi
The template "ASP.NET Core Web API" was created successfully.
This template contains technologies from parties other than Microsoft, see https://aka.ms/template-3pn for details.

Processing post-creation actions...
Running 'dotnet restore' on /Users/mbcrump/mbcwebapi/mbcwebapi.csproj...
  Restoring packages for /Users/mbcrump/mbcwebapi/mbcwebapi.csproj...
  Restore completed in 35.83 ms for /Users/mbcrump/mbcwebapi/mbcwebapi.csproj.
  Generating MSBuild file /Users/mbcrump/mbcwebapi/obj/mbcwebapi.csproj.nuget.g.props.
  Generating MSBuild file /Users/mbcrump/mbcwebapi/obj/mbcwebapi.csproj.nuget.g.targets.
  Restore completed in 1.96 sec for /Users/mbcrump/mbcwebapi/mbcwebapi.csproj.

Restore succeeded.
```
If you use `dotnet run` then you'll have a URL that you can paste into your browser. Ensure you add `http://localhost:5000/api/values` to see a response, otherwise the site will 404. 

You should see `["value1","value2"]`. Nice! It is working properly!

## Publish the .NET Core WebAPI

The `dotnet publish` command packs the application and its dependencies into a folder for deployment to a hosting system. We are going to prep our project for Docker, so use `dotnet publish -c Release -o ./obj/Docker/publish`. 

```text
Michaels-MacBook-Pro:mbcwebapi mbcrump$ dotnet publish -c Release -o ./obj/Docker/publish
Microsoft (R) Build Engine version 15.3.409.57025 for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  mbcwebapi -> /Users/mbcrump/mbcwebapi/bin/Release/netcoreapp2.0/mbcwebapi.dll
  mbcwebapi -> /Users/mbcrump/mbcwebapi/obj/Docker/publish/
Michaels-MacBook-Pro:mbcwebapi mbcrump$ 
```

If you navigate to the /obj/Docker/publish folder, then you will see our WebAPI is packaged and ready for deployment. 

```text
11/19/2017  12:12 PM               178 appsettings.Development.json
11/19/2017  12:12 PM               228 appsettings.json
11/19/2017  12:41 PM           284,199 mbcwebapi.deps.json
11/19/2017  12:41 PM             6,656 mbcwebapi.dll
11/19/2017  12:41 PM             1,312 mbcwebapi.pdb
11/19/2017  12:41 PM             2,560 mbcwebapi.PrecompiledViews.dll
11/19/2017  12:41 PM             7,680 mbcwebapi.PrecompiledViews.pdb
11/19/2017  12:41 PM               221 mbcwebapi.runtimeconfig.json
11/19/2017  12:41 PM               383 web.config
```

Success! We now have created and published a .NET Core WebAPI project. Come back tomorrow as we'll use Docker Compose to create an image that we'll use with [Web App for Containers](https://azure.microsoft.com/en-us/services/app-service/containers/).

## Want more Azure Tips and Tricks?

If you'd like to learn more Azure Tips and Tricks, then follow me on [twitter](http://twitter.com/mbcrump){: .btn .btn--success} or stay tuned to this blog! I'd also love to hear your tips and tricks for working in Azure, just leave a comment below. 