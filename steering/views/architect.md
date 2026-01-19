---
inclusion: auto
triggers: ["as architect", "architect view", "architecture view", "design decisions", "technical decisions", "system design"]
---

# Architect View

## Focus Sections

| Section | What You Need |
|---------|---------------|
| §3 Architecture | System overview, key decisions, tech stack |
| §6 Decision Log | Historical rationale for decisions |
| §4 Component Map | Current system structure |
| §4 Technical Debt Register | Architectural debt items |

## Quick Answers

| Question | Where to Look |
|----------|---------------|
| "Why did we choose this approach?" | §3 Key Decisions → Rationale field |
| "What alternatives were considered?" | §3 Key Decisions → Options field |
| "What's the current architecture?" | §3 System Overview |
| "What tech debt exists?" | §4 Technical Debt Register |
| "Who approved this design?" | §3 Key Decisions → Approval field |
| "When was this decided?" | §3 Key Decisions → Timestamp field |

## Red Flags

- Key Decisions with ⬚ Pending approval blocking Building phase
- Architecture decisions without documented rationale
- Technical debt items with "High" severity unaddressed
- Component Map out of sync with actual codebase (high drift)
- Design decisions made without considering alternatives

## Architecture Review Checklist

Before approving transition to Building phase:
- [ ] All Key Decisions have rationale documented
- [ ] Technology Stack choices justified
- [ ] Component boundaries clearly defined
- [ ] Non-functional requirements addressed (§5 Metrics targets)
- [ ] Technical debt acknowledged and prioritized

## Decision Documentation

When adding architecture decisions, ensure:
- ISO timestamp recorded
- Context explains WHY the decision was needed
- Options lists alternatives considered
- Rationale explains WHY this option was chosen
- Approval status tracked
