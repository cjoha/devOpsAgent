# Activity Runbook (Confluence)

> Guidance on how to find relevant documentation and runbooks in Confluence. Use this while understanding service architecture and operational procedures.

This runbook contains guidance on how to search Confluence for relevant documentation during incident investigation.

## Connection Details

- Confluence URL: `https://company.atlassian.net/wiki`
- Key Spaces: `OPS` (Operations), `ENG` (Engineering), `ARCH` (Architecture)

## Workflows

### Find Service Documentation

Search for service-specific documentation:
```
space:ENG AND title ~ "<service-name>"
```

### Find Runbooks for Service

Search for operational runbooks:
```
space:OPS AND (title ~ "runbook" OR label = "runbook") AND text ~ "<service-name>"
```

### Find Architecture Diagrams

Search for architecture documentation:
```
space:ARCH AND (title ~ "architecture" OR label = "architecture") AND text ~ "<service-name>"
```

### Find Recent Changes to Documentation

Check for recently updated pages that might indicate planned changes:
```
space:OPS AND lastmodified >= now("-7d")
```

## Key Documentation to Locate

| Document Type | Why It Matters |
|:--------------|:---------------|
| Service Runbook | Known issues and remediation steps |
| Architecture Diagram | Understanding dependencies |
| On-call Guide | Escalation paths and contacts |
| Deployment Guide | How the service is deployed |
| Incident History | Past incidents and resolutions |

## Useful Labels

| Label | Content Type |
|:------|:-------------|
| `runbook` | Operational runbooks |
| `architecture` | Architecture documentation |
| `oncall` | On-call procedures |
| `postmortem` | Past incident reviews |
| `<service-name>` | Service-specific docs |

## Correlation Tips

- Check if there's a known issue documented for the symptoms
- Review past postmortems for similar incidents
- Look for recent documentation updates indicating planned changes
