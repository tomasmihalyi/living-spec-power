# Tiered Approval System

## Overview

Not all spec changes carry equal risk. The tiered approval system reduces friction for low-risk updates while maintaining control over critical changes.

## Tier Definitions

### Tier 1: Autonomous (No Approval Required)

Changes that are mechanical, time-sensitive, or low-risk:

| Change Type | Example | Rationale |
|-------------|---------|-----------|
| Timestamps | `Last Updated: 2026-02-03T10:30:00Z` | Mechanical, always accurate |
| Status icons | `⬚ → 🔄 → ✅` | Reflects actual state |
| Drift scores | `Drift: 15%` | Calculated, not subjective |
| Phase markers | `🔵 → 🟢` (after approval) | Already approved |
| Formatting fixes | Typos, markdown fixes | No semantic change |

**Behavior:** Update immediately, no notification needed.

### Tier 2: Async Notification (Update + Notify)

Changes that are additive or low-impact but user should be aware:

| Change Type | Example | Rationale |
|-------------|---------|-----------|
| Component Map additions | New file discovered | Additive, doesn't change requirements |
| Tech Debt entries | New TODO found | Informational |
| Next Actions updates | Task completed | Reflects work done |
| Backlog additions | New idea captured | Doesn't commit to anything |
| Metric current values | `Latency: 150ms` | Observed, not target |

**Behavior:** Update immediately, then notify:
```
📝 Spec Updated (Tier 2)
- Added [component] to Component Map
- Updated Next Actions: [task] marked complete

Review at your convenience. No action required.
```

### Tier 3: Synchronous Approval (Blocks Until Approved)

Changes that affect project direction, commitments, or understanding:

| Change Type | Example | Rationale |
|-------------|---------|-----------|
| Requirements | New FR/NFR added | Commits to scope |
| Architecture decisions | Tech stack change | High impact |
| Phase transitions | Planning → Building | Major milestone |
| Success criteria | Metric targets | Defines success |
| Scope changes | In/out scope | Affects expectations |
| Hypothesis changes | Problem/solution pivot | Strategic shift |
| Failure triggers | New stop condition | Risk management |

**Behavior:** Present change, block until approved:
```
🛑 APPROVAL REQUIRED (Tier 3)

Proposed change to: [section]

Current:
[current content]

Proposed:
[new content]

Rationale: [why this change]

Approve? (yes/no/modify)
```

## Decision Matrix

When unsure which tier applies:

```
Is this change...
├── Mechanical/calculated? → Tier 1
├── Additive only? → Tier 2
├── Changing commitments? → Tier 3
├── Affecting scope? → Tier 3
├── Reversible easily? → Tier 2
└── Requiring discussion? → Tier 3
```

## Approval Request Format (Tier 3)

```markdown
## 🛑 Approval Request

**Section:** [section name]
**Tier:** 3 - Synchronous Approval
**Timestamp:** [ISO]

### Current State
[what it says now]

### Proposed Change
[what it would say]

### Rationale
[why this change is needed]

### Impact
[what this affects]

---
**Approve?** Reply with:
- `yes` - Accept as proposed
- `no` - Reject, keep current
- `modify: [your changes]` - Accept with modifications
```

## Audit Trail

All Tier 3 approvals logged in §6 Decision Log:

```
| [ISO] | [Change type] approved | [Phase] | [Brief rationale] | Approved by user |
```

## Anti-Patterns

- ❌ Treating all changes as Tier 3 (friction overload)
- ❌ Treating all changes as Tier 1 (loss of control)
- ❌ Not logging Tier 3 decisions
- ❌ Batching Tier 3 changes to avoid approvals
- ❌ Escalating to avoid responsibility
