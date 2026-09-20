# Task 01 - Design and Configure AWS Networking Infrastructure

## Objective

The objective of this task is to design and configure a secure networking infrastructure for a three-tier application architecture on AWS.

## AWS Services Used

### Amazon VPC
Amazon Virtual Private Cloud (VPC) is used to create an isolated network environment in AWS.

### Internet Gateway (IGW)
An Internet Gateway enables communication between the VPC and the Internet.

### NAT Gateway
A NAT Gateway allows resources in private subnets to access the Internet while preventing inbound connections from the Internet.

### Elastic IP
A static public IPv4 address attached to the NAT Gateway.

### Route Tables
Route tables define how network traffic is directed within the VPC.

### Subnets
Subnets divide the VPC into smaller network segments.

---

## Network Design

### VPC

| Resource | CIDR Block |
|-----------|------------|
| VPC | 10.0.0.0/16 |

### Public Subnets

| Subnet | CIDR |
|---------|---------|
| Public-A | 10.0.1.0/24 |
| Public-B | 10.0.2.0/24 |

### Private Application Subnets

| Subnet | CIDR |
|---------|---------|
| App-A | 10.0.11.0/24 |
| App-B | 10.0.12.0/24 |

### Private Database Subnets

| Subnet | CIDR |
|---------|---------|
| DB-A | 10.0.21.0/24 |
| DB-B | 10.0.22.0/24 |

---

## Route Table Associations

### Public Route Table

Associated Subnets:
- Public-A
- Public-B

Route:
- 0.0.0.0/0 → Internet Gateway

### Application Route Table

Associated Subnets:
- App-A
- App-B

Route:
- 0.0.0.0/0 → NAT Gateway

### Database Route Table

Associated Subnets:
- DB-A
- DB-B

Route:
- Local VPC Route

---

## Architecture

```text
                Internet
                    │
                    ▼
          Internet Gateway
                    │
            ┌───────┴───────┐
            │     VPC       │
            │ 10.0.0.0/16   │
            └───────┬───────┘
                    │
     ┌──────────────┼──────────────┐
     │                              │
 Public Subnets                Public Subnets
10.0.1.0/24                    10.0.2.0/24
     │                              │
     └──────────────┬──────────────┘
                    │
              NAT Gateway
                    │
      ┌─────────────┼─────────────┐
      │                           │
 App-A Subnet               App-B Subnet
10.0.11.0/24               10.0.12.0/24
      │                           │
      └─────────────┬─────────────┘
                    │
      ┌─────────────┼─────────────┐
      │                           │
 DB-A Subnet                DB-B Subnet
10.0.21.0/24               10.0.22.0/24
```

---

## Outcome

Successfully created:

- Custom VPC
- 6 Subnets across 2 Availability Zones
- Internet Gateway
- NAT Gateway
- Elastic IP
- Route Tables
- Route Table Associations

This networking infrastructure provides the foundation for deploying the Web Tier, Application Tier, and Database Tier in a secure and scalable manner.
