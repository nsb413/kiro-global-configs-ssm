# Global Demo - AWS Development Configuration

Global Kiro configurations for AWS development, steering guidance and MCP servers that apply across all your workspaces.

## Structure

```
global-demo/
├── steering/          # Always-included and conditional guidance
│   ├── aws-best-practices.md
│   ├── lambda-development.md
│   └── terraform-standards.md
└── settings/          # MCP server configurations
    └── mcp.json
```

## Steering Files

Steering files provide context and guidelines to Kiro:

- **aws-best-practices.md** - Always included, covers security, IaC, serverless, networking, and cost optimization
- **lambda-development.md** - Auto-included when working with Lambda function files
- **terraform-standards.md** - Auto-included when editing .tf files

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

## Usage

To use this configuration globally:

1. Copy or symlink this directory structure to `~/.kiro/`
2. MCP servers will be available across all workspaces
3. Steering files will provide context automatically

## Requirements

- AWS CLI configured with credentials
- uv/uvx (for MCP servers): `brew install uv` or `pip install uv`
