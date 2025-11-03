---
layout: legal
title: Partner Embedded Users Privacy Policy
last_updated: 2025-11-03
lang: en
---

<div class="policy-notice">
<strong>📋 Which Privacy Policy Applies to You?</strong>
<ul>
<li><strong>This policy:</strong> If you access LogicNodes <strong>through a partner's product</strong> (e.g., embedded AI features in Rackbeat, Shopify, etc.)</li>
<li><strong><a href="{{ '/en/privacy-policy.html' | relative_url }}">Standard Privacy Policy</a>:</strong> If you <strong>signed up directly</strong> at app.logicnodes.ai</li>
</ul>
</div>

---

# LogicNodes Platform - Privacy Policy

**Effective Date:** November 3, 2025

**Last Updated:** November 3, 2025

**Version:** 1.0

---

## 1. Introduction

LogicNodes ("we," "our," or "us") provides an embeddable AI agent platform that enables businesses ("Partners") to integrate AI-powered automation into their products. This Privacy Policy explains how we collect, use, store, and protect personal data when Partners integrate our platform into their products.

**Important:** If you are an end-user accessing LogicNodes through a Partner's product (e.g., Rackbeat, Shopify), your personal data is primarily controlled by the Partner. This policy explains LogicNodes' role as a **data processor** on behalf of the Partner (who is the **data controller**).

---

## 2. Roles & Responsibilities

### 2.1 Data Controller vs. Data Processor

**Partner (Data Controller):**
- Controls what personal data is collected
- Determines purposes and means of processing
- Responsible for obtaining user consent
- Must provide their own privacy policy to end-users

**LogicNodes (Data Processor):**
- Processes data on behalf of Partner
- Follows Partner's instructions via our API
- Implements security measures (encryption, access controls)
- Assists Partner with GDPR compliance (data deletion, export)

### 2.2 Your Rights (End-Users)

If you are an end-user accessing LogicNodes through a Partner's product:
- ✅ **Right to access:** Request copy of your data
- ✅ **Right to deletion:** Request deletion of your data
- ✅ **Right to portability:** Export your data in machine-readable format
- ✅ **Right to rectification:** Correct inaccurate data

**How to exercise rights:** Contact the Partner directly. They will instruct us to fulfill your request.

---

## 3. Data We Collect

### 3.1 Identity Data (via Partner)

When you access LogicNodes through a Partner's product, we receive:

| Data | Source | Purpose | Retention |
|------|--------|---------|-----------|
| Email address | Partner JWT | Account identification, notifications | Until deletion |
| Full name | Partner JWT | Display in UI | Until deletion |
| Organization ID | Partner JWT | Multi-tenant isolation | Until deletion |
| Organization name | Partner JWT (optional) | Display in UI | Until deletion |
| Partner user ID | Partner JWT | Link to Partner account | Until deletion |

**Legal Basis (GDPR):** Legitimate interest (providing service to Partner), Contractual necessity

### 3.2 Usage Data

When you use AI agents through our platform:

| Data | Purpose | Retention | Can Delete? |
|------|---------|-----------|-------------|
| Agent run history | Conversation continuity, debugging | 1-90 days (configurable) | ✅ Yes (automatic) |
| API requests/responses | Agent execution context | 1-90 days (configurable) | ✅ Yes (automatic) |
| Tool execution logs | Debugging, transparency | 1-90 days (configurable) | ✅ Yes (automatic) |
| Voice transcriptions | Process voice input | 1-90 days (configurable) | ✅ Yes (automatic) |
| Uploaded files | Agent input data | 1-90 days (configurable) | ✅ Yes (automatic) |

**Legal Basis (GDPR):** Legitimate interest (service functionality), Contractual necessity

### 3.3 Authentication Data

| Data | Purpose | Retention | Can Delete? |
|------|--------|-----------|-------------|
| Session tokens | Authenticate API requests | 1 hour (auto-expires) | ⚠️ No (security) |
| Audit logs (auth events) | Security monitoring, compliance | 1 year | ⚠️ No (compliance) |
| IP address | Security monitoring, fraud prevention | 1 year (audit logs) | ⚠️ No (compliance) |
| User agent | Security monitoring | 1 year (audit logs) | ⚠️ No (compliance) |

**Legal Basis (GDPR):** Legitimate interest (security), Legal obligation (audit requirements)

### 3.4 Technical Data (Automatically Collected)

| Data | Purpose | Retention |
|------|---------|-----------|
| Browser type/version | Compatibility, debugging | Session only |
| Device information | Optimize UI | Session only |
| Timezone | Display timestamps | Session only |

**Legal Basis (GDPR):** Legitimate interest (service optimization)

### 3.5 Data We Do NOT Collect

- ❌ Payment information (Partners handle billing)
- ❌ Passwords (shadow users use synthetic passwords managed by us)
- ❌ Social security numbers or government IDs
- ❌ Health information (unless Partner explicitly provides it)
- ❌ Financial account numbers

---

## 4. How We Use Data

### 4.1 Service Provision

We use your data to:
- ✅ Authenticate you via Partner JWT
- ✅ Execute AI agents on your behalf
- ✅ Display conversation history
- ✅ Process voice input (transcription)
- ✅ Store execution context for multi-turn conversations

### 4.2 Security & Fraud Prevention

We use your data to:
- ✅ Detect unauthorized access attempts
- ✅ Monitor for API abuse
- ✅ Investigate security incidents
- ✅ Comply with security audit requirements

### 4.3 Service Improvement

We use aggregated, anonymized data to:
- ✅ Analyze feature usage
- ✅ Optimize performance
- ✅ Improve AI agent accuracy

**Note:** We do NOT use your personal data for AI model training (LLM providers you configure may have their own policies).

### 4.4 Legal Compliance

We may use/disclose data to:
- ✅ Comply with legal obligations (subpoenas, court orders)
- ✅ Enforce our Terms of Service
- ✅ Protect our rights and safety
- ✅ Respond to lawful government requests

---

## 5. Data Sharing & Disclosure

### 5.1 With Partners

**Your data belongs to the Partner.** We share:
- ✅ Agent execution results (via API responses)
- ✅ Usage metrics (run counts, error rates)
- ⚠️ We do NOT share data across different Partners

### 5.2 With Sub-Processors

We use trusted third-party services:

| Sub-Processor | Service | Data Shared | Location | Safeguards |
|---------------|---------|-------------|----------|------------|
| **Supabase** | Database, Auth, Storage | All data | EU (AWS EU-North-1, Stockholm) | SOC 2, ISO 27001, GDPR DPA |
| **AWS** | Hosting infrastructure | All data (via Supabase) | EU (Stockholm) | SOC 1/2/3, ISO 27001 |
| **Mailgun** | Transactional emails | Email, name | USA/EU | GDPR DPA available |

**Sub-Processor Agreements:** All sub-processors have signed Data Processing Agreements (DPAs) with adequate GDPR safeguards.

### 5.3 With LLM Providers (Partner-Configured)

If Partners configure their own LLM API keys (OpenAI, Anthropic, Google, Grok):
- ✅ Agent prompts/responses sent to LLM provider
- ✅ Data subject to LLM provider's privacy policy
- ⚠️ LogicNodes is NOT responsible for LLM provider data handling

**Recommendation:** Partners should review LLM provider privacy policies and configure data retention settings.

### 5.4 No Sale of Personal Data

We do NOT sell, rent, or trade personal data to third parties. Ever.

---

## 6. Data Retention & Deletion

### 6.1 Automatic Retention Policies

| Data Type | Retention | Deletion Method |
|-----------|-----------|-----------------|
| Agent runs | 1-90 days (Partner-configurable) | Automatic daily cleanup |
| Agent run events | 1-90 days (Partner-configurable) | Automatic daily cleanup |
| Transcriptions | 1-90 days (Partner-configurable) | Automatic daily cleanup |
| Audit logs | 1 year (fixed) | Automatic after 1 year |
| User account data | Until deletion request | Manual or Partner-initiated |

**Cleanup Schedule:** Daily at 2:00 AM UTC

### 6.2 User-Initiated Deletion

**How to delete your data:**
1. Contact the Partner (data controller)
2. Partner sends deletion request via API
3. We cascade-delete all associated data:
   - ✅ User account
   - ✅ Organization membership
   - ✅ Agent runs, events, transcriptions
   - ✅ Agent execution context (checkpoints)
   - ✅ Vault secrets (encrypted credentials)

**Deletion Timeline:**
- Immediate: All data deleted from production database (synchronous CASCADE)
- Within 30 days: All data purged from encrypted backups

**Cannot Delete:**
- ⚠️ Audit logs (retained 1 year for compliance)
- ⚠️ Aggregated, anonymized analytics

### 6.3 Partner-Initiated Deletion

Partners can delete organizations/users via:
- `DELETE /api/v1/partner/organizations/{org_id}` (full org deletion)
- `DELETE /api/v1/partner/organizations/{org_id}/users/{user_id}` (user removal)

Same cascading deletion applies.

---

## 7. Data Security

### 7.1 Encryption

**At Rest:**
- ✅ Database encryption (Supabase default)
- ✅ Secrets encryption (Supabase Vault)
- ✅ Storage bucket encryption (AWS S3)

**In Transit:**
- ✅ TLS 1.2+ for all API communication
- ✅ HTTPS enforcement
- ✅ HSTS headers

### 7.2 Access Controls

**Multi-Tenant Isolation:**
- ✅ Row-Level Security (RLS) policies
- ✅ Application-layer access controls
- ✅ JWT-based session scoping

**Employee Access:**
- ✅ Least-privilege principle
- ✅ Service role access logged to audit logs
- ✅ Background checks for employees with production access

### 7.3 Security Monitoring

**Real-Time Monitoring:**
- ✅ Failed authentication attempts
- ✅ Unusual API access patterns
- ✅ Secret access/deletion events

**Incident Response:**
- ✅ 24-hour response time for critical issues
- ✅ Security contact: security@logicnodes.ai
- ✅ Post-incident reports (within 5 business days)

---

## 8. International Data Transfers

### 8.1 Data Location

**Primary Storage:** European Union (AWS EU-North-1, Stockholm via Supabase)

**Data Location:**
- ✅ EU data residency by default (Sweden)
- ✅ GDPR-compliant data hosting
- ✅ US data residency available upon Partner request

**International Transfers:**
- Standard Contractual Clauses (SCCs) available for US transfers
- Adequate safeguards per GDPR Article 46

### 8.2 Adequacy Decisions

We rely on:
- ✅ Standard Contractual Clauses (SCCs) - EU Commission approved
- ✅ Supabase compliance (SOC 2, ISO 27001)
- ✅ AWS compliance (SOC 1/2/3, ISO 27001)

---

## 9. Your Rights (GDPR)

### 9.1 Right to Access (Article 15)

**Request:** Copy of your personal data

**How to exercise:**
1. Contact Partner (data controller)
2. Partner requests export via API
3. We provide data within 30 days

**What you'll receive:**
- User account details (email, name, org)
- Agent run history (JSON export)
- Audit logs (if relevant)

### 9.2 Right to Rectification (Article 16)

**Request:** Correct inaccurate data

**How to exercise:**
1. Update data via Partner's product
2. Partner sends updated JWT (name, email changes)
3. We update immediately

### 9.3 Right to Erasure (Article 17)

**Request:** Delete your personal data ("right to be forgotten")

**How to exercise:**
1. Contact Partner
2. Partner sends deletion request via API
3. We delete within 24 hours (see section 6.2)

**Exceptions (we can refuse deletion):**
- ⚠️ Legal obligation to retain (audit logs - 1 year)
- ⚠️ Public interest (security investigation)
- ⚠️ Legal claims (ongoing litigation)

### 9.4 Right to Data Portability (Article 20)

**Request:** Export data in machine-readable format

**How to exercise:**
1. Contact Partner
2. Partner requests export via API
3. We provide JSON export (structured data)

**What's included:**
- User profile (email, name)
- Agent runs (conversation history)
- Execution logs (API requests/responses)

### 9.5 Right to Restrict Processing (Article 18)

**Request:** Temporarily stop processing your data

**How to exercise:**
1. Contact Partner
2. Partner disables user account
3. We stop processing (data retained but not used)

### 9.6 Right to Object (Article 21)

**Request:** Object to processing based on legitimate interest

**How to exercise:**
1. Contact Partner
2. Partner evaluates objection
3. If valid, Partner instructs us to delete data

### 9.7 Right to Withdraw Consent

**Request:** Withdraw consent for data processing

**How to exercise:**
1. Stop using Partner's product (no new data sent to LogicNodes)
2. Request deletion (see section 9.3)

---

## 10. Children's Privacy

**Age Restriction:** LogicNodes is NOT intended for children under 16.

**No Knowingly Collection:** We do not knowingly collect personal data from children under 16.

**Parental Notice:** If you believe we have collected data from a child under 16, contact us immediately at privacy@logicnodes.ai. We will delete the data within 24 hours.

---

## 11. California Privacy Rights (CCPA)

If you are a California resident:

### 11.1 Right to Know (CCPA § 1798.100)

You have the right to know:
- What personal information we collect
- Sources of personal information
- Purposes of collection
- Third parties we share with

**See sections 3-5 of this policy.**

### 11.2 Right to Delete (CCPA § 1798.105)

You have the right to request deletion of personal information.

**See section 6.2 for deletion process.**

### 11.3 Right to Opt-Out of Sale (CCPA § 1798.120)

**We do NOT sell personal information.** No opt-out necessary.

### 11.4 Right to Non-Discrimination (CCPA § 1798.125)

We will NOT discriminate against you for exercising CCPA rights.

### 11.5 Authorized Agent

California residents can designate an authorized agent to make requests on their behalf:
1. Provide written authorization
2. Verify identity (government-issued ID)
3. Submit request to privacy@logicnodes.ai

---

## 12. Changes to This Policy

**Notification Method:**
- Email to Partners (30 days advance notice)
- Update "Last Updated" date at top of policy
- Material changes require explicit consent

**Material Changes:**
- Expanding data collection (new categories)
- Changing retention periods (longer retention)
- Adding new sub-processors
- Changing legal basis for processing

**Non-Material Changes:**
- Clarifications, formatting
- Updates to contact information
- Correction of typos

---

## 13. Contact Us

### Privacy Team
**Email:** privacy@logicnodes.ai
**Response Time:** 5 business days

### Data Protection Officer (DPO)
**Email:** dpo@logicnodes.ai
**Purpose:** GDPR/CCPA requests, privacy concerns

### Security Team
**Email:** security@logicnodes.ai
**Purpose:** Security incidents, data breaches

### Mailing Address
LogicNodes Inc.
[Company Address]
[City, State, ZIP]
United States

---

## 14. Supervisory Authority (EU)

If you are located in the EU/EEA and believe we have violated GDPR, you have the right to lodge a complaint with your local data protection authority:

**List of EU Data Protection Authorities:**
https://edpb.europa.eu/about-edpb/board/members_en

**Example (Denmark):**
Datatilsynet
Carl Jacobsens Vej 35
2500 Valby
Denmark
Email: dt@datatilsynet.dk

---

## 15. Glossary

**Data Controller:** Entity that determines purposes and means of processing personal data (the Partner).

**Data Processor:** Entity that processes data on behalf of the Data Controller (LogicNodes).

**Personal Data:** Any information relating to an identified or identifiable natural person.

**Shadow User:** Synthetic user account created during Partner authentication (no password, email is `{platform_user_id}@{partner_id}.embed.logicnodes.internal`).

**JWT (JSON Web Token):** Signed token used for authentication, containing user identity claims.

**Vault:** Supabase encrypted secrets storage (for API keys, credentials).

**RLS (Row-Level Security):** Database security policies that enforce multi-tenant isolation.

**Cascading Delete:** Automatic deletion of related records when parent record is deleted.

---

## Appendix A: Data Processing Activities

| Processing Activity | Purpose | Legal Basis (GDPR) | Retention |
|---------------------|---------|-------------------|-----------|
| User authentication | Verify identity via Partner JWT | Legitimate interest, Contract | Session (1 hour) |
| Agent execution | Provide AI automation service | Contract | 1-90 days |
| Audit logging | Security monitoring, compliance | Legitimate interest, Legal obligation | 1 year |
| Secret storage | Store encrypted API keys | Contract | Until deletion |
| File storage | Process uploaded documents | Contract | 1-90 days |
| Email notifications | Send transactional emails | Contract | Session |

---

## Appendix B: Sub-Processor List

| Sub-Processor | Service | Data Shared | Location | DPA Signed |
|---------------|---------|-------------|----------|------------|
| Supabase | Database, Auth, Storage | All data | EU (AWS EU-North-1, Stockholm) | ✅ Yes |
| Amazon Web Services (AWS) | Cloud infrastructure | All data (via Supabase) | EU (Stockholm) | ✅ Yes (via Supabase) |
| Mailgun | Transactional email | Email, name | USA/EU | ✅ Yes |

**Last Updated:** November 3, 2025

**Changes Notification:** Partners notified 30 days before adding new sub-processors.

---

**© 2025 LogicNodes Inc. All rights reserved.**

This privacy policy is effective as of November 3, 2025. By using LogicNodes through a Partner's product, you acknowledge you have read and understood this policy.
