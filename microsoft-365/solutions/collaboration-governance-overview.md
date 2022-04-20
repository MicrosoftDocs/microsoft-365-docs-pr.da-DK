---
title: En samarbejdsstyringsramme for Microsoft 365
ms.reviewer: mmclean
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-collaboration
- m365solution-overview
- m365solution-collabgovernance
ms.custom:
- M365solutions
f1.keywords: NOCSH
recommendations: false
description: Få mere at vide om bedste praksis for styring af Microsoft 365 samarbejdsværktøjer, herunder Microsoft 365-grupper, Teams, SharePoint og Yammer.
ms.openlocfilehash: 130342725e8c43b4aeaac116b94704db3046e059
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64941385"
---
# <a name="what-is-collaboration-governance"></a>Hvad er styring af samarbejde?

Styring af samarbejde er den måde, du administrerer brugernes adgang til ressourcer på, overholder dine forretningsstandarder og sikrer sikkerheden af dine data.

Organisationer bruger i dag et alsidigt værktøjssæt. Der er teamet af udviklere, der bruger teamchat, de ledere, der sender mail, og hele organisationen opretter forbindelse via sociale virksomhedssamtaler. Flere samarbejdsværktøjer er i brug, fordi hver gruppe er unik og har deres egne funktionelle behov og arbejdsstil. Nogle vil kun bruge mail, mens andre primært vil live i chat. 

Hvis brugerne mener, at it-værktøjerne ikke passer til deres behov, vil de sandsynligvis downloade deres foretrukne forbrugerapp, som understøtter deres scenarier. Selvom denne proces giver brugerne mulighed for at komme hurtigt i gang, medfører det en frustrerende brugeroplevelse på tværs af organisationen med flere logon, problemer med at dele og intet enkelt sted at få vist indhold. Dette koncept kaldes "Shadow IT" og udgør en betydelig risiko for organisationer. Det reducerer muligheden for at administrere brugeradgang ensartet, sikre sikkerhed og overholdelse af angivne standarder for tjenesten.

Tjenester som Microsoft 365 grupper, Teams og Yammer styrke brugerne og reducerer risikoen for skygge-it ved at levere de værktøjer, der er nødvendige for at samarbejde. Microsoft 365 har en lang række værktøjer til at implementere de styringsfunktioner, din organisation måtte kræve. 

![Diagram, der viser indstillinger for styring af samarbejde i Microsoft 365.](../media/collaboration-governance-overview.png)

Denne artikelserie hjælper dig med at forstå, hvordan grupper, teams og SharePoint indstillinger interagerer, hvilke styringsfunktioner der er tilgængelige, og hvordan du opretter og implementerer en styringsramme for samarbejdsfunktionerne i Microsoft 365.

### <a name="setting-up-secure-collaboration-with-microsoft-365"></a>Konfiguration af sikkert samarbejde med Microsoft 365

Der er mange muligheder for at udrulle Microsoft 365-grupper og Teams til sikkert samarbejde i din organisation. Vi anbefaler, at du bruger dette styringsindhold sammen [med Konfigurer sikker fildeling og samarbejde med Microsoft Teams](setup-secure-collaboration-with-teams.md) og de tilknyttede artikler for at oprette den bedste samarbejdsløsning til din organisation.

### <a name="data-residency-governance"></a>Styring af dataopbevaring

Hvis din organisation er multinational, og du har krav til dataopbevaring for forskellige geografiske områder, skal du inkludere [Microsoft 365 Multi-Geo](/microsoft-365/enterprise/microsoft-365-multi-geo) som en del af din plan for styring af samarbejde.

## <a name="why-microsoft-365-groups-are-important-in-collaboration-governance"></a>Hvorfor er Microsoft 365 grupper vigtige i forbindelse med styring af samarbejde

Microsoft 365 grupper giver dig mulighed for at vælge et sæt personer, som du vil samarbejde med, og du kan nemt konfigurere en samling af ressourcer, som disse personer kan dele med. Tilføjelse af medlemmer til gruppen giver automatisk de nødvendige tilladelser til alle aktiver, der leveres af gruppen. Både Teams og Yammer bruger Microsoft 365 grupper til at administrere deres medlemskab.

Microsoft 365 grupper omfatter en pakke med sammenkædede ressourcer, som brugerne kan bruge til kommunikation og samarbejde. Grupper omfatter altid et SharePoint websted, Planner, et Power BI arbejdsområde, en postkasse og en kalender samt Stream. Afhængigt af hvordan du opretter gruppen, kan du eventuelt tilføje andre tjenester, f.eks. Teams, Yammer og Project.

![Diagram, der viser Microsoft 365-grupper og relaterede tjenester.](../media/microsoft-365-groups-hub-spoke.png)

|Ressource|Beskrivelse|
|:------|:----------|
|[Kalender](https://support.office.com/article/schedule-a-meeting-on-a-group-calendar-in-outlook-0cf1ad68-1034-4306-b367-d75e9818376a)|Til planlægning af hændelser, der er relateret til gruppen|
|[Indbakke](https://support.office.com/article/have-a-group-conversation-in-outlook-a0482e24-a769-4e39-a5ba-a7c56e828b22)|Til mailsamtaler mellem gruppemedlemmer. Denne indbakke har en mailadresse og kan indstilles til at acceptere meddelelser fra personer uden for gruppen og endda uden for din organisation på samme måde som en traditionel distributionsliste.|
|[OneNote notesbog](https://support.office.com/article/get-started-with-onenote-e768fafa-8f9b-4eac-8600-65aa10b2fe97)|Til indsamling af ideer, research og information|
|[Planner](https://support.office.com/article/microsoft-planner-help-4a9a13c6-3adf-4a60-a6fc-15c0b15e16fc)|Til tildeling og administration af projektopgaver blandt dine gruppemedlemmer|
|[Power BI arbejdsområde](/power-bi/collaborate-share/service-new-workspaces)|Et område til datasamarbejde med dashboards og rapporter|
|[Project og roadmap](https://support.microsoft.com/project)|Webbaserede projektstyringsværktøjer|
|[SharePoint teamwebsted](https://support.office.com/article/what-is-a-sharepoint-team-site-75545757-36c3-46a7-beed-0aaa74f0401e)|Et centralt lager til oplysninger, links og indhold, der relaterer til din gruppe|
|[Stream](https://support.microsoft.com/microsoft-stream)|En videostreamingtjeneste|
|[Teams](https://support.microsoft.com/teams)|Et chatbaseret arbejdsområde i Microsoft 365|
|[Yammer gruppe](https://support.office.com/article/Learn-about-Office-365-groups-b565caa1-5c40-40ef-9915-60fdb2d97fa2)|Et almindeligt sted at føre samtaler og dele oplysninger|

Microsoft 365-grupper omfatter en række styringskontrolelementer, herunder en udløbspolitik, navngivningskonventioner og en politik for blokerede ord, der kan hjælpe dig med at administrere grupper i din organisation. Da grupper styrer medlemskab og adgang til denne ressourcepakke, er administration af grupper en vigtig del af styringen af samarbejde i Microsoft 365.

## <a name="define-collaboration-governance-best-practices-for-your-organization"></a>Definer bedste praksis for styring af samarbejde for din organisation

Der er flere steder, hvor du kan samarbejde og føre samtaler i Microsoft 365. Hvis du forstår, hvor brugerne kan starte samtaler, kan det hjælpe dig med at definere en kommunikationsstrategi.

Der understøttes tre primære kommunikationsmetoder af Microsoft 365:

- Outlook: samarbejde via mail med en delt gruppeindbakke og -kalender
- Microsoft Teams: et vedvarende chatbaseret arbejdsområde, hvor du kan føre uformelle samtaler i realtid om en række forskellige emner, der er organiseret efter specifikke undergrupper
- Yammer: social virksomhedsoplevelse i forbindelse med samarbejde

![Diagram, der viser, hvornår du skal bruge Teams, Yammer og Outlook.](../media/inner-loop-outer-loop.png)

- Teams: chatbaseret arbejdsområde (samarbejde med høj hastighed) – indre løkke
  - Udviklet til samarbejde med de personer, dine brugere arbejder med hver dag
  - Sætter oplysninger lige ved hånden af brugerne i en enkelt oplevelse
  - Tilføj faner, forbindelser og robotter
  - Livechat, lyd-/videomøde, optagne møder

- Yammer: Opret forbindelse på tværs af organisationen (social virksomhed) – ydre løkke
  - Praksisfællesskaber – tværfunktionelle grupper af personer, der har fælles interesse eller ekspertise, men som ikke nødvendigvis arbejder sammen i det daglige
  - Lederforbindelse, lærings communities, rollebaserede communities

- Postkasse og kalender (mailbaseret samarbejde)
  - Bruges til målrettet kommunikation med en gruppe personer
  - Delt kalender for møder med andre gruppemedlemmer
 
Når du bestemmer, hvordan du vil bruge samarbejdsfunktioner i Microsoft 365, skal du overveje disse kommunikationsmetoder, og hvilke brugerne sandsynligvis vil bruge i forskellige scenarier.

> [!NOTE]
> Når der oprettes en ny Office 365-gruppe via Yammer eller Teams, er gruppen ikke synlig i Outlook eller i adressekartoteket, fordi den primære kommunikation mellem disse brugere sker i deres respektive klienter. Yammer grupper kan ikke have forbindelse til Teams.

## <a name="collaboration-governance-best-practices-checklist"></a>Tjekliste til bedste praksis for styring af samarbejde

Når du starter planlægningsprocessen for styringen, skal du være opmærksom på disse bedste fremgangsmåder:

- **Tal med dine brugere** – identificer dine største brugere af samarbejdsfunktioner, og mød dem for at forstå deres kerneforretningskrav og use case-scenarier.

- **Afstem risici og fordele** – gennemse din virksomheds, lovmæssige, juridiske og overholdelse af angivne standarder, og planlæg en løsning, der optimerer til alle resultater.

- **Tilpas til forskellige organisationer og forskellige typer indhold og scenarier** – overvej de forskellige behov for forskellige grupper eller afdelinger og forskellige typer indhold, f.eks. intranetindhold i forhold til en brugers OneDrive indhold.

- **Juster efter forretningsprioriteter** – forretningsmål hjælper dig med at definere, hvor meget tid og energi du har brug for at investere i styring.

- **Integrer beslutninger om styring direkte i de løsninger, du opretter** – mange beslutninger om styring kan implementeres ved at aktivere eller deaktivere funktioner i Microsoft 365.


- **Brug en faseinddelt tilgang** – Udrul samarbejdsfunktioner til en lille gruppe brugere først. Få feedback fra dem, hold øje med helpdeskanmodninger, og opdater eventuelle nødvendige indstillinger eller processer, før du fortsætter til en større gruppe.

- **Underdan med oplæring** – tilpas løsninger som [f.eks. Microsoft 365 læringsforløb](/office365/customlearning) for at sikre, at dine organisationsspecifikke forventninger styrkes med Microsoft-drevne kurser.

- **Hav en strategi for kommunikation af styringspolitikker og retningslinjer i din organisation** . Opret et Microsoft 365 Adoption Center på et SharePoint kommunikationswebsted for at kommunikere politikker og procedurer.

- **Definer roller og ansvar** – identificer dit styringskerneteam, og arbejd først med vigtige styringsbeslutninger om klargøring og navngivning og ekstern adgang, og gennemgå derefter de resterende beslutninger.

- **Gå tilbage til dine beslutninger i takt med forretnings- og teknologiændringer** – mød jævnligt for at gennemgå nye funktioner og nye forretningsforventninger.

Hvis du vil se nærmere på disse fremgangsmåder, skal du læse [Opret din plan for styring af samarbejde](collaboration-governance-first.md).

## <a name="end-user-impact-and-change-management"></a>Slutbrugerens indvirkning og ændringsstyring

Da grupper og teams kan oprettes på flere måder, anbefaler vi, at du oplærer dine brugere til at bruge den metode, der passer bedst til din organisation:

- Hvis din organisation udfører det meste af sin kommunikation via mail, skal du instruere dine brugere i at oprette grupper i Outlook.
- Hvis din organisation bruger SharePoint eller overfører fra SharePoint i det lokale miljø, skal du bede brugerne om at oprette SharePoint teamwebsteder til samarbejde.
- Hvis din organisation har udrullet Teams, kan du bede brugerne om at oprette et team, når de har brug for et samarbejdsområde.

Dette hjælper med at undgå forvirring, hvis brugerne ikke er bekendt med, hvordan grupper er relateret til deres relaterede tjenester. Du kan få flere oplysninger om, hvordan du taler med dine brugere om grupper, under [Forklare Microsoft 365-grupper til dine brugere](../admin/create-groups/explain-groups-knowledge-worker.md).

## <a name="key-collaboration-governance-capabilities-and-licensing-requirements"></a>Vigtige funktioner til styring af samarbejde og licenskrav

Styringsfunktioner til samarbejde i Microsoft 365 omfatter funktioner i Microsoft 365, Teams, SharePoint og Azure Active Directory.

| Funktionalitet eller funktion | Beskrivelse | Licensering |
|:----------------------|:------------|:----------|
|Deling af team og websted|Kontrollér, om teams, grupper og websteder kan deles med personer uden for din organisation.|Microsoft 365 E5 eller E3|
|Tillad/bloker domæne|Begræns deling med personer uden for din organisation til personer fra bestemte domæner.|Microsoft 365 E5 eller E3|
|Oprettelse af selvbetjeningswebsted|Tillad eller undgå, at brugerne opretter deres egne SharePoint websteder.|Microsoft 365 E5 eller E3|
|Begrænset websteds- og fildeling|Begræns deling af websteder, filer og mapper til medlemmer af en bestemt sikkerhedsgruppe.|Microsoft 365 E5 eller E3|
|Oprettelse af begrænset gruppe|Begræns oprettelse af team og gruppe til medlemmer af en bestemt sikkerhedsgruppe.|Microsoft 365 E5 eller E3 med Azure AD Premium- eller Azure AD Basic EDU-licenser|
|Politik for navngivning af gruppe|Gennemtving præfikser eller suffikser for gruppe- og teamnavne.|Microsoft 365 E5 eller E3 med Azure AD Premium- eller Azure AD Basic EDU-licenser|
|Politik for gruppeudløb|Angiv inaktive grupper og teams til at udløbe og slettes efter et angivet tidsrum.|Microsoft 365 E5 eller E3 med Azure AD Premium licenser|
|Gæsteadgang pr. gruppe|Tillad eller undgå deling af team og grupper med personer uden for din organisation pr. gruppe.|Microsoft 365 E5 eller E3|

## <a name="collaboration-governance-planning-recommendations"></a>Anbefalinger til planlægning af styring af samarbejde

Følg disse grundlæggende trin for at oprette din styringsplan:

1. Overvej vigtige forretningsmål og -processer – [opret din styringsplan](collaboration-governance-first.md) for at opfylde din virksomheds behov.
2. Forstå indstillinger i tjenester – [indstillinger i grupper og SharePoint](groups-sharepoint-governance.md) interagere med hinanden, ligesom [indstillinger i grupper, SharePoint og Teams](groups-sharepoint-teams-governance.md) og [andre tjenester](groups-services-interactions.md). Sørg for at forstå disse interaktioner, når du planlægger din strategi for styring.
3. Planlæg at administrere brugeradgang – planlæg [det adgangsniveau, du vil tildele brugere i grupper, SharePoint og Teams](groups-teams-access-governance.md).
4. Planlæg administration af indstillinger for overholdelse af angivne standarder – gennemse de tilgængelige [indstillinger for overholdelse af angivne standarder for Microsoft 365 grupper, Teams og SharePoint samarbejde](groups-teams-compliance-governance.md).
5. Planlæg at administrere kommunikation – gennemse de tilgængelige [muligheder for styring af kommunikation i forbindelse med samarbejdsscenarier](groups-teams-communication-governance.md).
6. Planlæg styring af organisation og livscyklus – vælg [de politikker, du vil bruge til oprettelse af grupper og team, navngivning, udløb og arkivering](plan-organization-lifecycle-governance.md). Forstå også [slutningen af livscyklusmulighederne for grupper, teams og Yammer](end-life-cycle-groups-teams-sites-yammer.md)

![Illustration af anbefalede styringstrin.](../media/collaboration-governance-steps.png)

## <a name="training-for-administrators"></a>Oplæring af administratorer

Disse træningsmoduler fra Microsoft Learn kan hjælpe dig med at lære styringsfunktionerne i Microsoft 365.

#### <a name="information-protection"></a>Beskyttelse af oplysninger

|Uddannelse:|Administrer beskyttelse og styring af oplysninger|
|:---|:---|
|![Oplæringsikonet Information Protection.](../media/information-protection-governance.svg)|Mængden af data, der genereres i dag, vokser hurtigere end nogensinde før, medarbejderne ønsker at få arbejdet udført overalt, og det lovgivningsmæssige landskab ændrer sig konstant. Microsofts løsninger til beskyttelse og styring af oplysninger hjælper organisationer med at opnå den rette balance mellem at holde deres data beskyttet og deres medarbejdere produktive. Dette læringsforløb kan hjælpe dig med at forberede dig på Microsoft 365 Certificeret: Sikkerhedsadministratormedarbejder og Microsoft 365 Certificeret: Certificeringer fra virksomhedsadministrationseksperter.<br><br>5 t. 13 min. – Learning sti – 7 moduler|

> [!div class="nextstepaction"]
> [Start >](/learn/modules/m365-compliance-information-governance/introduction/)

<br><br>

|Uddannelse:|Beskyt virksomhedsoplysninger med Microsoft 365|
|:---|:---|
|![Teams træningsikon.](../media/protect-enterprise-information-microsoft-365.svg)|Det er mere udfordrende end nogensinde før at beskytte og beskytte din organisations oplysninger. Læringsforløbet Beskyt virksomhedsoplysninger med Microsoft 365 beskriver, hvordan du beskytter dine følsomme oplysninger mod utilsigtet overdeling eller misbrug, hvordan du finder og klassificerer data, hvordan du beskytter dem med følsomhedsmærkater, og hvordan du både overvåger og analyserer dine følsomme oplysninger for at beskytte mod tab. Dette læringsforløb kan hjælpe dig med at forberede dig på Microsoft 365 Certificeret: Sikkerhedsadministratormedarbejder og Microsoft 365 certificeret: Certificeringer fra virksomhedsadministrationseksperter..<br><br>1 t. – Learning sti – 5 moduler|

> [!div class="nextstepaction"]
> [Start >](/learn/modules/m365-security-info-overview/introduction/)

#### <a name="security-and-compliance"></a>Sikkerhed og overholdelse af angivne standarder

|Uddannelse:|Demonstrer grundlæggende viden om Microsoft 365 funktioner til sikkerhed og overholdelse af angivne standarder|
|:---|:---|
|![Ikon for oplæring i sikkerhed og overholdelse af angivne standarder.](../media/microsoft-365-security-and-compliance-capabilities.svg)|Få mere at vide om områderne Microsoft 365 løsninger til sikkerhed og overholdelse af angivne standarder og de funktioner, der er tilgængelige for at hjælpe virksomheder med at sikre deres virksomhed og opfylde lovmæssige krav. Hvis du ikke er fortrolig med grundlæggende cloudcomputingkoncepter, anbefaler vi, at du tager [Cloud Concepts – principper for cloudcomputing](/learn/modules/principles-cloud-computing/index).<br><br>3 t. 11 min. - Learning sti - 8 moduler|

> [!div class="nextstepaction"]
> [Start >](/learn/modules/what-is-m365/1-introduction/)

## <a name="illustrations"></a>Illustrationer

Disse illustrationer hjælper dig med at forstå, hvordan grupper og teams interagerer med andre tjenester i Microsoft 365, og hvilke funktioner til styring og overholdelse af angivne standarder der er tilgængelige, som kan hjælpe dig med at administrere disse tjenester i din organisation.

### <a name="groups-in-microsoft-365-for-it-architects"></a>Grupper i Microsoft 365 for it-arkitekter
Det har it-arkitekter brug for at vide om grupper i Microsoft 365

|**Element**|**Beskrivelse**|
|:-----|:-----|
|[![Miniaturebillede for gruppers infografik.](../downloads/msft-m365-groups-architecture-thumb.png)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/msft-m365-groups.pdf) <br/> [PDF](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/msft-m365-groups.pdf) \| [Visio](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/msft-m365-groups.vsdx) <br> Opdateret i juni 2019|Disse illustrationer beskriver de forskellige typer af grupper, hvordan de oprettes og administreres, og nogle få anbefalinger til styring.|

### <a name="microsoft-teams-and-related-productivity-services-in-microsoft-365-for-it-architects"></a>Microsoft Teams og relaterede produktivitetstjenester i Microsoft 365 for it-arkitekter
Den logiske arkitektur af produktivitetstjenester i Microsoft 365, der fører med Microsoft Teams.

|**Element**|**Beskrivelse**|
|:-----|:-----|
|[![Thumb image for Teams logisk arkitektur plakat.](../downloads/msft-teams-logical-architecture-thumb.png)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/msft-m365-teams-logical-architecture.pdf) <br/> [PDF](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/msft-m365-teams-logical-architecture.pdf) \| [Visio](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/msft-m365-teams-logical-architecture.vsdx)  <br>Opdateret i april 2019   |Microsoft leverer en pakke med produktivitetstjenester, der arbejder sammen om at levere samarbejdsoplevelser med datastyring, sikkerhed og funktionalitet til overholdelse af angivne standarder. <br/> <br/>Denne serie illustrationer giver et overblik over den logiske arkitektur af produktivitetstjenester for virksomhedsarkitekter, der fører an i Microsoft Teams.|

### <a name="microsoft-365-information-protection-and-compliance-capabilities"></a>Microsoft 365 funktioner til beskyttelse af oplysninger og overholdelse af angivne standarder

Microsoft 365 omfatter en lang række funktioner til beskyttelse af oplysninger og overholdelse af angivne standarder. Sammen med Microsofts produktivitetsværktøjer er disse funktioner designet til at hjælpe organisationer med at samarbejde i realtid, samtidig med at de overholder strenge lovgivningsmæssige rammer for overholdelse af angivne standarder. 

Dette sæt illustrationer bruger en af de mest regulerede industrier, finansielle tjenester, til at vise, hvordan disse funktioner kan anvendes til at håndtere fælles lovgivningsmæssige krav. Du er velkommen til at tilpasse disse illustrationer til eget brug. 


| Element | Beskrivelse |
|:-----|:-----|
|[![Modelplakat: Microsoft Purview information protection and compliance capabilities.](../media/solutions-architecture-center/m365-compliance-illustrations-thumb.png)](https://download.microsoft.com/download/3/a/6/3a6ab1a3-feb0-4ee2-8e77-62415a772e53/m365-compliance-illustrations.pdf) <br/> Engelsk: [Download som en PDF Download](https://download.microsoft.com/download/3/a/6/3a6ab1a3-feb0-4ee2-8e77-62415a772e53/m365-compliance-illustrations.pdf)\| [som en Visio](https://download.microsoft.com/download/3/a/6/3a6ab1a3-feb0-4ee2-8e77-62415a772e53/m365-compliance-illustrations.vsdx)   <br/> Japansk: [Download som en PDF-download](https://download.microsoft.com/download/6/f/1/6f1a7d0e-dd8e-442e-b073-8e94327ae4f8/m365-compliance-illustrations.pdf)\| [som en Visio](https://download.microsoft.com/download/6/f/1/6f1a7d0e-dd8e-442e-b073-8e94327ae4f8/m365-compliance-illustrations.vsdx)   <br/> Opdateret i november 2020|Omfatter: <ul><li>  Microsoft Purview Information Protection og Microsoft Purview forebyggelse af datatab</li><li>Opbevaringspolitikker og opbevaringsmærkater </li><li>Informationsbarrierer</li><li>Kommunikationsoverholdelse</li><li>Insiderrisiko</li><li>Dataindtagelse fra tredjepart</li>|

## <a name="conference-sessions"></a>Mødesessioner

Se disse mødesessioner for at få mere at vide om styring af Microsoft 365-grupper og Teams.

**Fundamentals**

Få mere at vide om de grundlæggende funktioner og nye innovationer i Microsoft 365-grupper, herunder administration og styring i stor skala, bedste praksis for kørsel af brug og implementering samt selvbetjening.

- [Tag imod Microsoft 365-grupper](https://www.youtube.com/watch?v=dAamBF1gb7M)

**Styring**

Få mere at vide om, hvordan du konfigurerer dine gruppers udløbslivscyklus, navngivningspolitikker, klassificeringsmærkater, samarbejde med eksterne gæster og administrere tilladelser til oprettelse af grupper.

- [Transformér samarbejde, og bekæmp skygge-it med Office 365 grupper](https://www.youtube.com/watch?v=Bhf_bKx3lAg)

**Kundeeksempel**

Se et eksempel bag kulisserne på, hvordan Microsoft 365-grupper, SharePoint, Teams og Yammer arbejder sammen om at levere en global samarbejdsplatform.

- [Find et godt sted at samarbejde med Office 365 Grupper, SharePoint, Teams og Yammer](https://www.youtube.com/watch?v=Rx9eVwqXeQk)

## <a name="see-also"></a>Se også

[Microsoft 365 sikkerhedsdokumentation](../security/index.yml)

[Dokumentation til Microsoft Purview](../compliance/index.yml)