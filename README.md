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

