+++ 
draft = false
date = 2022-01-25T18:01:04-05:00
title = "Container Orchestration"
description = ""
slug = ""
authors = []
tags = []
categories = []
externalLink = ""
series = []
+++
*Container Orchestration* is all about managing the lifecycles of containers, especially in large, dynamic environments.

## Managed Cloud Services

- Google Kubernetes Engine (GKE)

- AWS Elastic Beanstalk (EB)

- AWS Elastic Container Service (ECS)

- AWS Elastic Kubernetes Service (EKS)

- Microsoft Azure Kubernetes Service (AKS)

- DigitalOcean Docker Swarm

All of the container orchestraion systems allow software developers and system adminstrators to run a fleet of servers that execute multiple containers simultaneously, with policy-based mechanisms for distributing multiple container instances among the cluster.

Container Orchestration is responsible for starting, monitoring, and moving container workloads from host to host as health checks and scaling contraints dicate.

### AWS ECS

ECS has two basic modalities:

- Containers run on a fleet of EC2 instances managed directly by the account owner

- Fargate: where AWS manages the nodes that container run on

---

#### References

[Docker for Developers | Packt](https://www.packtpub.com/product/docker-for-developers/9781789536058)

[What Is Container Orchestration? | New Relic](https://newrelic.com/blog/best-practices/container-orchestration-explained)

[AWS ECS](https://aws.amazon.com/ecs/)