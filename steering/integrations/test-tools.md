---
inclusion: auto
triggers: ["TestRail", "Jira Test", "test management", "test integration", "sync tests"]
---

# Test Tool Integration

## Supported Tools (via MCP)

| Tool | MCP Server | Status |
|------|------------|--------|
| TestRail | `@testrail/mcp-server` | Available |
| Jira Test Management | `@atlassian/mcp-jira-test` | Available |
| Zephyr | `@smartbear/mcp-zephyr` | Planned |

## Sync Behavior

| Living Spec Event | Test Tool Action |
|-------------------|------------------|
| Requirement added to §2 | Create test case placeholder |
| Test ID added to Traceability Matrix | Link to existing test case |
| Requirement marked ✅ | Check test execution status |
| Requirement changed | Flag linked tests for review |

## Setup

Add to project's `.kiro/mcp.json`:

```json
{
  "mcpServers": {
    "testrail": {
      "command": "npx",
      "args": ["-y", "@testrail/mcp-server"],
      "env": {
        "TESTRAIL_URL": "$TESTRAIL_URL",
        "TESTRAIL_API_KEY": "$TESTRAIL_API_KEY"
      }
    }
  }
}
```

## Usage

After setup, ask:
- "Link requirement PR-001 to TestRail case TC-123"
- "Check test status for all requirements"
- "Create test cases for unlinked requirements"
