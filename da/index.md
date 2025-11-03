---
layout: default
title: Hjem
lang: da
---

<div class="hero">
    <h2>Juridisk & Sikkerhedsdokumentation</h2>
    <p>Omfattende juridisk, privatlivs- og sikkerhedsinformation for brugere og partnere</p>
    <div class="language-switch">
        <a href="{{ '/' | relative_url }}">English</a>
        <span class="separator">|</span>
        <a href="{{ '/da/' | relative_url }}" class="active">Dansk</a>
    </div>
</div>

<section class="docs-section">
    <h3 class="section-title">For Slutbrugere</h3>
    <div class="legal-docs">
        <div class="doc-card">
            <h2>Privatlivspolitik</h2>
            <p>Lær hvordan vi indsamler, bruger og beskytter dine personoplysninger med vores minimale dataindsamlingstilgang.</p>
            <a href="{{ '/da/privatlivspolitik.html' | relative_url }}" class="btn">Læs Privatlivspolitik</a>
        </div>

        <div class="doc-card">
            <h2>Support</h2>
            <p>Få hjælp med LogicNodes. Kontakt vores supportteam for assistance med tekniske eller kontorelaterede problemer.</p>
            <a href="{{ '/da/support.html' | relative_url }}" class="btn">Kontakt Support</a>
        </div>
    </div>
</section>

<section class="docs-section">
    <h3 class="section-title">For Partnere & Virksomheder</h3>
    <div class="legal-docs">
        <div class="doc-card highlight">
            <div class="badge">Teknisk</div>
            <h2>Sikkerhedsarkitektur</h2>
            <p>Omfattende teknisk sikkerhedsdokumentation inklusive autentificering, multi-tenant isolation, kryptering og compliance status.</p>
            <a href="{{ '/da/sikkerhedsarkitektur.html' | relative_url }}" class="btn">Se Sikkerhedsdokumentation</a>
        </div>

        <div class="doc-card highlight">
            <div class="badge">Juridisk</div>
            <h2>Databehandleraftale</h2>
            <p>DPA i overensstemmelse med GDPR Artikel 28 for partnere, der behandler EU-persondata. Inkluderer SCC'er og underbehandler-detaljer.</p>
            <a href="{{ '/da/databehandleraftale.html' | relative_url }}" class="btn">Se DPA</a>
        </div>

        <div class="doc-card highlight">
            <div class="badge">Sikkerhed</div>
            <h2>Ansvarlig Offentliggørelse</h2>
            <p>Retningslinjer for rapportering af sikkerhedssårbarheder, safe harbor-politik og vores ansvarlige offentliggørelsesproces.</p>
            <a href="{{ '/da/ansvarlig-offentliggorelse.html' | relative_url }}" class="btn">Se Politik</a>
        </div>

        <div class="doc-card highlight">
            <div class="badge">Dokumentation</div>
            <h2>Partner Dokumentationshub</h2>
            <p>Komplet dokumentationsindeks inklusive integrationsguides, API'er, compliance-ressourcer og FAQ'er.</p>
            <a href="{{ '/da/partner-dokumentation.html' | relative_url }}" class="btn">Gennemse Dokumentation</a>
        </div>
    </div>
</section>

<section class="quick-links">
    <h3>Hurtige Links efter Rolle</h3>
    <div class="role-cards">
        <div class="role-card">
            <h4>🔒 Sikkerhedsteams</h4>
            <ul>
                <li><a href="{{ '/da/sikkerhedsarkitektur.html#authentication' | relative_url }}">Autentificering & Autorisation</a></li>
                <li><a href="{{ '/da/sikkerhedsarkitektur.html#multi-tenant' | relative_url }}">Multi-tenant Isolation</a></li>
                <li><a href="{{ '/da/sikkerhedsarkitektur.html#compliance' | relative_url }}">Compliance Status</a></li>
            </ul>
        </div>
        <div class="role-card">
            <h4>⚖️ Juridisk/Compliance</h4>
            <ul>
                <li><a href="{{ '/da/databehandleraftale.html' | relative_url }}">Underskriv DPA (GDPR)</a></li>
                <li><a href="{{ '/da/privatlivspolitik.html' | relative_url }}">Privatlivspolitik</a></li>
                <li><a href="{{ '/da/sikkerhedsarkitektur.html#compliance' | relative_url }}">Certificeringer</a></li>
            </ul>
        </div>
        <div class="role-card">
            <h4>👨‍💻 Udviklere</h4>
            <ul>
                <li><a href="{{ '/da/partner-dokumentation.html#widget-integration' | relative_url }}">Widget Integration</a></li>
                <li><a href="{{ '/da/partner-dokumentation.html#secret-management' | relative_url }}">Secret Management API</a></li>
                <li><a href="{{ '/da/partner-dokumentation.html#best-practices' | relative_url }}">Bedste sikkerhedspraksis</a></li>
            </ul>
        </div>
    </div>
</section>
