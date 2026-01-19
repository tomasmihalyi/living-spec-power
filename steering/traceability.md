---
inclusion: auto
triggers: ["traceability", "RTM", "test coverage", "requirements matrix", "QA", "trace requirements"]
---

# Traceability Management

## Linking Rules

| From | To | Requirement |
|------|----|-------------|
| Requirement (§2) | Design (§3) | MUST link to ≥1 design section |
| Design (§3) | Task (§4) | SHOULD link to ≥1 task |
| Task (§4) | Test | SHOULD link to ≥1 test (when tests exist) |

## Orphan Detection

Automatically flag items missing connections:
- Requirements with no design reference → ⬚ Unlinked
- Tasks with no test coverage → ⬚ Unlinked
- Tests with no requirement linkage → Orphaned test

## Status Values

| Status | Meaning |
|--------|---------|
| ⬚ Unlinked | Missing required connections |
| 🔄 Partial | Some links present, others missing |
| ✅ Complete | Fully traced end-to-end |

## Updating the Matrix

When adding requirements:
1. Add to §2 Project-Level Requirements
2. Matrix auto-adds row with ⬚ status
3. Link to design section when architecture defined
4. Link to tasks when implementation planned
5. Link to tests when test cases created

## QA Review Prompt

Ask: "Show traceability gaps" or "What requirements lack tests?"
