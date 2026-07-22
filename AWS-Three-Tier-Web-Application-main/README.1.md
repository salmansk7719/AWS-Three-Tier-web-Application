# AWS Three-Tier Web Application on AWS

![AWS](https://img.shields.io/badge/AWS-Cloud-orange)
![EC2](https://img.shields.io/badge/EC2-Compute-blue)
![VPC](https://img.shields.io/badge/VPC-Network-green)
![RDS](https://img.shields.io/badge/RDS-Database-red)
![ALB](https://img.shields.io/badge/Application_Load_Balancer-Load_Balancing-yellow)

## 📖 Project Overview

This project demonstrates the implementation of a secure and highly available Three-Tier Web Application Architecture on Amazon Web Services (AWS).

The infrastructure is designed using AWS networking best practices and consists of three logical layers:

- Presentation Layer
- Application Layer
- Database Layer

The application is deployed inside a custom Amazon VPC with public and private subnets across multiple Availability Zones. Internet-facing traffic is distributed using an Application Load Balancer, while backend application servers remain in private subnets. The database is hosted securely on Amazon RDS without public access.

---

# 🏗 Architecture

> Add your architecture diagram here.

Example

```
Internet
      │
Route53 (Optional)
      │
Application Load Balancer
      │
──────── Public Subnets ────────
│                               │
Jump Server                 NAT Gateway
│
──────── Private App Subnets ───
│               │
App Server 1    App Server 2
        │
──────── Private DB Subnets ────
│
Amazon RDS MySQL
```

---

# 🚀 AWS Services Used

- Amazon VPC
- Public & Private Subnets
- Internet Gateway
- NAT Gateway
- Route Tables
- Security Groups
- Amazon EC2
- Application Load Balancer
- Target Groups
- Amazon RDS (MySQL)
- Elastic IP

---

# 📁 Repository Structure

```
AWS-Three-Tier-Web-Application/

├── README.md
├── LICENSE
├── architecture/
├── screenshots/
├── docs/
└── diagrams/
```

---

# 📌 Project Implementation

## Part 1 – Network Infrastructure

- Created Custom VPC
- Configured Public Subnets
- Configured Private Application Subnets
- Configured Private Database Subnets
- Created Internet Gateway
- Created NAT Gateway
- Configured Route Tables
- Associated Route Tables

---

## Part 2 – Compute Layer

- Created Jump Server (Bastion Host)
- Created Two Private EC2 Instances
- Configured Security Groups
- Installed Apache
- Installed PHP
- Installed phpMyAdmin
- Created Target Group
- Configured Application Load Balancer
- Verified Load Balancing

---

## Part 3 – Database Layer

- Created DB Subnet Group
- Created Amazon RDS MySQL Database
- Configured Database Security Group
- Connected phpMyAdmin with RDS
- Enabled Target Group Stickiness
- Verified Database Connectivity

---

# 📷 Screenshots

Screenshots are available inside:

```
screenshots/
```

---

# 📚 Documentation

Detailed implementation steps are available inside the **docs/** directory.

- Project Overview
- Network Design
- Part 1 Documentation
- Part 2 Documentation
- Part 3 Documentation
- Learning Notes

---

# 🎯 Learning Outcomes

Through this project I learned:

- AWS VPC Networking
- CIDR Planning
- Public & Private Subnets
- Internet Gateway
- NAT Gateway
- Security Groups
- EC2
- Bastion Host Architecture
- Apache Web Server
- PHP Installation
- phpMyAdmin
- Application Load Balancer
- Target Groups
- Amazon RDS
- Three-Tier Architecture
- High Availability Design
- AWS Networking Best Practices

---

# 👨‍💻 Author

**Salman Shaikh**

AWS Cloud & DevOps Engineer

LinkedIn:
https://www.linkedin.com/in/salmansk7719

GitHub:
https://github.com/salmansk7719

---

## ⭐ If you found this project helpful, please consider giving it a Star.