# Spec Approach Decisions

When to use Living Specs, Kiro Specs, or Full AI-DLC.

## Decision Flow

### New Projects (Greenfield)

```
New Project
    │
    ▼
┌─────────────────────────────────┐
│ What's your context?            │
├─────────────────────────────────┤
│ A) MVP / Small team / Validation│──▶ Living Spec
│    1-5 devs, high uncertainty   │
│                                 │
│ B) Feature-focused / Formal     │──▶ Kiro Specs
│    Clear boundaries, EARS needed│
│                                 │
│ C) Enterprise / Compliance      │──▶ Full AI-DLC
│    5+ devs, audit requirements  │
│                                 │
│ D) Not sure                     │──▶ Living Spec
│    Start simple, grow as needed │
└─────────────────────────────────┘
```

### Existing Projects (Brownfield)

```
Existing Project
    │
    ▼
┌─────────────────────────────────┐
│ Current state?                  │
├─────────────────────────────────┤
│ A) No specs, small (1-3 features)│──▶ Living Spec only
│                                  │
│ B) No specs, large (4+ features) │──▶ Living Spec + Kiro Specs
│                                  │
│ C) Has scattered docs            │──▶ Living Spec (consolidate)
│                                  │
│ D) Has Kiro specs already        │──▶ Add Living Spec as orchestrator
│                                  │
│ E) Needs comprehensive analysis  │──▶ Full AI-DLC first
└──────────────────────────────────┘
```

## Quick Decision Table

| Factor | Living Spec | Kiro Specs | Full AI-DLC |
|--------|-------------|------------|-------------|
| Team size | 1-5 | Any | 5+ |
| Uncertainty | High | Medium | Low |
| Iteration | Fast | Moderate | Thorough |
| AI context | Unified | Per-feature | Distributed |
| Compliance | Basic | Standard | Full audit |

## When to Use Both

Living Spec + Kiro Specs work together when:
- Complex project with many features
- Need project-level coordination AND feature-level detail
- Growing project (start Living Spec, add Kiro specs)
- Mixed team preferences

**Architecture:**
```
.kiro/specs/
├── project.living.md     # Orchestrates, tracks phases
├── feature-a/            # Detailed implementation
│   ├── requirements.md
│   ├── design.md
│   └── tasks.md
└── feature-b/
```

## Phase-Level Tracking

Living Spec tracks Kiro specs at **phase level only**:

| Spec | Path | Phase | Status |
|------|------|-------|--------|
| Auth | `.kiro/specs/auth/` | 🟢 Building | 🔄 Active |
| Payments | `.kiro/specs/payments/` | 🔵 Planning | ⬚ Pending |

**Phase meanings:**
- 🔵 Planning = requirements.md or design.md
- 🟢 Building = tasks.md, implementing
- 🟡 Operating = deployed, monitoring

**Why phase-level:** Avoids duplicating tasks.md. Task tracking stays in Kiro specs.

## Migration Patterns

### Adding Living Spec to Existing Kiro Specs

1. Create Living Spec with project-level content
2. Move cross-cutting concerns (shared architecture, project metrics)
3. Add all specs to Related Kiro Specs table with phases
4. Keep feature-specific content in Kiro specs

### Extracting Kiro Spec from Living Spec

When a feature grows too detailed (50+ lines):

1. Create `.kiro/specs/[feature]/` folder
2. Move detailed requirements → requirements.md
3. Move design details → design.md
4. Create tasks.md for implementation
5. Keep summary in Living Spec
6. Add to Related Kiro Specs table

## Content Separation

| Content Type | Where It Lives |
|--------------|----------------|
| Project goals, hypothesis | Living Spec §1 |
| Feature requirements | Kiro spec requirements.md |
| Project-level requirements | Living Spec §2 |
| Feature design | Kiro spec design.md |
| Cross-cutting architecture | Living Spec §3 |
| Feature tasks | Kiro spec tasks.md |
| Project metrics | Living Spec §5 |
| Project decisions | Living Spec §6 |

**Rule:** One source of truth per piece of information. Reference, don't duplicate.
