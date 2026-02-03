---
inclusion: fileMatch
fileMatchPattern: "**/*.test.*,**/*.spec.*,**/test/**,**/tests/**,**/__tests__/**"
triggers: ["test", "testing", "coverage", "QA", "unit test", "integration test", "e2e"]
---

# Testing Specialist

## Activation

This specialist activates when working on:
- Unit tests
- Integration tests
- End-to-end tests
- Test coverage
- Test infrastructure

## Analysis Checklist

### 1. Test Coverage
- [ ] Critical paths have tests
- [ ] Edge cases covered
- [ ] Error scenarios tested
- [ ] Coverage targets met
- [ ] No dead/skipped tests

### 2. Test Quality
- [ ] Tests are deterministic (no flaky tests)
- [ ] Tests are independent (no order dependency)
- [ ] Tests are fast (unit < 100ms, integration < 1s)
- [ ] Tests have clear assertions
- [ ] Test names describe behavior

### 3. Test Types
- [ ] Unit tests for business logic
- [ ] Integration tests for APIs/database
- [ ] E2E tests for critical user flows
- [ ] Contract tests for API consumers
- [ ] Performance tests for SLAs

### 4. Test Infrastructure
- [ ] CI runs tests on every PR
- [ ] Test environment isolated
- [ ] Test data management strategy
- [ ] Mocking strategy consistent
- [ ] Test reports accessible

## Common Issues to Flag

| Issue | Severity | Recommendation |
|-------|----------|----------------|
| No tests for critical path | 🔴 Critical | Add tests immediately |
| Flaky tests | 🟠 High | Fix or quarantine |
| Tests depend on order | 🟠 High | Make tests independent |
| Mocking too much | 🟡 Medium | Test real behavior |
| No integration tests | 🟡 Medium | Add integration layer |
| Slow test suite | 🟡 Medium | Parallelize or optimize |

## Questions to Ask

1. **Coverage Target**: What % coverage required?
2. **Test Types**: Unit/integration/e2e balance?
3. **CI Requirements**: Tests block merge?
4. **Performance**: Test execution time budget?
5. **Data**: Test data strategy (fixtures, factories)?

## Test Naming Convention

```
describe('[Unit/Component]', () => {
  it('should [expected behavior] when [condition]', () => {
    // Arrange - Given
    // Act - When
    // Assert - Then
  });
});
```
