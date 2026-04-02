# Project 5 — EC2 Backup and Disaster Recovery using AMI

## Overview

This project demonstrates how to implement a Backup and Disaster Recovery (DR) strategy for an Amazon EC2 instance using Amazon Machine Images (AMI). The objective is to simulate a real-world failure scenario by backing up an EC2 instance, terminating it, and restoring it from the backup while ensuring that the application data remains intact.

This approach follows a Backup & Restore DR model, which is commonly used for workloads where cost efficiency is more important than zero downtime.

## Architecture

EC2 Instance → Root EBS Volume → AMI (EBS Snapshot Backup) → Instance Termination (Disaster Simulation) → New EC2 Instance from AMI → Restored Root Volume → Data Validation

## Implementation Steps
## 1. EC2 Instance Created

An Amazon Linux EC2 instance is launched to act as the source system for the backup and disaster recovery process. This instance represents a production-like workload whose data needs to be protected.

![EC2 Instance Created](Screenshots/01%20EC2%20Instance%20Created.png)


## 2. Pre-Backup Data Validation

Before creating a backup, data is written to the root volume and verified. This step ensures that there is identifiable data present on the instance which can later be used to confirm successful recovery.

This validation is important to prove data integrity after restoration.

![Pre-Backup Data Validation](Screenshots/02%20Pre-Backup%20Data%20Validation.png)

## 3. AMI Created

An Amazon Machine Image (AMI) is created from the running EC2 instance. During this process, AWS automatically creates snapshots of the attached root EBS volume and registers them as an AMI.

The AMI serves as a point-in-time backup of the EC2 instance.

![AMI Created](Screenshots/03%20AMI%20Created.png)

## 4. Instance Terminated

The original EC2 instance is manually terminated to simulate a disaster scenario such as accidental deletion, system failure, or infrastructure issues.

At this stage, the AMI becomes the only recovery source.

![Instance Terminated](Screenshots/04%20Instance%20Terminated.png)

## 5. New Instance from AMI

A new EC2 instance is launched using the previously created AMI. AWS restores the root volume from the snapshot and recreates the instance with the same operating system and data state.

This step represents the actual disaster recovery process.

![New Instance from AMI](Screenshots/05%20New%20Instance%20from%20AMI.png)

## 6. DR Complete

After connecting to the restored EC2 instance, the previously created test data is verified. The presence of the data confirms that the backup and restore process was successful and no data was lost.

![Post Recovery Data Validation](Screenshots/06%20Post%20Recovery%20Data%20Validation.png)

## 7. AMI and Snapshot Validation

After the AMI is created, its availability and associated snapshots are verified to ensure the backup is complete and usable before relying on it for recovery.

This validation confirms:
AMI state is Available
Root volume snapshot is successfully created
Snapshot status is Completed
This step ensures that the backup is valid and reliable before proceeding with disaster recovery actions

![AMI & Snapshot Validation](Screenshots/07%20AMI%20&%20Snapshot%20Validation.png)

## Key Learnings

AMI provides a simple and effective way to back up EC2 instances
AMIs internally rely on EBS snapshots for data storage
Backup & Restore DR is cost-effective but involves downtime
Pre- and post-backup validation is essential to confirm data integrity
This approach is suitable for non–mission-critical workloads

## Conclusion

In this project, an EC2-based disaster recovery workflow was successfully implemented using Amazon Machine Images. By simulating a real failure scenario and restoring the instance from an AMI, the project demonstrates a practical and reliable Backup & Restore DR strategy. This method is widely used in real-world environments where recovery time is acceptable and infrastructure costs need to be minimized.
