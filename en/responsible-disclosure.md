---
layout: legal
title: Responsible Disclosure Policy
last_updated: 2025-11-03
lang: en
---

# LogicNodes - Responsible Disclosure Policy

**Effective Date:** November 3, 2025  

**Last Updated:** November 3, 2025  

**Version:** 1.0  

---

## 1. Introduction

LogicNodes is committed to protecting the security and privacy of our partners and their users. We welcome and appreciate responsible disclosure of security vulnerabilities from the security research community.

This policy provides guidelines for security researchers to report vulnerabilities responsibly and outlines how LogicNodes will respond.

---

## 2. Scope

### 2.1 In-Scope Systems

Security researchers are authorized to test the following systems:

**Production Environment:**
- ✅ **Web Application:** https://app.logicnodes.ai
- ✅ **API Endpoints:** https://api.logicnodes.ai/api/v1/*
- ✅ **Embed Authentication:** POST /api/v1/embed/auth
- ✅ **Partner APIs:** /api/v1/partner/*
- ✅ **Organization APIs:** /api/organizations/*

**Testing Environment:**
- ✅ **Staging:** https://staging.logicnodes.ai (if available)
- ✅ **Demo accounts:** Request via security@logicnodes.ai

### 2.2 Out-of-Scope Systems

The following are **NOT authorized** for testing:

- ❌ Third-party services (Supabase, AWS, Mailgun - report to them directly)
- ❌ Physical security (offices, data centers)
- ❌ Social engineering (phishing, vishing)
- ❌ Denial of Service (DoS/DDoS attacks)
- ❌ Spam or bulk email testing
- ❌ Other customers' accounts or data (unless you own them)

---

## 3. In-Scope Vulnerabilities

We are interested in reports of the following vulnerability types:

### 3.1 Critical Severity

- **Authentication Bypass** - Access system without valid credentials
- **Authorization Bypass** - Access other organizations' data (cross-tenant data leak)
- **Remote Code Execution (RCE)** - Execute arbitrary code on our servers
- **SQL Injection** - Inject SQL queries to access/modify database
- **Secret Exposure** - Unauthorized access to API keys, signing secrets, vault secrets

**Examples:**
- Bypass JWT validation to create unauthorized sessions
- Access organization A's agent runs from organization B
- Extract partner signing secrets from Vault without authorization
- Execute arbitrary SQL via API endpoints

### 3.2 High Severity

- **Cross-Site Scripting (XSS)** - Reflected, Stored, DOM-based
- **Cross-Site Request Forgery (CSRF)** - Force authenticated users to perform actions
- **Insecure Direct Object References (IDOR)** - Access resources without authorization
- **Server-Side Request Forgery (SSRF)** - Force server to make unauthorized requests
- **XML External Entity (XXE)** - Process malicious XML to access files/systems

**Examples:**
- Store malicious script in agent run logs (visible to other users)
- Delete organization via CSRF attack
- Access other users' transcriptions via IDOR (manipulate UUID)

### 3.3 Medium Severity

- **Privilege Escalation** - Gain higher privileges than authorized (member → admin)
- **Information Disclosure** - Expose sensitive information (stack traces, config, internal IPs)
- **Weak Cryptography** - Use of weak algorithms, insufficient key lengths
- **Session Management Issues** - Session fixation, insecure session storage
- **Subdomain Takeover** - Take control of unused subdomains

**Examples:**
- Member role can delete organization (should require admin)
- Error messages expose database connection strings
- Session tokens do not expire after logout

### 3.4 Low Severity

- **Missing Security Headers** - HSTS, CSP, X-Frame-Options
- **Clickjacking** - Embed application in iframe without X-Frame-Options
- **Open Redirects** - Redirect users to malicious sites
- **Verbose Error Messages** - Expose software versions, internal paths
- **HTTP Security Issues** - Mixed content, insecure cookies

**Note:** Low severity issues are still valuable reports and will be addressed.

---

## 4. Out-of-Scope Vulnerabilities

The following are **NOT eligible** for acknowledgment or rewards:

### 4.1 Excluded Vulnerability Types

- ❌ **Denial of Service (DoS/DDoS)** - Overwhelming systems with traffic
- ❌ **Brute Force Attacks** - Attempting many passwords/API keys
- ❌ **Social Engineering** - Phishing, pretexting, vishing
- ❌ **Physical Attacks** - Office intrusion, dumpster diving
- ❌ **Email Spoofing** - SPF/DKIM/DMARC misconfigurations (unless leads to account compromise)
- ❌ **Rate Limiting** - Absence of rate limiting (unless causes DoS)
- ❌ **Version Disclosure** - Software version in headers (informational only)

### 4.2 Known Issues

The following are known and will not be addressed immediately:

- ⚠️ **Bug Bounty Program:** Not yet implemented (planned for 2026)
- ⚠️ **SOC 2 Certification:** In progress (estimated 2026)
- ⚠️ **Forced Logout:** Not yet available (sessions expire in 1 hour)

---

## 5. Responsible Disclosure Guidelines

### 5.1 Testing Rules

When testing for vulnerabilities, researchers must:

**DO:**
- ✅ Test only on your own accounts or with explicit permission
- ✅ Use test/demo accounts (request via security@logicnodes.ai)
- ✅ Limit testing to non-destructive methods
- ✅ Respect rate limits (stay below 100 requests/minute)
- ✅ Stop testing immediately if you discover user data
- ✅ Report findings promptly (within 24 hours of discovery)

**DON'T:**
- ❌ Access, modify, or delete other users' data
- ❌ Perform DoS/DDoS attacks or load testing
- ❌ Use automated scanners without prior approval (email security@logicnodes.ai)
- ❌ Exploit vulnerabilities beyond proof-of-concept
- ❌ Publicly disclose vulnerabilities before remediation (90-day embargo)
- ❌ Demand payment or ransom for vulnerability disclosure

### 5.2 Safe Harbor

LogicNodes commits to:

- ✅ **Not pursue legal action** against researchers who comply with this policy
- ✅ **Work with you** to understand and resolve the issue
- ✅ **Recognize your contribution** (with your permission)
- ✅ **Keep your identity confidential** (if requested)

**Conditions:**
- You must comply with this policy (testing rules, disclosure timeline)
- You must make a good faith effort to avoid harm
- You must not violate any laws in your jurisdiction

**Disclaimer:** This safe harbor does not grant permission to violate third-party terms of service (e.g., Supabase, AWS). You are responsible for compliance with all applicable laws and terms.

---

## 6. Reporting a Vulnerability

### 6.1 How to Report

**Primary Contact:**
- **Email:** security@logicnodes.ai
- **PGP Key:** Available upon request (email security@logicnodes.ai to request)
- **Response Time:** Within 24 hours (acknowledgment), 72 hours (initial assessment)

### 6.2 Report Format

Please include the following information:

**Required:**
1. **Vulnerability Type** (e.g., SQL Injection, XSS, Authorization Bypass)
2. **Affected System** (URL, API endpoint, component)
3. **Severity Assessment** (Critical, High, Medium, Low - your opinion)
4. **Steps to Reproduce** (detailed, numbered steps)
5. **Proof of Concept** (screenshots, code, HTTP requests)

**Optional:**
6. **Impact Assessment** (what an attacker could achieve)
7. **Suggested Remediation** (how to fix the issue)
8. **Your Name/Handle** (if you want credit)
9. **Disclosure Timeline** (if you have specific requirements)

**Example Report:**

```
Subject: [SECURITY] SQL Injection in /api/organizations/{org_id}/runs

Vulnerability Type: SQL Injection
Affected System: POST /api/organizations/{org_id}/runs
Severity: Critical

Steps to Reproduce:
1. Authenticate as organization member (POST /api/v1/embed/auth)
2. Send POST request to /api/organizations/{org_id}/runs with payload:
   {
     "filter": "status = 'completed' OR 1=1 --"
   }
3. Observe that all runs are returned (not just own organization)

Proof of Concept:
[Screenshot showing SQL query in error message]
[curl command to reproduce]

Impact:
Attacker can access all organizations' agent runs, bypassing RLS policies.

Suggested Remediation:
Use parameterized queries instead of string concatenation.

Reporter: John Doe (john@example.com)
Disclosure: 90 days (standard)
```

### 6.3 Encrypted Reporting (Optional)

For sensitive vulnerabilities, you may encrypt your report using PGP:

1. Request PGP key: security@logicnodes.ai
2. Encrypt report with our public key
3. Send encrypted email to security@logicnodes.ai

**Note:** PGP is optional. Unencrypted email to security@logicnodes.ai is acceptable.

---

## 7. Response Process

### 7.1 Timeline

**Within 24 Hours:**
- ✅ Acknowledgment email (confirming receipt)
- ✅ Ticket number assigned (for tracking)
- ✅ Initial questions (if clarification needed)

**Within 72 Hours:**
- ✅ Severity assessment (our internal classification)
- ✅ Validation (confirm vulnerability is reproducible)
- ✅ Remediation timeline (estimated fix date)

**Within 90 Days:**
- ✅ Remediation deployed (critical/high issues prioritized)
- ✅ Verification testing (confirm fix works)
- ✅ Public disclosure (if agreed upon)

### 7.2 Severity Classification

LogicNodes uses the following severity levels:

**Critical (P0):**
- Impact: Full system compromise, mass data breach
- Remediation: Within 24 hours
- Examples: RCE, authentication bypass, cross-tenant data leak

**High (P1):**
- Impact: Significant data exposure, privilege escalation
- Remediation: Within 7 days
- Examples: SQL injection, stored XSS, authorization bypass

**Medium (P2):**
- Impact: Limited data exposure, functionality compromise
- Remediation: Within 30 days
- Examples: Reflected XSS, IDOR, session management issues

**Low (P3):**
- Impact: Minimal security risk, defense-in-depth
- Remediation: Within 90 days
- Examples: Missing security headers, verbose errors

**Informational:**
- Impact: No immediate security risk
- Remediation: Backlog (no specific timeline)
- Examples: Version disclosure, minor configuration issues

### 7.3 Communication

**During Investigation:**
- We may ask follow-up questions to understand the issue
- We will keep you updated on remediation progress (weekly updates for critical/high)

**After Remediation:**
- We will notify you when the fix is deployed
- We will ask for verification (optional - you can re-test)

**Public Disclosure:**
- We prefer 90-day embargo before public disclosure
- We will coordinate disclosure with you (blog post, CVE, advisory)
- With your permission, we will credit you (name, handle, company)

---

## 8. Recognition & Rewards

### 8.1 Public Acknowledgment

Researchers who report valid vulnerabilities will be credited on our Security Hall of Fame (with permission):

**URL:** https://logicnodes.ai/security/hall-of-fame (coming soon)

**Information Published:**
- Name or handle (your choice)
- Company/Organization (optional)
- Vulnerability type (general description, no exploit details)
- Month/Year of disclosure

**Opt-Out:** If you prefer to remain anonymous, please indicate in your report.

### 8.2 Rewards

**Current Status:** No bug bounty program (planned for 2026)

**Future Plans:**
- Launch bug bounty program on HackerOne or Bugcrowd
- Rewards: $500 - $5,000 depending on severity
- Estimated launch: Q2 2026

**Current Recognition:**
- Public acknowledgment (with permission)
- Direct communication with engineering team
- Priority support channel (for severe issues)

---

## 9. Legal & Compliance

### 9.1 Safe Harbor (Expanded)

LogicNodes will not initiate legal action against researchers who:

1. **Comply with this policy** (testing rules, disclosure timeline)
2. **Make good faith effort to avoid harm** (no data theft, DoS, privacy violations)
3. **Report vulnerabilities promptly** (within 24 hours of discovery)
4. **Do not publicly disclose** (before 90-day embargo or mutual agreement)

**What Safe Harbor Covers:**
- Accessing systems in scope for testing purposes
- Creating test accounts for vulnerability research
- Viewing your own data or publicly accessible data

**What Safe Harbor Does NOT Cover:**
- Accessing other users' data (even if technically possible)
- Causing damage or disruption (DoS, data deletion)
- Violating third-party terms of service (Supabase, AWS)
- Using vulnerabilities for personal gain (theft, fraud)

### 9.2 Disclosure Timeline

**Standard Embargo:** 90 days from initial report

**Early Disclosure (with mutual agreement):**
- If fix is deployed and verified within 30 days, we may agree to earlier disclosure
- Coordinated disclosure (same day blog post, CVE, advisory)

**Extended Embargo:**
- For complex issues requiring architectural changes, we may request extension
- Maximum extension: 180 days (with researcher consent)

**Public Disclosure After 90 Days:**
- If LogicNodes has not remediated within 90 days, researcher may publicly disclose
- We request 7-day notice before public disclosure (to warn affected parties)

### 9.3 CVE Assignment

For vulnerabilities meeting CVE criteria:
- LogicNodes will request CVE from MITRE or GitHub Security Advisories
- CVE will credit reporter (with permission)
- LogicNodes will publish advisory on https://logicnodes.ai/security/advisories

---

## 10. Excluded Parties

The following parties are **NOT eligible** to participate:

- ❌ LogicNodes employees, contractors, or immediate family members
- ❌ Individuals in countries subject to U.S. sanctions (Iran, North Korea, Syria, Cuba, Crimea)
- ❌ Individuals on U.S. denied persons lists (OFAC SDN, BIS Denied Persons List)
- ❌ Minors under 18 years old (without parental consent)

---

## 11. Modifications to This Policy

LogicNodes may update this policy at any time. Changes will be posted at:
**URL:** https://logicnodes.ai/security/responsible-disclosure

**Notification:**
- Material changes: Announced via blog post, email to past reporters
- Minor changes: Updated "Last Updated" date

**Effective Date:**
- Policy changes effective immediately upon posting
- Existing vulnerability reports governed by policy version at time of report

---

## 12. Frequently Asked Questions

### 12.1 General

**Q: Do you have a bug bounty program?**
A: Not yet. Planned for Q2 2026 on HackerOne or Bugcrowd. Currently, we offer public acknowledgment and gratitude.

**Q: Can I use automated scanners?**
A: Please request permission first (security@logicnodes.ai). Automated scanners may trigger rate limits or DoS protections.

**Q: Can I test on production systems?**
A: Yes, but only on your own accounts. Request test accounts via security@logicnodes.ai for safer testing.

**Q: Can I disclose before 90 days?**
A: Only with mutual agreement. We prefer coordinated disclosure.

### 12.2 Scope

**Q: Is subdomain takeover in scope?**
A: Yes, if you can demonstrate impact (e.g., phishing, cookie theft).

**Q: Is rate limiting absence a valid report?**
A: Only if it enables DoS or brute force attacks. Missing rate limits alone are informational.

**Q: Are third-party dependencies in scope?**
A: Yes, if the vulnerability affects LogicNodes (e.g., outdated library with known CVE). Report to us and the vendor.

**Q: Is social engineering in scope?**
A: No. Do not phish employees, partners, or users.

### 12.3 Reporting

**Q: Can I report anonymously?**
A: Yes. Use ProtonMail or Tutanota for anonymous email. We will keep your identity confidential.

**Q: Can I report via Twitter/LinkedIn?**
A: Please use security@logicnodes.ai for all reports. Social media is not monitored for security reports.

**Q: What if my report is a duplicate?**
A: We will notify you if the issue was previously reported. Duplicates still receive acknowledgment (but no additional credit).

**Q: Can I report issues in third-party services?**
A: Report to the third party (Supabase, AWS, Mailgun) directly. If the issue affects LogicNodes' configuration, report to us as well.

### 12.4 Rewards

**Q: Will I be paid for my report?**
A: Not currently (no bug bounty program). You will receive public acknowledgment and our gratitude.

**Q: When will bug bounty launch?**
A: Estimated Q2 2026, pending revenue milestones.

**Q: Can I negotiate a reward?**
A: For exceptional findings (0-day, critical severity), contact security@logicnodes.ai to discuss.

---

## 13. Contact Information

### Security Team
**Email:** security@logicnodes.ai
**PGP Key:** Request via email
**Response Time:** Within 24 hours

### General Inquiries
**Email:** support@logicnodes.ai
**Purpose:** Non-security questions, product support

### Legal Department
**Email:** legal@logicnodes.ai
**Purpose:** Safe harbor questions, legal concerns

---

## 14. Acknowledgments

LogicNodes thanks the security research community for helping us protect our partners and their users. We are grateful for your responsible disclosure and collaboration.

**Special Thanks:**
- [Future: List of acknowledged researchers]

---

## 15. References

**Industry Standards:**
- **OWASP Top 10:** https://owasp.org/www-project-top-ten/
- **CWE (Common Weakness Enumeration):** https://cwe.mitre.org/
- **CVSS (Common Vulnerability Scoring System):** https://www.first.org/cvss/

**Disclosure Policies (Inspiration):**
- **Google VRP:** https://bughunters.google.com/
- **Microsoft MSRC:** https://www.microsoft.com/en-us/msrc
- **GitHub Security:** https://bounty.github.com/

**Responsible Disclosure Frameworks:**
- **ISO 29147:** Vulnerability disclosure
- **ISO 30111:** Vulnerability handling processes

---

**© 2025 LogicNodes Inc. All rights reserved.**

This Responsible Disclosure Policy is effective November 3, 2025. By submitting a vulnerability report, you agree to the terms of this policy.
