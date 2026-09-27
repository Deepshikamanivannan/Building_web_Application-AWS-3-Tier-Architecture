# Task 08 - Configure Nginx Reverse Proxy

## Objective

Configure Nginx on the Web Tier servers to forward API requests to the Internal Application Load Balancer hosting the Flask application.

---

## Why Reverse Proxy?

Before:

```text
User
  │
  ▼
Web Server
```

The web server only serves static pages.

After:

```text
User
  │
  ▼
Nginx
  │
  ├── Static Content
  │
  └── API Requests
          │
          ▼
   Internal ALB
          │
          ▼
      Flask Servers
```

Benefits:

- Hides backend server details
- Improves security
- Simplifies routing
- Creates a clean application architecture

---

## Services Used

- Nginx
- Internal Application Load Balancer
- Flask
- Amazon EC2

---

## Implementation Steps

### Step 1

Access Nginx configuration file.

```bash
sudo nano /etc/nginx/nginx.conf
```

### Step 2

Configure reverse proxy settings.

Example:

```nginx
location /api/ {
    proxy_pass http://internal-app-alb-dns-name;
}
```

### Step 3

Verify Nginx configuration.

```bash
sudo nginx -t
```

### Step 4

Restart Nginx.

```bash
sudo systemctl restart nginx
```

### Step 5

Validate API communication through Nginx.

---

## Architecture

```text
Internet
    │
    ▼
 Public ALB
    │
    ▼
 Nginx Web Tier
    │
    ▼
 Internal ALB
    │
    ▼
 Flask App Tier
```

---

## Outcome

Successfully configured Nginx as a reverse proxy and enabled communication between the Web Tier and Application Tier through the Internal Load Balancer.
