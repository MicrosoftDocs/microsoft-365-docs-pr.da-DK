---
title: Vurder risici i forbindelse med beskyttelse af data og identificer følsomme elementer Microsoft 365
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
description: Fastsæt regler for beskyttelse af data, de relevante scenarier, dit parathed og de typer af følsomme oplysninger, der findes i dit Microsoft 365 miljø.
ms.openlocfilehash: 5f8b5844ad3db4152a6144f9506a0267fa3af8f2
ms.sourcegitcommit: bae72428d229827cba4c807d9cd362417afbcccb
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/02/2022
ms.locfileid: "63590899"
---
# <a name="assess-data-privacy-risks-and-identify-sensitive-items-with-microsoft-365"></a>Vurder risici i forbindelse med beskyttelse af data og identificer følsomme elementer Microsoft 365

Vurdering af bestemmelser om beskyttelse af data og risici, som din organisation er underlagt, er det første trin, før du implementerer relaterede forbedringshandlinger, herunder handlinger, der kan gennemføres med Microsoft 365 funktioner og tjenester.

## <a name="potentially-applicable-data-privacy-regulations"></a>Potentielt gældende regler for beskyttelse af personlige oplysninger

Du kan finde et godt referencenummer til de bredere lovgivningsmæssige rammer for bestemmelser om beskyttelse af data i [Microsoft Services Trust Portal](https://servicetrust.microsoft.com/) og den række artikler om Persondataforordningen [(GDPR](/compliance/regulatory/gdpr)). Gennemgå også materialer for de bestemmelser, du kan være underlagt i din branche eller dit område.

### <a name="gdpr"></a>GDPR

GDPR er den mest velkendte og citerede af bestemmelserne om beskyttelse af personlige oplysninger. Det regulerer indsamling, lagring, behandling og deling af personlige data med en identificeret eller identificerbar naturlig person, der er bosiddende i EU.

I henhold til GDPR-artikel 4:

- "personlige data" betyder alle oplysninger om en identificeret eller identificerbar naturlig person ("den registrerede"). en identificerbar naturlig person er en person, der kan identificeres, direkte eller indirekte, især ved henvisning til et id, som f.eks. et navn, et identifikationsnummer, placeringsdata, et online-id eller en eller flere faktorer, der er specifikke for den fysiske, social, genetiske, mentale, økonomiske, kulturelle eller sociale identitet for den pågældende fysiske person.

### <a name="iso-27001"></a>ISO 27001

Overholdelse af andre standarder som ISO 27001 er også blevet genkendt af flere europæiske kontrolmyndighed som en gyldig proxy for hensigter på tværs af personer, proces- og teknologispektrum. De standarder, der angives, overlapper og overholder ISO-27001-drevne beskyttelsesmekanismer, kan betragtes som en proxy, der opfylder visse forpligtelser i forbindelse med beskyttelse af personlige oplysninger under visse omstændigheder.

### <a name="other-data-privacy-regulations"></a>Andre bestemmelser om beskyttelse af personlige oplysninger

Andre fremtrædende bestemmelser om beskyttelse af personlige oplysninger angiver også krav til håndtering af personlige data.

I USA omfatter disse California Consumer Protection Act ([CCPA](/compliance/regulatory/ccpa-faq)), HIPAA-HITECH (United States Health Care Privacy Act) og Graham Leach Bliley Act (GLBA). Yderligere state-specific regulations are also in-place or in development.

I hele verden kan du finde flere eksempler på Tysklands nationale GDPR Implementation Act (BDSG), LGPD (Brazil Data Protection Act) og mange andre.

## <a name="regulation-mapping-to-microsoft-365-technical-control-categories"></a>Bestemmelser, der tilknyttes Microsoft 365 kategorier for teknisk kontrol

Mange af de regler, der vedrører beskyttelse af personlige oplysninger, overlapper hinanden, så du skal forstå, hvilke bestemmelser de er underlagt, før du udvikler et teknisk kontrolskema.

Til senere brug i artiklerne for denne overordnede løsning giver denne tabel uddrag fra en stikprøve af bestemmelser om beskyttelse af personlige oplysninger.

|Forordning|Artikel/afsnit|Uddrag|Gældende kategorier for teknisk kontrol|
|---|---|---|---|
|GDPR|Artikel 5(1)(f)|Personlige data skal behandles på en måde, der sikrer passende sikkerhed for personlige data, herunder beskyttelse mod uautoriseret eller ulovlig behandling og mod utilsigtet tab, tilsigtet eller skade, ved hjælp af relevante tekniske eller organisatoriske foranstaltninger ('integritet og fortrolighed').|(Alle) <br> Identitet <br> Enhed <br> Trusselsbeskyttelse <br> Beskyt oplysninger <br> Styre oplysninger <br> Find og svar|
||Artikel (32)(1)(a)|Under hensyntagen til den avancerede tilstand, omkostningerne ved implementering og karakteren, omfanget, konteksten og formålet med behandlingen samt risikoen for varierende sandsynlighed og alvor i fysiske personers rettigheder og friheder skal controlleren og processoren implementere relevante tekniske og organisatoriske foranstaltninger for at sikre et sikkerhedsniveau, der er egnet til risikoen.  herunder bl.a. forskellige typer efter behov: (a) pseudonymisering og kryptering af personlige data.|Beskyt oplysninger|
||Artikel (13)(2)(a)|"... den dataansvarlige skal på det tidspunkt, hvor der indhentes personlige data, give den registrerede følgende yderligere oplysninger, som er nødvendige for at sikre fair og gennemsigtig behandling: (a) den periode, hvor personoplysningerne bliver gemt, eller, hvis det ikke er muligt, de kriterier, der bruges til at bestemme den pågældende periode.|Styre oplysninger|
||Artikel (15)(1)(e)|Den registrerede har ret til fra den dataansvarlige at få bekræftet, hvorvidt personlige data vedrørende ham eller hende behandles, og i så fald adgang til personoplysningerne og følgende oplysninger: (e) eksistensen af ret til at anmode den dataansvarlige om at indhente eller slette personlige data eller begrænsning af behandlingen af personlige data vedrørende den registrerede eller gøre objekt med en sådan. behandler|Find og svar|
|LGPD|Artikel 46|Behandlingsagenter skal indføre sikkerhedsforanstaltninger, tekniske og administrative foranstaltninger, der kan beskytte personlige data mod uautoriseret adgang og utilsigtede eller ulovlige situationer, hvor der er behov for handling, tab, ændring, kommunikation eller nogen form for forkert eller ulovlig behandling.|Beskyt oplysninger <br> Styre oplysninger <br> Find og svar|
||Artikel 48|Den dataansvarlige skal kommunikere til den nationale myndighed og den registrerede, om der er forekomst af en sikkerhedshændelse, der kan medføre risiko eller relevant skade for de registrerede.|Find og svar|
|HIPPA-HITECH|45 CFR 164.312(e)(1)|Implementer tekniske sikkerhedsforanstaltninger for at beskytte mod uautoriseret adgang til elektroniske beskyttede sundhedsoplysninger, der overføres via et elektronisk kommunikationsnetværk.|Beskyt oplysninger|
||45 C.F.R. 164.312(e)(2)(ii)|Implementer en mekanisme til at kryptere elektroniske beskyttede sundhedsoplysninger, når det anses for relevant.|Beskyt oplysninger|
||45 CFR 164.312(c)(2)|Implementere elektroniske mekanismer for at bekræfte, at elektroniske beskyttede sundhedsoplysninger ikke er blevet ændret eller ødelagt på uautoriseret vis.|Styre oplysninger|
||45 CFR 164.316(b)(1)(i)|Hvis en handling, aktivitet eller vurdering kræves af denne underdel for at kunne dokumenteres, skal du vedligeholde en skriftlig (som kan være elektronisk) registrering af handlingen, aktiviteten eller vurderingen|Styre oplysninger|
||45 CFR 164.316(b)(1)(ii)|Behold den dokumentation, der kræves i afsnit (b)(1) i denne sektion i 6 år fra oprettelsesdatoen eller den dato, hvor den sidst var gældende, alt efter hvad der er senere.|Styre oplysninger|
||45 C.F.R. 164.308(a)(1)(ii)(D)|Implementere procedurer for regelmæssigt at gennemgå datasystemaktivitet, f.eks. overvågningslogfiler, adgangsrapporter og rapporter til sporing af sikkerhedshændelser|Find og svar|
||45 C.F.R. 164.308(a)(6)(ii)|Identificer og svar på mistænkelige eller kendte sikkerhedshændelser; at reducere, i det omfang det er muligt, skadelige effekter af sikkerhedshændelser, som den omfattede enhed eller forretningspartner kender; og dokumentere sikkerhedshændelser og deres resultater.|Find og svar|
||45 C.F.R. 164.312(b)|Implementer hardware, software og proceduremæssige mekanismer, der registrerer og undersøger aktiviteter i informationssystemer, som indeholder eller bruger elektroniske oplysninger om beskyttet tilstand.|Find og svar|
|CCPA|1798.105(c)|En virksomhed, der modtager en bekræftelig anmodning fra en forbruger om at slette forbrugeres personlige oplysninger i henhold til underopdelingen (a) i dette afsnit, sletter forbrugeres personlige oplysninger fra dets registreringer og dirigerer alle tjenesteudbydere til at slette forbrugeres personlige oplysninger fra deres registreringer.|Find og svar|
||1798.105(d)|(undtagelser til 1798,105(c) <br> En virksomhed eller en serviceudbyder er ikke nødvendig for at overholde en forbrugers anmodning om at slette forbrugerens personlige oplysninger, hvis det er nødvendigt for virksomheden eller serviceudbyder at vedligeholde forbrugeres personlige oplysninger for at: (se den aktuelle lovgivning for yderligere oplysninger).|Find og svar|
|||||

> [!IMPORTANT]
> Dette er ikke ment som en komplet liste. Se [Overholdelsesstyring eller](../compliance/compliance-manager.md) din juridiske eller overholdelsesrådgiver for yderligere oplysninger om anvendelsesmulighederne for de citerede afsnit til de kategorier for teknisk kontrol, der er angivet.

## <a name="knowing-your-data"></a>At kende dine data

Uanset de bestemmelser, du er underlagt, er forskellige brugerdatatyper i og uden for organisationen alle vigtige faktorer, der kan påvirke din overordnede strategi for beskyttelse af personlige data, der er underlagt den branche og de offentlige bestemmelser, der gælder for din organisation. Dette omfatter, hvor personlige data gemmes, hvilken type de er, hvor meget af dem der er, og under hvilke omstændigheder de blev indsamlet.

![At kende dine data: Hvilken type det er, og hvor meget af dem der er, og under hvilke omstændigheder de blev indsamlet.](../media/information-protection-deploy-assess/information-protection-deploy-assess-knowing-data.png)

### <a name="data-portability"></a>Dataportabilitet

Data bevæger sig også rundt over tid, efterhånden som de behandles, finjusteres, og andre versioner er afledt af dem. Et indledende øjebliksbillede er aldrig nok. Der skal være en løbende proces for at kende dine data. Dette er en af de største udfordringer for store organisationer, der håndterer store mængder personlige data. Organisationer, der ikke tager hånd om problemet med "kender dine data", kan potentielt ende med meget høj risiko og mulige fines fra lovgivningsmæssige myndigheder.

![Datalivscyklussen.](../media/information-protection-deploy-assess/information-protection-deploy-assess-data-lifecycle.png)

### <a name="where-the-personal-data-is"></a>Hvor de personlige data er

For at tage hånd om bestemmelser om beskyttelse af personlige oplysninger i forbindelse med data kan du ikke stole på generelle begreber om, hvor du mener, personlige data kan findes, hverken nu eller i fremtiden. Bestemmelser om beskyttelse af personlige oplysninger for data kræver, at organisationer bekræfter, at de ved, hvor personoplysninger findes, løbende. Det gør det vigtigt at tage et indledende øjebliksbillede af alle dine datakilder for mulig lagring af personlige oplysninger, herunder dit Microsoft 365-miljø, og fastlægge mekanismer til vedvarende overvågning og registrering.

Hvis du ikke allerede har evalueret din overordnede parathed og risiko forbundet med regler om beskyttelse af personlige oplysninger, skal du bruge følgende tretrinsstruktur for at komme i gang.

![Trin til at vurdere din overordnede parathed og risiko forbundet med bestemmelser om beskyttelse af data.](../media/information-protection-deploy-assess/information-protection-deploy-assess-grid.png)

> [!NOTE]
> Denne artikel og dens indhold er ikke beregnet til at komme i stedet for juridiske rådgivningstjenester. Det giver blot nogle grundlæggende vejledninger og links til værktøjer, der kan være til hjælp i de tidlige faser af din vurdering.

## <a name="step-1-develop-a-foundational-understanding-of-your-organizations-personal-data-scenarios"></a>Trin 1: Udvikling af en grundlæggende forståelse af organisationens personlige datascenarier

Du skal måle eksponeringen for datas risiko for beskyttelse af personlige oplysninger baseret på den type personlige data, der administreres i øjeblikket, hvor de lagres, hvilke beskyttende kontroller, der anvendes, hvordan livscyklussen administreres, og hvem der har adgang til dem.

Som udgangspunkt er det vigtigt at finde ud af, hvilke typer personlige data der findes i dit Microsoft 365 miljø. Brug disse kategorier:

- Medarbejderdata, der er nødvendige for at udføre daglige virksomhedsfunktioner
- Data, som organisationen har om sine forretningskunder, partnere og andre relationer i B2B-scenariet (business-to-business)
- Data, som organisationen har om forbrugere, der leverer oplysninger til onlinetjenester, som organisationen administrerer i scenariet virksomhed-til-kunde (B2C)

Her er et eksempel på de forskellige typer data til typiske afdelinger i en organisation.

![Typer af personlige data.](../media/information-protection-deploy-assess/information-protection-deploy-assess-data-types.png)

Mange af de personlige data, der er underlagt lovgivningen om beskyttelse af personlige oplysninger, indsamles og gemmes typisk uden for Microsoft 365. Alle personlige data fra forbrugerrettede web- eller mobilprogrammer skal være eksporteret fra sådanne programmer til Microsoft 365 for at kunne granskes i dataene inden for Microsoft 365.

Din eksponering for beskyttelse af personlige oplysninger i Microsoft 365 være mere begrænset i forhold til dine webprogrammer og CRM-systemer, som denne løsning ikke omfatter.

Det er også vigtigt at overveje følgende almindelige udfordringer i forbindelse med overholdelse af regler og standarder for beskyttelse af personlige oplysninger, når du vurderer din risikoprofil:

- **Distribution af personlige data.** Hvor spredt er oplysningerne om et bestemt emne? Er det kendt nok til at overbevise lovgivningsmæssige organisationer om, at de rette kontrolfunktioner er på plads? Kan det undersøges og afhjælpes, hvis det er nødvendigt?
- **Beskyttelse mod udfyldning.** Hvordan beskytter man personlige data af en bestemt type eller kilde mod at blive kompromitteret, og hvordan kan man reagere, hvis den var?
- **Beskyttelse vs. risiko.** Hvilke informationsbeskyttelsesmekanismer er passende i forhold til risikoen, og hvordan man opretholder forretningskontinuitet og produktivitet og minimerer slutbrugerens virkning, hvis der kræves handling fra slutbrugerens side? Skal man f.eks. bruge manuel klassificering eller kryptering?
- **Opbevaring af personlige data.** Hvor længe skal oplysninger, der indeholder personlige data, opbevares af gyldige forretningsgrunde, og hvordan man undgår tidligere praksisser for uendeligt at beholde dem og afbalancere dem med opbevaringsbehov for forretningskontinuitet?
- **Håndtering af anmodninger fra den registrerede.** Hvilke mekanismer er nødvendige for at håndtere anmodninger fra registrerede og eventuelle afhjælpningshandlinger, f.eks. anonymisering, redaction og sletning?
- **Løbende overvågning og rapportering.** Hvilken slags daglig overvågning, overvågning og rapporteringsteknikker er tilgængelige for de forskellige datatyper og kilder?
- **Begrænsninger for behandling af data.** Er der begrænsninger på brugen af data til oplysninger, der indsamles eller gemmes via disse metoder, som organisationen skal afspejle i kontrolelementer til beskyttelse af personlige oplysninger? Forpligtelser om, at personlige data ikke vil blive brugt af salgsmedarbejdere, kan f.eks. kræve, at din organisation har nogle mekanismer, der forhindrer overførsel eller lagring af disse oplysninger i systemer, der er knyttet til salgsorganisationen.

### <a name="employee-data-required-to-carry-out-day-to-day-business-functions"></a>Medarbejderdata, der er nødvendige for at udføre daglige virksomhedsfunktioner

Organisationer har i sig selv brug for at indsamle data om medarbejdere til elektronisk identitet og HR-formål, afhængigt af hvad de accepterer i deres medarbejderaftaler. Så længe en person arbejder for en virksomhed, er dette typisk ikke et problem. Organisationen ønsker måske at få en mekanisme på plads for at forhindre ondsindede aktører i at eksfiltrere eller sive medarbejdernes personlige data ud.

Hvis en person forlader en virksomhed, har organisationer typisk processer, procedurer og opbevarings- og sletningsplaner til fjernelse af brugerkonti, afvikling af postkasser og personlige drev og ændring af medarbejderstatus i ting som HR-systemer. I situationer, hvor procesførelse er involveret, kan en medarbejder eller en anden part i en juridisk undersøgelse have gyldige grunde til at få oplysninger om personlige data, der er gemt i organisationens systemer. Denne part kan ved nogle tilfælde anmode om, at disse data fjernes eller anonymiseres.

For at imødekomme disse behov bør organisationer have indført processer og procedurer, der adresserer undgående, uønskede og afhjælpende behov for at afhjælpe sådanne anmodninger. Det bemærkes, at nogle oplysninger om en medarbejder med rimelighed kan betragtes som afgørende for forretningskontinuitet. Eksempelvis oplysninger om, at en person har skrevet en fil eller udført en funktion.

> [!NOTE]
> Se artiklen overvåge og svar for at finde Microsoft 365 oplysninger om metoder [til afhjælpning og afhjælpning af personlige data i dit arbejde](information-protection-deploy-monitor-respond.md). Du kan også anvende automatiserede klassificerings- og beskyttelsessystemer for at sikre, at personlige data kontrolleres inden for organisationen, og forhindre, at de forlader organisationen i ondsindede agentsituationer. Se artiklen [om beskyttelse af oplysninger for](information-protection-deploy-protect-information.md) at få flere oplysninger.

### <a name="data-the-organization-has-about-its-business-customers-in-the-b2b-scenario"></a>Data, som organisationen har om sine forretningskunder i B2B-scenariet

Indsamling af B2B-oplysninger er også en udfordring, fordi din organisation muligvis skal holde styr på kundenavne og transaktioner i dens forskellige systemer af forretningskontinuitetshensyn, men samtidig beskytte disse oplysninger mod utilsigtet eller skadelig udfyldning. Ligesom medarbejderdata skal organisationer have politikker, procedurer og tekniske kontrolelementer på plads for at beskytte sådanne data samt for at udælde dem i overensstemmelse med definerede tidsplaner for opbevaring og sletning.

Kontrakter med eksterne kunder, partnere og andre enheder, som organisationen gør forretninger med, vil typisk have sprog, der adresserer håndteringen af sådanne data, herunder beskyttelse, opbevaring og sletning både under og efter, at enheden har en relation til organisationen.

### <a name="data-the-organization-has-about-consumers-who-provide-information-to-online-services-that-the-organization-manages-in-the-b2c-scenario"></a>Data, som organisationen har om forbrugere, der leverer oplysninger til onlinetjenester, som organisationen administrerer i B2C-scenariet

Denne kategori er den kategori, som de fleste tænker på i forbindelse med beskyttelse af personlige oplysninger, på grund af mange offentlige forekomster af lækage af kundedata. Dette kan være bevidst, f.eks. en tredjepart i henhold til en kontrakt med udbyderen, eller utilsigtet, f.eks. udfyldning af en ondsindet agent. Beskyttelse af forbrugerdata er en af de primære grunde til, at EU og andre har vedtaget disse bestemmelser. Regler for beskyttelse af data som GDPR og CCPA kræver, at du planlægger:

- [Handlingsplaner og](/compliance/regulatory/gdpr-action-plan) [tjeklister for parathed af kontooplysninger](/compliance/regulatory/gdpr-arc-Office365)
- [Virkningsvurderinger for databeskyttelse](/compliance/regulatory/gdpr-data-protection-impact-assessments)
- [Meddelelser om brud](/compliance/regulatory/gdpr-breach-Office365)
- [Anmodninger fra den registrerede](/compliance/regulatory/gdpr-dsr-Office365)

Hvis din organisation ikke laver en masse direkte fra forbrugeres dataindsamling, kan denne kategori være mindre af et problem. Du kan dog stadig være nødt til at gennemgå de processer, der er beskrevet i disse artikler, for at opnå overholdelse af regler og standarder.

### <a name="step-1-summary"></a>Trin 1 oversigt

At forstå din eksponering for risiko og databeskyttelse er et vigtigt første trin, som er baseret på en grundlæggende forståelse af din organisations scenarier for personlige data.

Hvis du ikke har personlige data fra forbrugere i dit Microsoft 365-miljø, eller det er begrænset til visse dele af miljøet, og behovet for en teknisk kontrol er prædikeret på, at der er eksponering af data af forbrugertypen, skal den tekniske kontrol muligvis kun anvendes i dele af miljøet med høj risiko, ikke overalt.

Selvom en ekstern organisation eller et standardkontrolsæt, f.eks. fra Compliance Manager i Microsoft 365, kan hjælpe med at informere din kontrolstrategi, bør dit valg af implementering være drevet af bevidste datalager for at sætte tal på din eksponering for reelle risici.

De fleste organisationer vil have en vis eksponering for et af ovennævnte scenarier. Det er vigtigt at have en god tilgang til vurdering.

## <a name="step-2-assess-your-readiness-for-complying-with-data-privacy-regulations"></a>Trin 2: Vurder, om du er parat til at overholde bestemmelser om beskyttelse af data

Selvom det er specifikt for GDPR, kan spørgsmålene være med det gratis [værktøj til vurdering af Microsoft GDPR](https://clouddamcdnprodep.azureedge.net/gdc/1863571/original) , men de giver en god start på forståelsen af dit overordnede parathed til beskyttelse af personlige oplysninger.

Organisationer er underlagt andre bestemmelser om beskyttelse af personlige oplysninger, f.eks. CCPA i USA eller Brasiliens LGPD, kan også drage fordel af dette værktøjs lagerbeholdning af parathed overlappende bestemmelser med GDPR.

GDPR-vurdering består af disse afsnit:

|Sektion|Beskrivelse|
|:-------|:-----|
|Styring|<ol><li>Udtrykkeligt angives det i din politik om beskyttelse af personlige oplysninger, hvilke data der behandles? </li><li>Kører du regelmæssigt vurderinger af beskyttelse af personlige oplysninger (PIA'er)? </li><li> Bruger du et værktøj til at administrere personlige oplysninger (PI)? </li><li> Har du juridisk myndighed til at drive forretning ved hjælp af PI-data for en bestemt person? Sporer du samtykke til data? </li><li> Sporer, implementerer og administrerer du revisionskontrolelementer? Overvåger du for datalækager? </li></ol>|
|Sletning og meddelelse|<ol><li>Giver du eksplicitte instruktioner om, hvordan brugeres data kan tilgås? </li><li> Har du dokumenterede processer på plads til håndtering af fravalg af samtykke? </li><li> Har du en automatisk sletningsproces for data? </li><li> Har du en proces til validering af identitet, når du interagerer med en kunde? </li></ol>|
|Afhjælpning af risici og informationssikkerhed|<ol><li>Bruger du værktøjer til at scanne ustrukturerede data? </li><li>Er alle servere opdateret, og udnytter du firewalls til at beskytte dem? </li><li>Kører du regelmæssige sikkerhedskopier af dine servere? </li><li>Overvåger du aktivt for datalækager? </li><li>Krypterer du dine in rest- og overførselsdata? </li></ol>|
|Politikstyring|<ol><li>Hvordan administrerer du dine bindende virksomhedsregler (BCR'er)? </li><li>Sporer du samtykke til data? </li><li> Når en skala fra 1 til 5 er helt dækket, dækker dine kontrakter så dataklassificeringer og håndteringskrav? </li><li>Har du og tester regelmæssigt en plan for svar på hændelser? </li><li>Hvilken politik bruger du til at administrere adgang? </li></ol>|
|||

## <a name="step-3-identify-sensitive-information-types-that-occur-in-your-microsoft-365-environment"></a>Trin 3: Identificer typer af følsomme oplysninger, der forekommer i dit Microsoft 365 miljø

Dette trin indebærer identifikation af bestemte typer af følsomme oplysninger, der er underlagt bestemte lovgivningsmæssige kontrolelementer, samt forekomsten af dem i dit Microsoft 365 miljø.

At finde indhold i dit miljø, der indeholder personligt, kan være en formidabel opgave, tidligere med en kombination af Overholdelsessøgning, eDiscovery, Advanced eDiscovery, DLP og overvågning.

Med den nye løsning **Dataklassificering** i Microsoft Compliance Administration er dette blevet meget nemmere med [](../compliance/data-classification-content-explorer.md) funktionen Indholdsstifinder, som fungerer med enten indbyggede eller brugerdefinerede typer af følsomme oplysninger, herunder dem, der er relateret til personlige data.

### <a name="sensitive-information-types"></a>Typer af følsomme oplysninger

Microsoft Compliance Admin center er forudinstalleret med mere end 100 typer af følsomme oplysninger, som de fleste har at gøre med at identificere og finde personlige data. Disse indbyggede følsomme oplysningstyper kan hjælpe med at identificere og beskytte kreditkortnumre, bankkontonumre, pasnumre og meget mere, baseret på mønstre, der er defineret af et regulært udtryk (regex) eller en funktion. Du kan få mere at vide [under Hvad typerne af følsomme oplysninger søger efter](../compliance/sensitive-information-type-entity-definitions.md).

Hvis du har brug for at identificere og beskytte en organisationsspecifik eller regional type af følsomme elementer, f.eks. et brugerdefineret format for medarbejder-id'er eller andre personlige oplysninger, der ikke allerede er dækket af en indbygget type af følsomme oplysninger, kan du oprette en brugerdefineret type af følsomme oplysninger med disse metoder:

- PowerShell
- Brugerdefinerede regler med nøjagtigt dataoverensstemmelse (EDM)
- Via Brugergrænsefladen for Overholdelsescenter som fremhævet i artiklen [Brug overholdelsesscore og overholdelsesstyring](information-protection-deploy-compliance.md)

Du kan også tilpasse en eksisterende, indbygget følsom oplysningstype.

Se disse artikler for at få flere oplysninger:

- [Tilpasse en indbygget følsom oplysningstype](../compliance/customize-a-built-in-sensitive-information-type.md)
- [Få mere at vide om typer af følsomme oplysninger](../compliance/sensitive-information-type-learn-about.md)
- [Oprette en brugerdefineret type af følsomme oplysninger i & Security & Compliance Center](../compliance/create-a-custom-sensitive-information-type.md)
- [Opret en brugerdefineret type af følsomme oplysninger i Security & Compliance Center PowerShell](../compliance/create-a-custom-sensitive-information-type-in-scc-powershell.md)
- [Opret brugerdefinerede typer af følsomme oplysninger med nøjagtig dataoverensstemmelsesbaseret klassificering](../compliance/create-custom-sensitive-information-types-with-exact-data-match-based-classification.md)

### <a name="content-explorer"></a>Indholdsstifinder

Et vigtigt værktøj, der bruges til at fastslå forekomsten af følsomme elementer i dit miljø, er [](../compliance/data-classification-content-explorer.md) det nye indholdsstifinder i Microsoft 365 Compliance Administration. Det er et automatiseret værktøj til indledende og løbende scanning af hele dit Microsoft 365-abonnement for forekomsten af typer af følsomme oplysninger og visning af resultaterne.

Det nye værktøj Indholdsstifinder giver dig mulighed for hurtigt at identificere placeringen af følsomme elementer i dit miljø ved enten at bruge indbyggede typer af følsomme oplysninger eller brugerdefinerede. Dette kan omfatte at etablere en proces og have ansvaret for regelmæssigt at undersøge tilstedeværelse og placering af følsomme elementer.

Sammen med de andre trin, der er fremhævet i denne artikel, er dette et udgangspunkt for at identificere din overordnede eksponering for risici, parathed og placering af følsomme elementer, der skal beskyttes gennem planlagt Microsoft 365 konfiguration og overvågning.

### <a name="other-methods-to-identify-personal-data-in-your-environment"></a>Andre metoder til at identificere personlige data i dit miljø

Ud over Indholdsstifinder har organisationer adgang til funktionen Indholdssøgning til at oprette brugerdefinerede søgninger til at finde personlige data i deres miljø ved hjælp af avancerede søgekriterier og brugerdefinerede filtre.

I denne artikel finder du detaljerede anvisninger om brug af indholdssøgning til registrering af [personlige data](/compliance/regulatory/gdpr). Indholdssøgning og andre discovery-teknikker udforskes [også i DSR til GDPR og CCPA](/compliance/regulatory/gdpr-dsr-Office365#introduction-to-dsrs).

Du kan få yderligere viden om undersøgelser og afhjælpningsteknikker vedrørende personlige data Microsoft 365 du kan få i [artiklen overvåg og svar](information-protection-deploy-monitor-respond.md).

> [!NOTE]
> Hvis du vil finde ud af, hvilke følsomme oplysninger du har i filer, der er gemt lokalt, skal du [se Azure Information Protection](/azure/information-protection/quickstart-findsensitiveinfo).
