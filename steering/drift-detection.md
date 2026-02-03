---
inclusion: auto
triggers: ["drift", "spec outdated", "out of sync"]
---

# Enhanced Spec-Code Drift Detection

## When to Check

- After ANY code changes in files listed in §4 Component Map
- At start of each work session
- Before phase transitions
- When user asks "check drift" or "is spec up to date"

## Drift Score Calculation

```
drift_score = (files_changed_since_last_spec_update / total_mapped_files) × 100
```

### Factors that increase drift:
- Files modified but not reflected in spec
- New files created not in Component Map
- Deleted files still in Component Map
- Task marked ✅ but code differs significantly
- Architecture changes not documented

## Thresholds and Actions

| Score | Status | Action | Blocks Work? |
|-------|--------|--------|--------------|
| 0-20% | ✅ Healthy | Continue working | No |
| 21-50% | ⚠️ Review | Suggest spec update | No |
| 51-75% | 🟠 High | Prompt before continuing | Soft block |
| 76%+ | 🔴 Critical | Must sync before work | Hard block |

## Auto-Detection Rules

When user completes work, check:
1. Files in Component Map modified? → Calculate drift
2. New files created not in Component Map? → Suggest addition
3. Task marked ✅ but code differs significantly? → Flag for review
4. Architecture patterns changed? → Flag for §3 update

## Prompt Templates

### Healthy (0-20%)
```
✅ Spec is up to date (Drift: [X]%)
Continue working.
```

### Review Needed (21-50%)
```
⚠️ Spec drift detected: [X]%

Changes since last update:
- [file1] modified
- [file2] created

Should I update the Living Spec?
- Update §4 Component Map with new files
- Update task status in §4 Execution Plan
- Add entry to §6 Decision Log
```

### High Drift (51-75%)
```
🟠 HIGH DRIFT: [X]%

Significant changes detected:
- [list of changes]

Recommend syncing spec before continuing.
Options:
A) Sync now (recommended)
B) Continue anyway (drift will increase)
C) Review changes first
```

### Critical Drift (76%+)
```
🔴 CRITICAL DRIFT: [X]%

Spec is significantly out of sync with code.
Continuing without sync risks:
- Lost context
- Conflicting decisions
- Wasted effort

🛑 Please sync spec before continuing.
```

## Manual Check

User can ask:
- "Check spec drift"
- "Is my spec up to date?"
- "What's changed since last sync?"

## Drift Prevention

### Hooks (Optional)
Create a hook to check drift on file save:
```json
{
  "name": "Drift Check",
  "when": { "type": "fileEdited", "patterns": ["src/**"] },
  "then": { "type": "askAgent", "prompt": "Check spec drift for the edited file" }
}
```

### Session Start
Always show drift score when returning to project:
```
Welcome back!
- Phase: [Phase]
- Drift Score: [X]%
- Last Updated: [timestamp]
```

## Logging

Log drift checks in §6 Decision Log:
```
| [ISO] | Drift check: [X]% | [Phase] | [Action taken] | - |
```
