# Testing Audit Checklist

## Phase 1: Test Inventory

- [ ] All packages have test files
- [ ] Test file naming follows convention (`*_test.go`)
- [ ] No orphaned test files (testing deleted code)
- [ ] Test packages use appropriate suffix (`_test` for black-box)
- [ ] Integration tests in `testing/integration/`

## Phase 2: 1:1 Mapping

- [ ] Each source file has corresponding test file
- [ ] `user.go` → `user_test.go`
- [ ] Handler tests exist per handler
- [ ] Store tests exist per store
- [ ] Transformer tests exist per transformer

## Phase 3: Test Quality

- [ ] Tests have meaningful assertions (not just `err == nil`)
- [ ] Error paths tested
- [ ] Edge cases covered
- [ ] Table-driven tests used appropriately
- [ ] Test names describe behavior

## Phase 4: Test Infrastructure

- [ ] Fixtures in `testing/fixtures.go`
- [ ] Mocks in `testing/mocks.go`
- [ ] Helpers call `t.Helper()`
- [ ] Helpers accept `*testing.T` as first param
- [ ] Setup functions use option pattern

## Phase 5: Mock Quality

- [ ] Mocks use function-field pattern
- [ ] Mocks satisfy contracts
- [ ] Mock behavior is configurable
- [ ] No mocks that always succeed
- [ ] Mock assertions verify calls

## Phase 6: Benchmark Presence

- [ ] Critical paths have benchmarks
- [ ] Benchmarks in `testing/benchmarks/`
- [ ] `b.ReportAllocs()` called
- [ ] Results consumed (prevent optimization)
- [ ] Parallel variants where appropriate

## Phase 7: Integration Tests

- [ ] Integration setup in `testing/integration/setup.go`
- [ ] Real registry with real stores
- [ ] Option pattern for store injection
- [ ] Cleanup after tests
- [ ] Isolation between tests

## Phase 8: CI Integration

- [ ] Tests run in CI
- [ ] Race detector enabled (`-race`)
- [ ] Coverage collected
- [ ] Coverage thresholds enforced (70% floor, 80% patch)
- [ ] Benchmark regressions tracked (if applicable)

## Phase 9: Coverage Analysis

- [ ] Coverage report generated
- [ ] Critical paths have high coverage
- [ ] Low coverage areas justified
- [ ] No tests that inflate coverage without value
- [ ] Coverage trends monitored
