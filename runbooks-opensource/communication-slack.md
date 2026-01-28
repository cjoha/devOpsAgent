# Communication Runbook (Slack)

> Guidance on how to use Slack for incident communication and finding relevant context. Use this while coordinating incident response and if Slack tools are enabled.

This runbook contains guidance on how to search Slack for relevant context during incident investigation.


## Key Channels

| Channel | Purpose |
|:--------|:--------|
| `#incidents` | Active incident coordination |
| `#deployments` | Deployment announcements |
| `#alerts` | Automated alert notifications |
| `#ops-<service-name>` | Service-specific operations |

## Workflows

### Search for Related Alerts

Search in #alerts channel for related notifications:
```
in:#alerts <service-name>
in:#alerts <error-message>
```

### Search for Related Discussions

Search across channels for context:
```
<service-name> <error-keyword>
from:@oncall-bot
```

## Incident Communication Template

When posting incident updates:
```
🔴 *Incident Update*
*Status*: Investigating / Identified / Monitoring / Resolved
*Impact*: <description of user impact>
*Services*: <affected services>
*Current Actions*: <what's being done>
*Next Update*: <time>
```

## Correlation Tips

- Check #alerts for the first alert timestamp
- Look for deployment announcements before the incident
- Search for similar error messages in the past
- Check if anyone reported issues before alerts fired
