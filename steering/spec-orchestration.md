# Spec Orchestration Guide

How Kiro manages the relationship between Living Specs and Kiro Specs based on user choice.

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

**Living Spec (AI-DLC approach)** = Project orchestrator with hypothesis-driven development
**Kiro Specs** = Feature implementation with formal methodology

## Decision Flow: Which Approach to Use

### At Project Start

When user initiates a new project, Kiro asks:

> "How would you like to organize this project?"
> 
> **A) Kiro Spec** - Separate requirements.md, design.md, tasks.md per feature
>    - Formal methodology with EARS format requirements
>    - Property-based testing support
>    - Best for: Teams preferring structured spec-driven development
> 
> **B) Living Spec (AI-DLC approach)** - Single consolidated file as source of truth
>    - Hypothesis-driven with phase tracking (Planning → Building → Operating)
>    - Integrated decision logging and cost tracking
>    - Best for: AI-heavy development, unified context, rapid iteration

User choice determines the workflow. Kiro does NOT automatically suggest switching approaches.

### On Existing Projects

Living Specs are added **only when the user explicitly requests it**:

- "Create a Living Spec for this project"
- "Add a Living Spec to coordinate my specs"
- "I want to use the AI-DLC approach now"

### Switching Approaches

Users can switch or combine approaches at any time by asking:

**Adding Living Spec to Kiro Specs project:**
```
Create a Living Spec and reference my existing Kiro specs
```

**Adding Kiro Specs to Living Spec project:**
```
Create a Kiro spec for [feature] and reference it from the Living Spec
```


## When to Use Each Approach

### Use Kiro Spec For:

| Scenario | Why Kiro Spec |
|----------|---------------|
| Individual features with clear boundaries | Focused scope, detailed tracking |
| Detailed requirements needing EARS format | Formal methodology support |
| Features requiring property-based testing | Correctness properties in design.md |
| Implementation task tracking | tasks.md with checkboxes |
| Design decisions specific to one feature | Contained in feature's design.md |
| Teams familiar with spec-driven development | Matches existing workflow |

### Use Living Spec (AI-DLC approach) For:

| Scenario | Why Living Spec |
|----------|-----------------|
| Project-wide context and goals | Single source of truth |
| Hypothesis-driven development | Intent + validation tracking |
| Cross-cutting architectural decisions | Affects multiple features |
| Unified metrics dashboard | Business + technical metrics |
| Technical debt spanning features | Centralized tracking |
| Decision history with rationale | Historical context |
| AI-heavy development | Better context for AI assistants |
| Rapid iteration with phase tracking | Planning → Building → Operating |

### Use Both Together For:

| Scenario | How They Work Together |
|----------|------------------------|
| Complex projects with many features | Living Spec coordinates, Kiro specs detail |
| Teams with mixed preferences | Some features formal, project unified |
| Projects with shared infrastructure | Living Spec for infra, Kiro specs for features |

## Kiro Behaviors

### Reference Management (when Living Spec exists)

When a Living Spec exists and user creates a new Kiro spec:
1. Kiro offers to add to "Related Kiro Specs" table
2. Suggests relevant Living Spec sections to update

### Context Loading

When working on a feature with both spec types:
- Kiro loads the feature's Kiro spec for implementation detail
- Kiro loads the Living Spec for project context
- Both inform AI recommendations

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
