# Maintaining Living Specs

This guide covers how to keep Living Specs in sync with your codebase, Kiro specs, and evolving requirements.

## Core Principle: Two-Level Architecture

The Living Spec is the **project-level source of truth**. It must:
- Reference all Kiro feature specs in `.kiro/specs/`
- Track cross-cutting concerns and decisions
- Stay in sync with code changes
- Coordinate feature-level work

Kiro specs handle **feature-level detail**. They contain:
- Detailed requirements (EARS format)
- Feature-specific design decisions
- Implementation tasks
- Property-based testing specs

Your AI assistant handles bidirectional sync when you're explicit about what changed.

## Managing Kiro Spec References

### When New Kiro Specs Are Created

Kiro will automatically prompt:
> "Add [new-spec] to the Living Spec's Related Kiro Specs table?"

If yes, Kiro updates:
```markdown
| [Feature Name] | `.kiro/specs/[path]/` | ⬚ Not Started | [Description] |
```

### Periodic Validation

Ask Kiro to check alignment:
```
Validate that all Kiro specs in .kiro/specs/ are referenced in the Living Spec
```

Kiro will:
1. Scan `.kiro/specs/` for all feature spec folders
2. Compare against the Related Kiro Specs table
3. Report any missing references
4. Offer to add them

### Keeping References Current

Update the Related Kiro Specs table when:
- A new Kiro spec is created
- A spec is completed or archived
- A spec's status changes

Status indicators:
- ⬚ Not Started
- 🔄 In Progress
- ✅ Complete
- ❌ Dropped
- ⏸️ Deferred


## Bidirectional Sync

Living Specs work in both directions:
- **Spec → Code**: Requirements and decisions drive implementation
- **Code → Spec**: Implementation changes update the spec

## When to Update Each Section

### Section 1: Intent
**Update when:**
- Business goals change
- Success criteria are refined based on learnings
- Scope expands or contracts
- New failure triggers are identified

**Example prompt:**
```
We learned that mobile users prefer photo upload over email forwarding.
Update the Intent section in .kiro/specs/project.living.md to reflect
this pivot and add a new success criteria for mobile adoption.
```

### Section 2: Requirements
**Update when:**
- Project-level requirements change status
- New cross-cutting requirements are added
- Requirements are dropped or deferred
- New Kiro specs are created (add to Related Kiro Specs)
- Kiro spec status changes

**Example prompt:**
```
I just created a new Kiro spec at .kiro/specs/notifications/.
Update .kiro/specs/project.living.md:
- Add to Related Kiro Specs table
- Add PR-005 for cross-cutting notification preferences
```

### Section 3: Architecture
**Update when:**
- New architectural decisions are made
- Existing decisions are superseded
- Technology stack changes
- New integrations are added
- Cost estimates change

**Decision status flow:**
- Proposed → Accepted → (optionally) Deprecated/Superseded

**Example prompt:**
```
We decided to switch from REST to GraphQL for the mobile API.
Update the Architecture section:
- Mark the REST decision as superseded
- Add a new decision for GraphQL with rationale
- Update the Technology Stack table
- Note cost impact if any
```

### Section 4: Implementation
**Update when:**
- New components are added
- Files are moved or renamed
- Technical debt is introduced
- Technical debt is resolved
- Execution plan phases complete

**Example prompt:**
```
I refactored the categorization service:
- Moved from src/services/categorize.ts to src/ml/categorization/
- Split into multiple files
- Added a new dependency on @aws-sdk/bedrock

Update the Implementation section in .kiro/specs/project.living.md
```

### Section 5: Metrics
**Update when:**
- New measurements are available
- Targets are adjusted
- Metrics are added or removed
- Assumptions are validated or invalidated

**Example prompt:**
```
We launched last week. Here are the initial metrics:
- Activation rate: 38% (target: 40%)
- Categorization accuracy: 91% (target: 85%)

Update the Metrics section with current values and status indicators.
Also mark the "users want auto-categorization" assumption as validated.
```

### Section 6: Decision Log
**Update when:**
- Any significant decision is made
- Outcomes of past decisions become known
- Decisions are revisited

**This is your "why" archive.** Future developers will thank you.

**Example prompt:**
```
We decided to use Stripe instead of building our own payment processing.
Log this decision with:
- Context: Need payment processing for premium tier
- Options: Build custom, Stripe, PayPal
- Choice: Stripe
- Rationale: Faster time to market, PCI compliance handled
```

### Section 7: Next Actions
**Update when:**
- Tasks are completed
- New tasks are identified
- Priorities change
- Blockers appear or are resolved

**Example prompt:**
```
Sprint update for .kiro/specs/project.living.md:
- Completed: CSV export (PR-003)
- New blocker: SSO implementation waiting on enterprise contract
- New high priority: Rate limiting before we hit 1000 users
```


## Promoting Content Between Levels

### Moving Content to Living Spec

When patterns emerge across Kiro specs:
1. Identify shared decisions/requirements
2. Move to appropriate Living Spec section
3. Reference from Kiro specs: "See Living Spec Section 3 for architecture"

### Extracting to Kiro Spec

When Living Spec section becomes too detailed (50+ lines for a feature):
1. Create Kiro spec folder: `.kiro/specs/[feature-name]/`
2. Move detailed requirements to `requirements.md`
3. Move design details to `design.md`
4. Create `tasks.md` for implementation tracking
5. Keep summary in Living Spec
6. Add to Related Kiro Specs table

## Handling Common Scenarios

### New Kiro Spec Not Referenced

If Kiro detects a spec that isn't in the Living Spec:
> "I noticed .kiro/specs/new-feature/ isn't referenced in your Living Spec.
> Would you like me to add it to the Related Kiro Specs section?"

### Requirements Changed Mid-Sprint

1. Update the requirement status and description
2. Log the change in Decision Log with context
3. Adjust Next Actions

```markdown
## 6. Decision Log
| Date | Decision | Context | Outcome |
|------|----------|---------|---------|
| 2024-02-15 | Changed PR-003 scope | Customer feedback | 🔄 In Progress |
```

### Technical Debt Was Introduced

Add to the Tech Debt Register with a trigger condition:

```markdown
| ID | Description | Trigger Condition | Severity | Status |
|----|-------------|-------------------|----------|--------|
| TD-003 | Hardcoded API keys | Before open-sourcing | 🔴 High | ⬚ |
| TD-004 | No pagination | >1000 records | ⚠️ Medium | ⬚ |
```

### Architecture Decision Was Wrong

Don't delete—supersede:

```markdown
#### Decision: REST API (SUPERSEDED)
- **Date**: 2024-01-15
- **Status**: Superseded by GraphQL decision (2024-02-20)
- **Choice**: REST API
- **Outcome**: ❌ Mobile team found REST too chatty

#### Decision: GraphQL API
- **Date**: 2024-02-20
- **Status**: Accepted
- **Context**: REST API required too many round trips for mobile
- **Choice**: GraphQL with Apollo Server
- **Rationale**: Single request for complex data needs
```

### Phase Transitions

When moving between phases (Planning → Building → Operating):
1. Update the Phase indicator in the header
2. Log the transition in Decision Log
3. Review and update Next Actions for new phase
4. Never auto-transition—always confirm with user

## Sync Patterns

### After Implementing a Feature

```
I just implemented [feature] in [files].

Update .kiro/specs/project.living.md:
1. Mark related requirement as implemented
2. Add any new components to Implementation section
3. Log any decisions made during implementation
4. Move completed tasks in Next Actions
5. Update Related Kiro Specs status if applicable
```

### After Creating a New Kiro Spec

```
I just created a new Kiro spec at .kiro/specs/[feature-name]/.

Update .kiro/specs/project.living.md:
1. Add the new spec to Related Kiro Specs table
2. Add any project-level requirements to Requirements section
3. Update Next Actions with coordination tasks
```

### After a Planning Session

```
We had a planning session and decided:
- [Decision 1]
- [Decision 2]
- New requirements: [list]

Update .kiro/specs/project.living.md with these changes across
Architecture, Requirements, and Decision Log sections.
```

### After Launching to Production

```
We launched [feature] to production.

Update .kiro/specs/project.living.md:
1. Update Metrics section with baseline measurements
2. Update Phase to 🟡 Operating if appropriate
3. Add any post-launch tasks to Next Actions
4. Note the launch in Decision Log
5. Update Related Kiro Specs status
```

## Anti-Patterns to Avoid

### ❌ Letting the Spec Drift
Don't wait until the spec is completely out of date. Update incrementally.

### ❌ Missing Spec References
Every Kiro spec should be referenced in the Living Spec. Run periodic validation.

### ❌ Over-Documenting
Not every code change needs a spec update. Focus on:
- Requirement completions
- Architectural decisions
- Significant technical debt
- Metric changes
- New Kiro specs

### ❌ Deleting History
Never delete from Decision Log. Mark decisions as superseded instead.

### ❌ Vague Updates
❌ "Updated implementation"
✅ "Added rate limiting service, marked TD-001 resolved, added .kiro/specs/rate-limiting/ to Related Specs"

### ❌ Duplicating Detail
Keep feature details in Kiro specs, project context in Living Spec. Don't duplicate.
