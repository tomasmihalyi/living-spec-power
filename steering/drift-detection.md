---
inclusion: auto
triggers: ["drift", "spec outdated", "out of sync"]
---

# Spec-Code Drift Detection

## When to Check

After ANY code changes in files listed in §4 Component Map.

## Drift Score Calculation

```
drift_score = (files_changed_since_last_spec_update / total_mapped_files) × 100
```

## Thresholds

| Score | Status | Action |
|-------|--------|--------|
| 0-20% | ✅ Healthy | Continue working |
| 21-50% | ⚠️ Review | Suggest spec update |
| 51%+ | 🔴 Sync Required | Prompt before continuing |

## Auto-Detection Rules

When user completes work, check:
1. Files in Component Map modified? → Calculate drift
2. New files created not in Component Map? → Suggest addition
3. Task marked ✅ but code differs significantly? → Flag for review

## Prompt Template

After detecting drift:
```
I noticed changes to [files]. Drift score is now [X]%.

Should I update the Living Spec to reflect these changes?
- Update §4 Component Map with new files
- Update task status in §4 Execution Plan
- Add entry to §6 Decision Log
```

## Manual Check

User can ask: "Check spec drift" or "Is my spec up to date?"
