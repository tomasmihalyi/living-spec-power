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

```bash
mkdir -p specs
```

Then ask Kiro:
```
Create a new Living Spec for [your feature] in specs/
```

### 2. Reference It When Working

When starting work on a feature:
```
Read specs/my-feature.living.md and help me implement FR-003
```

### 3. Keep It Updated

After making changes:
```
Review my changes to src/api/handler.ts and update the Living Spec
```

## What Makes Living Specs Different

**Bidirectional Sync:** Spec changes drive code changes. Code changes update the spec. Your AI assistant handles both directions.

**AI-Maintainable:** The structured format means AI assistants can read, understand, and update the spec autonomously.

**Historically Aware:** Decision rationale lives inline. When someone asks "why DynamoDB?", the answer is in Section 6.

## When to Use Living Specs

**Good fit:**
- Features requiring upfront planning
- Systems where multiple people need context
- Projects using AI assistants heavily
- Teams following AI-DLC or spec-driven development

**Overkill for:**
- Bug fixes
- Trivial changes
- One-off scripts

## Using with Kiro Specs

Living Specs complement Kiro's spec-driven development:

- **Kiro specs** → Feature-level planning (requirements, design, tasks)
- **Living Specs** → Domain-level context (business goals, metrics, decisions, tech debt)

Create Living Specs at the system/domain level, referencing Kiro specs for feature details:

```
.kiro/specs/                          # Feature planning
├── payment-processing/
└── inventory-management/

specs/                                # Operational context
├── commerce-platform.living.md       # References multiple Kiro specs
└── user-experience.living.md         # Cross-cutting concerns
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

### File Naming

- Domain-level: `commerce-platform.living.md`
- Feature-level: `expense-categorization.living.md`
- Always use `.living.md` extension

### Location

Place Living Specs in `specs/` at your project root:
```
project/
├── specs/
│   ├── core-platform.living.md
│   └── user-experience.living.md
├── src/
└── ...
```

## Troubleshooting

### "My Living Spec is getting too long"

Split by domain, not by section. Create separate Living Specs for distinct systems:
- `specs/payments.living.md`
- `specs/inventory.living.md`
- `specs/analytics.living.md`

### "AI isn't updating the spec"

Be explicit in your prompts:
```
Update specs/my-feature.living.md:
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

## Resources

- [AI-DLC Documentation](https://aws.amazon.com/blogs/devops/ai-driven-development-life-cycle/)
- [AI-DLC Workflows Repository](https://github.com/awslabs/aidlc-workflows)
- [Kiro Spec-Driven Development](https://kiro.dev/blog/kiro-and-the-future-of-software-development/)
