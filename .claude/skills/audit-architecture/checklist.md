# Architecture Audit Checklist

## Phase 1: Surface Contracts

- [ ] Each API surface has its own `contracts/` directory
- [ ] Contracts define behavior, not implementation
- [ ] No store imports in contracts
- [ ] Contract methods accept context as first parameter
- [ ] Contract methods return domain types, not wire types

## Phase 2: Layer Separation

- [ ] Handlers import contracts, not stores
- [ ] Stores satisfy contracts without coupling
- [ ] Wire types separate from models
- [ ] Transformers bridge models ↔ wire
- [ ] No cross-surface imports

## Phase 3: Dependency Flow

- [ ] Dependencies flow inward (handlers → contracts → models)
- [ ] No circular imports
- [ ] Shared layers don't import surface-specific layers
- [ ] Registry provides dependency injection
- [ ] Config flows through registry, not globals

## Phase 4: Boundary Definitions

- [ ] Model boundaries defined in `models/boundary.go`
- [ ] Wire boundaries defined per surface
- [ ] Masking appropriate per surface (api masked, admin unmasked)
- [ ] Encryption/hashing applied at boundaries
- [ ] No sensitive data leaks through boundaries

## Phase 5: Store Patterns

- [ ] Stores use grub abstractions consistently
- [ ] Database stores use sum.Database
- [ ] Bucket stores use grub.Bucket
- [ ] KV stores use grub.Store
- [ ] Index stores use grub.Index

## Phase 6: Handler Patterns

- [ ] Handlers use rocco consistently
- [ ] OpenAPI annotations present
- [ ] Error responses use domain errors
- [ ] Validation uses check package
- [ ] SSE handlers use rocco streaming

## Phase 7: Event Architecture

- [ ] Events defined in `events/`
- [ ] Events use capitan signals
- [ ] Event handlers registered properly
- [ ] No direct coupling between event publishers and handlers
- [ ] Observability signals present

## Phase 8: Configuration

- [ ] Config types in `config/`
- [ ] Hot-reload config uses flux capacitors
- [ ] Secrets use secret managers
- [ ] No hardcoded values in code
- [ ] Environment-specific config supported

## Phase 9: Pipeline Architecture

- [ ] Pipelines use pipz composition
- [ ] Pipeline stages are testable independently
- [ ] Error handling at each stage
- [ ] Pipeline observability present
- [ ] No blocking operations in pipelines
