# Activity Runbook (Jira)

> Guidance on how to query for changes that occurred during the time window of the incident by searching Jira. Use this while understanding changes to the infrastructure and if Jira tools are enabled.

This runbook contains guidance on how to search Jira for issues that were resolved during the timeframe of an incident.

## Connection Details

- Jira URL: `https://company.atlassian.net`
- Project keys: `OPS`, `DEV`, `INFRA`

## Workflows

### Find Recently Deployed Changes

Search for issues that transitioned to "Done" or "Deployed" in the incident timeframe:
```jql
project IN (OPS, DEV, INFRA) AND status changed to "Done" DURING ("2024-01-15 10:00", "2024-01-15 14:00")
```

### Find Related Deployments

Search for deployment tickets in the timeframe:
```jql
project = OPS AND type = "Deployment" AND resolved >= -24h
```

### Find Changes to Specific Service

Search for changes related to a specific service:
```jql
project IN (OPS, DEV) AND (summary ~ "<service-name>" OR labels = "<service-name>") AND resolved >= -7d
```

### Find Infrastructure Changes

Search for infrastructure changes:
```jql
project = INFRA AND type IN ("Change Request", "Task") AND resolved >= -48h
```

## Key Fields to Review

| Field | Why It Matters |
|:------|:---------------|
| Summary | Quick understanding of the change |
| Resolved Date | When the change was completed |
| Assignee | Who to contact for details |
| Labels | Service/component affected |
| Linked Issues | Related changes or incidents |

## Correlation Tips

- Look for changes resolved 0-4 hours before the incident started
- Check for "hotfix" or "urgent" labels indicating rushed changes
- Review linked PRs in the issue for actual code changes
