# Creating a Living Spec

This guide walks through creating a new Living Spec from scratch.

## Before You Start: Check for Existing Specs

Before creating a Living Spec, Kiro will:

1. **Check for existing Living Specs** in `.kiro/specs/`
2. **Check for existing Kiro feature specs** in `.kiro/specs/`
3. **Suggest the appropriate approach:**
   - If no Living Spec exists → Offer to create one as the project's source of truth
   - If a Living Spec exists → Offer to reference new specs in it
   - For complex projects (3+ specs) → Recommend the Living Spec architecture

### If No Living Spec Exists

Kiro will ask:
> "I noticed you don't have a Living Spec yet. Would you like to create one as the source of truth for your project? It will reference all your feature specs and provide unified context for business goals, metrics, and architectural decisions."

### If a Living Spec Already Exists

Kiro will:
- Validate that existing specs are referenced in the Living Spec
- Offer to add any missing references
- Suggest updates if the Living Spec is out of sync

## Step 1: Determine the Scope

Before creating, decide the scope:

**Project-level** (recommended as source of truth):
- Covers the entire project or system
- References all Kiro feature specs
- Single source of truth for business goals, metrics, decisions
- Example: `project.living.md`, `commerce-platform.living.md`

**Domain-level** (for large projects with multiple domains):
- Covers a bounded context within a larger system
- Referenced by the project-level Living Spec
- Examples: `payments.living.md`, `user-management.living.md`

**Feature-level** (for standalone complex features):
- Covers a single significant feature
- Self-contained, doesn't reference other specs
- Examples: `expense-categorization.living.md`, `notification-system.living.md`

## Step 2: Create the File

Living Specs are created in `.kiro/specs/` for consistency with Kiro's spec-driven workflow:

```bash
mkdir -p .kiro/specs
touch .kiro/specs/[name].living.md
```

Or simply ask Kiro:
```
Create a Living Spec for [project/feature name]
```

## Step 3: Fill in the Template

Use this template structure:

```markdown
# Living Spec: [Project/Feature Name]

> **Last Updated**: [Today's date]
> **Owner**: @[username]
> **Status**: 🟡 In Progress
> **Type**: Project Source of Truth | Domain | Feature

---

## 1. Intent

### Problem Statement
[What problem are we solving? Who experiences it? What's the impact?]

### Success Criteria
| Criteria | Target | Measurement Method |
|----------|--------|-------------------|
| [Metric] | [Target value] | [How measured] |

### Failure Triggers
- [ ] [Condition that means we should pivot or stop]

### Scope
**In Scope:**
- [What's included]

**Out of Scope:**
- [What's explicitly excluded]

---

## 2. Requirements

### Functional Requirements
| ID | Requirement | Priority | Status |
|----|-------------|----------|--------|
| FR-001 | [Requirement] | HIGH | ⬚ Not Started |

### Non-Functional Requirements
| ID | Requirement | Target | Status |
|----|-------------|--------|--------|
| NFR-001 | Performance | [Target] | ⬚ |
| NFR-002 | Security | [Target] | ⬚ |

### Cross-Cutting Requirements
| ID | Requirement | Affects | Status |
|----|-------------|---------|--------|
| XR-001 | [Requirement] | [Systems] | ⬚ |

### Related Specs
| Spec | Path | Status | Description |
|------|------|--------|-------------|
| [Feature Name] | `.kiro/specs/[feature]/` | ⬚ | [Brief description] |

---

## 3. Architecture

### System Overview
[High-level description or diagram reference]

### Key Decisions

#### Decision: [First Major Decision]
- **Date**: [Date]
- **Status**: Proposed
- **Context**: [Why this decision is needed]
- **Options Considered**:
  1. [Option A]
  2. [Option B]
- **Choice**: [Selected option]
- **Rationale**: [Why this choice]
- **Trade-offs**: [What we're accepting]

### Technology Stack
| Layer | Technology | Rationale |
|-------|------------|-----------|
| [Layer] | [Tech] | [Why] |

---

## 4. Implementation

### Component Map
| Component | Location | Description | Owner |
|-----------|----------|-------------|-------|
| [Component] | `src/path/file.ts` | [Description] | @[owner] |

### Technical Debt Register
| ID | Description | Trigger Condition | Priority | Status |
|----|-------------|-------------------|----------|--------|
| TD-001 | [Debt item] | [When to address] | ⚠️ Monitor | |

---

## 5. Metrics

### Business Metrics
| Metric | Target | Current | Status |
|--------|--------|---------|--------|
| [Metric] | [Target] | - | ⬚ |

### Technical Metrics
| Metric | Target | Current | Status |
|--------|--------|---------|--------|
| Latency (p99) | [Target] | - | ⬚ |
| Error rate | [Target] | - | ⬚ |

---

## 6. Decision Log

| Date | Decision | Context | Outcome |
|------|----------|---------|---------|
| [Today] | Created Living Spec | [Why now] | - |

---

## 7. Next Actions

### Current Sprint
- [ ] **HIGH**: [First task] - @[owner]

### Backlog
- [ ] [Future task]

### Blocked
[None yet]

### Recently Completed
[None yet]

---

## Appendix

### Glossary
| Term | Definition |
|------|------------|
| [Term] | [Definition] |

### Change History
| Date | Author | Change |
|------|--------|--------|
| [Today] | @[username] | Initial creation |
```

## Step 4: Reference Existing Specs

If you have existing Kiro specs, add them to the "Related Specs" table:

```markdown
### Related Specs
| Spec | Path | Status | Description |
|------|------|--------|-------------|
| User Authentication | `.kiro/specs/user-auth/` | ✅ Complete | Login, signup, password reset |
| Payment Processing | `.kiro/specs/payments/` | 🔄 In Progress | Stripe integration |
| Inventory Management | `.kiro/specs/inventory/` | ⬚ Not Started | Stock tracking system |
```

Ask Kiro to help:
```
Scan .kiro/specs/ and add all existing Kiro specs to the Related Specs section
```

## Step 5: Fill in Early Sections First

Start with sections 1-3 (Intent, Requirements, Architecture). These establish the foundation.

**Section 1: Intent** - Answer these questions:
- What problem are we solving?
- How will we know if we succeeded?
- What would make us stop or pivot?
- What's explicitly out of scope?

**Section 2: Requirements** - Start with:
- 3-5 core functional requirements
- Key non-functional requirements (performance, security)
- Any cross-cutting concerns
- References to all existing Kiro specs

**Section 3: Architecture** - Document:
- At least one key decision with rationale
- Initial technology choices

## Step 6: Leave Placeholders for Later Sections

Sections 4-7 fill in as you build:
- **Implementation**: Update as you write code
- **Metrics**: Add targets now, fill current values after launch
- **Decision Log**: Add entries as decisions are made
- **Next Actions**: Keep current with your sprint

## Tips for Good Living Specs

### Be Specific in Intent
❌ "Improve user experience"
✅ "Reduce expense categorization time from 5+ hours/week to <30 minutes"

### Use Measurable Success Criteria
❌ "Users like it"
✅ "40% activation rate within 30 days, 60% week-2 retention"

### Include Failure Triggers
These help you know when to pivot:
- "<20% activation after 100 users"
- "Cost per transaction exceeds $0.50"
- "P99 latency exceeds 2 seconds"

### Document Decisions Inline
Don't create separate ADR files. Embed decisions in Section 3:
```markdown
#### Decision: Serverless Architecture
- **Date**: 2024-01-15
- **Choice**: AWS Lambda + DynamoDB
- **Rationale**: Pay-per-use optimal for unknown traffic
- **Trade-offs**: Cold starts acceptable for async processing
```

### Track Technical Debt with Triggers
Don't just list debt—specify when to address it:
```markdown
| ID | Description | Trigger Condition | Status |
|----|-------------|-------------------|--------|
| TD-001 | No rate limiting | 1000+ users | ⚠️ Monitor |
| TD-002 | Single region | >100ms latency from EU | ⬚ |
```

### Keep Related Specs Updated
When you create a new Kiro spec, always add it to the Living Spec:
```
I just created a new spec for [feature]. Add it to the Related Specs in .kiro/specs/project.living.md
```
