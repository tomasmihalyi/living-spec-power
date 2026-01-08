# Maintenance Steering Template

Create at `.kiro/steering/living-spec-maintenance.md` for options A or B.

## Template

```markdown
---
inclusion: always
---

# Living Spec Maintenance

## Source of Truth

The Living Spec at `.kiro/specs/00-[PROJECT_NAME].living.md` is the **single source of truth** for this project.

## When to Update

1. **Task/stage complete** → Update Execution Plan status
2. **New Kiro spec** → Add to Related Kiro Specs table
3. **Architecture decision** → Add to Key Decisions
4. **Scope change** → Update Intent section
5. **Phase complete** → Update Current Status + Decision Log
6. **Technical debt** → Add to Tech Debt Register
7. **Priority change** → Update Next Actions

## Update Format

- `Last Updated`: ISO timestamp
- Status: ⬚ (not started), 🔄 (in progress), ✅ (complete)
- Phases: 🔵 Planning, 🟢 Building, 🟡 Operating
- Decision Log: Always include ISO timestamp

## After Completing Work

> "Should I update the Living Spec to reflect this change?"

Update: Current Status, Execution Plan, Related Kiro Specs, Decision Log, Next Actions

## Spec Hierarchy

```
Living Spec (orchestrates)
└── 00-[PROJECT_NAME].living.md (🔵 Planning)
```

## Current Strategy

**Problem**: [To be defined]
**Current Phase**: 🔵 Planning
**Current Focus**: Complete Intent and Requirements Questionnaire
```

## Updating This File

| Event | Update |
|-------|--------|
| New Kiro spec | Add to Spec Hierarchy |
| Spec phase change | Update marker (🔵→🟢→🟡) |
| Strategy decision | Update Current Strategy |
