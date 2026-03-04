---
inclusion: always
---

# AWS Best Practices

When working with AWS infrastructure and services, follow these guidelines:

## Security
- Always use IAM roles instead of hardcoded credentials
- Enable MFA for all IAM users with console access
- Follow the principle of least privilege for IAM policies
- Use AWS Secrets Manager or Parameter Store for sensitive data
- Enable CloudTrail logging in all regions
- Use VPC endpoints for AWS service access when possible

## Infrastructure as Code
- Prefer Terraform or CloudFormation for infrastructure provisioning
- Store state files in S3 with versioning and encryption enabled
- Use remote state locking with DynamoDB for Terraform
- Tag all resources with: Environment, Project, Owner, CostCenter
- Use consistent naming conventions: `{project}-{environment}-{resource}-{identifier}`

## Serverless
- Use Lambda layers for shared dependencies
- Set appropriate memory and timeout configurations
- Enable X-Ray tracing for debugging
- Use environment variables for configuration
- Implement proper error handling and retries

## Networking
- Use private subnets for application and database tiers
- Place NAT Gateways in public subnets for outbound traffic
- Implement security groups with minimal required access
- Use Network ACLs as an additional security layer
- Enable VPC Flow Logs for network monitoring

## Cost Optimization
- Use appropriate instance types and sizes
- Implement auto-scaling where applicable
- Use Reserved Instances or Savings Plans for predictable workloads
- Enable S3 lifecycle policies for data archival
- Set up billing alerts and budgets
