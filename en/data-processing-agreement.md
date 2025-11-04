---
layout: legal
title: Data Processing Agreement
last_updated: 2025-11-04
lang: en
description: "Data Processing Agreement between LogicNodes ApS (Processor) and Partner (Controller). GDPR Art. 28 compliant."
---

# Data Processing Agreement (DPA)

**Between:**
- **Data Controller** ("[PARTNER NAME]", "Partner", "you")
- **Data Processor** ("LogicNodes ApS", "LogicNodes", "we", "us")

**Effective Date:** [DATE]  

## 1. Definitions

### 1.1 Defined Terms

For purposes of this Data Processing Agreement ("DPA"):

**"GDPR"** means Regulation (EU) 2016/679 of the European Parliament and of the Council of 27 April 2016 on the protection of natural persons with regard to the processing of personal data and on the free movement of such data.

**"Data Protection Laws"** means all applicable laws and regulations relating to privacy and data protection, including the GDPR, the UK GDPR and Data Protection Act 2018, the Swiss FADP, the CCPA/CPRA, and other applicable laws.

**"Personal Data"** means any information relating to an identified or identifiable natural person that is processed by LogicNodes on behalf of Partner in connection with the Services.

**"Processing"** means any operation or set of operations performed on Personal Data, such as collection, recording, organization, structuring, storage, adaptation, retrieval, consultation, use, disclosure, erasure, or destruction.

**"Data Subject"** means the individual to whom Personal Data relates (Partner's end-users).

**"Services"** means the LogicNodes embeddable AI agent platform as described in the Master Services Agreement.

**"Sub-Processor"** means any third party engaged by LogicNodes to process Personal Data on behalf of Partner.

**"Supervisory Authority"** means an independent public authority established by an EU Member State pursuant to GDPR Article 51.

**"Data Breach"** means a personal data breach as defined in the GDPR: a breach of security leading to the accidental or unlawful destruction, loss, alteration, unauthorized disclosure of, or access to, Personal Data transmitted, stored or otherwise processed.

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

**Special Categories:** Partner will not instruct LogicNodes to process Special Categories of Personal Data under GDPR Article 9 or criminal data under Article 10 unless expressly agreed in writing with appropriate safeguards.

### 2.3 Master Services Agreement

This DPA forms part of and supplements the Master Services Agreement ("MSA") between Partner and LogicNodes. In the event of conflict, this DPA prevails on data protection matters.

## 3. Processing of Personal Data

### 3.1 Partner Instructions

LogicNodes shall process Personal Data only:
1. On documented instructions from Partner (via API calls, configuration settings, written requests to support/security contacts, or the MSA)
2. As necessary to provide the Services
3. As required by applicable law (with notice to Partner if legally permitted)

**Partner Instructions Include:**
- User authentication via SDK (Partner provides JWTs containing user identity claims)
- Organization/user deletion requests (DELETE APIs)
- Secret management operations (POST/DELETE /api/v1/partner/secrets)
- Data retention configuration (default_retention_period setting)

### 3.2 Unauthorized Processing

If LogicNodes believes documented Partner instructions violate Data Protection Laws, LogicNodes will:
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
- If Partner provides Special Categories of Personal Data (e.g., health) or other sensitive data, Partner must  
(a) notify LogicNodes in advance in writing,  
(b) ensure a valid legal basis (e.g., GDPR Art. 9(2)), and  
(c) implement appropriate safeguards

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
- Encryption in transit (TLS 1.2 or higher; HTTPS enforcement)
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
- Dependency vulnerability scanning (automated via GitHub Dependabot)

### 4.3 Data Subject Requests

LogicNodes shall assist Partner in fulfilling Data Subject rights under Data Protection Laws. LogicNodes will assist **without undue delay**.

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
- Deletion timeline: Immediate (production), 30 days (backups)

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

**Legal Commitment (GDPR Art. 33):**
LogicNodes shall notify Partner **without undue delay** and, where feasible, within 72 hours of becoming aware of the Data Breach.

**Internal SLA Target (within 24 hours):**
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

If a DPIA indicates high risk and Partner must consult a Supervisory Authority (GDPR Art. 36), LogicNodes will provide necessary information and assistance. Any disclosures will be limited to information strictly necessary for the consultation.

## 5. Sub-Processing

### 5.1 Authorized Sub-Processors

Partner grants general authorization for LogicNodes to engage Sub-Processors, subject to the conditions in this section.

**Current Sub-Processors:**

**Complete Sub-Processor List:** /en/subprocessors

**Summary:**

| Sub-Processor | Service | Data Processed | Location | Safeguards |
|---------------|---------|----------------|----------|------------|
| **Supabase Inc.** | Database, Auth, Storage | All Personal Data | EU data hosting (AWS EU-North-1, Stockholm); entity domicile outside the EEA may apply | GDPR DPA, SCC (relies on SOC 2/ISO 27001 certified infrastructure: AWS) |
| **Vercel Inc.** | Web & Edge Hosting | Technical data, session data | EU (Frankfurt) | GDPR DPA, SCC |
| **Render Inc.** | Backend Hosting & APIs | All Personal Data | EU (Frankfurt) | EU-US DPF, GDPR DPA, SCC |
| **Mailgun Technologies Inc. (Sinch)** | Transactional email | Email, name | USA/EU (routing-dependent) | SOC 2 Type I & II, ISO 27001, GDPR DPA, SCC |
| **OpenAI LLC** | AI Model Inference (LLM) | Agent prompts, responses | Global / USA | SOC 2 Type II, GDPR DPA, SCC |
| **Anthropic PBC** | AI Model Inference (LLM) | Agent prompts, responses | Global / USA | SOC 2, GDPR DPA, SCC |
| **Google Cloud Platform** | AI Model Inference (Gemini) | Agent prompts, responses | EU / Global | SOC 2, ISO 27001, GDPR DPA, SCC |
| **xAI Corp.** | AI Model Inference (Grok) | Agent prompts, responses | Global / USA | GDPR DPA, SCC |

**LLM Providers:** By default, LogicNodes provides API keys for LLM services (OpenAI, Anthropic, Google, xAI). Partners may optionally provide their own API keys, in which case the LLM provider becomes Partner's direct processor (not LogicNodes' sub-processor).

**Sub-Processors of Sub-Processors:** Each sub-processor may engage their own sub-processors (e.g., Supabase uses AWS; Vercel and Render use AWS/Google Cloud). These are covered under respective vendor DPAs.

**Last Updated:** November 4, 2025

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
- Update to Sub-Processor list (Appendix B of Privacy Policy), and the public sub-processor page at /en/subprocessors

**Objection:**
Partner may object to new Sub-Processor on reasonable data protection grounds by notifying LogicNodes within 30 days.

**If Partner Objects:**
- LogicNodes will not engage the Sub-Processor
- OR: LogicNodes will work with Partner to address concerns
- OR: If no alternative, Partner may terminate MSA (30-day notice, no penalty)

### 5.4 Sub-Processor Liability

LogicNodes remains fully liable to Partner for Sub-Processor performance. If Sub-Processor fails to fulfill data protection obligations, LogicNodes is liable to Partner as if LogicNodes had performed the processing.

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

**UK Addendum / IDTA:** For transfers subject to UK law, the ICO International Data Transfer Addendum (or IDTA) applies by incorporation.

**Swiss Addendum:** For transfers subject to Swiss FADP, references to the GDPR and "EU" in the SCCs shall be read, mutatis mutandis, as references to the FADP and "Switzerland".

**Supabase SCCs:**
- Supabase has signed SCCs with LogicNodes
- LogicNodes has signed SCCs with Partner (via this DPA)

### 6.3 Additional Safeguards

In addition to SCCs, LogicNodes implements supplementary measures required by Schrems II:

**Encryption:**
- Data encrypted at rest with AES-256 (database, secrets, storage)
- Transport encryption with TLS 1.2 or higher
- HTTPS enforcement with HSTS headers

**Key Management:**
- AWS KMS-managed encryption keys
- Automatic key rotation at least annually
- Access to keys limited to service role
- All decrypt operations audit-logged

**Access Controls:**
- Multi-tenant isolation via PostgreSQL Row-Level Security (RLS)
- JWT-based authentication (RS256, 1-hour expiration)
- Role-based access control (admin, member, viewer)
- Application-layer access controls with MultiTenantRepository pattern
- Least-privilege principle for employee access

**Data Minimization:**
- Configurable retention periods (1-90 days for operational data)
- Automatic daily cleanup (2:00 AM UTC)
- No use of customer data for AI model training or analytics
- Purpose limitation enforced by design

**Transparency & Oversight:**
- Comprehensive audit logs (1-year retention)
- Data export APIs (JSON format, machine-readable)
- Partner access to audit logs via API
- Annual security assessments

**Government Access Requests:**
- We will promptly notify Partner unless legally prohibited
- We will use reasonable legal means to challenge or narrow over-broad requests
- We will disclose only the minimum Personal Data required by law
- All government requests will be documented and reported to Partner

### 6.4 Government Access Requests

If LogicNodes receives a lawful request from government authorities to access Personal Data:
1. Promptly notify Partner unless legally prohibited;
2. Use reasonable legal means to challenge or narrow the request;
3. Disclose only the minimum Personal Data required by law, and document the request and disclosure.

## 7. Data Retention & Deletion

### 7.1 Retention Periods

| Data Type | Retention | Deletion Method |
|-----------|-----------|-----------------|
| Agent runs, events | 1-90 days (Partner-configurable) | Automatic daily cleanup |
| Transcriptions | 1-90 days (Partner-configurable) | Automatic daily cleanup |
| Agent execution context (checkpoints) | 1-90 days (Partner-configurable) | Automatic daily cleanup |
| User account data | Until deletion request | Manual or Partner-initiated |
| Audit logs | 1 year (fixed) | Automatic after 1 year |

Backups are encrypted at rest (AES-256).

### 7.2 End of Service

Upon termination or expiration of the MSA, LogicNodes shall (at Partner's choice):

**Option A: Delete**
- Delete all Personal Data within 30 days
- Provide written certification of deletion, signed by an authorized representative

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
- **Primary:** Remote audit via documentation review, security questionnaire, and Q&A
- **Alternative:** Where available, LogicNodes may satisfy audit requests by providing recent third-party assessments (e.g., SOC 2 report when available, penetration test summaries under NDA)
- **On-Site:** On-site audit only if remote methods are insufficient to address reasonable audit concerns, with 60 days' advance notice, during business hours, and limited to reasonable duration (1-2 business days)

**Confidentiality:**
Partner agrees to sign NDA and limit access to confidential information.

**Costs:**
- First remote audit per year: No charge
- On-site audits: Reasonable costs (to be agreed in advance)
- Additional audits: Reasonable costs (to be agreed)

Audits must not unreasonably disrupt LogicNodes' operations and shall not require access to other customers' data or proprietary systems unrelated to Partner's data processing.

### 8.2 LogicNodes Certifications

LogicNodes will maintain industry-standard security practices and provide documentation upon reasonable request:
- SOC 2 Type II report (when available; targeted 2026)
- Penetration test summary reports (annual, under NDA when available)
- Sub-processor security documentation (DPAs, vendor security pages, available certifications)
- Security policies and procedures documentation
- Responses to standard security questionnaires (CAIQ, SIG, VSA)

## 9. Liability & Indemnification

### 9.1 Limitation of Liability

Each party's liability under this DPA is subject to the limitations and exclusions set out in the MSA, except to the extent such limitations are not permitted by applicable Data Protection Laws.

### 9.2 Indemnification

LogicNodes shall indemnify and hold harmless Partner from:
- Claims arising from LogicNodes' breach of this DPA
- Fines imposed by Supervisory Authorities due to LogicNodes' non-compliance with GDPR
- Data Subject claims arising from LogicNodes' unauthorized processing

**Exclusions:**
LogicNodes is NOT liable for claims arising from:
- Processing undertaken at Partner's documented instructions that contravene Data Protection Laws;
- Partner's breach of this DPA, the MSA, or Data Protection Laws;
- Events caused by Partner's systems, integrations, or end-users.

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

## 11. General Provisions

### 11.1 Governing Law

This DPA is governed by the laws specified in the MSA.

For GDPR compliance, EU data protection law applies to the extent required by GDPR Article 28(3)(a).

In case of conflict between this DPA and the SCCs with respect to personal data transfers, the SCCs shall prevail.

### 11.2 Amendments

LogicNodes may update this DPA to reflect changes required by Data Protection Laws by providing at least 30 days' notice to Partner. Material changes that adversely affect Partner's rights require Partner's consent, which may be evidenced by continued use of the Services after the effective date where permitted by law.

### 11.3 Severability

If any provision of this DPA is invalid or unenforceable, the remaining provisions remain in full force and effect. The invalid provision shall be replaced with a valid provision that achieves the original intent.

### 11.4 Entire Agreement

This DPA, together with the MSA and Privacy Policy, constitutes the entire agreement on data protection.

### 11.5 Order of Precedence

In the event of conflict:
1. This DPA (for data protection matters)
2. MSA (for commercial terms)
3. Privacy Policy (for end-user data rights)

## 12. Signatures

**Partner (Data Controller):**

Signature: _______________________________  
Name: [PARTNER AUTHORIZED SIGNATORY]  
Title: _______________________________  
Date: _______________________________  

**LogicNodes ApS (Data Processor):**

Signature: _______________________________  
Name: [LOGICNODES AUTHORIZED SIGNATORY]  
Title: _______________________________  
Date: _______________________________  

## Appendix A: Standard Contractual Clauses (SCCs)

**EU Commission Decision 2021/914 - Module 2 (Controller to Processor)**

Full text available at: https://eur-lex.europa.eu/eli/dec_impl/2021/914/oj

**Party Details:**

**Data Exporter (Controller):**
- Name: [PARTNER NAME]  
- Address: [PARTNER ADDRESS]  
- Contact: [PARTNER SECURITY CONTACT]  

**Data Importer (Processor):**
- Name: LogicNodes ApS
- Address: Sletvej 2D, 8310 Tranbjerg, Denmark
- CVR: DK45318362
- Contact: security@logicnodes.ai  

**Competent Supervisory Authority:**  
[Partner's local data protection authority, e.g., Datatilsynet for Denmark]

**Clause 7 (Docking Clause):**  
Not applicable

**Clause 9 (Use of Sub-Processors):**  
- General authorization granted (Section 5.1)
- 30-day notice for new Sub-Processors (Section 5.3)

**Clause 13 (Supervision):**  
Supervisory Authority: [Partner's local authority]

**Clause 17 (Governing Law):**  
Law of EU Member State where Data Exporter is established

**Clause 18 (Choice of Forum):**  
Courts of EU Member State where Data Exporter is established

**UK Addendum:**  
Where required, the UK Addendum to the SCCs (version issued by the ICO) forms part of this DPA.

**Swiss Addendum:**  
For Swiss FADP transfers, references in the SCCs to the GDPR and EU law shall be read as references to the FADP and Swiss law.

## Appendix B: Technical and Organizational Measures

**Security Measures Implemented by LogicNodes:**

### 1. Access Control

**Physical Access:**
- N/A (cloud-based infrastructure, no on-premise servers)
- Supabase/AWS manage physical datacenter security (ISO 27001, SOC 2)

**System Access:**
- Strong authentication required for production access (MFA enabled where supported)
- Role-based access control (least-privilege principle)
- Access limited to authorized personnel only
- All production access logged for audit purposes

**Data Access:**
- Row-Level Security (RLS) policies enforce multi-tenant isolation
- JWT-based authentication (RS256, 1-hour expiration)
- API key authentication (bcrypt hashing, show-once)
- Service role access logged to audit logs

### 2. Transmission Control

**Encryption in Transit:**
- TLS 1.2+ for all API communication
- HTTPS enforcement (HTTP redirects to HTTPS)
- HSTS headers (prevent downgrade attacks)

**API Security:**
- Rate limiting on authentication endpoints
- Input validation and parameterized queries
- SQL injection prevention (parameterized queries only)

### 3. Storage Control

**Encryption at Rest:**
- Database encryption (Supabase default, AES-256)
- Secrets encryption (Supabase Vault via AWS KMS)
- Storage bucket encryption (AWS S3, AES-256)
- Key Management: AWS KMS-managed keys, automatic rotation at least annually
- Key Access: Limited to service role, all decrypt operations audit-logged

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
- Cross-organization access prevention tests
- Automated security regression tests

### 6. Pseudonymization

**Shadow Users:**
- Synthetic email addresses ({platform_user_id}@{partner_id}.embed.logicnodes.internal)
- No PII in user IDs (UUIDs)

**Audit Logs:**
- User IDs instead of names/emails
- IP address handling aligned with security monitoring and legal requirements

### 7. Availability & Resilience

**Infrastructure:**
- Multi-AZ deployment (AWS EU-North-1, via Supabase)
- Automated failover (Supabase managed)
- High availability architecture (multi-AZ) provided by Supabase/AWS

**Disaster Recovery:**
- Daily automated backups
- Recovery time and point objectives designed to meet business continuity requirements

### 8. Incident Management

**Detection:**
- Real-time monitoring (failed auth, unusual patterns)
- Automated alerts (monitoring system)
- Audit log analysis (quarterly reviews)

**Response:**
- Incident response plan (documented procedures)
- 24-hour response time (critical issues)
- Post-incident reports (within 5 business days)

**Escalation:**
- Technical team notification (critical issues)
- CTO/technical lead oversight
- Partner communication via security contact (security@logicnodes.ai)

### 9. Data Portability & Deletion

**Export:**
- Agent run export API (JSON format)
- Structured, machine-readable data
- Response time: Within 30 days

**Deletion:**
- Cascading deletes (foreign key constraints)
- Automatic storage cleanup (triggers)
- Deletion timeline: Immediate (production), 30 days (backups)

### 10. Logging & Monitoring

**Audit Logs:**
- All authentication events logged
- Secret operations logged (automatic trigger)
- Admin operations logged (org/user deletion)
- 1-year retention

**Security Monitoring:**
- Failed authentication tracking
- API key usage monitoring
- Anomaly detection enhancements under continuous improvement

## Appendix C: Sub-Processor List

**Authoritative List:** /en/subprocessors

**Summary:**

| Sub-Processor | Service | Data Processed | Location | Safeguards | Contact |
|---------------|---------|----------------|----------|------------|---------|
| **Supabase Inc.** | Database, Authentication, Storage | All Personal Data | EU data hosting (AWS EU-North-1, Stockholm); entity domicile outside the EEA may apply | GDPR DPA, SCC (relies on SOC 2/ISO 27001 certified infrastructure: AWS) | privacy@supabase.com |
| **Vercel Inc.** | Web & Edge Hosting | Technical data, session data | EU (Frankfurt) | GDPR DPA, SCC | privacy@vercel.com |
| **Render Inc.** | Backend Hosting & APIs | All Personal Data | EU (Frankfurt) | EU-US DPF, GDPR DPA, SCC | privacy@render.com |
| **Mailgun Technologies Inc. (Sinch)** | Transactional email | Email, name | USA/EU (routing-dependent) | SOC 2 Type I & II, ISO 27001, GDPR DPA, SCC | privacy@mailgun.com |
| **OpenAI LLC** | AI Model Inference (LLM) | Agent prompts, responses | Global / USA | SOC 2 Type II, GDPR DPA, SCC | privacy@openai.com |
| **Anthropic PBC** | AI Model Inference (LLM) | Agent prompts, responses | Global / USA | SOC 2, GDPR DPA, SCC | privacy@anthropic.com |
| **Google Cloud Platform** | AI Model Inference (Gemini) | Agent prompts, responses | EU / Global | SOC 2, ISO 27001, GDPR DPA, SCC | cloud-privacy@google.com |
| **xAI Corp.** | AI Model Inference (Grok) | Agent prompts, responses | Global / USA | GDPR DPA, SCC | privacy@x.ai |

**LLM Providers:** By default, LogicNodes provides API keys for LLM services. Partners may optionally provide their own API keys, in which case the LLM provider becomes Partner's direct processor (not LogicNodes' sub-processor).

**Sub-Processors of Sub-Processors:** Each sub-processor may engage their own sub-processors (e.g., Supabase uses AWS; Vercel and Render use AWS/Google Cloud). These are covered under respective vendor DPAs.

**Last Updated:** November 4, 2025

**Changes:**
Partners will be notified 30 days before any changes to this list (new Sub-Processor, material change to existing).

The authoritative sub-processor list is maintained at /en/subprocessors.

**© 2025 LogicNodes ApS. All rights reserved.**

LogicNodes ApS
Sletvej 2D, 8310 Tranbjerg, Denmark
CVR: DK45318362

This DPA is confidential and intended for Partner execution. Public distribution is not permitted.
