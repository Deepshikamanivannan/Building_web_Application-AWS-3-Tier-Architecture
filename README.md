# AWS 3-Tier Architecture

A hands-on AWS project implementing a secure and highly available **3-Tier Web Application Architecture** using AWS networking and compute services.

## Architecture

The solution is divided into three layers:

* **Web Tier** – Public subnets hosting the Application Load Balancer
* **Application Tier** – Private subnets hosting the application servers
* **Database Tier** – Private subnets hosting Amazon RDS MySQL

## AWS Services Used

* Amazon VPC
* Public and Private Subnets
* Internet Gateway
* NAT Gateway
* Application Load Balancer (ALB)
* EC2
* Amazon RDS MySQL
* Security Groups
* Route Tables
* AWS Systems Manager Session Manager

## Key Objectives

* Design a secure VPC network across multiple Availability Zones
* Implement public and private subnet architecture
* Configure secure communication between Web, Application, and Database tiers
* Deploy an application on EC2
* Configure ALB for application traffic distribution
* Connect the application tier securely to RDS
* Use NAT Gateway for controlled outbound internet access from private resources
* Troubleshoot and validate end-to-end application connectivity

## Project Outcome

Successfully implemented and tested a functional AWS 3-Tier Architecture with separation of concerns, private database access, controlled network traffic, and secure application connectivity.

