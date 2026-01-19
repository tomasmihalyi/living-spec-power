---
inclusion: auto
triggers: ["multi-repo", "microservices", "cross-repo", "monorepo", "multiple repositories", "distributed"]
---

# Multi-Repository Orchestration

## When to Use

- Feature spans 2+ repositories
- Shared dependencies between services
- Coordinated releases required

## Structure

```
architecture-repo/
└── .kiro/specs/
    └── 00-platform.living.md    # Parent orchestrator

service-a-repo/
└── .kiro/
    ├── specs/00-service-a.living.md
    └── _spec-link.yml           # Links to parent

service-b-repo/
└── .kiro/
    ├── specs/00-service-b.living.md
    └── _spec-link.yml
```

## _spec-link.yml Format

```yaml
parent_spec: "https://github.com/org/arch-repo/blob/main/.kiro/specs/00-platform.living.md"
owns_sections: ["§4.2 Service A Components"]
depends_on: ["service-b §4.1 Auth Module"]
sync_phase: true  # Update parent when phase changes
```

## Parent Spec Aggregation

Parent's §2 Related Kiro Specs shows aggregated status:

| Service | Repo | Phase | Last Sync |
|---------|------|-------|-----------|
| Service A | org/svc-a | 🟢 Building | 2026-01-15 |
| Service B | org/svc-b | 🔵 Planning | 2026-01-14 |
| Service C | org/svc-c | 🟡 Operating | 2026-01-10 |

## Cross-Repo Dependencies

Track in parent spec §3 Architecture:
- Which services depend on which
- Shared contracts/APIs
- Deployment order constraints

## Sync Commands

- "Sync status from child repos"
- "Show cross-repo dependencies"
- "Which services block Service A?"
