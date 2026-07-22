# Part 1 – VPC Network Infrastructure

## Objective

The objective of this phase was to build a secure and highly available network infrastructure for the three-tier web application. This included creating a custom VPC, configuring public and private subnets, and setting up internet connectivity using an Internet Gateway and NAT Gateway.

---

# Network Architecture

## VPC

| Property | Value |
|----------|-------|
| Name | awsProject-vpc |
| CIDR Block | 20.0.0.0/20 |

---

# Public Subnets

| Subnet Name | Availability Zone | CIDR Block |
|-------------|-------------------|------------|
| web-pub-sub1 | ap-south-1a | 20.0.1.0/24 |
| web-pub-sub2 | ap-south-1b | 20.0.2.0/24 |

Purpose:

- Host internet-facing resources
- Bastion Host (Jump Server)
- NAT Gateway

---

# Private Application Subnets

| Subnet Name | Availability Zone | CIDR Block |
|-------------|-------------------|------------|
| app-pvt-sub1 | ap-south-1a | 20.0.3.0/24 |
| app-pvt-sub2 | ap-south-1b | 20.0.4.0/24 |

Purpose:

- Host EC2 application servers
- Prevent direct internet access
- Allow internet access only through the NAT Gateway

---

# Private Database Subnets

| Subnet Name | Availability Zone | CIDR Block |
|-------------|-------------------|------------|
| db-pvt-sub1 | ap-south-1a | 20.0.5.0/24 |
| db-pvt-sub2 | ap-south-1b | 20.0.6.0/24 |

Purpose:

- Host Amazon RDS database
- Keep database isolated from the public internet

---

# Internet Gateway

| Name |
|------|
| my-igw |

Purpose:

- Provides internet connectivity to resources in the public subnets.

---

# NAT Gateway

| Name | Subnet |
|------|--------|
| my-nat | web-pub-sub1 |

Purpose:

- Allows resources in private subnets to access the internet for updates and package installation.
- Prevents inbound internet connections to private resources.

---

# Route Tables

## route-web

Associated Subnets

- web-pub-sub1
- web-pub-sub2

Routes

| Destination | Target |
|-------------|--------|
| 0.0.0.0/0 | Internet Gateway |

---

## route-app

Associated Subnets

- app-pvt-sub1
- app-pvt-sub2

Routes

| Destination | Target |
|-------------|--------|
| 0.0.0.0/0 | NAT Gateway |

---

## route-db

Associated Subnets

- db-pvt-sub1
- db-pvt-sub2

Routes

| Destination | Target |
|-------------|--------|
| 0.0.0.0/0 | NAT Gateway |

---

# Components Created

- Custom Amazon VPC
- 2 Public Subnets
- 2 Private Application Subnets
- 2 Private Database Subnets
- Internet Gateway
- NAT Gateway
- Elastic IP
- 3 Route Tables
- Route Table Associations

---

# Validation Performed

The following checks were completed after the network setup:

- Verified VPC creation
- Verified subnet creation
- Verified Internet Gateway attachment
- Verified NAT Gateway availability
- Verified Route Table associations
- Verified internet route (0.0.0.0/0) in public route table
- Verified NAT Gateway route for private subnets

---

# Outcome

A secure three-tier AWS network infrastructure was successfully deployed. Public resources have direct internet access through the Internet Gateway, while application and database resources remain protected inside private subnets and use the NAT Gateway for outbound internet connectivity.
