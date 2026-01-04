# Project 2 — VPC with Bastion Host and Private Subnets

## Overview

This project demonstrates how to design and implement a secure AWS network architecture using a custom VPC, public and private subnets, a bastion host, and strict security group controls.
The goal is to allow secure administrative access to private EC2 instances without exposing them to the internet.

---

## Architecture

Internet  
↓  
Internet Gateway  
↓  
Public Subnet (Bastion Host)  
↓  
Private Subnet (Private EC2 Instance)

- Public subnet contains only the Bastion host  
- Private subnet contains application EC2 instances  
- SSH access to private instances is only possible through the Bastion  

---

## Implementation Steps

### 1. Create VPC
![01 VPC Created](screenshots/01-VPC%20Created.png)

---

### 2. Enable DNS
![02 Enable DNS](screenshots/02%20Enable%20DNS.png)

---

### 3. Create Public Subnet
![03 Public Subinet Created](screenshots/03%20Public%20Subinet%20Created.png)

---

### 4. Enable Auto Assign Public IP
![04 Enable Auto Assign IP for Public Subriet](screenshots/04%20Enable%20Auto%20Assign%20IP%20for%20Public%20Subriet.png)

---

### 5. Create Private Subnet
![05 Private Subnet Created](screenshots/05%20Private%20Subnet%20Created.png)

---

### 6. Create and Attach Internet Gateway
![06 IGW Created and Attached to VPC](screenshots/06%20IGW%20Created%20and%20Attached%20to%20VPC.png)

---

### 7. Create Route Table
![07 Route Table](screenshots/07%20Route%20Table.png)

---

### 8. Attach Route Table to Public Subnet
![08 Attach RT tu Public Subnet](screenshots/08%20Attach%20RT%20tu%20Public%20Subnet.png)

---

### 9. Create Bastion Security Group
![09 Bastian SG Created](screenshots/09%20Bastian%20SG%20Created.png)

---

### 10. Create Private EC2 Security Group
![10 Private SG Created](screenshots/10%20Private%20SG%20Created.png)

---

### 11. Launch Instances
![11 Instances Created](screenshots/11%20Instances%20Created.png)

---

### 12. Successful Connection to Private EC2
![12 Successful connection](screenshots/12%20Successful%20connection.png)

---

## Security Design

- Private EC2 has no public IP  
- SSH access to Private EC2 only allowed from Bastion Security Group  
- Bastion only allows SSH from my specific IP  
- Network isolation enforced through subnet routing and SG rules  

---

## Learning Outcomes

- Designed secure VPC network architecture  
- Implemented bastion-based access pattern  
- Practiced subnet isolation and routing control  
- Understood Security Group chaining for restricted access  
- Gained hands-on experience with private EC2 management  

---

## Clean-up

All resources were created inside a sandbox environment and terminated after completion to avoid any cost.
