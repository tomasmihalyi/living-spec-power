---
name: "living-specs"
displayName: "Living Specs"
description: "Consolidate all development artifacts into single, AI-maintainable specification files. Reduce documentation fragmentation and enable bidirectional sync between specs and code."
keywords: ["specs", "documentation", "requirements", "architecture", "ai-dlc", "spec-driven", "living-spec"]
author: "AWS"
---

# Living Specs

## Overview

Living Specs solve the documentation explosion problem in AI-driven development. Instead of fragmenting context across 10-20 files per feature, a Living Spec consolidates everything into one continuously evolving file with seven sections.

**The Problem:** AI assistants need context to be effective, but that context fragments across requirements docs, architecture decisions, implementation notes, and metrics dashboards. The coordination overhead drowns your progress.

**The Solution:** One file. Seven sections. Everything your AI assistant needs.

## Living Spec as Source of Truth

A Living Spec serves as the **single source of truth** for your entire project. It:
- References and tracks all Kiro feature specs in `.kiro/specs/`
- Provides project-wide context (business goals, metrics, architectural decisions, tech debt)
- Acts as the "master spec" that ties all feature-level specs together

This creates a hierarchical architecture:
```
.kiro/specs/
├── project.living.md          # Source of truth - references all specs below
├── feature-a/                  # Kiro feature spec
│   ├── requirements.md
│   ├── design.md
│   └── tasks.md
├── feature-b/                  # Kiro feature spec
│   ├── requirements.md
│   ├── design.md
│   └── tasks.md
└── feature-c.living.md         # Standalone Living Spec for complex features
```

## Kiro Integration Behavior

When this power is installed, Kiro will:

### When Creating a New Spec
1. Check if a Living Spec exists in `.kiro/specs/`
2. If no Living Spec exists → Suggest creating one as the project's source of truth
3. If a Living Spec exists → Offer to add a reference to the new spec in the Living Spec's "Related Specs" section

### When Working with Existing Specs
1. Validate that the Living Spec (if exists) references the spec being worked on
2. If the spec isn't referenced → Suggest adding it to maintain the source of truth
3. For complex projects → Suggest the Living Spec architecture if not already in place

### Contextual Suggestions
Kiro will suggest the Living Spec architecture based on:
- Number of existing specs (3+ specs suggests need for coordination)
- Project complexity indicators (multiple domains, cross-cutting concerns)
- When a user explicitly asks to create or work with specs

## Available Steering Files

- **creating** - Step-by-step guide to create a new Living Spec
- **maintaining** - How to keep Living Specs in sync with code

## Living Spec Structure

**Early Development:**
1. **Intent** - Problem statement, success criteria, failure triggers, scope
2. **Requirements** - Functional, non-functional, and cross-cutting requirements
3. **Architecture** - Decisions with inline ADRs, tech stack, integrations

**Build Phase:**
4. **Implementation** - Component map, API contracts, technical debt register
5. **Metrics** - Business and technical metrics with targets and status

**Iterate Phase:**
6. **Decision Log** - Historical choices with outcomes
7. **Next Actions** - Current sprint, backlog, blocked items

## Quick Start

### 1. Create Your First Living Spec

Ask Kiro:
```
Create a new Living Spec for [your project/feature]
```

Kiro will:
- Create the file in `.kiro/specs/[name].living.md`
- Check for existing specs and offer to reference them
- Guide you through the initial sections

### 2. Reference It When Working

When starting work on a feature:
```
Read .kiro/specs/project.living.md and help me implement FR-003
```

### 3. Keep It Updated

After making changes:
```
Review my changes to src/api/handler.ts and update the Living Spec
```

## What Makes Living Specs Different

**Source of Truth:** The Living Spec is the authoritative reference for your project, linking all feature specs and providing unified context.

**Bidirectional Sync:** Spec changes drive code changes. Code changes update the spec. Your AI assistant handles both directions.

**AI-Maintainable:** The structured format means AI assistants can read, understand, and update the spec autonomously.

**Historically Aware:** Decision rationale lives inline. When someone asks "why DynamoDB?", the answer is in Section 6.

## When to Use Living Specs

**Good fit:**
- Features requiring upfront planning
- Systems where multiple people need context
- Projects using AI assistants heavily
- Teams following AI-DLC or spec-driven development
- Projects with multiple Kiro specs that need coordination

**Overkill for:**
- Bug fixes
- Trivial changes
- One-off scripts

## Using with Kiro Specs

Living Specs complement Kiro's spec-driven development:

- **Kiro specs** → Feature-level planning (requirements, design, tasks)
- **Living Specs** → Project-level context (business goals, metrics, decisions, tech debt)

Create a Living Spec at the project level as your source of truth, referencing Kiro specs for feature details:

```
.kiro/specs/
├── project.living.md              # Source of truth for the project
├── payment-processing/            # Kiro feature spec
│   ├── requirements.md
│   ├── design.md
│   └── tasks.md
├── inventory-management/          # Kiro feature spec
│   ├── requirements.md
│   ├── design.md
│   └── tasks.md
└── user-experience.living.md      # Domain-specific Living Spec (optional)
```

### Referencing Kiro Specs in Living Specs

In your Living Spec's Requirements section, reference related Kiro specs:

```markdown
### Related Specs
| Spec | Path | Status | Description |
|------|------|--------|-------------|
| Payment Processing | `.kiro/specs/payment-processing/` | 🔄 In Progress | Core payment flow |
| Inventory Management | `.kiro/specs/inventory-management/` | ⬚ Not Started | Stock tracking |
| User Onboarding | `.kiro/specs/user-onboarding/` | ✅ Complete | First-time user flow |
```

## Best Practices

### Section Updates

| When you... | Update these sections |
|-------------|----------------------|
| Start a feature | 1. Intent, 2. Requirements |
| Make architecture decisions | 3. Architecture, 6. Decision Log |
| Write code | 4. Implementation |
| Ship to production | 5. Metrics, 7. Next Actions |
| Take shortcuts | 4. Implementation (Tech Debt) |
| Complete work | 7. Next Actions (move to completed) |
| Create a new Kiro spec | 2. Requirements (Related Specs) |

### File Naming

- Project-level: `project.living.md` or `[project-name].living.md`
- Domain-level: `commerce-platform.living.md`
- Feature-level: `expense-categorization.living.md`
- Always use `.living.md` extension

### Location

Place all specs in `.kiro/specs/` for consistency with Kiro's spec-driven workflow:
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

Split by domain, not by section. Create separate Living Specs for distinct systems while keeping one as the primary source of truth:
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

### "Requirements keep changing"

That's the point! Living Specs evolve. Use status indicators:
- ⬚ Not Started
- 🔄 In Progress  
- ✅ Implemented
- ❌ Dropped

Log why requirements changed in Section 6 (Decision Log).

### "Kiro specs aren't referenced in the Living Spec"

Ask Kiro to validate and update:
```
Review .kiro/specs/ and ensure all Kiro specs are referenced in the Living Spec
```

## Resources

- [AI-DLC Documentation](https://aws.amazon.com/blogs/devops/ai-driven-development-life-cycle/)
- [AI-DLC Workflows Repository](https://github.com/awslabs/aidlc-workflows)
- [Kiro Spec-Driven Development](https://kiro.dev/blog/kiro-and-the-future-of-software-development/)
