---
inclusion: fileMatch
fileMatchPattern: '*.tf'
---

# Terraform Standards

Follow these conventions when writing Terraform code.

## File Organization
- `main.tf` - Primary resource definitions
- `variables.tf` - Input variable declarations
- `outputs.tf` - Output value declarations
- `versions.tf` - Provider version constraints
- `terraform.tfvars` - Variable values (gitignored)

## Naming Conventions
- Use snake_case for resource names and variables
- Resource names should be descriptive: `aws_instance.web_server`
- Avoid redundant prefixes: Use `aws_s3_bucket.data` not `aws_s3_bucket.s3_data`

## Variables
```hcl
variable "environment" {
  description = "Environment name (dev, staging, prod)"
  type        = string
  validation {
    condition     = contains(["dev", "staging", "prod"], var.environment)
    error_message = "Environment must be dev, staging, or prod."
  }
}
```

## Required Tags
```hcl
locals {
  common_tags = {
    Environment = var.environment
    Project     = var.project_name
    ManagedBy   = "Terraform"
    Owner       = var.owner
  }
}
```

## State Management
- Always use remote state (S3 backend)
- Use workspaces for environment separation
- Never commit state files to version control

## Best Practices
- Use data sources to reference existing resources
- Implement lifecycle rules to prevent accidental deletion
- Use `terraform fmt` before committing
- Run `terraform validate` in CI/CD
- Use modules for reusable components
