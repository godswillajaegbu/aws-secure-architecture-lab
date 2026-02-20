# aws-secure-architecture-lab
Secure AWS VPC architecture with IAM roles, EC2 deployment, and cloud security best practices.



## Overview
This lab demonstrates how to design and deploy a secure AWS cloud environment using VPC, public and private subnets, EC2 instances, IAM roles, and security groups.

## Objectives
- Create a custom VPC
- Configure public & private subnets
- Launch EC2 securely
- Apply IAM least privilege
- Configure Security Groups
- Implement S3 secure access

## Architecture Design
(Insert architecture diagram image here)

## Step-by-Step Implementation

### 1. Create VPC
- CIDR: 10.0.0.0/16

### 2. Create Subnets
- Public subnet: 10.0.1.0/24
- Private subnet: 10.0.2.0/24

### 3. Configure Internet Gateway
Attached to VPC

### 4. Launch EC2 Instance
- Amazon Linux 2
- IAM Role attached
- Security Group: Allow SSH from specific IP

### 5. Configure IAM Policy
Principle of Least Privilege applied

## Security Best Practices Applied
- IAM role instead of access keys
- Private subnet isolation
- Restricted security group rules
- Encrypted EBS volumes

## Lessons Learned
Cloud security must prioritize access control, network segmentation, and monitoring.




Components to include:

VPC (10.0.0.0/16) → Big rectangle

Public Subnet (10.0.1.0/24) → contains EC2 Instance + IGW

Private Subnet (10.0.2.0/24) → contains EC2 Instance + DB (optional)

Internet Gateway (IGW) → connected to Public Subnet

NAT Gateway → optional, for private subnet internet access

Security Groups / IAM → annotate on EC2

S3 Bucket → connected to VPC (optional)

Example Layout (ASCII-style for visualization):



                ┌───────────────────────── VPC 10.0.0.0/16 ─────────────────────────┐
                │                                                             │
  Public Subnet │ 10.0.1.0/24                  Private Subnet 10.0.2.0/24       │
 ┌─────────────┐│ ┌─────────────┐           ┌─────────────┐                     │
 │ EC2 Web     ││ │ Internet GW │           │ EC2 App     │                     │
 │ Server      ││ └─────────────┘           │ Server      │                     │
 │ SG: SSH     ││                           │ SG: App only│                     │
 └─────────────┘│                           └─────────────┘                     │
                │                             │                                  │
                │                             └─────> IAM Roles applied          │
                │                                                             │
                │                             S3 Bucket (secure access)        │
                └─────────────────────────────────────────────────────────────┘

