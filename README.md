# Global Demo - AWS Development Configuration

This directory contains global configuration files that work across all workspaces for AWS development.

## Structure

```
global-demo/
├── steering/          # Always-included and conditional guidance
│   ├── aws-best-practices.md
│   ├── lambda-development.md
│   └── terraform-standards.md
├── skills/            # Reusable implementation patterns
│   ├── cloudformation-serverless-api.md
│   ├── terraform-vpc-module.md
│   ├── s3-static-website.md
│   └── rds-postgres-setup.md
├── settings/          # MCP server configurations
│   └── mcp.json
└── hooks/             # Automated workflows
    ├── terraform-validate.kiro.hook
    └── cloudformation-lint.kiro.hook
```

## Steering Files

Steering files provide context and guidelines to Kiro:

- **aws-best-practices.md** - Always included, covers security, IaC, serverless, networking, and cost optimization
- **lambda-development.md** - Auto-included when working with Lambda function files
- **terraform-standards.md** - Auto-included when editing .tf files

## Skills

Skills are reusable implementation guides:

- **cloudformation-serverless-api.md** - API Gateway + Lambda REST API setup
- **terraform-vpc-module.md** - Production-ready VPC with public/private subnets
- **s3-static-website.md** - S3 + CloudFront static website hosting
- **rds-postgres-setup.md** - RDS PostgreSQL with security and backups

## MCP Servers

Configured AWS-related MCP servers from [awslabs/mcp](https://github.com/awslabs/mcp):

- **aws-docs** - Search and retrieve AWS documentation (Windows/Mac/Linux compatible)
- **aws-kb** - Query AWS Knowledge Base articles and best practices (Windows/Mac/Linux compatible)
- **aws-support** - Access AWS Support case management and Trusted Advisor (Windows/Mac/Linux compatible)

To use these servers, ensure you have `uv` and `uvx` installed:
```bash
# macOS with Homebrew
brew install uv

# Windows with pip
pip install uv

# Or with pip on any platform
pip install uv
```

These servers work cross-platform and are maintained by AWS Labs.

## Hooks

Automated workflows that trigger on file events:

- **terraform-validate.kiro.hook** - Formats and validates Terraform files on save
- **cloudformation-lint.kiro.hook** - Lints CloudFormation templates on save

## Usage

To use this configuration globally:

1. Copy or symlink this directory structure to `~/.kiro/`
2. MCP servers will be available across all workspaces
3. Steering files will provide context automatically
4. Skills can be referenced with `#` in chat
5. Hooks will trigger based on file events

## Requirements

- AWS CLI configured with credentials
- Terraform (for Terraform-related features)
- cfn-lint (for CloudFormation linting): `pip install cfn-lint`
- uv/uvx (for MCP servers): `brew install uv` or `pip install uv`
