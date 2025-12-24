---
name: "living-specs"
displayName: "Living Specs"
description: "Consolidate all development artifacts into single, AI-maintainable specification files. Intelligently orchestrates Kiro specs and proposes Living Specs when project complexity grows."
keywords: ["specs", "documentation", "requirements", "architecture", "ai-dlc", "spec-driven", "living-spec", "orchestration"]
author: "AWS"
---

# Living Specs

## Overview

Living Specs solve the documentation explosion problem in AI-driven development. Instead of fragmenting context across 10-20 files per feature, a Living Spec consolidates everything into one continuously evolving file with seven sections.

**The Problem:** AI assistants need context to be effective, but that context fragments across requirements docs, architecture decisions, implementation notes, and metrics dashboards. The coordination overhead drowns your progress.

**The Solution:** One file. Seven sections. Smart orchestration of Kiro specs.

## Living Spec as Project Orchestrator

A Living Spec serves as the **project-level source of truth** that:
- Provides unified project context (goals, architecture, metrics, decisions)
- References and coordinates Kiro feature specs in `.kiro/specs/`
- Tracks cross-cutting concerns that span multiple features
- Maintains decision history and technical debt register
- Grows with your project complexity

This creates a two-level architecture:
```
.kiro/specs/
├── project.living.md          # Project-level: orchestrates everything below
├── feature-a/                  # Feature-level: detailed implementation
│   ├── requirements.md
│   ├── design.md
│   └── tasks.md
├── feature-b/
│   ├── requirements.md
│   ├── design.md
│   └── tasks.md
└── feature-c.living.md         # Complex feature needing its own Living Spec
```

## Kiro Integration Behavior

### At Project Start (New Project)

When a user starts a new project, Kiro asks:

> "How would you like to organize this project?"
> 
> **A) Kiro Spec** - Separate requirements.md, design.md, tasks.md per feature
>    - Formal methodology with EARS format requirements
>    - Property-based testing support
>    - Best for: Teams preferring structured spec-driven development
> 
> **B) Living Spec (AI-DLC approach)** - Single consolidated file as source of truth
>    - Hypothesis-driven with phase tracking (Planning → Building → Operating)
>    - Integrated decision logging and cost tracking
>    - Best for: AI-heavy development, unified context, rapid iteration

User choice determines the workflow for the project.

### On Existing Projects

Living Specs are applied to existing projects **only when the user explicitly requests it**:

```
Create a Living Spec for this project
```
or
```
Add a Living Spec to coordinate my existing specs
```

When requested on an existing project, Kiro will:
1. Scan `.kiro/specs/` for existing Kiro specs
2. Create the Living Spec with project-level content
3. Offer to reference all existing Kiro specs in the Related Specs table
4. Identify any cross-cutting concerns to consolidate

### When Creating New Kiro Specs (Living Spec Exists)

If a Living Spec already exists and user creates a new Kiro spec:
1. Kiro offers to add reference to Living Spec's "Related Kiro Specs" table
2. Suggests which Living Spec sections might need updates

## When to Use Each Approach

### Use Kiro Spec For:
- Individual features with clear boundaries
- Detailed requirements needing EARS format
- Features requiring property-based testing
- Implementation task tracking
- Design decisions specific to one feature
- Teams preferring formal spec-driven methodology

### Use Living Spec (AI-DLC approach) For:
- Project-wide context and goals
- Hypothesis-driven or validation-stage projects
- Cross-cutting architectural decisions
- Unified metrics dashboard
- Technical debt that spans features
- Decision history with rationale
- AI-heavy development needing unified context
- Rapid iteration with phase tracking

### When Each Approach Works Best

| Scenario | Recommended Approach |
|----------|---------------------|
| Formal methodology preference | Kiro Spec |
| Property-based testing needed | Kiro Spec |
| Single feature focus | Kiro Spec |
| AI-heavy development | Living Spec |
| Need unified project context | Living Spec |
| Hypothesis-driven/validation stage | Living Spec |
| Multiple cross-cutting concerns | Living Spec |
| Want to coordinate existing specs | Living Spec (add when needed) |

## Available Steering Files

- **creating** - Step-by-step guide to create a new Living Spec
- **maintaining** - How to keep Living Specs in sync with code and Kiro specs
- **spec-orchestration** - When and how to use Living Specs vs Kiro Specs

## Living Spec Structure

A Living Spec has seven sections that cover the full development lifecycle:

**Planning Phase (🔵):**
1. **Intent** - Problem statement, hypothesis (optional), success criteria, scope
2. **Requirements** - Project-level requirements + Related Kiro Specs table
3. **Architecture** - Key decisions with inline ADRs, tech stack, cost considerations

**Building Phase (🟢):**
4. **Implementation** - Execution plan, component map, technical debt register
5. **Metrics** - Business and technical metrics, validation status

**Operating Phase (🟡):**
6. **Decision Log** - Historical choices with context and outcomes
7. **Next Actions** - Current focus, backlog, blocked items

## Quick Start

### 1. Choose Your Approach

When starting a project, tell Kiro your preference:
```
I want to use Kiro specs for this project
```
or
```
Create a Living Spec for [your project]
```

### 2. Let Complexity Guide You

If you start with Kiro specs, Kiro will suggest a Living Spec when:
- You reach 3+ feature specs
- Cross-cutting concerns emerge
- You need unified project context

### 3. Reference It When Working

When starting work on a feature:
```
Read .kiro/specs/project.living.md and help me implement PR-003
```

### 4. Keep It Updated

After making changes:
```
Review my changes to src/api/handler.ts and update the Living Spec
```

## What Makes Living Specs Different

**Smart Orchestration:** Kiro knows when to suggest a Living Spec based on project complexity, not arbitrary rules.

**Two-Level Architecture:** Living Specs handle project-level concerns while Kiro specs handle feature-level detail. Each does what it's best at.

**Bidirectional Sync:** Spec changes drive code changes. Code changes update the spec. Your AI assistant handles both directions.

**AI-Maintainable:** The structured format means AI assistants can read, understand, and update the spec autonomously.

**Historically Aware:** Decision rationale lives inline. When someone asks "why DynamoDB?", the answer is in Section 6.

**Phase-Aware:** Optional phase tracking (Planning → Building → Operating) for projects that benefit from structured progression.

## Living Spec Template

```markdown
# Living Spec: [Project Name]

> **Last Updated**: [date]
> **Phase**: 🔵 Planning | 🟢 Building | 🟡 Operating
> **Owner**: @[username]
> **Type**: Project Source of Truth

---

## 1. Intent

### Problem Statement
[What problem, who experiences it, what's the impact]

### Hypothesis (optional)
| Element | Description |
|---------|-------------|
| Problem | |
| Solution | |
| Customer | |
| Value Prop | |

### Success Criteria
| Criteria | Target | Current | Status |
|----------|--------|---------|--------|
| 🎯 Primary | | | ⬚ |
| 📈 Secondary | | | ⬚ |

### Failure Triggers
- [ ] [Condition that means pivot or stop]

### Scope
**In Scope:** 
**Out of Scope:**

---

## 2. Requirements

### Project-Level Requirements
| ID | Requirement | Priority | Status | Spec Reference |
|----|-------------|----------|--------|----------------|
| PR-001 | [Cross-cutting requirement] | HIGH | ⬚ | - |

### Related Kiro Specs
| Spec | Path | Status | Description |
|------|------|--------|-------------|
| [Feature] | `.kiro/specs/[name]/` | ⬚ | [Brief description] |

---

## 3. Architecture

### System Overview
[High-level diagram or description]

### Key Decisions
#### Decision: [Name]
- **Date**: 
- **Phase**: 
- **Context**: 
- **Options**: 
- **Choice**: 
- **Rationale**: 
- **Trade-offs**: 
- **Cost Impact**: 

### Technology Stack
| Layer | Technology | Rationale | Est. Cost |
|-------|------------|-----------|-----------|

---

## 4. Implementation

### Execution Plan (optional)
| Phase | Name | Goal | Duration | Status |
|-------|------|------|----------|--------|

### Component Map
| Component | Location | Description | Related Spec |
|-----------|----------|-------------|--------------|

### Technical Debt Register
| ID | Description | Trigger Condition | Severity | Status |
|----|-------------|-------------------|----------|--------|

---

## 5. Metrics

### Business Metrics
| Metric | Target | Current | Status |
|--------|--------|---------|--------|

### Technical Metrics
| Metric | Target | Current | Status |
|--------|--------|---------|--------|

### Validation Status (optional)
| Assumption | Validated? | Evidence |
|------------|------------|----------|

---

## 6. Decision Log

| Date | Decision | Context | Outcome |
|------|----------|---------|---------|

---

## 7. Next Actions

### Current Focus
- [ ] **HIGH**: [task]

### Backlog
### Blocked
### Completed

---

## Appendix

### Glossary
### Change History
| Date | Author | Change |
```

## Best Practices

### Section Updates

| When you... | Update these sections |
|-------------|----------------------|
| Start a project | 1. Intent, 2. Requirements |
| Make architecture decisions | 3. Architecture, 6. Decision Log |
| Create a new Kiro spec | 2. Requirements (Related Kiro Specs) |
| Write code | 4. Implementation |
| Ship to production | 5. Metrics, 7. Next Actions |
| Take shortcuts | 4. Implementation (Tech Debt) |
| Complete work | 7. Next Actions |

### File Naming

- Project-level: `project.living.md` or `[project-name].living.md`
- Domain-level: `commerce-platform.living.md`
- Feature-level: `expense-categorization.living.md`
- Always use `.living.md` extension

### Location

Place all specs in `.kiro/specs/` for consistency:
```
project/
├── .kiro/
│   └── specs/
│       ├── project.living.md        # Source of truth
│       ├── feature-a/               # Kiro feature specs
│       └── feature-b/
├── src/
└── ...
```

## Troubleshooting

### "My Living Spec is getting too long"

Split by domain, not by section. Create separate Living Specs for distinct systems:
- `.kiro/specs/project.living.md` (primary, references others)
- `.kiro/specs/payments.living.md`
- `.kiro/specs/inventory.living.md`

### "AI isn't updating the spec"

Be explicit in your prompts:
```
Update .kiro/specs/project.living.md:
- Mark FR-003 as implemented
- Add the caching decision to the Decision Log
- Update Next Actions
```

### "Kiro specs aren't referenced in the Living Spec"

Ask Kiro to validate and update:
```
Review .kiro/specs/ and ensure all Kiro specs are referenced in the Living Spec
```

### "When should I extract a Kiro spec from the Living Spec?"

When a feature section becomes too detailed (50+ lines of requirements), extract to a Kiro spec and keep a summary in the Living Spec.

## Resources

- [AI-DLC Documentation](https://aws.amazon.com/blogs/devops/ai-driven-development-life-cycle/)
- [AI-DLC Workflows Repository](https://github.com/awslabs/aidlc-workflows)
- [Kiro Spec-Driven Development](https://kiro.dev/blog/kiro-and-the-future-of-software-development/)
