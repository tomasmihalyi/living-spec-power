# Creating a Living Spec

This guide walks through creating a new Living Spec from scratch.

## Before Creating: Choose Your Approach

At project start, Kiro asks which approach you prefer:

### Option A: Kiro Spec
- Separate files: requirements.md, design.md, tasks.md per feature
- EARS format for requirements
- Property-based testing support
- Best for: Formal methodology, structured task tracking

### Option B: Living Spec (AI-DLC approach)
- Single consolidated file as source of truth
- Hypothesis-driven with phase tracking (Planning → Building → Operating)
- Integrated decision logging and cost awareness
- Best for: AI-heavy development, unified context, rapid iteration

### Adding Living Spec to Existing Project

If you already have Kiro specs and want to add a Living Spec later:
```
Create a Living Spec for this project and reference my existing specs
```

Kiro will scan for existing specs and offer to reference them.

## Check for Existing Specs

Before creating a Living Spec, Kiro will:

1. **Scan `.kiro/specs/`** for existing Kiro feature specs
2. **Offer to reference** any existing specs in the Living Spec

### If Kiro Specs Already Exist

When you request a Living Spec on an existing project, Kiro will ask:
> "I found [N] existing Kiro specs. Would you like me to:
> A) Create a Living Spec and reference all of them
> B) Create a Living Spec and let you choose which to reference
> C) Just create the Living Spec, I'll add references later"

## Step 1: Determine the Scope

Before creating, decide the scope:

**Project-level** (recommended as source of truth):
- Covers the entire project or system
- References all Kiro feature specs
- Single source of truth for goals, metrics, decisions
- Example: `project.living.md`, `commerce-platform.living.md`

**Domain-level** (for large projects with multiple domains):
- Covers a bounded context within a larger system
- Referenced by the project-level Living Spec
- Examples: `payments.living.md`, `user-management.living.md`

**Feature-level** (for standalone complex features):
- Covers a single significant feature too complex for standard Kiro spec
- Self-contained, may not reference other specs
- Examples: `ml-pipeline.living.md`, `notification-system.living.md`

## Step 2: Create the File

Living Specs are created in `.kiro/specs/`:

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
> **Phase**: 🔵 Planning | 🟢 Building | 🟡 Operating
> **Owner**: @[username]
> **Type**: Project Source of Truth | Domain | Feature

---

## 1. Intent

### Problem Statement
[What problem are we solving? Who experiences it? What's the impact?]

### Hypothesis (optional - for validation-stage projects)
| Element | Description |
|---------|-------------|
| Problem | [Core problem being addressed] |
| Solution | [Proposed solution approach] |
| Customer | [Target user/customer] |
| Value Prop | [Why this solution wins] |

### Success Criteria
| Criteria | Target | Current | Status |
|----------|--------|---------|--------|
| 🎯 Primary | [Main success metric] | - | ⬚ |
| 📈 Secondary | [Supporting metric] | - | ⬚ |

### Failure Triggers
- [ ] [Condition that means we should pivot or stop]
- [ ] [Another failure condition]

### Scope
**In Scope:**
- [What's included]

**Out of Scope:**
- [What's explicitly excluded]

---

## 2. Requirements

### Project-Level Requirements
| ID | Requirement | Priority | Status | Spec Reference |
|----|-------------|----------|--------|----------------|
| PR-001 | [Cross-cutting requirement] | HIGH | ⬚ | - |
| PR-002 | [Another project requirement] | MEDIUM | ⬚ | - |

### Related Kiro Specs
| Spec | Path | Status | Description |
|------|------|--------|-------------|
| [Feature Name] | `.kiro/specs/[feature]/` | ⬚ | [Brief description] |

*Feature-level requirements live in Kiro specs. This section tracks project-wide concerns and references.*

---

## 3. Architecture

### System Overview
[High-level description or diagram reference]

### Key Decisions

#### Decision: [First Major Decision]
- **Date**: [Date]
- **Phase**: 🔵 Planning
- **Context**: [Why this decision is needed]
- **Options Considered**:
  1. [Option A] - [pros/cons]
  2. [Option B] - [pros/cons]
- **Choice**: [Selected option]
- **Rationale**: [Why this choice]
- **Trade-offs**: [What we're accepting]
- **Cost Impact**: [Estimated cost implications, if relevant]

### Technology Stack
| Layer | Technology | Rationale | Est. Cost |
|-------|------------|-----------|-----------|
| [Layer] | [Tech] | [Why] | [Monthly] |

---

## 4. Implementation

### Execution Plan (optional - for phased projects)
| Phase | Name | Goal | Duration | Status |
|-------|------|------|----------|--------|
| 1 | [Phase name] | [What it achieves] | [Time] | ⬚ |

### Component Map
| Component | Location | Description | Related Spec |
|-----------|----------|-------------|--------------|
| [Component] | `src/path/` | [Description] | [Spec if any] |

### Technical Debt Register
| ID | Description | Trigger Condition | Severity | Status |
|----|-------------|-------------------|----------|--------|
| TD-001 | [Debt item] | [When to address] | ⚠️ Medium | ⬚ |

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

### Validation Status (optional - for hypothesis-driven projects)
| Assumption | Validated? | Evidence |
|------------|------------|----------|
| [Key assumption] | ⬚ | - |

---

## 6. Decision Log

| Date | Decision | Context | Outcome |
|------|----------|---------|---------|
| [Today] | Created Living Spec | [Why now] | - |

---

## 7. Next Actions

### Current Focus
- [ ] **HIGH**: [First priority task]

### Backlog
- [ ] [Future task]

### Blocked
[None yet]

### Completed
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

## Step 4: Reference Existing Kiro Specs

If you have existing Kiro specs, add them to the "Related Kiro Specs" table:

```markdown
### Related Kiro Specs
| Spec | Path | Status | Description |
|------|------|--------|-------------|
| User Authentication | `.kiro/specs/user-auth/` | ✅ Complete | Login, signup, password reset |
| Payment Processing | `.kiro/specs/payments/` | 🔄 In Progress | Stripe integration |
| Inventory Management | `.kiro/specs/inventory/` | ⬚ Not Started | Stock tracking system |
```

Ask Kiro to help:
```
Scan .kiro/specs/ and add all existing Kiro specs to the Related Kiro Specs section
```

## Step 5: Fill in Early Sections First

Start with sections 1-3 (Intent, Requirements, Architecture). These establish the foundation.

**Section 1: Intent** - Answer these questions:
- What problem are we solving?
- How will we know if we succeeded?
- What would make us stop or pivot?
- What's explicitly out of scope?

**Section 2: Requirements** - Start with:
- 3-5 project-level requirements (cross-cutting concerns)
- References to all existing Kiro specs
- Note: Feature requirements stay in Kiro specs

**Section 3: Architecture** - Document:
- At least one key decision with rationale
- Initial technology choices with cost estimates

## Step 6: Leave Placeholders for Later Sections

Sections 4-7 fill in as you build:
- **Implementation**: Update as you write code
- **Metrics**: Add targets now, fill current values after launch
- **Decision Log**: Add entries as decisions are made
- **Next Actions**: Keep current with your work

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
- **Phase**: 🔵 Planning
- **Choice**: AWS Lambda + DynamoDB
- **Rationale**: Pay-per-use optimal for unknown traffic
- **Trade-offs**: Cold starts acceptable for async processing
- **Cost Impact**: ~$5-20/month at expected scale
```

### Track Technical Debt with Triggers
Don't just list debt—specify when to address it:
```markdown
| ID | Description | Trigger Condition | Severity | Status |
|----|-------------|-------------------|----------|--------|
| TD-001 | No rate limiting | 1000+ users | 🔴 High | ⬚ |
| TD-002 | Single region | >100ms latency from EU | ⚠️ Medium | ⬚ |
```

### Keep Related Kiro Specs Updated
When you create a new Kiro spec, always add it to the Living Spec:
```
I just created a new spec for [feature]. Add it to the Related Kiro Specs in .kiro/specs/project.living.md
```

## When to Extract a Kiro Spec

If a section of your Living Spec grows too detailed (50+ lines for a single feature), extract it:

1. Create a Kiro spec folder: `.kiro/specs/[feature-name]/`
2. Move detailed requirements to `requirements.md`
3. Move design details to `design.md`
4. Create `tasks.md` for implementation tracking
5. Keep a summary in the Living Spec
6. Add reference to Related Kiro Specs table

This keeps the Living Spec focused on project-level orchestration.
