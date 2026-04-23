---
layout: legal
title: Databehandleraftale
last_updated: 2026-04-21
lang: da
lang_equivalent: /en/data-processing-agreement/
---

# Databehandleraftale (DPA)

**Mellem:**
- **Dataansvarlig** ("[PARTNER NAVN]", "Partner", "du")
- **Databehandler** ("LogicNodes ApS", "LogicNodes", "vi", "os")

**Ikrafttrædelsesdato:** [DATO]  

---

## 1. Definitioner

### 1.1 Definerede Begreber

Til brug for denne Databehandleraftale ("DPA"):

**"GDPR"** betyder Europa-Parlamentets og Rådets forordning (EU) 2016/679 af 27. april 2016 om beskyttelse af fysiske personer i forbindelse med behandling af personoplysninger og om fri udveksling af sådanne oplysninger.

**"Databeskyttelseslovgivning"** betyder alle gældende love og regler vedrørende privatliv og databeskyttelse, herunder GDPR, UK GDPR og Data Protection Act 2018, den schweiziske FADP, CCPA/CPRA og andre gældende love.

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
- Slutbrugeridentitetsoplysninger (e-mail, navn, organisation)
- Agenteksekverings-logs (agent-prompts, -svar og API-anmodninger/svar)
- Stemmeoptagelser (lydoptagelser fra stemmebaserede agenter) og voiceprints (biometriske data, Art. 9 — jf. §2.3)
- Uploadede og hentede filer
- Revisionslogfiler

### 2.3 Voiceprints og biometriske data

Platformen tilbyder valgfri stemmeidentifikation, der anvender biometriske stemmeprofiler ("voiceprints") til at identificere talere i lydoptagelser. Voiceprints udgør biometriske data i henhold til GDPR artikel 9, stk. 1, og behandles udelukkende med henblik på talaridentifikation. Hvert voiceprint er knyttet til et selvvalgt navn.

**Særlige Kategorier:** Partner skal sikre et gyldigt retsgrundlag (f.eks. GDPR Art. 9(2)) og implementere passende beskyttelsesforanstaltninger, inden LogicNodes instrueres til at behandle voiceprints eller andre Særlige Kategorier af Personoplysninger.

---

## 3. Behandling af Personoplysninger

### 3.1 Partner-instruktioner

LogicNodes må kun behandle Personoplysninger:
1. På dokumenterede instruktioner fra Partner (via API-kald, konfigurationsindstillinger, skriftlige anmodninger til support/sikkerhedskontakter eller MSA)
2. Som nødvendigt for at levere Tjenesterne
3. Som krævet af gældende lovgivning (med varsel til Partner, hvis lovligt tilladt)

**Partner-instruktioner inkluderer:**
- Brugerautentificering via SDK (Partner leverer JWT'er med brugeridentitets-claims)
- Organisation/bruger-sletning (via platformens brugergrænseflade eller skriftlig anmodning til kontakt@logicnodes.ai)
- Håndtering af hemmeligheder (via platformens brugergrænseflade eller skriftlig anmodning til kontakt@logicnodes.ai)
- Konfiguration af dataopbevaringsperiode (default_retention_period indstilling)

### 3.2 Uautoriseret Behandling

Hvis LogicNodes mener, at Partners dokumenterede instruktioner krænker Databeskyttelseslovgivningen, vil LogicNodes:
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
- Identitetsoplysninger: E-mail, navn, bruger-ID, organisations-ID
- Brugsdata: Agentkørsler, agent-prompts og -svar, transskriptioner
- Tekniske data: IP-adresse, user agent (af sikkerhedsmæssige årsager)
- Stemmeoptagelser: Lydoptagelser fra stemmebaserede agenter; inkl. voiceprints knyttet til selvvalgte navne (biometriske data, Art. 9 — jf. §2.3; valgfri funktionalitet)
- Uploadede filer: Indsendte og hentede dokumenter

**Kategorier af Registrerede:**
- Partners slutbrugere (medarbejdere, kunder, konsulenter)

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

**Overholdelse (fremadrettet):**
- SOC 2 Type II-forberedelser er påbegyndt (rapport målrettet 2026/2027; ikke endnu certificeret)
- Årlig penetrationstest (planlagt Q3 2026)
- Automatiseret sårbarhedsscanning (via GitHub Dependabot)

### 4.3 Anmodninger fra Registrerede

LogicNodes skal assistere Partner med at opfylde Registreredes rettigheder i henhold til Databeskyttelseslovgivningen uden unødig forsinkelse.

**Ret til Indsigt (GDPR Art. 15):**
- Eksport af agentkørselshistorik via platformens brugergrænseflade eller per anmodning til kontakt@logicnodes.ai
- JSON-format til maskinlæsbar eksport
- Svartid: Inden for 30 dage

**Ret til Berigtigelse (GDPR Art. 16):**
- Partner opdaterer data via JWT (navn, e-mail-ændringer)
- Ændringer reflekteres øjeblikkeligt

**Ret til Sletning (GDPR Art. 17):**
- Sletning af bruger/organisation via platformens brugergrænseflade eller per anmodning til kontakt@logicnodes.ai
- Kaskade-sletning sikrer fuldstændig fjernelse
- Sletningsperiode: Øjeblikkeligt (produktion), 30 dage (backups)

**Ret til Dataportabilitet (GDPR Art. 20):**
- Data kan eksporteres i JSON-format via platformens brugergrænseflade eller per anmodning til kontakt@logicnodes.ai
- Strukturerede, maskinlæsbare data

**Ret til Begrænsning af Behandling (GDPR Art. 18):**
- Partner kan deaktivere brugerkonti
- Behandling stoppes (data bevares, men anvendes ikke)

**Ret til Indsigelse (GDPR Art. 21):**
- Partner evaluerer indsigelsen og instruerer LogicNodes
- Hvis berettiget, slettes data via platformens brugergrænseflade eller per anmodning til kontakt@logicnodes.ai

**Assistance:**
LogicNodes vil besvare Partner-anmodninger inden for 5 arbejdsdage og levere rimelig assistance (dokumentation, API-vejledning, teknisk support).

### 4.4 Underretning om Databrud

I tilfælde af et Databrud skal LogicNodes:

**Juridisk forpligtelse (GDPR Art. 33):**
LogicNodes skal underrette Partner **uden unødig forsinkelse** og, hvor det er muligt, inden for 72 timer efter at have fået kendskab til Databruddet.

**Internt SLA-mål (inden for 24 timer):**
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

Hvis en DPIA indikerer høj risiko, og Partner skal konsultere en Tilsynsmyndighed (GDPR Art. 36), vil LogicNodes levere nødvendige oplysninger og assistance. Enhver videregivelse vil være begrænset til oplysninger, der er strengt nødvendige for konsultationen.

---

## 5. Underdatabehandling

### 5.1 Autoriserede Underdatabehandlere

Partner giver generel autorisation til LogicNodes til at engagere Underdatabehandlere, underlagt betingelserne i dette afsnit.

**Komplet Underdatabehandler-liste:** /da/underbehandlere

<iframe src="https://docs.google.com/spreadsheets/d/e/2PACX-1vRHy76XGvurEqCuaIjMYAKlogtBJg4Maz1EOIptwtBQth89Vyaq3CM929kRdwEEf8mSbESwZrfnd9o7/pubhtml?gid=0&single=true" width="100%" height="550" frameborder="0" scrolling="no"></iframe>

Den autoritative og opdaterede liste over Underdatabehandlere vedligeholdes på /da/underbehandlere og opdateres med 30 dages forhåndsvarsel ved ændringer.

**Bring Your Own Key (BYOK) — AI-inferenstjenester:**
Partner kan til enhver tid vælge at anvende egne API-nøgler til AI-tjenester. Når egne nøgler anvendes, behandler AI-udbyderen data direkte på Partners vegne og er Partners direkte databehandler — ikke LogicNodes' underdatabehandler.

**Underdatabehandleres underdatabehandlere:** Underdatabehandlere kan engagere egne underdatabehandlere (f.eks. benytter Supabase AWS; Vercel benytter AWS/Google Cloud; Hetzner behandler data udelukkende i egne EU-datacentre). Disse er dækket af de respektive leverandørers DPA'er.

### 5.2 Krav til Underdatabehandlere

LogicNodes skal sikre, at alle Underdatabehandlere (med undtagelse af BYOK-valgte AI-udbydere, som er Partners direkte databehandlere):
1. Er bundet af databeskyttelsesforpligtelser svarende til denne DPA
2. Implementerer passende tekniske og organisatoriske sikkerhedsforanstaltninger
3. Er bundet af Databehandleraftaler eller tilsvarende kontraktuelle mekanismer, herunder Standardkontraktbestemmelser (SCC EU 2021/914) for behandlere uden for EØS
4. Undergår regelmæssige sikkerhedsvurderinger

**Afgrænsning af dokumentationsforpligtelse:** LogicNodes' forpligtelse over for Underdatabehandlere er begrænset til de mekanismer, der er angivet i kolonnen "Sikkerhed" i §5.1 og Appendiks C — dvs. at en GDPR DPA og, hvor relevant, SCC (EU 2021/914) er på plads. LogicNodes afgiver ingen erklæring om og påtager sig intet ansvar for Underdatabehandleres sikkerhedscertificeringer (herunder men ikke begrænset til SOC 2, ISO 27001 eller tilsvarende standarder), medmindre sådanne certificeringer er udtrykkeligt nævnt for den pågældende Underdatabehandler i denne DPA.

### 5.3 Nye Underdatabehandlere

**Underretning:**
LogicNodes vil underrette Partner mindst **30 dage** før engagement af nye Underdatabehandlere eller væsentlig ændring af eksisterende Underdatabehandlere.

**Underretningsmetode:**
- E-mail til Partners sikkerhedskontakt
- Opdatering til den offentlige underdatabehandler-side på /da/underbehandlere

**Indsigelse:**
Partner kan gøre indsigelse mod ny Underdatabehandler på rimelige databeskyttelsesgrunde ved at underrette LogicNodes inden for 30 dage.

**Hvis Partner Gør Indsigelse:**
- LogicNodes vil ikke engagere Underdatabehandleren
- ELLER: LogicNodes vil arbejde med Partner om at løse bekymringer
- ELLER: Hvis intet alternativ, kan Partner opsige MSA (30-dages varsel, ingen straf)

### 5.4 Underdatabehandler-ansvar

LogicNodes forbliver fuldt ansvarlig over for Partner for Underdatabehandlers præstation. Hvis Underdatabehandler fejler i at opfylde databeskyttelsesforpligtelser, er LogicNodes ansvarlig over for Partner, som hvis LogicNodes selv havde udført behandlingen. Ansvaret gælder ikke for AI-tjenester, som Partner anvender via egne API-nøgler (BYOK), idet disse udbydere i så fald er Partners direkte databehandlere.

---

## 6. Internationale Dataoverførsler

### 6.1 Datalokation

**Primær Opbevaring:** Den Europæiske Union (AWS EU-North-1, Stockholm via Supabase)

**US Data-residens (Valgfrit):** Partner kan anmode om dataopbevaring i USA. Yderligere gebyrer kan forekomme.

**Præcisering — AI-inferens:** Uanset valg af datalagringsregion indebærer standardbrug af platformen, at agent-prompts og -svar transmitteres til LLM-udbydere (OpenAI, Anthropic, Google Cloud, xAI) med servere i USA ved hver agentkørsel. Disse inferenskald udgør internationale dataoverførsler, der er dækket af SCC og de respektive Underdatabehandleres DPA'er som beskrevet i §5 og Appendiks C. Partner kan reducere omfanget af sådanne overførsler ved at anvende egne API-nøgler (BYOK), hvorved LLM-udbyderen bliver Partners direkte databehandler.

### 6.2 Overførselsmekanismer

**Standard:** Data opbevaret i EU (ingen international overførsel for EU-kunder)

For overførsler af Personoplysninger til lande uden en tilstrækkeligheds-afgørelse (hvis Partner anmoder om US-residens), stoler LogicNodes på:

**Standardkontraktbestemmelser (SCC'er):**
- EU-Kommissionens afgørelse 2021/914 (Modul 2: Dataansvarlig til Databehandler)
- Inkorporeret ved reference i denne DPA
- Fuld tekst tilgængelig på: https://eur-lex.europa.eu/eli/dec_impl/2021/914/oj

**UK-tillæg / IDTA:** For overførsler underlagt UK-lovgivning gælder ICO International Data Transfer Addendum (eller IDTA) ved inkorporering.

**Schweizisk tillæg:** For overførsler underlagt schweizisk FADP skal henvisninger til GDPR og "EU" i SCC'erne læses som henvisninger til FADP og "Schweiz".

### 6.3 Yderligere Beskyttelsesforanstaltninger

Ud over SCC'er implementerer LogicNodes supplerende foranstaltninger som krævet af Schrems II:

**Kryptering:**
- Data krypteret i hvile med AES-256 (database, hemmeligheder, opbevaring)
- Transportkryptering med TLS 1.2 eller højere
- HTTPS-håndhævelse med HSTS-headers

**Nøglehåndtering:**
- AWS KMS-administrerede krypteringsnøgler
- Automatisk nøglerotation mindst årligt
- Adgang til nøgler begrænset til tjenesterolle
- Alle dekrypteringsoperationer revisionslogges

**Adgangskontrol:**
- Multi-tenant-isolation via PostgreSQL Row-Level Security (RLS)
- JWT-baseret autentificering (RS256, 1-times udløb)
- Rollebaseret adgangskontrol (admin, medlem, viewer)
- Applikationslags-adgangskontrol (cross-tenant adgang forhindres by design)
- Mindst-privilegium princip for medarbejderadgang

**Dataminimering:**
- Konfigurerbare opbevaringsperioder (1-90 dage for operationelle data)
- Automatisk daglig oprydning
- Ingen brug af kundedata til AI-modeltræning eller -analyse
- Formålsbegrænsning håndhævet by design

**Transparens & Tilsyn:**
- Omfattende revisionslogfiler (1-års opbevaring)
- Dataeksport-API'er (JSON-format, maskinlæsbart)
- Partner-adgang til revisionslogfiler via API
- Årlige sikkerhedsvurderinger

**Myndighedsadgangsanmodninger:**
- Vi underretter Partner omgående, medmindre det er juridisk forbudt
- Vi anvender rimelige juridiske midler til at anfægte eller indsnævre alt for brede anmodninger
- Vi videregiver kun det minimum af Personoplysninger, der kræves ved lov
- Alle myndighedsanmodninger dokumenteres og rapporteres til Partner

### 6.4 Myndighedsadgangsanmodninger

Hvis LogicNodes modtager en lovlig anmodning fra offentlige myndigheder om adgang til Personoplysninger:
1. Underretter vi omgående Partner, medmindre det er juridisk forbudt
2. Anvender vi rimelige juridiske midler til at anfægte eller indsnævre anmodningen
3. Videregiver vi kun det minimum af Personoplysninger, der kræves ved lov, og dokumenterer anmodningen og videregivelsen

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

Backups er krypteret i hvile (AES-256).

### 7.2 Afslutning af Tjeneste

Ved opsigelse eller udløb af MSA skal LogicNodes (efter Partners valg):

**Mulighed A: Slet**
- Slet alle Personoplysninger inden for 30 dage
- Lever skriftlig bekræftelse på sletning, underskrevet af en autoriseret repræsentant

**Mulighed B: Returnér**
- Eksportér alle Personoplysninger i JSON-format
- Lever til Partner inden for 30 dage
- Slet efter Partner bekræfter modtagelse

**Undtagelse:** LogicNodes kan opbevare Personoplysninger i det omfang, som kræves af gældende lovgivning (f.eks. revisionslogfiler til overholdelse).

### 7.3 Partner-initieret Sletning

Partner kan til enhver tid slette data via:
- Platformens brugergrænseflade
- Skriftlig anmodning til kontakt@logicnodes.ai

LogicNodes sletter øjeblikkeligt fra produktionsdatabasen (synkron CASCADE) og fjerner fra backups inden for 30 dage.

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
- **Primær:** Fjernrevision via gennemgang af dokumentation, sikkerhedsspørgeskema og Q&A
- **Alternativ:** Tredjeparts-vurderinger (SOC 2-rapport når tilgængelig, penetrationstestresultater under NDA)
- **On-site:** Kun hvis fjernmetoder er utilstrækkelige med 60 dages forhåndsvarsel, i arbejdstiden, begrænset til rimelig varighed (1-2 arbejdsdage)

**Fortrolighed:**
Partner accepterer at underskrive NDA og begrænse adgang til fortrolige oplysninger.

**Omkostninger:**
- Første fjernrevision per år: Ingen gebyr
- On-site revisioner: Rimelige omkostninger (aftales på forhånd)
- Yderligere revisioner: Rimelige omkostninger (skal aftales)

### 8.2 LogicNodes Certificeringer

LogicNodes vil opretholde industri-standard sikkerhedspraksis og levere dokumentation på rimelig anmodning:
- SOC 2 Type II-rapport (når tilgængelig, planlagt 2026)
- Penetrationstestrapporter (årligt, under NDA)
- Underdatabehandler-sikkerhedsdokumentation (DPA'er, leverandørsikkerhedssider, tilgængelige certifikater)
- Svar på standard sikkerhedsspørgeskemaer (CAIQ, SIG, VSA)

---

## 9. Ansvar & Erstatning

### 9.1 Ansvarsbegrænsning

Begge parter er ansvarlige for tab, der direkte skyldes overtrædelse af denne DPA. Ingen af parterne er ansvarlig for indirekte tab, følgeskader eller tab af data, medmindre tabet skyldes forsæt eller grov uagtsomhed. Disse begrænsninger gælder ikke, hvor lovgivningen forbyder dem, herunder ved overtrædelse af GDPR.

### 9.2 Erstatning

LogicNodes skal skadesløsholde og holde Partner fri for:
- Krav opstået fra LogicNodes' brud på denne DPA
- Bøder pålagt af Tilsynsmyndigheder på grund af LogicNodes' manglende overholdelse af GDPR
- Registreredes krav opstået fra LogicNodes' uautoriserede behandling

**Undtagelser:**
LogicNodes er IKKE ansvarlig for krav opstået fra:
- Behandling foretaget på Partners dokumenterede instruktioner, som strider mod Databeskyttelseslovgivningen
- Partners brud på denne DPA, MSA eller Databeskyttelseslovgivning
- Hændelser forårsaget af Partners systemer, integrationer eller slutbrugere

---

## 10. Periode & Opsigelse

### 10.1 Periode

Denne DPA træder i kraft fra Ikrafttrædelsesdatoen og gælder, indtil den opsiges af en af parterne i overensstemmelse med afsnit 10.2.

### 10.2 Opsigelse

Denne DPA ophører automatisk ved opsigelse.

### 10.3 Overlevelse

Følgende afsnit overlever opsigelse:
- Afsnit 4.2 (Sikkerhedsforanstaltninger) - indtil data slettes
- Afsnit 4.4 (Underretning om Databrud) - for brud forekommet under perioden
- Afsnit 7 (Dataopbevaring & Sletning) - indtil data slettes
- Afsnit 9 (Ansvar & Erstatning) - i 2 år efter opsigelse

---

## 11. Generelle Bestemmelser

### 11.1 Lovvalg

Denne DPA er underlagt dansk ret. For GDPR-overholdelse gælder EU-databeskyttelseslovgivning i det omfang, som kræves af GDPR artikel 28(3)(a). I tilfælde af konflikt mellem denne DPA og SCC'erne vedrørende overførsler af personoplysninger har SCC'erne forrang.

### 11.2 Ændringer

LogicNodes kan opdatere denne DPA ved at give mindst 30 dages skriftligt varsel til Partner. Partner kan inden varselets udløb vælge at opsige denne DPA med virkning fra varselets udløb. Fortsætter Partner brugen af Ydelserne efter varselets udløb, anses den opdaterede DPA for accepteret.

### 11.3 Adskillelse

Hvis nogen bestemmelse i denne DPA er ugyldig eller ikke kan håndhæves, forbliver de resterende bestemmelser i fuld kraft og virkning. Den ugyldige bestemmelse skal erstattes af en gyldig bestemmelse, der opnår den oprindelige hensigt.

### 11.4 Hele Aftalen

Denne DPA udgør sammen med Privatlivspolitikken hele aftalen om databeskyttelse.

### 11.5 Rangorden

I tilfælde af konflikt:
1. Denne DPA (for databeskyttelsesmæssige spørgsmål)
2. Privatlivspolitik (for slutbrugeres datarettigheder)

---

## 12. Underskrifter

**Partner (Dataansvarlig):**

Underskrift: _______________________________  
Navn: [PARTNER AUTORISERET UNDERSKRIVER]  
Titel: _______________________________  
Dato: _______________________________  

**LogicNodes ApS (Databehandler):**

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
- Navn: LogicNodes ApS
- Adresse: Sletvej 2D, 8310 Tranbjerg, Danmark
- CVR: DK45318362
- Kontakt: kontakt@logicnodes.ai  

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

**UK-tillæg:**
Hvor det er påkrævet, udgør UK-tillægget til SCC'erne (version udstedt af ICO) en del af denne DPA.

**Schweizisk tillæg:**
For schweiziske FADP-overførsler skal henvisninger i SCC'erne til GDPR og EU-lovgivning læses som henvisninger til FADP og schweizisk lovgivning.

---

## Appendiks B: Tekniske og Organisatoriske Foranstaltninger

**Sikkerhedsforanstaltninger Implementeret af LogicNodes:**

### 1. Adgangskontrol

**Fysisk Adgang:**
- Ikke relevant (cloud-baseret infrastruktur, ingen on-premise servere)
- Supabase/AWS administrerer fysisk datacenter-sikkerhed (ISO 27001, SOC 2)

**Systemadgang:**
- Multi-faktor-autentificering (MFA) krævet for produktionsadgang
- Nøglebaseret autentificering (adgangskode-baseret login deaktiveret)
- Mindst-privilegium-adgangsprincip (rollebaseret)
- Al produktionsadgang logget til revisionsformål

**Dataadgang:**
- Row-Level Security (RLS)-politikker håndhæver multi-tenant-isolation
- JWT-baseret autentificering (RS256, 1-times udløb)
- API-nøgle-autentificering (bcrypt-hashing, vis-én-gang)
- Service role-adgang logget til revisionslogfiler

### 2. Transmissionskontrol

**Kryptering under Transmission:**
- TLS 1.2+ for al API-kommunikation
- HTTPS-håndhævelse (HTTP omdirigerer til HTTPS)
- HSTS-headers (forhindrer nedrustningsangreb)

**API-sikkerhed:**
- Hastighedsbegrænsning på autentificeringsendpoints
- Input-validering og parameteriserede forespørgsler
- SQL-injektionsforebyggelse (kun parameteriserede forespørgsler)

### 3. Opbevaringskontrol

**Kryptering i Hvile:**
- Database-kryptering (Supabase standard, AES-256)
- Hemmeligheder-kryptering (Supabase Vault via AWS KMS)
- Storage bucket-kryptering (AWS S3, AES-256)
- Nøglehåndtering: AWS KMS-administrerede nøgler, automatisk rotation mindst årligt
- Nøgleadgang: Begrænset til tjenesterolle, alle dekrypteringsoperationer revisionslogges

**Backup-sikkerhed:**
- Automatiserede daglige backups (Supabase)
- Backups krypteret i hvile
- 30-dages backup-opbevaring

### 4. Brugerkontrol

**Bruger-autentificering:**
- Skygge-brugere (ingen adgangskode-deling med LogicNodes)
- JWT-validering (partners signeringsnøgle)
- Session-administration (1-times udløb, refresh tokens)

**Autorisation:**
- Rollebaseret adgangskontrol (admin, medlem, viewer)
- Tilladelsessystem (runs:read, runs:create osv.)
- Organisations-scoping (brugere får kun adgang til egen org-data)

### 5. Dataadskillelse

**Multi-Tenancy:**
- Database RLS-politikker (håndhæver organization_id scoping)
- Applikationslags-validering (cross-tenant adgang forhindres by design)
- JWT custom claims (org_id indlejret i session)

**Testdækning:**
- Forebyggelse af adgang på tværs af organisationer tests
- Automatiserede sikkerhedsregressionstests

### 6. Pseudonymisering

**Skygge-brugere:**
- Syntetiske e-mail-adresser ({platform_user_id}@{partner_id}.embed.logicnodes.internal)
- Ingen PII i bruger-ID'er (UUID'er)

**Revisionslogfiler:**
- Bruger-ID'er i stedet for navne/e-mails
- IP-adresser håndteres i overensstemmelse med sikkerhedsovervågning og juridiske krav

### 7. Tilgængelighed & Modstandsdygtighed

**Infrastruktur:**
- Multi-AZ-deployment (AWS EU-North-1, via Supabase)
- Automatiseret failover (Supabase-administreret)
- Høj tilgængelighed via Supabase/AWS

**Katastrofegendannelse:**
- Daglige automatiserede backups
- Genopretnings-tid og -punkt mål designet til at opfylde forretningskontinuitetskrav

### 8. Hændelsesstyring

**Detektion:**
- Realtidsovervågning (fejlet auth, usædvanlige mønstre)
- Automatiserede alarmer
- Revisionslog-analyse (kvartalsvis gennemgang)

**Respons:**
- Hændelsesresponsplan (dokumenterede procedurer)
- 24-timers svartid (kritiske problemer)
- Post-hændelsesrapporter (inden for 5 arbejdsdage)

**Eskalering:**
- Teknisk team-notifikation (kritiske problemer)
- CTO/teknisk ledelse-tilsyn
- Partnerkommunikation via sikkerhedskontakt (kontakt@logicnodes.ai)

### 9. Dataportabilitet & Sletning

**Eksport:**
- Agent-kørselseksport-API (JSON-format)
- Struktureret, maskinlæsbare data
- Svartid: Inden for 30 dage

**Sletning:**
- Kaskaderende sletninger (foreign key constraints)
- Automatisk storage-oprydning (triggers)
- Sletningstidslinje: Øjeblikkeligt (produktion), 30 dage (backups)

### 10. Logning & Overvågning

**Revisionslogfiler:**
- Alle autentificeringshændelser logget
- Hemmeligheder-operationer logget (automatisk trigger)
- Admin-operationer logget (org/bruger-sletning)
- 1-års opbevaring

**Sikkerhedsovervågning:**
- Sporing af fejlet autentificering
- API-nøgle-brugsovervågning
- Løbende forbedring af anomalidetektion

---

## Appendiks C: Underdatabehandler-liste

**Autoritativ Liste:** /da/underbehandlere

<iframe src="https://docs.google.com/spreadsheets/d/e/2PACX-1vRHy76XGvurEqCuaIjMYAKlogtBJg4Maz1EOIptwtBQth89Vyaq3CM929kRdwEEf8mSbESwZrfnd9o7/pubhtml?gid=0&single=true" width="100%" height="550" frameborder="0" scrolling="no"></iframe>

Den komplette og opdaterede liste over Underdatabehandlere vedligeholdes på /da/underbehandlere. Partnere underrettes 30 dage før eventuelle ændringer til denne liste (ny Underdatabehandler, væsentlig ændring af eksisterende).

**LLM-udbydere:** Som standard leverer LogicNodes API-nøgler til LLM-tjenester. Partnere kan valgfrit levere deres egne API-nøgler, i hvilket tilfælde LLM-udbyderen bliver Partners direkte databehandler (ikke LogicNodes' underdatabehandler).

**Senest Opdateret:** 21. april 2026

---

**© 2026 LogicNodes ApS. Alle rettigheder forbeholdes.**

LogicNodes ApS  
Sletvej 2D, 8310 Tranbjerg, Danmark  
CVR: DK45318362

Denne Databehandleraftale er fortrolig og beregnet til Partner-eksekvering. Offentlig distribution er ikke tilladt.
