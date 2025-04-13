# SYST35144 CloudFormation Lab

This repository contains three reusable and DRY AWS CloudFormation templates created for the SYST35144 course lab. The infrastructure is deployed entirely using CloudFormation without any manual steps, following the specified architecture.

## 📁 Files Overview

### 1. `create-vpc.yml`
- Creates a **VPC** with:
  - One **public subnet**
  - One **private subnet**
  - An **Internet Gateway**
  - A **NAT Gateway**
  - Route tables for both public and private traffic
- Outputs:
  - VPC ID
  - Public subnet ID
  - Private subnet ID

### 2. `create-sg.yml`
- Creates a **Security Group** that:
  - Allows **SSH (port 22)** from any IPv4 address
  - Allows **HTTP (port 80)** from any IPv4 address
- Outputs:
  - Security Group ID

### 3. `create-ec2.yml`
- Launches **EC2 instances** with parameters:
  - Deploys into either **public** or **private** subnet conditionally
  - Uses the **Security Group** created by `create-sg.yml`
  - Uses subnet and VPC IDs from the `create-vpc.yml` outputs

## ⚙️ Deployment Instructions

1. **Deploy VPC Template:**
   ```bash
   aws cloudformation deploy --template-file create-vpc.yml --stack-name my-vpc-stack --capabilities CAPABILITY_NAMED_IAM
