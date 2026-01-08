# Living Specs - Kiro Power

Consolidate development artifacts into single, AI-maintainable specification files with AI-DLC principles.

## What is Living Specs?

Living Specs solve the documentation explosion problem. Instead of fragmenting context across 10-20 files per feature, consolidate everything into one continuously evolving file with seven sections aligned to AI-DLC phases.

## Three Approaches

| Approach | Best For |
|----------|----------|
| **Living Spec** | MVPs, small teams, AI-heavy development |
| **Kiro Specs** | Clear feature boundaries, formal methodology |
| **Full AI-DLC** | Enterprise, compliance, multiple teams |

## AI-DLC Phases

- **🔵 Planning** - Intent, Requirements, Architecture (WHAT and WHY)
- **🟢 Building** - Implementation, Metrics targets (HOW)
- **🟡 Operating** - Metrics, Decisions, Next Actions (RUN and MEASURE)

## Two-Level Architecture

```
.kiro/specs/
├── project.living.md     # Project-level: orchestrates everything
├── feature-a/            # Feature-level: detailed implementation
│   ├── requirements.md
│   ├── design.md
│   └── tasks.md
└── feature-b/
```

Living Spec tracks Kiro specs at **phase level** (🔵/🟢/🟡), not task level.

## Installation

1. Open Kiro's Powers panel
2. Click "Add Power" → "From Local Directory"
3. Select this `living-specs` folder

## Usage

```
Create a Living Spec for [project name]
```

On first activation, the power creates a maintenance steering file at `.kiro/steering/living-spec-maintenance.md` that ensures the Living Spec stays up-to-date as the single source of truth.

## File Structure

```
living-specs/
├── POWER.md              # Main documentation
├── README.md             # This file
└── steering/
    ├── workflow.md       # How to create, execute, maintain
    ├── decisions.md      # When to use which approach
    ├── template.md       # Living Spec template
    └── maintenance-template.md  # Project steering file template
```

## Resources

- [AI-DLC Documentation](https://aws.amazon.com/blogs/devops/ai-driven-development-life-cycle/)
- [AI-DLC Workflows Repository](https://github.com/awslabs/aidlc-workflows)

## License

Apache 2.0
