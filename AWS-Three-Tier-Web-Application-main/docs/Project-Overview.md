# Project Overview

## Introduction

This project demonstrates the implementation of a secure, scalable, and highly available Three-Tier Web Application Architecture on Amazon Web Services (AWS).

The infrastructure is designed by following AWS networking best practices. It separates the application into three logical layers to improve security, scalability, and maintainability.

- Presentation Layer (Public)
- Application Layer (Private)
- Database Layer (Private)

The architecture uses multiple Availability Zones (AZs) to provide high availability and fault tolerance.

---

# Objectives

The main objectives of this project are:

- Design a custom Amazon VPC
- Create public and private subnets
- Configure secure network routing
- Deploy application servers in private subnets
- Use a Bastion Host (Jump Server) for secure administration
- Install Apache, PHP, and phpMyAdmin on application servers
- Configure an Application Load Balancer (ALB)
- Deploy a private Amazon RDS MySQL database
- Connect phpMyAdmin to the RDS database
- Follow AWS security best practices

---

# Architecture Components

## Networking

- Amazon VPC
- Public Subnets
- Private Application Subnets
- Private Database Subnets
- Internet Gateway
- NAT Gateway
- Route Tables
- Elastic IP

---

## Compute

- Jump Server (Bastion Host)
- Application Server 1
- Application Server 2

---

## Load Balancing

- Application Load Balancer
- Target Group
- Health Checks

---

## Database

- Amazon RDS MySQL
- DB Subnet Group

---

## Security

- Security Groups
- Private Networking
- Controlled SSH Access
- Database Isolation

---

# Architecture Workflow

1. Users access the application through the Application Load Balancer.
2. The Application Load Balancer distributes incoming traffic across multiple EC2 application servers.
3. The application servers are deployed inside private subnets and are not directly accessible from the internet.
4. Administrative access is performed securely through the Bastion Host located in the public subnet.
5. The application communicates with the Amazon RDS MySQL database hosted inside private database subnets.
6. Security Groups control communication between each layer of the architecture.

---

# AWS Services Used

- Amazon VPC
- Amazon EC2
- Amazon RDS
- Application Load Balancer
- Target Groups
- Internet Gateway
- NAT Gateway
- Route Tables
- Security Groups
- Elastic IP

---

# High Availability Features

- Multi-AZ Deployment
- Multiple Public Subnets
- Multiple Private Application Subnets
- Multiple Private Database Subnets
- Application Load Balancer
- Health Checks
- Redundant Application Servers

---

# Security Features

- Private Application Servers
- Private Database Servers
- Bastion Host for Secure SSH Access
- Restricted Security Group Rules
- No Public Access to Amazon RDS
- Controlled Database Connectivity

---

# Project Outcome

By completing this project, a complete production-style AWS three-tier architecture was successfully deployed. The environment provides secure networking, load balancing, high availability, and private database connectivity while following AWS best practices.

This project demonstrates practical knowledge of AWS networking, compute, load balancing, and database services, making it a strong portfolio project for Cloud Engineer and DevOps Engineer roles.