# Living Spec Workflow

How to create, execute, and maintain Living Specs.

## Activation

This workflow activates when:
- User says "Create a Living Spec"
- User starts a new project and chooses Living Spec approach
- User requests to add a Living Spec to existing project

## First-Time Setup

**On first activation in a project**, before creating the Living Spec:

### Step 0: Create Maintenance Steering File

Create `.kiro/steering/living-spec-maintenance.md` to ensure the Living Spec stays up-to-date.

**Process:**
1. Check if `.kiro/steering/living-spec-maintenance.md` exists
2. If not, create it using template from #[[file:steering/maintenance-template.md]]
3. Fill in project-specific details:
   - `{{PROJECT_NAME}}`: Use the project/feature name from user request
   - `{{SPEC_HIERARCHY}}`: Initially just the Living Spec being created
   - `{{PROJECT_STRATEGY}}`: Fill after completing Intent section

**Initial Spec Hierarchy (before any Kiro specs exist):**
```markdown
| Spec | Path | Phase | Description |
|------|------|-------|-------------|
| [Project Name] | `.kiro/specs/[name].living.md` | 🔵 Planning | Main project orchestrator |
```

**Initial Project Strategy (placeholder until Intent is complete):**
```markdown
**Problem**: [To be defined in Planning phase]
**Hypothesis**: [To be defined if validation-stage project]
**Success Criteria**: [To be defined in Planning phase]
**Current Phase**: 🔵 Planning
**Current Focus**: Complete Intent section
```

4. After creating the Living Spec and completing the Intent section, update the steering file with actual project details

### Why This Matters

The maintenance steering file:
- Has `inclusion: always` so it's included in every interaction
- Reminds the AI to keep the Living Spec updated
- Documents when and how to update each section
- Tracks the current spec hierarchy
- Preserves project strategy context

## Creating a Living Spec

### Step 1: Determine Scope

- **Project-level** (recommended): `project.living.md` - covers entire project
- **Domain-level**: `payments.living.md` - bounded context in large project
- **Feature-level**: `ml-pipeline.living.md` - complex standalone feature

### Step 2: Create File

Location: `.kiro/specs/[name].living.md`

Use template from: #[[file:steering/template.md]]

### Step 3: Detect Workspace

**Greenfield:**
- Set `Project Type: Greenfield`
- Skip Project Context section

**Brownfield:**
- Set `Project Type: Brownfield`
- Fill Project Context with current state
- Scan for existing Kiro specs to reference

## Phase Execution

### 🔵 Planning Phase

**Purpose:** WHAT to build and WHY

**Sections:** 1. Intent, 2. Requirements, 3. Architecture

**Execute:**
1. Fill Intent (problem, hypothesis, success criteria, scope)
2. Generate requirements questions in spec file (not chat)
3. Wait for user to fill Answer column
4. Document architecture decisions with timestamps
5. Get approval for each major decision

**Completion criteria:**
- Intent complete with measurable success criteria
- All requirements questions answered
- Architecture decisions approved

### 🟢 Building Phase

**Purpose:** HOW to build it

**Sections:** 4. Implementation, 5. Metrics (targets)

**Execute:**
1. Create execution plan with stages
2. Update stage status as work progresses (⬚ → 🔄 → ✅)
3. Add components to Component Map
4. Track technical debt with triggers
5. Set metric targets before deployment

**Completion criteria:**
- All execution plan stages complete
- Tests passing
- Ready for deployment

### 🟡 Operating Phase

**Purpose:** Deploy, monitor, iterate

**Sections:** 5. Metrics (current), 6. Decision Log, 7. Next Actions

**Execute:**
1. Deploy and track status
2. Fill current values in Metrics
3. Validate assumptions with evidence
4. Log decisions and outcomes
5. Plan iterations based on learnings

## Phase Transitions

**CRITICAL: Never auto-transition. Always ask for approval.**

### Planning → Building

1. Present summary:
   ```
   🔵 Planning Complete
   - Intent: [summary]
   - Requirements: [X] questions answered
   - Architecture: [Y] decisions approved
   
   Ready to proceed to Building?
   ```
2. Wait for explicit approval
3. Update header: `Phase: 🟢 Building`
4. Log transition in Decision Log with timestamp

### Building → Operating

1. Present summary:
   ```
   🟢 Building Complete
   - Stages: [X/Y] complete
   - Tests: Passing
   
   Ready to deploy and proceed to Operating?
   ```
2. Wait for explicit approval
3. Update header: `Phase: 🟡 Operating`
4. Log transition in Decision Log with timestamp

## Session Continuity

### Resuming Work

When returning to existing Living Spec:

1. Read header for current phase and status
2. Load context from completed sections
3. Present:
   ```
   Welcome back!
   - Phase: [Phase]
   - Stage: [Stage]
   - Next Action: [Action]
   
   A) Continue where you left off
   B) Review a previous section
   C) Check Kiro spec statuses
   ```
4. Wait for user choice

### Maintaining State

Keep Current Status updated:
```markdown
## Current Status
- **Next Action**: [What to do next]
- **Blockers**: [Any blockers]
- **Last Completed**: [Last completed stage]
```

## Updating the Spec

### When to Update Each Section

| Section | Update When |
|---------|-------------|
| 1. Intent | Goals change, scope shifts, new failure triggers |
| 2. Requirements | New Kiro spec created, spec phase changes |
| 3. Architecture | New decisions, tech stack changes |
| 4. Implementation | Stages complete, components added, debt introduced |
| 5. Metrics | New measurements, targets adjusted |
| 6. Decision Log | Any significant decision, phase transitions |
| 7. Next Actions | Tasks complete, priorities change |

### Updating the Maintenance Steering File

Also update `.kiro/steering/living-spec-maintenance.md` when:

| Change | What to Update |
|--------|----------------|
| New Kiro spec created | Add to Spec Hierarchy table |
| Kiro spec phase changes | Update phase marker in Spec Hierarchy |
| Project strategy changes | Update Project Strategy section |
| Phase transition | Update Current Phase in Project Strategy |
| Priorities change | Update Current Focus in Project Strategy |

### Decision Logging

Always include:
- ISO timestamp (e.g., `2024-12-24T10:30:00Z`)
- Phase context
- Approval status

### Kiro Spec Phase Updates

Update Related Kiro Specs table when:
- New Kiro spec created → add with 🔵 Planning
- Spec moves to tasks.md → update to 🟢 Building
- Feature deployed → update to 🟡 Operating

## Error Handling

### Incomplete Section at Transition

1. Identify missing elements
2. Present what's missing
3. Ask: complete or skip?
4. Log decision

### Spec Conflicts with Code

1. Identify conflict
2. Present both versions
3. Ask which is correct
4. Update incorrect source
5. Log resolution

### Recovery from Interruption

1. Read header for last known state
2. Check Audit Trail for last action
3. Resume from last checkpoint
4. Ask user to verify before continuing

## Adaptive Depth

Match depth to complexity:

| Complexity | Intent | Questions | Architecture | Execution |
|------------|--------|-----------|--------------|-----------|
| Simple | Brief | 3-5 | 1-2 decisions | 3-5 stages |
| Moderate | Full | 5-10 | Multiple | 5-10 stages |
| Complex | Complete | 10+ | Comprehensive | Multi-phase |

## Anti-Patterns

❌ **Duplicating task tracking** - Track phases in Living Spec, tasks in Kiro specs
❌ **Auto-transitioning phases** - Always wait for explicit approval
❌ **Skipping timestamps** - Always include ISO timestamps
❌ **Deleting history** - Mark decisions as superseded, don't delete
❌ **Vague updates** - Be specific: "Added auth service" not "Updated implementation"
