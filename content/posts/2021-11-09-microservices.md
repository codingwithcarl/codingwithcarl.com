+++ 
draft = false
date = 2021-11-09T19:44:40-05:00
title = "Microservices"
description = "An introduction to microservices with examples."
slug = ""
authors = []
tags = []
categories = []
externalLink = ""
series = []
+++
As a prerequisite to [containers](https://www.codingwithcarl.com/posts/2021-11-30-docker/) and how applications are developed today, we need an introduction to microservices and the monolithic architecture. 

## Monoliths

Monolithic architecture is a design style based on a single application. In the Java domain, an application is complied into a .jar or .war file and deployed as a whole into a production environment. Applications that follow a monolithic architecture are notoriously hard to maintain, tightly coupled, and difficult to understand. 

## Understanding Microservices

There is no single definition for microservices. A consensus view has evolved over time in the industry.

To me, a *microservice* is a "mini-service" / "mini-app" that is built within the larger context of the whole application. Similar to the Unix philosophy, a microservice should do only one thing and one thing well.

A *microservice model* or *microservice architecture* is the design style around microservices. When someone states that the application follows the microservices model, they are talking about how the application is built, rather than an individual microservice.

The application should be structured as loosely coupled, easily deployable, testable, and organized in a well defined business domain.

1. Loosely Coupled: Services have little or no knowledge about other components and there are few or no dependencies between these components.

2. Easily Deployable: Services can be deployed independently of each other. An automated CI/CD pipeline has been built to easily deploy and implement changes quickly and not impact any of the associated services.

3. Testable: Each microservice should be able to be tested on it's own. Ideally, automated testing written within the CI/CD pipeline would handle most of this.

4. Well defined business domain: Each microservice is logically separated and generally "make sense" within the context of the business domain at hand.

## Example

An application following the microservice architecture will have it's functionality logically separated.

- UI

- Database

- Recommendation Engine

- Cart Service

- Payment Service

- Reporting Function

## Summary

| Monolith                                         | Microservices                         |
|:------------------------------------------------:|:-------------------------------------:|
| server-side system based on a single application | every app function is its own service |
| easy to develop, deploy, manage                  | own container                         |
| single application                               | communicate via APIs                  |
| highly dependent codebase                        | loosely coupled codebase              |
| scaling problems                                 | independent scaling                   |
| high risk in change                              | less risk in change                   |
| lengthy iteration process                        | iterate at will / DevOps Pipeline     |

A microservice architecture, a variant of the service-oriented architecture structural style, arranges an application as a collection of loosely-coupled services. In a microservices architecture, services are fine-grained and the protocols are lightweight.

---

#### References

[Diagram: Monolith vs Microservices - Google Drive](https://drive.google.com/file/d/1oNH0nIvrd2vkuRWIWvfHPjAnaZSalsNk/view?usp=sharing)

[AWS for Solutions Architects | Packt](https://www.packtpub.com/product/aws-for-solutions-architects/9781789539233)

[Docker for Developers | Packt](https://www.packtpub.com/product/docker-for-developers/9781789536058)

[What are Microservices? - YouTube](https://www.youtube.com/watch?v=CdBtNQZH8a4)

[What Are Microservices And How To Succeed With Them - YouTube](https://youtu.be/k67TMBC6tyo)

[Getting Started With Microservices - YouTube](https://youtu.be/S8Aiqws3N5o)

[Microservices - YouTube](https://youtu.be/y8OnoxKotPQ)
