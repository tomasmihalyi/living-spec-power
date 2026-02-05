# Living Spec Workflow

## Activation

Triggers: User mentions specs/documentation, starts new project, or says "Create a Living Spec"

## First-Time Flow

**🛑 MANDATORY: Always ask user for approach selection. Do NOT skip this step.**

### Step 1: Present Options

```
Which approach fits your project?

A) LIVING SPEC ONLY - MVPs, small teams, rapid iteration
B) LIVING SPEC + KIRO SPECS - Multiple features, growing projects
C) KIRO SPECS ONLY - Clear feature boundaries, formal EARS

Your choice (A/B/C):
```

**Do NOT proceed until user responds. This is a blocking requirement.**

### Why Living Spec?

> 💡 **For skeptical developers:** This isn't another doc to maintain. The AI updates it as you work. You just approve changes.
>
> **Time investment:** 15-30 min setup, then ~2 min per update approval.
>
> **What you get:** Single source of truth, no more hunting through wikis, requirements/architecture/tasks in one place.

### Step 2: Handle Selection

- **A/B**: Create maintenance steering file → Create Living Spec
- **C**: Exit workflow, use standard Kiro spec flow

### Step 3: Create Maintenance Steering File

For A/B, create `.kiro/steering/living-spec-maintenance.md` using #[[file:steering/maintenance-template.md]]

Replace `[PROJECT_NAME]` with actual project name.

### Step 4: Create Living Spec

Create `.kiro/specs/00-[project].living.md` using #[[file:steering/template.md]]

- **Greenfield**: Set `Project Type: Greenfield`, skip Project Context
- **Brownfield**: Set `Project Type: Brownfield`, run multi-agent reverse engineering (see #[[file:steering/multi-agent.md]])

## Brownfield Reverse Engineering (Multi-Agent)

For brownfield projects, use parallel agent analysis. See #[[file:steering/parallel-analysis.md]] for the complete workflow.

**Quick summary:** Spawn 3 parallel analysis agents:
1. `architecture-analyzer` - Structure, patterns, entry points
2. `dependency-analyzer` - Tech stack, integrations, versions
3. `quality-analyzer` - Tests, debt, security concerns

See #[[file:steering/multi-agent.md]] for agent prompt templates.

## Phase Execution

### 🔵 Planning

1. Fill Intent (problem, hypothesis, success criteria, scope)
2. Generate Requirements Questionnaire in spec file
3. **BLOCK**: "⚠️ Complete the Requirements Questionnaire before proceeding to Architecture"
4. Wait for all answers (⬚ → ✅)
5. Document architecture decisions with timestamps
6. Get approval for each decision

**Exit criteria**: Intent complete, questionnaire answered, architecture approved

### 🟢 Building

1. Create execution plan with stages
2. Update status as work progresses (⬚ → 🔄 → ✅)
3. Track components and technical debt
4. Set metric targets
5. **Activate domain specialists** based on work type (see #[[file:steering/specialists/]])

**Exit criteria**: All stages complete, tests passing

### 🟡 Operating

1. Deploy and track status
2. Fill current metric values
3. Validate assumptions with evidence
4. Log decisions and outcomes

## Phase Transitions with Comprehension Gates

**Never auto-transition. Always ask for approval AND verify comprehension.**

See #[[file:steering/comprehension-gates.md]] for full comprehension gate protocol.

### Planning → Building
```
🔵 Planning Complete
- Intent: [summary]
- Requirements: [X] questions answered
- Architecture: [Y] decisions approved

📋 COMPREHENSION CHECK (required before proceeding):
1. In your own words, what problem does this solve?
2. What's the main architectural decision and why?
3. What would make this project fail?

Ready to proceed to Building? (Answer questions first)
```

### Building → Operating
```
🟢 Building Complete
- Stages: [X/Y] complete
- Tests: Passing

📋 COMPREHENSION CHECK (required before proceeding):
1. What are the key components and how do they interact?
2. What technical debt was deferred and why?
3. What metrics will tell us if this is working?

Ready to deploy and proceed to Operating? (Answer questions first)
```

## Session Continuity

When returning to existing Living Spec:
```
Welcome back!
- Phase: [Phase]
- Next Action: [Action]
- Drift Score: [X]%

A) Continue where you left off
B) Review a previous section
C) Check Kiro spec statuses
D) Run drift detection
```

## Updating Rules (Tiered Approvals)

See #[[file:steering/tiered-approvals.md]] for full details.

### Tier 1: Autonomous (No Approval)
- Timestamps
- Status icons (⬚ → 🔄 → ✅)
- Drift scores
- Last Updated field

### Tier 2: Async Notification (Update + Notify)
- Component Map additions
- Tech Debt Register entries
- Next Actions updates
- Backlog changes

### Tier 3: Synchronous Approval (Blocks)
- Requirements changes
- Architecture decisions
- Phase transitions
- Success criteria modifications
- Scope changes

### Format Rules

- ISO timestamps always
- Status: ⬚ (not started), 🔄 (in progress), ✅ (complete)
- Phases: 🔵 Planning, 🟢 Building, 🟡 Operating

## Adaptive Depth

| Complexity | Questions | Decisions | Stages |
|------------|-----------|-----------|--------|
| Simple | 3-5 | 1-2 | 3-5 |
| Moderate | 5-10 | 3-5 | 5-10 |
| Complex | 10+ | 5+ | Multi-phase |

## Anti-Patterns

- ❌ Duplicating task tracking (phases in Living Spec, tasks in Kiro specs)
- ❌ Auto-transitioning phases
- ❌ Skipping timestamps
- ❌ Deleting history (mark superseded instead)
- ❌ Skipping comprehension gates
- ❌ Rubber-stamping without understanding

## Spec Quality Checks

Before major milestones, run spec critic. See #[[file:steering/spec-critic.md]].

**Auto-triggers:**
- Before phase transitions
- On user request ("review spec quality")
- After major code changes

**Health thresholds:**
- 80%+: ✅ Proceed
- 60-79%: ⚠️ Address issues first
- <60%: 🔴 Stop and fix
