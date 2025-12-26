# eks-hands-on-workshop
Demonstrates end-to-end setup and deployment of applications on AWS EKS
## Credits
This project is based on the AWS sample project:
https://github.com/aws-samples/amazon-ecs-mythicalmisfits-workshop
Modified and extended for learning AWS EKS and Kubernetes.

## Overview
The goal is to showcase practical knowledge of Kubernetes, AWS networking, IAM, and CI/CD-ready infrastructure.

## Technologies Used
- AWS EKS
- eksctl
- Kubernetes (Deployment, Service, Ingress)
- AWS IAM
- ALB Ingress Controller
- Helm
- Docker
- AWS ECR

## Architecture
![EKS Architecture](architecture/eks-architecture.png)

## What I Implemented
- Created EKS cluster using eksctl
- Configured IAM roles for service accounts (IRSA)
- Deployed containerized application from ECR
- Exposed application using ALB Ingress
- Used Helm for application deployment
- Implemented basic monitoring

## Step-by-Step Implementation
1. Created EKS cluster
2. Configured node groups and IAM
3. Built and pushed Docker image to ECR
4. Deployed application using Kubernetes manifests
5. Configured ingress with ALB
6. Verified application access

## Challenges & Learnings
- Understood how IAM roles are mapped to Kubernetes service accounts
- Debugged ImagePullBackOff issues
- Learned how ALB Ingress dynamically creates AWS Load Balancers

## How to Run This Project
(Commands here)

## Clean-Up
(To avoid AWS charges)

