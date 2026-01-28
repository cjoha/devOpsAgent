# DevOps Agent Runbooks

This folder contains runbooks for the AWS DevOps Agent to use during incident investigation. These runbooks provide context and guidance for querying integrated third-party systems.

## Runbook Structure

| Runbook | Purpose | Integration |
|:--------|:--------|:------------|
| [topology.md](./topology.md) | Maps AWS resources to telemetry providers | All |
| [metrics-grafana-prometheus.md](./metrics-grafana-prometheus.md) | Query metrics from Prometheus | Grafana/Prometheus |
| [logs-grafana-loki.md](./logs-grafana-loki.md) | Query logs from Loki | Grafana/Loki |
| [activity-jira.md](./activity-jira.md) | Find changes via Jira | Jira |
| [activity-github.md](./activity-github.md) | Find code changes via GitHub | GitHub |
| [activity-confluence.md](./activity-confluence.md) | Find documentation | Confluence |
| [communication-slack.md](./communication-slack.md) | Incident communication | Slack |

## How to Use

1. **Customize the topology runbook first** - This is the foundation that maps your services to telemetry
2. **Update connection details** - Replace placeholder URLs and project names with your actual values
3. **Add service-specific queries** - Extend the metrics/logs runbooks with queries specific to your services
4. **Keep it concise** - Too much information fills context and confuses the LLM

## Best Practices

- Start minimal, add detail as you learn what the agent needs
- Use consistent naming (service names, labels) across all runbooks
- Include example queries that work in your environment
- Document the "happy path" queries first, edge cases later

## Per-Brand Customization

For UK and Ireland brands, consider:
- Creating brand-specific topology files if services differ
- Using environment labels to distinguish between brands
- Documenting any brand-specific alerting thresholds
