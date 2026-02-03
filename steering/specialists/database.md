---
inclusion: fileMatch
fileMatchPattern: "**/*.sql,**/migrations/**,**/schema/**,**/models/**,**/entities/**"
triggers: ["database", "schema", "migration", "SQL", "query", "ORM", "table", "index"]
---

# Database Specialist

## Activation

This specialist activates when working on:
- Database schema changes
- Migration files
- Query optimization
- Data modeling
- ORM configurations

## Analysis Checklist

When database work is detected, analyze:

### 1. Schema Design
- [ ] Tables properly normalized (or intentionally denormalized)
- [ ] Primary keys defined
- [ ] Foreign key relationships correct
- [ ] Indexes support query patterns
- [ ] Data types appropriate for use case

### 2. Migration Safety
- [ ] Migration is reversible (has down migration)
- [ ] No data loss in migration
- [ ] Large table migrations have batching strategy
- [ ] Backward compatible with running code
- [ ] Tested on production-like data volume

### 3. Query Performance
- [ ] Queries use indexes effectively
- [ ] No N+1 query patterns
- [ ] Pagination implemented for large result sets
- [ ] Expensive queries identified and optimized
- [ ] Query plans reviewed for complex queries

### 4. Data Integrity
- [ ] Constraints enforce business rules
- [ ] Transactions used appropriately
- [ ] Concurrent access handled (locking strategy)
- [ ] Soft delete vs hard delete decision documented

## Common Issues to Flag

| Issue | Severity | Recommendation |
|-------|----------|----------------|
| Missing index on foreign key | 🟡 Medium | Add index for join performance |
| VARCHAR without length limit | 🟡 Medium | Define appropriate max length |
| No migration rollback | 🟠 High | Add down migration |
| SELECT * in production code | 🟡 Medium | Select only needed columns |
| Missing created_at/updated_at | 🟢 Low | Add audit timestamps |

## Questions to Ask

1. **Data Volume**: How much data? Growth rate?
2. **Access Patterns**: Read-heavy or write-heavy?
3. **Consistency**: Strong consistency required or eventual OK?
4. **Retention**: How long to keep data? Archival strategy?
5. **Compliance**: PII? GDPR/CCPA requirements?
