---
layout: legal
title: Databehandleraftale
last_updated: 2025-11-03
lang: da
---

# Databehandleraftale (DPA)

**Mellem:**
- **Dataansvarlig** ("[PARTNER NAVN]", "Partner", "du")
- **Databehandler** ("LogicNodes Inc.", "LogicNodes", "vi", "os")

**Ikrafttrædelsesdato:** [DATO]  

**Version:** 1.0  

---

## 1. Definitioner

### 1.1 Definerede Begreber

Til brug for denne Databehandleraftale ("DPA"):

**"GDPR"** betyder Europa-Parlamentets og Rådets forordning (EU) 2016/679 af 27. april 2016 om beskyttelse af fysiske personer i forbindelse med behandling af personoplysninger og om fri udveksling af sådanne oplysninger.

**"Databeskyttelseslovgivning"** betyder alle gældende love og regler vedrørende privatliv og databeskyttelse, herunder GDPR, CCPA og andre gældende love.

**"Personoplysninger"** betyder enhver information vedrørende en identificeret eller identificerbar fysisk person, som behandles af LogicNodes på vegne af Partner i forbindelse med Tjenesterne.

**"Behandling"** betyder enhver handling eller række af handlinger, der foretages med Personoplysninger, såsom indsamling, registrering, organisering, strukturering, opbevaring, tilpasning, genfinding, konsultation, anvendelse, videregivelse, sletning eller tilintetgørelse.

**"Registrerede"** betyder den person, som Personoplysninger vedrører (Partners slutbrugere).

**"Tjenester"** betyder LogicNodes' integrerbare AI-agentplatform som beskrevet i Hovedserviceaftalen.

**"Underdatabehandler"** betyder enhver tredjepart, som LogicNodes anvender til at behandle Personoplysninger på vegne af Partner.

**"Tilsynsmyndighed"** betyder en uafhængig offentlig myndighed etableret af en EU-medlemsstat i henhold til GDPR artikel 51.

**"Databrud"** betyder et brud på sikkerheden, der fører til hændelig eller ulovlig tilintetgørelse, tab, ændring, uautoriseret videregivelse af eller adgang til Personoplysninger.

---

## 2. Anvendelsesområde & Roller

### 2.1 Forhold

Denne DPA regulerer behandlingen af Personoplysninger af LogicNodes (Databehandler) på vegne af Partner (Dataansvarlig) i forbindelse med Tjenesterne.

### 2.2 Anvendelighed

Denne DPA gælder for alle Personoplysninger, som behandles af LogicNodes på Partners vegne, herunder men ikke begrænset til:
- Slutbrugeridentitetsdata (e-mail, navn, organisation)
- Agent-udførelseslogfiler (API-anmodninger/svar)
- Stemmetransskriptioner
- Uploadede filer
- Revisionslogfiler

### 2.3 Hovedserviceaftale

Denne DPA udgør en del af og supplerer Hovedserviceaftalen ("MSA") mellem Partner og LogicNodes. I tilfælde af konflikt har denne DPA forrang i databeskyttelsesspørgsmål.

---

## 3. Behandling af Personoplysninger

### 3.1 Partner-instruktioner

LogicNodes må kun behandle Personoplysninger:
1. På dokumenterede instruktioner fra Partner (via API-kald, konfigurationsindstillinger)
2. Som nødvendigt for at levere Tjenesterne
3. Som krævet af gældende lovgivning (med varsel til Partner, hvis lovligt tilladt)

**Partner-instruktioner inkluderer:**
- Autentificeringsanmodninger (POST /api/v1/embed/auth)
- Anmodninger om sletning af organisation/bruger (DELETE APIs)
- Hemmeligheder-administrationsoperationer (POST/DELETE /api/v1/partner/secrets)
- Konfiguration af dataopbevaringsperiode (default_retention_period indstilling)

### 3.2 Uautoriseret Behandling

Hvis LogicNodes mener, at Partners instruktioner krænker Databeskyttelseslovgivningen, vil LogicNodes:
1. Straks informere Partner
2. Suspendere behandling indtil instruktioner afklares
3. Dokumentere hændelsen til revisionsformål

### 3.3 Behandlingsdetaljer

**Genstand:** Levering af AI-agent-automatiseringsplatform

**Varighed:** MSA-periode + opbevaringsperiode (som konfigureret af Partner)

**Art & Formål:**
- Autentificere slutbrugere via JWT-validering
- Udføre AI-agenter på vegne af slutbrugere
- Gemme udførelseskontekst for samtalekontinuitet
- Levere debugging- og transparensværktøjer

**Type af Personoplysninger:**
- Identitetsdata: E-mail, navn, bruger-ID, organisations-ID
- Brugsdata: Agent-kørsler, API-anmodninger/svar, transskriptioner
- Tekniske data: IP-adresse, user agent (til sikkerhed)

**Kategorier af Registrerede:**
- Partners slutbrugere (medarbejdere, kunder, kontraktansatte)

**Særlige Kategorier af Data:**
- Ingen behandlet som standard
- Hvis Partner leverer følsomme data (sundhed, økonomi osv.), skal Partner meddele LogicNodes og sikre passende beskyttelsesforanstaltninger

---

## 4. LogicNodes' Forpligtelser

### 4.1 Fortrolighed

LogicNodes skal sikre, at alt personale autoriseret til at behandle Personoplysninger:
1. Er underlagt fortrolighedsforpligtelser (ansættelseskontrakter, NDA'er)
2. Har modtaget passende træning i databeskyttelse
3. Kun får adgang til Personoplysninger som nødvendigt for deres rolle

### 4.2 Sikkerhedsforanstaltninger

LogicNodes implementerer passende tekniske og organisatoriske foranstaltninger til beskyttelse af Personoplysninger, herunder:

**Tekniske Foranstaltninger:**
- Kryptering af data i hvile (database, hemmeligheder, opbevaring)
- Kryptering under transmission (TLS 1.2+, HTTPS-håndhævelse)
- Multi-tenant-isolation (RLS-politikker, applikationslags-adgangskontrol)
- Adgangskontrol (JWT-baseret autentificering, rollebaserede tilladelser)
- Revisionslogning (al adgang logget i 1 år)
- Hastighedsbegrænsning (forebyggelse af misbrug)
- Automatiserede backups (dagligt, krypteret)

**Organisatoriske Foranstaltninger:**
- Baggrundstjek for medarbejdere med produktionsadgang
- Mindst-privilegium adgangsprincip
- Hændelsesresponsplan (24-timers svartid)
- Sikkerhedsbevidsthedstræning (årligt)
- Leverandørrisikostyring (underdatabehandler-gennemgange)

**Overholdelse:**
- SOC 2-klar (formel revision planlagt)
- Årlig penetrationstest (planlagt Q2 2026)
- Sårbarheds-scanning (automatiseret, ugentligt)

### 4.3 Anmodninger fra Registrerede

LogicNodes skal assistere Partner med at opfylde Registreredes rettigheder i henhold til Databeskyttelseslovgivningen:

**Ret til Adgang (GDPR Art. 15):**
- Eksport-API-endpoints for agent-kørselshistorik
- JSON-format til maskinlæsbar eksport
- Svartid: Inden for 30 dage

**Ret til Berigtigelse (GDPR Art. 16):**
- Partner opdaterer data via JWT (navn, e-mail-ændringer)
- Ændringer reflekteres øjeblikkeligt

**Ret til Sletning (GDPR Art. 17):**
- DELETE-API'er til bruger/organisationsfjernelse
- Kaskaderende sletninger sikrer fuldstændig fjernelse
- Sletningstidslinje: Inden for 24 timer (produktion), 30 dage (backups)

**Ret til Dataportabilitet (GDPR Art. 20):**
- Eksport-API returnerer JSON-format
- Struktureret, maskinlæsbare data

**Ret til Begrænsning af Behandling (GDPR Art. 18):**
- Partner kan deaktivere brugerkonti
- Behandling stoppet (data bevaret men ikke brugt)

**Ret til Indsigelse (GDPR Art. 21):**
- Partner evaluerer indsigelse og instruerer LogicNodes
- Hvis gyldig, slettes data via DELETE-API'er

**Assistance:**
LogicNodes vil besvare Partner-anmodninger inden for 5 arbejdsdage og levere rimelig assistance (dokumentation, API-vejledning, teknisk support).

### 4.4 Underretning om Databrud

I tilfælde af et Databrud skal LogicNodes:

**Øjeblikkelige Handlinger (inden for 24 timer):**
1. Begrænse bruddet (stoppe uautoriseret adgang)
2. Underrette Partner via e-mail (sikkerhedskontakt)
3. Levere foreløbig hændelsesrapport (omfang, berørte data, grundårsag)

**Opfølgende Handlinger (inden for 72 timer):**
1. Detaljeret hændelsesrapport (tidslinje, konsekvensanalyse, berørte Registrerede)
2. Afhjælpningsplan (trin taget, forebyggende foranstaltninger)
3. Assistance med underretning til Tilsynsmyndighed (hvis krævet af GDPR Art. 33)

**Partner-forpligtelser:**
- Partner er ansvarlig for at underrette Registrerede (hvis krævet af GDPR Art. 34)
- LogicNodes vil levere rimelig assistance (lister over berørte brugere, konsekvensanalyse)

### 4.5 Konsekvensanalyse vedrørende Databeskyttelse (DPIA)

LogicNodes skal levere rimelig assistance, hvis Partner er forpligtet til at udføre en DPIA i henhold til GDPR artikel 35, herunder:
- Beskrivelse af behandlingsoperationer
- Sikkerhedsforanstaltninger implementeret
- Risikovurdering (sandsynlighed for databrud, konsekvens)
- Information om underdatabehandlere

### 4.6 Forudgående Høring

Hvis en DPIA indikerer høj risiko, og Partner skal konsultere en Tilsynsmyndighed (GDPR Art. 36), vil LogicNodes levere nødvendige oplysninger og assistance.

---

## 5. Underdatabehandling

### 5.1 Autoriserede Underdatabehandlere

Partner giver generel autorisation til LogicNodes til at engagere Underdatabehandlere, underlagt betingelserne i dette afsnit.

**Nuværende Underdatabehandlere:**

| Underdatabehandler | Tjeneste | Behandlede Data | Lokation | Beskyttelsesforanstaltninger |
|---------------|---------|----------------|----------|------------|
| **Supabase Inc.** | Database, Auth, Storage | Alle Personoplysninger | EU (AWS EU-North-1, Stockholm) | SOC 2, ISO 27001, GDPR DPA, SCC |
| **Amazon Web Services (AWS)** | Cloud-infrastruktur | Alle Personoplysninger (via Supabase) | EU (Stockholm) | SOC 1/2/3, ISO 27001, SCC |
| **Mailgun Technologies Inc.** | Transaktions-e-mail | E-mail, navn | USA/EU | GDPR DPA, SCC |

**Sidst Opdateret:** 3. november 2025

### 5.2 Krav til Underdatabehandlere

LogicNodes skal sikre, at alle Underdatabehandlere:
1. Er bundet af databeskyttelsesforpligtelser svarende til denne DPA
2. Implementerer passende tekniske og organisatoriske sikkerhedsforanstaltninger
3. Har underskrevet Databehandleraftaler (eller tilsvarende)
4. Undergår regelmæssige sikkerhedsvurderinger

### 5.3 Nye Underdatabehandlere

**Underretning:**
LogicNodes vil underrette Partner mindst **30 dage** før engagement af nye Underdatabehandlere eller væsentlig ændring af eksisterende Underdatabehandlere.

**Underretningsmetode:**
- E-mail til Partners sikkerhedskontakt
- Opdatering til Underdatabehandler-liste (Appendiks B i Privatlivspolitik)

**Indsigelse:**
Partner kan gøre indsigelse mod ny Underdatabehandler på rimelige databeskyttelsesgrunde ved at underrette LogicNodes inden for 30 dage.

**Hvis Partner Gør Indsigelse:**
- LogicNodes vil ikke engagere Underdatabehandleren
- ELLER: LogicNodes vil arbejde med Partner om at løse bekymringer
- ELLER: Hvis intet alternativ, kan Partner opsige MSA (30-dages varsel, ingen straf)

### 5.4 Underdatabehandler-ansvar

LogicNodes forbliver fuldt ansvarlig over for Partner for Underdatabehandlers præstation. Hvis Underdatabehandler fejler i at opfylde databeskyttelsesforpligtelser, er LogicNodes ansvarlig over for Partner, som hvis LogicNodes havde udført behandlingen.

---

## 6. Internationale Dataoverførsler

### 6.1 Datalokation

**Primær Opbevaring:** Den Europæiske Union (AWS EU-North-1, Stockholm via Supabase)

**US Data-residens (Valgfrit):**
Partner kan anmode om US data-residens. Yderligere gebyrer kan være gældende.

### 6.2 Overførselsmekanismer

**Standard:** Data opbevaret i EU (ingen international overførsel for EU-kunder)

For overførsler af Personoplysninger til lande uden en tilstrækkeligheds-afgørelse (hvis Partner anmoder om US-residens), stoler LogicNodes på:

**Standardkontraktbestemmelser (SCC'er):**
- EU-Kommissionens afgørelse 2021/914 (Modul 2: Dataansvarlig til Databehandler)
- Inkorporeret ved reference i denne DPA
- Fuld tekst tilgængelig på: https://eur-lex.europa.eu/eli/dec_impl/2021/914/oj

**Supabase SCC'er:**
- Supabase har underskrevet SCC'er med LogicNodes
- LogicNodes har underskrevet SCC'er med Partner (via denne DPA)

### 6.3 Yderligere Beskyttelsesforanstaltninger

Ud over SCC'er implementerer LogicNodes supplerende foranstaltninger:
- Kryptering i hvile og under transmission (TLS 1.2+, AES-256)
- Adgangskontrol (multi-tenant-isolation, RLS-politikker)
- Dataminimering (opbevaringspolitikker, automatisk oprydning)
- Transparens (revisionslogfiler, dataeksport-API'er)

### 6.4 Regeringsadgangsanmodninger

Hvis LogicNodes modtager en lovlig anmodning fra offentlige myndigheder om adgang til Personoplysninger:
1. LogicNodes vil forsøge at omdirigere anmodningen til Partner
2. Hvis lovligt tilladt, vil LogicNodes underrette Partner før videregivelse
3. Hvis forbudt fra at underrette, vil LogicNodes anfægte anmodningen eller søge tilladelse til at underrette

---

## 7. Dataopbevaring & Sletning

### 7.1 Opbevaringsperioder

| Datatype | Opbevaring | Sletningsmetode |
|-----------|-----------|-----------------|
| Agent-kørsler, events | 1-90 dage (Partner-konfigurerbar) | Automatisk daglig oprydning |
| Transskriptioner | 1-90 dage (Partner-konfigurerbar) | Automatisk daglig oprydning |
| Agent-udførelseskontekst (checkpoints) | 1-90 dage (Partner-konfigurerbar) | Automatisk daglig oprydning |
| Brugerkontodata | Indtil sletningsanmodning | Manuel eller Partner-initieret |
| Revisionslogfiler | 1 år (fast) | Automatisk efter 1 år |

### 7.2 Afslutning af Tjeneste

Ved opsigelse eller udløb af MSA skal LogicNodes (efter Partners valg):

**Mulighed A: Slet**
- Slet alle Personoplysninger inden for 30 dage
- Lever skriftlig bekræftelse på sletning

**Mulighed B: Returnér**
- Eksportér alle Personoplysninger i JSON-format
- Lever til Partner inden for 30 dage
- Slet efter Partner bekræfter modtagelse

**Undtagelse:** LogicNodes kan opbevare Personoplysninger i det omfang, som kræves af gældende lovgivning (f.eks. revisionslogfiler til overholdelse).

### 7.3 Partner-initieret Sletning

Partner kan anmode om sletning når som helst via:
- DELETE /api/v1/partner/organizations/{org_id} (fuld org-sletning)
- DELETE /api/v1/partner/organizations/{org_id}/users/{user_id} (brugersletning)

LogicNodes vil slette øjeblikkeligt fra produktionsdatabase (synkron CASCADE), rense fra backups inden for 30 dage.

---

## 8. Revision & Overholdelse

### 8.1 Partners Revisionsrettigheder

Partner har ret til at revidere LogicNodes' overholdelse af denne DPA, underlagt:

**Frekvens:** Én gang per kalenderår (eller flere hvis Databrud forekommer)

**Omfang:**
- Sikkerhedsforanstaltninger (gennemgang af dokumentation)
- Underdatabehandler-aftaler
- Dataopbevaringspolitikker
- Hændelsesrespons-procedurer

**Metode:**
- Fjernrevision (gennemgang af dokumentation, Q&A)
- ELLER: On-site revision (med 30 dages varsel, i arbejdstiden)
- ELLER: Tredjeparts-revision (SOC 2-rapport, penetrationstestresultater)

**Fortrolighed:**
Partner accepterer at underskrive NDA og begrænse adgang til fortrolige oplysninger.

**Omkostninger:**
- Første revision per år: Ingen gebyr
- Yderligere revisioner: Rimelige omkostninger (skal aftales)

### 8.2 LogicNodes Certificeringer

LogicNodes vil opretholde industri-standard certificeringer og levere på anmodning:
- SOC 2 Type II-rapport (når tilgængelig, estimeret 2026)
- Penetrationstestrapporter (årligt, under NDA)
- Underdatabehandler-certificeringer (Supabase SOC 2, ISO 27001)

---

## 9. Ansvar & Erstatning

### 9.1 Ansvarsbegrænsning

Hver parts ansvar under denne DPA er underlagt begrænsninger og undtagelser i MSA, undtagen:
- Ansvar for Databrud forårsaget af LogicNodes' grove uagtsomhed eller forsætlig mishandling
- Ansvar for overtrædelser af Databeskyttelseslovgivning forårsaget af LogicNodes' manglende overholdelse af denne DPA

### 9.2 Erstatning

LogicNodes skal skadesløsholde og holde Partner fri for:
- Krav opstået fra LogicNodes' brud på denne DPA
- Bøder pålagt af Tilsynsmyndigheder på grund af LogicNodes' manglende overholdelse af GDPR
- Registreredes krav opstået fra LogicNodes' uautoriserede behandling

**Undtagelser:**
LogicNodes er IKKE ansvarlig for krav opstået fra:
- Partners instruktioner (hvis Partner instruerer ulovlig behandling)
- Partners manglende overholdelse af Databeskyttelseslovgivning
- Registreredes handlinger (hvis Registrerede forårsager brud)

---

## 10. Periode & Opsigelse

### 10.1 Periode

Denne DPA er gyldig fra Ikrafttrædelsesdatoen og fortsætter i MSA's varighed.

### 10.2 Opsigelse

Denne DPA opsiges automatisk ved opsigelse eller udløb af MSA.

### 10.3 Overlevelse

Følgende afsnit overlever opsigelse:
- Afsnit 4.2 (Sikkerhedsforanstaltninger) - indtil data slettes
- Afsnit 4.4 (Underretning om Databrud) - for brud forekommet under perioden
- Afsnit 7 (Dataopbevaring & Sletning) - indtil data slettes
- Afsnit 9 (Ansvar & Erstatning) - per MSA-begrænsningsperiode

---

## 11. Generelle Bestemmelser

### 11.1 Lovvalg

Denne DPA er underlagt lovene specificeret i MSA.

For GDPR-overholdelse gælder EU-databeskyttelseslovgivning i det omfang, som kræves af GDPR artikel 28(3)(a).

### 11.2 Ændringer

LogicNodes kan ændre denne DPA for at overholde ændringer i Databeskyttelseslovgivningen ved at give 30 dages varsel til Partner.

Væsentlige ændringer kræver Partners samtykke (fortsat brug af Tjenester udgør samtykke).

### 11.3 Adskillelse

Hvis nogen bestemmelse i denne DPA er ugyldig eller ikke kan håndhæves, forbliver de resterende bestemmelser i fuld kraft og virkning. Den ugyldige bestemmelse skal erstattes af en gyldig bestemmelse, der opnår den oprindelige hensigt.

### 11.4 Hele Aftalen

Denne DPA udgør sammen med MSA og Privatlivspolitikken hele aftalen om databeskyttelse.

### 11.5 Rangorden

I tilfælde af konflikt:
1. Denne DPA (for databeskyttelsesspørgsmål)
2. MSA (for kommercielle vilkår)
3. Privatlivspolitik (for slutbrugerdatarettigheder)

---

## 12. Underskrifter

**Partner (Dataansvarlig):**

Underskrift: _______________________________  
Navn: [PARTNER AUTORISERET UNDERSKRIVER]  
Titel: _______________________________  
Dato: _______________________________  

**LogicNodes Inc. (Databehandler):**

Underskrift: _______________________________  
Navn: [LOGICNODES AUTORISERET UNDERSKRIVER]  
Titel: _______________________________  
Dato: _______________________________  

---

## Appendiks A: Standardkontraktbestemmelser (SCC'er)

**EU-Kommissionens Afgørelse 2021/914 - Modul 2 (Dataansvarlig til Databehandler)**

Fuld tekst tilgængelig på: https://eur-lex.europa.eu/eli/dec_impl/2021/914/oj

**Part-detaljer:**

**Dataeksportør (Dataansvarlig):**
- Navn: [PARTNER NAVN]  
- Adresse: [PARTNER ADRESSE]  
- Kontakt: [PARTNER SIKKERHEDSKONTAKT]  

**Dataimportør (Databehandler):**
- Navn: LogicNodes Inc.  
- Adresse: [LOGICNODES ADRESSE]  
- Kontakt: security@logicnodes.ai  

**Kompetent Tilsynsmyndighed:**
[Partners lokale databeskyttelsesmyndighed, f.eks. Datatilsynet for Danmark]

**Klausul 7 (Docking-klausul):** Ikke gældende

**Klausul 9 (Brug af Underdatabehandlere):**
- Generel autorisation givet (Afsnit 5.1)
- 30-dages varsel for nye Underdatabehandlere (Afsnit 5.3)

**Klausul 13 (Tilsyn):**
Tilsynsmyndighed: [Partners lokale myndighed]

**Klausul 17 (Lovvalg):**
Lovgivningen i det EU-medlemsland, hvor Dataeksportør er etableret

**Klausul 18 (Valg af Forum):**
Domstole i det EU-medlemsland, hvor Dataeksportør er etableret

---

## Appendiks B: Tekniske og Organisatoriske Foranstaltninger

**Sikkerhedsforanstaltninger Implementeret af LogicNodes:**

### 1. Adgangskontrol

**Fysisk Adgang:**
- Ikke relevant (cloud-baseret infrastruktur, ingen on-premise servere)
- Supabase/AWS administrerer fysisk datacenter-sikkerhed (ISO 27001, SOC 2)

**Systemadgang:**
- Multi-faktor-autentificering (MFA) krævet for produktionsadgang
- SSH-nøglebaseret autentificering (ingen adgangskode-login)
- IP-whitelisting for produktionssystemer
- Mindst-privilegium-adgangsprincip (rollebaseret)

**Dataadgang:**
- Row-Level Security (RLS)-politikker håndhæver multi-tenant-isolation
- JWT-baseret autentificering (HS256, 1-times udløb)
- API-nøgle-autentificering (bcrypt-hashing, vis-én-gang)
- Service role-adgang logget til revisionslogfiler

### 2. Transmissionskontrol

**Kryptering under Transmission:**
- TLS 1.2+ for al API-kommunikation
- HTTPS-håndhævelse (HTTP omdirigerer til HTTPS)
- HSTS-headers (forhindrer nedrustningsangreb)

**API-sikkerhed:**
- Hastighedsbegrænsning (10 anm./min på autentificeringsendpoints)
- Input-validering (Pydantic-skemaer, UUID-validering)
- SQL-injektionsforebyggelse (kun parameteriserede forespørgsler)

### 3. Opbevaringskontrol

**Kryptering i Hvile:**
- Database-kryptering (Supabase standard, AES-256)
- Hemmeligheder-kryptering (Supabase Vault, administrerede nøgler)
- Storage bucket-kryptering (AWS S3, AES-256)

**Backup-sikkerhed:**
- Automatiserede daglige backups (Supabase)
- Backups krypteret i hvile
- 30-dages backup-opbevaring

### 4. Brugerkontrol

**Bruger-autentificering:**
- Skygge-brugere (ingen adgangskode-deling med LogicNodes)
- JWT-validering (partners signeringshemmelighed)
- Session-administration (1-times udløb, refresh tokens)

**Autorisation:**
- Rollebaseret adgangskontrol (admin, medlem, viewer)
- Tilladelsessystem (runs:read, runs:create osv.)
- Organisations-scoping (brugere får kun adgang til egen org-data)

### 5. Dataadskillelse

**Multi-Tenancy:**
- Database RLS-politikker (håndhæver organization_id scoping)
- Applikationslags-validering (MultiTenantRepository-mønster)
- JWT custom claims (org_id indlejret i session)

**Testdækning:**
- 85%+ sikkerhedstestdækning
- Forebyggelse af adgang på tværs af organisationer tests
- Automatiserede sikkerhedsregressionstests

### 6. Pseudonymisering

**Skygge-brugere:**
- Syntetiske e-mail-adresser ({platform_user_id}@{partner_id}.embed.logicnodes.internal)
- Ingen PII i bruger-ID'er (UUID'er)

**Revisionslogfiler:**
- Bruger-ID'er i stedet for navne/e-mails
- IP-adresser hashet (planlagt, ikke implementeret endnu)

### 7. Tilgængelighed & Modstandsdygtighed

**Infrastruktur:**
- Multi-AZ-deployment (AWS EU-North-1, via Supabase)
- Automatiseret failover (Supabase-administreret)
- 99,9% uptime SLA (Supabase)

**Katastrofegendannelse:**
- Daglige automatiserede backups
- Point-in-time gendannelse (sidste 7 dage)
- RTO: 4 timer, RPO: 15 minutter

### 8. Hændelsesstyring

**Detektion:**
- Realtidsovervågning (fejlet auth, usædvanlige mønstre)
- Automatiserede alarmer (PagerDuty-integration)
- Revisionslog-analyse (kvartalsvis gennemgang)

**Respons:**
- Hændelsesresponsplan (dokumenterede procedurer)
- 24-timers svartid (kritiske problemer)
- Post-hændelsesrapporter (inden for 5 arbejdsdage)

**Eskalering:**
- Vagtingeniør (24/7)
- Hændelseskommandør (CTO)
- Kundekommunikation (Customer Success)

### 9. Dataportabilitet & Sletning

**Eksport:**
- Agent-kørselseksport-API (JSON-format)
- Struktureret, maskinlæsbare data
- Svartid: Inden for 30 dage

**Sletning:**
- Kaskaderende sletninger (foreign key constraints)
- Automatisk storage-oprydning (triggers)
- Sletningstidslinje: 24 timer (produktion), 30 dage (backups)

### 10. Logning & Overvågning

**Revisionslogfiler:**
- Alle autentificeringshændelser logget
- Hemmeligheder-operationer logget (automatisk trigger)
- Admin-operationer logget (org/bruger-sletning)
- 1-års opbevaring

**Sikkerhedsovervågning:**
- Sporing af fejlet autentificering
- API-nøgle-brugsovervågning
- Anomali-detektion (planlagt, ikke implementeret endnu)

---

## Appendiks C: Underdatabehandler-liste

| Underdatabehandler | Tjeneste | Behandlede Data | Lokation | Beskyttelsesforanstaltninger | Kontakt |
|---------------|---------|----------------|----------|------------|---------|
| **Supabase Inc.** | Database, Autentificering, Opbevaring | Alle Personoplysninger | EU (AWS EU-North-1, Stockholm) | SOC 2, ISO 27001, GDPR DPA | privacy@supabase.com |
| **Amazon Web Services (AWS)** | Cloud-infrastruktur | Alle Personoplysninger (via Supabase) | EU (Stockholm) | SOC 1/2/3, ISO 27001, PCI DSS | aws-compliance@amazon.com |
| **Mailgun Technologies Inc. (Sinch)** | Transaktions-e-mail | E-mail, navn | USA/EU | GDPR DPA, SCC | privacy@mailgun.com |

**Sidst Opdateret:** 3. november 2025

**Ændringer:**
Partnere vil blive underrettet 30 dage før eventuelle ændringer til denne liste (ny Underdatabehandler, væsentlig ændring af eksisterende).

---

**© 2025 LogicNodes Inc. Alle rettigheder forbeholdes.**

Denne Databehandleraftale er fortrolig og beregnet til Partner-eksekvering kun.
