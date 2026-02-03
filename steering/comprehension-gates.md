# Comprehension Gates

## Why Comprehension Gates?

Research shows AI assistance can reduce skill mastery by 17% when developers rubber-stamp without understanding. Comprehension gates ensure developers maintain deep understanding of their systems.

> **Goal:** Prevent "skill atrophy" - the gradual loss of system understanding when AI handles too much.

## When Gates Activate

| Transition | Gate Required |
|------------|---------------|
| Planning → Building | ✅ Yes |
| Building → Operating | ✅ Yes |
| Major architecture change | ✅ Yes |
| New team member onboarding | ✅ Yes |
| After extended absence (>2 weeks) | ✅ Yes |

## Gate Protocol

### Step 1: Present Questions

Before allowing phase transition, present 3-5 comprehension questions:

```
📋 COMPREHENSION GATE

Before proceeding, please answer these questions in your own words.
This ensures you understand the system deeply, not just the AI's summary.

[Questions based on phase]

Type your answers below, or say "skip" to bypass (not recommended).
```

### Step 2: Evaluate Responses

- **Detailed, accurate answers** → Proceed
- **Vague or incorrect answers** → Offer clarification, re-ask
- **Skip requested** → Log skip in Decision Log, proceed with warning

### Step 3: Log Outcome

Add to §6 Decision Log:
```
| [ISO timestamp] | Comprehension Gate: [Phase] | [Phase] | [Passed/Skipped] | [Notes] |
```

## Phase-Specific Questions

### Planning → Building Gate

```
📋 COMPREHENSION CHECK: Planning → Building

1. PROBLEM UNDERSTANDING
   In your own words, what problem does this project solve and for whom?

2. ARCHITECTURAL RATIONALE
   What's the main architectural decision we made and why did we choose it over alternatives?

3. FAILURE AWARENESS
   What conditions would make this project fail? What are we watching for?

4. SCOPE CLARITY
   What's explicitly OUT of scope and why?

5. SUCCESS DEFINITION
   How will we know this project succeeded? What metrics matter?
```

### Building → Operating Gate

```
📋 COMPREHENSION CHECK: Building → Operating

1. COMPONENT UNDERSTANDING
   What are the 3-5 key components and how do they interact?

2. DATA FLOW
   Trace a typical user request through the system. What happens at each step?

3. TECHNICAL DEBT AWARENESS
   What technical debt did we defer and why? When should we address it?

4. FAILURE MODES
   What are the most likely failure modes? How do we detect and recover?

5. OPERATIONAL READINESS
   What metrics will tell us if this is working in production?
```

### Architecture Change Gate

```
📋 COMPREHENSION CHECK: Architecture Change

1. CHANGE RATIONALE
   Why is this change necessary? What problem does it solve?

2. IMPACT ANALYSIS
   What components are affected? What might break?

3. ROLLBACK PLAN
   If this change fails, how do we roll back?

4. MIGRATION PATH
   How do we get from current state to new state safely?
```

## Handling Skips

If user requests to skip comprehension gate:

```
⚠️ SKIP REQUESTED

Skipping comprehension gates is not recommended. Benefits of completing:
- Ensures you can debug issues without AI assistance
- Builds mental model for future decisions
- Catches misunderstandings early

Are you sure you want to skip? (yes/no)
```

If confirmed:
1. Log skip in Decision Log with timestamp
2. Add warning to Current Status: "⚠️ Comprehension gate skipped at [phase] transition"
3. Proceed with transition

## Comprehension Score (Optional)

Track comprehension over time:

```
## Comprehension Tracking

| Date | Gate | Score | Notes |
|------|------|-------|-------|
| [ISO] | Planning→Building | 5/5 | Strong understanding |
| [ISO] | Building→Operating | 3/5 | Needed clarification on data flow |
```

Score: Count of questions answered satisfactorily / Total questions

## Anti-Patterns

- ❌ Accepting one-word answers
- ❌ Allowing copy-paste from spec
- ❌ Skipping gates for "urgent" work
- ❌ Not logging skipped gates
- ❌ Asking yes/no questions instead of open-ended
