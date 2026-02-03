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

## Tiered Update Rules

### Tier 1: Autonomous (Auto-update)
- Timestamps, status icons, drift scores
- No approval needed

### Tier 2: Async Notification (Update + Notify)
- Component Map additions
- Tech Debt entries
- Next Actions updates

### Tier 3: Synchronous Approval (Blocks)
- Requirements changes
- Architecture decisions
- Phase transitions
- Scope changes

## When to Update

1. **Task/stage complete** → Update Execution Plan status (Tier 1)
2. **New Kiro spec** → Add to Related Kiro Specs table (Tier 2)
3. **Architecture decision** → Add to Key Decisions (Tier 3)
4. **Scope change** → Update Intent section (Tier 3)
5. **Phase complete** → Update Current Status + Decision Log (Tier 3)
6. **Technical debt** → Add to Tech Debt Register (Tier 2)
7. **Priority change** → Update Next Actions (Tier 2)

## Update Format

- `Last Updated`: ISO timestamp
- Status: ⬚ (not started), 🔄 (in progress), ✅ (complete)
- Phases: 🔵 Planning, 🟢 Building, 🟡 Operating
- Decision Log: Always include ISO timestamp

## After Completing Work

> "Should I update the Living Spec to reflect this change?"

Update: Current Status, Execution Plan, Related Kiro Specs, Decision Log, Next Actions

## Spec Hierarchy

\`\`\`
Living Spec (orchestrates)
└── 00-[PROJECT_NAME].living.md (🔵 Planning)
\`\`\`

## Current Strategy

**Problem**: [To be defined]
**Current Phase**: 🔵 Planning
**Current Focus**: Complete Intent and Requirements Questionnaire

## Comprehension Gate Settings

- Planning → Building: Required
- Building → Operating: Required
- Skip allowed: Yes (logged)
```

## Updating This File

| Event | Update |
|-------|--------|
| New Kiro spec | Add to Spec Hierarchy |
| Spec phase change | Update marker (🔵→🟢→🟡) |
| Strategy decision | Update Current Strategy |
