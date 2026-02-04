# Secure Multi-Tier Architecture on AWS

## Project Overview

This project demonstrates the implementation of a **Secure Multi-Tier Architecture on AWS**, designed to follow cloud security best practices, high availability, and network isolation principles. The solution separates the application into independent tiers hosted within a secure Virtual Private Cloud (VPC).

The live webpage for this project is hosted at:

🔗 **Application URL:** [Multi-Tier-App-423453926.eu-north-1.elb.amazonaws.com](https://personalshare91.wixsite.com/abdulsamadcloudsolut)

---

## Architecture Design

The architecture follows a **3-tier model**:

<img width="986" height="657" alt="image" src="https://github.com/user-attachments/assets/8251d32a-4513-464a-9707-ec24a352f053" />


### 1. Presentation Tier (Public Subnets)

* Accessible from the internet
* Uses an **Application Load Balancer (ALB)**
* Handles incoming HTTP/HTTPS requests

### 2. Application Tier (Private Subnets)

* Runs business logic
* Hosted on **EC2 instances or ECS services**
* Not directly accessible from the internet
* Receives traffic only from the ALB

### 3. Database Tier (Private Subnets)

* Uses **Amazon RDS (Multi-AZ)**
* Stores application data securely
* Accessible only from the application tier
* Public access disabled

---
## Architecture Diagram

![Secure Multi-Tier Architecture](architecture-diagram.png)

## Web Application Screenshot

![Live Webpage Screenshot](webpage-screenshot.png)


## AWS Services Used

* Amazon VPC
* Public and Private Subnets
* Application Load Balancer (ALB)
* Amazon EC2 / Amazon ECS
* Amazon RDS (Multi-AZ)
* Security Groups
* IAM Roles
* Amazon CloudWatch

---

## Network Architecture

* Custom VPC with CIDR block
* Multiple Availability Zones for high availability
* Public subnets host the ALB
* Private subnets host application and database layers
* Internet Gateway attached to public subnets

---

## Security Design

### Security Groups

| Source            | Destination       | Allowed Traffic    |
| ----------------- | ----------------- | ------------------ |
| Internet          | ALB               | HTTP / HTTPS       |
| ALB               | Application Layer | HTTP / HTTPS       |
| Application Layer | RDS               | Database Port Only |

* No direct internet access to EC2/ECS or RDS

### IAM Roles

* IAM roles attached to EC2/ECS
* No hardcoded credentials
* Least privilege access model

---

## Architecture Flow

1. Users access the application through the public URL
2. Traffic reaches the Application Load Balancer
3. ALB forwards requests to the application tier
4. Application processes requests securely
5. Database operations are performed through RDS
6. Response is returned to the user via ALB

---

## High Availability & Reliability

* Multi-AZ subnets
* Load-balanced application tier
* RDS Multi-AZ with automatic failover
* Fault isolation using subnet separation

---

## Monitoring & Logging

* Amazon CloudWatch for metrics and logs
* ALB health checks
* EC2/ECS and RDS monitoring

---

## Web Application Screenshot

Below is a screenshot of the deployed web application hosted at the provided URL:

**Webpage URL:** [https://personalshare91.wixsite.com/abdulsamadcloudsolut](https://personalshare91.wixsite.com/abdulsamadcloudsolut)

📸 *Screenshot of the application homepage should be captured and attached here for documentation or repository use.*

---

## Best Practices Followed

* Network isolation using private subnets
* Least privilege IAM access
* No direct database exposure
* Secure inbound and outbound traffic rules
* Use of managed AWS services

---

## Conclusion

This project showcases a secure, scalable, and highly available AWS multi-tier architecture suitable for production-grade web applications. By separating concerns across tiers and enforcing strong security controls, the architecture ensures reliability, security, and maintainability.

---

**End of README**
