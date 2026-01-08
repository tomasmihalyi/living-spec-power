---
name: "living-specs"
displayName: "Living Specs"
description: "Consolidate development artifacts into single, AI-maintainable specification files with AI-DLC principles and smart Kiro spec orchestration."
keywords: ["specs", "documentation", "requirements", "architecture", "ai-dlc", "spec-driven", "living-spec", "orchestration"]
author: "AWS"
---

# Living Specs

## Overview

Living Specs solve the documentation explosion problem in AI-driven development. Instead of fragmenting context across 10-20 files per feature, a Living Spec consolidates everything into one continuously evolving file.

**The Problem:** AI assistants need context, but it fragments across requirements, architecture decisions, implementation notes, and metrics.

**The Solution:** One file. Seven sections. AI-DLC principles. Smart orchestration of Kiro specs.

## When to Use

At project start, Kiro asks which approach fits:

| Approach | Best For |
|----------|----------|
| **Living Spec** | MVPs, small teams (1-5), AI-heavy development, rapid iteration |
| **Kiro Specs** | Clear feature boundaries, formal EARS methodology, property-based testing |
| **Full AI-DLC** | Enterprise, compliance requirements, multiple teams, comprehensive audit |

See #[[file:steering/decisions.md]] for detailed decision guidance.

## Two-Level Architecture

Living Spec orchestrates at project level; Kiro specs handle feature detail:

```
.kiro/specs/
├── project.living.md          # Project-level: orchestrates everything
├── feature-a/                  # Feature-level: detailed implementation
│   ├── requirements.md
│   ├── design.md
│   └── tasks.md
└── feature-b/
```

Living Spec tracks Kiro specs at **phase level** (🔵/🟢/🟡), not task level—avoiding duplication with tasks.md.

## AI-DLC Phases

Living Specs follow AI-DLC's three-phase workflow:

| Phase | Purpose | Sections |
|-------|---------|----------|
| 🔵 Planning | WHAT and WHY | 1. Intent, 2. Requirements, 3. Architecture |
| 🟢 Building | HOW | 4. Implementation, 5. Metrics (targets) |
| 🟡 Operating | RUN and MEASURE | 5. Metrics (current), 6. Decision Log, 7. Next Actions |

**Key principles:**
- Approval gates before phase transitions (never auto-transition)
- Adaptive depth based on complexity
- Decision logging with ISO timestamps
- Technical debt tracking with triggers

## Seven Sections

**🔵 Planning:**
1. **Intent** - Problem, hypothesis, success criteria, scope
2. **Requirements** - Questions table, project requirements, Related Kiro Specs
3. **Architecture** - Key decisions with inline ADRs, tech stack, cost estimates

**🟢 Building:**
4. **Implementation** - Execution plan, component map, tech debt register
5. **Metrics** - Business and technical targets

**🟡 Operating:**
6. **Decision Log** - Historical choices with context and outcomes
7. **Next Actions** - Current focus, backlog, blocked items

## Quick Start

### 1. Create Living Spec
```
Create a Living Spec for [project name]
```

### 2. Work Through Phases
- **Planning**: Fill Intent, Requirements, Architecture → get approval
- **Building**: Execute plan, track progress → get approval
- **Operating**: Monitor metrics, iterate

### 3. Add Kiro Specs as Needed
```
Create a Kiro spec for [feature] and reference it from the Living Spec
```

### 4. Keep Updated
```
Review my changes and update the Living Spec
```

## Steering Files

| File | Purpose |
|------|---------|
| #[[file:steering/workflow.md]] | How to create, execute, and maintain Living Specs |
| #[[file:steering/decisions.md]] | When to use Living Specs vs Kiro Specs vs Full AI-DLC |
| #[[file:steering/template.md]] | Living Spec template to copy |
| #[[file:steering/maintenance-template.md]] | Template for project maintenance steering file |

## First-Time Setup

On first activation in a project, the Living Specs power creates a maintenance steering file at `.kiro/steering/living-spec-maintenance.md`. This file:

- Has `inclusion: always` to be included in every interaction
- Defines the Living Spec as the single source of truth
- Lists when and how to update the Living Spec
- Tracks the current spec hierarchy
- Documents the project strategy/roadmap

This ensures the Living Spec stays current as the project evolves.

## File Naming

- Project-level: `project.living.md`
- Domain-level: `payments.living.md`
- Feature-level: `expense-categorization.living.md`
- Always use `.living.md` extension
- Location: `.kiro/specs/`

## Troubleshooting

**Living Spec too long?** Split by domain, not section. Create `payments.living.md`, reference from `project.living.md`.

**When to extract Kiro spec?** When a feature needs formal EARS requirements, property-based testing, or 50+ lines of requirements.

**How to track Kiro spec progress?** Phase level in Living Spec (🔵/🟢/🟡), detailed tasks in Kiro spec's tasks.md.

## Resources

- [AI-DLC Documentation](https://aws.amazon.com/blogs/devops/ai-driven-development-life-cycle/)
- [AI-DLC Workflows Repository](https://github.com/awslabs/aidlc-workflows)
