# Mission Audit

Evaluate whether the application's implementation aligns with its stated mission and identify drift.

## Principles

1. **Mission defines purpose** — Everything in the application MUST serve the mission
2. **Scope is bounded** — Non-goals are as important as goals
3. **Success is measurable** — The mission's success criteria MUST be met by the implementation
4. **Drift is caught early** — Feature creep and scope drift are identified before they compound

## Execution

1. Read `checklist.md` in this skill directory
2. Read MISSION.md for the application's stated purpose
3. Read PHILOSOPHY.md for zoobzio-wide principles
4. Work through each phase systematically
5. Compile findings into structured report

## Specifications

### MISSION.md Structure

A well-formed MISSION.md contains:

| Section | Purpose |
|---------|---------
| Purpose | What the application does — one clear statement |
| The Stack | What packages and dependencies it uses |
| API Surfaces | What consumers it serves |
| Project Structure | How the codebase is organized |
| Conventions | Patterns and standards in use |

### Alignment Assessment

For each endpoint, handler, and capability:
- Does it serve the stated purpose?
- Is it covered by the project structure?
- Does it follow the stated conventions?

### Drift Categories

**Mission-aligned** — Directly serves the stated purpose.

**Mission-adjacent** — Related to the purpose but not explicitly covered. May indicate the mission needs updating or the feature needs removing.

**Mission-contradictory** — Directly contradicts a non-goal or explicit exclusion. This is a defect.

**Mission-orphaned** — Neither serves nor contradicts the mission. Dead weight.

### Success Criteria Verification

Each documented capability MUST be:
- Actually achievable with the current implementation
- Testable by following the described patterns
- Not blocked by missing functionality

### Philosophy Alignment

The application MUST align with PHILOSOPHY.md:
- Dependency policy (minimal production deps, isolated providers)
- Type safety (generics over interface{})
- Boundaries (explicit data transformation)
- Composition (interfaces, processors, connectors)
- Errors (semantic, contextual)
- Context (all I/O accepts context.Context)

## Output

### Report Structure

```markdown
## Summary
[One paragraph: overall mission alignment and primary recommendation]

## Mission Statement
[Reproduce the application's stated purpose from MISSION.md]

## Alignment Matrix

| Category | Status | Primary Issue |
|----------|--------|---------------|
| Purpose Clarity | [✓/~/✗] | |
| Stack Accuracy | [✓/~/✗] | |
| API Surfaces | [✓/~/✗] | |
| Project Structure | [✓/~/✗] | |
| Conventions | [✓/~/✗] | |
| Philosophy Alignment | [✓/~/✗] | |

## Feature Alignment

| Feature/Capability | Classification | Notes |
|--------------------|---------------|-------|
| [feature] | [aligned/adjacent/contradictory/orphaned] | |

## Capability Verification

| Capability | Achievable | Blocked By |
|-----------|-----------|------------|
| [capability] | [✓/✗] | [blocker if any] |

## Mission Drift
[Features or capabilities that have drifted from the stated mission]

## Mission Gaps
[Stated mission items that the implementation doesn't fulfill]

## MISSION.md Quality
[Assessment of the mission document itself — is it clear, complete, current?]

## Recommendations
[Prioritized list: fix the implementation, update the mission, or both]
```

Status legend: ✓ Compliant, ~ Partial, ✗ Missing/Non-compliant
