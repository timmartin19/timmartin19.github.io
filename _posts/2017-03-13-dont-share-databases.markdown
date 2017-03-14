---
layout:     post
title:      "Microservices Don't Let Microservices Share Databases"
date:       2017-03-13 19:38:00 -0500
categories: software microservices
tags: software microservices databases
---

&nbsp;&nbsp;&nbsp;&nbsp;It seems like the first thing people do when they
decide that they want to build microservices.  They split out a bunch of services
from the monolithic application, wash their hands, and declare themselves a 
microservice based architecture.  The problem is that their architecture is
not independent.  Everything still relies on a centralized database.

&nbsp;&nbsp;&nbsp;&nbsp;So the architecture went from a monolithic application with a monolithic database
to multiple applications with a monolithic database.

![monolithic-to-microservices]({{site.url}}/assets/images/monolithic-to-microservice.jpg)

&nbsp;&nbsp;&nbsp;&nbsp;What happens when database table needs to be updated?  What was previously a simple migration
and then deploy of a single application now requires updates to a series of 
applications.  Even worse, you have to coordinate deploys or multiple services
will break.  If you've never had to coordinate deploys in a "microservice" architecture,
consider yourself lucky.  Everything grinds to a halt and nobody can get any work done.
Suddenly, your microservice architecture requires intense coordination on every deploy
and your team is about to post to Medium about how Microservices are Satan's gift
to the world.

&nbsp;&nbsp;&nbsp;&nbsp;Instead of having "microservices" revolving around a centralized database,
side effects should be minimized.  Wherever possible, each database should
only have one dependent microservice.

![microservices-and-micro-dbs]({{site.url}}/assets/images/microservices-with-microdatabases.jpg)

&nbsp;&nbsp;&nbsp;&nbsp;If microservice A requires data from database B, don't directly access database B.
Instead, microservice B should provide the data to microservice A.  This way,
the contract between microservice A and microservice B is clearly defined rather
than implicitly through a centralized database.
