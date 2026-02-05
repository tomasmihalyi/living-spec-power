---
inclusion: auto
triggers: ["analyze codebase", "brownfield analysis", "parallel analysis", "reverse engineer", "understand codebase"]
---

# Parallel Analysis Workflow

## Overview

For brownfield projects, spawn multiple analysis agents simultaneously using Kiro's `invokeSubAgent`. This provides comprehensive codebase understanding in a fraction of the time.

## When to Use

- Starting work on an unfamiliar codebase
- Onboarding to a new project
- Before major refactoring
- Creating Living Spec for existing project
- Investigating cross-cutting concerns

## Agent Configuration

### Agent 1: Architecture Analyzer

**Sub-agent:** `context-gatherer` then `general-task-execution`

**Focus Areas:**
- Folder structure and organization
- Design patterns (MVC, hexagonal, microservices)
- Layer separation
- Module boundaries
- Entry points

**Prompt:**
```
Analyze the codebase architecture. Identify:
1. Overall architecture pattern
2. Layer structure (presentation, business, data)
3. Key modules and their responsibilities
4. Entry points (main files, API routes, handlers)
5. Configuration management approach

Return findings as structured data for Living Spec §1 Project Context and §3 Architecture.
```

### Agent 2: Dependency Analyzer

**Sub-agent:** `general-task-execution`

**Focus Areas:**
- Package dependencies
- Framework versions
- External service integrations
- Database connections
- API clients

**Prompt:**
```
Analyze project dependencies. Identify:
1. Languages and runtime versions
2. Framework and library dependencies
3. Database and storage technologies
4. External service integrations
5. Development vs production dependencies
6. Outdated or vulnerable packages

Return findings as structured data for Living Spec §1 Tech Stack.
```

### Agent 3: Quality Analyzer

**Sub-agent:** `general-task-execution`

**Focus Areas:**
- Test coverage
- Code quality issues
- Technical debt markers
- Documentation state
- Security concerns

**Prompt:**
```
Analyze codebase quality. Identify:
1. Test coverage and test types present
2. TODO/FIXME/HACK comments
3. Code smells (long files, complex functions)
4. Missing documentation
5. Security concerns (hardcoded secrets, SQL injection risks)
6. Accessibility issues (if frontend)

Return findings as structured data for Living Spec §4 Technical Debt Register.
```

## Execution Flow

### Step 1: Announce Analysis

```
📊 Starting Parallel Codebase Analysis

Spawning 3 analysis agents:
├── 🏗️ Architecture Analyzer - Structure and patterns
├── 📦 Dependency Analyzer - Tech stack and integrations  
└── 🔍 Quality Analyzer - Tests, debt, and concerns

Estimated time: 2-5 minutes depending on codebase size.
```

### Step 2: Spawn Agents

Use `invokeSubAgent` for each analyzer. All three run concurrently.

```javascript
// Conceptual - actual implementation via Kiro's invokeSubAgent tool

// Agent 1: Architecture
invokeSubAgent({
  name: "context-gatherer",
  prompt: "Identify key architectural files: entry points, config, core modules"
})

// Then spawn analysis agents in parallel
invokeSubAgent({
  name: "general-task-execution", 
  prompt: "[Architecture analysis prompt]"
})

invokeSubAgent({
  name: "general-task-execution",
  prompt: "[Dependency analysis prompt]"
})

invokeSubAgent({
  name: "general-task-execution",
  prompt: "[Quality analysis prompt]"
})
```

### Step 3: Aggregate Results

Once all agents complete, merge findings:

```
📊 Parallel Analysis Complete

## Architecture Findings
- Pattern: [detected]
- Layers: [identified]
- Entry Points: [count] found
- Modules: [count] identified

## Dependency Findings  
- Languages: [list]
- Frameworks: [list]
- Databases: [list]
- External Services: [count]

## Quality Findings
- Test Coverage: [estimate]%
- Tech Debt Items: [count]
- Security Concerns: [count]
- Documentation: [status]

Populating Living Spec sections...
```

### Step 4: Populate Living Spec

Map findings to spec sections:

| Agent | Populates |
|-------|-----------|
| Architecture | §1 Project Context, §3 Architecture |
| Dependency | §1 Tech Stack, §4 Component Map |
| Quality | §4 Technical Debt Register, §5 Metrics baseline |

### Step 5: User Validation

```
📋 Review Auto-Populated Sections

The following sections were populated from analysis:

§1 Project Context
- Architecture: [pattern]
- Tech Stack: [summary]

§3 Architecture  
- [key decisions identified]

§4 Technical Debt
- [count] items identified

Please review and correct any inaccuracies.
Approve? (yes/modify/reject)
```

## Handling Large Codebases

For codebases > 10,000 files:

1. **Scope first**: Use context-gatherer to identify core directories
2. **Prioritize**: Focus on src/, lib/, app/ directories
3. **Exclude**: Skip node_modules/, vendor/, build/
4. **Sample**: For very large codebases, analyze representative samples

```
⚠️ Large Codebase Detected ([X] files)

Recommend scoped analysis:
- Core source: src/, lib/, app/
- Config: root config files
- Tests: sample of test files

Proceed with scoped analysis? (yes/full/custom)
```

## Error Handling

If an agent fails:

```
⚠️ Agent [name] encountered an issue

Error: [description]

Options:
A) Retry this agent
B) Continue without this analysis
C) Run manual analysis for this area
```

## Performance Tips

1. **Use context-gatherer first** - Identifies relevant files, reduces noise
2. **Set reasonable timeouts** - 5 minutes per agent max
3. **Cache results** - Store in spec for future reference
4. **Incremental updates** - Don't re-analyze unchanged areas

## Integration with Living Spec Workflow

This analysis runs automatically when:
- User selects "Brownfield" project type
- User says "analyze this codebase"
- Creating Living Spec for existing project

Results feed directly into the Living Spec template, reducing manual documentation effort by 60-80%.
