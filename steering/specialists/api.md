---
inclusion: fileMatch
fileMatchPattern: "**/routes/**,**/controllers/**,**/handlers/**,**/api/**,**/*.graphql,**/openapi.*"
triggers: ["API", "endpoint", "REST", "GraphQL", "contract", "route", "handler", "controller"]
---

# API Specialist

## Activation

This specialist activates when working on:
- REST API endpoints
- GraphQL schemas and resolvers
- API contracts (OpenAPI/Swagger)
- Request/response handling
- API versioning

## Analysis Checklist

### 1. Contract Design
- [ ] Endpoints follow REST conventions (or GraphQL best practices)
- [ ] HTTP methods used correctly (GET/POST/PUT/PATCH/DELETE)
- [ ] Status codes meaningful and consistent
- [ ] Request/response schemas documented
- [ ] Versioning strategy defined

### 2. Input Validation
- [ ] All inputs validated
- [ ] Validation errors return helpful messages
- [ ] Type coercion handled safely
- [ ] Size limits on payloads
- [ ] File upload limits if applicable

### 3. Error Handling
- [ ] Consistent error response format
- [ ] Errors don't leak sensitive information
- [ ] Appropriate status codes for error types
- [ ] Retry guidance in responses (Retry-After header)
- [ ] Rate limit errors include limit info

### 4. Security
- [ ] Authentication required where needed
- [ ] Authorization checks on resources
- [ ] CORS configured appropriately
- [ ] Rate limiting implemented
- [ ] Sensitive data not in URLs

### 5. Performance
- [ ] Pagination for list endpoints
- [ ] Filtering/sorting supported
- [ ] Response compression enabled
- [ ] Caching headers set appropriately
- [ ] Async operations for long-running tasks

## Common Issues to Flag

| Issue | Severity | Recommendation |
|-------|----------|----------------|
| No input validation | 🔴 Critical | Add validation middleware |
| Sensitive data in URL | 🔴 Critical | Move to request body or headers |
| No rate limiting | 🟠 High | Implement rate limiting |
| Inconsistent error format | 🟡 Medium | Standardize error responses |
| Missing pagination | 🟡 Medium | Add limit/offset or cursor |

## Questions to Ask

1. **Consumers**: Who calls this API? Internal/external?
2. **Volume**: Expected requests per second?
3. **Latency**: Required response time (p50, p99)?
4. **Compatibility**: Breaking change policy?
5. **Documentation**: OpenAPI spec required?
