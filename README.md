# Terraform-Web-Automation

## Overview

Terraform-Web-Automation is a simple Terraform-based infrastructure automation project for web-hosted applications.
This repository includes Terraform configuration, state, and variable examples to provision cloud resources consistently.

## Repository Organization

- `first.tf` - main Terraform resource definitions
- `variables.tf` - variable declarations
- `output.tf` - outputs exposed after apply
- `var.tfvars` - sample variable values (local/testing)
- `terraform.tfstate`, `terraform.tfstate.backup` - Terraform state files (should be kept out of git in real projects)
- `index.html` - optional web content template
- `.gitignore` - ignores Terraform state, plan and editor files

## Prerequisites

1. Install Terraform v1.0+.
2. Configure cloud provider access (AWS CLI or your cloud provider of choice).
3. (Optional) Install Git and a code editor (VS Code, etc.).

## Setup

1. Open terminal in repository root: `c:\Users\delak\OneDrive\Desktop\Kanshu-Project`
2. Initialize Terraform:
   - `terraform init`
3. (Optional) Validate config:
   - `terraform validate`

## Variables and tfvars

- Define variables in `variables.tf`.
- Default values can exist there, but sensitive/provision-specific values should go in a `.tfvars` file.
- Example values file: `var.tfvars`.
- This project includes `var.tfvars` (not committed in production) to show variable use.

### Sample `var.tfvars`

```hcl
aws_region = "us-east-1"
instance_type = "t3.micro"
app_port = 8080
```

### Applying with tfvars

- `terraform plan -var-file="var.tfvars"
`
- `terraform apply -var-file="var.tfvars"
`

> Keep secrets out of VCS. Add `*.tfvars`, `*.tfvars.json`, and `terraform.tfstate*` to `.gitignore`.

## Usage

1. `terraform plan -var-file="var.tfvars"`
2. `terraform apply -var-file="var.tfvars"`
3. Inspect resources via cloud console or CLI.
4. Tear down with `terraform destroy -var-file="var.tfvars"`.

## Good practices

- Use environment-specific var files (e.g. `dev.tfvars`, `prod.tfvars`).
- Keep sensitive values in secrets manager or CI vault.
- Don’t commit state artifacts.

## Troubleshooting

- If apply fails, check output for missing provider credentials, invalid variable types, or existing resource conflicts.
- Run `terraform fmt` and `terraform validate` to catch syntax and type issues quickly.

## Notes

- This README is generated to match your local project layout and value usage (`usagetfvars`).
- Adjust provider setup in `first.tf` as needed for your provider and region.

