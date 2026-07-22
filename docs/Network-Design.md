# Network Design

## Overview

This project follows a Three-Tier Architecture to provide a secure, scalable, and highly available web application environment on Amazon Web Services (AWS).

The infrastructure is divided into three logical layers:

- Presentation Layer
- Application Layer
- Database Layer

Each layer is isolated using dedicated subnets and controlled through route tables and security groups.

---

# Architecture Diagram

```
                        Internet
                            │
                       Internet Gateway
                            │
                  Application Load Balancer
                            │
        ┌───────────────────┴───────────────────┐
        │                                       │
  Public Subnet 1                         Public Subnet 2
 (web-pub-sub1)                         (web-pub-sub2)
        │
   Bastion Host
        │
────────────────────────────────────────────────────────────
                Private Application Layer
────────────────────────────────────────────────────────────
        │                                       │
 App Server 1                           App Server 2
(app-pvt-sub1)                        (app-pvt-sub2)
        │                                       │
        └───────────────────┬───────────────────┘
                            │
────────────────────────────────────────────────────────────
                  Private Database Layer
────────────────────────────────────────────────────────────
                            │
                     Amazon RDS MySQL
                db-pvt-sub1 / db-pvt-sub2
```

---

# VPC Configuration

| Property | Value |
|----------|-------|
| VPC Name | awsProject-vpc |
| CIDR Block | 20.0.0.0/20 |

The VPC provides an isolated virtual network for all AWS resources used in this project.

---

# Subnet Design

## Public Subnets

| Name | CIDR |
|------|------|
| web-pub-sub1 | 20.0.1.0/24 |
| web-pub-sub2 | 20.0.2.0/24 |

Resources deployed:

- Bastion Host
- NAT Gateway
- Application Load Balancer

Purpose:

- Internet-facing resources
- Administrative access
- Outbound internet connectivity for private resources

---

## Private Application Subnets

| Name | CIDR |
|------|------|
| app-pvt-sub1 | 20.0.3.0/24 |
| app-pvt-sub2 | 20.0.4.0/24 |

Resources deployed:

- EC2 Application Server 1
- EC2 Application Server 2

Purpose:

- Host web application
- Prevent direct internet exposure

---

## Private Database Subnets

| Name | CIDR |
|------|------|
| db-pvt-sub1 | 20.0.5.0/24 |
| db-pvt-sub2 | 20.0.6.0/24 |

Resources deployed:

- Amazon RDS MySQL

Purpose:

- Secure database layer
- No public internet access

---

# Traffic Flow

## User Request

```
User
      │
Application Load Balancer
      │
Application Servers
      │
Amazon RDS
```

Users access the application through the Application Load Balancer. The load balancer distributes incoming traffic between the application servers, which process requests and communicate with the Amazon RDS database.

---

# Administrative Access

```
Administrator
        │
SSH
        │
Jump Server
        │
SSH
        │
Private Application Servers
```

The Bastion Host provides secure SSH access to the private EC2 instances.

---

# Internet Connectivity

Public Resources

```
Internet
      │
Internet Gateway
      │
Public Subnets
```

Private Resources

```
Private EC2
      │
NAT Gateway
      │
Internet Gateway
      │
Internet
```

Private instances can download software updates without being directly accessible from the internet.

---

# High Availability

The infrastructure is deployed across two Availability Zones.

Benefits include:

- Improved fault tolerance
- Reduced downtime
- Load distribution
- Better application availability

---

# Security Design

The following security measures were implemented:

- Public and private subnet isolation
- Bastion Host for SSH access
- Security Groups for controlled communication
- Private EC2 instances
- Private Amazon RDS deployment
- No direct internet access to the database
- Controlled database access using Security Groups

---

# Design Benefits

- Secure network architecture
- High availability across multiple Availability Zones
- Scalable application layer
- Private database deployment
- Centralized administrative access
- AWS networking best practices
- Production-style infrastructure design