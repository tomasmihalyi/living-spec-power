# Maintaining Living Specs

This guide covers how to keep Living Specs in sync with your codebase and evolving requirements.

## Core Principle: Bidirectional Sync

Living Specs work in both directions:
- **Spec → Code**: Requirements and decisions drive implementation
- **Code → Spec**: Implementation changes update the spec

Your AI assistant handles both directions when you're explicit about what changed.

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
Update the Intent section in specs/expense-tracker.living.md to reflect
this pivot and add a new success criteria for mobile adoption.
```

### Section 2: Requirements
**Update when:**
- Requirements are implemented (change status)
- New requirements are added
- Requirements are dropped or deferred
- Priority changes

**Status indicators:**
- ⬚ Not Started
- 🔄 In Progress
- ✅ Implemented
- ❌ Dropped
- ⏸️ Deferred

**Example prompt:**
```
I just finished implementing FR-003 (CSV export) in src/api/exports.ts.
Update specs/expense-tracker.living.md:
- Mark FR-003 as implemented
- Add FR-004 for PDF export to the backlog
```

### Section 3: Architecture
**Update when:**
- New architectural decisions are made
- Existing decisions are superseded
- Technology stack changes
- New integrations are added

**Decision status flow:**
- Proposed → Accepted → (optionally) Deprecated/Superseded

**Example prompt:**
```
We decided to switch from REST to GraphQL for the mobile API.
Update the Architecture section:
- Mark the REST decision as superseded
- Add a new decision for GraphQL with rationale
- Update the Technology Stack table
```

### Section 4: Implementation
**Update when:**
- New components are added
- Files are moved or renamed
- Technical debt is introduced
- Technical debt is resolved
- Dependencies change

**Example prompt:**
```
I refactored the categorization service:
- Moved from src/services/categorize.ts to src/ml/categorization/
- Split into multiple files
- Added a new dependency on @aws-sdk/bedrock

Update the Implementation section in specs/expense-tracker.living.md
```

### Section 5: Metrics
**Update when:**
- New measurements are available
- Targets are adjusted
- Metrics are added or removed
- Status changes (hitting/missing targets)

**Example prompt:**
```
We launched last week. Here are the initial metrics:
- Activation rate: 38% (target: 40%)
- Categorization accuracy: 91% (target: 85%)

Update the Metrics section with current values and status indicators.
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
Sprint update for specs/expense-tracker.living.md:
- Completed: CSV export (FR-003)
- New blocker: SSO implementation waiting on enterprise contract
- New high priority: Rate limiting before we hit 1000 users
```

## Sync Patterns

### After Implementing a Feature

```
I just implemented [feature] in [files].

Update specs/[name].living.md:
1. Mark [requirement ID] as implemented
2. Add any new components to Implementation section
3. Log any decisions made during implementation
4. Move completed tasks in Next Actions
```

### After a Planning Session

```
We had a planning session and decided:
- [Decision 1]
- [Decision 2]
- New requirements: [list]

Update specs/[name].living.md with these changes across
Architecture, Requirements, and Decision Log sections.
```

### After Launching to Production

```
We launched [feature] to production.

Update specs/[name].living.md:
1. Update Metrics section with baseline measurements
2. Add any post-launch tasks to Next Actions
3. Note the launch in Decision Log
```

### During Code Review

```
Review my changes to [files] and suggest updates to
specs/[name].living.md if any sections need updating.
```

## Handling Common Scenarios

### Requirements Changed Mid-Sprint

1. Update the requirement status and description
2. Log the change in Decision Log with context
3. Adjust Next Actions

```markdown
## 6. Decision Log
| Date | Decision | Context | Outcome |
|------|----------|---------|---------|
| 2024-02-15 | Changed FR-003 from CSV to Excel export | Customer feedback: 80% use Excel | 🔄 In Progress |
```

### Technical Debt Was Introduced

Add to the Tech Debt Register with a trigger condition:

```markdown
| ID | Description | Trigger Condition | Priority | Status |
|----|-------------|-------------------|----------|--------|
| TD-003 | Hardcoded API keys | Before open-sourcing | 🔴 Critical | |
| TD-004 | No pagination | >1000 records | ⚠️ Monitor | |
```

### Architecture Decision Was Wrong

Don't delete—supersede:

```markdown
#### Decision: REST API (SUPERSEDED)
- **Date**: 2024-01-15
- **Status**: Superseded by GraphQL decision (2024-02-20)
- **Choice**: REST API
- **Outcome**: ❌ Mobile team found REST too chatty for their use case

#### Decision: GraphQL API
- **Date**: 2024-02-20
- **Status**: Accepted
- **Context**: REST API required too many round trips for mobile
- **Choice**: GraphQL with Apollo Server
- **Rationale**: Single request for complex data needs
```

### Metrics Aren't Being Hit

Update status and add action items:

```markdown
## 5. Metrics
| Metric | Target | Current | Trend | Status |
|--------|--------|---------|-------|--------|
| Activation rate | 40% | 32% | ↓ | 🔴 |

## 7. Next Actions
### Current Sprint
- [ ] **HIGH**: Investigate activation drop - @alice
- [ ] **HIGH**: A/B test onboarding flow changes
```

## Automation Tips

### Git Hooks

Consider a pre-commit reminder:
```bash
# .git/hooks/pre-commit
if git diff --cached --name-only | grep -q "^src/"; then
  echo "📝 Remember to update the Living Spec if needed"
fi
```

### PR Templates

Add to your PR template:
```markdown
## Living Spec Updates
- [ ] Updated Implementation section (if new/moved files)
- [ ] Logged decisions in Decision Log (if applicable)
- [ ] Updated requirement status (if completing a requirement)
- [ ] N/A - No spec updates needed
```

### Periodic Reviews

Schedule monthly reviews:
```
Review specs/[name].living.md for staleness:
- Are all requirement statuses current?
- Are metrics up to date?
- Is the tech debt register accurate?
- Are Next Actions reflecting current priorities?
```

## Anti-Patterns to Avoid

### ❌ Letting the Spec Drift
Don't wait until the spec is completely out of date. Update incrementally.

### ❌ Over-Documenting
Not every code change needs a spec update. Focus on:
- Requirement completions
- Architectural decisions
- Significant technical debt
- Metric changes

### ❌ Deleting History
Never delete from Decision Log. Mark decisions as superseded instead.

### ❌ Vague Updates
❌ "Updated implementation"
✅ "Added rate limiting service to Implementation, marked TD-001 as resolved"
