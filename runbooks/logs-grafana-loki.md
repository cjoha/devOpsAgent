# Logs Runbook (Grafana Loki)

> Guidance on how to query logs present in Grafana Loki. Use this while retrieving logs for a resource and if Grafana/Loki is enabled.

This runbook contains guidance on how to query logs stored in Loki via Grafana.

## Connection Details

- Grafana URL: `https://grafana.example.com`
- Loki datasource name: `loki-prod`

## Per Resource Queries

### ECS Service Logs

To find logs for an ECS service:
```logql
{app="<service-name>", environment="prod"}
```

To filter for errors:
```logql
{app="<service-name>"} |= "ERROR"
```

To parse JSON logs and filter:
```logql
{app="<service-name>"} | json | level="error"
```

### Lambda Function Logs

To find logs for a Lambda function:
```logql
{function_name="<function-name>"}
```

To find cold starts:
```logql
{function_name="<function-name>"} |= "INIT_START"
```

## Common Labels

| Label | Description | Example |
|:------|:------------|:--------|
| app | Application/service name | `example-api` |
| environment | Deployment environment | `prod`, `staging` |
| function_name | Lambda function name | `example-worker` |
| container_name | ECS container name | `app`, `sidecar` |

## Log Patterns to Search

| Pattern | Meaning |
|:--------|:--------|
| `ERROR` | Application errors |
| `WARN` | Warnings that may indicate issues |
| `timeout` | Timeout-related issues |
| `connection refused` | Network/connectivity issues |
| `OOM` | Out of memory errors |

## Time Range Guidance

- Start with 15 minutes before the incident alert time
- Expand to 1 hour if root cause not found
- Use line limit of 1000 initially to avoid overwhelming context
