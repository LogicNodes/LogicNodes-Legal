---
layout: legal
title: Underbehandlere
lang: da
lang_equivalent: /en/subprocessors
last_updated: 2026-04-23
description: "Komplet liste over tredjepartsunderbehandlere engageret af LogicNodes ApS til servicelevering. GDPR-kompatibel notifikationsside."
---

# LogicNodes – Autoriserede Underbehandlere

**Ikrafttrædelsesdato:** 23. april 2026
<p class="last-updated">Senest opdateret: {{ page.last_updated | date: "%B %-d, %Y" }}</p>

Denne side viser alle tredjepartsunderbehandlere engageret af **LogicNodes ApS** (CVR: DK45318362) i forbindelse med levering af LogicNodes-platformen og relaterede services.

Alle underbehandlere er bundet af en gyldig **Databehandleraftale (DPA)** med passende GDPR-sikkerhedsforanstaltninger (f.eks. standardkontraktbestemmelser, SOC 2, ISO 27001).

Kopier af alle underskrevne eller klikbaserede DPA'er opbevares internt og kan udleveres til partnere på anmodning.

---

## Primære Underbehandlere

<iframe src="https://docs.google.com/spreadsheets/d/e/2PACX-1vRHy76XGvurEqCuaIjMYAKlogtBJg4Maz1EOIptwtBQth89Vyaq3CM929kRdwEEf8mSbESwZrfnd9o7/pubhtml?gid=0&single=true" width="100%" height="550" frameborder="0" scrolling="no"></iframe>

### Hvad hver underbehandler bruges til

| Underbehandler | Service |
|---|---|
| **Supabase** | Database, brugergodkendelse og fillagring |
| **Vercel** | Hosting af webapplikation og edge-levering |
| **Hetzner** | Hosting af backend-API |
| **Mailgun** | Transaktionel e-maillevering |
| **ElevenLabs** | Tale-til-tekst transskription |
| **Pyannote** | Talaridentifikation (valgfrit; involverer biometriske data — GDPR Art. 9) |
| **OpenAI / Anthropic / Google / xAI** | AI-sprogmodelsinferens |

---

## LLM-udbyderes Datahåndtering

**Standardkonfiguration:**
Som standard leverer LogicNodes API-nøgler til LLM-services (OpenAI, Anthropic, Google, xAI). I denne konfiguration:
- LogicNodes er **Databehandler** (på vegne af Partner, den Dataansvarlige)
- LLM-udbydere er **Underbehandlere** af LogicNodes
- LogicNodes opretholder DPA'er med alle LLM-udbydere
- LogicNodes deaktiverer udbyderbaseret træning og lagring, hvor det er muligt at konfigurere
- Al databehandling er dækket under LogicNodes' DPA med Partneren

**Valgfrit: Partner-leverede API-nøgler**
Partnere kan vælge at levere egne API-nøgler til LLM-services. I denne konfiguration:
- Partneren indgår direkte aftale med LLM-udbyderen
- LLM-udbyderen bliver Partnerens **Direkte Databehandler** (ikke LogicNodes' underbehandler)
- Partneren er ansvarlig for sin egen DPA med LLM-udbyderen
- Partnere bør gennemgå LLM-udbydernes privatlivspolitikker og håndhæve indstillinger om ingen træning og ingen lagring
- LogicNodes er ikke ansvarlig for LLM-udbyderes datahåndtering i denne konfiguration

**Partnerkontrol:**
Partnere kan specificere hvilke LLM-udbydere der anvendes, eller deaktivere LLM-funktioner helt. Denne fleksibilitet giver Partnere mulighed for at:
- Anvende LogicNodes-administrerede nøgler (standard, dækket under denne underbehandlerliste)
- Levere egne nøgler (Partnerens direkte relation til LLM-udbyderen)
- Deaktivere specifikke LLM-udbydere
- Udelukkende anvende EU-baserede udbydere (f.eks. Google Cloud EU-regioner)

---

## Underbehandleres Underbehandlere

Hver underbehandler kan benytte egne infrastrukturudbydere til at levere deres tjeneste. Kendte eksempler:

| Underbehandler | Infrastruktur | Formål |
|---|---|---|
| Supabase | AWS (eu-north-1, Stockholm) | Administreret database og objektlagring |
| Vercel | AWS, Google Cloud | Edge-netværk og CDN-levering |
| Hetzner | Egne EU-datacentre (Falkenstein/Nürnberg) | Dedikeret serverinfrastruktur |
| Mailgun | Diverse e-mailleveringsnetværk | E-mailrouting og -levering |

Disse relationer er reguleret under den respektive leverandørs DPA og er offentligt dokumenteret på deres trust- og juridiske sider (se appendiks for links). DPA'en mellem LogicNodes ApS og den enkelte underbehandler dækker underbehandlerens brug af egne underbehandlere.

---

## Datalokalisering

**Standardkonfiguration:**
- Primær datalagring: **EU (AWS eu-north-1, Stockholm via Supabase)**
- Webhosting: **EU (Frankfurt via Vercel)**
- Backend-services: **EU (Falkenstein/Nürnberg via Hetzner)**
- E-maillevering: **EU/USA afhængigt af routing (via Mailgun)**

**Amerikansk datalokalisering:**
Tilgængelig på partneranmodning. Tillægsgebyrer kan forekomme. Kontakt kontakt@logicnodes.ai.

**LLM-behandling:**
Når partnere konfigurerer LLM-udbydere, kan databehandling finde sted i udbyderens globale infrastruktur (typisk USA for OpenAI, Anthropic, xAI; EU/globalt for Google). Partnere bør gennemgå den enkelte udbyders muligheder for datalokalitet.

---

## Sikkerhed & Compliance

Alle underbehandlere opfylder eller overstiger LogicNodes' sikkerhedskrav:

| Krav | Status |
|-------------|--------|
| GDPR-overensstemmelse | ✅ Alle underbehandlere |
| Standardkontraktbestemmelser (SCC'er) | ✅ Alle internationale overførsler |
| SOC 2 Type II | ✅ Mailgun, OpenAI, Anthropic, Google |
| ISO 27001 | ✅ Mailgun, Google, AWS (via Supabase) |
| EU-US Data Privacy Framework (DPF) | ✅ ElevenLabs |
| HIPAA-egnet infrastruktur | ✅ Mailgun, AWS (via Supabase), Google |
| Kryptering i hvile (AES-256) | ✅ Alle datalagerudbydere |
| Kryptering under overførsel (TLS 1.2+) | ✅ Alle underbehandlere |

---

## Gennemgangs- og Verificeringsproces

**Intern styring:**
- LogicNodes gennemgår og reverificerer alle underbehandleres DPA'er **mindst én gang årligt**
- DPA'er gennemgås på ny, når en leverandør opdaterer sine juridiske vilkår
- Alle DPA'er er tidsstemplede og arkiveret i vores interne juridiske register
- Sikkerhedscertificeringer (SOC 2, ISO 27001) verificeres årligt

**Seneste fuld gennemgang:** April 2026
**Næste planlagte gennemgang:** Oktober 2026

**Ændringslog:**
- **2025-11-04:** Første publikation med komplet underbehandlerliste
- **2025-11-04:** Tilføjet LLM-udbydere (OpenAI, Anthropic, Google, xAI)
- **2025-11-04:** Præciseret EU-datalokalisering og routing
- **2026-04-23:** Erstattet Render med Hetzner Online GmbH til backend-hosting
- **2026-04-23:** Tilføjet ElevenLabs Inc. (taletranskription) og Pyannote SAS (talaridentifikation)
- **2026-04-23:** Opdateret xAI enterprise-kontakt-e-mail

---

## Meddelelse om Ændringer

**30 dages forudgående varsel:**
LogicNodes ApS opdaterer denne side mindst **30 dage forud** for:
- Tilføjelse af en ny underbehandler
- Væsentlig ændring af en eksisterende underbehandlerrelation
- Ændring af databehandlingslokationer

**Underretningsmetode:**
1. Opdatering af denne side med ændringen og ikrafttrædelsesdatoen
2. E-mailunderretning til alle aktive partneres sikkerhedskontakter
3. Versionshistorik spores via GitHub Pages-commit-log

**Partnerens indsigelsesret:**
Partnere kan gøre indsigelse mod nye underbehandlere på rimelige databeskyttelsesgrunde ved at underrette LogicNodes inden for 30 dage. Se din Databehandleraftale (DPA) for fulde detaljer.

**Overvågning af denne side:**
- Bogmærk denne side: [/da/underbehandlere](/da/underbehandlere)
- Overvåg GitHub Pages-commit-historik for versionssporing

---

## Relateret Dokumentation

**Centrale juridiske dokumenter:**
- [Databehandleraftale (DPA)](/da/databehandleraftale/) – GDPR Art. 28-kompatibel databehandleraftale
- [Partner Privatlivspolitik](/da/partner-privatlivspolitik/) – Privatlivspolitik for partner-indlejrede brugere
- [Ansvarlig Offentliggørelse](/da/ansvarlig-offentliggorelse/) – Retningslinjer for sikkerhedssårbarhedsrapportering
- **Sikkerhedsarkitektur** – Tilgængelig på anmodning (kontakt kontakt@logicnodes.ai)

**Partnerressourcer:**
- [Partnerdokumentation](https://docs.logicnodes.ai/partners) – Integrationsvejledninger og API-dokumentation
- [Sikkerhedsspørgeskemaer](mailto:kontakt@logicnodes.ai) – Anmod om udfyldte sikkerhedsvurderinger

---

## Kontaktoplysninger

**Privatliv & Compliance:**
- **E-mail:** kontakt@logicnodes.ai
- **Svartid:** 5 arbejdsdage

**Sikkerhedsteam:**
- **E-mail:** kontakt@logicnodes.ai
- **PGP-nøgle:** /en/pgp
- **Svartid:** 24 timer for kritiske problemer

**Salg & Partnerskaber:**
- **E-mail:** kontakt@logicnodes.ai
- **Formål:** DPA-eksekvering, tilpassede aftaler, anmodninger om amerikansk datalokalisering

**Postadresse:**
LogicNodes ApS
Sletvej 2D
8310 Tranbjerg
Danmark
CVR: DK45318362

---

## Appendiks: Underbehandleres Kontaktoplysninger

Til direkte henvendelser til underbehandlere vedrørende deres databehandlingspraksis:

| Underbehandler | Privatlivskontakt | DPA-information |
|---------------|-----------------|-----------------|
| Supabase Inc. | privacy@supabase.com | [Supabase Trust Center](https://supabase.com/security) |
| Vercel Inc. | privacy@vercel.com | [Vercel DPA](https://vercel.com/legal/dpa) |
| Hetzner Online GmbH | datenschutz@hetzner.com | [Hetzner Privatliv](https://www.hetzner.com/legal/privacy-policy/) |
| Mailgun / Sinch | privacy@mailgun.com | [Mailgun Privatliv](https://www.mailgun.com/legal/privacy-policy/) |
| OpenAI LLC | privacy@openai.com | [OpenAI Privatliv](https://openai.com/privacy/) |
| Anthropic PBC | privacy@anthropic.com | [Anthropic Privatliv](https://www.anthropic.com/legal/privacy) |
| Google Cloud | cloud-privacy@google.com | [Google Cloud Privatliv](https://cloud.google.com/privacy) |
| xAI Corp. | privacy+enterprise@x.ai | [xAI Privatliv](https://x.ai/privacy/) |
| ElevenLabs Inc. | legal@elevenlabs.io | [ElevenLabs Trust Center](https://compliance.elevenlabs.io/) |
| Pyannote SAS | support@pyannote.ai | [PyAnnoteAI](https://pyannote.ai/) |

**Bemærk:** Kontaktoplysninger er alene til reference. Alle underbehandlerrelationer administreres af LogicNodes ApS. Partnere bør rette alle henvendelser til kontakt@logicnodes.ai.

---

**Version:** 1.1
**Ikrafttrædelsesdato:** 23. april 2026
**Sidst opdateret:** 23. april 2026

**© 2025 LogicNodes ApS. Alle rettigheder forbeholdes.**

Denne underbehandlerliste opretholdes som en del af LogicNodes' GDPR-overholdelseforpligtelser i henhold til Artikel 28(3)(d).
