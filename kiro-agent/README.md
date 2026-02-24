# DevOps Agent Runbook Builder — Kiro Custom Agent

A Kiro CLI custom agent that guides you through building [AWS DevOps Agent](https://docs.aws.amazon.com/devopsagent/latest/userguide/about-aws-devops-agent.html) runbooks for your environment.

The agent asks a few quick questions about your telemetry stack and tooling, then generates customized runbook files ready to add to your DevOps Agent Space.

## What It Does

1. Asks which telemetry stack you use (Open Source or Commercial)
2. Gathers key identifiers (datasource names, labels, project keys)
3. Generates runbook files tailored to your environment using the templates in this repository

Total time: ~5-10 minutes.

## Installation

Copy the `devops-runbook-builder` folder into your Kiro agents directory (`~/.kiro/agents/`).

### macOS / Linux

```bash
# From the root of this repository
cp -r kiro-agent/devops-runbook-builder ~/.kiro/agents/
```

### Windows (PowerShell)

```powershell
# From the root of this repository
Copy-Item -Recurse -Path "kiro-agent\devops-runbook-builder" -Destination "$env:USERPROFILE\.kiro\agents\devops-runbook-builder"
```

### Windows (Command Prompt)

```cmd
# From the root of this repository
xcopy /E /I "kiro-agent\devops-runbook-builder" "%USERPROFILE%\.kiro\agents\devops-runbook-builder"
```

> **Note:** Installing to `~/.kiro/agents/` makes the agent available globally across all your workspaces. If you prefer it scoped to a single workspace, copy it to `<your-workspace>/.kiro/agents/` instead.

## Usage

1. Open Kiro CLI at the root of this cloned repository
2. In chat, invoke the agent:
   ```
   @DevOps Agent Runbook Builder
   ```
3. Follow the prompts — pick your stack, provide a few details, and the agent generates your runbook files into a `runbooks/` directory

## What Gets Generated

Depending on your answers, the agent creates some or all of these files:

| File | Purpose |
|:-----|:--------|
| `runbooks/topology.md` | Maps AWS resources to telemetry providers |
| `runbooks/metrics-*.md` | How to query metrics from your telemetry platform |
| `runbooks/logs-*.md` | How to query logs from your telemetry platform |
| `runbooks/activity-jira.md` | Finding changes via Jira |
| `runbooks/activity-github.md` | Finding code changes via GitHub |
| `runbooks/activity-confluence.md` | Finding documentation via Confluence |
| `runbooks/communication-slack.md` | Incident communication via Slack |

## After Generation

1. Review the generated files and adjust any values
2. Add the runbooks to your DevOps Agent Space via **Settings → Runbooks** in the web app
3. Use clear titles and descriptions — the DevOps Agent uses these to decide which runbook to consult
4. Iterate based on what the agent does in investigations

## Requirements

- [Kiro CLI](https://kiro.dev) installed and configured
- This repository cloned locally (the agent reads the runbook templates from `runbooks-opensource/` and `runbooks-commercial/`)
