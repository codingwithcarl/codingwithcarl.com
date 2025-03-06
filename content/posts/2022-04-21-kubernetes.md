+++ 
draft = false
date = 2022-04-21T22:40:16-04:00
title = "Kubernetes"
description = "An introduction to Kubernetes"
slug = ""
authors = []
tags = []
categories = []
externalLink = ""
series = []
+++

**Kubernetes**, also known as K8s, is an open-source system for automating deployment, scaling, and management of [containerized applications](https://www.codingwithcarl.com/posts/2021-11-30-docker/). Google originally designed Kubernetes, but the Cloud Native Computing Foundation now maintains the project.

Kubernetes opens up a huge universe of tools and techniques for running clustered applications with a vender-neutral, cloud-native approach. However, Kubernetes is a lot more involved and complex than using a managed service such as [AWS ECS](https://www.codingwithcarl.com/posts/2022-02-02-ecs/). Everything under the hood must be managed by an individual or the development team.

### Tech Requirements

These are the tools you'll need to get a local development environment started. 

1. [Docker](https://www.docker.com/)
2. [kubectl](https://kubernetes.io/docs/tasks/tools/)
3. [minikube](https://minikube.sigs.k8s.io/docs/start/)
4. [helm](https://helm.sh/docs/)

### Key Terminology

[**Pod:**](https://kubernetes.io/docs/concepts/workloads/pods/) a group of one or more [containers](https://kubernetes.io/docs/concepts/containers/), with shared storage and network resources, and a specification for how to run the containers. A pod is the smallest deployable units of computing that you can create and manage in Kubernetes.

[**Node:**](https://kubernetes.io/docs/concepts/architecture/nodes/) a virtual or physical machine that runs Kubernetes workloads. Kubernetes runs your workload by placing containers into Pods to run on Nodes. Each node is managed by the Control Plane and contains the services necessary to run Pods.

[**Cluster:**](https://www.vmware.com/topics/glossary/content/kubernetes-cluster.html) a set of nodes that run containerized applications. Kubernetes clusters allow containers to run across multiple machines and environments.

[**Control Plane:**](https://kubernetes.io/docs/reference/glossary/?all=true#term-control-plane)The container orchestration layer that exposes the API and interfaces to define, deploy, and manage the lifecycle of containers. 

[**Namespace:**](https://kubernetes.io/docs/concepts/overview/working-with-objects/namespaces/) provides a mechanism for isolating groups of resources within a single cluster. Namespaces enable users to divide cluster resources within the physical cluster among different teams via resource quotas.

[**ConfigMaps:**](https://kubernetes.io/docs/concepts/configuration/configmap/) an API object used to store non-confidential data in key-value pairs.

[**Services:**](https://kubernetes.io/docs/concepts/services-networking/service/) An abstract way of declaring how your application exposes its interfaces to the world.

[**Ingress Controller:**](https://kubernetes.io/docs/concepts/services-networking/ingress-controllers/) Kubernetes manages an internal network where the applications in a cluster can communicate with one another via a private network. By default, there is no way to reach applications running on the inside of a Kubernetes cluster from the outside. The Ingress Contoller plays a role of a proxy and connection broker. The contoller is also useful when you want a vendor-neutral way of granting access to Kubernetes applications.

[**Secrets:**](https://kubernetes.io/docs/concepts/configuration/secret/) an object that contains a small amount of sensitive data such as a password, a token, or a key. Such information might otherwise be put in a Pod specification or in a container image.

[**DaemonSet:**](https://kubernetes.io/docs/concepts/workloads/controllers/daemonset/) ensures that all (or some) Nodes run a copy of a Pod. As nodes are added to the cluster, Pods are added to them. As nodes are removed from the cluster, those Pods are garbage collected. Deleting a DaemonSet will clean up the Pods it created.

### Tools

[**minikube:**](https://kubernetes.io/docs/tutorials/hello-minikube/) a tool that lets you run Kubernetes locally.

[**kubectl:**](https://kubernetes.io/docs/reference/kubectl/) the Kubernetes CLI that allows you to run commands against Kubernetes clusters.

[**helm:**](https://helm.sh) the package manager for Kubernetes (think npm for node).

[**helm chart:**](https://helm.sh/docs/topics/charts/)  a collection of files that describe a related set of Kubernetes resources.

### GKE

[**Google Kubernetes Engine (GKE)**](https://cloud.google.com/kubernetes-engine) is Google's service for hosting containers in a Kubernetes-based environment. It's the most mature by cloud providers and includes the following features:

-  A single cluster quick start option for trailing the service

- Container vulnerability scanning

- Built-in data encryption

- Multiple channels for upgrading, repairing, and releasing

- Integration with Google monitoring services

- Automatic scaling and load balancing

- Google-managed hardware

### EKS

[**Amazon Elastic Kubernetes Service (Amazon EKS)**](https://aws.amazon.com/eks/features/) is Amazon's service for hosting containers in a Kubernetes-based environment. Amazon EKS automatically manages the availability and scalability of the Kubernetes control plane nodes responsible for scheduling containers, managing application availability, storing cluster data, and other key tasks:

- Serverless hosting via [AWS Fargate](https://www.codingwithcarl.com/posts/2022-02-09-fargate/) 

- Server deployment options on EC2

- Zero-downtime upgrades and patching

- Auto-detction of unhealthy nodes

- Hybrid hosting solutions with [AWS Outposts](https://aws.amazon.com/outposts/)  

- Kubernetes Jobs for batch processing

### OpenShift

[**OpenShift**](https://www.redhat.com/en/technologies/cloud-computing/openshift) is a collection of software developed by Red Hat geared toward containerized application architectures. It enables a cloud-like experience everywhere it's deployed making it vendor-neutral. OpenShift facilates many CI-CD funcitonality and features such as:

- Ability to create builds, test runs, and deployments

- Automated upgrades and life cycle management

- Open source code on [GitHub](https://github.com/openshift)

- Deploy in any cloud, in a data center, or on-premises 

- An image registry

- Monitoring and log aggregation 

### AKS

[**Azure Kubernetes Service (AKS)**](https://azure.microsoft.com/en-us/services/kubernetes-service/#overview) is Microsoft's service for hosting containers in a Kubernetes-based environment. It's great for those who are already familiar with Microsoft's cloud products and who may be looking for comparable Kubernetes features:

- Elastic provisioning of services

- Integration with the Azure DevOps and Monitor services

- Identity and Access Management with Active Directory

- Failure detection and container health monitoring

- Canary deployments

- Log aggregation

---

#### References

[Docker for Developers | Packt](https://www.packtpub.com/product/docker-for-developers/9781789536058)

[Kubernetes Documentation](https://kubernetes.io/docs/home/)

[GKE Documentation](https://cloud.google.com/kubernetes-engine/docs)

[EKS Documentation](https://docs.aws.amazon.com/eks/latest/userguide/getting-started.html)

[OpenShift Documentation](https://docs.openshift.com/) 

[AKS Documentation](https://docs.microsoft.com/en-us/azure/aks/)
