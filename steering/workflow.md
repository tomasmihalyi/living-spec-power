# Living Spec Workflow

## Activation

Triggers: User mentions specs/documentation, starts new project, or says "Create a Living Spec"

## First-Time Flow

### Step 1: Present Options

```
Which approach fits your project?

A) LIVING SPEC ONLY - MVPs, small teams, rapid iteration
B) LIVING SPEC + KIRO SPECS - Multiple features, growing projects
C) KIRO SPECS ONLY - Clear feature boundaries, formal EARS

Your choice (A/B/C):
```

**Wait for response.**

### Step 2: Handle Selection

- **A/B**: Create maintenance steering file → Create Living Spec
- **C**: Exit workflow, use standard Kiro spec flow

### Step 3: Create Maintenance Steering File

For A/B, create `.kiro/steering/living-spec-maintenance.md` using #[[file:steering/maintenance-template.md]]

Replace `[PROJECT_NAME]` with actual project name.

### Step 4: Create Living Spec

Create `.kiro/specs/00-[project].living.md` using #[[file:steering/template.md]]

- **Greenfield**: Set `Project Type: Greenfield`, skip Project Context
- **Brownfield**: Set `Project Type: Brownfield`, fill Project Context, scan for existing specs

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

**Exit criteria**: All stages complete, tests passing

### 🟡 Operating

1. Deploy and track status
2. Fill current metric values
3. Validate assumptions with evidence
4. Log decisions and outcomes

## Phase Transitions

**Never auto-transition. Always ask for approval.**

### Planning → Building
```
🔵 Planning Complete
- Intent: [summary]
- Requirements: [X] questions answered
- Architecture: [Y] decisions approved

Ready to proceed to Building?
```

### Building → Operating
```
🟢 Building Complete
- Stages: [X/Y] complete
- Tests: Passing

Ready to deploy and proceed to Operating?
```

## Session Continuity

When returning to existing Living Spec:
```
Welcome back!
- Phase: [Phase]
- Next Action: [Action]

A) Continue where you left off
B) Review a previous section
C) Check Kiro spec statuses
```

## Updating Rules

### Living Spec Updates

| Trigger | Update |
|---------|--------|
| Task/stage complete | Execution Plan status |
| New Kiro spec | Related Kiro Specs table |
| Architecture decision | Key Decisions section |
| Scope change | Intent section |
| Phase complete | Current Status + Decision Log |
| Technical debt | Tech Debt Register |
| Priority change | Next Actions |

### Maintenance Steering Updates

| Trigger | Update |
|---------|--------|
| New Kiro spec | Spec Hierarchy |
| Spec phase change | Phase marker (🔵→🟢→🟡) |
| Strategy change | Current Strategy section |

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
