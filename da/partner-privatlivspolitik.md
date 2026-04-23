---
layout: legal
title: Privatlivspolitik (Partner Embedded Brugere)
last_updated: 2026-04-21
lang: da
lang_equivalent: /en/partner-privacy-policy/
---

<div class="policy-notice">
<strong>📋 Hvilken Privatlivspolitik Gælder for Dig?</strong>
<ul>
<li><strong>Denne politik:</strong> Hvis du tilgår LogicNodes <strong>gennem en partners produkt</strong> (f.eks. indlejrede AI-funktioner i Rackbeat, Shopify, osv.)</li>
<li><strong><a href="{{ '/da/privatlivspolitik/' | relative_url }}">Standard Privatlivspolitik</a>:</strong> Hvis du <strong>tilmeldte dig direkte</strong> på app.logicnodes.ai</li>
</ul>
</div>

---

# LogicNodes Platform - Privatlivspolitik

**Ikrafttrædelsesdato:** 21. april 2026  

<p class="last-updated">Senest opdateret: {{ page.last_updated | date: "%B %-d, %Y" }}</p>

**Version:** 1.0  

---

## 1. Introduktion

LogicNodes ("vi", "vores" eller "os") leverer en embeddable AI agent-platform der gør det muligt for virksomheder ("Partnere") at integrere AI-drevet automatisering i deres produkter. Denne Privatlivspolitik forklarer hvordan vi indsamler, bruger, gemmer og beskytter persondata når Partnere integrerer vores platform i deres produkter.

**Vigtigt:** Hvis du er en slutbruger der tilgår LogicNodes gennem en Partners produkt (f.eks. Rackbeat, Shopify), kontrolleres dine persondata primært af Partneren. Denne politik forklarer LogicNodes' rolle som **databehandler** på vegne af Partneren (som er **dataansvarlig**).

---

## 2. Roller & Ansvar

### 2.1 Dataansvarlig vs. Databehandler

**Partner (Dataansvarlig):**
- Kontrollerer hvilke persondata der indsamles
- Bestemmer formål og midler til behandling
- Ansvarlig for at indhente brugersamtykke
- Skal levere deres egen privatlivspolitik til slutbrugere

**LogicNodes (Databehandler):**
- Behandler data på Partnerens vegne
- Følger Partnerens instruktioner via vores API
- Implementerer sikkerhedsforanstaltninger (kryptering, adgangskontrol)
- Assisterer Partner med GDPR compliance (datasletning, eksport)

### 2.2 Dine Rettigheder (Slutbrugere)

Hvis du er en slutbruger der tilgår LogicNodes gennem en Partners produkt:
- ✅ **Ret til adgang:** Anmod om kopi af dine data
- ✅ **Ret til sletning:** Anmod om sletning af dine data
- ✅ **Ret til portabilitet:** Eksporter dine data i maskinlæsbart format
- ✅ **Ret til berigtigelse:** Ret unøjagtige data

**Hvordan man udøver rettigheder:** Kontakt Partneren direkte. De vil instruere os om at opfylde din anmodning.

---

## 3. Data Vi Indsamler

### 3.1 Identitetsdata (via Partner)

Når du tilgår LogicNodes gennem en Partners produkt, modtager vi:

| Data | Kilde | Formål | Opbevaring |
|------|--------|---------|-----------|
| Emailadresse | Partner JWT | Kontoidentifikation, notifikationer | Indtil sletning |
| Fuldt navn | Partner JWT | Visning i UI | Indtil sletning |
| Organisations-ID | Partner JWT | Multi-tenant isolering | Indtil sletning |
| Organisationsnavn | Partner JWT (valgfrit) | Visning i UI | Indtil sletning |
| Partner bruger-ID | Partner JWT | Link til Partner-konto | Indtil sletning |

**Juridisk Grundlag (GDPR):** Legitim interesse (levering af service til Partner), Kontraktlig nødvendighed

### 3.2 Brugsdata

Når du bruger AI-agenter gennem vores platform:

| Data | Formål | Opbevaring | Kan Slettes? |
|------|---------|-----------|-------------|
| Agent-kørselshistorik | Samtale kontinuitet, debugging | 1-90 dage (konfigurerbar) | ✅ Ja (automatisk) |
| API forespørgsler/svar | Agent eksekveringskontekst | 1-90 dage (konfigurerbar) | ✅ Ja (automatisk) |
| Værktøjseksekveringslogs | Debugging, gennemsigtighed | 1-90 dage (konfigurerbar) | ✅ Ja (automatisk) |
| Stemmetransskriptioner | Behandle stemmeinput | 1-90 dage (konfigurerbar) | ✅ Ja (automatisk) |
| Uploadede filer | Agent inputdata | 1-90 dage (konfigurerbar) | ✅ Ja (automatisk) |

**Juridisk Grundlag (GDPR):** Legitim interesse (servicefunktionalitet), Kontraktlig nødvendighed

### 3.3 Autentificeringsdata

| Data | Formål | Opbevaring | Kan Slettes? |
|------|---------|-----------|-------------|
| Session tokens | Autentificer API-forespørgsler | 1 time (auto-udløber) | ⚠️ Nej (sikkerhed) |
| Audit logs (auth hændelser) | Sikkerhedsovervågning, compliance | 1 år | ⚠️ Nej (compliance) |
| IP-adresse | Sikkerhedsovervågning, fraud prevention | 1 år (audit logs) | ⚠️ Nej (compliance) |
| User agent | Sikkerhedsovervågning | 1 år (audit logs) | ⚠️ Nej (compliance) |

**Juridisk Grundlag (GDPR):** Legitim interesse (sikkerhed), Juridisk forpligtelse (audit-krav)

### 3.4 Tekniske Data (Automatisk Indsamlet)

| Data | Formål | Opbevaring |
|------|---------|-----------|
| Browser type/version | Kompatibilitet, debugging | Kun session |
| Enhedsinformation | Optimer UI | Kun session |
| Tidszone | Vis tidsstempler | Kun session |

**Juridisk Grundlag (GDPR):** Legitim interesse (serviceoptimering)

### 3.5 Data Vi IKKE Indsamler

- ❌ Betalingsinformation (Partnere håndterer fakturering)
- ❌ Passwords (shadow-brugere bruger syntetiske passwords administreret af os)
- ❌ CPR-numre eller offentlige ID'er
- ❌ Sundhedsinformation (medmindre Partner eksplicit leverer den)
- ❌ Finansielle kontonumre

---

## 4. Hvordan Vi Bruger Data

### 4.1 Servicelevering

Vi bruger dine data til:
- ✅ Autentificere dig via Partner JWT
- ✅ Eksekvere AI-agenter på dine vegne
- ✅ Vise samtalehistorik
- ✅ Behandle stemmeinput (transskription)
- ✅ Gemme eksekveringskontekst til multi-turn samtaler

### 4.2 Sikkerhed & Fraud Prevention

Vi bruger dine data til:
- ✅ Opdage uautoriserede adgangsforsøg
- ✅ Overvåge API-misbrug
- ✅ Undersøge sikkerhedshændelser
- ✅ Overholde sikkerhedsaudit-krav

### 4.3 Serviceforbedring

Vi bruger aggregerede, anonymiserede data til:
- ✅ Analysere funktionsbrug
- ✅ Optimere ydeevne
- ✅ Forbedre AI agent-nøjagtighed

**Bemærk:** Vi bruger IKKE dine persondata til AI-model træning (LLM-udbydere du konfigurerer kan have deres egne politikker).

### 4.4 Juridisk Compliance

Vi kan bruge/offentliggøre data til:
- ✅ Overholde juridiske forpligtelser (stævninger, retskendelser)
- ✅ Håndhæve vores Servicevilkår
- ✅ Beskytte vores rettigheder og sikkerhed
- ✅ Reagere på lovlige myndighedsanmodninger

---

## 5. Datadeling & Offentliggørelse

### 5.1 Med Partnere

**Dine data tilhører Partneren.** Vi deler:
- ✅ Agent-eksekveringsresultater (via API-svar)
- ✅ Brugsmetrikker (kørselstællinger, fejlprocenter)
- ⚠️ Vi deler IKKE data på tværs af forskellige Partnere

### 5.2 Med Sub-Processors

Vi bruger betroede tredjepartstjenester:

| Sub-Processor | Service | Data Delt | Lokalitet | Sikkerhedsforanstaltninger |
|---------------|---------|-----------|----------|------------|
| **Supabase** | Database, Auth, Storage | Alle data | EU (AWS EU-North-1, Stockholm) | SOC 2, ISO 27001, GDPR DPA |
| **AWS** | Hosting infrastruktur | Alle data (via Supabase) | EU (Stockholm) | SOC 1/2/3, ISO 27001 |
| **Mailgun** | Transaktionelle emails | Email, navn | USA/EU | GDPR DPA tilgængelig |

**Sub-Processor Aftaler:** Alle sub-processors har underskrevet Databehandleraftaler (DPAs) med tilstrækkelige GDPR-sikkerhedsforanstaltninger.

### 5.3 Med LLM-udbydere (Partner-Konfigureret)

Hvis Partnere konfigurerer deres egne LLM API-nøgler (OpenAI, Anthropic, Google, Grok):
- ✅ Agent prompts/svar sendt til LLM-udbyder
- ✅ Data underlagt LLM-udbyders privatlivspolitik
- ⚠️ LogicNodes er IKKE ansvarlig for LLM-udbyder datahåndtering

**Anbefaling:** Partnere bør gennemgå LLM-udbyder privatlivspolitikker og konfigurere dataopbevaringsindstillinger.

### 5.4 Intet Salg af Persondata

Vi sælger, udlejer eller handler IKKE med persondata til tredjeparter. Nogensinde.

---

## 6. Dataopbevaring & Sletning

### 6.1 Automatiske Opbevaringspolitikker

| Datatype | Opbevaring | Sletningsmetode |
|-----------|-----------|-----------------|
| Agent-kørsler | 1-90 dage (Partner-konfigurerbar) | Automatisk daglig oprydning |
| Agent-kørselshændelser | 1-90 dage (Partner-konfigurerbar) | Automatisk daglig oprydning |
| Transskriptioner | 1-90 dage (Partner-konfigurerbar) | Automatisk daglig oprydning |
| Audit logs | 1 år (fast) | Automatisk efter 1 år |
| Brugerkontodata | Indtil sletteanmodning | Manuel eller Partner-initieret |

**Oprydningsplan:** Dagligt kl. 2:00 UTC

### 6.2 Bruger-initieret Sletning

**Hvordan man sletter dine data:**
1. Kontakt Partneren (dataansvarlig)
2. Partner sender sletteanmodning via API
3. Vi cascade-sletter alle tilknyttede data:
   - ✅ Brugerkonto
   - ✅ Organisationsmedlemskab
   - ✅ Agent-kørsler, hændelser, transskriptioner
   - ✅ Agent eksekveringskontekst (checkpoints)
   - ✅ Vault secrets (krypterede legitimationsoplysninger)

**Sletningstidslinje:**
- Øjeblikkeligt: Alle data slettet fra produktionsdatabase (synkron CASCADE)
- Inden for 30 dage: Alle data fjernet fra krypterede backups

**Kan Ikke Slettes:**
- ⚠️ Audit logs (bevaret 1 år for compliance)
- ⚠️ Aggregerede, anonymiserede analyser

### 6.3 Partner-initieret Sletning

Partnere kan slette organisationer/brugere via:
- `DELETE /api/v1/partner/organizations/{org_id}` (fuld org-sletning)
- `DELETE /api/v1/partner/organizations/{org_id}/users/{user_id}` (brugerfjernelse)

Samme cascading-sletning gælder.

---

## 7. Datasikkerhed

### 7.1 Kryptering

**I Hvile:**
- ✅ Databasekryptering (Supabase standard)
- ✅ Secrets-kryptering (Supabase Vault)
- ✅ Lager-bucket kryptering (AWS S3)

**Under Transport:**
- ✅ TLS 1.2+ til al API-kommunikation
- ✅ HTTPS-håndhævelse
- ✅ HSTS-headers

### 7.2 Adgangskontrol

**Multi-Tenant Isolering:**
- ✅ Row-Level Security (RLS) politikker
- ✅ Applikationslag adgangskontrol
- ✅ JWT-baseret session scoping

**Medarbejderadgang:**
- ✅ Least-privilege princip
- ✅ Service role-adgang logget til audit logs
- ✅ Baggrundstjek for medarbejdere med produktionsadgang

### 7.3 Sikkerhedsovervågning

**Realtidsovervågning:**
- ✅ Mislykkede autentificeringsforsøg
- ✅ Usædvanlige API-adgangsmønstre
- ✅ Secret adgang/sletningshændelser

**Incident Response:**
- ✅ 24-timers svartid for kritiske problemer
- ✅ Sikkerhedskontakt: kontakt@logicnodes.ai
- ✅ Post-incident rapporter (inden for 5 arbejdsdage)

---

## 8. Internationale Dataoverførsler

### 8.1 Datalokalitet

**Primær Opbevaring:** Den Europæiske Union (AWS EU-North-1, Stockholm via Supabase)

**Datalokalitet:**
- ✅ EU data residency som standard (Sverige)
- ✅ GDPR-compliant datahosting
- ✅ US data residency tilgængelig efter Partner-anmodning

**Internationale Overførsler:**
- Standard Contractual Clauses (SCCs) tilgængelig til US-overførsler
- Tilstrækkelige sikkerhedsforanstaltninger pr. GDPR Artikel 46

### 8.2 Adequacy Decisions

Vi stoler på:
- ✅ Standard Contractual Clauses (SCCs) - EU-Kommissionen godkendt
- ✅ Supabase compliance (SOC 2, ISO 27001)
- ✅ AWS compliance (SOC 1/2/3, ISO 27001)

---

## 9. Dine Rettigheder (GDPR)

### 9.1 Ret til Adgang (Artikel 15)

**Anmodning:** Kopi af dine persondata

**Hvordan man udøver:**
1. Kontakt Partner (dataansvarlig)
2. Partner anmoder om eksport via API
3. Vi leverer data inden for 30 dage

**Hvad du modtager:**
- Brugerkontodetajler (email, navn, org)
- Agent-kørselshistorik (JSON-eksport)
- Audit logs (hvis relevant)

### 9.2 Ret til Berigtigelse (Artikel 16)

**Anmodning:** Ret unøjagtige data

**Hvordan man udøver:**
1. Opdater data via Partners produkt
2. Partner sender opdateret JWT (navn, email-ændringer)
3. Vi opdaterer øjeblikkeligt

### 9.3 Ret til Sletning (Artikel 17)

**Anmodning:** Slet dine persondata ("ret til at blive glemt")

**Hvordan man udøver:**
1. Kontakt Partner
2. Partner sender sletteanmodning via API
3. Vi sletter inden for 24 timer (se sektion 6.2)

**Undtagelser (vi kan nægte sletning):**
- ⚠️ Juridisk forpligtelse til at bevare (audit logs - 1 år)
- ⚠️ Offentlig interesse (sikkerhedsundersøgelse)
- ⚠️ Juridiske krav (igangværende retssager)

### 9.4 Ret til Dataportabilitet (Artikel 20)

**Anmodning:** Eksporter data i maskinlæsbart format

**Hvordan man udøver:**
1. Kontakt Partner
2. Partner anmoder om eksport via API
3. Vi leverer JSON-eksport (strukturerede data)

**Hvad er inkluderet:**
- Brugerprofil (email, navn)
- Agent-kørsler (samtalehistorik)
- Eksekveringslogs (API forespørgsler/svar)

### 9.5 Ret til Begrænsning af Behandling (Artikel 18)

**Anmodning:** Midlertidigt stop behandling af dine data

**Hvordan man udøver:**
1. Kontakt Partner
2. Partner deaktiverer brugerkonto
3. Vi stopper behandling (data bevaret men ikke brugt)

### 9.6 Ret til Indsigelse (Artikel 21)

**Anmodning:** Gør indsigelse mod behandling baseret på legitim interesse

**Hvordan man udøver:**
1. Kontakt Partner
2. Partner evaluerer indsigelse
3. Hvis gyldig, instruerer Partner os om at slette data

### 9.7 Ret til at Tilbagetrække Samtykke

**Anmodning:** Tilbagetræk samtykke til databehandling

**Hvordan man udøver:**
1. Stop med at bruge Partners produkt (ingen nye data sendt til LogicNodes)
2. Anmod om sletning (se sektion 9.3)

---

## 10. Børns Privatliv

**Aldersbegrænsning:** LogicNodes er IKKE beregnet til børn under 16 år.

**Ingen Bevidst Indsamling:** Vi indsamler ikke bevidst persondata fra børn under 16 år.

**Forældrevarsel:** Hvis du mener vi har indsamlet data fra et barn under 16 år, kontakt os øjeblikkeligt på kontakt@logicnodes.ai. Vi sletter dataene inden for 24 timer.

---

## 11. Californiens Privatlivsrettigheder (CCPA)

Hvis du er bosiddende i Californien:

### 11.1 Ret til at Vide (CCPA § 1798.100)

Du har ret til at vide:
- Hvilke personlige oplysninger vi indsamler
- Kilder til personlige oplysninger
- Formål med indsamling
- Tredjeparter vi deler med

**Se sektioner 3-5 af denne politik.**

### 11.2 Ret til Sletning (CCPA § 1798.105)

Du har ret til at anmode om sletning af personlige oplysninger.

**Se sektion 6.2 for sletningsproces.**

### 11.3 Ret til at Fravælge Salg (CCPA § 1798.120)

**Vi sælger IKKE personlige oplysninger.** Ingen fravalg nødvendigt.

### 11.4 Ret til Ikke-diskrimination (CCPA § 1798.125)

Vi vil IKKE diskriminere mod dig for at udøve CCPA-rettigheder.

### 11.5 Autoriseret Agent

Californiens bosiddende kan udpege en autoriseret agent til at fremsætte anmodninger på deres vegne:
1. Lever skriftlig autorisation
2. Verificer identitet (offentligt udstedt ID)
3. Indsend anmodning til kontakt@logicnodes.ai

---

## 12. Ændringer til Denne Politik

**Underretningsmetode:**
- Email til Partnere (30 dages forhåndsvarsel)
- Opdater "Senest Opdateret" dato øverst i politik
- Væsentlige ændringer kræver eksplicit samtykke

**Væsentlige Ændringer:**
- Udvide dataindsamling (nye kategorier)
- Ændre opbevaringsperioder (længere opbevaring)
- Tilføje nye sub-processors
- Ændre juridisk grundlag for behandling

**Ikke-væsentlige Ændringer:**
- Afklaringer, formatering
- Opdateringer til kontaktoplysninger
- Rettelse af tastefejl

---

## 13. Kontakt Os

### Privatlivsteam
**Email:** kontakt@logicnodes.ai
**Svartid:** 5 arbejdsdage

### Databeskyttelsesrådgiver (DPO)
**Email:** kontakt@logicnodes.ai
**Formål:** GDPR/CCPA-anmodninger, privatlivsbekymringer

### Sikkerhedsteam
**Email:** kontakt@logicnodes.ai
**Formål:** Sikkerhedshændelser, databrud

### Postadresse
LogicNodes ApS  
Sletvej 2D  
8310 Tranbjerg  
Danmark  
CVR: DK45318362

---

## 14. Tilsynsmyndighed (EU)

Hvis du er beliggende i EU/EØS og mener vi har overtrådt GDPR, har du ret til at indgive klage til din lokale databeskyttelsesmyndighed:

**Liste over EU Databeskyttelsesmyndigheder:**
https://edpb.europa.eu/about-edpb/board/members_en

**Eksempel (Danmark):**
Datatilsynet  
Carl Jacobsens Vej 35  
2500 Valby  
Danmark  
Email: dt@datatilsynet.dk

---

## 15. Ordliste

**Dataansvarlig:** Enhed der bestemmer formål og midler til behandling af persondata (Partneren).

**Databehandler:** Enhed der behandler data på Dataansvarligs vegne (LogicNodes).

**Persondata:** Enhver information relateret til en identificeret eller identificerbar fysisk person.

**Shadow-bruger:** Syntetisk brugerkonto oprettet under Partner-autentificering (ingen password, email er `{platform_user_id}@{partner_id}.embed.logicnodes.internal`).

**JWT (JSON Web Token):** Signeret token brugt til autentificering, indeholdende brugeridentitets-claims.

**Vault:** Supabase krypteret secrets-opbevaring (til API-nøgler, legitimationsoplysninger).

**RLS (Row-Level Security):** Database sikkerhedspolitikker der håndhæver multi-tenant isolering.

**Cascading Delete:** Automatisk sletning af relaterede records når overordnet record slettes.

---

## Appendiks A: Databehandlingsaktiviteter

| Behandlingsaktivitet | Formål | Juridisk Grundlag (GDPR) | Opbevaring |
|---------------------|---------|-------------------|-----------|
| Brugerautentificering | Verificer identitet via Partner JWT | Legitim interesse, Kontrakt | Session (1 time) |
| Agent-eksekvering | Lever AI-automatiserings-service | Kontrakt | 1-90 dage |
| Audit logging | Sikkerhedsovervågning, compliance | Legitim interesse, Juridisk forpligtelse | 1 år |
| Secret-opbevaring | Gem krypterede API-nøgler | Kontrakt | Indtil sletning |
| Filopbevaring | Behandle uploadede dokumenter | Kontrakt | 1-90 dage |
| Email-notifikationer | Send transaktionelle emails | Kontrakt | Session |

---

## Appendiks B: Sub-Processor Liste

| Sub-Processor | Service | Data Delt | Lokalitet | DPA Underskrevet |
|---------------|---------|-----------|----------|------------|
| Supabase | Database, Auth, Storage | Alle data | EU (AWS EU-North-1, Stockholm) | ✅ Ja |
| Amazon Web Services (AWS) | Cloud infrastruktur | Alle data (via Supabase) | EU (Stockholm) | ✅ Ja (via Supabase) |
| Mailgun | Transaktionelle emails | Email, navn | USA/EU | ✅ Ja |

**Senest Opdateret:** 21. april 2026  

**Ændringsnotifikation:** Partnere underrettet 30 dage før tilføjelse af nye sub-processors.

---

**© 2026 LogicNodes ApS. Alle rettigheder forbeholdes.**

Denne privatlivspolitik træder i kraft d. 21. april 2026. Ved at bruge LogicNodes gennem en Partners produkt, anerkender du at du har læst og forstået denne politik.
