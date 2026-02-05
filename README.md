# DevOps Agent Runbooks

This repository contains runbooks for the AWS DevOps Agent to use during incident investigation. These runbooks provide context and guidance for querying integrated third-party systems.

## Runbook Examples

| Folder | Telemetry Stack | Description |
|:-------|:----------------|:------------|
| [runbooks-opensource](./runbooks-opensource/) | Grafana, Prometheus, Loki | Open source observability stack |
| [runbooks-commercial](./runbooks-commercial/) | Splunk | Commercial telemetry platform |

## How to Use

1. **Choose your telemetry stack** - Use the folder matching your monitoring tools
2. **Customize the topology runbook first** - This is the foundation that maps your services to telemetry
3. **Add your MCP Connections to DevOps Agent** - Always make sure these runbook files reference that MCP Connection name. So the agent understands the file context
4. **Add service-specific queries** - Extend the metrics/logs runbooks with queries specific to your services
5. **Keep it concise** - Too much information fills context and confuses the LLM

## Best Practices

- Start minimal, add detail as you learn what the agent needs
- Use consistent naming (service names, labels) across all runbooks
- Include example queries that work in your environment
- Document the "happy path" queries first, edge cases later

## Runbook Types

| Runbook | Purpose |
|:--------|:--------|
| `topology.md` | Maps AWS resources to telemetry providers |
| `metrics-*.md` | Query metrics from your telemetry platform |
| `logs-*.md` | Query logs from your telemetry platform |
| `activity-jira.md` | Find changes via Jira |
| `activity-github.md` | Find code changes via GitHub |
| `activity-confluence.md` | Find documentation |
| `communication-slack.md` | Incident communication |
