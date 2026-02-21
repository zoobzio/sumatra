# README Audit

Evaluate an existing README against quality standards and provide actionable recommendations.

## Principles

1. **Essence over problem** — MUST lead with what makes this application unique
2. **Show, don't frame** — Code MUST speak louder than prose
3. **Voice from nature** — Tone MUST match the application's character
4. **Structure as scaffolding** — Sections MUST provide rhythm without feeling scripted

## Execution

1. Read `checklist.md` in this skill directory
2. Work through each phase systematically
3. Compile findings into structured report

## Specifications

### Required Badges

README MUST include appropriate badges after the title:

| Badge | URL Pattern |
|-------|-------------|
| CI Status | `github.com/.../workflows/CI/badge.svg` |
| Coverage | `codecov.io/gh/.../graph/badge.svg` |
| Go Reference | `pkg.go.dev/badge/...` |
| License | `img.shields.io/github/license/...` |
| Go Version | `img.shields.io/github/go-mod-go-version/...` |

### Required Sections

| # | Section | Requirements |
|---|---------|--------------|
| 1 | Header | Title, badges, tagline |
| 2 | Overview | Application-specific description |
| 3 | Quick Start | How to run locally |
| 4 | Configuration | Environment variables, config files |
| 5 | API Surfaces | Public and Admin API overview |
| 6 | Project Structure | Directory layout explanation |
| 7 | Development | How to contribute |
| 8 | License | Single line |

### Anti-Patterns

MUST flag if present:
- Template voice (sounds like any application)
- Problem-first framing ("The Problem / The Solution")
- Feature laundry lists
- API reference that belongs in docs
- Missing configuration documentation

## Output

### Report Structure

```markdown
## Summary
[One paragraph: overall impression and primary recommendation]

## Badge Assessment

| Badge | Present | Working |
|-------|---------|---------|
| CI Status | [✓/✗] | [✓/✗] |
| Coverage | [✓/✗] | [✓/✗] |
| Go Reference | [✓/✗] | [✓/✗] |
| License | [✓/✗] | [✓/✗] |
| Go Version | [✓/✗] | [✓/✗] |

## Structure Assessment

| Section | Present | Quality |
|---------|---------|---------|
| Header | [✓/✗] | [Strong/Adequate/Weak] |
| Overview | [✓/✗] | [Strong/Adequate/Weak] |
| Quick Start | [✓/✗] | [Strong/Adequate/Weak] |
| Configuration | [✓/✗] | [Strong/Adequate/Weak] |
| API Surfaces | [✓/✗] | [Strong/Adequate/Weak] |
| Project Structure | [✓/✗] | [Strong/Adequate/Weak] |
| Development | [✓/✗] | [Strong/Adequate/Weak] |

## Anti-Patterns Detected
[List any anti-patterns found]

## Strengths
[What the README does well]

## Issues
[Prioritized list with recommendations]
```
