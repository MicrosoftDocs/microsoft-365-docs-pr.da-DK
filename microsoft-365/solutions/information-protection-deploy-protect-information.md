---
title: Beskyt oplysninger, der er underlagt lovgivningen om beskyttelse af personlige oplysninger
ms.author: bcarter
author: brendacarter
f1.keywords:
- NOCSH
manager: laurawi
ms.date: 06/09/2020
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
description: Udrul Microsoft 365 sikkerheds- og overholdelsesfunktioner, og beskyt dine personlige oplysninger.
ms.openlocfilehash: 0876cc1ff51b133e22d13b4c7fbc9a575db32d26
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64943277"
---
# <a name="protect-information-subject-to-data-privacy-regulation"></a>Beskyt oplysninger, der er underlagt lovgivningen om beskyttelse af personlige oplysninger

Der kan anvendes en række kontrolelementer til beskyttelse af oplysninger i dit abonnement for at hjælpe med at håndtere behov og bestemmelser for overholdelse af angivne standarder for beskyttelse af personlige oplysninger. Disse omfatter persondataforordningen (GDPR), HIPAA-HITECH (den USA lov om beskyttelse af personlige oplysninger for sundhedspleje), California Consumer Protection Act (CCPA) og LGPD (Brasilien Data Protection Act).

Disse kontrolelementer er inden for følgende løsningsområder:

- Følsomhedsmærkater
- Microsoft Purview Forebyggelse af datatab (DLP)
- Microsoft Purview-meddelelsekryptering
- Teams- og webstedsadgangskontrolelementer

![Vigtige tjenester til beskyttelse af personlige oplysninger, der er underlagt lovgivningen om beskyttelse af personlige oplysninger.](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-grid.png)

> [!NOTE]
> Denne løsning beskriver sikkerheds- og overholdelsesfunktioner for at beskytte oplysninger, der er underlagt regler om beskyttelse af personlige oplysninger. Du kan se en komplet liste over sikkerhedsfunktioner i Microsoft 365 i [Microsoft 365 sikkerhedsdokumentation](../security/index.yml). Du kan se en komplet liste over funktioner til overholdelse af angivne standarder i Microsoft 365 i [dokumentationen til Microsoft Purview](../compliance/index.yml).

## <a name="data-privacy-regulations-that-impact-information-protection-controls"></a>Bestemmelser om beskyttelse af personlige oplysninger, der påvirker kontrolelementer til beskyttelse af oplysninger

Her er et eksempel på en liste over bestemmelser om beskyttelse af personlige oplysninger, der kan relatere til kontrolelementer til beskyttelse af oplysninger:

- GDPR-artikel 5, stk. 1, litra f))
- GDPR-artikel (32)(1)(a)
- LGPD-artikel 46
- HIPAA-HITECH (45 CFR 164.312(e)(1))
- HIPAA-HITECH (45 C.F.R. 164.312(e)(2)(ii))

Se [artiklen vurder risici for beskyttelse af personlige oplysninger og identificer følsomme elementer](information-protection-deploy-assess.md) for at få flere oplysninger om hver af ovenstående.

Anbefalinger til beskyttelse af personlige oplysninger i forbindelse med beskyttelse af personlige oplysninger:

- Beskyttelse mod tab eller uautoriseret adgang, brug og/eller transmission.
- Risikobaseret anvendelse af beskyttelsesmekanismer.
- Brug af kryptering, hvor det er relevant.

Din organisation vil måske også gerne beskytte Microsoft 365 indhold til andre formål, f.eks. andre behov for overholdelse af angivne standarder eller af forretningsmæssige årsager. Oprettelse af din databeskyttelsesordning for beskyttelse af personlige oplysninger skal udføres som en del af den overordnede planlægning, implementering og administration af information beskyttelse.

For at hjælpe dig med at komme i gang med et system til beskyttelse af oplysninger i Microsoft 365 indeholder følgende afsnit en kort liste over relaterede funktioner og forbedringshandlinger for Microsoft 365. Listen indeholder funktioner og forbedringshandlinger, der gælder for regler om beskyttelse af personlige oplysninger. Listen indeholder dog ikke ældre teknologier, hvis der er en nyere egenskab, der stort set tilsidesætter den ældre. IRM (Information Rights Management) til SharePoint og OneDrive er f.eks. ikke inkluderet på listen, men følsomhedsmærkater er inkluderet.

## <a name="managing-information-protection-in-microsoft-365"></a>Administration af beskyttelse af oplysninger i Microsoft 365

[Microsofts løsninger til beskyttelse af oplysninger](../compliance/information-protection.md) omfatter en række integrerede funktioner på tværs af Microsoft 365, Microsoft Azure og Microsoft Windows. I Microsoft 365 omfatter løsninger til beskyttelse af oplysninger:

- [Følsomme oplysningstyper](../compliance/sensitive-information-type-entity-definitions.md) (beskrevet i [artiklen vurder risici for beskyttelse af personlige oplysninger og identificer følsomme elementer](information-protection-deploy-assess.md)
- [Følsomhedsmærkater](../compliance/sensitivity-labels.md)
  - Tjeneste-/objektbeholderniveau
  - Klientside/indholdsniveau
  - Automatiseret til inaktive data i SharePoint og OneDrive
- Forebyggelse af datatab (DLP)
- [Forebyggelse af datatab for slutpunkt](../compliance/endpoint-dlp-learn-about.md)
- [Office 365 meddelelseskryptering nye funktioner (OME)](../compliance/ome.md) og OME [Advanced Message Encryption](../compliance/ome-advanced-message-encryption.md)

Desuden er websteds- og biblioteksbeskyttelse vigtige mekanismer, der skal medtages i alle beskyttelsesordninger.

Du kan få oplysninger om andre funktioner til beskyttelse af oplysninger uden for Microsoft 365 i:

- [Microsoft Defender for Cloud Apps](/cloud-app-security/)
- [Azure Information Protection](/azure/information-protection/what-is-information-protection)
- [Microsoft Endpoint Manager](https://www.microsoft.com/microsoft-365/microsoft-endpoint-manager)
- [Windows Information Protection](/windows/security/information-protection/windows-information-protection/protect-enterprise-data-using-wip)

## <a name="sensitivity-labels"></a>Følsomhedsmærkater

Følsomhedsmærkater fra Microsoft Purview Information Protection giver dig mulighed for at klassificere og beskytte din organisations data uden at hindre brugernes produktivitet og deres mulighed for at samarbejde.

> [!div class="mx-imgBorder"]
> ![Følsomhedsmærkater i Microsoft 365.](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-labels.png)

### <a name="prerequisites-for-sensitivity-labels"></a>Forudsætninger for følsomhedsmærkater

Fuldfør disse aktiviteter, før du implementerer en af de funktioner, der er baseret på følsomhedsmærkater, som er fremhævet nedenfor:

1. Forstå følgende:
   - **Forretningskrav.** Fastlæg de forretningsmæssige årsager til anvendelse af følsomhedsmærkater i din virksomhed. Det kan f.eks. være krav til beskyttelse af personlige oplysninger.
   - **Egenskaber for følsomhedsmærkat.** Følsomhedsmærkater kan blive komplekse, så sørg for at læse [dokumentationen til følsomhedsmærkater](../compliance/sensitivity-labels.md) , før du går i gang.
   - **Vigtige ting at huske** Følsomhedsmærkater administreres på Microsoft Purview-overholdelsesportalen, men målretnings- og programindstillingerne varierer betydeligt.
      - Der er følsomhedsmærkater for websteder, grupper og Teams på objektbeholderniveau (indstillingerne gælder ikke for indhold i objektbeholderen). Disse publiceres til brugere og grupper, der anvender dem, når et websted, en gruppe eller et team klargøres.
      - Der er følsomhedsmærkater for aktivt indhold. Disse publiceres også til brugere eller grupper, som enten anvender dem manuelt, eller som anvendes automatisk, når:
        - Filen åbnes/redigeres/gemmes enten på brugerens skrivebord eller på et SharePoint websted.
        - Der sendes en mail.
      - Der er følsomhedsmærkater for automatisk anvendelse på inaktive filer i SharePoint og OneDrive ud over mails under overførsel gennem Exchange. Disse er målrettet til enten alle websteder eller specifikke websteder og gælder automatisk for inaktive filer i disse miljøer.

2. Rationaliser aktuel følsomhedsmærkatering med tidligere eller alternative metoder

   - Azure Information Protection

      Det aktuelle skema for følsomhedsmærkater skal muligvis afstemmes med alle eksisterende [implementeringer af Azure Information Protection-mærkat](../compliance/sensitivity-labels.md#sensitivity-labels-and-azure-information-protection).
   - OME

      Hvis du planlægger at bruge moderne følsomhedsmærkatering til mailbeskyttelse, og eksisterende metoder til kryptering af mail, f.eks. OME, er på plads, kan de eksistere side om side, men du bør forstå de scenarier, hvor begge skal anvendes. Se [Office 365 Meddelelseskryptering nye funktioner (OME),](#office-365-message-encryption-ome-new-capabilities) som omfatter en tabel, der sammenligner moderne beskyttelse af følsomhedsmærkattyper med OME-baseret beskyttelse.

3. Plan for integration i en bredere ordning for beskyttelse af oplysninger. Ud over at fungere sammen med OME kan følsomhedsmærkater bruges side om side, f.eks. Microsoft Purview DLP (Forebyggelse af datatab) og Microsoft Defender for Cloud Apps. Se [Beskyt dine data med Microsoft Purview](../compliance/information-protection.md) for at opnå dine mål for beskyttelse af personlige oplysninger relateret til beskyttelse af personlige oplysninger.

4. Udvikl et klassificerings- og kontrolskema for følsomhedsmærkater. Se [Taksonomi for dataklassificering og følsomhedsmærkat](https://aka.ms/dataclassificationwhitepaper).

### <a name="general-guidance"></a>Generel vejledning

1. **Skemadefinition.** Før du bruger tekniske funktioner til at anvende mærkater og beskyttelse, skal du arbejde på tværs af organisationen for at definere et klassificeringsskema. Du har muligvis allerede et klassificeringsskema, hvilket gør det nemmere at tilføje personlige data.
2. **Introduktion.** Start med at beslutte, hvor mange og navne på mærkater der skal implementeres. Gør denne aktivitet uden at bekymre dig om, hvilken teknologi der skal bruges, og hvordan mærkaterne skal anvendes. Anvend dette skema universelt i hele organisationen, herunder data, der er placeret i det lokale miljø og i andre cloudtjenester.
3. **Yderligere anbefalinger** Når du designer og implementerer politikker, mærkater og betingelser, bør du overveje at følge disse anbefalinger:

   - **Brug eksisterende klassificeringsskema (hvis der er nogen).** Mange organisationer bruger allerede dataklassificering i en eller anden form. Evaluer nøje det eksisterende mærkatskema, og brug det, som det er, hvis det er muligt. Brug af velkendte mærkater, der kan genkendes af dine slutbrugere, vil føre til indførelse.
   - **Start i det små.** Der er stort set ingen grænse for, hvor mange mærkater du kan oprette. Et stort antal mærkater og undermærkater kan dog gøre det langsomt at indføre dem.
   - **Brug scenarier og use cases.** Identificer almindelige use cases i din organisation, og brug scenarier, der er afledt af de bestemmelser om beskyttelse af personlige oplysninger, som du er underlagt. Kontrollér, om konfigurationen af den klargjorte mærkat og klassificering fungerer i praksis.
   - **Udspørg alle anmodninger om en ny etiket.** Har alle scenarier eller use case virkelig brug for en ny mærkat, eller kan du bruge det, du allerede har? Det forbedrer vedtagelsen at holde antallet af mærkater på et minimum.
   - **Brug undernavne til vigtige afdelinger.** Nogle afdelinger har specifikke behov, der kræver specifikke mærkater. Definer disse mærkater som undernavne til en eksisterende etiket, og overvej at bruge områdebaserede politikker, der er tildelt brugergrupper i stedet for globalt.
   - **Overvej omfangsdelagte politikker.** Politikker, der er målrettet til undersæt af brugere, forhindrer overbelastning af mærkater. En områdebaseret politik gør det muligt kun at tildele rolle- eller afdelingsspecifikke mærkater eller undernavne til medarbejdere, der arbejder for den pågældende afdeling.
   - **Brug meningsfulde navne.** Prøv ikke at bruge jargon, standarder eller akronymer som navne. Prøv at bruge navne, der giver genlyd hos slutbrugeren, for at forbedre indføringen. I stedet for at bruge mærkater som PII, PCI, HIPAA, LBI, MBI og HBI kan du overveje navne som Non-Business, Public, General, Confidential og Highly Confidential.

### <a name="create-and-deploy-sensitivity-labels-for-sites-groups-and-teams"></a>Opret og udrul følsomhedsmærkater for websteder, grupper og teams

Når du opretter [følsomhedsmærkater](../compliance/sensitivity-labels-teams-groups-sites.md) på <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview-overholdelsesportalen</a>, kan du nu anvende dem på disse objektbeholdere:

- Microsoft Teams websteder
- Microsoft 365 grupper (tidligere Office 365 grupper)
- SharePoint websteder

Brug følgende navneindstillinger til at beskytte indholdet i disse objektbeholdere:

- Beskyttelse af personlige oplysninger (offentlig eller privat) for Microsoft 365 gruppeforbundne Teams websteder
- Ekstern brugeradgang
- Adgang fra ikke-administrerede enheder

Hvis du vil forhindre ekstern deling af objektbeholdere, der skal bruges til at gemme indhold med følsomme personlige data, skal du markere de filer, der indeholder dataene, som private, og kræve administrerede enheder.

### <a name="create-and-deploy-sensitivity-labels-for-content"></a>Opret og udrul følsomhedsmærkater for indhold

Følsomhedsmærkater, der anvendes på filer, giver dig mulighed for at kryptere deres indhold, vandmærke indholdet og definere andre kontrolelementer for Office programindhold, herunder Outlook og Office på internettet.

Når du er klar til at begynde at beskytte din organisations data med følsomhedsmærkater:

1. **Opret etiketterne.** Opret og navngiv dine følsomhedsmærkater i henhold til din organisations klassificeringstosonomi for forskellige følsomhedsniveauer for indhold. Du kan få flere oplysninger om udvikling af en klassificeringstsonomi i [hvidbogen Dataklassificering og Taksonomi for følsomhedsmærkat](https://aka.ms/dataclassificationwhitepaper).
2. **Definer, hvad hver etiket kan gøre.** Konfigurer de beskyttelsesindstillinger, du vil knytte til hver etiket. Det kan f.eks. være, at du ønsker, at der kun anvendes et sidehoved eller en sidefod med lavere følsomhed (f.eks. mærkaten "Generelt"), mens et vandmærke med højere følsomhed (f.eks. mærkaten "Fortroligt") skal have et vandmærke og kryptering aktiveret.
3. **Publicer etiketterne.** Når dine følsomhedsmærkater er konfigureret, kan du publicere dem ved hjælp af en mærkatpolitik. Beslut, hvilke brugere og grupper der skal have mærkaterne, og hvilke politikindstillinger der skal bruges. En enkelt etiket kan genbruges. Du definerer den én gang, og derefter kan du inkludere den i flere mærkatpolitikker, der er tildelt forskellige brugere.

Når du publicerer følsomhedsmærkater fra <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview-overholdelsesportalen</a>, vises de i [Office apps](../compliance/sensitivity-labels-office-apps.md), hvor brugerne kan klassificere og beskytte indhold, når det oprettes eller redigeres.

![Udrulningsflow for følsomhedsmærkat i Microsoft 365.](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-label-flow.png)

I forbindelse med beskyttelse af personlige oplysninger anvender du manuelt en følsomhedsmærkat med kryptering og andre regler på mail eller indhold, der indeholder følsomme personlige oplysninger.

> [!NOTE]
> Følsomhedsmærkater med kryptering aktiveret for mail har en vis overlappende funktionalitet med OME. Se [Sammenligning af sikre mailscenarier med OME og følsomhedsmærkater](#secure-email-scenarios-comparison-with-ome-and-sensitivity-labels).

### <a name="client-side-auto-labeling-when-users-edit-documents-or-compose-emails"></a>Automatisk mærkning på klientsiden, når brugerne redigerer dokumenter eller opretter mails

Når du opretter en følsomhedsmærkat, kan du [automatisk tildele denne mærkat](../compliance/apply-sensitivity-label-automatically.md) til indhold, herunder mail, når den opfylder de betingelser, du angiver.

Muligheden for automatisk at anvende følsomhedsmærkater på indhold er vigtig, fordi:

- Du behøver ikke at oplære dine brugere, hvornår de skal bruge hver af dine klassificeringer.
- Du behøver ikke at stole på, at brugerne klassificerer alt indhold korrekt.
- Brugerne behøver ikke længere at kende til dine politikker – de kan i stedet fokusere på deres arbejde.

Automatisk mærkning understøtter anbefalelse af en mærkat til brugere samt automatisk anvendelse af en mærkat. Men i begge tilfælde beslutter brugeren, om brugeren vil acceptere eller afvise mærkaten, for at sikre korrekt mærkning af indhold.

Denne navngivning på klientsiden har minimal forsinkelse for dokumenter, fordi mærkaten kan anvendes, selv før dokumentet gemmes. Det er dog ikke alle klientapps, der understøtter automatisk mærkning. Denne funktion understøttes af Azure Information Protection Unified Labeling-klienten og [nogle versioner af Office apps](../compliance/sensitivity-labels-office-apps.md#support-for-sensitivity-label-capabilities-in-apps).

Du kan finde konfigurationsanvisninger under [Sådan konfigurerer du automatisk mærkning for Office apps](../compliance/sensitivity-labels-office-apps.md#support-for-sensitivity-label-capabilities-in-apps).

I forbindelse med beskyttelse af personlige oplysninger anvender du automatisk følsomhedsmærkater for indhold, der indeholder følsomme personlige oplysninger.

### <a name="service-side-auto-labeling-when-content-is-already-saved"></a>Automatisk mærkning på tjenestesiden, når indhold allerede er gemt

Denne metode kaldes automatisk klassificering med følsomhedsmærkater. Du kan også høre den kaldet automatisk mærkning af inaktive data (for dokumenter i SharePoint og OneDrive) og data under overførsel (for mails, der sendes eller modtages af Exchange). For Exchange omfatter den ikke inaktive mails i postkasser.

Da denne mærkning anvendes af selve tjenesten i stedet for af brugerprogrammet, behøver du ikke at bekymre dig om, hvilke apps brugerne har, og hvilken version de har. Denne funktion er derfor tilgængelig i hele organisationen med det samme og egner sig til mærkning i stor skala. Politikker for automatisk mærkning understøtter ikke anbefalet mærkning, fordi brugeren ikke interagerer med mærkatprocessen. Administratoren kører i stedet politikkerne i simuleringstilstand for at sikre korrekt mærkning af indhold, før mærkaten anvendes.

Du kan finde konfigurationsanvisninger under [Sådan konfigurerer du politikker for automatisk mærkning for SharePoint, OneDrive og Exchange](../compliance/apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange).

For beskyttelse af personlige oplysninger på websteder, der giver anledning til bekymring, skal du overføre følsomhedsmærkater til automatisk kryptering af indhold, der indeholder følsomme personlige oplysninger.

## <a name="data-loss-prevention"></a>Forebyggelse af datatab

Du kan bruge [forebyggelse af datatab](../compliance/dlp-learn-about-dlp.md) i Microsoft 365 til at registrere, advare og blokere risikable, utilsigtede eller upassende deling, f.eks. deling af data, der indeholder personlige oplysninger, både internt og eksternt.

DLP giver dig mulighed for at:

- Identificer og overvåg risikable delingsaktiviteter.
- Oplær brugere med vejledning i kontekst, så de kan træffe de rigtige beslutninger.
- Gennemtving politikker for brug af data på indhold uden at hæmme produktiviteten.
- Integrer med klassificering og mærkning for at registrere og beskytte data, når de deles.

### <a name="supported-workloads-for-dlp"></a>Understøttede arbejdsbelastninger til DLP

Med en DLP-politik på <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview-overholdelsesportalen</a> kan du identificere, overvåge og automatisk beskytte følsomme elementer på tværs af mange placeringer i Microsoft 365, f.eks. Exchange Online, SharePoint, OneDrive og Microsoft Teams.

Du kan f.eks. identificere et hvilket som helst dokument, der indeholder et kreditkortnummer, som er gemt på et hvilket som helst OneDrive websted, eller du kan kun overvåge OneDrive websteder for bestemte personer.

Du kan også overvåge og beskytte følsomme elementer i de lokalt installerede versioner af Excel, PowerPoint og Word, som omfatter muligheden for at identificere følsomme elementer og anvende DLP-politikker. DLP giver mulighed for løbende overvågning, når personer deler indhold fra disse Office apps.

> [!div class="mx-imgBorder"]
> ![Understøttede arbejdsbelastninger til DLP.](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-supported-workloads.png)

Dette tal viser et eksempel på DLP til beskyttelse af personlige data.

> [!div class="mx-imgBorder"]
> ![Eksempel på beskyttelse af personlige data ved hjælp af DLP.](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-dlp-example-use.png)

DLP bruges til at identificere et dokument eller en mail, der indeholder en tilstandspost, og blokerer derefter automatisk adgangen til dokumentet eller blokerer mailen fra at blive sendt. DLP giver derefter modtageren et politiktip og sender en besked til slutbrugeren og administratoren.

### <a name="planning-for-dlp"></a>Planlægning af DLP

Planlæg dine DLP-politikker for:

- Dine forretningskrav.

- En risikobaseret vurdering af organisationen som beskrevet i [artiklen vurder risici for beskyttelse af personlige oplysninger og identificer følsomme elementer](information-protection-deploy-assess.md).

- Andre mekanismer til beskyttelse og styring af oplysninger, som er på plads eller i forbindelse med planlægning af beskyttelse af personlige oplysninger.

- De typer følsomme oplysninger, som du har identificeret for personlige data baseret på dit vurderingsarbejde, som beskrevet i [artiklen vurder risici for beskyttelse af personlige oplysninger og identificer følsomme elementer](information-protection-deploy-assess.md). DLP-politikbetingelser kan være baseret på både følsomme informationstyper og opbevaringsmærkater.

- De opbevaringsmærkater, du skal bruge for at angive DLP-betingelser. Du kan få flere oplysninger [i artiklen Om regler for beskyttelse af personlige oplysninger i din organisation](information-protection-deploy-govern.md) .

- Løbende administration af DLP-politik, som kræver, at en person i organisationen kører og justerer politikker for ændringer i følsomme informationstyper, opbevaringsmærkater, regler og politikker for overholdelse af angivne standarder.

Selvom følsomhedsmærkater ikke kan bruges i DLP-politikbetingelser, kan visse beskyttelsesscenarier for at forhindre adgang være opnåelige med kun følsomhedsmærkater, der kan anvendes automatisk baseret på følsomme informationstyper. Hvis der er robust følsomhedsmærkater på plads, skal du overveje, om DLP skal bruges til at forbedre beskyttelsen, fordi:

  - DLP kan forhindre deling af filer. Følsomhedsmærkater kan blot forhindre adgang.

  - DLP har mere detaljerede kontrolniveauer med hensyn til regler, betingelser og handlinger.

  - DLP-politikker kan anvendes på Teams chat- og kanalmeddelelser. Følsomhedsmærkater kan kun anvendes på dokumenter og mail.


### <a name="dlp-policies"></a>DLP-politikker

DLP-politikker konfigureres på Microsoft Purview-overholdelsesportalen og angiver beskyttelsesniveauet, den følsomme informationstype, som politikken leder efter, og målarbejdsbelastningerne. Deres grundlæggende komponenter består i at identificere beskyttelsen og typerne af data.

> [!div class="mx-imgBorder"]
> ![Konfiguration af DLP-politik i Microsoft 365.](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-dlp-config.png)

Her er et eksempel på DLP-politik for bevidsthed om GDPR.

![Eksempel på DLP-politik for bevidsthed om GDPR.](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-dlp-example-policy.png)

Se [denne artikel](../compliance/create-test-tune-dlp-policy.md) for at få flere oplysninger om oprettelse og anvendelse af DLP-politikker.

### <a name="protection-levels-for-data-privacy"></a>Beskyttelsesniveauer for beskyttelse af personlige oplysninger

I følgende tabel vises tre konfigurationer med øget beskyttelse ved hjælp af DLP.

![Beskyttelsesniveauer for beskyttelse af personlige oplysninger med DLP.](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-dlp-protection-levels.png)

Den første konfiguration, Awareness, kan bruges som udgangspunkt og minimumsniveau for beskyttelse til at håndtere overholdelsesbehov for regler om beskyttelse af personlige oplysninger.

> [!NOTE]
> Efterhånden som beskyttelsesniveauet øges, reduceres brugernes mulighed for at dele og få adgang til oplysninger i nogle tilfælde og kan potentielt påvirke deres produktivitet eller evne til at udføre daglige opgaver.

Hvis du vil hjælpe dine medarbejdere med at blive ved med at være produktive i et mere sikkert miljø, når beskyttelsesniveauet øges, skal du bruge tid på at oplære og uddanne dem i nye sikkerhedspolitikker og -procedurer.

### <a name="example-of-using-sensitivity-labels-with-dlp"></a>Eksempel på brug af følsomhedsmærkater med DLP

Følsomhedsmærkater kan arbejde sammen med DLP for at sikre beskyttelse af personlige oplysninger i et stærkt reguleret miljø. Her er de vigtigste trin i den integrerede installation:

1. Lovmæssige og på anden måde forretningsmæssige krav til beskyttelse af personlige oplysninger er dokumenteret.
2. Måldatakilder, -typer og -ejerskab er kendetegnet i forhold til bekymringer om beskyttelse af personlige oplysninger.
3. Der etableres en overordnet strategi for at håndtere krav og beskytte og styre hotspots for beskyttelse af personlige oplysninger.
4. Der oprettes en faseinddelt handlingsplan til at håndtere strategien til kontrol af beskyttelse af personlige oplysninger.

Når disse elementer er fastlagt, kan du bruge følsomme oplysningstyper, taksonomi for følsomhedsmærkater og DLP-politikker sammen. Dette tal viser et eksempel.

> [!div class="mx-imgBorder"]
> ![Eksempel på følsomhedsmærkater, der arbejder med DLP.](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-sensitivity-lables-dlp.png)

[Se en større version af dette billede](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-sensitivity-lables-dlp.png)

Her er nogle databeskyttelsesscenarier, hvor DLP og følsomhedsmærkater bruges sammen som vist i figuren.

| Scenario | Proces |
|:-------|:-----|
| A | <ol><li>Følsomhedsmærkater for indhold publiceres af en administrator til brugere og grupper til manuel eller automatisk anvendelse på indhold og mail. </li><li>Bruger A anvender mærkaterne manuelt eller automatisk, når der interageres med indhold, med kryptering eller andre indstillinger anvendt. </li><li>Bruger A sender en beskyttet mail eller fil til bruger B, en gæstebruger. </li></ol> |
| B | DLP-politik, der er publiceret af en administrator til Bruger A, blokerer bruger A fra at sende mailen og/eller filen til Bruger B. |
| C |  Følsomhedsmærkat med indstillingen "Ejer kan ikke invitere gæster" er publiceret til Bruger A, der klargør et Teams team eller SharePoint websted. En anden bruger af webstedet forsøger selektivt at dele en fil med Bruger B, men DLP blokerer den. |
| D | Følsomhedsmærkat for automatisk anvendelse på webstedsindhold publiceres på et eller flere websteder, hvilket giver et andet beskyttelseslag, hvilket resulterer i et beskyttet websted. |
|||

## <a name="office-365-message-encryption-ome-new-capabilities"></a>nye funktioner Office 365 meddelelseskryptering (OME)

Folk bruger ofte mail til at udveksle følsomme elementer, f.eks. oplysninger om patienttilstand eller kunde- og medarbejderoplysninger. Kryptering af mailmeddelelser hjælper med at sikre, at det kun er modtagere, der er beregnet til at få vist meddelelsesindhold.

Med [OME](../compliance/ome.md) kan du sende og modtage krypterede meddelelser mellem personer i og uden for din organisation. OME fungerer sammen med Outlook.com, Yahoo!, Gmail og andre mailtjenester. OME hjælper med at sikre, at kun de ønskede modtagere kan få vist meddelelsesindhold.

I forbindelse med beskyttelse af personlige oplysninger skal du bruge OME til at beskytte interne meddelelser, der indeholder følsomme elementer. Office 365 Meddelelseskryptering er en onlinetjeneste, der er baseret på Azure RMS (Microsoft Azure Rights Management), som er en del af Azure Information Protection. Dette omfatter politikker for kryptering, identitet og godkendelse for at hjælpe med at beskytte din mail. Du kan kryptere meddelelser ved hjælp af rettighedsadministrationsskabeloner, indstillingen Videresend ikke og indstillingen Kun kryptering.

Du kan også definere regler for mailflow for at anvende denne beskyttelse. Du kan f.eks. oprette en regel, der kræver kryptering af alle meddelelser, der er adresseret til en bestemt modtager, eller som indeholder bestemte nøgleordsord i emnelinjen, og også angive, at modtagerne ikke kan kopiere eller udskrive indholdet af meddelelsen.

Derudover hjælper OME [Advanced Message Encryption](../compliance/ome-advanced-message-encryption.md) dig med at opfylde overholdelsesforpligtelser, der kræver mere fleksible kontroller over eksterne modtagere og deres adgang til krypterede mails. Med OME Advanced Message Encryption i Microsoft 365 kan du styre følsomme mails, der deles uden for organisationen, med automatiske politikker, der registrerer følsomme informationstyper.

I forbindelse med beskyttelse af personlige oplysninger kan du angive en udløbsdato og tilbagekalde meddelelser, hvis du har brug for at dele mail med en ekstern part. Du kan kun tilbagekalde og angive en udløbsdato for meddelelser, der sendes til eksterne modtagere.

### <a name="secure-email-scenarios-comparison-with-ome-and-sensitivity-labels"></a>Sammenligning af sikre mailscenarier med OME og følsomhedsmærkater

OME og følsomhedsmærkater, der anvendes på mail med kryptering, overlapper hinanden, så det er vigtigt at forstå, hvilke scenarier der enten gælder for, som vist i denne tabel.

| Scenario | Følsomhedsmærkater | OME |
|:-------|:-----|:-------|
| Interne + partnere <br> Kommuniker og samarbejd sikkert mellem interne brugere og partnere, der er tillid til | Anbefal – mærkater med fuldt tilpasset klassificering og beskyttelse | Ja – kun kryptering eller videresend ikke beskyttelse uden klassificering |
| Eksterne parter <br> Kommuniker og samarbejd sikkert med eksterne brugere/forbrugerbrugere | Ja – foruddefinerede modtagere i etiket | Anbefal – just-in-time-beskyttelse baseret på modtagere |
| Interne + partnere med udløb/tilbagekaldelse <br> Styr adgangen til mail og indhold med interne brugere og partnere, der er tillid til, med udløb og tilbagekaldelse | Anbefal – fuldt tilpasset beskyttelse med adgangsvarighed, brugeren kan manuelt spore og tilbagekalde filer | Nej – ingen tilbagekaldelse eller udløb for intern mail |
| Eksterne parter med udløb/tilbagekaldelse <br> Styr adgangen til mail og indhold med eksterne brugere/forbrugere med udløb og tilbagekaldelse | Ja – brugeren kan spore filer manuelt | Anbefal (E5) – administratoren kan tilbagekalde mails fra Security & Compliance Center |
| Automatisk mærkning <br> Organisationen ønsker automatisk at beskytte mails/vedhæftede filer med bestemt følsomt indhold og/eller bestemte modtagere | Anbefal (E5) – Automatisk mærkning i Exchange og Outlook klienter, regler for mailflow og DLP-politik | Ja – regler for mailflow og DLP-politik med beskyttelse af kryptering eller Videresend ikke |
||||

Der vil også være forskelle i slutbruger- og administratoroplevelser mellem disse to metoder.

## <a name="teams-with-protection-for-highly-sensitive-data"></a>Teams med beskyttelse af meget følsomme data

For organisationer, der planlægger at gemme personlige data i henhold til regler om beskyttelse af personlige oplysninger i Teams, skal du se [Konfigurer et team med sikkerhedsisolation](secure-teams-security-isolation.md), som indeholder detaljeret vejledning og konfigurationstrin til:

- Identitets- og enhedsadgang
- Oprettelse af et privat team
- Låsning af tilladelser til underliggende teamwebsteder
- En gruppebaseret følsomhedsmærkat med kryptering
