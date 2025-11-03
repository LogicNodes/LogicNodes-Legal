---
layout: legal
title: Sikkerhedsarkitektur
last_updated: 2025-11-03
lang: da
---

# LogicNodes Platform - Sikkerhedsarkitektur

**Til Partner Teknisk Evaluering**  

**Version:** 2.1  

**Senest Opdateret:** 2025-11-03  

**Målgruppe:** Tekniske beslutningstagere, sikkerhedsteams, compliance-ansvarlige

---

## Resumé

LogicNodes embeddable AI agent platform er designet med **enterprise-grade sikkerhed** for at beskytte dine data og dine kunders data. Dette dokument forklarer vores sikkerhedsgarantier, datahåndteringspraksis og compliance-muligheder.

### Sikkerhedsgarantier

✅ **Komplet Dataisolering** - Dine organisationers data er kryptografisk isoleret
✅ **Krypterede Secrets** - API-nøgler og legitimationsoplysninger krypteret i hvile, aldrig eksponeret til frontend
✅ **Automatiseret Dataopbevaring** - Du kontrollerer opbevaring (1-90 dage), vi håndterer automatisk oprydning
✅ **Omfattende Audit Logging** - 1-årigt audit trail af alle sikkerhedshændelser
✅ **Sikre API-nøgler** - Industristandard hashing, vis-én-gang workflow
✅ **Rate Limiting** - Beskyttelse mod misbrug og brute force-angreb
✅ **GDPR-Klar** - Ret til sletning, dataeksport, cascading deletes

---

## Indholdsfortegnelse

1. [Autentificering](#1-autentificering)
2. [Datasikkerhed](#2-datasikkerhed)
3. [API Key Management](#3-api-key-management)
4. [Secrets Management](#4-secrets-management)
5. [Dataopbevaring & Privatliv](#5-dataopbevaring--privatliv)
6. [Audit & Compliance](#6-audit--compliance)
7. [Partner-muligheder](#7-partner-muligheder)
8. [Compliance & Certificeringer](#8-compliance--certificeringer)
9. [Incident Response](#9-incident-response)
10. [Sikkerhedsbest Practices](#10-sikkerhedsbest-practices)

---

## 1. Autentificering

### 1.1 Sådan Fungerer Autentificering

Du autentificerer dine brugere til LogicNodes via signerede JWTs. Dette betyder:
- ✅ **Du kontrollerer autentificering** - Brugere opretter aldrig LogicNodes passwords
- ✅ **Øjeblikkelig tilbagekaldelse** - Stop med at udstede tokens for at tilbagekalde adgang øjeblikkeligt
- ✅ **Nul legitimationsdeling** - Vi ser aldrig dine brugeres passwords
- ✅ **Fuldt audit trail** - Alle autentificeringsforsøg logget

**Flow:**
```
Bruger logger ind på DIN platform
    ↓
DIN backend genererer JWT (signeret med dit secret)
    ↓
DIN frontend sender JWT til LogicNodes (/api/v1/embed/auth)
    ↓
LogicNodes validerer signatur og opretter session
    ↓
Bruger får adgang til AI-funktionalitet
```

### 1.2 JWT-krav

**Påkrævede Claims:**
- `user_id` - Bruger-ID i dit system
- `org_id` - Organisations-ID i dit system
- `email` - Brugerens emailadresse
- `name` - Brugerens visningsnavn
- `exp` - Token udløb (Unix timestamp)

**Valgfrie Claims:**
- `org_name` - Organisationens visningsnavn

**Eksempel JWT Payload:**
```json
{
  "user_id": "user_12345",
  "org_id": "org_67890",
  "email": "john@acme.com",
  "name": "John Doe",
  "org_name": "Acme Corporation",
  "exp": 1735689600
}
```

**Signering:**
- **Algoritme:** RS256 (RSA with SHA-256)
- **Public Key:** Du leverer din RSA public key under onboarding (gemt i vores database)
- **Private Key:** Du holder din RSA private key sikker (aldrig delt med LogicNodes)
- **Udløb:** Anbefaler maksimalt 1 time

### 1.3 Session Management

Efter succesfuld JWT-validering returnerer vi standard session tokens:

```json
{
  "user_id": "uuid",
  "organization_id": "uuid",
  "is_new_user": false,
  "session": {
    "access_token": "eyJhbGc...",
    "refresh_token": "v1.MR5S...",
    "expires_at": 1735693200,
    "expires_in": 3600
  }
}
```

**Session-egenskaber:**
- Access tokens udløber efter 1 time
- Refresh tokens kan bruges til at få nye access tokens
- Al sessionaktivitet logges til audit logs

### 1.4 Sikkerhedsfunktioner

- **Rate Limiting:** 10 forespørgsler/minut pr. IP-adresse på embed autentificeringsendpoint (forhindrer brute force)
- **Audit Logging:** Alle autentificeringsforsøg logget (succes og fejl)
- **Token-validering:** Hver API-forespørgsel validerer access token
- **Automatisk Udløb:** Sessioner udløber efter 1 times inaktivitet

---

## 2. Datasikkerhed

### 2.1 Multi-Tenant Isolering

Dine data er fuldstændigt isoleret fra andre organisationer gennem flere sikkerhedslag:

**Database-niveau:**
- Row-level security policies håndhæver organisationsgrænser
- Forespørgsler automatisk filtreret efter organization_id
- Selv privilegeret adgang respekterer organisationsscopning

**Applikationsniveau:**
- Al dataadgang kræver eksplicit organisationskontekst
- Cross-organisation forespørgsler forhindres by design
- Omfattende testdækning for isoleringsscenarier

**Session-niveau:**
- Organisations-ID indlejret i JWT (kan ikke manipuleres)
- Hver forespørgsel scopet til autentificeret brugers organisation

**Resultat:** Nul cross-organisation datalækage. Verificeret af omfattende sikkerhedstest.

### 2.2 Kryptering

**Data i Hvile:**
- Database: Krypteret (industristandard)
- Secrets: Krypteret i Vault (kan ikke dekrypteres uden korrekt adgang)
- Fillager: Krypteret (industristandard)

**Data Under Transport:**
- TLS 1.2+ til al API-kommunikation
- HTTPS-håndhævelse (HTTP omdirigerer til HTTPS)
- Certificate pinning anbefalet til mobile apps

### 2.3 Adgangskontrol

**Brugeradgang:**
- Rollebaseret adgangskontrol (admin, medlem, viewer)
- Brugere kan kun tilgå deres organisations data
- Tilladelser håndhævet på database- og applikationsniveau

**Partner API-adgang:**
- API-nøgler til backend-til-backend kommunikation
- Secrets scopet efter organisation
- Al API-adgang logget til audit logs

---

## 3. API Key Management

### 3.1 Oversigt

Generer API-nøgler til programmatisk adgang til organisationssecrets og admin-operationer. Muliggør sikker backend-til-backend kommunikation uden brugerautentificering.

### 3.2 API Key Format

**Eksempel:** `pk_yourcompany_7j2k9f3n8m4q1p6r5t0w2x9y8z7a6b5c4d3e2f1g0h`

**Struktur:**
- Præfiks: `pk_` (partner key)
- Dit firma-ID: Identificerer din organisation
- Tilfældig komponent: Kryptografisk sikker tilfældig streng

### 3.3 Sikkerhed

- **Hashing:** Industristandard bcrypt (samme som Stripe, GitHub)
- **Vis Én Gang:** Nøgle vises kun under generering, kan ikke hentes senere
- **Opbevaring:** Kun hash gemt i database (databaselækage eksponerer ikke brugbare nøgler)
- **Validering:** Constant-time sammenligning (forhindrer timing-angreb)

### 3.4 Livscyklus

**Generering:**
```bash
POST /api/v1/partner/api-key/generate
→ Returns: { "api_key": "pk_...", "prefix": "pk_yourcompany_..." }
```
⚠️ **Gem øjeblikkeligt - nøgle kan ikke hentes senere**

**Brug:**
```bash
Authorization: Bearer pk_yourcompany_...
```

**Rotation:**
- Generer ny nøgle (samme endpoint)
- Opdater dine systemer til at bruge ny nøgle
- Gammel nøgle automatisk invalideret

**Overvågning:**
```bash
GET /api/v1/partner/api-key/info
→ Returns: { "prefix": "pk_...", "created_at": "...", "last_used_at": "..." }
```

**Best Practice:** Roter nøgler hver 90. dag

---

## 4. Secrets Management

### 4.1 Oversigt

Gem krypterede API-nøgler og legitimationsoplysninger (OpenAI, Anthropic, dine platformlegitimationsoplysninger) til AI agent-eksekvering. Secrets er:
- ✅ Krypteret i hvile (kan ikke dekrypteres uden korrekt adgang)
- ✅ Aldrig eksponeret til frontend-kode
- ✅ Scopet efter organisation (isoleret fra andre orgs)
- ✅ Audit-logget (oprettelse, sletning, opdateringer)

### 4.2 Management Modes

**Partner-Managed Secrets:**
- Du kontrollerer via API (anbefalet til sikkerhedskritiske legitimationsoplysninger)
- Brugere kan ikke ændre eller slette
- Ideel til: Dine platform API-nøgler, faste integrationer

**User-Managed Secrets:**
- Brugere kan ændre via dashboard
- Ideel til: Brugers personlige API-nøgler (OpenAI, Anthropic)

### 4.3 API-operationer

**Opret/Opdater Secret (via API-nøgle):**
```bash
POST /api/v1/partner/secrets
{
  "org_id": "org_67890",
  "key": "YOUR_PLATFORM_API_KEY",
  "value": "sk_live_...",
  "description": "API key for customer integration",
  "managed_by": "partner"
}
```

**List Secrets (kun metadata):**
```bash
GET /api/v1/partner/secrets/{org_id}
→ Returns: [{ "key": "YOUR_PLATFORM_API_KEY", "description": "...", "managed_by": "partner" }]
```
⚠️ **Værdier returneres aldrig** (sikkerhed by design)

**Slet Secret:**
```bash
DELETE /api/v1/partner/secrets/{org_id}/{key}
```

### 4.4 Runtime Sikkerhed

Når AI-agenter eksekverer:
1. Secrets dekrypteres **på vores backend** (aldrig sendt til frontend)
2. Injiceret i agent-eksekverings-miljø
3. Aldrig persisteret i logs eller database
4. Automatisk ryddet efter eksekvering afsluttes

---

## 5. Dataopbevaring & Privatliv

### 5.1 Hvad Vi Gemmer

| Datatype | Opbevaring | Formål | Din Kontrol |
|----------|-----------|---------|-------------|
| Brugerprofil (email, navn) | Indtil sletning | Kontoadministration | DELETE API |
| Agent eksekveringshistorik | 1-90 dage (du konfigurerer) | Samtale kontinuitet, debugging | Konfigurerbar opbevaring |
| API forespørgsler/svar | 1-90 dage (du konfigurerer) | Agent kontekst, gennemsigtighed | Konfigurerbar opbevaring |
| Stemmetransskriptioner | 1-90 dage (du konfigurerer) | Stemmeindtastningsbehandling | Konfigurerbar opbevaring |
| Agent eksekveringskontekst (checkpoints) | 1-90 dage (du konfigurerer) | Agent state kontinuitet | Konfigurerbar opbevaring |
| Krypterede secrets | Indtil sletning | Værktøjseksekvering | DELETE API |
| Audit logs | 1 år (fast) | Sikkerhedsovervågning, compliance | Skrivebeskyttet |

### 5.2 Automatiseret Oprydning

**Daglig Oprydning (2:00 AM UTC):**
- Agent-kørsler ældre end opbevaringsperiode → **Slettet**
- Tilknyttede filer og transskriptioner → **Slettet**
- Lagerfiler uden databaserecords → **Slettet**

**Ingen manuel indgriben påkrævet.** Vi håndterer GDPR compliance automatisk.

### 5.3 Konfigurerbar Opbevaring

**Indstil opbevaringsperiode pr. organisation:**
```bash
# Via dashboard eller API
default_retention_period = 30  # dage (1-90)
```

**Use cases:**
- **Kort opbevaring (1-7 dage):** Meget følsomme data, minimal GDPR-risiko
- **Mellem opbevaring (30 dage):** Balance mellem funktionalitet og compliance
- **Lang opbevaring (90 dage):** Maksimal samtalekontinuitet

### 5.4 Datasletning

**Brugersletning:**
```bash
DELETE /api/v1/partner/organizations/{org_id}/users/{user_id}
```

**Organisationssletning:**
```bash
DELETE /api/v1/partner/organizations/{org_id}
```

**Hvad Bliver Slettet:**
- ✅ Bruger/organisationsrecords
- ✅ Alle agent-kørsler og eksekveringshistorik
- ✅ Alle uploadede filer og transskriptioner
- ✅ Alle krypterede secrets
- ✅ Organisationsmedlemskaber

**Sletningstidslinje:**
- Øjeblikkeligt: Slettet fra produktionsdatabase (synkron CASCADE)
- Inden for 30 dage: Fjernet fra krypterede backups

**Undtagelse:** Audit logs bevaret i 1 år (compliance-krav)

---

## 6. Audit & Compliance

### 6.1 Hvad Vi Logger

**Autentificeringshændelser:**
- JWT-valideringsforsøg (succes/fejl)
- Sessionoprettelse
- API-nøgle autentificering

**Secret-operationer:**
- Secret oprettelse, opdateringer, sletning
- Hvem udførte handlingen
- Tidsstempel og IP-adresse

**Admin-operationer:**
- Organisations-/brugersletning
- API-nøglegenerering
- Konfigurationsændringer

### 6.2 Audit Log Adgang

**Din Adgang:**
```bash
# Forespørg audit logs for dit partner-ID
GET /api/v1/partner/audit-logs?partner_id=yourcompany
```

**Hvad Du Ser:**
- Hændelsestype (f.eks. "jwt_validation", "api_key_authenticated")
- Tidsstempel
- IP-adresse og User-Agent
- Bruger/organisationskontekst
- Succes/fejl status
- Hændelsesdetaljer (JSON)

**Opbevaring:** Minimum 1 år

### 6.3 Use Cases

- **Sikkerhedsovervågning:** Spor mislykkede autentificeringsforsøg
- **Compliance Audits:** Demonstrer GDPR compliance
- **Incident-undersøgelse:** Gennemgå sikkerhedshændelser
- **Brugsanalyse:** Forstå partner aktivitetsmønstre

---

## 7. Partner-muligheder

### 7.1 Organisationsadministration

**List Organisationer:**
```bash
GET /api/v1/partner/organizations
```
Returnerer: Organisationsliste med brugsstatistikker (brugerantal, nylig aktivitet)

**Slet Organisation:**
```bash
DELETE /api/v1/partner/organizations/{org_id}
```
Sletter: Organisation + alle brugere, kørsler, secrets, filer (GDPR-compliant)

### 7.2 Brugeradministration

**List Brugere i Organisation:**
```bash
GET /api/v1/partner/organizations/{org_id}/users
```

**Slet Bruger:**
```bash
DELETE /api/v1/partner/organizations/{org_id}/users/{user_id}
```

### 7.3 Secret Provisionering

**Use Case:** Automatisk provisionering af dine platform API-nøgler når kunder tilmelder sig

**Workflow:**
1. Kunde aktiverer AI-funktion i din platform
2. Din backend genererer API-nøgle (POST /api/v1/partner/secrets)
3. AI-agenter kan nu kalde din platform på kundens vegne
4. Kunde deaktiverer → Du sletter secret (DELETE /api/v1/partner/secrets/{org_id}/{key})

---

## 8. Compliance & Certificeringer

### 8.1 GDPR Compliance

**Dataansvarlig vs Databehandler:**
- **Du** er Dataansvarlig (du bestemmer formål og midler til behandling)
- **Vi** er Databehandler (vi behandler data på dine vegne)

**GDPR-rettigheder Vi Understøtter:**
- ✅ Ret til Adgang (via dashboard og API)
- ✅ Ret til Sletning (DELETE APIs, cascading deletes)
- ✅ Ret til Dataportabilitet (via dashboard og API)
- ✅ Ret til Berigtigelse (opdater via dashboard og API)
- ✅ Dataminimering (opbevaringspolitikker, automatiseret oprydning)

**Databehandleraftale:**
- Skabelon tilgængelig (docs/partners/DATA_PROCESSING_AGREEMENT.md)
- GDPR Artikel 28 compliant
- Standard Contractual Clauses (SCCs) til internationale overførsler

### 8.2 Datalokalitet

**Primær:** Den Europæiske Union (AWS EU-North-1, Stockholm)

**US Residency:** Tilgængelig efter anmodning (yderligere gebyrer kan gælde)

**Internationale Overførsler:**
- Standard Contractual Clauses (EU-Kommissionen godkendt)
- Tilstrækkelige sikkerhedsforanstaltninger pr. GDPR Artikel 46

### 8.3 Infrastruktur Compliance

**Vores Infrastrukturudbyder (Supabase):**
- ✅ SOC 2 Type II certificeret
- ✅ ISO 27001 certificeret
- ✅ GDPR-compliant
- ✅ HIPAA tilgængelig (efter anmodning)

**Cloud-udbyder (AWS):**
- ✅ SOC 1, 2, 3
- ✅ ISO 27001
- ✅ PCI DSS

### 8.4 LogicNodes Certificeringer

**Aktuel:**
- ✅ SOC 2 Ready (bygget på SOC 2-principper)
- ✅ Omfattende sikkerhedsdokumentation
- ✅ Årlig penetrationstest (planlagt Q2 2026)

**Planlagt:**
- ⏳ SOC 2 Type II audit (når vi når $1M ARR, estimeret 2026)
- ⏳ ISO 27001 (til EU-kunder, estimeret 2026)
- ⏳ Bug bounty-program (Q2 2026)

### 8.5 Sub-Processors

| Udbyder | Service | Lokalitet | Certificeringer |
|---------|---------|-----------|-----------------|
| Supabase | Database, Auth, Storage | USA | SOC 2, ISO 27001, GDPR DPA |
| AWS | Cloud Infrastructure | USA | SOC 1/2/3, ISO 27001 |
| Mailgun | Transaktionelle Emails | USA/EU | GDPR DPA |

**Ændringsnotifikation:** 30 dages forhåndsvarsel før tilføjelse af nye sub-processors

---

## 9. Incident Response

### 9.1 Sikkerhedskontakt

**Email:** security@logicnodes.ai
**PGP-nøgle:** Tilgængelig efter anmodning
**Svartid:** Inden for 24 timer for kritiske problemer

### 9.2 Databrudnotifikation

Hvis vi opdager uautoriseret adgang til dine data:

**Inden for 24 Timer:**
- Inddæm bruddet (stop uautoriseret adgang)
- Underret dig via email
- Lever foreløbig incident-rapport

**Inden for 72 Timer:**
- Detaljeret incident-rapport (tidslinje, berørte data, grundårsag)
- Afhjælpningsplan (trin taget, forebyggende foranstaltninger)
- Assistance med lovpligtig notifikation (hvis påkrævet)

**Dit Ansvar:**
- Underret berørte brugere (hvis påkrævet af GDPR Artikel 34)
- Vi leverer: Berørte brugerlister, konsekvensanalyse, tekniske detaljer

### 9.3 Ansvarlig Offentliggørelse

Sikkerhedsforskere kan rapportere sårbarheder:
- **Email:** security@logicnodes.ai
- **Safe Harbor:** Vi vil ikke forfølge retssager for god-faith forskning
- **90-dages Embargo:** Giv os 90 dage til at fixe før offentlig offentliggørelse
- **Anerkendelse:** Offentlig anerkendelse i vores Security Hall of Fame

Fuld politik: [RESPONSIBLE_DISCLOSURE_POLICY.md](./RESPONSIBLE_DISCLOSURE_POLICY.md)

---

## 10. Sikkerhedsbest Practices

### 10.1 JWT Autentificering

**GØR:**
- ✅ Gem signeringssecret i miljøvariabler (aldrig i kode)
- ✅ Brug HTTPS til alle API-kald
- ✅ Indstil JWT-udløb til 1 time eller mindre
- ✅ Overvåg mislykkede autentificeringsforsøg i audit logs
- ✅ Roter signeringssecrets hver 90. dag

**GØR IKKE:**
- ❌ Hardcode signeringssecret i kildekode
- ❌ Del signeringssecret på tværs af miljøer (dev/staging/prod)
- ❌ Indstil JWT-udløb >24 timer
- ❌ Inkluder følsomme data i JWT claims (de er synlige for alle med token)
- ❌ Prøv igen mislykkede auth >10 gange/minut (du rammer rate limits)

### 10.2 API Key Management

**GØR:**
- ✅ Roter API-nøgler hver 90. dag
- ✅ Gem API-nøgler i secret management system (AWS Secrets Manager, Vault)
- ✅ Overvåg last_used_at for at opdage forældede nøgler
- ✅ Generer ny nøgle før tilbagekaldelse af gammel (zero-downtime rotation)
- ✅ Brug API-nøgler kun fra backend (aldrig frontend)

**GØR IKKE:**
- ❌ Commit API-nøgler til versionskontrol
- ❌ Del API-nøgler på tværs af teams/projekter
- ❌ Brug API-nøgler i frontend JavaScript
- ❌ Gem API-nøgler i plaintext-konfigurationsfiler

### 10.3 Secret Management

**GØR:**
- ✅ Brug `managed_by: "partner"` til sikkerhedskritiske secrets
- ✅ Roter LLM-udbyder API-nøgler hver 90. dag
- ✅ Slet secrets under kundeafvikling
- ✅ Brug separate secrets pr. miljø (dev/staging/prod)

**GØR IKKE:**
- ❌ Gem secrets på brugersynlige steder (beskrivelser, noter)
- ❌ Del secrets på tværs af organisationer
- ❌ Brug produktionssecrets i staging-miljøer

### 10.4 Dataopbevaring

**GØR:**
- ✅ Indstil opbevaringsperiode baseret på dine compliance-krav
- ✅ Kommuniker opbevaringspolitik til slutbrugere
- ✅ Eksporter kritiske data før opbevaring udløber (hvis nødvendigt)
- ✅ Gennemgå audit logs kvartalsvis

**GØR IKKE:**
- ❌ Indstil opbevaring til 1 dag (bryder samtalekontinuitet)
- ❌ Indstil opbevaring til 90 dage hvis du gemmer meget følsomt PII
- ❌ Stol på LogicNodes til langtidsarkivering (vi auto-sletter)

### 10.5 Sikkerhedsovervågning

**Anbefalet:**
- ✅ Overvåg audit logs for mislykkede autentificeringsforsøg
- ✅ Opsæt alarmer for usædvanlig aktivitet (f.eks. 10+ mislykkede logins)
- ✅ Gennemgå API-nøgle last_used_at månedligt (opdage kompromitterede nøgler)
- ✅ Tjek for uautoriserede organisations-/brugersletninger
- ✅ Eksporter audit logs til din egen compliance (1-års opbevaring)

---

## 11. Ofte Stillede Spørgsmål

### 11.1 Generel Sikkerhed

**Q: Hvor gemmes data?**
A: Den Europæiske Union (AWS EU-North-1, Stockholm). US data residency tilgængelig efter anmodning.  

**Q: Er data krypteret?**
A: Ja. Krypteret i hvile (database, secrets, lager) og under transport (TLS 1.2+).  

**Q: Har I SOC 2?**
A: Ikke endnu. Vi er SOC 2-klar (bygget på SOC 2-principper). Formel audit planlagt når vi når $1M ARR (estimeret 2026).  

**Q: Kan I signere tilpassede sikkerhedsspørgeskemaer?**
A: Ja. Send til security@logicnodes.ai. Svartid: 5-10 arbejdsdage.  

### 11.2 Autentificering

**Q: Kan brugere logge direkte ind på LogicNodes?**
A: Brugere autentificeret via din JWT kan ikke (by design). De kan kun tilgå gennem din platform.  

**Q: Hvordan tilbagekalder jeg adgang for en bruger?**
A: Stop med at udstede JWTs til den bruger. Eksisterende sessioner udløber inden for 1 time.  

**Q: Hvad hvis mit signeringssecret kompromitteres?**
A: Kontakt security@logicnodes.ai øjeblikkeligt. Vi roterer dit secret og invaliderer alle sessioner.  

### 11.3 Data & Privatliv

**Q: Logger I API-forespørgsler til min platform?**
A: Ja, i agent eksekveringslogs (til debugging og samtalekontinuitet). Opbevaring: 1-90 dage (du konfigurerer).  

**Q: Hvordan overholder jeg GDPR-sletteanmodninger?**
A: Brug vores DELETE APIs. Cascading deletes sikrer komplet datafjernelse inden for 24 timer (produktion) + 30 dage (backups).  

**Q: Slettes audit logs ved brugersletning?**
A: Nej. Audit logs bevaret i 1 år for compliance. De indeholder kun bruger-IDs (ingen PII).  

**Q: Kan jeg eksportere alle data for en bruger?**
A: Brugere kan se og eksportere deres data via dashboard. API-adgang til agent-kørsler tilgængelig via GET endpoints.  

### 11.4 Secrets

**Q: Hvad hvis jeg mister min API-nøgle?**
A: Generer en ny (POST /api/v1/partner/api-key/generate). Gammel nøgle automatisk invalideret.  

**Q: Kan LogicNodes-medarbejdere se mine secrets?**
A: Secrets er krypteret. Service role kan dekryptere (logget og begrænset til on-call engineers til support), men adgang er sjælden og logget.  

**Q: Er secrets synlige for mine brugere?**
A: Nej. Secrets er backend-only. Aldrig eksponeret til frontend-kode.  

### 11.5 Compliance

**Q: Har I en DPA?**
A: Ja. Skabelon tilgængelig på [DATA_PROCESSING_AGREEMENT.md](./DATA_PROCESSING_AGREEMENT.md).  

**Q: Er I HIPAA-compliant?**
A: Infrastruktur er HIPAA-capable (Supabase Business plan). Applikationsniveau BAA tilgængelig for healthcare-kunder.  

**Q: Kan I levere en sub-processor liste?**
A: Ja. Se Sektion 8.5 (Supabase, AWS, Mailgun). Fuld liste i DPA-skabelon.  

---

## 12. Kontakt & Support

### Sikkerhedsteam
**Email:** security@logicnodes.ai
**Svartid:** 24 timer for kritiske problemer

### Privatliv & Compliance
**Email:** privacy@logicnodes.ai
**Svartid:** 5 arbejdsdage

### Salg & Partnerskaber
**Email:** sales@logicnodes.ai
**Formål:** DPA-eksekvering, tilpassede aftaler, sikkerhedsspørgeskemaer

### Teknisk Support
**Email:** support@logicnodes.ai
**Svartid:** 4 arbejdstimer

---

## Dokumenthistorik

| Version | Dato | Ændringer |
|---------|------|-----------|
| 1.0 | 2025-01-31 | Indledende sikkerhedsoversigt |
| 2.0 | 2025-11-03 | Omfattende omskrivning (API-nøgler, audit logs, partner admin) |
| 2.1 | 2025-11-03 | Partner-fokuseret revision (fjernede interne implementeringsdetaljer) |

---

**© 2025 LogicNodes Inc. Alle rettigheder forbeholdes.**

Dette dokument er fortroligt og beregnet kun til partnerevaluering. Må ikke distribueres uden tilladelse.
