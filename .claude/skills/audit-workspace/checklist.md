# Workspace Audit Checklist

## Phase 1: File Organization

- [ ] `cmd/` contains application binaries
- [ ] `cmd/app/` for public API
- [ ] `cmd/admin/` for admin API
- [ ] Root module files present (`go.mod`, `go.sum`)
- [ ] No stray files in root

## Phase 2: Module Structure

- [ ] `go.mod` has appropriate module path
- [ ] Go version specified
- [ ] Dependencies pinned appropriately
- [ ] No replace directives in production (unless intentional)
- [ ] `go.sum` committed

## Phase 3: Shared Layers

- [ ] `models/` contains domain models
- [ ] `stores/` contains data access
- [ ] `migrations/` contains database migrations
- [ ] `events/` contains domain events
- [ ] `config/` contains configuration types

## Phase 4: Surface Layers

- [ ] `api/` surface structure complete
- [ ] `admin/` surface structure complete
- [ ] Each surface has contracts/, wire/, handlers/, transformers/
- [ ] No cross-surface imports
- [ ] Registration files present per surface

## Phase 5: Test Infrastructure

- [ ] `testing/` directory exists
- [ ] `testing/fixtures.go` present
- [ ] `testing/mocks.go` present
- [ ] `testing/integration/` for integration tests
- [ ] `testing/benchmarks/` for benchmarks (if applicable)

## Phase 6: Configuration

- [ ] Config files have appropriate extensions
- [ ] Environment-specific configs supported
- [ ] Secrets not committed
- [ ] `.env.example` present (if using env files)
- [ ] Config documentation exists

## Phase 7: Build Artifacts

- [ ] `.gitignore` ignores build artifacts
- [ ] Binary output directories ignored
- [ ] IDE files handled appropriately
- [ ] No generated files committed (unless intentional)
- [ ] Clean build possible from fresh clone

## Phase 8: Documentation

- [ ] `README.md` at root
- [ ] `docs/` directory for detailed docs
- [ ] `CHANGELOG.md` present (if versioned)
- [ ] `LICENSE` present (if open source)
- [ ] Contributing guide present (if accepting contributions)

## Phase 9: CI/CD

- [ ] CI configuration present (`.github/workflows/` or similar)
- [ ] Build workflow defined
- [ ] Test workflow defined
- [ ] Lint workflow defined
- [ ] Deploy workflow defined (if applicable)

## Phase 10: Development Environment

- [ ] Makefile or task runner present
- [ ] Common tasks documented
- [ ] Local development setup documented
- [ ] Database setup documented
- [ ] Required tools listed
