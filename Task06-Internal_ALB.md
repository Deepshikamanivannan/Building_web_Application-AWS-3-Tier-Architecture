# Task 07 - Internal Application Load Balancer

## Objective
Create an Internal Load Balancer to distribute requests across multiple Flask Application Servers.

## Why?

Without Internal ALB:
Web Tier → App-Server-1

Single point of failure.

With Internal ALB:
Web Tier → Internal ALB → App-Server-1/App-Server-2

Provides high availability and load balancing.

## Outcome
Successfully created an Internal ALB, registered Flask servers, configured health checks, and verified communication between the Web Tier and Application Tier.
