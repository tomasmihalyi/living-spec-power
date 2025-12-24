# Spec Orchestration Guide

How Kiro manages the relationship between Living Specs and Kiro Specs, and when to suggest each approach.

## The Two-Level Architecture

```
.kiro/specs/
├── project.living.md          # Project-level: goals, architecture, metrics, coordination
├── feature-a/                  # Feature-level: detailed requirements & tasks
│   ├── requirements.md
│   ├── design.md
│   └── tasks.md
├── feature-b/
│   ├── requirements.md
│   ├── design.md
│   └── tasks.md
└── complex-feature.living.md   # Feature Living Spec (for very complex features)
```

**Living Spec** = Project orchestrator (the "what" and "why" at project level)
**Kiro Specs** = Feature implementation (the "how" for specific features)

## Decision Flow: Which Approach to Use

### At Project Start

When user initiates a new project, Kiro asks:

> "How would you like to organize this project?"
> 
> **A) Kiro Specs** - Separate requirements.md, design.md, tasks.md per feature
>    - Best for: Single features, formal methodology, property-based testing
>    - You can add a Living Spec later when complexity grows
> 
> **B) Living Spec** - Single consolidated file as source of truth
>    - Best for: Projects needing unified context, multiple concerns, AI-heavy development
>    - Can reference Kiro specs for feature details as needed

### During Development

Kiro monitors `.kiro/specs/` and suggests based on complexity:

| Spec Count | Kiro Behavior |
|------------|---------------|
| 0 specs | Ask user preference (A or B above) |
| 1-2 specs | Continue with chosen approach, mention alternatives |
| 3-5 specs | Suggest Living Spec if not exists: "Consider coordinating with a Living Spec" |
| 6+ specs | Strongly recommend: "A Living Spec would help maintain coherence" |

### Complexity Triggers

Beyond spec count, Kiro suggests Living Spec when:
- Multiple specs share architectural concerns
- User asks about "overall project" or "how things connect"
- Cross-cutting requirements emerge (auth, logging, error handling)
- User mentions needing "unified context" or "project overview"
- Technical debt spans multiple features
- Metrics need project-level tracking


## When to Use Each Approach

### Use Kiro Specs For:

| Scenario | Why Kiro Specs |
|----------|----------------|
| Individual features with clear boundaries | Focused scope, detailed tracking |
| Detailed requirements needing EARS format | Formal methodology support |
| Features requiring property-based testing | Correctness properties in design.md |
| Implementation task tracking | tasks.md with checkboxes |
| Design decisions specific to one feature | Contained in feature's design.md |
| Teams familiar with spec-driven development | Matches existing workflow |

### Use Living Spec For:

| Scenario | Why Living Spec |
|----------|-----------------|
| Project-wide context and goals | Single source of truth |
| Cross-cutting architectural decisions | Affects multiple features |
| Unified metrics dashboard | Business + technical metrics |
| Technical debt spanning features | Centralized tracking |
| Decision history affecting multiple specs | Historical context |
| Coordinating 3+ Kiro specs | Orchestration layer |
| Hypothesis-driven or validation projects | Intent + validation tracking |
| Solo developers or small teams | Less overhead, unified context |
| AI-heavy development | Better context for AI assistants |

### Use Both Together For:

| Scenario | How They Work Together |
|----------|------------------------|
| Complex projects (6+ features) | Living Spec coordinates, Kiro specs detail |
| Teams with mixed preferences | Some features formal, project unified |
| Evolving projects | Start simple, add structure as needed |
| Projects with shared infrastructure | Living Spec for infra, Kiro specs for features |

## Automatic Behaviors

### Spec Count Monitoring

Kiro tracks specs in `.kiro/specs/` and suggests appropriately:

**At 3 specs (no Living Spec):**
> "I notice you have 3 feature specs now. Would you like me to create a 
> Living Spec to coordinate them? It would provide:
> - Unified project context and goals
> - Cross-cutting architectural decisions
> - Consolidated metrics and tech debt tracking
> - Single reference point for AI context"

**At 6 specs (no Living Spec):**
> "With 6 specs, a Living Spec is recommended to maintain coherence.
> Should I create one and reference all existing specs?"

### Reference Management

When Living Spec exists and new Kiro spec is created:
1. Kiro offers to add to "Related Kiro Specs" table
2. Suggests relevant Living Spec sections to update
3. Identifies if new spec introduces cross-cutting concerns

### Context Loading

When working on a feature with both spec types:
- Kiro loads the feature's Kiro spec for implementation detail
- Kiro loads the Living Spec for project context
- Both inform AI recommendations and decisions

## Migration Patterns

### Adding Living Spec to Existing Kiro Specs

When project grows and needs coordination:

1. **Create Living Spec** with project-level content:
   ```
   Create a Living Spec for this project and reference all existing Kiro specs
   ```

2. **Move cross-cutting content** from feature specs:
   - Shared architectural decisions → Living Spec Section 3
   - Project-wide requirements → Living Spec Section 2
   - Metrics affecting multiple features → Living Spec Section 5

3. **Add all existing specs** to Related Kiro Specs table

4. **Keep feature-specific content** in Kiro specs

### Extracting Kiro Spec from Living Spec

When a Living Spec section grows too detailed:

1. **Identify the feature** that needs its own spec (50+ lines of detail)

2. **Create Kiro spec structure**:
   ```
   .kiro/specs/[feature-name]/
   ├── requirements.md
   ├── design.md
   └── tasks.md
   ```

3. **Move detailed content**:
   - Detailed requirements → requirements.md
   - Design decisions → design.md
   - Implementation tasks → tasks.md

4. **Keep summary** in Living Spec

5. **Add reference** to Related Kiro Specs table

### Converting Between Approaches

**From Kiro Specs to Living Spec:**
- Create Living Spec
- Reference all Kiro specs
- Move shared concerns to Living Spec
- Keep Kiro specs for feature detail

**From Living Spec to Kiro Specs:**
- Extract features that need formal methodology
- Keep Living Spec as coordinator
- Reference new Kiro specs from Living Spec

## Best Practices

### Keep Separation Clean

| Content Type | Where It Lives |
|--------------|----------------|
| Project goals, hypothesis | Living Spec Section 1 |
| Feature requirements | Kiro spec requirements.md |
| Project-level requirements | Living Spec Section 2 |
| Feature design | Kiro spec design.md |
| Cross-cutting architecture | Living Spec Section 3 |
| Feature tasks | Kiro spec tasks.md |
| Project metrics | Living Spec Section 5 |
| Project decisions | Living Spec Section 6 |

### Avoid Duplication

- Don't copy feature requirements into Living Spec
- Reference Kiro specs instead of duplicating
- Keep one source of truth for each piece of information

### Update Both When Needed

When making changes that affect both levels:
1. Update the Kiro spec with feature details
2. Update Living Spec with project impact
3. Log significant decisions in Living Spec Decision Log

### Regular Validation

Periodically ask Kiro:
```
Validate that all Kiro specs are referenced in the Living Spec
and check for any content that should be promoted or extracted
```
