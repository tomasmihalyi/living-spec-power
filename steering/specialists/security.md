---
inclusion: fileMatch
fileMatchPattern: "**/auth/**,**/security/**,**/middleware/auth*,**/guards/**"
triggers: ["security", "auth", "authentication", "authorization", "validation", "threats", "encryption"]
---

# Security Specialist

## Activation

This specialist activates when working on:
- Authentication systems
- Authorization/permissions
- Input validation
- Encryption/secrets
- Security configurations

## Analysis Checklist

### 1. Authentication
- [ ] Passwords hashed with strong algorithm (bcrypt, argon2)
- [ ] Session management secure
- [ ] Token expiration appropriate
- [ ] Multi-factor authentication available (if required)
- [ ] Account lockout after failed attempts

### 2. Authorization
- [ ] Principle of least privilege applied
- [ ] Role-based or attribute-based access control
- [ ] Resource ownership verified
- [ ] Admin functions protected
- [ ] Audit logging for sensitive operations

### 3. Input Validation
- [ ] All user input validated server-side
- [ ] SQL injection prevented (parameterized queries)
- [ ] XSS prevented (output encoding)
- [ ] CSRF tokens implemented
- [ ] File upload validation (type, size, content)

### 4. Data Protection
- [ ] Sensitive data encrypted at rest
- [ ] TLS for data in transit
- [ ] Secrets not in code/logs
- [ ] PII handling compliant
- [ ] Data retention policies enforced

## Common Issues to Flag

| Issue | Severity | Recommendation |
|-------|----------|----------------|
| Hardcoded secrets | 🔴 Critical | Use environment variables/secrets manager |
| SQL string concatenation | 🔴 Critical | Use parameterized queries |
| Missing CSRF protection | 🔴 Critical | Add CSRF tokens |
| Weak password hashing | 🔴 Critical | Use bcrypt/argon2 |
| No rate limiting on auth | 🟠 High | Add rate limiting |
| Verbose error messages | 🟡 Medium | Generic errors to users |

## Questions to Ask

1. **Compliance**: SOC 2, HIPAA, GDPR requirements?
2. **Authentication**: SSO, OAuth, or custom auth?
3. **Authorization**: Role-based or attribute-based?
4. **Data Classification**: What data is sensitive?
5. **Audit**: What actions need logging?
