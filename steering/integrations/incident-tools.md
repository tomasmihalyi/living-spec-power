---
inclusion: auto
triggers: ["PagerDuty", "OpsGenie", "incident", "on-call", "production issue", "outage"]
---

# Incident Tool Integration

## Supported Tools (via MCP)

| Tool | MCP Server | Status |
|------|------------|--------|
| PagerDuty | `@pagerduty/mcp-server` | Available |
| OpsGenie | `@atlassian/mcp-opsgenie` | Available |
| AWS CloudWatch | `@aws/mcp-cloudwatch` | Available |

## Incident → Spec Flow

When incident detected:
1. Query incident details via MCP
2. Check if §2 Requirements covers the failure scenario
3. If gap found:
   - Generate new requirement tagged `[PROD-DERIVED]`
   - Add to §7 Next Actions for review
4. Link incident ID to relevant requirement

## Setup

Add to project's `.kiro/mcp.json`:

```json
{
  "mcpServers": {
    "pagerduty": {
      "command": "npx",
      "args": ["-y", "@pagerduty/mcp-server"],
      "env": {
        "PD_API_KEY": "$PD_API_KEY"
      }
    }
  }
}
```

## Usage

After setup, ask:
- "Check recent incidents for spec gaps"
- "Link incident INC-123 to requirement PR-001"
- "Generate requirement from incident INC-456"

## [PROD-DERIVED] Requirements

Requirements generated from production incidents:
- Tagged with `[PROD-DERIVED]` for traceability
- Include incident ID reference
- Require human review before implementation
