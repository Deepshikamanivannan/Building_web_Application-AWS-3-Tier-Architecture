# Task 02 - Web Tier Deployment

## Objective

Deploy the Presentation Layer of the application using Amazon EC2 and Nginx.

## Services Used

- Amazon EC2
- Nginx
- Security Groups
- Public Subnets

## Implementation Steps

### Step 1: Launch EC2 Instances

Two EC2 instances were launched:

- Web-Server-1 in Public-Subnet-A
- Web-Server-2 in Public-Subnet-B

### Step 2: Configure Security Group

Inbound Rules:

| Protocol | Port | Purpose |
|-----------|--------|---------|
| SSH | 22 | Remote access using MobaXterm |
| HTTP | 80 | Web access |
| HTTPS | 443 | Secure web access |

### Step 3: Install Nginx

Commands used:

```bash
sudo apt update
sudo apt install nginx -y
sudo systemctl enable nginx
sudo systemctl start nginx
```

### Step 4: Validate Nginx

Verified Nginx installation using:

```bash
sudo systemctl status nginx
```

Verified web page using:

```text
http://<Public-IP>
```

## Architecture

```text
Internet
    │
    ▼
Web-Server-1 (Nginx)

Internet
    │
    ▼
Web-Server-2 (Nginx)
```

## Outcome

Successfully deployed and configured the Web Tier using Nginx on two EC2 instances and verified that the web server is accessible from the internet.
