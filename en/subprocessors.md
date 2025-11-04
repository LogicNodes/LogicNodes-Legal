---
layout: legal
title: Sub-Processor List
last_updated: 2025-11-04
lang: en
description: "Complete list of third-party sub-processors engaged by LogicNodes ApS for service delivery. GDPR-compliant notification page."
---

# LogicNodes – Authorized Sub-Processors

**Effective Date:** November 4, 2025
**Last Updated:** November 4, 2025

This page lists all third-party sub-processors engaged by **LogicNodes ApS** (CVR: DK45318362) in connection with providing the LogicNodes platform and related services.

Each sub-processor is bound by a valid **Data Processing Agreement (DPA)** that includes appropriate GDPR safeguards (e.g., Standard Contractual Clauses, SOC 2, ISO 27001).

Copies of all executed or click-through DPAs are maintained internally and can be provided to partners upon request.

---

## Primary Sub-Processors

| Sub-Processor | Service | Primary Region | DPA Status | Notes |
|----------------|----------|---------|-------------|--------|
| **Supabase Inc.** | Database, Authentication, Storage | EU (eu-north-1 – Stockholm) | ✅ Signed | Core data infrastructure provider. Supabase may engage AWS and other infrastructure vendors under its own DPA. |
| **Vercel Inc.** | Web & Edge Hosting for Frontend Services | EU (Frankfurt) | ✅ Auto-executed on signup | Used for hosting web assets and edge functions. |
| **Render Inc.** | Backend Hosting & APIs | EU (Frankfurt) | ✅ Auto-executed on signup | Used for application servers and scheduled jobs. |
| **Sinch / Mailgun Technologies Inc.** | Transactional Email Delivery | EU (Germany) / USA | ✅ Auto-executed on signup | Used for system notifications and transactional email. Routing is region-dependent. |
| **OpenAI LLC** | AI Model Inference (LLM) | Global / USA | ✅ Auto-executed on signup | LogicNodes-provided API keys by default. Partners may optionally provide their own keys (becoming direct processors). |
| **Anthropic PBC** | AI Model Inference (LLM) | Global / USA | ✅ Auto-executed on signup | LogicNodes-provided API keys by default. Partners may optionally provide their own keys (becoming direct processors). |
| **Google Cloud Platform** | AI Model Inference (Gemini API) | EU / Global | ✅ Auto-executed on signup | LogicNodes-provided API keys by default. Partners may optionally provide their own keys (becoming direct processors). |
| **xAI Corp.** | AI Model Inference (Grok API) | Global / USA | ✅ Auto-executed on signup | LogicNodes-provided API keys by default. Partners may optionally provide their own keys (becoming direct processors). |

---

## LLM Provider Data Handling

**Default Configuration:**
By default, LogicNodes provides API keys for LLM services (OpenAI, Anthropic, Google, xAI). In this configuration:
- LogicNodes is the **Data Processor** (on behalf of Partner, the Data Controller)
- LLM providers are **Sub-Processors** of LogicNodes
- LogicNodes maintains DPAs with all LLM providers
- LogicNodes disables provider-side training and retention where configurable
- All data processing is covered under LogicNodes' DPA with the Partner

**Optional: Partner-Provided API Keys**
Partners may choose to provide their own API keys for LLM services. In this configuration:
- Partner contracts directly with the LLM provider
- LLM provider becomes Partner's **Direct Processor** (not LogicNodes' sub-processor)
- Partner is responsible for their own DPA with the LLM provider
- Partners should review LLM provider privacy policies and enforce no-training, no-retention settings
- LogicNodes is not responsible for LLM provider data handling in this configuration

**Partner Control:**
Partners can specify which LLM provider(s) to use or disable LLM features entirely. This flexibility allows Partners to:
- Use LogicNodes-managed keys (default, covered under this sub-processor list)
- Provide their own keys (Partner's direct relationship with LLM provider)
- Disable specific LLM providers
- Use only EU-based providers (e.g., Google Cloud EU regions)

---

## Sub-Processor of Sub-Processors

Each sub-processor listed above may in turn engage their own sub-processors (for example, infrastructure or CDN providers).

**Examples:**
- **Supabase** uses AWS (Amazon Web Services) for infrastructure
- **Vercel** uses AWS and Google Cloud for edge network
- **Render** uses AWS and Google Cloud for infrastructure
- **Mailgun** uses various email delivery networks

These nested relationships are governed under the respective vendor's DPA, which LogicNodes ApS has reviewed and archived.

All major sub-processors maintain their own sub-processor lists:
- Supabase maintains transparency documentation for their infrastructure stack
- Vercel, Render, and Mailgun publish their own sub-processor lists
- LLM providers publish their infrastructure and data handling documentation

LogicNodes ApS monitors these relationships and maintains archived copies of all relevant agreements.

---

## Data Processing Agreements (DPAs)

**Our Commitments:**
- All sub-processors have executed DPAs with GDPR-compliant safeguards
- Standard Contractual Clauses (SCCs) are in place for all international transfers
- Sub-processors maintain appropriate security certifications and rely on certified infrastructure

**DPA Availability:**
Partners may request copies of archived DPAs by contacting:
- **Email:** privacy@logicnodes.ai
- **Response Time:** 5 business days

**What We Provide:**
- Copy of executed or auto-accepted DPA (with timestamp)
- Certification documentation (SOC 2 reports, ISO certificates)
- Sub-processor's own sub-processor list (where applicable)

---

## Data Location & Residency

**Default Configuration:**
- Primary data storage: **EU (AWS eu-north-1, Stockholm via Supabase)**
- Web hosting: **EU (Frankfurt via Vercel)**
- Backend services: **EU (Frankfurt via Render)**
- Email delivery: **EU/USA routing-dependent (via Mailgun)**

**US Data Residency:**
Available upon Partner request. Additional fees may apply. Contact sales@logicnodes.ai.

**LLM Processing:**
When partners configure LLM providers, data processing may occur in the provider's global infrastructure (typically USA for OpenAI, Anthropic, xAI; EU/Global for Google). Partners should review each provider's data residency options.

---

## Security & Compliance

All sub-processors meet or exceed LogicNodes' security requirements:

| Requirement | Status |
|-------------|--------|
| GDPR Compliance | ✅ All sub-processors |
| Standard Contractual Clauses (SCCs) | ✅ All international transfers |
| SOC 2 Type II | ✅ Mailgun, OpenAI, Anthropic, Google |
| ISO 27001 | ✅ Mailgun, Google, AWS (via Supabase) |
| EU-US Data Privacy Framework (DPF) | ✅ Render |
| HIPAA-Eligible Infrastructure | ✅ Mailgun, AWS (via Supabase), Google |
| Encryption at Rest (AES-256) | ✅ All data storage providers |
| Encryption in Transit (TLS 1.2+) | ✅ All sub-processors |

---

## Review & Verification Process

**Internal Governance:**
- LogicNodes reviews and re-verifies all sub-processor DPAs **at least annually**
- DPAs are re-reviewed whenever a vendor updates their legal terms
- All DPAs are timestamped and archived in our internal legal repository
- Security certifications (SOC 2, ISO 27001) are verified annually

**Last Full Review:** November 2025
**Next Scheduled Review:** May 2026

**Change Log:**
- **2025-11-04:** Initial publication with complete sub-processor list
- **2025-11-04:** Added LLM providers (OpenAI, Anthropic, Google, xAI)
- **2025-11-04:** Clarified EU data residency and routing

---

## Notification of Changes

**30-Day Advance Notice:**
LogicNodes ApS will update this page at least **30 days prior** to:
- Adding a new sub-processor
- Materially changing an existing sub-processor relationship
- Changing data processing locations

**Notification Method:**
1. Update this page with the change and effective date
2. Email notification to all active partners' security contacts
3. Version history tracked via GitHub Pages commit log

**Partner Objection Rights:**
Partners may object to new sub-processors on reasonable data protection grounds by notifying LogicNodes within 30 days. See your Data Processing Agreement (DPA) for full details.

**Monitoring This Page:**
- Subscribe to updates via RSS feed: [/subprocessors.xml](/subprocessors.xml)
- Monitor GitHub Pages commit history for version tracking
- Bookmark this page: [/en/subprocessors](/en/subprocessors)

---

## Related Documentation

**Core Legal Documents:**
- [Data Processing Agreement (DPA)](/en/data-processing-agreement.html) – GDPR Art. 28 compliant processor agreement
- [Privacy Policy (Partner Embedded)](/en/partner-privacy-policy.html) – Privacy policy for partner-embedded users
- [Responsible Disclosure Policy](/en/responsible-disclosure.html) – Security vulnerability reporting
- **Security Architecture** – Available on request (contact security@logicnodes.ai)

**Partner Resources:**
- [Partner Documentation](https://docs.logicnodes.ai/partners) – Integration guides and API documentation
- [Security Questionnaires](mailto:security@logicnodes.ai) – Request completed security assessments

---

## Contact Information

**Privacy & Compliance:**
- **Email:** privacy@logicnodes.ai
- **Response Time:** 5 business days

**Security Team:**
- **Email:** security@logicnodes.ai
- **PGP Key:** /en/pgp
- **Response Time:** 24 hours for critical issues

**Sales & Partnerships:**
- **Email:** sales@logicnodes.ai
- **Purpose:** DPA execution, custom agreements, US data residency requests

**Mailing Address:**
LogicNodes ApS
Sletvej 2D
8310 Tranbjerg
Denmark
CVR: DK45318362

---

## Appendix: Sub-Processor Contact Information

For direct inquiries to sub-processors regarding their data processing practices:

| Sub-Processor | Privacy Contact | DPA Information |
|---------------|-----------------|-----------------|
| Supabase Inc. | privacy@supabase.com | [Supabase Trust Center](https://supabase.com/security) |
| Vercel Inc. | privacy@vercel.com | [Vercel DPA](https://vercel.com/legal/dpa) |
| Render Inc. | privacy@render.com | [Render Security](https://render.com/security) |
| Mailgun / Sinch | privacy@mailgun.com | [Mailgun Privacy](https://www.mailgun.com/legal/privacy-policy/) |
| OpenAI LLC | privacy@openai.com | [OpenAI Privacy](https://openai.com/privacy/) |
| Anthropic PBC | privacy@anthropic.com | [Anthropic Privacy](https://www.anthropic.com/legal/privacy) |
| Google Cloud | cloud-privacy@google.com | [Google Cloud Privacy](https://cloud.google.com/privacy) |
| xAI Corp. | privacy@x.ai | [xAI Privacy](https://x.ai/privacy/) |

**Note:** Contact information is provided for reference only. All sub-processor relationships are managed by LogicNodes ApS. Partners should direct all inquiries to privacy@logicnodes.ai.

---

**Version:** 1.0
**Effective Date:** November 4, 2025
**Last Updated:** November 4, 2025

**© 2025 LogicNodes ApS. All rights reserved.**

This sub-processor list is maintained as part of LogicNodes' GDPR compliance obligations under Article 28(3)(d).
