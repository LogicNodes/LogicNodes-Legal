---
layout: legal
title: Sub-Processor List
last_updated: 2026-04-23
lang: en
lang_equivalent: /da/underbehandlere
description: "Complete list of third-party sub-processors engaged by LogicNodes ApS for service delivery. GDPR-compliant notification page."
---

# LogicNodes – Authorized Sub-Processors

**Effective Date:** April 23, 2026
<p class="last-updated">Last Updated: {{ page.last_updated | date: "%B %-d, %Y" }}</p>

This page lists all third-party sub-processors engaged by **LogicNodes ApS** (CVR: DK45318362) in connection with providing the LogicNodes platform and related services.

Each sub-processor is bound by a valid **Data Processing Agreement (DPA)** that includes appropriate GDPR safeguards (e.g., Standard Contractual Clauses, SOC 2, ISO 27001).

Copies of all executed or click-through DPAs are maintained internally and can be provided to partners upon request.

---

## Primary Sub-Processors

<iframe src="https://docs.google.com/spreadsheets/d/e/2PACX-1vRHy76XGvurEqCuaIjMYAKlogtBJg4Maz1EOIptwtBQth89Vyaq3CM929kRdwEEf8mSbESwZrfnd9o7/pubhtml?gid=0&single=true" width="100%" height="550" frameborder="0" scrolling="no"></iframe>

### What Each Sub-Processor Does

| Sub-Processor | Service |
|---|---|
| **Supabase** | Database, authentication, and file storage |
| **Vercel** | Web application hosting and edge delivery |
| **Hetzner** | Backend API hosting |
| **Mailgun** | Transactional email delivery |
| **ElevenLabs** | Speech-to-text transcription |
| **Pyannote** | Speaker identification (optional; involves biometric data — GDPR Art. 9) |
| **OpenAI / Anthropic / Google / xAI** | AI language model inference |

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

Each sub-processor may use their own infrastructure providers to deliver their service. Known examples:

| Sub-Processor | Infrastructure | Purpose |
|---|---|---|
| Supabase | AWS (eu-north-1, Stockholm) | Managed database and object storage |
| Vercel | AWS, Google Cloud | Edge network and CDN delivery |
| Hetzner | Own EU data centres (Falkenstein/Nuremberg) | Dedicated server infrastructure |
| Mailgun | Various email delivery networks | Email routing and delivery |

These relationships are governed under each vendor's own DPA and are publicly documented on their trust and legal pages (see the appendix for links). The DPA between LogicNodes ApS and each sub-processor covers that sub-processor's use of its own sub-processors.

---

## Data Location & Residency

**Default Configuration:**
- Primary data storage: **EU (AWS eu-north-1, Stockholm via Supabase)**
- Web hosting: **EU (Frankfurt via Vercel)**
- Backend services: **EU (Falkenstein/Nuremberg via Hetzner)**
- Email delivery: **EU/USA routing-dependent (via Mailgun)**

**US Data Residency:**
Available upon Partner request. Additional fees may apply. Contact kontakt@logicnodes.ai.

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
| EU-US Data Privacy Framework (DPF) | ✅ ElevenLabs |
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

**Last Full Review:** April 2026
**Next Scheduled Review:** October 2026

**Change Log:**
- **2025-11-04:** Initial publication with complete sub-processor list
- **2025-11-04:** Added LLM providers (OpenAI, Anthropic, Google, xAI)
- **2025-11-04:** Clarified EU data residency and routing
- **2026-04-23:** Replaced Render with Hetzner Online GmbH for backend hosting
- **2026-04-23:** Added ElevenLabs Inc. (speech transcription) and Pyannote SAS (speaker identification)
- **2026-04-23:** Updated xAI enterprise contact email

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
- [Data Processing Agreement (DPA)](/en/data-processing-agreement/) – GDPR Art. 28 compliant processor agreement
- [Privacy Policy (Partner Embedded)](/en/partner-privacy-policy/) – Privacy policy for partner-embedded users
- [Responsible Disclosure Policy](/en/responsible-disclosure/) – Security vulnerability reporting
- **Security Architecture** – Available on request (contact kontakt@logicnodes.ai)

**Partner Resources:**
- [Partner Documentation](https://docs.logicnodes.ai/partners) – Integration guides and API documentation
- [Security Questionnaires](mailto:kontakt@logicnodes.ai) – Request completed security assessments

---

## Contact Information

**Privacy & Compliance:**
- **Email:** kontakt@logicnodes.ai
- **Response Time:** 5 business days

**Security Team:**
- **Email:** kontakt@logicnodes.ai
- **PGP Key:** /en/pgp
- **Response Time:** 24 hours for critical issues

**Sales & Partnerships:**
- **Email:** kontakt@logicnodes.ai
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
| Hetzner Online GmbH | datenschutz@hetzner.com | [Hetzner Privacy](https://www.hetzner.com/legal/privacy-policy/) |
| Mailgun / Sinch | privacy@mailgun.com | [Mailgun Privacy](https://www.mailgun.com/legal/privacy-policy/) |
| OpenAI LLC | privacy@openai.com | [OpenAI Privacy](https://openai.com/privacy/) |
| Anthropic PBC | privacy@anthropic.com | [Anthropic Privacy](https://www.anthropic.com/legal/privacy) |
| Google Cloud | cloud-privacy@google.com | [Google Cloud Privacy](https://cloud.google.com/privacy) |
| xAI Corp. | privacy+enterprise@x.ai | [xAI Privacy](https://x.ai/privacy/) |
| ElevenLabs Inc. | legal@elevenlabs.io | [ElevenLabs Trust Center](https://compliance.elevenlabs.io/) |
| Pyannote SAS | support@pyannote.ai | [PyAnnoteAI](https://pyannote.ai/) |

**Note:** Contact information is provided for reference only. All sub-processor relationships are managed by LogicNodes ApS. Partners should direct all inquiries to kontakt@logicnodes.ai.

---

**Version:** 1.1
**Effective Date:** April 23, 2026
**Last Updated:** April 23, 2026

**© 2025 LogicNodes ApS. All rights reserved.**

This sub-processor list is maintained as part of LogicNodes' GDPR compliance obligations under Article 28(3)(d).
