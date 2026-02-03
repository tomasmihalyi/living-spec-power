# Multi-Agent Analysis

## Overview

For brownfield projects and complex analysis tasks, use Kiro's `invokeSubAgent` to spawn parallel analysis agents. This dramatically speeds up codebase understanding and ensures comprehensive coverage.

## When to Use Multi-Agent Analysis

- **Brownfield reverse engineering** - Understanding existing codebases
- **Risk assessment** - Security, performance, and debt analysis
- **Feature impact analysis** - Understanding cross-cutting concerns
- **Architecture review** - Validating design patterns

## Agent Definitions

### 1. Requirements Analyst

**Purpose:** Extract functional and non-functional requirements from existing code

**Prompt Template:**
```
Analyze this codebase to extract existing requirements. Focus on:

1. FUNCTIONAL REQUIREMENTS - What does the system do?
   - User-facing features
   - Business logic rules
   - Data transformations
   - Integration points

2. NON-FUNCTIONAL REQUIREMENTS - How well does it do it?
   - Performance characteristics (response times, throughput)
   - Security measures in place
   - Scalability patterns
   - Reliability mechanisms

Format findings as EARS requirements:
- Ubiquitous: THE system SHALL [behavior]
- Event-Driven: WHEN [trigger] THE system SHALL [response]
- State-Driven: WHILE [state] THE system SHALL [behavior]
- Unwanted: IF [condition] THEN THE system SHALL [response]

Return a structured list of requirements with IDs (FR-001, NFR-001).
```

### 2. Architecture Reviewer

**Purpose:** Analyze design patterns, structure, and architectural decisions

**Prompt Template:**
```
Analyze this codebase architecture. Identify:

1. ARCHITECTURE PATTERN
   - Overall pattern (MVC, microservices, monolith, hexagonal, etc.)
   - Layer separation (presentation, business, data)
   - Module boundaries

2. TECH STACK
   - Languages and versions
   - Frameworks and libraries
   - Databases and storage
   - External services

3. KEY COMPONENTS
   - Entry points (main files, API routes, handlers)
   - Core modules and their responsibilities
   - Shared utilities and helpers

4. DESIGN DECISIONS
   - Patterns used (repository, factory, observer, etc.)
   - State management approach
   - Error handling strategy
   - Configuration management

Return findings as a structured architecture summary suitable for §3 of a Living Spec.
```

### 3. Risk Assessor

**Purpose:** Identify security vulnerabilities, performance issues, and technical debt

**Prompt Template:**
```
Analyze this codebase for risks. Identify:

1. SECURITY RISKS
   - Authentication/authorization gaps
   - Input validation issues
   - Sensitive data handling
   - Dependency vulnerabilities

2. PERFORMANCE RISKS
   - N+1 queries or inefficient data access
   - Missing caching opportunities
   - Blocking operations
   - Memory leaks or resource issues

3. TECHNICAL DEBT
   - Code smells (long methods, god classes, etc.)
   - TODO/FIXME comments
   - Outdated dependencies
   - Missing tests
   - Inconsistent patterns

4. OPERATIONAL RISKS
   - Missing logging/monitoring
   - No health checks
   - Deployment concerns
   - Configuration issues

Rate each risk: 🔴 Critical, 🟠 High, 🟡 Medium, 🟢 Low

Return findings as a structured risk register suitable for §4 Tech Debt Register.
```

## Parallel Execution Pattern

When analyzing a brownfield codebase, spawn all three agents simultaneously:

```
📊 Starting Multi-Agent Brownfield Analysis

Spawning 3 parallel analysis agents:
├── 🔍 Requirements Analyst - Extracting FR/NFR
├── 🏗️ Architecture Reviewer - Analyzing patterns
└── ⚠️ Risk Assessor - Identifying risks

Please wait while agents analyze the codebase...
```

### Implementation

Use `invokeSubAgent` with `context-gatherer` first to identify relevant files, then spawn analysis agents:

**Step 1: Context Gathering**
```
invokeSubAgent(
  name: "context-gatherer",
  prompt: "Identify all relevant source files, configuration files, and documentation for comprehensive codebase analysis. Focus on entry points, core business logic, and infrastructure code."
)
```

**Step 2: Parallel Analysis**
After context is gathered, spawn analysis tasks. Each agent receives the gathered context and performs specialized analysis.

## Aggregating Results

After all agents complete, aggregate findings into the Living Spec:

| Agent | Populates Section |
|-------|-------------------|
| Requirements Analyst | §2 Requirements (Project-Level Requirements) |
| Architecture Reviewer | §1 Project Context, §3 Architecture |
| Risk Assessor | §4 Technical Debt Register |

### Aggregation Template

```
📊 Multi-Agent Analysis Complete

## Requirements Analyst Findings
[X] Functional Requirements extracted
[Y] Non-Functional Requirements identified

## Architecture Reviewer Findings
- Pattern: [detected pattern]
- Tech Stack: [languages, frameworks]
- Components: [count] identified

## Risk Assessor Findings
- 🔴 Critical: [count]
- 🟠 High: [count]
- 🟡 Medium: [count]
- 🟢 Low: [count]

Review the auto-populated Living Spec and correct any inaccuracies.
```

## Domain Specialist Agents

During the Building phase, spawn domain specialists based on the work being done:

| Work Type | Specialist | Triggers |
|-----------|------------|----------|
| Database changes | Database Specialist | schema, migration, SQL, query |
| API development | API Specialist | endpoint, REST, GraphQL, contract |
| Frontend work | Frontend Specialist | component, React, Vue, UI, UX |
| Security features | Security Specialist | auth, validation, encryption |
| Test creation | Test Specialist | test, coverage, QA |

See individual specialist steering files in `steering/specialists/` for detailed prompts.

## Best Practices

1. **Always use context-gatherer first** - Don't analyze blindly
2. **Run agents in parallel** - Saves time, comprehensive coverage
3. **Validate findings with user** - Agents may miss context
4. **Update spec immediately** - Don't let findings go stale
5. **Track agent confidence** - Flag uncertain findings for review
