---
layout: default
title: Home
lang: en
---

<div class="hero">
    <h2>Legal & Security Documentation</h2>
    <p>Comprehensive legal, privacy, and security information for users and partners</p>
    <div class="language-switch">
        <a href="{{ '/en/' | relative_url }}" class="active">English</a>
        <span class="separator">|</span>
        <a href="{{ '/da/' | relative_url }}">Dansk</a>
    </div>
</div>

<section class="docs-section">
    <h3 class="section-title">For End Users</h3>
    <div class="legal-docs">
        <div class="doc-card">
            <h2>Privacy Policy</h2>
            <p>Learn how we collect, use, and protect your personal information with our minimal data collection approach.</p>
            <a href="{{ '/en/privacy-policy.html' | relative_url }}" class="btn">Read Privacy Policy</a>
        </div>

        <div class="doc-card">
            <h2>Support</h2>
            <p>Get help with LogicNodes. Contact our support team for assistance with technical or account issues.</p>
            <a href="{{ '/en/support.html' | relative_url }}" class="btn">Contact Support</a>
        </div>
    </div>
</section>

<section class="docs-section">
    <h3 class="section-title">For Partners & Enterprise</h3>
    <div class="legal-docs">
        <div class="doc-card highlight">
            <div class="badge">Technical</div>
            <h2>Security Architecture</h2>
            <p>Comprehensive technical security documentation including authentication, multi-tenant isolation, encryption, and compliance status.</p>
            <a href="{{ '/en/security-architecture.html' | relative_url }}" class="btn">View Security Docs</a>
        </div>

        <div class="doc-card highlight">
            <div class="badge">Legal</div>
            <h2>Data Processing Agreement</h2>
            <p>GDPR Article 28 compliant DPA for partners processing EU personal data. Includes SCCs and sub-processor details.</p>
            <a href="{{ '/en/data-processing-agreement.html' | relative_url }}" class="btn">View DPA</a>
        </div>

        <div class="doc-card highlight">
            <div class="badge">Security</div>
            <h2>Responsible Disclosure</h2>
            <p>Security vulnerability reporting guidelines, safe harbor policy, and our responsible disclosure process.</p>
            <a href="{{ '/en/responsible-disclosure.html' | relative_url }}" class="btn">View Policy</a>
        </div>

        <div class="doc-card highlight">
            <div class="badge">Documentation</div>
            <h2>Partner Documentation Hub</h2>
            <p>Complete documentation index including integration guides, APIs, compliance resources, and FAQs.</p>
            <a href="{{ '/en/partner-docs.html' | relative_url }}" class="btn">Browse Docs</a>
        </div>
    </div>
</section>

<section class="quick-links">
    <h3>Quick Links by Role</h3>
    <div class="role-cards">
        <div class="role-card">
            <h4>🔒 Security Teams</h4>
            <ul>
                <li><a href="{{ '/en/security-architecture.html#authentication' | relative_url }}">Authentication & Authorization</a></li>
                <li><a href="{{ '/en/security-architecture.html#multi-tenant' | relative_url }}">Multi-tenant Isolation</a></li>
                <li><a href="{{ '/en/security-architecture.html#compliance' | relative_url }}">Compliance Status</a></li>
            </ul>
        </div>
        <div class="role-card">
            <h4>⚖️ Legal/Compliance</h4>
            <ul>
                <li><a href="{{ '/en/data-processing-agreement.html' | relative_url }}">Sign DPA (GDPR)</a></li>
                <li><a href="{{ '/en/privacy-policy.html' | relative_url }}">Privacy Policy</a></li>
                <li><a href="{{ '/en/security-architecture.html#compliance' | relative_url }}">Certifications</a></li>
            </ul>
        </div>
        <div class="role-card">
            <h4>👨‍💻 Developers</h4>
            <ul>
                <li><a href="{{ '/en/partner-docs.html#widget-integration' | relative_url }}">Widget Integration</a></li>
                <li><a href="{{ '/en/partner-docs.html#secret-management' | relative_url }}">Secret Management API</a></li>
                <li><a href="{{ '/en/partner-docs.html#best-practices' | relative_url }}">Security Best Practices</a></li>
            </ul>
        </div>
    </div>
</section>
