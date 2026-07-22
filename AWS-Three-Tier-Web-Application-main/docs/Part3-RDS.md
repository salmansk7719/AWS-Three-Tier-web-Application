# Part 3 – Amazon RDS Integration

## Objective

The objective of this phase was to deploy a secure Amazon RDS MySQL database inside private database subnets and integrate it with the application servers using phpMyAdmin. The database was configured to remain inaccessible from the public internet while allowing secure access only from the application layer.

---

# Architecture

```
                 Application Load Balancer
                          │
            ┌─────────────┴─────────────┐
            │                           │
      App Server 1                App Server 2
      (Private Subnet)           (Private Subnet)
            │                           │
            └─────────────┬─────────────┘
                          │
                 Amazon RDS MySQL
               (Private DB Subnets)
```

---

# DB Subnet Group

| Property | Value |
|----------|-------|
| Name | db-subnetgroup |
| VPC | awsProject-vpc |

Associated Subnets

- db-pvt-sub1
- db-pvt-sub2

Purpose

- Allows Amazon RDS to be deployed inside private database subnets across multiple Availability Zones.

---

# Amazon RDS Configuration

| Property | Value |
|----------|-------|
| Database Engine | MySQL |
| Deployment | Free Tier |
| DB Identifier | mydb-project |
| Instance Class | db.t3.micro |
| Public Access | No |
| Credentials | Self Managed |
| VPC | awsProject-vpc |
| DB Subnet Group | db-subnetgroup |

---

# Database Security Group

Security Group Name

```
db-sg
```

Inbound Rule

| Port | Protocol | Source |
|------|----------|--------|
| 3306 | MySQL | app-sg |

Purpose

- Allows MySQL connections only from the application servers.
- Blocks direct database access from the internet.

---

# phpMyAdmin Configuration

The phpMyAdmin configuration file was updated to connect with the Amazon RDS database.

Configuration File

```
/var/www/html/phpMyAdmin/config.inc.php
```

The database host was changed from:

```
localhost
```

to the Amazon RDS Endpoint.

This allows phpMyAdmin to communicate directly with the private MySQL database hosted on Amazon RDS.

---

# Target Group Stickiness

The Application Load Balancer Target Group was configured with Stickiness enabled.

Configuration

| Property | Value |
|----------|-------|
| Stickiness | Enabled |
| Type | Load Balancer Generated Cookie |

Purpose

- Ensures users continue interacting with the same application server during an active session.
- Improves user experience for session-based applications.

---

# Validation Performed

The following validations were completed successfully:

- DB Subnet Group created successfully.
- Amazon RDS instance reached the Available state.
- Public access remained disabled.
- Database Security Group allowed traffic only from the application servers.
- phpMyAdmin successfully connected to the Amazon RDS database.
- Database login completed successfully.
- Application Load Balancer Stickiness enabled successfully.

---

# Security Best Practices

The following AWS security best practices were implemented:

- Database deployed inside private subnets.
- Public access disabled for Amazon RDS.
- Database accessible only through application servers.
- Security Groups used to restrict database access.
- Application servers communicate securely with the database.

---

# Outcome

A secure Amazon RDS MySQL database was successfully deployed in private database subnets and integrated with the application servers using phpMyAdmin. The database remained protected from direct internet access while allowing secure communication from the application layer, completing the implementation of a production-style three-tier web application architecture on AWS.