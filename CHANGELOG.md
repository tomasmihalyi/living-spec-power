# Changelog

All notable changes to the Living Specs Power are documented here.

## [2.0.0] - 2026-02-05

### Added

#### Multi-Agent Architecture
- **parallel-analysis.md** - Dedicated workflow for spawning parallel analysis agents
- **multi-agent.md** - Agent definitions and prompt templates for:
  - Architecture Analyzer
  - Dependency Analyzer  
  - Quality Analyzer
- Support for `invokeSubAgent` with `context-gatherer` and `general-task-execution`

#### Comprehension Gates
- **comprehension-gates.md** - Blocking verification at phase transitions
- Three gate types:
  - Planning → Building gate
  - Building → Operating gate
  - Architecture change gate
- Comprehension tracking in spec template
- Skip logging and warnings

#### Tiered Approvals
- **tiered-approvals.md** - Risk-based approval system
- Tier 1: Autonomous (timestamps, status icons)
- Tier 2: Async notification (component map, tech debt)
- Tier 3: Synchronous approval (requirements, architecture)

#### Domain Specialists
- **specialists/database.md** - Schema, migrations, queries
- **specialists/api.md** - REST, GraphQL, contracts
- **specialists/frontend.md** - Components, accessibility, UX
- **specialists/security.md** - Auth, validation, threats
- **specialists/testing.md** - Coverage, test types, quality
- File pattern triggers for automatic activation

#### Spec Critic
- **spec-critic.md** - Automated gap analysis
- Three scoring dimensions:
  - Completeness (section coverage)
  - Consistency (trace integrity)
  - Quality (specificity, measurability)
- Health thresholds with blocking at critical levels
- Integration with phase gates

#### Enhanced Drift Detection
- Git-aware drift scoring
- Soft block at 51-75% drift
- Hard block at 76%+ drift
- Detailed drift reports

#### Hooks
- **hooks/drift-monitor.json** - Auto-check drift on file edits
- **hooks/phase-gate-reminder.json** - Remind about gates after work
- **hooks/spec-sync-prompt.json** - Prompt for spec updates

#### Views
- **views/developer.md** - Developer-focused spec view
- **views/manager.md** - Manager/PM status view
- **views/qa.md** - QA/testing view
- **views/architect.md** - Architecture decision view

#### Compliance & Integrations
- **compliance/controls.md** - SOC 2, HIPAA, GDPR mappings
- **integrations/test-tools.md** - TestRail, Jira Test integration
- **integrations/incident-tools.md** - PagerDuty, OpsGenie integration

### Changed

- Updated **POWER.md** with v2.0 feature table
- Enhanced **workflow.md** with multi-agent and spec critic integration
- Updated **template.md** with comprehension tracking section
- Enhanced **drift-detection.md** with blocking thresholds

### Migration from v1.x

No breaking changes. All new features are additive:

1. Existing steering files continue to work
2. New features activate via triggers
3. Hooks are optional - install only if desired
4. Existing Living Specs are compatible

## [1.0.0] - Initial Release

- Core Living Spec workflow
- AI-DLC phase alignment
- Three approaches (A/B/C)
- Basic drift detection
- Traceability management
- Multi-repo support
