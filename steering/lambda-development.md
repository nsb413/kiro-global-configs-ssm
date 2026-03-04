---
inclusion: fileMatch
fileMatchPattern: '*lambda*.{py,js,ts,go}'
---

# AWS Lambda Development Guidelines

This guidance applies when working with Lambda function code.

## Function Structure
- Keep handler functions small and focused
- Separate business logic from handler code
- Initialize SDK clients outside the handler for connection reuse
- Use async/await patterns for Node.js functions

## Environment Variables
- Store configuration in environment variables
- Never hardcode secrets - use Secrets Manager
- Validate environment variables at startup

## Error Handling
```python
import json
import logging

logger = logging.getLogger()
logger.setLevel(logging.INFO)

def lambda_handler(event, context):
    try:
        # Your logic here
        return {
            'statusCode': 200,
            'body': json.dumps({'message': 'Success'})
        }
    except Exception as e:
        logger.error(f"Error: {str(e)}")
        return {
            'statusCode': 500,
            'body': json.dumps({'error': 'Internal server error'})
        }
```

## Performance
- Minimize cold start time by reducing package size
- Use Lambda layers for large dependencies
- Set memory appropriately (CPU scales with memory)
- Use provisioned concurrency for latency-sensitive functions

## Testing
- Write unit tests for business logic
- Use moto library for mocking AWS services in Python
- Test with sample events from the Lambda console
