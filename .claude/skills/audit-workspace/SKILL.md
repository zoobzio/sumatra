# Workspace Audit

Evaluate existing application workspace structure for proper organization and build configuration.

## Principles

1. **Clear binary separation** — Each API surface MUST have its own binary
2. **Shared code is explicit** — Common packages MUST be clearly organized
3. **Build configuration is consistent** — All binaries follow the same patterns
4. **Local development is seamless** — Development workflow is documented

## Execution

1. Read `checklist.md` in this skill directory
2. Work through each phase systematically
3. Compile findings into structured report

## Specifications

### Required Directory Structure

```
cmd/
├── app/           # Public API binary
│   └── main.go
└── admin/         # Admin API binary
    └── main.go

# Shared layers
config/            # Configuration types
models/            # Domain models
stores/            # Data access (shared)
events/            # Domain events
migrations/        # Database migrations
internal/          # Internal packages
testing/           # Test infrastructure

# Surface-specific layers
api/
├── contracts/
├── wire/
├── handlers/
└── transformers/

admin/
├── contracts/
├── wire/
├── handlers/
└── transformers/
```

### Required Files

- `go.mod` — Module definition
- `Makefile` or `justfile` — Build commands
- `.env.example` — Environment template
- `docker-compose.yml` — Local development services

### Go Module Requirements

- Module path: `github.com/zoobzio/[app]`
- Go version: 1.24+
- Toolchain directive present

### Build Configuration

Each binary MUST:
- Have its own `main.go` in `cmd/[name]/`
- Be buildable independently
- Have documented build flags

### Layer Organization

| Layer | Purpose | Shared? |
|-------|---------|---------|
| models/ | Domain entities | Yes |
| stores/ | Data access | Yes |
| migrations/ | Schema changes | Yes |
| config/ | Configuration | Yes |
| events/ | Domain events | Yes |
| {surface}/contracts/ | Interfaces | No |
| {surface}/wire/ | Request/response | No |
| {surface}/handlers/ | HTTP handlers | No |
| {surface}/transformers/ | Mapping | No |

## Output

### Report Structure

```markdown
## Summary
[One paragraph: overall workspace health and primary recommendation]

## Coverage Matrix

| Category | Status | Primary Issue |
|----------|--------|---------------|
| Directory Structure | [✓/~/✗] | |
| Binary Organization | [✓/~/✗] | |
| Go Module | [✓/~/✗] | |
| Build Configuration | [✓/~/✗] | |
| Layer Separation | [✓/~/✗] | |
| Development Setup | [✓/~/✗] | |

## Binary Analysis
[Assessment of cmd/ organization]

## Layer Analysis
[Assessment of shared vs surface-specific code]

## Missing Files
[Required files that don't exist]

## Structural Issues
[Problems with organization]

## Quick Wins
[Low-effort fixes]
```

Status legend: ✓ Compliant, ~ Partial, ✗ Missing/Non-compliant
