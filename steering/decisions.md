# Spec Approach Decisions

## Quick Decision

| Factor | Living Spec | Kiro Specs |
|--------|-------------|------------|
| Team size | 1-5 | Any |
| Uncertainty | High | Medium-Low |
| Iteration | Fast | Moderate |
| Compliance | Basic | Standard |

## By Project Type

### Greenfield
| Context | Recommendation |
|---------|----------------|
| MVP, small team, high uncertainty | Living Spec |
| Clear feature boundaries, EARS needed | Kiro Specs |
| Not sure | Living Spec (grow as needed) |

### Brownfield
| Context | Recommendation |
|---------|----------------|
| No specs, 1-3 features | Living Spec only |
| No specs, 4+ features | Living Spec + Kiro Specs |
| Scattered docs | Living Spec (consolidate) |
| Has Kiro specs | Add Living Spec as orchestrator |

## Living Spec + Kiro Specs

Use both when:
- Complex project with many features
- Need project-level coordination AND feature-level detail
- Growing project

**Architecture:**
```
.kiro/specs/
├── 00-project.living.md  # Orchestrates, tracks phases
├── feature-a/            # Detailed implementation
│   ├── requirements.md
│   ├── design.md
│   └── tasks.md
```

**Phase tracking:** Living Spec tracks at phase level (🔵/🟢/🟡), tasks stay in Kiro specs.

## Content Separation

| Content | Location |
|---------|----------|
| Project goals, hypothesis | Living Spec §1 |
| Feature requirements | Kiro spec requirements.md |
| Cross-cutting architecture | Living Spec §3 |
| Feature tasks | Kiro spec tasks.md |
| Project metrics/decisions | Living Spec §5-6 |

**Rule:** One source of truth per item. Reference, don't duplicate.

## When to Extract Kiro Spec

Extract when feature has:
- 50+ lines of requirements
- Needs formal EARS methodology
- Needs property-based testing
