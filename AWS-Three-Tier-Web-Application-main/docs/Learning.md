# Learning

## Project Summary

This project provided hands-on experience in designing, deploying, and managing a secure Three-Tier Web Application Architecture on Amazon Web Services (AWS).

Throughout the implementation, I learned how different AWS networking, compute, and database services work together to build a scalable and highly available cloud infrastructure.

---

# AWS Services Learned

## Networking

- Amazon VPC
- CIDR Block Planning
- Public Subnets
- Private Application Subnets
- Private Database Subnets
- Internet Gateway
- NAT Gateway
- Elastic IP
- Route Tables
- Route Table Associations

---

## Compute

- Amazon EC2
- Amazon Linux
- Bastion Host (Jump Server)
- SSH Connectivity
- Security Groups
- Private EC2 Access

---

## Web Server

- Apache HTTP Server
- PHP 8.2
- PHP-FPM
- phpMyAdmin

---

## Load Balancing

- Application Load Balancer (ALB)
- Target Groups
- Health Checks
- Target Registration
- Session Stickiness

---

## Database

- Amazon RDS (MySQL)
- DB Subnet Group
- Database Security Groups
- Private Database Deployment
- RDS Endpoint Configuration

---

# Practical Skills Gained

- Designed a custom VPC from scratch.
- Planned IP addressing using CIDR blocks.
- Configured public and private subnets across multiple Availability Zones.
- Implemented secure internet access using an Internet Gateway and NAT Gateway.
- Created and managed EC2 instances.
- Configured Security Groups for controlled communication.
- Installed and configured Apache, PHP, and phpMyAdmin.
- Created and configured an Application Load Balancer.
- Configured Target Groups and Health Checks.
- Deployed a private Amazon RDS MySQL database.
- Connected application servers to the RDS database.
- Verified application availability using load balancing.

---

# AWS Best Practices Applied

- Multi-AZ architecture
- Public and private subnet isolation
- Bastion Host for secure administration
- Private database deployment
- Least privilege access using Security Groups
- High availability through multiple application servers
- Outbound internet access using NAT Gateway
- Layered network architecture

---

# Challenges Faced

During the project, several challenges were encountered and resolved, including:

- Configuring secure SSH access to private EC2 instances using a Bastion Host.
- Installing and configuring Apache, PHP, and phpMyAdmin on private EC2 instances.
- Registering EC2 instances with the Target Group and verifying healthy status.
- Troubleshooting Application Load Balancer connectivity.
- Configuring Amazon RDS inside private subnets.
- Updating phpMyAdmin configuration to connect with the RDS endpoint.
- Validating end-to-end communication between the application and database layers.

---

# Key Takeaways

This project strengthened my understanding of:

- AWS networking fundamentals
- Cloud security principles
- High availability architecture
- Load balancing concepts
- Private networking
- Database connectivity
- Infrastructure design
- Production-style AWS deployments

---

# Future Improvements

The following enhancements can be implemented in future versions of this project:

- HTTPS using AWS Certificate Manager (ACM)
- Route 53 custom domain integration
- Auto Scaling Group (ASG)
- Amazon CloudWatch monitoring
- AWS WAF for web application protection
- AWS Backup for automated database backups
- Infrastructure as Code using Terraform or AWS CloudFormation
- CI/CD pipeline using GitHub Actions or Jenkins

---

# Conclusion

This project demonstrates the implementation of a production-style Three-Tier Web Application Architecture on AWS. It combines networking, compute, load balancing, and database services while following AWS best practices for security, scalability, and high availability.

Completing this project has significantly improved my practical knowledge of AWS Cloud infrastructure and strengthened my skills in designing and deploying secure cloud-based applications.