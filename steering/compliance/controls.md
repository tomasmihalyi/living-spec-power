---
inclusion: auto
triggers: ["SOC 2", "HIPAA", "GDPR", "compliance", "audit", "controls", "regulatory"]
---

# Controls-Based Compliance

## Philosophy

Templates document. Controls prove. Map Living Spec sections to control evidence.

## Control Mapping

| Control | Living Spec Evidence | Verification |
|---------|---------------------|--------------|
| CC6.1 Access Control | §3 Architecture (auth design) | Design review approved ✅ |
| CC7.2 Change Management | §6 Decision Log | All changes timestamped |
| CC8.1 Risk Assessment | §1 Failure Triggers | Risks documented |
| CC3.1 Requirements | §2 Requirements | Questionnaire complete |

## Evidence Chain

```
Requirement (§2) → Design (§3) → Task (§4) → Test (Matrix) → Deploy (§6 Log)
     ↓                ↓              ↓            ↓              ↓
  Approved        Approved       Completed    Passed      Logged + SHA
```

## Git as Audit Trail

Every Living Spec change is a git commit. For high-compliance:

| Requirement | Git Feature |
|-------------|-------------|
| Immutable history | Git commit log |
| Change attribution | Commit author |
| Timestamps | Commit timestamps |
| Tamper evidence | Signed commits (`git commit -S`) |
| Review proof | PR approvals |

## High-Compliance Setup

```bash
# Require signed commits
git config commit.gpgsign true

# Branch protection on specs
# In GitHub: Settings → Branches → Add rule for `.kiro/specs/*`
# - Require PR reviews
# - Require signed commits
```

## Audit Export

Generate from Living Spec + git:
- Decision Log entries with commit SHAs
- Phase transitions with approver
- Requirement changes with git diff links
- Architecture decisions with rationale
