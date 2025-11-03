---
layout: legal
title: Ansvarlig Offentliggørelse
last_updated: 2025-11-03
lang: da
---

# LogicNodes - Politik for Ansvarlig Offentliggørelse

**Ikrafttrædelsesdato:** 3. november 2025  

**Senest Opdateret:** 3. november 2025  

**Version:** 1.0  

---

## 1. Introduktion

LogicNodes er forpligtet til at beskytte sikkerheden og privatlivet for vores partnere og deres brugere. Vi byder velkommen til og påskønner ansvarlig offentliggørelse af sikkerhedssårbarheder fra sikkerhedsforskningssamfundet.

Denne politik giver retningslinjer for sikkerhedsforskere til ansvarlig rapportering af sårbarheder og beskriver hvordan LogicNodes vil reagere.

---

## 2. Anvendelsesområde

### 2.1 Systemer Inden for Anvendelsesområdet

Sikkerhedsforskere er autoriseret til at teste følgende systemer:

**Produktionsmiljø:**
- ✅ **Webapplikation:** https://app.logicnodes.ai
- ✅ **API Endpoints:** https://api.logicnodes.ai/api/v1/*
- ✅ **Embed Autentificering:** POST /api/v1/embed/auth
- ✅ **Partner APIs:** /api/v1/partner/*
- ✅ **Organisation APIs:** /api/organizations/*

**Testmiljø:**
- ✅ **Staging:** https://staging.logicnodes.ai (hvis tilgængeligt)
- ✅ **Demo-konti:** Anmod via security@logicnodes.ai

### 2.2 Systemer Uden for Anvendelsesområdet

Følgende er **IKKE autoriseret** til test:

- ❌ Tredjepartstjenester (Supabase, AWS, Mailgun - rapporter direkte til dem)
- ❌ Fysisk sikkerhed (kontorer, datacentre)
- ❌ Social engineering (phishing, vishing)
- ❌ Denial of Service (DoS/DDoS-angreb)
- ❌ Spam eller massemail-test
- ❌ Andre kunders konti eller data (medmindre du ejer dem)

---

## 3. Sårbarheder Inden for Anvendelsesområdet

Vi er interesserede i rapporter om følgende sårbarheds-typer:

### 3.1 Kritisk Sværhedsgrad

- **Authentication Bypass** - Adgang til system uden gyldige legitimationsoplysninger
- **Authorization Bypass** - Adgang til andre organisationers data (cross-tenant datalækage)
- **Remote Code Execution (RCE)** - Udfør vilkårlig kode på vores servere
- **SQL Injection** - Injicér SQL-forespørgsler for at få adgang til/ændre database
- **Secret Exposure** - Uautoriseret adgang til API-nøgler, signeringssecrets, vault secrets

**Eksempler:**
- Omgå JWT-validering for at oprette uautoriserede sessioner
- Få adgang til organisation A's agent-kørsler fra organisation B
- Udtrække partner-signeringssecrets fra Vault uden autorisation
- Udfør vilkårlig SQL via API endpoints

### 3.2 Høj Sværhedsgrad

- **Cross-Site Scripting (XSS)** - Reflected, Stored, DOM-based
- **Cross-Site Request Forgery (CSRF)** - Tvinge autentificerede brugere til at udføre handlinger
- **Insecure Direct Object References (IDOR)** - Få adgang til ressourcer uden autorisation
- **Server-Side Request Forgery (SSRF)** - Tvinge server til at lave uautoriserede forespørgsler
- **XML External Entity (XXE)** - Behandle ondsindet XML for at få adgang til filer/systemer

**Eksempler:**
- Gem ondsindet script i agent-kørselslogs (synlig for andre brugere)
- Slet organisation via CSRF-angreb
- Få adgang til andre brugeres transskriptioner via IDOR (manipuler UUID)

### 3.3 Mellem Sværhedsgrad

- **Privilege Escalation** - Opnå højere privilegier end autoriseret (medlem → admin)
- **Information Disclosure** - Afsløre følsomme oplysninger (stack traces, config, interne IP'er)
- **Weak Cryptography** - Brug af svage algoritmer, utilstrækkelige nøglelængder
- **Session Management Issues** - Session fixation, usikker sessionopbevaring
- **Subdomain Takeover** - Overtag kontrol over ubrugte subdomæner

**Eksempler:**
- Medlemsrolle kan slette organisation (burde kræve admin)
- Fejlmeddelelser afslører databaseforbindelsesstrenge
- Session tokens udløber ikke efter logout

### 3.4 Lav Sværhedsgrad

- **Missing Security Headers** - HSTS, CSP, X-Frame-Options
- **Clickjacking** - Indlejre applikation i iframe uden X-Frame-Options
- **Open Redirects** - Omdirigere brugere til ondsindede sites
- **Verbose Error Messages** - Afsløre softwareversioner, interne stier
- **HTTP Security Issues** - Blandet indhold, usikre cookies

**Bemærk:** Sårbarheder med lav sværhedsgrad er stadig værdifulde rapporter og vil blive behandlet.

---

## 4. Sårbarheder Uden for Anvendelsesområdet

Følgende er **IKKE berettiget** til anerkendelse eller belønninger:

### 4.1 Ekskluderede Sårbarheds-typer

- ❌ **Denial of Service (DoS/DDoS)** - Overbelaste systemer med trafik
- ❌ **Brute Force-angreb** - Forsøge mange passwords/API-nøgler
- ❌ **Social Engineering** - Phishing, pretexting, vishing
- ❌ **Fysiske Angreb** - Kontorindtrængning, dumpster diving
- ❌ **Email Spoofing** - SPF/DKIM/DMARC-fejlkonfigurationer (medmindre det fører til kontokompromittering)
- ❌ **Rate Limiting** - Fravær af rate limiting (medmindre det forårsager DoS)
- ❌ **Version Disclosure** - Softwareversion i headers (kun informativt)

### 4.2 Kendte Problemer

Følgende er kendte og vil ikke blive behandlet øjeblikkeligt:

- ⚠️ **Bug Bounty-program:** Ikke implementeret endnu (planlagt til 2026)
- ⚠️ **SOC 2-certificering:** Under udvikling (estimeret 2026)
- ⚠️ **Tvunget Logout:** Ikke tilgængelig endnu (sessioner udløber efter 1 time)

---

## 5. Retningslinjer for Ansvarlig Offentliggørelse

### 5.1 Testregler

Ved test for sårbarheder skal forskere:

**GØR:**
- ✅ Test kun på dine egne konti eller med udtrykkelig tilladelse
- ✅ Brug test/demo-konti (anmod via security@logicnodes.ai)
- ✅ Begræns test til ikke-destruktive metoder
- ✅ Respekter rate limits (hold dig under 100 forespørgsler/minut)
- ✅ Stop test øjeblikkeligt hvis du opdager brugerdata
- ✅ Rapporter fund hurtigt (inden for 24 timer efter opdagelse)

**GØR IKKE:**
- ❌ Få adgang til, ændre eller slette andre brugeres data
- ❌ Udfør DoS/DDoS-angreb eller belastningstest
- ❌ Brug automatiserede scannere uden forudgående godkendelse (email security@logicnodes.ai)
- ❌ Udnyt sårbarheder ud over proof-of-concept
- ❌ Offentliggør sårbarheder før afhjælpning (90-dages embargo)
- ❌ Kræv betaling eller løsesum for sårbarheds-offentliggørelse

### 5.2 Safe Harbor

LogicNodes forpligter sig til:

- ✅ **Ikke at forfølge retssag** mod forskere der overholder denne politik
- ✅ **Arbejde med dig** for at forstå og løse problemet
- ✅ **Anerkende dit bidrag** (med din tilladelse)
- ✅ **Holde din identitet fortrolig** (hvis anmodet)

**Betingelser:**
- Du skal overholde denne politik (testregler, offentliggørelsestidslinje)
- Du skal gøre en god faith indsats for at undgå skade
- Du må ikke overtræde love i din jurisdiktion

**Ansvarsfraskrivelse:** Dette safe harbor giver ikke tilladelse til at overtræde tredjeparters servicevilkår (f.eks. Supabase, AWS). Du er ansvarlig for overholdelse af alle gældende love og vilkår.

---

## 6. Rapportering af en Sårbarhed

### 6.1 Hvordan Man Rapporterer

**Primær Kontakt:**
- **Email:** security@logicnodes.ai
- **PGP-nøgle:** Tilgængelig efter anmodning (email security@logicnodes.ai for at anmode)
- **Svartid:** Inden for 24 timer (bekræftelse), 72 timer (indledende vurdering)

### 6.2 Rapportformat

Inkluder venligst følgende information:

**Påkrævet:**
1. **Sårbarheds-type** (f.eks. SQL Injection, XSS, Authorization Bypass)
2. **Berørt System** (URL, API endpoint, komponent)
3. **Sværhedsgrads-vurdering** (Kritisk, Høj, Mellem, Lav - din mening)
4. **Trin til Reproduktion** (detaljerede, nummererede trin)
5. **Proof of Concept** (screenshots, kode, HTTP-forespørgsler)

**Valgfrit:**
6. **Konsekvensvurdering** (hvad en angriber kunne opnå)
7. **Foreslået Afhjælpning** (hvordan man fixer problemet)
8. **Dit Navn/Handle** (hvis du ønsker kredit)
9. **Offentliggørelses-tidslinje** (hvis du har specifikke krav)

**Eksempel Rapport:**

```
Emne: [SECURITY] SQL Injection i /api/organizations/{org_id}/runs

Sårbarheds-type: SQL Injection
Berørt System: POST /api/organizations/{org_id}/runs
Sværhedsgrad: Kritisk

Trin til Reproduktion:
1. Autentificer som organisationsmedlem (POST /api/v1/embed/auth)
2. Send POST-forespørgsel til /api/organizations/{org_id}/runs med payload:
   {
     "filter": "status = 'completed' OR 1=1 --"
   }
3. Observer at alle kørsler returneres (ikke kun egen organisation)

Proof of Concept:
[Screenshot der viser SQL-forespørgsel i fejlmeddelelse]
[curl-kommando til reproduktion]

Konsekvens:
Angriber kan få adgang til alle organisationers agent-kørsler og omgå RLS-politikker.

Foreslået Afhjælpning:
Brug parameteriserede forespørgsler i stedet for strengsammenkædning.

Rapportør: John Doe (john@example.com)
Offentliggørelse: 90 dage (standard)
```

### 6.3 Krypteret Rapportering (Valgfrit)

For følsomme sårbarheder kan du kryptere din rapport med PGP:

1. Anmod om PGP-nøgle: security@logicnodes.ai
2. Krypter rapport med vores public key
3. Send krypteret email til security@logicnodes.ai

**Bemærk:** PGP er valgfrit. Ukrypteret email til security@logicnodes.ai er acceptabel.

---

## 7. Responsproces

### 7.1 Tidslinje

**Inden for 24 Timer:**
- ✅ Bekræftelsesemail (bekræfter modtagelse)
- ✅ Ticket-nummer tildelt (til sporing)
- ✅ Indledende spørgsmål (hvis afklaring nødvendig)

**Inden for 72 Timer:**
- ✅ Sværhedsgrads-vurdering (vores interne klassificering)
- ✅ Validering (bekræft at sårbarhed er reproducerbar)
- ✅ Afhjælpningstidslinje (estimeret fix-dato)

**Inden for 90 Dage:**
- ✅ Afhjælpning deployeret (kritiske/høje problemer prioriteret)
- ✅ Verifikationstest (bekræft at fix virker)
- ✅ Offentlig offentliggørelse (hvis aftalt)

### 7.2 Sværhedsgrads-klassificering

LogicNodes bruger følgende sværhedsgrads-niveauer:

**Kritisk (P0):**
- Konsekvens: Fuld systemkompromittering, massiv databrud
- Afhjælpning: Inden for 24 timer
- Eksempler: RCE, authentication bypass, cross-tenant datalækage

**Høj (P1):**
- Konsekvens: Betydelig dataeksponering, privilege escalation
- Afhjælpning: Inden for 7 dage
- Eksempler: SQL injection, stored XSS, authorization bypass

**Mellem (P2):**
- Konsekvens: Begrænset dataeksponering, funktionalitetskompromittering
- Afhjælpning: Inden for 30 dage
- Eksempler: Reflected XSS, IDOR, session management-problemer

**Lav (P3):**
- Konsekvens: Minimal sikkerhedsrisiko, defense-in-depth
- Afhjælpning: Inden for 90 dage
- Eksempler: Manglende sikkerhedsheaders, verbøse fejl

**Informativ:**
- Konsekvens: Ingen umiddelbar sikkerhedsrisiko
- Afhjælpning: Backlog (ingen specifik tidslinje)
- Eksempler: Versionsoffentliggørelse, mindre konfigurationsproblemer

### 7.3 Kommunikation

**Under Undersøgelse:**
- Vi kan stille opfølgende spørgsmål for at forstå problemet
- Vi holder dig opdateret om afhjælpningsfremskridt (ugentlige opdateringer for kritisk/høj)

**Efter Afhjælpning:**
- Vi underretter dig når fix er deployed
- Vi beder om verifikation (valgfrit - du kan gen-teste)

**Offentlig Offentliggørelse:**
- Vi foretrækker 90-dages embargo før offentlig offentliggørelse
- Vi koordinerer offentliggørelse med dig (blog post, CVE, advisory)
- Med din tilladelse krediterer vi dig (navn, handle, firma)

---

## 8. Anerkendelse & Belønninger

### 8.1 Offentlig Anerkendelse

Forskere der rapporterer gyldige sårbarheder vil blive krediteret på vores Security Hall of Fame (med tilladelse):

**URL:** https://logicnodes.ai/security/hall-of-fame (kommer snart)

**Information Publiceret:**
- Navn eller handle (dit valg)
- Firma/Organisation (valgfrit)
- Sårbarheds-type (generel beskrivelse, ingen exploit-detaljer)
- Måned/År for offentliggørelse

**Opt-Out:** Hvis du foretrækker at forblive anonym, angiv venligst i din rapport.

### 8.2 Belønninger

**Aktuel Status:** Ingen bug bounty-program (planlagt til 2026)

**Fremtidige Planer:**
- Start bug bounty-program på HackerOne eller Bugcrowd
- Belønninger: $500 - $5,000 afhængig af sværhedsgrad
- Estimeret lancering: Q2 2026

**Aktuel Anerkendelse:**
- Offentlig anerkendelse (med tilladelse)
- Direkte kommunikation med ingeniørteam
- Prioriteret supportkanal (til alvorlige problemer)

---

## 9. Juridisk & Compliance

### 9.1 Safe Harbor (Udvidet)

LogicNodes vil ikke indlede retssag mod forskere der:

1. **Overholder denne politik** (testregler, offentliggørelses-tidslinje)
2. **Gør god faith indsats for at undgå skade** (ingen datatyveri, DoS, privatlivskrænkelser)
3. **Rapporterer sårbarheder hurtigt** (inden for 24 timer efter opdagelse)
4. **Ikke offentliggør** (før 90-dages embargo eller gensidig aftale)

**Hvad Safe Harbor Dækker:**
- Få adgang til systemer inden for anvendelsesområdet til testformål
- Oprette testkonti til sårbarheds-forskning
- Se dine egne data eller offentligt tilgængelige data

**Hvad Safe Harbor IKKE Dækker:**
- Få adgang til andre brugeres data (selv hvis teknisk muligt)
- Forårsage skade eller forstyrrelser (DoS, datasletning)
- Overtræde tredjeparters servicevilkår (Supabase, AWS)
- Bruge sårbarheder til personlig vinding (tyveri, bedrageri)

### 9.2 Offentliggørelses-tidslinje

**Standard Embargo:** 90 dage fra indledende rapport

**Tidlig Offentliggørelse (med gensidig aftale):**
- Hvis fix er deployed og verificeret inden for 30 dage, kan vi aftale tidligere offentliggørelse
- Koordineret offentliggørelse (samme dag blog post, CVE, advisory)

**Udvidet Embargo:**
- For komplekse problemer der kræver arkitektoniske ændringer, kan vi anmode om forlængelse
- Maksimal forlængelse: 180 dage (med forskers samtykke)

**Offentlig Offentliggørelse Efter 90 Dage:**
- Hvis LogicNodes ikke har afhjulpet inden for 90 dage, kan forsker offentliggøre
- Vi anmoder om 7-dages varsel før offentlig offentliggørelse (for at advare berørte parter)

### 9.3 CVE-tildeling

For sårbarheder der opfylder CVE-kriterier:
- LogicNodes anmoder om CVE fra MITRE eller GitHub Security Advisories
- CVE krediterer rapportør (med tilladelse)
- LogicNodes publicerer advisory på https://logicnodes.ai/security/advisories

---

## 10. Ekskluderede Parter

Følgende parter er **IKKE berettiget** til at deltage:

- ❌ LogicNodes-medarbejdere, kontraktører eller nærmeste familiemedlemmer
- ❌ Personer i lande underlagt U.S. sanktioner (Iran, Nordkorea, Syrien, Cuba, Krim)
- ❌ Personer på U.S. denied persons lists (OFAC SDN, BIS Denied Persons List)
- ❌ Mindreårige under 18 år (uden forældresamtykke)

---

## 11. Ændringer til Denne Politik

LogicNodes kan opdatere denne politik når som helst. Ændringer vil blive posted på:
**URL:** https://logicnodes.ai/security/responsible-disclosure

**Underretning:**
- Væsentlige ændringer: Annonceret via blog post, email til tidligere rapportører
- Mindre ændringer: Opdateret "Senest Opdateret" dato

**Ikrafttrædelsesdato:**
- Politikændringer træder i kraft øjeblikkeligt ved posting
- Eksisterende sårbarheds-rapporter styret af politik-version på tidspunkt for rapport

---

## 12. Ofte Stillede Spørgsmål

### 12.1 Generelt

**Q: Har I et bug bounty-program?**
A: Ikke endnu. Planlagt til Q2 2026 på HackerOne eller Bugcrowd. I øjeblikket tilbyder vi offentlig anerkendelse og taknemmelighed.  

**Q: Kan jeg bruge automatiserede scannere?**
A: Anmod venligst om tilladelse først (security@logicnodes.ai). Automatiserede scannere kan udløse rate limits eller DoS-beskyttelser.  

**Q: Kan jeg teste på produktionssystemer?**
A: Ja, men kun på dine egne konti. Anmod om testkonti via security@logicnodes.ai for sikrere test.  

**Q: Kan jeg offentliggøre før 90 dage?**
A: Kun med gensidig aftale. Vi foretrækker koordineret offentliggørelse.  

### 12.2 Anvendelsesområde

**Q: Er subdomain takeover inden for anvendelsesområdet?**
A: Ja, hvis du kan demonstrere konsekvens (f.eks. phishing, cookie-tyveri).  

**Q: Er fravær af rate limiting en gyldig rapport?**
A: Kun hvis det muliggør DoS eller brute force-angreb. Manglende rate limits alene er informative.  

**Q: Er tredjeparts-afhængigheder inden for anvendelsesområdet?**
A: Ja, hvis sårbarheden påvirker LogicNodes (f.eks. forældet bibliotek med kendt CVE). Rapporter til os og leverandøren.  

**Q: Er social engineering inden for anvendelsesområdet?**
A: Nej. Phish ikke medarbejdere, partnere eller brugere.  

### 12.3 Rapportering

**Q: Kan jeg rapportere anonymt?**
A: Ja. Brug ProtonMail eller Tutanota til anonym email. Vi holder din identitet fortrolig.  

**Q: Kan jeg rapportere via Twitter/LinkedIn?**
A: Brug venligst security@logicnodes.ai til alle rapporter. Sociale medier overvåges ikke for sikkerhedsrapporter.  

**Q: Hvad hvis min rapport er en duplikat?**
A: Vi underretter dig hvis problemet tidligere er rapporteret. Duplikater modtager stadig anerkendelse (men ingen yderligere kredit).  

**Q: Kan jeg rapportere problemer i tredjepartstjenester?**
A: Rapporter til tredjeparten (Supabase, AWS, Mailgun) direkte. Hvis problemet påvirker LogicNodes' konfiguration, rapporter også til os.  

### 12.4 Belønninger

**Q: Får jeg betaling for min rapport?**
A: Ikke i øjeblikket (intet bug bounty-program). Du modtager offentlig anerkendelse og vores taknemmelighed.  

**Q: Hvornår lanceres bug bounty?**
A: Estimeret Q2 2026, afventende indtægtsmilepæle.  

**Q: Kan jeg forhandle en belønning?**
A: For ekstraordinære fund (0-day, kritisk sværhedsgrad), kontakt security@logicnodes.ai for diskussion.  

---

## 13. Kontaktoplysninger

### Sikkerhedsteam
**Email:** security@logicnodes.ai
**PGP-nøgle:** Anmod via email
**Svartid:** Inden for 24 timer

### Generelle Henvendelser
**Email:** support@logicnodes.ai
**Formål:** Ikke-sikkerhedsspørgsmål, produktsupport

### Juridisk Afdeling
**Email:** legal@logicnodes.ai
**Formål:** Safe harbor-spørgsmål, juridiske bekymringer

---

## 14. Anerkendelser

LogicNodes takker sikkerhedsforsknings-samfundet for at hjælpe os med at beskytte vores partnere og deres brugere. Vi er taknemmelige for jeres ansvarlige offentliggørelse og samarbejde.

**Særlig Tak:**
- [Fremtid: Liste over anerkendte forskere]

---

## 15. Referencer

**Industristandarder:**
- **OWASP Top 10:** https://owasp.org/www-project-top-ten/
- **CWE (Common Weakness Enumeration):** https://cwe.mitre.org/
- **CVSS (Common Vulnerability Scoring System):** https://www.first.org/cvss/

**Offentliggørelses-politikker (Inspiration):**
- **Google VRP:** https://bughunters.google.com/
- **Microsoft MSRC:** https://www.microsoft.com/en-us/msrc
- **GitHub Security:** https://bounty.github.com/

**Ansvarlig Offentliggørelses-rammer:**
- **ISO 29147:** Sårbarheds-offentliggørelse
- **ISO 30111:** Sårbarheds-håndteringsprocesser

---

**© 2025 LogicNodes Inc. Alle rettigheder forbeholdes.**

Denne Politik for Ansvarlig Offentliggørelse træder i kraft 3. november 2025. Ved at indsende en sårbarheds-rapport accepterer du vilkårene i denne politik.
