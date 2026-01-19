---
name: "living-specs"
displayName: "Living Specs"
description: "Consolidate development artifacts into single, AI-maintainable specification files with AI-DLC principles."
keywords: ["specs", "documentation", "requirements", "architecture", "ai-dlc", "spec-driven", "living-spec", "orchestration", "single source of truth", "consolidate", "project documentation"]
author: "AWS"
---

# Living Specs

One file. Seven sections. AI-DLC principles. Solves documentation fragmentation.

## First-Time Activation

**🛑 MANDATORY: On first trigger, you MUST ask the user which approach before doing anything else.**

| Option | Best For | Creates |
|--------|----------|---------|
| A) Living Spec Only | MVPs, small teams (1-5), rapid iteration | Living Spec + maintenance steering |
| B) Living Spec + Kiro Specs | Multiple features, growing projects | Living Spec orchestrates Kiro specs |
| C) Kiro Specs Only | Clear feature boundaries, formal EARS | Individual specs (exit this workflow) |

**Do NOT proceed until user responds with A, B, or C.**

For A/B: Create `.kiro/steering/living-spec-maintenance.md` then `.kiro/specs/00-[project].living.md`

## Steering Files

| File | Purpose |
|------|---------|
| #[[file:steering/workflow.md]] | Complete workflow: setup, phases, transitions, updates |
| #[[file:steering/decisions.md]] | When to use which approach |
| #[[file:steering/template.md]] | Living Spec template |
| #[[file:steering/maintenance-template.md]] | Maintenance steering file template |

### On-Demand Steering (loaded when triggered)

| File | Triggers |
|------|----------|
| #[[file:steering/adoption/playbook.md]] | rollout, adoption, pilot |
| #[[file:steering/drift-detection.md]] | drift, out of sync, spec outdated |
| #[[file:steering/traceability.md]] | traceability, RTM, QA |
| #[[file:steering/multi-repo.md]] | multi-repo, microservices |
| #[[file:steering/compliance/controls.md]] | SOC 2, HIPAA, GDPR, audit |
| #[[file:steering/integrations/test-tools.md]] | TestRail, Jira Test |
| #[[file:steering/integrations/incident-tools.md]] | PagerDuty, OpsGenie, incident |
| #[[file:steering/views/developer.md]] | as a developer, my tasks |
| #[[file:steering/views/manager.md]] | as a manager, project status |
| #[[file:steering/views/qa.md]] | as QA, test coverage |
| #[[file:steering/views/architect.md]] | as architect, design decisions |

## AI-DLC Phases

| Phase | Purpose | Sections |
|-------|---------|----------|
| 🔵 Planning | WHAT and WHY | 1. Intent, 2. Requirements, 3. Architecture |
| 🟢 Building | HOW | 4. Implementation, 5. Metrics |
| 🟡 Operating | RUN and MEASURE | 6. Decision Log, 7. Next Actions |

**Key rules:** Approval gates before transitions. ISO timestamps. Never auto-transition.

## Two-Level Architecture

```
.kiro/specs/
├── 00-project.living.md   # Orchestrates (sorts first)
├── feature-a/             # Kiro spec detail
│   ├── requirements.md
│   ├── design.md
│   └── tasks.md
```

Living Spec tracks Kiro specs at **phase level** (🔵/🟢/🟡), not task level.

## File Naming

- `00-project.living.md` - Main orchestrator (sorts first)
- `01-domain.living.md` - Domain specs if needed
- Always `.living.md` extension in `.kiro/specs/`
