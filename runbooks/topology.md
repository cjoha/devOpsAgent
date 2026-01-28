# Topology Runbook

> Contains mappings of AWS resources to third-party telemetry providers. Use this runbook while forming an understanding of the application architecture and if a third-party telemetry provider is enabled.

This runbook contains relationships between AWS resources and telemetry providers outside of CloudWatch.

## 3P Resource Mapping

| Name | Type | 3P Telemetry |
|:-----|:-----|:-------------|
| example-api | AWS::ECS::Service | Metrics in Prometheus (job: `ecs-example-api`), Logs in Grafana Loki (app: `example-api`) |
| example-worker | AWS::Lambda::Function | Metrics in Prometheus (job: `lambda-example-worker`) |
| example-db | AWS::RDS::DBInstance | Metrics in Prometheus (job: `rds-example-db`) |

## Service Dependencies

```
[User] --> [example-api (ECS)] --> [example-db (RDS)]
                |
                v
         [example-worker (Lambda)]
```

## Notes

- Add rows for each service your team owns
- Include the exact job/label names used in Prometheus for quick correlation
- Document any custom exporters or sidecars deployed alongside services
