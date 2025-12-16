# Living Specs - Kiro Power

A Kiro Power that helps you consolidate development artifacts into single, AI-maintainable specification files.

## What is Living Specs?

Living Specs solve the documentation explosion problem in AI-driven development. Instead of fragmenting context across 10-20 files per feature, a Living Spec consolidates everything into one continuously evolving file with seven sections:

1. **Intent** - Problem statement, success criteria, failure triggers
2. **Requirements** - Functional, non-functional, cross-cutting
3. **Architecture** - Decisions with inline ADRs, tech stack
4. **Implementation** - Component map, API contracts, tech debt
5. **Metrics** - Business and technical metrics
6. **Decision Log** - Historical choices with outcomes
7. **Next Actions** - Sprint, backlog, blocked items

## Installation

1. Open Kiro's Powers panel
2. Click "Add Power" → "From Local Directory"
3. Select this `living-specs` folder
4. The power will be available immediately

## Usage

After installation, activate the power in chat:

```
@living-specs help me create a Living Spec for my authentication system
```

Or use the steering files for guided workflows:
- **creating** - Step-by-step guide to create a new Living Spec
- **maintaining** - How to keep Living Specs in sync with code

## File Structure

```
living-specs/
├── POWER.md              # Main documentation
├── README.md             # This file
└── steering/
    ├── creating.md       # Guide for creating new specs
    └── maintaining.md    # Guide for keeping specs updated
```

## Quick Start

1. Create a specs directory: `mkdir -p specs`
2. Ask Kiro: "Create a new Living Spec for [your feature] in specs/"
3. Reference it when working: "Read specs/my-feature.living.md and help me implement FR-003"
4. Keep it updated: "Review my changes and update the Living Spec"

## Resources

- [AI-DLC Documentation](https://aws.amazon.com/blogs/devops/ai-driven-development-life-cycle/)
- [AI-DLC Workflows Repository](https://github.com/awslabs/aidlc-workflows)
- [Kiro Spec-Driven Development](https://kiro.dev/blog/kiro-and-the-future-of-software-development/)

## License

Apache 2.0
