# Part 2 – EC2, Bastion Host, and Application Load Balancer

## Objective

The objective of this phase was to deploy the application layer of the three-tier architecture. This included launching EC2 instances, configuring secure SSH access through a Bastion Host, installing Apache and PHP, deploying phpMyAdmin, and configuring an Application Load Balancer (ALB) for high availability.

---

# Architecture

```
                    Internet
                        │
                Application Load Balancer
                        │
        ┌───────────────┴───────────────┐
        │                               │
   App Server 1                   App Server 2
 (Private Subnet)               (Private Subnet)
        │                               │
        └───────────────┬───────────────┘
                        │
                 Bastion Host
                 (Public Subnet)
```

---

# EC2 Instances

| Instance Name | Purpose | Subnet | Public IP |
|--------------|---------|--------|-----------|
| jump-server | Bastion Host | web-pub-sub1 | Yes |
| app-server1 | Application Server | app-pvt-sub1 | No |
| app-server2 | Application Server | app-pvt-sub2 | No |

---

# Security Groups

## jump-sg

### Inbound Rules

| Port | Protocol | Source |
|------|----------|--------|
| 22 | SSH | Your Public IP |
| 80 | HTTP | Anywhere |

Purpose

- Secure SSH access to the Bastion Host.
- Optional HTTP access for testing.

---

## alb-sg

### Inbound Rules

| Port | Protocol | Source |
|------|----------|--------|
| 80 | HTTP | Anywhere |

Purpose

- Allow incoming HTTP traffic to the Application Load Balancer.

---

## app-sg

### Inbound Rules

| Port | Protocol | Source |
|------|----------|--------|
| 22 | SSH | jump-server |
| All Traffic | All | alb-sg |

Purpose

- Allow SSH access only through the Bastion Host.
- Allow application traffic from the Application Load Balancer.

---

# Bastion Host Configuration

The Bastion Host (Jump Server) was deployed in the public subnet to securely access EC2 instances located in private subnets.

The private key was copied to the Bastion Host and used to establish SSH connections with the private application servers.

---

# Application Server Configuration

The following software was installed on both application servers:

- Apache HTTP Server
- PHP 8.2
- PHP-FPM
- phpMyAdmin
- PHP Extensions

Apache service was enabled to start automatically after reboot.

---

# Application Deployment

Two different test pages were created.

## app-server1

```
PHP Server 1
```

## app-server2

```
PHP Server 2
```

These pages were used to verify Application Load Balancer traffic distribution.

---

# Target Group

| Property | Value |
|----------|-------|
| Name | app-tg |
| Target Type | Instance |
| Protocol | HTTP |
| Port | 80 |
| Health Check | / |

Registered Targets

- app-server1
- app-server2

Health Status

- Healthy

---

# Application Load Balancer

| Property | Value |
|----------|-------|
| Name | project-alb |
| Type | Internet Facing |
| Listener | HTTP :80 |
| Target Group | app-tg |

Purpose

- Distribute incoming HTTP requests across multiple application servers.
- Improve application availability and reliability.

---

# Validation Performed

The following validations were completed:

- Successfully connected to the Bastion Host using SSH.
- Successfully accessed private EC2 instances through the Bastion Host.
- Apache service started successfully.
- PHP installed successfully.
- phpMyAdmin deployed successfully.
- Target Group health checks passed.
- Application Load Balancer became Active.
- Requests were distributed between both EC2 instances.
- Browser displayed "PHP Server 1" and "PHP Server 2" on refresh.

---

# High Availability

The application layer was deployed across two Availability Zones.

Benefits:

- Improved fault tolerance
- Automatic traffic distribution
- Reduced downtime
- Better scalability

---

# Outcome

A highly available application layer was successfully deployed using Amazon EC2 and an Application Load Balancer. Secure administrative access was provided through a Bastion Host, while application traffic was distributed across two private EC2 instances using the Application Load Balancer.