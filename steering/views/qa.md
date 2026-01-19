---
inclusion: auto
triggers: ["as QA", "QA view", "test coverage", "what needs testing", "quality assurance", "testing status"]
---

# QA View

## Focus Sections

| Section | What You Need |
|---------|---------------|
| §2 Traceability Matrix | Coverage gaps, unlinked requirements |
| §2 Requirements | Acceptance criteria for each requirement |
| §4 Execution Plan | Task completion status |

## Quick Answers

| Question | Where to Look |
|----------|---------------|
| "What's untested?" | Traceability Matrix → ⬚ Unlinked in Test IDs column |
| "What requirements changed?" | §6 Decision Log → filter by Requirements changes |
| "Is this requirement testable?" | §2 Requirements → check acceptance criteria clarity |
| "What's the coverage status?" | Traceability Matrix → count ✅ vs ⬚ |
| "What's blocking test completion?" | Current Status → Blockers |

## Red Flags

- ⬚ Requirements with no Test IDs linked
- Requirements marked ✅ but tests not passing
- Acceptance criteria that are vague or unmeasurable
- High drift score (>50%) - tests may be invalidated
- Tasks complete but no corresponding test updates

## Traceability Check

Ask: "Show traceability gaps" or "What requirements lack tests?"

Response should show:
- Requirements without test coverage
- Tests without requirement linkage (orphaned tests)
- Requirements changed since last test update
