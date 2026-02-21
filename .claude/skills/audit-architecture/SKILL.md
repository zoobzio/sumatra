# Architecture Audit

Evaluate existing application architecture against zoobzio design principles and provide actionable recommendations.

## Principles

1. **Composition over inheritance** — Interfaces MUST be small, nestable, and composable
2. **Boundaries are explicit** — Data transformations MUST happen at well-defined boundaries
3. **Dependencies are deliberate** — Production dependencies MUST be justified
4. **Type safety is non-negotiable** — Generics over `interface{}`, compile-time over runtime

## Execution

1. Read `checklist.md` in this skill directory
2. Work through each phase systematically
3. Compile findings into structured report

## Specifications

### Layer Architecture

The application follows a layered architecture:

| Layer | Purpose | Location |
|-------|---------|----------|
| Models | Domain entities | `models/` |
| Stores | Data access | `stores/` |
| Contracts | Interface definitions | `{surface}/contracts/` |
| Wire | Request/response types | `{surface}/wire/` |
| Handlers | HTTP endpoints | `{surface}/handlers/` |
| Transformers | Model ↔ wire mapping | `{surface}/transformers/` |

### Interface Design

Interfaces MUST:
- Express one abstraction level per interface
- Be composable — larger interfaces embed smaller ones
- Be implementable by both real and test types
- Accept `context.Context` for I/O operations

Interfaces MUST NOT:
- Be wider than their consumers need
- Contain methods from multiple abstraction levels
- Require concrete type knowledge to implement

### Boundary Design

Each boundary MUST:
- Be identifiable (receiving input, loading, storing, sending output)
- Transform data explicitly via transformers
- Validate at ingress (handlers)
- Mask/redact at egress where appropriate (wire types)

### Dependency Policy

Production dependencies:
- stdlib first
- zoobzio stack packages second (sum, rocco, grub, etc.)
- external packages as last resort with clear justification

### Error Design

- Errors carry context: what failed, where, why
- Semantic errors (`ErrNotFound`, `ErrDuplicate`) are consistent across implementations
- Error wrapping preserves the chain
- Sentinel errors are defined at the package level

### Observability

- Components have identity
- Signals are emittable without requiring external infrastructure
- Correlation is possible across component boundaries

## Output

### Report Structure

```markdown
## Summary
[One paragraph: overall architectural health and primary recommendation]

## Coverage Matrix

| Category | Status | Primary Issue |
|----------|--------|---------------|
| Layer Separation | [✓/~/✗] | |
| Interface Design | [✓/~/✗] | |
| Boundary Design | [✓/~/✗] | |
| Dependency Policy | [✓/~/✗] | |
| Error Design | [✓/~/✗] | |
| Observability | [✓/~/✗] | |
| Type Safety | [✓/~/✗] | |

## Layer Analysis
[Assessment of layer separation and dependencies]

## Interface Analysis
[Assessment of interface design — width, composability, abstraction levels]

## Boundary Analysis
[Assessment of boundary explicitness and data flow through transformers]

## Dependency Analysis
[Assessment of dependency justification and isolation]

## Structural Issues
[Problems with overall application organization]

## Quick Wins
[Low-effort fixes]
```

Status legend: ✓ Compliant, ~ Partial, ✗ Missing/Non-compliant
