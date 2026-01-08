# Living Spec Template

```markdown
# Living Spec: [Project/Feature Name]

> **Last Updated**: [ISO timestamp]
> **Phase**: 🔵 Planning | 🟢 Building | 🟡 Operating
> **Current Stage**: [Stage within phase]
> **Project Type**: Greenfield | Brownfield
> **Owner**: @[username]

## Current Status
- **Next Action**: [What to do next]
- **Blockers**: [Any blockers]
- **Last Completed**: [Last completed stage]

---

## 1. Intent

### Project Context (Brownfield Only)
| Aspect | Current State |
|--------|---------------|
| Existing Architecture | [Description] |
| Technology Stack | [Current stack] |
| Key Dependencies | [Main dependencies] |

### Problem Statement
[What problem are we solving? Who experiences it? What's the impact?]

### Hypothesis (optional)
| Element | Description |
|---------|-------------|
| Problem | [Core problem] |
| Solution | [Proposed approach] |
| Customer | [Target user] |
| Value Prop | [Why this wins] |

### Success Criteria
| Criteria | Target | Current | Status |
|----------|--------|---------|--------|
| 🎯 Primary | [Main metric] | - | ⬚ |
| 📈 Secondary | [Supporting metric] | - | ⬚ |

### Failure Triggers
- [ ] [Condition to pivot or stop]

### Scope
**In Scope:** [What's included]
**Out of Scope:** [What's excluded]

---

## 2. Requirements

### ⚠️ QUESTIONNAIRE - ACTION REQUIRED

> **🛑 STOP: Complete this questionnaire before proceeding to Architecture.**

#### Q1: [Question Title]
**Question:** [Detailed question text]
**Options:** A) [Option A] B) [Option B] C) [Option C]
**Your Answer:** `_______________`
**Status:** ⬚ Unanswered

---

*Add more questions as needed using same format*

### Questionnaire Status
| Total | Answered | Ready to Proceed? |
|-------|----------|-------------------|
| [X] | [0] | ❌ No |

### Project-Level Requirements
| ID | Requirement | Priority | Status |
|----|-------------|----------|--------|
| PR-001 | [Requirement] | HIGH | ⬚ |

### Related Kiro Specs
| Spec | Path | Phase | Description |
|------|------|-------|-------------|
| [Feature] | `.kiro/specs/[name]/` | 🔵/🟢/🟡 | [Brief description] |

---

## 3. Architecture

### Approval Gate
> ⚠️ **APPROVAL REQUIRED** before Building phase.
> Status: ⬚ Pending | ✅ Approved | 🔄 Changes Requested

### System Overview
[High-level description or diagram]

### Key Decisions

#### Decision: [Title]
- **Timestamp**: [ISO]
- **Context**: [Why needed]
- **Options**: 1) [A] 2) [B]
- **Choice**: [Selected]
- **Rationale**: [Why]
- **Approval**: ⬚ Pending

### Technology Stack
| Layer | Technology | Rationale |
|-------|------------|-----------|
| [Layer] | [Tech] | [Why] |

---

## 4. Implementation

### Phase Gate: Planning → Building
> - [ ] Intent complete
> - [ ] Questionnaire answered (all ✅)
> - [ ] Architecture approved

### Execution Plan
| Stage | Name | Goal | Status |
|-------|------|------|--------|
| 1 | [Stage] | [Goal] | ⬚ |

### Component Map
| Component | Location | Description |
|-----------|----------|-------------|
| [Component] | `src/path/` | [Description] |

### Technical Debt Register
| ID | Description | Trigger | Severity |
|----|-------------|---------|----------|
| TD-001 | [Debt] | [When to address] | ⚠️ Medium |

---

## 5. Metrics

### Phase Gate: Building → Operating
> - [ ] All stages complete
> - [ ] Tests passing

### Business Metrics
| Metric | Target | Current | Status |
|--------|--------|---------|--------|
| [Metric] | [Target] | - | ⬚ |

### Technical Metrics
| Metric | Target | Current | Status |
|--------|--------|---------|--------|
| Latency (p99) | [Target] | - | ⬚ |
| Error rate | [Target] | - | ⬚ |

---

## 6. Decision Log

| Timestamp | Decision | Phase | Context | Outcome |
|-----------|----------|-------|---------|---------|
| [ISO] | Created Living Spec | 🔵 | [Why] | - |

---

## 7. Next Actions

### Current Focus
- [ ] **HIGH**: [Priority task]

### Backlog
- [ ] [Future task]

### Blocked
[None]

### Completed
[None]
```
