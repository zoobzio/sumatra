# Implementation Audit Checklist

## Phase 1: Linter Compliance

- [ ] `go vet ./...` passes
- [ ] `golangci-lint run` passes (if configured)
- [ ] No ignored linter directives without justification
- [ ] Import grouping follows convention (stdlib, external, internal)
- [ ] No unused code

## Phase 2: Naming Conventions

- [ ] Models are singular (`User`, not `Users`)
- [ ] Stores are plural (`Users`, not `User`)
- [ ] Contracts match store naming
- [ ] Handlers use Verb+Singular (`GetUser`, `CreateUser`)
- [ ] Wire types have appropriate suffixes (`UserResponse`, `CreateUserRequest`)

## Phase 3: Godoc Standards

- [ ] Package-level doc comments present
- [ ] Exported types documented
- [ ] Exported functions documented
- [ ] Examples provided for complex functions
- [ ] No placeholder comments

## Phase 4: Error Handling

- [ ] Errors wrapped with context
- [ ] Custom errors in `{surface}/handlers/errors.go`
- [ ] Error types implement appropriate interfaces
- [ ] No swallowed errors
- [ ] Error messages are actionable

## Phase 5: Context Usage

- [ ] Context passed through call chain
- [ ] Context cancellation respected
- [ ] No context.Background() in handlers
- [ ] Timeouts set appropriately
- [ ] Context values used sparingly

## Phase 6: Pattern Compliance

- [ ] Handlers follow rocco patterns
- [ ] Stores follow grub patterns
- [ ] Config uses flux capacitors where hot-reload needed
- [ ] Events use capitan signals
- [ ] Boundaries use cereal appropriately

## Phase 7: Registration

- [ ] Stores registered in `stores/stores.go`
- [ ] Handlers registered in `{surface}/handlers/handlers.go`
- [ ] Errors registered in `{surface}/handlers/errors.go`
- [ ] Boundaries registered appropriately
- [ ] No orphaned implementations

## Phase 8: Dependencies

- [ ] No circular dependencies
- [ ] Minimal external dependencies
- [ ] Dependencies pinned appropriately
- [ ] No deprecated dependencies
- [ ] Security vulnerabilities addressed
