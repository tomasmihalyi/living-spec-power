---
inclusion: auto
triggers: ["review spec", "gap analysis", "spec quality", "missing requirements", "spec health", "audit spec"]
---

# Spec Critic

## Purpose

Automated gap analysis and quality scoring for Living Specs. Identifies missing content, broken traces, and quality issues before they become problems.

## When to Run

- Before phase transitions (automatic)
- On user request ("review spec", "check spec quality")
- After major code changes
- During sprint planning
- Before stakeholder reviews

## Analysis Dimensions

### 1. Completeness Score

Check that all sections have meaningful content:

| Section | Required Content | Weight |
|---------|------------------|--------|
| §1 Intent | Problem statement, success criteria, scope | 20% |
| §2 Requirements | At least 1 requirement, questionnaire complete | 20% |
| §3 Architecture | System overview, at least 1 decision | 20% |
| §4 Implementation | Execution plan, component map | 20% |
| §5 Metrics | At least 1 metric with target | 10% |
| §6 Decision Log | At least creation entry | 5% |
| §7 Next Actions | Current focus defined | 5% |

**Scoring:**
- Section complete: Full points
- Section partial: Half points
- Section empty: Zero points

### 2. Consistency Score

Check internal consistency:

| Check | Description | Weight |
|-------|-------------|--------|
| Requirement traces | All requirements link to design | 25% |
| Design traces | All design decisions link to tasks | 25% |
| Component coverage | All components in map exist in code | 25% |
| Status accuracy | Status icons match actual state | 25% |

**Flags:**
- Orphaned requirements (no design link)
- Orphaned tasks (no requirement link)
- Ghost components (in map but not in code)
- Stale status (marked complete but code changed)

### 3. Quality Score

Check content quality:

| Check | Description | Weight |
|-------|-------------|--------|
| Problem specificity | Problem statement is concrete, not vague | 20% |
| Measurable success | Success criteria have numbers | 20% |
| Clear scope | In/out scope explicitly stated | 20% |
| Decision rationale | Decisions explain "why" | 20% |
| Actionable next | Next actions are specific | 20% |

**Red Flags:**
- Vague problem: "improve performance" (vs "reduce p99 latency to <200ms")
- Unmeasurable success: "users are happy" (vs "NPS > 50")
- Missing rationale: "chose React" (vs "chose React because team expertise")

## Report Format

```
📊 SPEC QUALITY REPORT
Generated: [ISO timestamp]

═══════════════════════════════════════════════════════
OVERALL HEALTH: [HEALTHY | NEEDS ATTENTION | CRITICAL]
═══════════════════════════════════════════════════════

## Completeness: [X]%
┌─────────────────┬────────┬─────────┐
│ Section         │ Status │ Issues  │
├─────────────────┼────────┼─────────┤
│ §1 Intent       │ ✅/⚠️/❌ │ [count] │
│ §2 Requirements │ ✅/⚠️/❌ │ [count] │
│ §3 Architecture │ ✅/⚠️/❌ │ [count] │
│ §4 Implementation│ ✅/⚠️/❌ │ [count] │
│ §5 Metrics      │ ✅/⚠️/❌ │ [count] │
│ §6 Decision Log │ ✅/⚠️/❌ │ [count] │
│ §7 Next Actions │ ✅/⚠️/❌ │ [count] │
└─────────────────┴────────┴─────────┘

## Consistency: [X]%
- Orphaned requirements: [count]
- Orphaned tasks: [count]
- Ghost components: [count]
- Stale statuses: [count]

## Quality: [X]%
- Vague items: [count]
- Missing rationale: [count]
- Unmeasurable criteria: [count]

═══════════════════════════════════════════════════════
PRIORITY FIXES
═══════════════════════════════════════════════════════

1. 🔴 [Critical issue]
2. 🟠 [High priority issue]
3. 🟡 [Medium priority issue]

═══════════════════════════════════════════════════════
RECOMMENDATIONS
═══════════════════════════════════════════════════════

[Specific actionable recommendations]
```

## Health Thresholds

| Overall Score | Status | Recommendation |
|---------------|--------|----------------|
| 80-100% | ✅ HEALTHY | Continue, minor improvements optional |
| 60-79% | ⚠️ NEEDS ATTENTION | Address issues before next phase |
| 0-59% | 🔴 CRITICAL | Stop and fix before continuing |

## Common Issues and Fixes

### Completeness Issues

| Issue | Fix |
|-------|-----|
| Empty problem statement | Interview stakeholders, document pain points |
| No success criteria | Define 1-3 measurable outcomes |
| Missing scope | List 3 things in scope, 3 out of scope |
| No architecture decisions | Document at least the main tech choice |
| Empty component map | Run codebase scan, populate from findings |

### Consistency Issues

| Issue | Fix |
|-------|-----|
| Orphaned requirement | Link to design section or mark as deferred |
| Ghost component | Remove from map or create the component |
| Broken trace | Update traceability matrix |
| Stale status | Verify actual state, update status |

### Quality Issues

| Issue | Fix |
|-------|-----|
| Vague problem | Add specific metrics, user impact |
| Unmeasurable success | Add numbers, percentages, or counts |
| Missing rationale | Document why, not just what |
| Generic next actions | Make specific: who, what, when |

## Integration with Phase Gates

Before phase transitions, spec critic runs automatically:

```
📋 PRE-TRANSITION SPEC REVIEW

Running spec critic before Planning → Building...

[Report output]

⚠️ Spec health is [X]%. 
Recommended: Address [N] critical issues before proceeding.

Options:
A) Fix issues now
B) Proceed anyway (not recommended if < 60%)
C) Review issues in detail
```

## Continuous Improvement

Track spec health over time:

```
## Spec Health History

| Date | Completeness | Consistency | Quality | Overall |
|------|--------------|-------------|---------|---------|
| [ISO] | [X]% | [X]% | [X]% | [X]% |
```

Trend analysis:
- Improving: 📈 Good progress
- Stable: ➡️ Maintaining quality
- Declining: 📉 Needs attention
