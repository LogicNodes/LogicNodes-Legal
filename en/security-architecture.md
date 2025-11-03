---
layout: legal
title: Security Architecture
last_updated: 2025-11-03
lang: en
---

# LogicNodes Platform - Security Architecture

**For Partner Technical Evaluation**

**Version:** 2.1

**Last Updated:** 2025-11-03

**Audience:** Technical decision-makers, security teams, compliance officers

---

## Executive Summary

The LogicNodes embeddable AI agent platform is designed with **enterprise-grade security** to protect your data and your customers' data. This document explains our security guarantees, data handling practices, and compliance capabilities.

### Security Guarantees

✅ **Complete Data Isolation** - Your organizations' data is cryptographically isolated
✅ **Encrypted Secrets** - API keys and credentials encrypted at rest, never exposed to frontend
✅ **Automated Data Retention** - You control retention (1-90 days), we handle automatic cleanup
✅ **Comprehensive Audit Logging** - 1-year audit trail of all security events
✅ **Secure API Keys** - Industry-standard hashing, show-once workflow
✅ **Rate Limiting** - Protection against abuse and brute force attacks
✅ **GDPR Ready** - Right to deletion, data export, cascading deletes

---

## Table of Contents

1. [Authentication](#1-authentication)
2. [Data Security](#2-data-security)
3. [API Key Management](#3-api-key-management)
4. [Secrets Management](#4-secrets-management)
5. [Data Retention & Privacy](#5-data-retention--privacy)
6. [Audit & Compliance](#6-audit--compliance)
7. [Partner Capabilities](#7-partner-capabilities)
8. [Compliance & Certifications](#8-compliance--certifications)
9. [Incident Response](#9-incident-response)
10. [Security Best Practices](#10-security-best-practices)

---

## 1. Authentication

### 1.1 How Authentication Works

You authenticate your users to LogicNodes via signed JWTs. This means:
- ✅ **You control authentication** - Users never create LogicNodes passwords
- ✅ **Immediate revocation** - Stop issuing tokens to revoke access instantly
- ✅ **Zero credential sharing** - We never see your users' passwords
- ✅ **Full audit trail** - All authentication attempts logged

**Flow:**
```
User logs into YOUR platform
    ↓
YOUR backend generates JWT (signed with your secret)
    ↓
YOUR frontend sends JWT to LogicNodes (/api/v1/embed/auth)
    ↓
LogicNodes validates signature and creates session
    ↓
User accesses AI functionality
```

### 1.2 JWT Requirements

**Required Claims:**
- `user_id` - User ID in your system
- `org_id` - Organization ID in your system
- `email` - User's email address
- `name` - User's display name
- `exp` - Token expiration (Unix timestamp)

**Optional Claims:**
- `org_name` - Organization display name

**Example JWT Payload:**
```json
{
  "user_id": "user_12345",
  "org_id": "org_67890",
  "email": "john@acme.com",
  "name": "John Doe",
  "org_name": "Acme Corporation",
  "exp": 1735689600
}
```

**Signing:**
- **Algorithm:** RS256 (RSA with SHA-256)
- **Public Key:** You provide your RSA public key during onboarding (stored in our database)
- **Private Key:** You keep your RSA private key secure (never shared with LogicNodes)
- **Expiration:** Recommend 1 hour maximum

### 1.3 Session Management

After successful JWT validation, we return standard session tokens:

```json
{
  "user_id": "uuid",
  "organization_id": "uuid",
  "is_new_user": false,
  "session": {
    "access_token": "eyJhbGc...",
    "refresh_token": "v1.MR5S...",
    "expires_at": 1735693200,
    "expires_in": 3600
  }
}
```

**Session Properties:**
- Access tokens expire in 1 hour
- Refresh tokens can be used to get new access tokens
- All session activity is logged to audit logs

### 1.4 Security Features

- **Rate Limiting:** 10 requests/minute per IP address on embed authentication endpoint (prevents brute force)
- **Audit Logging:** All authentication attempts logged (success and failures)
- **Token Validation:** Every API request validates the access token
- **Automatic Expiration:** Sessions expire after 1 hour of inactivity

---

## 2. Data Security

### 2.1 Multi-Tenant Isolation

Your data is completely isolated from other organizations through multiple security layers:

**Database Level:**
- Row-level security policies enforce organization boundaries
- Queries automatically filtered by organization_id
- Even privileged access respects organization scoping

**Application Level:**
- All data access requires explicit organization context
- Cross-organization queries are prevented by design
- Extensive test coverage for isolation scenarios

**Session Level:**
- Organization ID embedded in JWT (cannot be tampered)
- Every request scoped to authenticated user's organization

**Result:** Zero cross-organization data leakage. Verified by extensive security testing.

### 2.2 Encryption

**Data at Rest:**
- Database: Encrypted (industry-standard)
- Secrets: Encrypted in Vault (cannot be decrypted without proper access)
- File Storage: Encrypted (industry-standard)

**Data in Transit:**
- TLS 1.2+ for all API communication
- HTTPS enforcement (HTTP redirects to HTTPS)
- Certificate pinning recommended for mobile apps

### 2.3 Access Controls

**User Access:**
- Role-based access control (admin, member, viewer)
- Users can only access their organization's data
- Permissions enforced at database and application level

**Partner API Access:**
- API keys for backend-to-backend communication
- Secrets scoped by organization
- All API access logged to audit logs

---

## 3. API Key Management

### 3.1 Overview

Generate API keys for programmatic access to organization secrets and admin operations. Enables secure backend-to-backend communication without user authentication.

### 3.2 API Key Format

**Example:** `pk_yourcompany_7j2k9f3n8m4q1p6r5t0w2x9y8z7a6b5c4d3e2f1g0h`

**Structure:**
- Prefix: `pk_` (partner key)
- Your company ID: Identifies your organization
- Random component: Cryptographically secure random string

### 3.3 Security

- **Hashing:** Industry-standard bcrypt (same as Stripe, GitHub)
- **Show Once:** Key displayed only during generation, cannot be retrieved later
- **Storage:** Only hash stored in database (database leak does not expose usable keys)
- **Validation:** Constant-time comparison (prevents timing attacks)

### 3.4 Lifecycle

**Generation:**
```bash
POST /api/v1/partner/api-key/generate
→ Returns: { "api_key": "pk_...", "prefix": "pk_yourcompany_..." }
```
⚠️ **Save immediately - key cannot be retrieved later**

**Usage:**
```bash
Authorization: Bearer pk_yourcompany_...
```

**Rotation:**
- Generate new key (same endpoint)
- Update your systems to use new key
- Old key automatically invalidated

**Monitoring:**
```bash
GET /api/v1/partner/api-key/info
→ Returns: { "prefix": "pk_...", "created_at": "...", "last_used_at": "..." }
```

**Best Practice:** Rotate keys every 90 days

---

## 4. Secrets Management

### 4.1 Overview

Store encrypted API keys and credentials (OpenAI, Anthropic, your platform credentials) for AI agent execution. Secrets are:
- ✅ Encrypted at rest (cannot be decrypted without proper access)
- ✅ Never exposed to frontend code
- ✅ Scoped by organization (isolated from other orgs)
- ✅ Audit logged (creation, deletion, updates)

### 4.2 Management Modes

**Partner-Managed Secrets:**
- You control via API (recommended for security-critical credentials)
- Users cannot modify or delete
- Ideal for: Your platform API keys, fixed integrations

**User-Managed Secrets:**
- Users can modify via dashboard
- Ideal for: User's personal API keys (OpenAI, Anthropic)

### 4.3 API Operations

**Create/Update Secret (via API key):**
```bash
POST /api/v1/partner/secrets
{
  "org_id": "org_67890",
  "key": "YOUR_PLATFORM_API_KEY",
  "value": "sk_live_...",
  "description": "API key for customer integration",
  "managed_by": "partner"
}
```

**List Secrets (metadata only):**
```bash
GET /api/v1/partner/secrets/{org_id}
→ Returns: [{ "key": "YOUR_PLATFORM_API_KEY", "description": "...", "managed_by": "partner" }]
```
⚠️ **Values are never returned** (security by design)

**Delete Secret:**
```bash
DELETE /api/v1/partner/secrets/{org_id}/{key}
```

### 4.4 Runtime Security

When AI agents execute:
1. Secrets are decrypted **on our backend** (never sent to frontend)
2. Injected into agent execution environment
3. Never persisted in logs or database
4. Automatically cleared after execution completes

---

## 5. Data Retention & Privacy

### 5.1 What We Store

| Data Type | Retention | Purpose | Your Control |
|-----------|-----------|---------|--------------|
| User profile (email, name) | Until deletion | Account management | DELETE API |
| Agent execution history | 1-90 days (you configure) | Conversation continuity, debugging | Configurable retention |
| API requests/responses | 1-90 days (you configure) | Agent context, transparency | Configurable retention |
| Voice transcriptions | 1-90 days (you configure) | Voice input processing | Configurable retention |
| Agent execution context (checkpoints) | 1-90 days (you configure) | Agent state continuity | Configurable retention |
| Encrypted secrets | Until deletion | Tool execution | DELETE API |
| Audit logs | 1 year (fixed) | Security monitoring, compliance | Read-only |

### 5.2 Automated Cleanup

**Daily Cleanup (2:00 AM UTC):**
- Agent runs older than retention period → **Deleted**
- Associated files and transcriptions → **Deleted**
- Storage files without database records → **Deleted**

**No manual intervention required.** We handle GDPR compliance automatically.

### 5.3 Configurable Retention

**Set retention period per organization:**
```bash
# Via dashboard or API
default_retention_period = 30  # days (1-90)
```

**Use cases:**
- **Short retention (1-7 days):** Highly sensitive data, minimal GDPR risk
- **Medium retention (30 days):** Balance between functionality and compliance
- **Long retention (90 days):** Maximum conversation continuity

### 5.4 Data Deletion

**User Deletion:**
```bash
DELETE /api/v1/partner/organizations/{org_id}/users/{user_id}
```

**Organization Deletion:**
```bash
DELETE /api/v1/partner/organizations/{org_id}
```

**What Gets Deleted:**
- ✅ User/organization records
- ✅ All agent runs and execution history
- ✅ All uploaded files and transcriptions
- ✅ All encrypted secrets
- ✅ Organization memberships

**Deletion Timeline:**
- Immediate: Deleted from production database (synchronous CASCADE)
- Within 30 days: Purged from encrypted backups

**Exception:** Audit logs retained for 1 year (compliance requirement)

---

## 6. Audit & Compliance

### 6.1 What We Log

**Authentication Events:**
- JWT validation attempts (success/failure)
- Session creation
- API key authentication

**Secret Operations:**
- Secret creation, updates, deletion
- Who performed the action
- Timestamp and IP address

**Admin Operations:**
- Organization/user deletion
- API key generation
- Configuration changes

### 6.2 Audit Log Access

**Your Access:**
```bash
# Query audit logs for your partner ID
GET /api/v1/partner/audit-logs?partner_id=yourcompany
```

**What You'll See:**
- Event type (e.g., "jwt_validation", "api_key_authenticated")
- Timestamp
- IP address and User-Agent
- User/organization context
- Success/failure status
- Event details (JSON)

**Retention:** 1 year minimum

### 6.3 Use Cases

- **Security Monitoring:** Track failed authentication attempts
- **Compliance Audits:** Demonstrate GDPR compliance
- **Incident Investigation:** Review security events
- **Usage Analytics:** Understand partner activity patterns

---

## 7. Partner Capabilities

### 7.1 Organization Management

**List Organizations:**
```bash
GET /api/v1/partner/organizations
```
Returns: Organization list with usage stats (user count, recent activity)

**Delete Organization:**
```bash
DELETE /api/v1/partner/organizations/{org_id}
```
Deletes: Organization + all users, runs, secrets, files (GDPR compliant)

### 7.2 User Management

**List Users in Organization:**
```bash
GET /api/v1/partner/organizations/{org_id}/users
```

**Delete User:**
```bash
DELETE /api/v1/partner/organizations/{org_id}/users/{user_id}
```

### 7.3 Secret Provisioning

**Use Case:** Automatically provision your platform API keys when customers sign up

**Workflow:**
1. Customer activates AI feature in your platform
2. Your backend generates API key (POST /api/v1/partner/secrets)
3. AI agents can now call your platform on customer's behalf
4. Customer deactivates → You delete secret (DELETE /api/v1/partner/secrets/{org_id}/{key})

---

## 8. Compliance & Certifications

### 8.1 GDPR Compliance

**Data Controller vs Processor:**
- **You** are the Data Controller (you determine purposes and means of processing)
- **We** are the Data Processor (we process data on your behalf)

**GDPR Rights We Support:**
- ✅ Right to Access (via dashboard and API)
- ✅ Right to Deletion (DELETE APIs, cascading deletes)
- ✅ Right to Data Portability (via dashboard and API)
- ✅ Right to Rectification (update via dashboard and API)
- ✅ Data Minimization (retention policies, automated cleanup)

**Data Processing Agreement:**
- Template available (docs/partners/DATA_PROCESSING_AGREEMENT.md)
- GDPR Article 28 compliant
- Standard Contractual Clauses (SCCs) for international transfers

### 8.2 Data Location

**Primary:** European Union (AWS EU-North-1, Stockholm)

**US Residency:** Available upon request (additional fees may apply)

**International Transfers:**
- Standard Contractual Clauses (EU Commission approved)
- Adequate safeguards per GDPR Article 46

### 8.3 Infrastructure Compliance

**Our Infrastructure Provider (Supabase):**
- ✅ SOC 2 Type II certified
- ✅ ISO 27001 certified
- ✅ GDPR compliant
- ✅ HIPAA available (on request)

**Cloud Provider (AWS):**
- ✅ SOC 1, 2, 3
- ✅ ISO 27001
- ✅ PCI DSS

### 8.4 LogicNodes Certifications

**Current:**
- ✅ SOC 2 Ready (built on SOC 2 principles)
- ✅ Comprehensive security documentation
- ✅ Annual penetration testing (planned Q2 2026)

**Planned:**
- ⏳ SOC 2 Type II audit (when we reach $1M ARR, estimated 2026)
- ⏳ ISO 27001 (for EU customers, estimated 2026)
- ⏳ Bug bounty program (Q2 2026)

### 8.5 Sub-Processors

| Provider | Service | Location | Certifications |
|----------|---------|----------|----------------|
| Supabase | Database, Auth, Storage | USA | SOC 2, ISO 27001, GDPR DPA |
| AWS | Cloud Infrastructure | USA | SOC 1/2/3, ISO 27001 |
| Mailgun | Transactional Email | USA/EU | GDPR DPA |

**Change Notification:** 30 days advance notice before adding new sub-processors

---

## 9. Incident Response

### 9.1 Security Contact

**Email:** security@logicnodes.ai
**PGP Key:** Available upon request
**Response Time:** Within 24 hours for critical issues

### 9.2 Data Breach Notification

If we detect unauthorized access to your data:

**Within 24 Hours:**
- Contain the breach (stop unauthorized access)
- Notify you via email
- Provide preliminary incident report

**Within 72 Hours:**
- Detailed incident report (timeline, affected data, root cause)
- Remediation plan (steps taken, preventive measures)
- Assistance with regulatory notification (if required)

**Your Responsibility:**
- Notify affected users (if required by GDPR Article 34)
- We'll provide: Affected user lists, impact assessment, technical details

### 9.3 Responsible Disclosure

Security researchers can report vulnerabilities:
- **Email:** security@logicnodes.ai
- **Safe Harbor:** We will not pursue legal action for good-faith research
- **90-Day Embargo:** Allow us 90 days to fix before public disclosure
- **Recognition:** Public acknowledgment in our Security Hall of Fame

Full policy: [RESPONSIBLE_DISCLOSURE_POLICY.md](./RESPONSIBLE_DISCLOSURE_POLICY.md)

---

## 10. Security Best Practices

### 10.1 JWT Authentication

**DO:**
- ✅ Store signing secret in environment variables (never in code)
- ✅ Use HTTPS for all API calls
- ✅ Set JWT expiration to 1 hour or less
- ✅ Monitor failed authentication attempts in audit logs
- ✅ Rotate signing secrets every 90 days

**DON'T:**
- ❌ Hardcode signing secret in source code
- ❌ Share signing secret across environments (dev/staging/prod)
- ❌ Set JWT expiration >24 hours
- ❌ Include sensitive data in JWT claims (they're visible to anyone with token)
- ❌ Retry failed auth >10 times/minute (you'll hit rate limits)

### 10.2 API Key Management

**DO:**
- ✅ Rotate API keys every 90 days
- ✅ Store API keys in secret management system (AWS Secrets Manager, Vault)
- ✅ Monitor last_used_at to detect stale keys
- ✅ Generate new key before revoking old (zero-downtime rotation)
- ✅ Use API keys only from backend (never frontend)

**DON'T:**
- ❌ Commit API keys to version control
- ❌ Share API keys across teams/projects
- ❌ Use API keys in frontend JavaScript
- ❌ Store API keys in plaintext configuration files

### 10.3 Secret Management

**DO:**
- ✅ Use `managed_by: "partner"` for security-critical secrets
- ✅ Rotate LLM provider API keys every 90 days
- ✅ Delete secrets during customer offboarding
- ✅ Use separate secrets per environment (dev/staging/prod)

**DON'T:**
- ❌ Store secrets in user-visible locations (descriptions, notes)
- ❌ Share secrets across organizations
- ❌ Use production secrets in staging environments

### 10.4 Data Retention

**DO:**
- ✅ Set retention period based on your compliance requirements
- ✅ Communicate retention policy to end-users
- ✅ Export critical data before retention expires (if needed)
- ✅ Review audit logs quarterly

**DON'T:**
- ❌ Set retention to 1 day (breaks conversation continuity)
- ❌ Set retention to 90 days if storing highly sensitive PII
- ❌ Rely on LogicNodes for long-term data archival (we auto-delete)

### 10.5 Security Monitoring

**Recommended:**
- ✅ Monitor audit logs for failed authentication attempts
- ✅ Set up alerts for unusual activity (e.g., 10+ failed logins)
- ✅ Review API key last_used_at monthly (detect compromised keys)
- ✅ Check for unauthorized organization/user deletions
- ✅ Export audit logs for your own compliance (1-year retention)

---

## 11. Frequently Asked Questions

### 11.1 General Security

**Q: Where is data stored?**
A: European Union (AWS EU-North-1, Stockholm). US data residency available upon request.

**Q: Is data encrypted?**
A: Yes. Encrypted at rest (database, secrets, storage) and in transit (TLS 1.2+).

**Q: Do you have SOC 2?**
A: Not yet. We're SOC 2 ready (built on SOC 2 principles). Formal audit planned when we reach $1M ARR (estimated 2026).

**Q: Can you sign custom security questionnaires?**
A: Yes. Send to security@logicnodes.ai. Response time: 5-10 business days.

### 11.2 Authentication

**Q: Can users login directly to LogicNodes?**
A: Users authenticated via your JWT cannot (by design). They can only access through your platform.

**Q: How do I revoke access for a user?**
A: Stop issuing JWTs for that user. Existing sessions expire within 1 hour.

**Q: What if my signing secret is compromised?**
A: Contact security@logicnodes.ai immediately. We'll rotate your secret and invalidate all sessions.

### 11.3 Data & Privacy

**Q: Do you log API requests to my platform?**
A: Yes, in agent execution logs (for debugging and conversation continuity). Retention: 1-90 days (you configure).

**Q: How do I comply with GDPR deletion requests?**
A: Use our DELETE APIs. Cascading deletes ensure complete data removal within 24 hours (production) + 30 days (backups).

**Q: Are audit logs deleted on user deletion?**
A: No. Audit logs retained for 1 year for compliance. They contain only user IDs (no PII).

**Q: Can I export all data for a user?**
A: Users can view and export their data via the dashboard. API access to agent runs available via GET endpoints.

### 11.4 Secrets

**Q: What if I lose my API key?**
A: Generate a new one (POST /api/v1/partner/api-key/generate). Old key automatically invalidated.

**Q: Can LogicNodes employees see my secrets?**
A: Secrets are encrypted. Service role can decrypt (logged and restricted to on-call engineers for support), but access is rare and logged.

**Q: Are secrets visible to my users?**
A: No. Secrets are backend-only. Never exposed to frontend code.

### 11.5 Compliance

**Q: Do you have a DPA?**
A: Yes. Template available at [DATA_PROCESSING_AGREEMENT.md](./DATA_PROCESSING_AGREEMENT.md).

**Q: Are you HIPAA compliant?**
A: Infrastructure is HIPAA-capable (Supabase Business plan). Application-level BAA available for healthcare customers.

**Q: Can you provide a sub-processor list?**
A: Yes. See Section 8.5 (Supabase, AWS, Mailgun). Full list in DPA template.

---

## 12. Contact & Support

### Security Team
**Email:** security@logicnodes.ai
**Response Time:** 24 hours for critical issues

### Privacy & Compliance
**Email:** privacy@logicnodes.ai
**Response Time:** 5 business days

### Sales & Partnerships
**Email:** sales@logicnodes.ai
**Purpose:** DPA execution, custom agreements, security questionnaires

### Technical Support
**Email:** support@logicnodes.ai
**Response Time:** 4 business hours

---

## Document History

| Version | Date | Changes |
|---------|------|---------|
| 1.0 | 2025-01-31 | Initial security overview |
| 2.0 | 2025-11-03 | Comprehensive rewrite (API keys, audit logs, partner admin) |
| 2.1 | 2025-11-03 | Partner-focused revision (removed internal implementation details) |

---

**© 2025 LogicNodes Inc. All rights reserved.**

This document is confidential and intended for partner evaluation only. Do not distribute without permission.
