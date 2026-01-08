# Living Spec Template

Copy this template when creating a new Living Spec.

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

### Hypothesis (optional - for validation-stage projects)
| Element | Description |
|---------|-------------|
| Problem | [Core problem being addressed] |
| Solution | [Proposed solution approach] |
| Customer | [Target user/customer] |
| Value Prop | [Why this solution wins] |

### Success Criteria
| Criteria | Target | Current | Status |
|----------|--------|---------|--------|
| 🎯 Primary | [Main success metric] | - | ⬚ |
| 📈 Secondary | [Supporting metric] | - | ⬚ |

### Failure Triggers
- [ ] [Condition that means we should pivot or stop]

### Scope
**In Scope:**
- [What's included]

**Out of Scope:**
- [What's explicitly excluded]

---

## 2. Requirements

---
### ⚠️ QUESTIONNAIRE - ACTION REQUIRED ⚠️

> **🛑 STOP: You must complete this questionnaire before proceeding to Architecture.**
> 
> Kiro will generate questions based on your project. Review each question carefully and provide your answer in the designated space. This is a **blocking requirement** for phase progression.

---

#### Q1: [Question Title]
**Question:** [Detailed question text]

**Options:**
- A) [Option A description]
- B) [Option B description]  
- C) [Option C description]

**Your Answer:** `_______________`

**Status:** ⬚ Unanswered

---

#### Q2: [Question Title]
**Question:** [Detailed question text]

**Options:**
- A) [Option A description]
- B) [Option B description]
- C) [Option C description]

**Your Answer:** `_______________`

**Status:** ⬚ Unanswered

---

#### Q3: [Question Title]
**Question:** [Detailed question text]

**Options:**
- A) [Option A description]
- B) [Option B description]
- C) [Option C description]

**Your Answer:** `_______________`

**Status:** ⬚ Unanswered

---

### Questionnaire Completion Status

| Total Questions | Answered | Remaining | Ready to Proceed? |
|-----------------|----------|-----------|-------------------|
| [X] | [0] | [X] | ❌ No |

> **Next Step:** Once all questions are answered, update status markers to ✅ and change "Ready to Proceed?" to "✅ Yes"

---

### Project-Level Requirements
| ID | Requirement | Priority | Status | Spec Reference |
|----|-------------|----------|--------|----------------|
| PR-001 | [Cross-cutting requirement] | HIGH | ⬚ | - |

### Related Kiro Specs
| Spec | Path | Phase | Status | Description |
|------|------|-------|--------|-------------|
| [Feature] | `.kiro/specs/[name]/` | 🔵/🟢/🟡 | ⬚ | [Brief description] |

*Phase: 🔵 Planning, 🟢 Building, 🟡 Operating*

---

## 3. Architecture

### Approval Gate
> ⚠️ **APPROVAL REQUIRED**: Review architecture decisions before proceeding to Building phase.
> 
> Status: ⬚ Pending | ✅ Approved | 🔄 Changes Requested

### System Overview
[High-level description or diagram]

### Key Decisions

#### Decision: [First Major Decision]
- **Timestamp**: [ISO timestamp]
- **Phase**: 🔵 Planning
- **Context**: [Why this decision is needed]
- **Options Considered**:
  1. [Option A] - [pros/cons]
  2. [Option B] - [pros/cons]
- **Choice**: [Selected option]
- **Rationale**: [Why this choice]
- **Trade-offs**: [What we're accepting]
- **Cost Impact**: [Estimated cost implications]
- **Approval**: ⬚ Pending | ✅ Approved

### Technology Stack
| Layer | Technology | Rationale | Est. Cost |
|-------|------------|-----------|-----------|
| [Layer] | [Tech] | [Why] | [Monthly] |

---

## 4. Implementation

### Phase Gate: Planning → Building
> ⚠️ **PHASE TRANSITION**: Confirm all Planning sections are complete.
> 
> - [ ] Intent section complete
> - [ ] **Requirements Questionnaire fully answered** (all questions show ✅)
> - [ ] Architecture decisions approved
> - [ ] Ready to proceed to Building phase

### Execution Plan
| Stage | Name | Goal | Duration | Status |
|-------|------|------|----------|--------|
| 1 | [Stage name] | [What it achieves] | [Time] | ⬚ |

### Component Map
| Component | Location | Description | Related Spec |
|-----------|----------|-------------|--------------|
| [Component] | `src/path/` | [Description] | [Spec if any] |

### Technical Debt Register
| ID | Description | Trigger Condition | Severity | Status |
|----|-------------|-------------------|----------|--------|
| TD-001 | [Debt item] | [When to address] | ⚠️ Medium | ⬚ |

---

## 5. Metrics

### Phase Gate: Building → Operating
> ⚠️ **PHASE TRANSITION**: Confirm Building is complete before Operating.
> 
> - [ ] All execution plan stages complete
> - [ ] Tests passing
> - [ ] Ready for deployment

### Business Metrics
| Metric | Target | Current | Status |
|--------|--------|---------|--------|
| [Metric] | [Target] | - | ⬚ |

### Technical Metrics
| Metric | Target | Current | Status |
|--------|--------|---------|--------|
| Latency (p99) | [Target] | - | ⬚ |
| Error rate | [Target] | - | ⬚ |

### Validation Status
| Assumption | Validated? | Evidence |
|------------|------------|----------|
| [Key assumption] | ⬚ | - |

---

## 6. Decision Log

| Timestamp | Decision | Phase | Context | Approval | Outcome |
|-----------|----------|-------|---------|----------|---------|
| [ISO] | Created Living Spec | 🔵 | [Why now] | ✅ | - |

---

## 7. Next Actions

### Current Focus
- [ ] **HIGH**: [First priority task]

### Backlog
- [ ] [Future task]

### Blocked
[None yet]

### Completed
[None yet]

---

## Audit Trail

### Session History
| Timestamp | Action | User Response | Status |
|-----------|--------|---------------|--------|
| [ISO] | Created Living Spec | - | ✅ |

---

## Appendix

### Glossary
| Term | Definition |
|------|------------|
| [Term] | [Definition] |

### Change History
| Date | Author | Change |
|------|--------|--------|
| [Today] | @[username] | Initial creation |
```
