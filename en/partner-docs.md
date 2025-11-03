---
layout: legal
title: Partner Documentation Hub
last_updated: 2025-11-03
lang: en
---

# Partner Documentation Hub

<p class="last-updated">Last Updated: November 3, 2025</p>

**Comprehensive Security, Privacy & Integration Resources**

---

## Welcome Partners!

This documentation hub provides everything you need to evaluate, integrate, and maintain LogicNodes in your environment. Whether you're conducting security due diligence, integrating our API, or ensuring compliance, you'll find the resources here.

---

## 📋 Documentation Index

### 🔒 Security Documentation

#### [Security Architecture]({{ '/en/security-architecture.html' | relative_url }})
**Target Audience:** Technical decision-makers, security teams, compliance officers

**Key Topics:**
- Authentication & Authorization (JWT, API keys, shadow users)
- Multi-tenant security architecture (triple-layer defense)
- Secrets management (Supabase Vault encryption)
- Data retention & automated cleanup
- Audit logging (1-year retention)
- Partner admin capabilities (org/user management)
- Infrastructure security (encryption, RLS, rate limiting)
- Compliance status (GDPR, SOC 2 roadmap)

**When to Use:**
- Security questionnaire responses
- Technical due diligence
- Integration planning
- Security team evaluation

---

### 🛡️ Privacy & Compliance

#### [Privacy Policy]({{ '/en/privacy-policy.html' | relative_url }})
**Target Audience:** Legal teams, compliance officers, end-users

**Key Topics:**
- Data controller vs processor roles
- What data we collect (and don't collect)
- How we use, share, and protect data
- Data retention & deletion policies
- GDPR rights (access, deletion, portability)
- CCPA compliance (California residents)
- International data transfers (SCCs)

**When to Use:**
- GDPR compliance review
- Privacy impact assessments (DPIA)
- End-user privacy disclosures
- Legal team evaluation

---

#### [Data Processing Agreement]({{ '/en/data-processing-agreement.html' | relative_url }})
**Target Audience:** Legal teams, procurement

**Key Topics:**
- GDPR Article 28 compliant DPA
- Processing details (subject matter, duration, data types)
- LogicNodes obligations (security, breach notification, data subject rights)
- Sub-processor authorization & notification
- International data transfers (SCCs)
- Audit rights & certifications
- Liability & indemnification

**When to Use:**
- Contract negotiation
- GDPR compliance (required for EU data)
- Legal review before integration
- Procurement process

---

### 🐛 Security Reporting

#### [Responsible Disclosure Policy]({{ '/en/responsible-disclosure.html' | relative_url }})
**Target Audience:** Security researchers, penetration testers

**Key Topics:**
- Scope (in-scope systems, vulnerability types)
- Testing guidelines (do's and don'ts)
- Safe harbor (legal protections)
- Reporting process (format, timeline)
- Response process (24hr acknowledgment, 90-day embargo)
- Recognition & rewards

**When to Use:**
- Security research authorization
- Vulnerability reporting
- Penetration testing scope definition
- Bug bounty reference (when launched)

---

## 🎯 Quick Start by Role

### For Security Teams
**Start Here:**
1. [Security Architecture]({{ '/en/security-architecture.html' | relative_url }}) - Full technical security overview
2. [Privacy Policy]({{ '/en/privacy-policy.html' | relative_url }}) - Data handling & privacy
3. [Responsible Disclosure Policy]({{ '/en/responsible-disclosure.html' | relative_url }}) - Security reporting

**Key Questions Answered:**
- How is multi-tenant isolation enforced? → Security Architecture (Section 2)
- How are secrets encrypted? → Security Architecture (Section 4)
- What's your GDPR compliance status? → Privacy Policy + Security Architecture (Section 9)
- Do you have SOC 2? → Security Architecture (Section 8)

---

### For Legal/Compliance Teams
**Start Here:**
1. [Privacy Policy]({{ '/en/privacy-policy.html' | relative_url }}) - GDPR/CCPA compliance
2. [Data Processing Agreement]({{ '/en/data-processing-agreement.html' | relative_url }}) - DPA template
3. [Security Architecture]({{ '/en/security-architecture.html' | relative_url }}) - Technical safeguards

**Key Questions Answered:**
- Are you GDPR compliant? → Yes (see Privacy Policy)
- Can we sign a DPA? → Yes (see DPA template)
- Where is data stored? → EU (AWS EU-North-1, Stockholm)
- How long is data retained? → 1-90 days (configurable), audit logs 1 year

---

### For Developers
**Start Here:**
1. Widget Integration Guide - Frontend integration (Coming soon)
2. Secret Management API - Backend integration (Coming soon)
3. [Security Architecture]({{ '/en/security-architecture.html' | relative_url }}) - Best practices

**Key Questions Answered:**
- How do I integrate the widget? → Widget Integration Guide
- How do I provision secrets? → Secret Management API
- How do I generate JWTs? → Widget Integration Guide
- What are security best practices? → Security Architecture (Section 10)

---

### For Executives/Decision Makers
**Start Here:**
1. [Security Architecture]({{ '/en/security-architecture.html' | relative_url }}) - Executive Summary
2. [Privacy Policy]({{ '/en/privacy-policy.html' | relative_url }}) - Introduction

**Key Questions Answered:**
- Is LogicNodes secure? → Yes (enterprise-grade architecture)
- Are we GDPR compliant if we use LogicNodes? → Yes (DPA available)
- What certifications do you have? → SOC 2 ready, pen test planned Q2 2026
- Can we delete user data on demand? → Yes (API-driven deletion, 24hr timeline)

---

## 📞 Contact Information

### Security Team
**Email:** [security@logicnodes.ai](mailto:security@logicnodes.ai)
**Purpose:** Security questions, vulnerability reports, incident response
**Response Time:** 24 hours

### Privacy/Compliance Team
**Email:** [privacy@logicnodes.ai](mailto:privacy@logicnodes.ai)
**Purpose:** GDPR/CCPA requests, DPA execution, privacy questions
**Response Time:** 5 business days

### Sales & Partnerships
**Email:** [sales@logicnodes.ai](mailto:sales@logicnodes.ai)
**Purpose:** Contract questions, custom agreements, security questionnaires
**Response Time:** 2 business days

### Technical Support
**Email:** [support@logicnodes.ai](mailto:support@logicnodes.ai)
**Purpose:** Integration help, API questions, troubleshooting
**Response Time:** 4 business hours

---

## 🛠️ Using These Documents

### Security Questionnaires

Most security questionnaires can be answered using these documents:

**Common Questions → Document Sections:**

| Question | Document | Section |
|----------|----------|---------|
| "Describe your authentication mechanism" | Security Architecture | Authentication |
| "How do you enforce multi-tenancy?" | Security Architecture | Data Security |
| "Do you encrypt data at rest?" | Security Architecture | Infrastructure |
| "What is your data retention policy?" | Privacy Policy | Data Retention |
| "Do you have SOC 2?" | Security Architecture | Compliance |
| "Are you GDPR compliant?" | Privacy Policy | All sections |
| "Can you sign a DPA?" | DPA Template | All sections |
| "What sub-processors do you use?" | DPA | Sub-processors |

### Vendor Security Assessments

**Common Assessment Frameworks:**

**CAIQ (Consensus Assessments Initiative Questionnaire):**
- Primary document: Security Architecture
- Supplement with: Privacy Policy, DPA

**SIG (Standardized Information Gathering):**
- Primary document: Security Architecture
- Supplement with: Privacy Policy, DPA, Responsible Disclosure

**VSA (Vendor Security Assessment):**
- Custom questionnaires: Use all documents as reference
- Contact security@logicnodes.ai for assistance

---

## 🔄 Document Updates

All documents are version-controlled and updated regularly:

**Update Frequency:**
- Security Architecture: Quarterly (or after major changes)
- Privacy Policy: As needed (30-day notice for material changes)
- DPA: As needed (in sync with Privacy Policy)
- Responsible Disclosure: Annually (or as bug bounty program evolves)

**Notification:**
Partners will be notified via email of material changes to:
- Privacy Policy (30 days advance notice)
- DPA (30 days advance notice)
- Sub-processor list (30 days advance notice)

---

## 📚 Additional Resources

### External Links

**Supabase (Infrastructure Provider):**
- [SOC 2 Report](https://supabase.com/security)
- [Security Docs](https://supabase.com/docs/guides/platform/security)

**GDPR Resources:**
- [Official Text](https://gdpr-info.eu/)
- [Article 28 (DPA Requirements)](https://gdpr-info.eu/art-28-gdpr/)

**Security Standards:**
- [OWASP Top 10](https://owasp.org/www-project-top-ten/)
- [CWE Top 25](https://cwe.mitre.org/top25/)

---

## 🎓 Glossary

**Shadow User:** Synthetic user account created during partner authentication (no password, email is `{platform_user_id}@{partner_id}.embed.logicnodes.internal`)

**RLS (Row-Level Security):** Database security policies that enforce multi-tenant isolation at the row level

**JWT (JSON Web Token):** Signed token used for authentication, containing user identity claims

**Vault:** Supabase encrypted secrets storage (for API keys, credentials)

**DPA (Data Processing Agreement):** GDPR Article 28 contract between data controller and processor

**SCC (Standard Contractual Clauses):** EU-approved contract for international data transfers

**Sub-Processor:** Third party engaged by processor to process personal data (e.g., Supabase, AWS)

**Data Controller:** Entity that determines purposes and means of processing (the Partner)

**Data Processor:** Entity that processes data on behalf of controller (LogicNodes)

---

## 📄 License & Usage

**Copyright:** © 2025 LogicNodes Inc. All rights reserved.

**Usage Rights:**
- ✅ Share with internal teams (legal, security, engineering)
- ✅ Reference in security questionnaires (with proper attribution)
- ✅ Include in internal compliance documentation
- ❌ Publicly distribute without permission
- ❌ Modify or create derivative works

**Questions:** Contact [legal@logicnodes.ai](mailto:legal@logicnodes.ai) for usage permissions.

---

**For the complete partner documentation repository, contact [sales@logicnodes.ai](mailto:sales@logicnodes.ai)**
