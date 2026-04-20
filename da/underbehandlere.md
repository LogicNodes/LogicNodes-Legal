---
layout: legal
title: Underbehandlere
lang: da
lang_equivalent: /en/subprocessors
last_updated: 2025-11-04
description: "Komplet liste over tredjepartsunderbehandlere engageret af LogicNodes ApS til servicelevering. GDPR-kompatibel notifikationsside."
---

# LogicNodes – Autoriserede Underbehandlere

**Ikrafttrædelsesdato:** 4. november 2025
<p class="last-updated">Senest opdateret: {{ page.last_updated | date: "%B %-d, %Y" }}</p>

Denne side viser alle tredjepartsunderbehandlere engageret af **LogicNodes ApS** (CVR: DK45318362) i forbindelse med levering af LogicNodes-platformen og relaterede services.

Alle underbehandlere er bundet af en gyldig **Databehandleraftale (DPA)** med passende GDPR-sikkerhedsforanstaltninger (f.eks. standardkontraktbestemmelser, SOC 2, ISO 27001).

Kopier af alle underskrevne eller klikbaserede DPA'er opbevares internt og kan udleveres til partnere på anmodning.

---

## Primære Underbehandlere

| Underbehandler | Service | Primær Region | DPA-status | Bemærkninger |
|----------------|----------|---------|-------------|--------|
| **Supabase Inc.** | Database, Autentificering, Lagring | EU (eu-north-1 – Stockholm) | ✅ Underskrevet | Central databaseinfrastrukturleverandør. Supabase kan engagere AWS og andre infrastrukturleverandører under sin egen DPA. |
| **Vercel Inc.** | Web & Edge Hosting for Frontend-services | EU (Frankfurt) | ✅ Auto-accepteret ved tilmelding | Bruges til hosting af webaktiver og edge-funktioner. |
| **Render Inc.** | Backend Hosting & API'er | EU (Frankfurt) | ✅ Auto-accepteret ved tilmelding | Bruges til applikationsservere og planlagte opgaver. |
| **Sinch / Mailgun Technologies Inc.** | Transaktionel e-maillevering | EU (Tyskland) / USA | ✅ Auto-accepteret ved tilmelding | Bruges til systemnotifikationer og transaktionel e-mail. Routing er regionsafhængig. |
| **OpenAI LLC** | AI-modelinferens (LLM) | Global / USA | ✅ Auto-accepteret ved tilmelding | LogicNodes-leverede API-nøgler som standard. Partnere kan valgfrit levere egne nøgler (og dermed blive direkte databehandlere). |
| **Anthropic PBC** | AI-modelinferens (LLM) | Global / USA | ✅ Auto-accepteret ved tilmelding | LogicNodes-leverede API-nøgler som standard. Partnere kan valgfrit levere egne nøgler. |
| **Google Cloud Platform** | AI-modelinferens (Gemini API) | EU / Global | ✅ Auto-accepteret ved tilmelding | LogicNodes-leverede API-nøgler som standard. Partnere kan valgfrit levere egne nøgler. |
| **xAI Corp.** | AI-modelinferens (Grok API) | Global / USA | ✅ Auto-accepteret ved tilmelding | LogicNodes-leverede API-nøgler som standard. Partnere kan valgfrit levere egne nøgler. |

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
Partnere kan specificere hvilke LLM-udbydere der anvendes, eller deaktivere LLM-funktioner helt.

---

## Underbehandleres Underbehandlere

Hver underbehandler oplistet ovenfor kan selv engagere egne underbehandlere (f.eks. infrastruktur- eller CDN-udbydere).

**Eksempler:**
- **Supabase** bruger AWS (Amazon Web Services) til infrastruktur
- **Vercel** bruger AWS og Google Cloud til edge-netværk
- **Render** bruger AWS og Google Cloud til infrastruktur
- **Mailgun** bruger diverse e-mailleveringsnetværk

Disse indlejrede relationer er reguleret under den respektive leverandørs DPA, som LogicNodes ApS har gennemgået og arkiveret.

---

## Databehandleraftaler (DPA'er)

**Vores forpligtelser:**
- Alle underbehandlere har underskrevet DPA'er med GDPR-kompatible sikkerhedsforanstaltninger
- Standardkontraktbestemmelser (SCC'er) er på plads for alle internationale overførsler
- Underbehandlere opretholder passende sikkerhedscertificeringer

**DPA-tilgængelighed:**
Partnere kan anmode om kopier af arkiverede DPA'er ved at kontakte:
- **E-mail:** kontakt@logicnodes.ai
- **Svartid:** 5 arbejdsdage

---

## Datalokalisering

**Standardkonfiguration:**
- Primær datalagring: **EU (AWS eu-north-1, Stockholm via Supabase)**
- Webhosting: **EU (Frankfurt via Vercel)**
- Backend-services: **EU (Frankfurt via Render)**
- E-maillevering: **EU/USA afhængigt af routing (via Mailgun)**

**Amerikansk datalokalisering:**
Tilgængelig på partneranmodning. Tillægsgebyrer kan forekomme. Kontakt kontakt@logicnodes.ai.

---

## Sikkerhed & Compliance

| Krav | Status |
|-------------|--------|
| GDPR-overensstemmelse | ✅ Alle underbehandlere |
| Standardkontraktbestemmelser (SCC'er) | ✅ Alle internationale overførsler |
| SOC 2 Type II | ✅ Mailgun, OpenAI, Anthropic, Google |
| ISO 27001 | ✅ Mailgun, Google, AWS (via Supabase) |
| EU-US Data Privacy Framework (DPF) | ✅ Render |
| Kryptering i hvile (AES-256) | ✅ Alle datalagerudbydere |
| Kryptering under overførsel (TLS 1.2+) | ✅ Alle underbehandlere |

---

## Meddelelse om Ændringer

**30 dages forudgående varsel:**
LogicNodes ApS opdaterer denne side mindst **30 dage forud** for:
- Tilføjelse af en ny underbehandler
- Væsentlig ændring af en eksisterende underbehandlerrelation
- Ændring af databehandlingslokationer

**Partnerens indsigelsesret:**
Partnere kan gøre indsigelse mod nye underbehandlere på rimelige databeskyttelsesgrunde ved at underrette LogicNodes inden for 30 dage. Se din Databehandleraftale (DPA) for fulde detaljer.

---

## Relateret Dokumentation

- [Databehandleraftale (DPA)](/da/databehandleraftale/) – GDPR Art. 28-kompatibel databehandleraftale
- [Partner Privatlivspolitik](/da/partner-privatlivspolitik/) – Privatlivspolitik for partner-indlejrede brugere
- [Ansvarlig Offentliggørelse](/da/ansvarlig-offentliggorelse/) – Retningslinjer for sikkerhedssårbarhedsrapportering

---

## Kontaktoplysninger

**Privatliv & Compliance:**
- **E-mail:** kontakt@logicnodes.ai
- **Svartid:** 5 arbejdsdage

**Sikkerhedsteam:**
- **E-mail:** kontakt@logicnodes.ai
- **Svartid:** 24 timer for kritiske problemer

**LogicNodes ApS**
Sletvej 2D, 8310 Tranbjerg, Danmark
CVR: DK45318362

---

**Version:** 1.0
**Ikrafttrædelsesdato:** 4. november 2025
**Sidst opdateret:** 4. november 2025

**© 2025 LogicNodes ApS. Alle rettigheder forbeholdes.**

Denne underbehandlerliste opretholdes som en del af LogicNodes' GDPR-overholdelseforpligtelser i henhold til Artikel 28(3)(d).
