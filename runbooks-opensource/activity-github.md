# Activity Runbook (GitHub)

> Guidance on how to query for code changes and deployments that occurred during the time window of the incident by searching GitHub. Use this while understanding what changed and if GitHub tools are enabled.

This runbook contains guidance on how to search GitHub for changes during an incident timeframe.

## Connection Details

- Key Repositories: `example-api`, `example-worker`, `infrastructure`

## Workflows

### Find Recent Merges to Main

Look for PRs merged to main/master in the incident timeframe:
- Navigate to repository → Pull Requests → Closed
- Filter by merge date

### Find Commits in Timeframe

Search for commits in a specific date range:
```
repo:company-org/<repo-name> merged:2024-01-15..2024-01-16
```

### Find Deployments

Check GitHub Actions workflow runs:
- Navigate to repository → Actions
- Filter by workflow (e.g., "Deploy to Production")
- Look for runs in the incident timeframe

### Find Changes to Specific Files

Search for changes to configuration or critical files:
```
repo:company-org/<repo-name> path:config/ 
repo:company-org/<repo-name> path:*.tf
```

## Key Areas to Review

| Area | What to Look For |
|:-----|:-----------------|
| Recent PRs | Code changes merged before incident |
| Actions/Workflows | Deployment runs and their status |
| Releases | New versions deployed |
| Config changes | Environment variables, feature flags |
| Infrastructure | Terraform/CDK changes |

## Correlation Tips

- Check for failed deployments that were retried
- Look for PRs with "hotfix" or "urgent" in the title
- Review any reverted commits
- Check if feature flags were toggled
