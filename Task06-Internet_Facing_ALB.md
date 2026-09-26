# Task 06 - Configure the Internet-Facing Application Load Balancer

## Objective

Configure an Internet-Facing Application Load Balancer (ALB) to distribute incoming traffic across multiple web servers and provide high availability.

---

## Why We Use an ALB

Before ALB:

```text
User
  ↓
Web-Server-1 Public IP
```

Problem:
- Single point of failure
- Users must know EC2 IP
- No load balancing

After ALB:

```text
Internet
    │
    ▼
Public Application Load Balancer
    │
 ┌──┴──┐
 ▼     ▼
Web-1 Web-2
```

Benefits:
- High Availability
- Load Distribution
- Fault Tolerance
- Single DNS Endpoint

---

## Services Used

- Application Load Balancer
- Target Group
- Amazon EC2
- Security Groups

---

## Step 1: Create Target Group

Configuration:

- Target Type: Instance
- Protocol: HTTP
- Port: 80
- Name: web-tier-tg
- VPC: Three-Tier-VPC

---

## Step 2: Register Targets

Registered:

- Web-Server-1
- Web-Server-2

---

## Step 3: Configure Health Checks

Configuration:

- Protocol: HTTP
- Path: /

The ALB continuously checks the health of web servers.

---

## Step 4: Create Public ALB

Configuration:

- Internet-Facing
- IPv4
- Public-Subnet-A
- Public-Subnet-B
- ALB-SG

---

## Step 5: Configure Listener

Listener:

- HTTP : 80

Forward To:

- web-tier-tg

---

## Step 6: Verify Target Health

Verified:

- Web-Server-1 = Healthy
- Web-Server-2 = Healthy

---

## Step 7: Verify Application

Used:

http://ALB-DNS-NAME

Verified that the application loaded successfully through the ALB.

---

## Architecture

```text
                 Internet
                     │
                     ▼
            Public Application
             Load Balancer
                     │
           ┌─────────┴─────────┐
           │                   │
           ▼                   ▼
     Web-Server-1       Web-Server-2
         (Nginx)           (Nginx)
```

---

## Outcome

Successfully configured an Internet-Facing Application Load Balancer, registered web servers, configured health checks, and verified application access through the ALB DNS name.
``
