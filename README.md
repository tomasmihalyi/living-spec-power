# Living Specs - Kiro Power

A Kiro Power that helps you consolidate development artifacts into single, AI-maintainable specification files with intelligent orchestration of Kiro specs.

## What is Living Specs?

Living Specs solve the documentation explosion problem in AI-driven development. Instead of fragmenting context across 10-20 files per feature, a Living Spec consolidates everything into one continuously evolving file with seven sections:

1. **Intent** - Problem statement, hypothesis (optional), success criteria
2. **Requirements** - Project-level requirements + Related Kiro Specs table
3. **Architecture** - Key decisions with inline ADRs, tech stack, cost considerations
4. **Implementation** - Execution plan, component map, tech debt register
5. **Metrics** - Business and technical metrics, validation status
6. **Decision Log** - Historical choices with context and outcomes
7. **Next Actions** - Current focus, backlog, blocked items

## Smart Spec Orchestration

Living Specs manages the relationship with Kiro specs based on user choice:

- **At project start**: Asks whether you prefer Kiro Spec or Living Spec (AI-DLC approach)
- **On existing projects**: Applies Living Spec only when user explicitly requests it
- **When creating specs**: Offers to add references to the Living Spec if one exists

## Installation

1. Open Kiro's Powers panel
2. Click "Add Power" → "From Local Directory"
3. Select this `living-specs` folder
4. The power will be available immediately

## Usage

At project start, Kiro will ask your preference:

```
# Kiro asks:
"How would you like to organize this project?"
A) Kiro Spec - formal methodology with separate files
B) Living Spec (AI-DLC approach) - single consolidated file
```

To add a Living Spec to an existing project:
```
Create a Living Spec for this project
```

## Steering Files

- **creating** - Step-by-step guide to create a new Living Spec
- **maintaining** - How to keep Living Specs in sync with code and Kiro specs
- **spec-orchestration** - When and how to use Living Specs vs Kiro Specs

## File Structure

```
living-specs/
├── POWER.md              # Main documentation
├── README.md             # This file
└── steering/
    ├── creating.md       # Guide for creating new specs
    ├── maintaining.md    # Guide for keeping specs updated
    └── spec-orchestration.md  # Living Spec vs Kiro Spec guidance
```

## Quick Start

1. Start a project and choose your approach (Kiro specs or Living Spec)
2. If using Kiro specs, Kiro will suggest a Living Spec at 3+ specs
3. Reference the Living Spec when working: "Read .kiro/specs/project.living.md"
4. Keep it updated: "Review my changes and update the Living Spec"

## Two-Level Architecture

```
.kiro/specs/
├── project.living.md          # Project-level coordination
├── feature-a/                  # Feature-level detail
│   ├── requirements.md
│   ├── design.md
│   └── tasks.md
└── feature-b/
    └── ...
```

- **Living Spec**: Project goals, cross-cutting architecture, metrics, decisions
- **Kiro Specs**: Feature requirements, design, implementation tasks

## Resources

- [AI-DLC Documentation](https://aws.amazon.com/blogs/devops/ai-driven-development-life-cycle/)
- [AI-DLC Workflows Repository](https://github.com/awslabs/aidlc-workflows)
- [Kiro Spec-Driven Development](https://kiro.dev/blog/kiro-and-the-future-of-software-development/)

## License

Apache 2.0
