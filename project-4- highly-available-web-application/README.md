# Project 4 — Highly Available Web Application with Auto Scaling and Monitoring

## Overview
This project demonstrates how to design and deploy a highly available, fault-tolerant web application architecture on AWS using an Application Load Balancer (ALB), Auto Scaling Group (ASG), Launch Template, CloudWatch monitoring, and dynamic scaling policies. The system automatically replaces unhealthy instances and scales based on CPU load.

## Architecture

User
↓  
Application Load Balancer (ALB)  
↓  
Auto Scaling Group (Multi-AZ EC2 instances)  
↓  
Target Group  
↓  
(Optional) RDS / Backend  

## Implementation Steps

### 1. Create Launch Template
A launch template defines how EC2 instances should be created inside the Auto Scaling Group, including AMI, instance type, key pair, security groups, and user data.

![Launch Template Created](Screenshots/01%20Launch%20Template%20Created.png)

---

### 2. Create Target Group
The target group registers EC2 instances and performs health checks so that only healthy instances receive traffic.

![Target Group Created](Screenshots/02%20Target%20Group%20Created.png)

---

### 3. Create ALB Security Group
A security group is created for the ALB to allow inbound HTTP (port 80) from the internet and outbound access to EC2 instances.

![ALB Security Group Created](Screenshots/03%20ALB%20Security%20Group%20Created.png)

---

### 4. Create Application Load Balancer
The ALB is deployed in public subnets across multiple Availability Zones and forwards traffic to the target group.

![ALB Created](Screenshots/04%20ALB%20Created.png)

---

### 5. Create Auto Scaling Group
The ASG is created using the launch template and attached to the target group so instances are automatically registered and deregistered.

![Auto Scaling Group Created](Screenshots/05%20Auto%20Scaling%20Group%20Created.png)

---

### 6. Terminate One EC2 Instance (Failure Simulation)
One EC2 instance is manually terminated to simulate a failure scenario.

![Terminating Instance](Screenshots/06%20Terminating%20One%20Instance.png)

---

### 7. Auto Scaling Group Launches Replacement Instance
The ASG automatically detects the missing instance and launches a new one to maintain desired capacity.

![New Instance Created](Screenshots/07%20New%20Instance%20Created%20by%20ASG.png)

---

### 8. Verify ALB DNS Endpoint
The ALB DNS name is used to access the web application and confirm traffic routing.

![ALB DNS Output](Screenshots/08%20DB%20ALB%20DNS%20Output.png)

---

### 9. Create Dynamic Scaling Policy
A target tracking scaling policy is created to increase or decrease capacity based on CPU utilization.

![Dynamic Scaling Created](Screenshots/09%20Dynamic%20Scaling%20Created.png)

---

### 10. Generate Load to Increase CPU Utilization
CPU load is generated on instances using a stress command to trigger scaling.

Example command used:
sudo yum install stress -y
stress --cpu 2 --timeout 300

![Increasing CPU](Screenshots/10%20Increasing%20CPU%20Utilization.png)

---

### 11. CloudWatch Alarm Triggered
CloudWatch detects high CPU usage and triggers the scaling policy.

![Alarm Triggered](Screenshots/11%20Alarm%20Triggered.png)

---

### 12. ASG Launches Additional Instance
The Auto Scaling Group launches a new instance in response to the alarm.

![Instance Launched](Screenshots/12%20instance%20Launch%20by%20ASG.png)

---

### 13. Instance Passes Health Checks
The new instance passes ALB health checks and starts serving traffic.

![Instance Successful](Screenshots/12%20Instance%20Successful.png)

---

### 14. Alarm Returns to OK State
Once CPU utilization drops, the CloudWatch alarm returns to the OK state.

![Alarm OK](Screenshots/13%20Alarm%20State%20OK.png)

---

## Learning Outcomes
- Designed a highly available web architecture using AWS managed services
- Implemented self-healing infrastructure with Auto Scaling
- Configured load balancing and health checks
- Practiced monitoring and alerting using CloudWatch
- Tested fault tolerance and dynamic scaling behavior

## Clean-up
All resources were created inside a sandbox environment and were terminated after completion to avoid unnecessary costs.
