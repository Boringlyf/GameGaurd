# GameGaurd
> Continuous Infrastructure Security Monitoring for AWS EKS-Based Game Platforms

## Purpose

This project is designed to understand how security vulnerabilities and misconfigurations in cloud-native game infrastructure can be identified, monitored, and visualized using Elastic.

It simulates a modern AWS and Kubernetes-based gaming environment and demonstrates how Infrastructure-as-Code (IaC) security scanning tools like Checkov and Trivy can detect misconfigurations, and how these findings can be centralized into Elasticsearch and visualized through Kibana dashboards.

The goal is to gain hands-on experience in securing cloud-native game systems, building security monitoring pipelines, and translating IaC security findings into actionable insights for DevSecOps, game studios, and MSSP environments.


## Lab Setup
### What we need
- Create and configure a VPC
- Create and configure subnets
- Deploy EC2 instances ( 2 VMs - 1 for Elastic, 1 for Scanner like trivy and checkov)
- Create and configure EKS cluster
- Create and configure S3 bucket (this is where scan results will be stored)

### Create and Configure VPC on AWS

A dedicated Virtual Private Cloud (VPC) was created to simulate a realistic cloud-native gaming environment. The VPC provides network isolation and serves as the foundation for hosting the Elastic Stack, IaC scanning infrastructure, and the Amazon EKS cluster. Public and private subnets were configured to separate internet-facing resources from backend game services, following security best practices commonly used in modern game studio cloud architectures.


<img width="1512" height="870" alt="image" src="https://github.com/user-attachments/assets/f38a82ba-3b77-4566-938b-089a030420cf" />

<img width="1889" height="715" alt="image" src="https://github.com/user-attachments/assets/bbb4db4e-74e7-41d6-a20c-c20481360a9c" />



### Create and Configure multiple Subnets within the VPC

Public and private subnets were created across multiple Availability Zones to simulate a production-grade cloud environment for online gaming services. Public subnets to host the internet-facing components such as the Elastic Stack and security scanning infrastructure, while private subnets host the Amazon EKS worker nodes and backend game services. This network segmentation follows cloud security best practices and provides a realistic lab environment for monitoring, detecting, and visualizing infrastructure security risks.

#### Public Subnets will host
- Elastic Server EC2
- Scanner Server EC2

#### Private Subnets will host
- EKS Worker Nodes
- Redis
- Matchmaking Service
- Game API
- Leaderboard Service

#### Subnets created: (In my case)
- Public subnet a (10.0.1.0/24)
- Public subnet b (10.0.2.0/24)
- Private subnet a (10.0.11.0/24)
- Private subnet b (10.0.12.0/24)

<img width="1910" height="811" alt="image" src="https://github.com/user-attachments/assets/126115d2-7538-4d7c-aadf-b155a0f19468" />

<img width="459" height="617" alt="image" src="https://github.com/user-attachments/assets/2cd5713b-ee5c-4ff0-ac7c-78e40c4b049d" />,

#### Add Tags to the private subnets that will host EKS worker nodes and backend game services
> EKS uses subnet tags to determine where to place resources.

##### Tags to add to subnets created:
<img width="1300" height="620" alt="image" src="https://github.com/user-attachments/assets/e848ed46-c343-4232-abd7-fd8b75719403" />
<img width="1289" height="615" alt="image" src="https://github.com/user-attachments/assets/801c9cf5-fdc7-416a-ae8f-23d287c4619f" />

These tags will allow EKS to create public load balancers when later game services are exposed down the line in this project.


