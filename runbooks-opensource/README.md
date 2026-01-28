# Open Source Telemetry Runbooks

This folder contains runbooks for open source telemetry providers (Grafana, Prometheus, Loki).

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
