# 3-Tier Web Application on AWS (Terraform)

## Overview
A production-grade 3-tier web application deployed on AWS using Terraform.
Includes VPC, EC2 Auto Scaling Group, Application Load Balancer, RDS PostgreSQL
database in private subnets, S3 storage, IAM roles, and CloudWatch monitoring.

## Architecture
Internet → ALB → Auto Scaling Group (EC2) → RDS (PostgreSQL)
                                              ↓
                                         S3 Bucket

## Services Used
- VPC (public + private subnets across 2 AZs)
- Internet Gateway + Route Tables
- Security Groups (ALB, EC2, RDS)
- EC2 Auto Scaling Group (t3.micro)
- Application Load Balancer
- RDS PostgreSQL (private subnets)
- S3 (static storage, public access blocked)
- IAM Role + Policy (least privilege)
- CloudWatch Alarms (CPU monitoring)
- Terraform (Infrastructure as Code)

## Prerequisites
- AWS account
- Terraform installed
- AWS CLI configured

## How to Deploy
1. Clone this repo
2. Run `terraform init`
3. Run `terraform plan`
4. Run `terraform apply`
5. Copy the `alb_dns_name` from outputs and open it in your browser

## Deployment Output
Apply complete! Resources: 25 added, 0 changed, 0 destroyed.

Outputs:

alb_dns_name = "my-alb-1234567890.us-east-1.elb.amazonaws.com"
db_endpoint = "my-database.xxxxx.us-east-1.rds.amazonaws.com:5432"
s3_bucket = "my-project-static-20260911"

## How to Destroy
Run `terraform destroy`

## Screenshots


## Challenges Faced
- Security Group misconfiguration locked me out of SSH
- RDS username "admin" is reserved — changed to "dbadmin"
- Amazon Linux 2 uses `yum` not `dnf`

## Author
Treasure.
