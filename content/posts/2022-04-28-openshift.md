+++ 
draft = false
date = 2022-04-28T20:43:25-04:00
title = "OpenShift"
description = "An introduction to OpenShift"
slug = ""
authors = []
tags = []
categories = []
externalLink = ""
series = []
+++

Red Hat OpenShift is a Kubernetes platform that enables a cloud-like experience everywhere it's deployed.

- Run containerized applications and workflows
- Can run in the cloud or on prem
- Powered by Kubernetes
- Comes with Red Hat support

### Archetechitural Layers

| the layers |
| ---------- |
| containers |
| OpenShift  |
| Kubernetes |
| RHEL       |
| AWS        |

### What it does

OpenShift can take care of the entire CI-CD pipeline where all the developer has to do is push their code to a repo (GitHub/BitBucket).

1. Dev pushes code to GitHub > hits a webhook
2. OpenShift creates a Jenkins job which builds a Docker image
3. Image is pushed to an image registry (i.e. AWS ECR)
4. OpenShift deploys the Docker image to a Kubernetes cluster(s)
5. OpenShift runs the image into a container on the Kubernetes cluster(s)

OpenShift can make these changes with no downtime to currently running applications. It can also use Ansible Playbooks to scale applications (adding hosts to the cluster).

## ROSA

**Red Hat Openshift Service on AWS**, or ROSA  provides an integrated experience to use OpenShift on AWS. It is a pay-as-you-go managed service that is jointly supported by Red Hat and Amazon. A developer can use the wide range of AWS compute, database, analytics, machine learning, networking, mobile, and other services to build secure and scalable applications. ROSA includes tools such as the [ROSA CLI](https://docs.openshift.com/rosa/rosa_cli/rosa-get-started-cli.html) to facilate this integrated experience.

---

#### References

[What is OpenShift - YouTube](https://youtu.be/KTN_QBuDplo)

[What is ROSA (Red Hat OpenShift Service on AWS)? - YouTube](https://youtu.be/6W-xDavWgYg)

[Red Hat OpenShift Service on AWS – Amazon Web Services](https://aws.amazon.com/rosa/)