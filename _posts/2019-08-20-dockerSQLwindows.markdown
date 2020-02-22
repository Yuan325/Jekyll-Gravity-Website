---
layout: post
title:  "Windows container SQL server -- Docker"
date:   2019-08-20 15:30:00
categories: "computerscience"
---

From Beginner; For Beginner

I heard a lot about docker, and how simple it make things, however, when I first started, IT WAS NOT SIMPLE.
Maybe because I was new to the whole IT or Development world, or solely because I can't grasp the concept behind the whole container thing.
Well, I am still confused about it now, perhaps, just not as confused as I was before!

### What is DOCKER??? 
<blockquote> Dockerfile <br> Docker image <br> Docker Container</blockquote>

### Which DOCKER should I use???
This question hits me so hard! I stumbled around and got stucked just because I was either using the wrong version of Docker, or the wrong operating system.
To begin, I started using docker within Windows Server 2016 VM. There was not a lot of information online about windows container/docker; specifically for server 2016. _in fact, most of the threads are from 2 years ago? which utilize the older version of docker._ Docker changed a lot since then. From Docker Community Edition for Windows to Docker Desktop for Windows... I wanted the latest docker version to utilize the newest feature, and also, going through docker online courses! As a student solely planning on learning about it, I didn't want to pay for Docker Enterprise. _which might be an option I guess?_

Guess what?? It took me *weeks* to figure out that *The latest Docker can't really run on Windows Server 2016*. Maybe I was doing something wrong? I just couldn't get it configured properly on my machine. _yeap, it sucks_

At some point, I gave up and installed _Docker Desktop for Windows_ on my local laptop that is running *Windows 10*. AND IT WORKED. 

So yeap! Windows 10 it is!

### Getting Started ! 
Of note, I wanted to run it in windows container (instead of Linux container). Tested out ```docker run hello-world``` and it worked. _I was SOOOO excited_

Alright, let's get straight into the topic! -- Running SQL server in docker windows container.
I am not going to give a long explaination on WHY each step were taken. I went through the article that I cited below, and these are the final few piece of codes that I used to get docker working on my laptop.
P/S: these were all executed in PowerShell

```
docker pull microsoft/mssql-server-windows-developer: 2017-latest
``` 
```
docker run -d -p 1400:1433 --name <name> -e sa_password=<Password> -e ACCEPT_EULA=Y microsoft/mssql-server-windows-developer:2017-latest
```
```
sqlcmd -S <IP address>,<port> -U SA -P “<Password>”
```
If IP address is unknown,check with using the below code
```
ipconfig
```
if sqlcmd is working correctly, you should be in SQL! 
Just do the following queries and it should bring you what you need.
```
PRINT "Hello World";
GO
```
or
```
SELECT @@version;
GO
```


WOOHOO! THANK YOU FOR READING! Hope you are having fun with DOCKER right now!

<hr color="#DCDCDC" size="5">
Source:

><https://nexxtjump.com/2017/12/12/step-by-step-guide-to-run-sql-server-in-a-windows-docker-container/>
<br>
><https://docs.microsoft.com/en-us/sql/linux/sql-server-linux-configure-docker?view=sql-server-2017>

