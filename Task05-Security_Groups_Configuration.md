# Task 05 - Security Groups Configuration

## Objective

Implement security controls to restrict communication between the Web Tier, Application Tier, Database Tier, and Load Balancer.

---

## Services Used

- Amazon EC2 Security Groups
- Application Load Balancer
- Amazon RDS

---

## Security Architecture

```text
Internet
   │
   ▼
ALB-SG
   │
   ▼
Web-SG
   │
   ▼
App-SG
   │
   ▼
DB-SG
```

---

## Security Groups Created

### 1. Web-SG

Used by:

- Web-Server-1
- Web-Server-2

Inbound Rules:

| Type | Port | Source |
|--------|--------|--------|
| SSH | 22 | My IP |
| HTTP | 80 | 0.0.0.0/0 |
| HTTPS | 443 | 0.0.0.0/0 |

Purpose:

- Allow users to access the website.
- Allow administrators to manage the web servers.

---

### 2. App-SG

Used by:

- App-Server-1
- App-Server-2

Inbound Rules:

| Type | Port | Source |
|--------|--------|--------|
| SSH | 22 | Web-SG |
| Custom TCP | 5000 | Web-SG |

Purpose:

- Allow Web Tier instances to communicate with Flask applications.
- Prevent direct internet access to the application servers.

---

### 3. DB-SG

Used by:

- Amazon RDS MySQL

Inbound Rules:

| Type | Port | Source |
|--------|--------|--------|
| MySQL/Aurora | 3306 | App-SG |

Purpose:

- Allow database access only from the Application Tier.

---

### 4. ALB-SG

Used by:

- Internet-Facing Application Load Balancer

Inbound Rules:

| Type | Port | Source |
|--------|--------|--------|
| HTTP | 80 | 0.0.0.0/0 |
| HTTPS | 443 | 0.0.0.0/0 |

Purpose:

- Allow client traffic from the internet to reach the load balancer.

---

## Security Flow

```text
Internet
   │
   ▼
Application Load Balancer
   │
   ▼
Web Tier
   │
   ▼
Application Tier
   │
   ▼
Database Tier
```

Each tier communicates only with the tier directly above or below it.

---

## Outcome

Successfully implemented Security Groups to protect each layer of the three-tier architecture and enforce controlled communication between application components.

---

## Key Learnings

- Security Groups act as virtual firewalls.
- Security Group references provide secure communication between tiers.
- Application and Database servers should remain private.
- Least-privilege access improves security.
