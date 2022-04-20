---
title: Vurder risici for beskyttelse af personlige oplysninger, og identificer følsomme elementer med Microsoft 365
ms.author: bcarter
author: brendacarter
f1.keywords:
- NOCSH
manager: laurawi
ms.date: 07/13/2020
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- m365solution-infoprotection
- m365solution-scenario
ms.custom: ''
description: Bestem reglerne for beskyttelse af personlige oplysninger, de relevante scenarier, din parathed og de følsomme oplysningstyper, der findes i dit Microsoft 365 miljø.
ms.openlocfilehash: e2d87599315e7bb43b289d74b5f192b29aecd965
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/20/2022
ms.locfileid: "64973468"
---
# <a name="assess-data-privacy-risks-and-identify-sensitive-items-with-microsoft-365"></a>Vurder risici for beskyttelse af personlige oplysninger, og identificer følsomme elementer med Microsoft 365

Vurdering af reglerne for beskyttelse af personlige oplysninger og risici, som din organisation er underlagt, er et første skridt, før du implementerer relaterede forbedringshandlinger, herunder handlinger, der kan opnås med Microsoft 365 funktioner og tjenester.

## <a name="potentially-applicable-data-privacy-regulations"></a>Gældende regler for beskyttelse af personlige oplysninger

Hvis du vil have en god reference til den bredere lovgivningsmæssige ramme for bestemmelser om beskyttelse af personlige oplysninger, skal du se [Microsoft Services Trust Portal](https://servicetrust.microsoft.com/) og [i rækken af artikler om gdpr-forordningen (General Data Protection Regulation).](/compliance/regulatory/gdpr) Gennemse også materialer om de regler, du kan være underlagt i din branche eller dit område.

### <a name="gdpr"></a>GDPR

GDPR er den mest kendte og citerede forordning om beskyttelse af personlige oplysninger. Den regulerer indsamling, opbevaring, behandling og deling af alle personoplysninger, der er relateret til en identificeret eller identificerbar fysisk person, der er bosat i EU.

Ifølge GDPR-artikel 4:

- »personoplysninger«: enhver oplysning vedrørende en identificeret eller identificerbar fysisk person (»den registrerede«). en identificerbar fysisk person er en person, der direkte eller indirekte kan identificeres, navnlig ved henvisning til en identifikator, f.eks. et navn, et identifikationsnummer, placeringsdata, en onlineidentifikator eller til en eller flere faktorer, der er specifikke for den pågældende fysiske persons fysiske, fysiologiske, genetiske, mentale, økonomiske, kulturelle eller sociale identitet.

### <a name="iso-27001"></a>ISO 27001

Adskillige europæiske tilsynsmyndigheder har også anerkendt overholdelse af andre standarder som ISO 27001 som en gyldig hensigtserklæring på tværs af mennesker, processer og teknologispektrer. De standarder, der specificerer overlapning og overholdelse af ISO-27001-drevne beskyttelsesmekanismer, kan betragtes som en proxy, der opfylder visse forpligtelser til beskyttelse af personlige oplysninger under visse omstændigheder.

### <a name="other-data-privacy-regulations"></a>Andre bestemmelser om beskyttelse af personlige oplysninger

Andre fremtrædende regler for beskyttelse af personlige oplysninger angiver også krav til håndtering af personlige data.

I USA omfatter disse loven om forbrugerbeskyttelse i Californien ([CCPA](/compliance/regulatory/ccpa-faq)), HIPAA-HITECH (USA loven om beskyttelse af personlige oplysninger for sundhedspleje) og Graham Leach Bliley Act (GLBA). Yderligere statsspecifikke bestemmelser er også på plads eller under udvikling.

Rundt om i verden kan du finde yderligere eksempler på Germany's National GDPR Implementation Act (BDSG), LGPD (Brasilien Data Protection Act) og mange andre.

## <a name="regulation-mapping-to-microsoft-365-technical-control-categories"></a>Tilknytning af regulering til Microsoft 365 tekniske kontrolkategorier

Mange af de bestemmelser, der vedrører beskyttelse af personlige oplysninger, har overlappende krav, så du skal forstå, hvilke regler de er underlagt, før du udvikler en teknisk kontrolordning.

Til senere henvisninger i artiklerne i denne overordnede løsning indeholder denne tabel uddrag fra en stikprøve af regler for beskyttelse af personlige oplysninger.

|Forordning|Artikel/sektion|Uddrag|Relevante tekniske kontrolkategorier|
|---|---|---|---|
|GDPR|Artikel 5, stk. 1, litra f)|Personoplysninger skal behandles på en måde, der sikrer passende sikkerhed for personoplysningerne, herunder beskyttelse mod uautoriseret eller ulovlig behandling og mod utilsigtet tab, ødelæggelse eller skade, ved hjælp af passende tekniske eller organisatoriske foranstaltninger ("integritet og fortrolighed".|(Alle) <br> Identitet <br> Enhed <br> Trusselsbeskyttelse <br> Beskyt oplysninger <br> Styr oplysninger <br> Opdag og svar|
||Artikel 32, stk. 1, litra a)|Under hensyntagen til den tekniske udvikling, gennemførelsesomkostningerne og behandlingens art, omfang, sammenhæng og formål samt risikoen for varierende sandsynlighed og alvor for fysiske personers rettigheder og friheder skal den dataansvarlige og databehandleren iværksætte passende tekniske og organisatoriske foranstaltninger for at sikre et sikkerhedsniveau, der svarer til risikoen.  herunder bl.a. efter behov: (a) pseudonymisering og kryptering af personoplysninger.|Beskyt oplysninger|
||Artikel 13, stk. 2, litra a)|"... den dataansvarlige skal på det tidspunkt, hvor der indhentes personoplysninger, give den registrerede følgende yderligere oplysninger, der er nødvendige for at sikre en retfærdig og gennemsigtig behandling: (a) den periode, hvor personoplysningerne vil blive opbevaret, eller hvis dette ikke er muligt, de kriterier, der anvendes til at fastslå den pågældende periode.|Styr oplysninger|
||Artikel 15, stk. 1, litra e)|Den registrerede har ret til fra den dataansvarlige at få bekræftet, om personoplysninger om ham eller hende behandles, og hvis det er tilfældet, adgang til personoplysningerne og følgende oplysninger: e) tilstedeværelsen af retten til at anmode den dataansvarlige om at korrigere eller slette personoplysninger eller begrænsning af behandlingen af den registreredes personoplysninger eller gøre indsigelse mod sådanne Behandling|Opdag og svar|
|LGPD|Artikel 46|Behandlingsagenter skal vedtage sikkerheds-, tekniske og administrative foranstaltninger, der kan beskytte personoplysninger mod uautoriseret adgang og hændelige eller ulovlige situationer med ødelæggelse, tab, ændring, kommunikation eller enhver form for uretmæssig eller ulovlig behandling.|Beskyt oplysninger <br> Styr oplysninger <br> Opdag og svar|
||Artikel 48|Den dataansvarlige skal underrette den nationale myndighed og den registrerede om forekomsten af en sikkerhedsrisiko, der kan medføre risiko eller relevant skade på den registrerede.|Opdag og svar|
|HIPPA-HITECH|45 CFR 164.312(e)(1)|Implementer tekniske sikkerhedsforanstaltninger for at beskytte mod uautoriseret adgang til elektroniske beskyttede sundhedsoplysninger, der overføres via et elektronisk kommunikationsnetværk.|Beskyt oplysninger|
||45 F.F.R. 164.312(e)(2)(ii)|Implementer en mekanisme til kryptering af elektroniske beskyttede tilstandsoplysninger, når det skønnes hensigtsmæssigt.|Beskyt oplysninger|
||45 CFR 164.312(c)(2)|Implementere elektroniske mekanismer til at bekræfte, at elektroniske beskyttede sundhedsoplysninger ikke er blevet ændret eller destrueret på en uautoriseret måde.|Styr oplysninger|
||45 CFR 164.316(b)(1)(i)|Hvis en handling, aktivitet eller vurdering af denne subpart kræves for at blive dokumenteret, skal du vedligeholde en skriftlig (som kan være elektronisk) registrering af handlingen, aktiviteten eller vurderingen|Styr oplysninger|
||45 CFR 164.316(b)(1)(ii)|Bevar den dokumentation, der kræves i henhold til afsnit b) (1) i dette afsnit i seks år fra oprettelsesdatoen eller datoen for sidste anvendelse, alt efter hvad der sker senere.|Styr oplysninger|
||45 F.F.R. 164.308(a)(1)(ii)(D)|Implementer procedurer for regelmæssigt at gennemse poster over aktiviteter i informationssystemet, f.eks. overvågningslogge, adgangsrapporter og sporingsrapporter for sikkerhedshændelser|Opdag og svar|
||45 F.F.R. 164.308(a)(6)(ii)|Identificere og reagere på formodede eller kendte sikkerhedshændelser; i det omfang det er praktisk muligt at afhjælpe skadelige virkninger af sikkerhedshændelser, der er kendt af den dækkede enhed eller forretningspartner og dokumentere sikkerhedshændelser og deres resultater.|Opdag og svar|
||45 F.F.R. 164.312(b)|Implementer hardware-, software- og proceduremekanismer, der registrerer og undersøger aktiviteter i informationssystemer, der indeholder eller bruger elektroniske beskyttede tilstandsoplysninger.|Opdag og svar|
|CCPA|1798.105(c)|En virksomhed, der modtager en verificerbar anmodning fra en forbruger om at slette forbrugerens personlige oplysninger i henhold til underinddeling (a) i dette afsnit, skal slette forbrugerens personlige oplysninger fra dens poster og bede tjenesteudbydere om at slette forbrugerens personlige oplysninger fra deres registre|Opdag og svar|
||1798.105(d)|(undtagelser fra 1798.105(c) <br> En virksomhed eller en tjenesteyder er ikke forpligtet til at opfylde en forbrugers anmodning om at slette forbrugerens personlige oplysninger, hvis det er nødvendigt for virksomheden eller tjenesteudbyderen at vedligeholde forbrugerens personlige oplysninger med henblik på: (se den aktuelle forordning for yderligere oplysninger).|Opdag og svar|
|||||

> [!IMPORTANT]
> Det er ikke meningen, at dette skal være en udtømmende liste. Se [Overholdelsesstyring](../compliance/compliance-manager.md) eller din juridiske rådgiver eller rådgiver for overholdelse af angivne standarder for at få yderligere oplysninger om anvendeligheden af de citerede afsnit i de angivne tekniske kontrolkategorier.

## <a name="knowing-your-data"></a>At kende dine data

Uanset hvilke regler du er underlagt, hvor forskellige brugerdatatyper i og uden for din organisation interagerer med dine systemer, er alle vigtige faktorer, der kan påvirke din overordnede strategi for beskyttelse af personlige oplysninger, underlagt de branche- og offentlige bestemmelser, der gælder for din organisation. Dette omfatter, hvor personlige data gemmes, hvilken type de er, og hvor meget af dem der er, og under hvilke omstændigheder de blev indsamlet.

![Viden om dine data: Hvilken type det er, og hvor meget af dem der er, og under hvilke omstændigheder det blev indsamlet.](../media/information-protection-deploy-assess/information-protection-deploy-assess-knowing-data.png)

### <a name="data-portability"></a>Dataportabilitet

Data flyttes også rundt over tid, efterhånden som de behandles, finjusteres og andre versioner af dem. Et indledende snapshot er aldrig nok. Der skal være en løbende proces for at kende dine data. Dette er en af de største udfordringer for store organisationer, der håndterer store mængder personlige data. Organisationer, der ikke løser problemet "kend dine data", kan potentielt ende med meget høj risiko og mulige bøder fra regulerende myndigheder.

![Datalivscyklussen.](../media/information-protection-deploy-assess/information-protection-deploy-assess-data-lifecycle.png)

### <a name="where-the-personal-data-is"></a>Hvor de personlige data er

For at håndtere regler for beskyttelse af personlige oplysninger kan du ikke stole på generelle begreber om, hvor du mener, at der findes personlige data, hverken nu eller i fremtiden. Bestemmelser om beskyttelse af personlige oplysninger kræver, at organisationer beviser, at de ved, hvor personlige data er løbende. Det gør det vigtigt at tage et indledende snapshot af alle dine datakilder for at få mulighed for at lagre personlige oplysninger, herunder dit Microsoft 365 miljø, og etablere mekanismer til løbende overvågning og registrering.

Hvis du ikke allerede har vurderet din overordnede parathed og risiko i forbindelse med regler for beskyttelse af personlige oplysninger, skal du bruge følgende tretrinsramme for at komme i gang.

![Trin til at vurdere din overordnede parathed og risiko, der er knyttet til regler for beskyttelse af personlige oplysninger.](../media/information-protection-deploy-assess/information-protection-deploy-assess-grid.png)

> [!NOTE]
> Denne artikel og dens indhold er ikke beregnet til at træde i stedet for juridiske rådgivningstjenester. Den indeholder blot nogle grundlæggende vejledninger og links til værktøjer, der kan være til hjælp i de tidlige faser af din vurdering.

## <a name="step-1-develop-a-foundational-understanding-of-your-organizations-personal-data-scenarios"></a>Trin 1: Udvikl en grundlæggende forståelse af organisationens scenarier med personlige data

Du skal måle eksponeringen for risikoen for beskyttelse af personlige oplysninger på baggrund af den type personlige data, der i øjeblikket administreres, hvor de er gemt, hvilke beskyttende kontrolelementer der er placeret på dem, hvordan livscyklussen administreres, og hvem der har adgang til dem.

Som udgangspunkt er det vigtigt at gøre status over, hvilke typer personlige data der findes i dit Microsoft 365 miljø. Brug disse kategorier:

- Medarbejderdata, der kræves for at udføre daglige forretningsfunktioner
- Data, som organisationen har om sine forretningskunder, partnere og andre relationer i B2B-scenariet (business-to-business)
- Data, som organisationen har om forbrugere, der leverer oplysninger til onlinetjenester, som organisationen administrerer i B2C-scenariet (business-to-customer)

Her er et eksempel på de forskellige datatyper for typiske afdelinger i en organisation.

![Typer af personlige data.](../media/information-protection-deploy-assess/information-protection-deploy-assess-data-types.png)

Mange af de personlige data, der er underlagt lovgivningen om beskyttelse af personlige oplysninger, indsamles typisk og gemmes uden for Microsoft 365. Alle personlige data fra forbrugerorienterede web- eller mobilapps skal være blevet eksporteret fra sådanne applikationer for at Microsoft 365 for at være underlagt kontrol af beskyttelse af personlige oplysninger inden for Microsoft 365.

Eksponeringen af beskyttelse af personlige oplysninger i Microsoft 365 kan være mere begrænset i forhold til dine webprogrammer og CRM-systemer, som denne løsning ikke løser.

Det er også vigtigt at tænke på følgende almindelige udfordringer med overholdelse af angivne standarder for beskyttelse af personlige oplysninger, når du evaluerer din risikoprofil:

- **Distribution af personlige data.** Hvor spredte er oplysninger om et bestemt emne? Er det kendt nok til at overbevise de regulerende organer om, at der er en ordentlig kontrol på plads? Kan det undersøges og afhjælpes, hvis det er nødvendigt?
- **Beskyttelse mod eksfiltration.** Hvordan beskytter du personlige data af en given type eller kilde mod at blive kompromitteret, og hvordan du reagerer, hvis de var det?
- **Beskyttelse i forhold til risiko.** Hvilke mekanismer til beskyttelse af oplysninger er passende i forhold til risikoen, og hvordan man sikrer virksomhedens kontinuitet og produktivitet og minimerer slutbrugerens indvirkning, hvis det er nødvendigt at gribe ind over for slutbrugerne? Skal der f.eks. bruges manuel klassificering eller kryptering?
- **Opbevaring af personlige data.** Hvor længe skal oplysninger, der indeholder personlige data, opbevares af gyldige forretningsmæssige årsager, og hvordan man undgår tidligere keep-it-forever-praksis, der er afbalanceret med opbevaringsbehov for forretningskontinuitet?
- **Håndtering af dataemneanmodninger.** Hvilke mekanismer skal der bruges til at håndtere DSR-anmodninger (data subject requests) og eventuelle afhjælpende handlinger, f.eks. anonymisering, redaction og sletning?
- **Løbende overvågning og rapportering.** Hvilken slags daglige overvågnings-, undersøgelses- og rapporteringsteknikker er tilgængelige for de forskellige datatyper og kilder?
- **Begrænsninger for databehandling.** Er der begrænsninger for dataanvendelse for oplysninger, der indsamles eller gemmes via disse metoder, som organisationen skal afspejle i kontrolelementerne til beskyttelse af personlige oplysninger? Forpligtelser, der ikke bruges af salgsafdelingen, kan f.eks. kræve, at din organisation anvender mekanismer til at forhindre overførsel eller lagring af disse oplysninger i systemer, der er knyttet til salgsorganisationen.

### <a name="employee-data-required-to-carry-out-day-to-day-business-functions"></a>Medarbejderdata, der kræves for at udføre daglige forretningsfunktioner

Organisationer skal i sagens natur indsamle data om medarbejdere til elektroniske identitets- og HR-formål, afhængigt af hvad de accepterer i deres medarbejderaftaler. Så længe en person arbejder for en virksomhed, er dette normalt ikke et problem. Organisationen ønsker måske at indføre mekanismer til at forhindre ondsindede aktører fra exfiltration eller lække medarbejderens personlige data.

Hvis en person forlader en virksomhed, har organisationer typisk processer, procedurer og planer for opbevaring og sletning til fjernelse af brugerkonti, nedlukning af postkasser og personlige drev og ændring af medarbejderstatus i f.eks. HR-systemer. I situationer, hvor der er tale om procesførelse, kan en medarbejder eller en anden part i en juridisk undersøgelse have gyldige grunde til at indhente oplysninger om personlige data, der er gemt i organisationens systemer. I nogle tilfælde kan den pågældende part anmode om, at sådanne data fjernes eller anonymiseres.

For at imødekomme sådanne behov bør organisationer have indført processer og procedurer, der håndterer forebyggende, detektiviske og afhjælpende behov for at lette sådanne anmodninger, idet det bemærkes, at nogle oplysninger om en medarbejder med rimelighed kan anses for at være afgørende for forretningskontinuitet. Det kan f.eks. være oplysninger, som en person har oprettet en fil eller udført en funktion.

> [!NOTE]
> Du kan få oplysninger om undersøgelses- og afhjælpningsteknikker i forbindelse med personlige data i Microsoft 365 i [artiklen Overvåg og besvar](information-protection-deploy-monitor-respond.md). Det kan også være en god idé at anvende automatiserede klassificerings- og beskyttelsesordninger for at sikre, at personlige data styres i organisationen, samt forhindre den i at forlade organisationen i ondsindede agentsituationer. Du kan få flere oplysninger i [artiklen om beskyttelse af oplysninger](information-protection-deploy-protect-information.md) .

### <a name="data-the-organization-has-about-its-business-customers-in-the-b2b-scenario"></a>Data, som organisationen har om sine forretningskunder i B2B-scenariet

Indsamling af B2B-oplysninger er også en udfordring, fordi din organisation muligvis har brug for at registrere kundenavne og transaktioner i sine forskellige systemer med henblik på forretningskontinuitet, men beskytte disse oplysninger mod utilsigtet eller ondsindet eksfiltration. På samme måde som med medarbejderdata skal organisationer have politikker, procedurer og tekniske kontroller på plads for at beskytte disse data samt udælde dem i henhold til definerede planer for opbevaring og sletning.

Kontrakter med eksterne kunder, partnere og andre enheder, som organisationen gør forretning med, vil typisk have sprog til håndtering af sådanne data, herunder beskyttelse, opbevaring og sletning både under og efter, at enheden har en relation til organisationen.

### <a name="data-the-organization-has-about-consumers-who-provide-information-to-online-services-that-the-organization-manages-in-the-b2c-scenario"></a>Data, som organisationen har om forbrugere, der leverer oplysninger til onlinetjenester, som organisationen administrerer i B2C-scenariet

Denne kategori er den kategori, som de fleste tænker på i forbindelse med beskyttelse af personlige oplysninger på grund af mange offentlige forekomster af kundedatalækage. Dette kan være bevidst, f.eks. en tredjepart, der er kontraktligt med udbyderen, eller utilsigtet, f.eks. exfiltration af en ondsindet aktør. Beskyttelse af forbrugerdata er en af de primære årsager til, at EU og andre har vedtaget disse bestemmelser. Bestemmelser om beskyttelse af personlige oplysninger, f.eks. GDPR og CCPA, kræver, at du planlægger følgende:

- [Handlingsplaner](/compliance/regulatory/gdpr-action-plan) og [kontrollister for ansvarlighedsparathed](/compliance/regulatory/gdpr-arc-Office365)
- [Konsekvensvurderinger af databeskyttelse](/compliance/regulatory/gdpr-data-protection-impact-assessments)
- [Meddelelser om brud](/compliance/regulatory/gdpr-breach-Office365)
- [Anmodninger fra den registrerede](/compliance/regulatory/gdpr-dsr-Office365)

Hvis din organisation ikke foretager en masse indsamling af data direkte fra forbrugere, kan denne kategori være mindre af et problem. Du skal muligvis stadig gennemgå de processer, der er beskrevet i disse artikler, for at opnå overholdelse af angivne standarder.

### <a name="step-1-summary"></a>Trin 1 - oversigt

At forstå din eksponering for risici og regler for beskyttelse af personlige oplysninger er et vigtigt første skridt, der er baseret på en grundlæggende forståelse af organisationens personlige datascenarier.

Hvis du ikke har personlige data fra forbrugere i dit Microsoft 365 miljø, eller hvis de er begrænset til visse dele af miljøet, og behovet for en teknisk kontrol er baseret på eksponering af data af forbrugertypen, skal denne tekniske kontrol muligvis kun anvendes i dele af miljøet med høj risiko, ikke overalt.

Selvom en ekstern organisation eller anbefaling af standardkontrolsæt, f.eks. fra Overholdelsesstyring i Microsoft 365, kan hjælpe med at informere din kontrolstrategi, bør dit valg af implementering styres af datalagerbevidstheden for at kvantificere din reelle risikoeksponering.

De fleste organisationer vil have en vis eksponering over for et af ovenstående scenarier. Det er vigtigt at have en holistisk tilgang til vurdering.

## <a name="step-2-assess-your-readiness-for-complying-with-data-privacy-regulations"></a>Trin 2: Vurder, om du er parat til at overholde reglerne for beskyttelse af personlige oplysninger

Selvom de er specifikke for GDPR, giver spørgsmålene i det gratis [Microsoft GDPR-vurderingsværktøj](https://clouddamcdnprodep.azureedge.net/gdc/1863571/original) et godt udgangspunkt for at forstå din overordnede parathed til beskyttelse af personlige oplysninger.

Organisationer, der er underlagt andre bestemmelser om beskyttelse af personlige oplysninger, f.eks. CCPA i USA eller Brasiliens LGPD, kan også drage fordel af dette værktøjs oversigt over parathed på grund af overlappende bestemmelser med GDPR.

GDPR-vurderingen består af følgende afsnit:

|Afsnit|Beskrivelse|
|:-------|:-----|
|Styring|<ol><li>Angiver din politik om beskyttelse af personlige oplysninger eksplicit, hvilke data der behandles? </li><li>Kører du jævnligt konsekvensvurderinger af beskyttelse af personlige oplysninger? </li><li> Bruger du et værktøj til at administrere personlige oplysninger (PI)? </li><li> Har du juridisk myndighed til at drive forretning ved hjælp af PI-data på en given person? Sporer du samtykke til data? </li><li> Sporer, implementerer og administrerer du overvågningskontrolelementer? Overvåger du for datalækager? </li></ol>|
|Sletning og meddelelse|<ol><li>Giver du eksplicitte instruktioner om, hvordan brugernes data kan tilgås? </li><li> Har du dokumenterede processer på plads til håndtering af fravalgssamtykke? </li><li> Har du en proces til automatisk sletning af data? </li><li> Har du en proces til validering af identitet, når du interagerer med en kunde? </li></ol>|
|Risikomitigering og informationssikkerhed|<ol><li>Bruger du værktøjer til at scanne ustrukturerede data? </li><li>Er alle servere opdaterede, og bruger du firewalls til at beskytte dem? </li><li>Kører du almindelige sikkerhedskopier af dine servere? </li><li>Overvåger du aktivt for datalækager? </li><li>Krypterer du dine inaktive data og i overførsel? </li></ol>|
|Politikadministration|<ol><li>Hvordan administrerer du dine bindingsregler for virksomheder? </li><li>Sporer du samtykke til data? </li><li> Dækker dine kontrakter dataklassificeringer og håndteringskrav på en skala fra 1 til 5, hvor 5 er helt dækket? </li><li>Har du og tester regelmæssigt en plan for svar på hændelser? </li><li>Hvilken politik bruger du til at administrere adgang? </li></ol>|
|||

## <a name="step-3-identify-sensitive-information-types-that-occur-in-your-microsoft-365-environment"></a>Trin 3: Identificer følsomme oplysningstyper, der forekommer i dit Microsoft 365 miljø

Dette trin omfatter identifikation af bestemte følsomme informationstyper, der er underlagt specifikke lovmæssige kontroller, samt forekomsten af dem i dit Microsoft 365 miljø.

Det kan være en stor opgave at finde indhold i dit miljø, der indeholder personlige oplysninger, og det kan tidligere omfatte en kombination af at bruge Søgning efter overholdelse, eDiscovery, eDiscovery (Premium), DLP og overvågning.

Med den nye **dataklassificeringsløsning** på Microsoft Purview-overholdelsesportalen er dette blevet meget nemmere med funktionen [Indholdsoversigt](../compliance/data-classification-content-explorer.md) , som fungerer sammen med enten indbyggede eller brugerdefinerede typer følsomme oplysninger, herunder dem, der er relateret til personlige data.

### <a name="sensitive-information-types"></a>Typer af følsomme oplysninger

Microsoft Purview-overholdelsesportalen er forudinstalleret med mere end 100 følsomme oplysningstyper, hvoraf de fleste er relateret til at identificere og finde personlige data. Disse indbyggede typer følsomme oplysninger kan hjælpe med at identificere og beskytte kreditkortnumre, bankkontonumre, pasnumre m.m., baseret på mønstre, der er defineret af et regulært udtryk (regex) eller en funktion. Du kan få mere at vide under [Hvad de følsomme oplysningstyper søger efter](../compliance/sensitive-information-type-entity-definitions.md).

Hvis du har brug for at identificere og beskytte en organisationsspecifik eller regional type følsomme elementer, f.eks. et brugerdefineret format for medarbejder-id'er eller andre personlige oplysninger, der ikke allerede er omfattet af en indbygget type følsomme oplysninger, kan du oprette en brugerdefineret type følsomme oplysninger ved hjælp af disse metoder:

- PowerShell
- Brugerdefinerede regler med nøjagtigt datamatch (EDM)
- Via brugergrænsefladen i Overholdelsescenter som fremhævet i [artiklen Brug overholdelsesscore og Overholdelsesstyring](information-protection-deploy-compliance.md)

Du kan også tilpasse en eksisterende indbygget type følsomme oplysninger.

Se disse artikler for at få flere oplysninger:

- [Tilpas en indbygget type af følsomme oplysninger](../compliance/customize-a-built-in-sensitive-information-type.md)
- [Få mere at vide om typer af følsomme oplysninger.](../compliance/sensitive-information-type-learn-about.md)
- [Opret en brugerdefineret type følsomme oplysninger i Security & Compliance Center](../compliance/create-a-custom-sensitive-information-type.md)
- [Opret en brugerdefineret type følsomme oplysninger i Security & Compliance Center PowerShell](../compliance/create-a-custom-sensitive-information-type-in-scc-powershell.md)
- [Opret brugerdefinerede typer følsomme oplysninger med nøjagtig datamatchbaseret klassificering](../compliance/create-custom-sensitive-information-types-with-exact-data-match-based-classification.md)

### <a name="content-explorer"></a>Indholdsoversigt

Et vigtigt værktøj, der til bestemmelse af forekomsten af følsomme elementer i dit miljø er den nye [Indholdsoversigt](../compliance/data-classification-content-explorer.md) i Microsoft Purview Administration. Det er et automatiseret værktøj til indledende og løbende scanning af hele dit Microsoft 365 abonnement for forekomsten af følsomme informationstyper og visning af resultaterne.

Med det nye værktøj i Indholdsoversigt kan du hurtigt identificere placeringen af følsomme elementer i dit miljø ved hjælp af enten indbyggede typer følsomme oplysninger eller brugerdefinerede. Dette kan omfatte oprettelse af en proces og ansvar for regelmæssigt at undersøge tilstedeværelsen og placeringen af følsomme elementer.

Sammen med de andre trin, der er fremhævet i denne artikel, giver dette et udgangspunkt for at identificere din samlede risikoeksponering, parathed og placering af følsomme elementer, der skal beskyttes gennem planlagt Microsoft 365 konfiguration og overvågning.

### <a name="other-methods-to-identify-personal-data-in-your-environment"></a>Andre metoder til at identificere personlige data i dit miljø

Ud over Indholdsoversigt har organisationer adgang til funktionen Indholdssøgning til at oprette brugerdefinerede søgninger for at finde personlige data i deres miljø ved hjælp af avancerede søgekriterier og brugerdefinerede filtre.

Denne [artikel](/compliance/regulatory/gdpr) indeholder en detaljeret vejledning i brugen af indholdssøgning til registrering af personlige data. Indholdssøgning og andre opdagelsesteknikker udforskes også i [DSR-anmodninger om GDPR og CCPA](/compliance/regulatory/gdpr-dsr-Office365#introduction-to-dsrs).

Yderligere indsigt i undersøgelses- og afhjælpningsteknikker for personlige data i Microsoft 365 er angivet i [artiklen Overvåg og reager](information-protection-deploy-monitor-respond.md).

> [!NOTE]
> Hvis du vil finde ud af, hvilke følsomme oplysninger du har i filer, der er gemt i det lokale miljø, skal du se [Azure Information Protection](/azure/information-protection/quickstart-findsensitiveinfo).
