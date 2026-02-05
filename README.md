# Living Spec Power

v2.0 - Multi-Agent Architecture

Enhanced Living Specs power for Kiro with multi-agent architecture and advanced workflow features.

## What It Does

Consolidates project documentation into a single, AI-maintainable specification file. Instead of fragmenting context across 10-20 files per feature, Living Spec keeps everything in one evolving document with seven sections aligned to AI-DLC phases (Planning → Building → Operating).

## What's New in v2.0

| Feature | Description |
|---------|-------------|
| **Multi-Agent Analysis** | Specialized agents work in parallel for brownfield analysis |
| **Comprehension Gates** | Verify developer understanding at phase transitions |
| **Tiered Approvals** | Autonomous, async, and blocking updates based on risk |
| **Domain Specialists** | Context-aware steering for DB/API/Frontend/Security work |
| **Enhanced Drift Detection** | Git-aware drift scoring with blocking at critical levels |

## Key Features

- Single source of truth for project intent, requirements, architecture, and progress
- Automatic maintenance steering ensures the spec stays updated
- Supports brownfield projects with codebase reverse engineering
- Orchestrates multiple Kiro specs at phase level (🔵/🟢/🟡)
- Multi-agent parallel analysis for comprehensive codebase understanding
- Comprehension gates prevent "skill atrophy" at phase transitions
- Tiered approval system reduces friction while maintaining control

## Three Approaches

| Approach | Best For | Creates |
|----------|----------|---------|
| A) Living Spec Only | MVPs, small teams | Single spec file |
| B) Living Spec + Kiro Specs | Multiple features, growing projects | Orchestrator + EARS feature specs |
| C) Kiro Specs Only | Formal EARS methodology | Individual specs |

## How to Import

1. Open Kiro IDE
2. Open the Powers panel (click the Powers icon in the sidebar)
3. Click "Add Custom Power" → "From Github"
4. Paste the link to this repository

## First Activation

Start a conversation mentioning "living spec" in a new or existing project.

## Multi-Agent Brownfield Analysis

When analyzing existing codebases, three agents work simultaneously:
- **Requirements Analyst** - Extracts FR/NFR in EARS format
- **Architecture Reviewer** - Analyzes design patterns
- **Risk Assessor** - Identifies security, performance, debt

## Domain Specialists

Automatically activated based on file patterns:
- **Database** - Schema, migrations, SQL
- **API** - Endpoints, REST, GraphQL
- **Frontend** - Components, React, UI
- **Security** - Auth, validation, threats
- **Testing** - Tests, coverage, QA

## Tiered Approval System

| Tier | Changes | Behavior |
|------|---------|----------|
| Tier 1 | Timestamps, status icons | Auto-updated |
| Tier 2 | Component Map, Tech Debt | Update + notify |
| Tier 3 | Requirements, Architecture | Blocks until approved |

## Enhanced Drift Detection

| Score | Status | Action |
|-------|--------|--------|
| 0-20% | ✅ Healthy | Continue |
| 21-50% | ⚠️ Review | Suggest sync |
| 51-75% | 🟠 High | Soft block |
| 76%+ | 🔴 Critical | Hard block |

## Spec Critic (Gap Analysis)

Automated quality scoring across three dimensions:

| Dimension | Checks |
|-----------|--------|
| **Completeness** | All sections have content, requirements defined |
| **Consistency** | Traces intact, components exist, statuses accurate |
| **Quality** | Problem specific, success measurable, rationale documented |

Health thresholds:
- 80-100%: ✅ Healthy
- 60-79%: ⚠️ Needs Attention  
- 0-59%: 🔴 Critical

## Hooks (Optional Automation)

| Hook | Trigger | Action |
|------|---------|--------|
| `drift-monitor` | File edited | Check drift score |
| `phase-gate-reminder` | Agent stops | Remind about gates |
| `spec-sync-prompt` | Agent stops | Prompt for updates |

## File Structure

```
living-spec-power/
├── POWER.md
├── README.md
├── hooks/
│   ├── drift-monitor.json
│   ├── phase-gate-reminder.json
│   └── spec-sync-prompt.json
└── steering/
    ├── workflow.md
    ├── multi-agent.md
    ├── parallel-analysis.md
    ├── comprehension-gates.md
    ├── tiered-approvals.md
    ├── spec-critic.md
    ├── drift-detection.md
    ├── decisions.md
    ├── template.md
    ├── maintenance-template.md
    ├── traceability.md
    ├── multi-repo.md
    ├── specialists/
    │   ├── database.md
    │   ├── api.md
    │   ├── frontend.md
    │   ├── security.md
    │   └── testing.md
    ├── adoption/
    │   └── playbook.md
    ├── compliance/
    │   └── controls.md
    ├── integrations/
    │   ├── test-tools.md
    │   └── incident-tools.md
    └── views/
        ├── developer.md
        ├── manager.md
        ├── qa.md
        └── architect.md
```

