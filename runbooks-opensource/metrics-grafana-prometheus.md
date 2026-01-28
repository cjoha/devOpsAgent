# Metrics Runbook (Grafana/Prometheus)

> Guidance on how to query metrics present in Prometheus via Grafana. Use this while retrieving metrics for a resource and if Grafana/Prometheus is enabled.

This runbook contains guidance on how to query metrics stored in Prometheus.

## Connection Details

- Prometheus datasource name: `prometheus-prod`

## Per Resource Queries

### ECS Service Metrics

To find CPU/Memory for an ECS service:
```promql
# CPU Usage
rate(container_cpu_usage_seconds_total{job="ecs-<service-name>"}{[5m]})

# Memory Usage
container_memory_usage_bytes{job="ecs-<service-name>"}
```

### Lambda Function Metrics

To find invocation metrics for a Lambda function:
```promql
# Invocation count
sum(rate(aws_lambda_invocations_total{function_name="<function-name>"}[5m]))

# Error rate
sum(rate(aws_lambda_errors_total{function_name="<function-name>"}[5m]))
```

### RDS Database Metrics

To find database performance metrics:
```promql
# Connection count
aws_rds_database_connections{dbinstance_identifier="<db-name>"}

# CPU utilization
aws_rds_cpuutilization{dbinstance_identifier="<db-name>"}
```

## Common Labels

| Label | Description | Example |
|:------|:------------|:--------|
| job | Prometheus scrape job name | `ecs-example-api` |
| environment | Deployment environment | `prod`, `staging` |
| region | AWS region | `eu-west-1` |

## Time Range Guidance

- For P1 incidents, start with last 1 hour, then expand to 24 hours if needed
- Use `[5m]` rate windows for smooth graphs, `[1m]` for granular analysis. Ask which the user prefers.
