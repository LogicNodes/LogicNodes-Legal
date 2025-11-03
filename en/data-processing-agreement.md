---
layout: legal
title: Data Processing Agreement
last_updated: 2025-11-03
lang: en
---

# Data Processing Agreement (DPA)

**Between:**
- **Data Controller** ("[PARTNER NAME]", "Partner", "you")
- **Data Processor** ("LogicNodes Inc.", "LogicNodes", "we", "us")

**Effective Date:** [DATE]
**Version:** 1.0

---

## 1. Definitions

### 1.1 Defined Terms

For purposes of this Data Processing Agreement ("DPA"):

**"GDPR"** means Regulation (EU) 2016/679 of the European Parliament and of the Council of 27 April 2016 on the protection of natural persons with regard to the processing of personal data and on the free movement of such data.

**"Data Protection Laws"** means all applicable laws and regulations relating to privacy and data protection, including GDPR, CCPA, and other applicable laws.

**"Personal Data"** means any information relating to an identified or identifiable natural person that is processed by LogicNodes on behalf of Partner in connection with the Services.

**"Processing"** means any operation or set of operations performed on Personal Data, such as collection, recording, organization, structuring, storage, adaptation, retrieval, consultation, use, disclosure, erasure, or destruction.

**"Data Subject"** means the individual to whom Personal Data relates (Partner's end-users).

**"Services"** means the LogicNodes embeddable AI agent platform as described in the Master Services Agreement.

**"Sub-Processor"** means any third party engaged by LogicNodes to process Personal Data on behalf of Partner.

**"Supervisory Authority"** means an independent public authority established by an EU Member State pursuant to GDPR Article 51.

**"Data Breach"** means a breach of security leading to the accidental or unlawful destruction, loss, alteration, unauthorized disclosure of, or access to, Personal Data.

---

## 2. Scope & Roles

### 2.1 Relationship

This DPA governs the processing of Personal Data by LogicNodes (Data Processor) on behalf of Partner (Data Controller) in connection with the Services.

### 2.2 Applicability

This DPA applies to all Personal Data processed by LogicNodes on Partner's behalf, including but not limited to:
- End-user identity data (email, name, organization)
- Agent execution logs (API requests/responses)
- Voice transcriptions
- Uploaded files
- Audit logs

### 2.3 Master Services Agreement

This DPA forms part of and supplements the Master Services Agreement ("MSA") between Partner and LogicNodes. In the event of conflict, this DPA prevails on data protection matters.

---

## 3. Processing of Personal Data

### 3.1 Partner Instructions

LogicNodes shall process Personal Data only:
1. On documented instructions from Partner (via API calls, configuration settings)
2. As necessary to provide the Services
3. As required by applicable law (with notice to Partner if legally permitted)

**Partner Instructions Include:**
- Authentication requests (POST /api/v1/embed/auth)
- Organization/user deletion requests (DELETE APIs)
- Secret management operations (POST/DELETE /api/v1/partner/secrets)
- Data retention configuration (default_retention_period setting)

### 3.2 Unauthorized Processing

If LogicNodes believes Partner's instructions violate Data Protection Laws, LogicNodes will:
1. Immediately inform Partner
2. Suspend processing until instructions are clarified
3. Document the incident for audit purposes

### 3.3 Processing Details

**Subject Matter:** Provision of AI agent automation platform

**Duration:** Term of MSA + retention period (as configured by Partner)

**Nature & Purpose:**
- Authenticate end-users via JWT validation
- Execute AI agents on behalf of end-users
- Store execution context for conversation continuity
- Provide debugging and transparency tools

**Type of Personal Data:**
- Identity data: Email, name, user ID, organization ID
- Usage data: Agent runs, API requests/responses, transcriptions
- Technical data: IP address, user agent (for security)

**Categories of Data Subjects:**
- Partner's end-users (employees, customers, contractors)

**Special Categories of Data:**
- None processed by default
- If Partner provides sensitive data (health, financial, etc.), Partner must notify LogicNodes and ensure appropriate safeguards

---

## 4. LogicNodes Obligations

### 4.1 Confidentiality

LogicNodes shall ensure that all personnel authorized to process Personal Data:
1. Are subject to confidentiality obligations (employment contracts, NDAs)
2. Have received appropriate training on data protection
3. Access Personal Data only as necessary for their role

### 4.2 Security Measures

LogicNodes implements appropriate technical and organizational measures to protect Personal Data, including:

**Technical Measures:**
- Encryption at rest (database, secrets, storage)
- Encryption in transit (TLS 1.2+, HTTPS enforcement)
- Multi-tenant isolation (RLS policies, application-layer access controls)
- Access controls (JWT-based authentication, role-based permissions)
- Audit logging (all access logged for 1 year)
- Rate limiting (abuse prevention)
- Automated backups (daily, encrypted)

**Organizational Measures:**
- Background checks for employees with production access
- Least-privilege access principle
- Incident response plan (24-hour response time)
- Security awareness training (annual)
- Vendor risk management (sub-processor reviews)

**Compliance:**
- SOC 2 ready (formal audit planned)
- Annual penetration testing (planned Q2 2026)
- Vulnerability scanning (automated, weekly)

### 4.3 Data Subject Requests

LogicNodes shall assist Partner in fulfilling Data Subject rights under Data Protection Laws:

**Right to Access (GDPR Art. 15):**
- Export API endpoints for agent run history
- JSON format for machine-readable export
- Response time: Within 30 days

**Right to Rectification (GDPR Art. 16):**
- Partner updates data via JWT (name, email changes)
- Changes reflected immediately

**Right to Erasure (GDPR Art. 17):**
- DELETE APIs for user/organization removal
- Cascading deletes ensure complete removal
- Deletion timeline: Within 24 hours (production), 30 days (backups)

**Right to Data Portability (GDPR Art. 20):**
- Export API returns JSON format
- Structured, machine-readable data

**Right to Restrict Processing (GDPR Art. 18):**
- Partner can disable user accounts
- Processing stopped (data retained but not used)

**Right to Object (GDPR Art. 21):**
- Partner evaluates objection and instructs LogicNodes
- If valid, data deleted via DELETE APIs

**Assistance:**
LogicNodes will respond to Partner requests within 5 business days and provide reasonable assistance (documentation, API guidance, technical support).

### 4.4 Data Breach Notification

In the event of a Data Breach, LogicNodes shall:

**Immediate Actions (within 24 hours):**
1. Contain the breach (stop unauthorized access)
2. Notify Partner via email (security contact)
3. Provide preliminary incident report (scope, affected data, root cause)

**Follow-Up Actions (within 72 hours):**
1. Detailed incident report (timeline, impact assessment, affected Data Subjects)
2. Remediation plan (steps taken, preventive measures)
3. Assistance with Supervisory Authority notification (if required by GDPR Art. 33)

**Partner Obligations:**
- Partner is responsible for notifying Data Subjects (if required by GDPR Art. 34)
- LogicNodes will provide reasonable assistance (affected user lists, impact analysis)

### 4.5 Data Protection Impact Assessment (DPIA)

LogicNodes shall provide reasonable assistance if Partner is required to conduct a DPIA under GDPR Article 35, including:
- Description of processing operations
- Security measures implemented
- Risk assessment (data breach likelihood, impact)
- Sub-processor information

### 4.6 Prior Consultation

If a DPIA indicates high risk and Partner must consult a Supervisory Authority (GDPR Art. 36), LogicNodes will provide necessary information and assistance.

---

## 5. Sub-Processing

### 5.1 Authorized Sub-Processors

Partner grants general authorization for LogicNodes to engage Sub-Processors, subject to the conditions in this section.

**Current Sub-Processors:**

| Sub-Processor | Service | Data Processed | Location | Safeguards |
|---------------|---------|----------------|----------|------------|
| **Supabase Inc.** | Database, Auth, Storage | All Personal Data | EU (AWS EU-North-1, Stockholm) | SOC 2, ISO 27001, GDPR DPA, SCC |
| **Amazon Web Services (AWS)** | Cloud infrastructure | All Personal Data (via Supabase) | EU (Stockholm) | SOC 1/2/3, ISO 27001, SCC |
| **Mailgun Technologies Inc.** | Transactional email | Email, name | USA/EU | GDPR DPA, SCC |

**Last Updated:** November 3, 2025

### 5.2 Sub-Processor Requirements

LogicNodes shall ensure that all Sub-Processors:
1. Are bound by data protection obligations equivalent to this DPA
2. Implement appropriate technical and organizational security measures
3. Have signed Data Processing Agreements (or equivalent)
4. Undergo regular security assessments

### 5.3 New Sub-Processors

**Notification:**
LogicNodes will notify Partner at least **30 days** before engaging new Sub-Processors or materially changing existing Sub-Processors.

**Notification Method:**
- Email to Partner's security contact
- Update to Sub-Processor list (Appendix B of Privacy Policy)

**Objection:**
Partner may object to new Sub-Processor on reasonable data protection grounds by notifying LogicNodes within 30 days.

**If Partner Objects:**
- LogicNodes will not engage the Sub-Processor
- OR: LogicNodes will work with Partner to address concerns
- OR: If no alternative, Partner may terminate MSA (30-day notice, no penalty)

### 5.4 Sub-Processor Liability

LogicNodes remains fully liable to Partner for Sub-Processor performance. If Sub-Processor fails to fulfill data protection obligations, LogicNodes is liable to Partner as if LogicNodes had performed the processing.

---

## 6. International Data Transfers

### 6.1 Data Location

**Primary Storage:** European Union (AWS EU-North-1, Stockholm via Supabase)

**US Data Residency (Optional):**
Partner may request US data residency. Additional fees may apply.

### 6.2 Transfer Mechanisms

**Default:** Data stored in EU (no international transfer for EU customers)

For transfers of Personal Data to countries without an adequacy decision (if Partner requests US residency), LogicNodes relies on:

**Standard Contractual Clauses (SCCs):**
- EU Commission Decision 2021/914 (Module 2: Controller to Processor)
- Incorporated by reference into this DPA
- Full text available at: https://eur-lex.europa.eu/eli/dec_impl/2021/914/oj

**Supabase SCCs:**
- Supabase has signed SCCs with LogicNodes
- LogicNodes has signed SCCs with Partner (via this DPA)

### 6.3 Additional Safeguards

In addition to SCCs, LogicNodes implements supplementary measures:
- Encryption at rest and in transit (TLS 1.2+, AES-256)
- Access controls (multi-tenant isolation, RLS policies)
- Data minimization (retention policies, automatic cleanup)
- Transparency (audit logs, data export APIs)

### 6.4 Government Access Requests

If LogicNodes receives a lawful request from government authorities to access Personal Data:
1. LogicNodes will attempt to redirect the request to Partner
2. If legally permitted, LogicNodes will notify Partner before disclosure
3. If prohibited from notifying, LogicNodes will challenge the request or seek permission to notify

---

## 7. Data Retention & Deletion

### 7.1 Retention Periods

| Data Type | Retention | Deletion Method |
|-----------|-----------|-----------------|
| Agent runs, events | 1-90 days (Partner-configurable) | Automatic daily cleanup |
| Transcriptions | 1-90 days (Partner-configurable) | Automatic daily cleanup |
| Agent execution context (checkpoints) | 1-90 days (Partner-configurable) | Automatic daily cleanup |
| User account data | Until deletion request | Manual or Partner-initiated |
| Audit logs | 1 year (fixed) | Automatic after 1 year |

### 7.2 End of Service

Upon termination or expiration of the MSA, LogicNodes shall (at Partner's choice):

**Option A: Delete**
- Delete all Personal Data within 30 days
- Provide written certification of deletion

**Option B: Return**
- Export all Personal Data in JSON format
- Provide to Partner within 30 days
- Delete after Partner confirms receipt

**Exception:** LogicNodes may retain Personal Data to the extent required by applicable law (e.g., audit logs for compliance).

### 7.3 Partner-Initiated Deletion

Partner may request deletion at any time via:
- DELETE /api/v1/partner/organizations/{org_id} (full org deletion)
- DELETE /api/v1/partner/organizations/{org_id}/users/{user_id} (user deletion)

LogicNodes will delete immediately from production database (synchronous CASCADE), purge from backups within 30 days.

---

## 8. Audit & Compliance

### 8.1 Partner Audit Rights

Partner has the right to audit LogicNodes' compliance with this DPA, subject to:

**Frequency:** Once per calendar year (or more if Data Breach occurs)

**Scope:**
- Security measures (documentation review)
- Sub-Processor agreements
- Data retention policies
- Incident response procedures

**Method:**
- Remote audit (documentation review, Q&A)
- OR: On-site audit (with 30 days' notice, during business hours)
- OR: Third-party audit (SOC 2 report, penetration test results)

**Confidentiality:**
Partner agrees to sign NDA and limit access to confidential information.

**Costs:**
- First audit per year: No charge
- Additional audits: Reasonable costs (to be agreed)

### 8.2 LogicNodes Certifications

LogicNodes will maintain industry-standard certifications and provide upon request:
- SOC 2 Type II report (when available, estimated 2026)
- Penetration test reports (annual, under NDA)
- Sub-processor certifications (Supabase SOC 2, ISO 27001)

---

## 9. Liability & Indemnification

### 9.1 Limitation of Liability

Each party's liability under this DPA is subject to the limitations and exclusions in the MSA, except:
- Liability for Data Breaches caused by LogicNodes' gross negligence or willful misconduct
- Liability for violations of Data Protection Laws caused by LogicNodes' failure to comply with this DPA

### 9.2 Indemnification

LogicNodes shall indemnify and hold harmless Partner from:
- Claims arising from LogicNodes' breach of this DPA
- Fines imposed by Supervisory Authorities due to LogicNodes' non-compliance with GDPR
- Data Subject claims arising from LogicNodes' unauthorized processing

**Exclusions:**
LogicNodes is NOT liable for claims arising from:
- Partner's instructions (if Partner instructs unlawful processing)
- Partner's failure to comply with Data Protection Laws
- Actions of Data Subjects (if Data Subject causes breach)

---

## 10. Term & Termination

### 10.1 Term

This DPA is effective as of the Effective Date and continues for the duration of the MSA.

### 10.2 Termination

This DPA terminates automatically upon termination or expiration of the MSA.

### 10.3 Survival

The following sections survive termination:
- Section 4.2 (Security Measures) - until data deleted
- Section 4.4 (Data Breach Notification) - for breaches occurring during term
- Section 7 (Data Retention & Deletion) - until data deleted
- Section 9 (Liability & Indemnification) - per MSA limitations period

---

## 11. General Provisions

### 11.1 Governing Law

This DPA is governed by the laws specified in the MSA.

For GDPR compliance, EU data protection law applies to the extent required by GDPR Article 28(3)(a).

### 11.2 Amendments

LogicNodes may amend this DPA to comply with changes in Data Protection Laws by providing 30 days' notice to Partner.

Material changes require Partner consent (continued use of Services constitutes consent).

### 11.3 Severability

If any provision of this DPA is invalid or unenforceable, the remaining provisions remain in full force and effect. The invalid provision shall be replaced with a valid provision that achieves the original intent.

### 11.4 Entire Agreement

This DPA, together with the MSA and Privacy Policy, constitutes the entire agreement on data protection.

### 11.5 Order of Precedence

In the event of conflict:
1. This DPA (for data protection matters)
2. MSA (for commercial terms)
3. Privacy Policy (for end-user data rights)

---

## 12. Signatures

**Partner (Data Controller):**

Signature: _______________________________
Name: [PARTNER AUTHORIZED SIGNATORY]
Title: _______________________________
Date: _______________________________

**LogicNodes Inc. (Data Processor):**

Signature: _______________________________
Name: [LOGICNODES AUTHORIZED SIGNATORY]
Title: _______________________________
Date: _______________________________

---

## Appendix A: Standard Contractual Clauses (SCCs)

**EU Commission Decision 2021/914 - Module 2 (Controller to Processor)**

Full text available at: https://eur-lex.europa.eu/eli/dec_impl/2021/914/oj

**Party Details:**

**Data Exporter (Controller):**
- Name: [PARTNER NAME]
- Address: [PARTNER ADDRESS]
- Contact: [PARTNER SECURITY CONTACT]

**Data Importer (Processor):**
- Name: LogicNodes Inc.
- Address: [LOGICNODES ADDRESS]
- Contact: security@logicnodes.ai

**Competent Supervisory Authority:**
[Partner's local data protection authority, e.g., Datatilsynet for Denmark]

**Clause 7 (Docking Clause):** Not applicable

**Clause 9 (Use of Sub-Processors):**
- General authorization granted (Section 5.1)
- 30-day notice for new Sub-Processors (Section 5.3)

**Clause 13 (Supervision):**
Supervisory Authority: [Partner's local authority]

**Clause 17 (Governing Law):**
Law of EU Member State where Data Exporter is established

**Clause 18 (Choice of Forum):**
Courts of EU Member State where Data Exporter is established

---

## Appendix B: Technical and Organizational Measures

**Security Measures Implemented by LogicNodes:**

### 1. Access Control

**Physical Access:**
- N/A (cloud-based infrastructure, no on-premise servers)
- Supabase/AWS manage physical datacenter security (ISO 27001, SOC 2)

**System Access:**
- Multi-factor authentication (MFA) required for production access
- SSH key-based authentication (no password logins)
- IP whitelisting for production systems
- Least-privilege access principle (role-based)

**Data Access:**
- Row-Level Security (RLS) policies enforce multi-tenant isolation
- JWT-based authentication (HS256, 1-hour expiration)
- API key authentication (bcrypt hashing, show-once)
- Service role access logged to audit logs

### 2. Transmission Control

**Encryption in Transit:**
- TLS 1.2+ for all API communication
- HTTPS enforcement (HTTP redirects to HTTPS)
- HSTS headers (prevent downgrade attacks)

**API Security:**
- Rate limiting (10 req/min on authentication endpoints)
- Input validation (Pydantic schemas, UUID validation)
- SQL injection prevention (parameterized queries only)

### 3. Storage Control

**Encryption at Rest:**
- Database encryption (Supabase default, AES-256)
- Secrets encryption (Supabase Vault, managed keys)
- Storage bucket encryption (AWS S3, AES-256)

**Backup Security:**
- Automated daily backups (Supabase)
- Backups encrypted at rest
- 30-day backup retention

### 4. User Control

**User Authentication:**
- Shadow users (no password sharing with LogicNodes)
- JWT validation (partner's signing secret)
- Session management (1-hour expiration, refresh tokens)

**Authorization:**
- Role-based access control (admin, member, viewer)
- Permission system (runs:read, runs:create, etc.)
- Organization scoping (users only access own org data)

### 5. Data Separation

**Multi-Tenancy:**
- Database RLS policies (enforce organization_id scoping)
- Application-layer validation (MultiTenantRepository pattern)
- JWT custom claims (org_id embedded in session)

**Test Coverage:**
- 85%+ security test coverage
- Cross-organization access prevention tests
- Automated security regression tests

### 6. Pseudonymization

**Shadow Users:**
- Synthetic email addresses ({platform_user_id}@{partner_id}.embed.logicnodes.internal)
- No PII in user IDs (UUIDs)

**Audit Logs:**
- User IDs instead of names/emails
- IP addresses hashed (planned, not yet implemented)

### 7. Availability & Resilience

**Infrastructure:**
- Multi-AZ deployment (AWS EU-North-1, via Supabase)
- Automated failover (Supabase managed)
- 99.9% uptime SLA (Supabase)

**Disaster Recovery:**
- Daily automated backups
- Point-in-time recovery (last 7 days)
- RTO: 4 hours, RPO: 15 minutes

### 8. Incident Management

**Detection:**
- Real-time monitoring (failed auth, unusual patterns)
- Automated alerts (PagerDuty integration)
- Audit log analysis (quarterly reviews)

**Response:**
- Incident response plan (documented procedures)
- 24-hour response time (critical issues)
- Post-incident reports (within 5 business days)

**Escalation:**
- On-call engineer (24/7)
- Incident commander (CTO)
- Customer communication (Customer Success)

### 9. Data Portability & Deletion

**Export:**
- Agent run export API (JSON format)
- Structured, machine-readable data
- Response time: Within 30 days

**Deletion:**
- Cascading deletes (foreign key constraints)
- Automatic storage cleanup (triggers)
- Deletion timeline: 24 hours (production), 30 days (backups)

### 10. Logging & Monitoring

**Audit Logs:**
- All authentication events logged
- Secret operations logged (automatic trigger)
- Admin operations logged (org/user deletion)
- 1-year retention

**Security Monitoring:**
- Failed authentication tracking
- API key usage monitoring
- Anomaly detection (planned, not yet implemented)

---

## Appendix C: Sub-Processor List

| Sub-Processor | Service | Data Processed | Location | Safeguards | Contact |
|---------------|---------|----------------|----------|------------|---------|
| **Supabase Inc.** | Database, Authentication, Storage | All Personal Data | EU (AWS EU-North-1, Stockholm) | SOC 2, ISO 27001, GDPR DPA | privacy@supabase.com |
| **Amazon Web Services (AWS)** | Cloud infrastructure | All Personal Data (via Supabase) | EU (Stockholm) | SOC 1/2/3, ISO 27001, PCI DSS | aws-compliance@amazon.com |
| **Mailgun Technologies Inc. (Sinch)** | Transactional email | Email, name | USA/EU | GDPR DPA, SCC | privacy@mailgun.com |

**Last Updated:** November 3, 2025

**Changes:**
Partners will be notified 30 days before any changes to this list (new Sub-Processor, material change to existing).

---

**© 2025 LogicNodes Inc. All rights reserved.**

This Data Processing Agreement is confidential and intended for Partner execution only.
