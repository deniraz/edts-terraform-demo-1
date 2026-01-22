# Terraform Demo 1 — EC2 + VPC (Init, Validate, Plan Only)

## Goal
Show Terraform workflow:
- `terraform init`
- `terraform validate`
- `terraform plan`

> No `terraform apply` in this demo.

## What this config describes
- VPC
- Public subnet
- Internet Gateway + route table
- Security Group (SSH)
- EC2 instance (Amazon Linux 2023) via AMI data source

## Run
```bash
terraform init
terraform validate

# If you don't have AWS credentials, try (may still need provider auth depending on setup):
terraform plan -refresh=false

# With AWS credentials:
terraform plan
