---
name: "living-specs"
displayName: "Living Specs"
description: "Enhanced Living Specs with multi-agent architecture, comprehension gates, tiered approvals, and domain specialists. Consolidates development artifacts into single, AI-maintainable specification files with AI-DLC principles."
keywords: ["specs", "documentation", "requirements", "architecture", "ai-dlc", "spec-driven", "living-spec", "orchestration", "single source of truth", "consolidate", "project documentation", "multi-agent", "comprehension", "domain-specialist"]
author: "AWS"
version: "2.0.0"
---

# Living Specs

One file. Seven sections. AI-DLC principles. Multi-agent architecture. Solves documentation fragmentation.

## What's New in v2.0

| Feature | Description |
|---------|-------------|
| **Multi-Agent Analysis** | Specialized agents work in parallel for brownfield analysis |
| **Comprehension Gates** | Verify developer understanding at phase transitions |
| **Tiered Approvals** | Autonomous, async, and blocking updates based on risk |
| **Domain Specialists** | Context-aware steering for DB/API/Frontend/Security work |
| **Enhanced Drift Detection** | Git-aware drift scoring with blocking at critical levels |

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

### Multi-Agent & Advanced Features

| File | Purpose |
|------|---------|
| #[[file:steering/multi-agent.md]] | Parallel agent orchestration for analysis |
| #[[file:steering/comprehension-gates.md]] | Developer understanding checkpoints |
| #[[file:steering/tiered-approvals.md]] | Risk-based approval system |

### Domain Specialists (loaded when triggered)

| File | Triggers |
|------|----------|
| #[[file:steering/specialists/database.md]] | database, schema, migration, SQL |
| #[[file:steering/specialists/api.md]] | API, endpoint, REST, GraphQL |
| #[[file:steering/specialists/frontend.md]] | frontend, component, React, UI |
| #[[file:steering/specialists/security.md]] | security, auth, validation, threats |
| #[[file:steering/specialists/testing.md]] | test, coverage, QA, testing |

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

**Key rules:** Approval gates before transitions. ISO timestamps. Never auto-transition. Comprehension gates at transitions.

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

## Tiered Approval System

| Tier | Changes | Behavior |
|------|---------|----------|
| **Tier 1: Autonomous** | Timestamps, status icons, drift scores | Auto-updated |
| **Tier 2: Async Notification** | Component Map, Tech Debt, Next Actions | Update + notify |
| **Tier 3: Synchronous Approval** | Requirements, Architecture, Phase transitions | Blocks until approved |

## File Naming

- `00-project.living.md` - Main orchestrator (sorts first)
- `01-domain.living.md` - Domain specs if needed
- Always `.living.md` extension in `.kiro/specs/`
