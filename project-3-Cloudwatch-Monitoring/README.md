## Project 3 — AWS EC2 Monitoring & Alerting

## Overview
This project demonstrates monitoring an AWS EC2 instance using CloudWatch metrics and alarms, integrated with SNS notifications, and visualized through a CloudWatch dashboard. The goal is to implement a basic monitoring and alerting workflow similar to what is used in real production environments.

## Architecture

EC2 Instance
↓
CloudWatch Metrics
↓
CloudWatch Alarms
↓
SNS Topic (Email Notifications)
↓
CloudWatch Dashboard

CloudWatch collects metrics from EC2
Alarms are triggered based on thresholds
SNS sends alert emails
Dashboard visualizes metrics and alarm states

## Implementation Steps

## 1. Launch EC2 Instance
01 Instance Created

Launch an Amazon Linux 2023 EC2 instance (t2.micro)
Connect using Instance Connect
Ensure the instance is running and reachable

Screenshot: Screenshots/01 Instance Created.png

## 2. Create SNS Topic
02 SNS Topic Created

Create a standard SNS topic named monitoring-alerts
Add email subscription and confirm it

Screenshot: Screenshots/02 SNS Topic Created.png

## 3. Create CloudWatch Alarms
03 CloudWatch Alarms Created

Create CPU Utilization alarm:
Metric: CPUUtilization
Condition: Greater than 70
Period: 1 minute
Datapoints: 1
Action: Send notification to monitoring-alerts SNS topic
Name: high-cpu

Create Status Check alarm:
Metric: StatusCheckFailed_Instance
Condition: Greater than 0
Action: Send notification to monitoring-alerts SNS topic
Name: statuscheck-failed-monitoring-ec2

Screenshot: Screenshots/03 Alarms Created.png

## 4. Generate CPU Load
04 Increase CPU Utilization

Connect to the EC2 instance and run:

yes > /dev/null &

Wait until alarm triggers and email is received, then stop load:

killall yes

Screenshot: Screenshots/04 Increase CPU Utilization.png

## 5. Alarm Triggered
05 Alarm Received

Confirm that email notification is received when CPU crosses threshold

Screenshot: Screenshots/05 Alarm Received.png

## 6. Create CloudWatch Dashboard
06 CloudWatch Dashboard Created

Create dashboard named monitoring-dashboard
Add CPUUtilization graph widget
Add StatusCheckFailed number widget labeled Instance Health
Optionally add NetworkIn and NetworkOut

Screenshot: Screenshots/06 CloudWatch Dashboard Created.png

## Security Design

EC2 instance has no monitoring ports exposed
Monitoring is handled internally via CloudWatch
Alerts are delivered through SNS email notifications
No public access is required for monitoring visibility

## Learning Outcomes

Understood how CloudWatch collects and visualizes metrics
Learned how to configure alarms based on thresholds
Integrated SNS with CloudWatch for alerting
Simulated real load to test monitoring effectiveness
Built a basic observability setup for EC2

## Clean-up

Terminate EC2 instance
Delete CloudWatch alarms and dashboard
Delete SNS topic and subscriptions
