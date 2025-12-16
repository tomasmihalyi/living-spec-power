# Creating a Living Spec

This guide walks through creating a new Living Spec from scratch.

## Step 1: Determine the Scope

Before creating, decide the scope:

**Domain-level** (recommended for most cases):
- Covers a system or bounded context
- References multiple Kiro specs
- Examples: `commerce-platform.living.md`, `user-management.living.md`

**Feature-level** (for standalone features):
- Covers a single significant feature
- Self-contained, doesn't reference other specs
- Examples: `expense-categorization.living.md`, `notification-system.living.md`

## Step 2: Create the File

```bash
mkdir -p specs
touch specs/[name].living.md
```

## Step 3: Fill in the Template

Use this template structure:

```markdown
# Living Spec: [Feature/Domain Name]

> **Last Updated**: [Today's date]
> **Owner**: @[username]
> **Status**: 🟡 In Progress

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
- [Link to Kiro specs if applicable]

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

## Step 4: Fill in Early Sections First

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

**Section 3: Architecture** - Document:
- At least one key decision with rationale
- Initial technology choices

## Step 5: Leave Placeholders for Later Sections

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
