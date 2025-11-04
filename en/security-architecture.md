---
layout: legal
title: Security Overview
description: "LogicNodes Platform – Enterprise security overview, data protection, and compliance commitments."
last_updated: 2025-11-03
lang: en
---

# LogicNodes Platform - Security Overview

**Last Updated:** 2025-11-03  
**Audience:** Prospective partners, security teams, compliance officers

**Distribution:** This is a high-level security overview for public evaluation. Our detailed Security Architecture document (including implementation specifics, API endpoints, and operational parameters) is available upon request for qualified partners under NDA.

**Request Full Documentation:** Contact [security@logicnodes.ai](mailto:security@logicnodes.ai)

## Executive Summary

The LogicNodes embeddable AI agent platform is designed with enterprise-grade security to protect your data and your customers' data. This overview explains our security guarantees, data handling practices, and compliance capabilities. LogicNodes is designed for secure embedding and integration within partner SaaS platforms, following the principles of least privilege and data minimization.

We do **not** use customer data for training or fine-tuning AI models.

## Security Guarantees

**Complete Data Isolation** - Your organizations' data is cryptographically isolated through multi-tenant architecture

**Encrypted Data** - All data encrypted at rest and in transit (TLS 1.2 or higher)

**Configurable Retention** - You control data retention periods; automated cleanup handles GDPR compliance

**Comprehensive Audit Logging** - Security events logged and retained for compliance

**Secure Authentication** - JWT-based authentication; you control user access

**Rate Limiting** - Protection against abuse and unauthorized access attempts

**GDPR Ready** - Right to deletion, data export, data portability, cascading deletes

## Authentication & Access Control

### How It Works

You authenticate your users to LogicNodes via signed JWTs:
- **You control authentication** - Users never create LogicNodes passwords
- **Immediate revocation** - Stop issuing tokens to revoke access
- **Zero credential sharing** - We never see your users' passwords
- **Full audit trail** - All authentication attempts logged

**Authentication Method:** RS256-signed JWTs (RSA with SHA-256)

**Session Security:** Token-based sessions with automatic expiration and refresh capability

## Data Security

### Multi-Tenant Isolation

Your data is completely isolated from other organizations through multiple security layers:

**Database Level:**
- Row-level security policies enforce organization boundaries
- Queries automatically filtered by organization
- Privileged access respects organization scoping

**Application Level:**
- All data access requires explicit organization context
- Cross-organization queries prevented by design
- Extensive test coverage for isolation scenarios

**Result:** Zero cross-organization data leakage. Adheres to the principle of least privilege and enforces strict tenant separation.

### Encryption

**Data at Rest:**
- Database: Industry-standard encryption
- Secrets: Encrypted and stored in secure vaults (cannot be decrypted without authorized backend access)
- File Storage: Industry-standard encryption

**Data in Transit:**
- TLS 1.2 or higher for all API communication
- HTTPS enforcement
- Certificate pinning recommended for mobile apps

### Access Controls

**User Access:**
- Role-based access control (admin, member, viewer)
- Users can only access their organization's data
- Permissions enforced at database and application level

**Partner API Access:**
- Secure API keys for backend-to-backend communication
- Secrets scoped by organization
- All API access logged to audit logs

## Data Retention & Privacy

### What We Store

| Data Type | Retention | Purpose | Your Control |
|-----------|-----------|---------|--------------|
| User profile (email, name) | Until deletion | Account management | DELETE API |
| Agent execution history | Configurable (1-90 days) | Conversation continuity, debugging | Configurable retention |
| API requests/responses | Configurable (1-90 days) | Agent context, transparency | Configurable retention |
| AI model interactions | Configurable (1-90 days) | Improve agent continuity and debugging | Configurable retention; **not used for model training** |
| Encrypted secrets | Until deletion | Tool execution | DELETE API |
| Audit logs | 1 year (fixed) | Security monitoring, compliance | Read-only |

### Automated Cleanup

**Daily automated cleanup** removes data older than your configured retention period. We handle GDPR compliance automatically - no manual intervention required.

### Data Deletion

**User and Organization Deletion APIs** support GDPR right to deletion:
- Immediate deletion from production database (synchronous)
- Purged from encrypted backups within 30 days
- Cascading deletes ensure complete data removal

**Exception:** Audit logs retained for 1 year for compliance (contain only user IDs, no PII)

**Audit Log Protection:**
- Tamper-resistant and write-protected via Row-Level Security
- Only authorized operations can modify logs (requires elevated privileges)
- Organization deletion preserves audit trail (logs retained for compliance)

## Compliance & Certifications

### GDPR Compliance

**Data Controller vs Processor:**
- **You** are the Data Controller (you determine purposes and means of processing)
- **We** are the Data Processor (we process data on your behalf)

**GDPR Rights We Support:**
- Right to Access (via dashboard and API)
- Right to Deletion (DELETE APIs, cascading deletes)
- Right to Data Portability (via dashboard and API)
- Right to Rectification (update via dashboard and API)
- Data Minimization (retention policies, automated cleanup)

**Data Processing Agreement:** Template available at [data-processing-agreement.md](./data-processing-agreement.md)
- GDPR Article 28 compliant
- Standard Contractual Clauses (SCCs) for international transfers

### Data Location

**Primary Data Residency:** European Union (AWS EU-North-1, Stockholm)

**US Residency:** Available upon request (additional fees may apply)

**International Transfers:**
- Standard Contractual Clauses (EU Commission approved)
- Adequate safeguards per GDPR Article 46

All data is stored in AWS EU-North-1 (Stockholm) by default, and no data is transferred outside the EU unless explicitly requested.

### Infrastructure Compliance

LogicNodes' infrastructure runs on Supabase (built on AWS). Supabase operates on Amazon Web Services (AWS), inheriting its physical and network security controls.

**Our Infrastructure Provider (Supabase):**
- SOC 2 Type II certified
- ISO 27001 certified
- GDPR compliant
- HIPAA available (on request)

**Cloud Provider (AWS):**
- SOC 1, 2, 3
- ISO 27001
- PCI DSS

### LogicNodes Certifications

**Current:**
- SOC 2 Aligned (built on SOC 2 Trust Service Principles)
- Comprehensive security documentation
- Annual penetration testing (planned Q2 2026)

**Planned:**
- SOC 2 Type II audit (as part of our 2026 compliance milestone)
- ISO 27001 (for EU customers, estimated 2026)
- Bug bounty program (Q2 2026)

### Sub-Processors

The authoritative, current list of sub-processors is maintained below. We provide 30-day advance notice before adding new sub-processors.

| Provider | Service | Location | Certifications |
|----------|---------|----------|----------------|
| Supabase | Database, Auth, Storage | EU (Stockholm) | GDPR DPA (relies on AWS SOC 2/ISO 27001) |
| AWS | Cloud Infrastructure (via Supabase) | EU (Stockholm) | SOC 1/2/3, ISO 27001 |
| Vercel | Web & Edge Hosting | EU (Frankfurt) | GDPR DPA |
| Render | Backend Hosting & APIs | EU (Frankfurt) | EU-US DPF, GDPR DPA |
| Mailgun | Transactional Email | USA/EU | SOC 2 Type I & II, ISO 27001, GDPR DPA |
| OpenAI | AI Model Inference (LLM) | Global / USA | SOC 2 Type II, GDPR DPA |
| Anthropic | AI Model Inference (LLM) | Global / USA | SOC 2, GDPR DPA |
| Google Cloud | AI Model Inference (Gemini) | EU / Global | SOC 2, ISO 27001, GDPR DPA |
| xAI | AI Model Inference (Grok) | Global / USA | GDPR DPA |

## Incident Response

### Security Contact

**Email:** security@logicnodes.ai  
**PGP Fingerprint:** Published at [https://logicnodes.ai/.well-known/security.txt](https://logicnodes.ai/.well-known/security.txt)  
**Response Time:** Within 24 hours for critical issues

### Data Breach Notification

If we detect unauthorized access to your data:

**Within 24 Hours:**
- Contain the breach (stop unauthorized access)
- Rotate all access tokens and API keys as part of containment (manual rotation completed within 24 hours)
- Notify you via email
- Provide preliminary incident report

**Within 72 Hours:**
- Detailed incident report (timeline, affected data, root cause), in accordance with GDPR Article 33
- Remediation plan (steps taken, preventive measures)
- Assistance with regulatory notification (if required)

**Your Responsibility:**
- Notify affected users (if required by GDPR Article 34)
- We'll provide: Affected user lists, impact assessment, technical details

### Responsible Disclosure

Security researchers can report vulnerabilities:
- **Email:** security@logicnodes.ai
- **Safe Harbor:** We will not pursue legal action for good-faith research
- **90-Day Embargo:** Allow us 90 days to fix before public disclosure
- **Recognition:** Public acknowledgment in our Security Hall of Fame

Full policy: [https://logicnodes.ai/responsible-disclosure](https://logicnodes.ai/responsible-disclosure)

Please review our full [Responsible Disclosure Policy](https://logicnodes.ai/responsible-disclosure) for scope and testing guidelines before conducting security research.

## Frequently Asked Questions

### General Security

**Q: Where is data stored?**  
A: European Union (AWS EU-North-1, Stockholm). US data residency available upon request.

**Q: Is data encrypted?**  
A: Yes. Encrypted at rest (database, secrets, storage) and in transit (TLS 1.2+).

**Q: Do you have SOC 2?**  
A: We're SOC 2 Aligned (built on SOC 2 Trust Service Principles). Formal audit planned as part of our 2026 compliance milestone.

**Q: Can you sign custom security questionnaires?**
A: Yes. Send to security@logicnodes.ai. Response time: 5-10 business days.

**Q: How is access to production systems controlled?**
A: Access to production data and infrastructure requires backend access, protected by MFA and fully audit-logged. All backend access is restricted to authorized engineers.

### Authentication

**Q: Can users login directly to LogicNodes?**  
A: Users authenticated via your JWT cannot (by design). They can only access through your platform.

**Q: How do I revoke access for a user?**  
A: Stop issuing JWTs for that user. Existing sessions expire automatically.

**Q: What if my signing secret is compromised?**  
A: Contact security@logicnodes.ai immediately. We'll rotate your secret and invalidate all sessions.

### Data & Privacy

**Q: Do you use customer data for AI training?**  
A: No. We do not use customer data for training or fine-tuning AI models.

**Q: How do I comply with GDPR deletion requests?**  
A: Use our DELETE APIs. Cascading deletes ensure complete data removal within 24 hours (production) + 30 days (backups).

**Q: Are audit logs deleted on user deletion?**  
A: No. Audit logs retained for 1 year for compliance. They contain only user IDs (no PII).

**Q: Can data remain within the EU only?**  
A: Yes. All data is stored in AWS EU-North-1 (Stockholm) by default, and no data is transferred outside the EU unless explicitly requested.

### Compliance

**Q: Do you have a DPA?**  
A: Yes. Template available at [data-processing-agreement.md](./data-processing-agreement.md).

**Q: Are you HIPAA compliant?**
A: Infrastructure is HIPAA-capable (Supabase Business plan). HIPAA compliance available upon request for healthcare customers. Additional security controls, legal consultation, and fees required. Contact sales@logicnodes.ai for details.

**Q: Can you provide a sub-processor list?**  
A: Yes. See the Sub-Processors section above. Full list in DPA template.

## Request Full Security Architecture

For detailed technical specifications including:
- Complete API endpoint documentation
- Detailed authentication flows and session management
- API key management and rotation procedures
- Secrets management implementation details
- Audit log schemas and access procedures
- Partner API capabilities
- Security best practices and recommendations

**Contact:** [security@logicnodes.ai](mailto:security@logicnodes.ai)

Our full Security Architecture document is available to qualified partners under NDA for security evaluation and compliance review.

## Contact & Support

### Security Team
**Email:** security@logicnodes.ai  
**PGP Fingerprint:** Published at [https://logicnodes.ai/.well-known/security.txt](https://logicnodes.ai/.well-known/security.txt)  
**Response Time:** 24 hours for critical issues  
**Full Security Architecture:** Available under NDA or by request  

### Privacy & Compliance
**Email:** privacy@logicnodes.ai  
**Response Time:** 5 business days  

### Sales & Partnerships
**Email:** sales@logicnodes.ai  
**Purpose:** DPA execution, custom agreements, security questionnaires  

### Technical Support
**Email:** support@logicnodes.ai  
**Response Time:** 4 business hours  

## Document Information

**Version:** 1.0 (Public Overview)  
**Last Updated:** 2025-11-03  
**Status:** This page is informational and subject to change  

**© 2025 LogicNodes ApS. All rights reserved.**

This document is intended for partner evaluation. The full Security Architecture is available upon request.
