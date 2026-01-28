# Logs Runbook (Grafana Loki)

> Guidance on how to query logs present in Grafana Loki. Use this while retrieving logs for a resource and if Grafana/Loki is enabled.

This runbook contains guidance on how to query logs stored in Loki via Grafana.

## Connection Details

- Loki datasource name: `loki-prod`

## Per Resource Queries

### EC2 Service Logs

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


## Common Labels

| Label | Description | Example |
|:------|:------------|:--------|
| app | Application/service name | `example-api` |
| environment | Deployment environment | `prod`, `staging` |
| function_name | Lambda function name | `example-worker` |
| ec2 | ec2 tag values for service-name | `app` |

## Log Patterns to Search

| Pattern | Meaning |
|:--------|:--------|
| `ERROR` | Application errors |
| `WARN` | Warnings that may indicate issues |
| `timeout` | Timeout-related issues |
| `connection refused` | Network/connectivity issues |
| `OOM` | Out of memory errors |
