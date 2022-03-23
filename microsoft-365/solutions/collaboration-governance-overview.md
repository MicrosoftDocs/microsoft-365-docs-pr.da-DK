---
title: En ramme for samarbejdsstyring for Microsoft 365
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
description: Lær om bedste praksis for styring Microsoft 365 samarbejdsværktøjer, herunder Microsoft 365 grupper, Teams, SharePoint og Yammer.
ms.openlocfilehash: 62030dcb9b89105f87a0cf50f1b950b816727015
ms.sourcegitcommit: c2b5ce3150ae998e18a51bad23277cedad1f06c6
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/17/2021
ms.locfileid: "63588468"
---
# <a name="what-is-collaboration-governance"></a>Hvad er styring af samarbejde?

Styring af samarbejde er den måde, du administrerer brugernes adgang til ressourcer på, overholder virksomhedens standarder og sikrer sikkerheden for dine data.

Organisationer bruger i dag et forskelligt værktøjssæt. Der er et team af udviklere, der bruger teamchat, ledere, der sender mails, og hele organisationen opretter forbindelse via sociale netværk for virksomheder. Der bruges flere samarbejdsværktøjer, fordi hver gruppe er unik og har sine egne funktionelle behov og arbejdsstil. Nogle vil kun bruge mail, mens andre primært vil bo i chat. 

Hvis brugerne føler, at de it-leverede værktøjer ikke opfylder deres behov, vil de sandsynligvis downloade deres foretrukne forbrugerapp, der understøtter deres scenarier. Selvom denne proces giver brugerne mulighed for at komme hurtigt i gang, giver det en frustrerende brugeroplevelse i hele organisationen med flere logons, besvær med at dele og intet enkelt sted at få vist indhold. Dette koncept kaldes for "Skygge IT" og udgør en betydelig risiko for organisationer. Det reducerer muligheden for at administrere brugeradgangen ensartet, sikre behov for sikkerhed og tjenesteoverholdelse.

Tjenester som f.eks. Microsoft 365 grupper, Teams og Yammer giver brugerne nye værktøjer og reducerer risikoen for skygge-it ved at levere de værktøjer, der er nødvendige for at samarbejde. Microsoft 365 har et omfattende sæt værktøjer til at implementere de styringsfunktioner, din organisation måtte kræve. 

![Diagram, der viser indstillinger for styring af samarbejde Microsoft 365.](../media/collaboration-governance-overview.png)

Denne serie af artikler hjælper dig med at forstå, hvordan grupper, teams og SharePoint-indstillinger interagerer, hvilke styringsfunktioner der er tilgængelige, og hvordan du opretter og implementerer en styringsstruktur for samarbejdsfunktionerne i Microsoft 365.

### <a name="setting-up-secure-collaboration-with-microsoft-365"></a>Konfiguration af sikkert samarbejde med Microsoft 365

Der er mange muligheder for at udrulle Microsoft 365 Grupper og Teams for sikkert samarbejde i organisationen. Vi anbefaler, at du bruger dette indhold til styring sammen med Konfigurer sikker fildeling og samarbejde [med Microsoft Teams](setup-secure-collaboration-with-teams.md) og de tilknyttede artikler for at skabe den bedste samarbejdsløsning for din organisation.

### <a name="data-residency-governance"></a>Styring af dataopbevaring

Hvis din organisation er multi national, og du har krav til dataopbevaring for forskellige områder, skal [du Microsoft 365 multi-geo](/microsoft-365/enterprise/microsoft-365-multi-geo) som en del af din plan for styring af samarbejde.

## <a name="why-microsoft-365-groups-are-important-in-collaboration-governance"></a>Derfor Microsoft 365 grupperinger vigtige for samarbejdsstyringen

Microsoft 365 grupper kan du vælge en gruppe af personer, som du ønsker at samarbejde med, og nemt konfigurere en ressourcesamling, som de pågældende personer kan dele med. Når du føjer medlemmer til gruppen, får de nødvendige tilladelser til alle aktiver leveret af gruppen automatisk. Både Teams og Yammer bruger Microsoft 365 til at administrere deres medlemskab.

Microsoft 365 indeholder en pakke med sammenkædede ressourcer, som brugerne kan bruge til kommunikation og samarbejde. Grupper omfatter altid et SharePoint, Planner, et Power BI arbejdsområde, en postkasse og kalender og Stream. Afhængigt af hvordan du opretter gruppen, kan du vælge at tilføje andre tjenester, f.eks. Teams, Yammer og Project.

![Diagram, der Microsoft 365 grupper og relaterede tjenester.](../media/microsoft-365-groups-hub-spoke.png)

|Ressource|Beskrivelse|
|:------|:----------|
|[Kalender](https://support.office.com/article/schedule-a-meeting-on-a-group-calendar-in-outlook-0cf1ad68-1034-4306-b367-d75e9818376a)|Ved planlægning af begivenheder, der er relateret til gruppen|
|[Indbakke](https://support.office.com/article/have-a-group-conversation-in-outlook-a0482e24-a769-4e39-a5ba-a7c56e828b22)|Til mailsamtaler mellem gruppemedlemmer. Denne indbakke har en mailadresse og kan indstilles til at acceptere meddelelser fra personer uden for gruppen og endda uden for organisationen, ligesom en traditionel distributionsliste.|
|[OneNote notesbog](https://support.office.com/article/get-started-with-onenote-e768fafa-8f9b-4eac-8600-65aa10b2fe97)|Til indsamling af ideer, research og information|
|[Planner](https://support.office.com/article/microsoft-planner-help-4a9a13c6-3adf-4a60-a6fc-15c0b15e16fc)|Til tildeling og administration af projektopgaver blandt dine gruppemedlemmer|
|[Power BI arbejdsområde](/power-bi/collaborate-share/service-new-workspaces)|Et datasamarbejdeområde med dashboards og rapporter|
|[Project og oversigt](https://support.microsoft.com/project)|Webbaserede projektstyringsværktøjer|
|[SharePoint teamwebsted](https://support.office.com/article/what-is-a-sharepoint-team-site-75545757-36c3-46a7-beed-0aaa74f0401e)|Et centralt lager til oplysninger, links og indhold, der er knyttet til din gruppe|
|[Stream](https://support.microsoft.com/microsoft-stream)|En videostreamingtjeneste|
|[Teams](https://support.microsoft.com/teams)|Et chatbaseret arbejdsområde i Microsoft 365|
|[Yammer gruppe](https://support.office.com/article/Learn-about-Office-365-groups-b565caa1-5c40-40ef-9915-60fdb2d97fa2)|Et fælles sted at have samtaler og dele oplysninger|

Microsoft 365 indeholder en række forskellige styringskontrolelementer, herunder en udløbspolitik, navngivningskonventioner og en politik for blokerede ord, der kan hjælpe dig med at administrere grupper i organisationen. Da grupper styrer medlemskab og adgang til denne ressourcepakke, er administration af grupper en vigtig del af at styre samarbejdet i Microsoft 365.

## <a name="define-collaboration-governance-best-practices-for-your-organization"></a>Definer bedste fremgangsmåder for samarbejdsstyring for din organisation

Der er flere forskellige steder at samarbejde og have samtaler i Microsoft 365. Når du forstår, hvor brugerne kan starte samtaler, kan det hjælpe dig med at definere en strategi for kommunikation.

Der er tre primære kommunikationsmetoder, der understøttes af Microsoft 365:

- Outlook: samarbejde via mail med en delt gruppeindbakke og kalender
- Microsoft Teams: et fast chatbaseret arbejdsområde, hvor man kan have uformelle samtaler i realtid om en række emner, der er organiseret efter bestemte undergrupper
- Yammer: Social oplevelse for virksomheder til samarbejde

![Diagram, der viser, hvornår du Teams, Yammer og Outlook.](../media/inner-loop-outer-loop.png)

- Teams: chatbaseret arbejdsområde (samarbejde ved høj hastighed) – indre løkke
  - Udviklet til samarbejde med de personer, dine brugere arbejder sammen med hver dag
  - Giver oplysninger lige ved hånden for brugerne i en enkelt oplevelse
  - Tilføj faner, forbindelser og botter
  - Livechat, lyd-/videomøder, optagede møder

- Yammer: Opret forbindelse på tværs af organisationen (socialt netværk for virksomheder) – ydre løkke
  - Praksisfællesskaber – Tværfunktionelle grupper af personer, som har fælles interesser eller ekspertise, men som ikke nødvendigvis samarbejder på daglig basis
  - Lederforbindelse, læringsfællesskaber, rollebaserede communities

- Postkasse og kalender (mailbaseret samarbejde)
  - Bruges til målrettet kommunikation med en gruppe personer
  - Delt kalender for møder med andre gruppemedlemmer
 
Når du beslutter, hvordan du vil bruge samarbejdsfunktioner i Microsoft 365, kan du overveje disse kommunikationsmetoder, og hvilke brugere der sandsynligvis vil bruge i forskellige scenarier.

> [!NOTE]
> Når der oprettes en ny Office 365-gruppe via Yammer eller Teams, er gruppen ikke synlig i Outlook eller adressekartoteket, fordi den primære kommunikation mellem disse brugere sker i deres respektive klienter. Yammer-grupper kan ikke forbindes Teams.

## <a name="collaboration-governance-best-practices-checklist"></a>Tjekliste for bedste praksis for samarbejdsstyring

Når du starter planlægningsprocessen for styringen, skal du huske på følgende bedste fremgangsmåder:

- **Tal med dine brugere –** identificer de største brugere af samarbejdsfunktioner, og mød dem for at forstå deres kerne forretningskrav og scenarier med use case- scenarier.

- **Balancer risici og fordele** – gennemgå dine behov for forretning, lovgivning, juridiske og overholdelse af regler og standarder, og planlæg en løsning, der optimerer for alle resultater.

- **Tilpas til forskellige** organisationer og forskellige typer indhold og scenarier – overvej de forskellige behov for forskellige grupper eller afdelinger og forskellige typer indhold, f.eks intranetindhold kontra en brugers OneDrive indhold.

- **Juster til virksomhedsprioriteter** – forretningsmål kan hjælpe dig med at definere, hvor meget tid og energi du har brug for til at investere i styringen.

- **Integrer styringsbeslutninger direkte i** de løsninger, du opretter – mange styringsbeslutninger kan gennemføres ved at slå funktioner til eller Microsoft 365.


- **Brug en trinvis tilgang –** Rul samarbejdsfunktioner ud til en lille gruppe af brugere først. Få feedback fra dem, se efter helpdeskbilletter, og opdater de nødvendige indstillinger eller processer, før du fortsætter til en større gruppe.

- **Styrke uddannelse –** tilpas løsninger som [f.eks. Microsoft 365 læringsstier](/office365/customlearning) for at sikre, at din organisations specifikke forventninger understøttes af Microsoft-uddannelsesressourcer.

- **Hav en strategi til kommunikation** af styringspolitikker og retningslinjer i din organisation – opret et Microsoft 365 Adoption Center i et SharePoint-kommunikationswebsted til kommunikation af politikker og procedurer.

- **Definer roller og** ansvarsområder – identificer dit lederteam, og arbejd gennem vigtige styringsbeslutninger om klargøring og navngivning og ekstern adgang først, og arbejd derefter gennem de resterende beslutninger.

- **Gennemgå dine beslutninger i forbindelse med virksomheds- og teknologiændringer** – mødes med jævne mellemrum for at gennemgå nye funktioner og nye forretningsmæssige forventninger.

Hvis du vil se nærmere på disse fremgangsmåder, skal du [læse Opret din plan for styring af samarbejde](collaboration-governance-first.md).

## <a name="end-user-impact-and-change-management"></a>Slutbrugerens virkning og administration af ændringer

Da grupper og teams kan oprettes på flere måder, anbefaler vi, at du lærer dine brugere at bruge den metode, der passer bedst til din organisation:

- Hvis din organisation gør det meste af sin kommunikation via mail, skal du bede dine brugere om at oprette grupper Outlook.
- Hvis din organisation bruger meget SharePoint eller overfører fra SharePoint lokalt miljø, skal du bede dine brugere om at SharePoint teamwebsteder til samarbejde.
- Hvis din organisation har installeret en Teams, skal du bede dine brugere om at oprette et team, når de skal bruge et samarbejdsområde.

Dette hjælper med at undgå forvirring, hvis brugerne ikke er bekendt med, hvordan grupperne er relateret til deres relaterede tjenester. Du kan finde flere oplysninger om, hvordan du taler med dine brugere om grupper, [i forklaring Microsoft 365 grupper til dine brugere](../admin/create-groups/explain-groups-knowledge-worker.md).

## <a name="key-collaboration-governance-capabilities-and-licensing-requirements"></a>Vigtige funktioner til styring af samarbejde og licenskrav

Styringsfunktioner til samarbejde i Microsoft 365 omfatter funktioner i Microsoft 365, Teams, SharePoint og Azure Active Directory.

| Funktionalitet eller funktion | Beskrivelse | Licensering |
|:----------------------|:------------|:----------|
|Team- og webstedsdeling|Kontroller, om teams, grupper og websteder kan deles med personer uden for organisationen.|Microsoft 365 E5 eller E3|
|Tillad/bloker for domæne|Begræns deling med personer uden for organisationen til personer fra bestemte domæner.|Microsoft 365 E5 eller E3|
|Oprettelse af et websted til selvbetjening|Tillad eller forbyd, at brugerne opretter deres egne SharePoint websteder.|Microsoft 365 E5 eller E3|
|Begrænset websteds- og fildeling|Begræns websteds-, fil- og mappedeling til medlemmer af en bestemt sikkerhedsgruppe.|Microsoft 365 E5 eller E3|
|Oprettelse af begrænset gruppe|Begrænse oprettelse af team og grupper til medlemmer af en bestemt sikkerhedsgruppe.|Microsoft 365 E5 eller E3 med Azure AD Premium eller Azure AD Basic EDU-licenser|
|Politik for gruppenavngivning|Gennemtving præfikser eller suffikser på gruppe- og teamnavne.|Microsoft 365 E5 eller E3 med Azure AD Premium eller Azure AD Basic EDU-licenser|
|Udløbspolitik for gruppe|Indstil inaktive grupper og teams til at udløbe og blive slettet efter en bestemt tidsperiode.|Microsoft 365 E5 eller E3 med Azure AD Premium-licenser|
|Gæsteadgang pr. gruppe|Tillad eller forbyd deling af team og gruppe med personer uden for organisationen pr. gruppe.|Microsoft 365 E5 eller E3|

## <a name="collaboration-governance-planning-recommendations"></a>Anbefalinger til planlægning af styring af samarbejde

Følg disse grundlæggende trin for at oprette din styringsplan:

1. Overvej de vigtigste forretningsmål og processer – [opret din styringsplan](collaboration-governance-first.md) , så den opfylder behovene i din virksomhed.
2. Forstå indstillinger i tjenester – indstillinger i grupper [og SharePoint](groups-sharepoint-governance.md) interagerer med hinanden, og det samme gør indstillingerne i grupper[, SharePoint og Teams](groups-sharepoint-teams-governance.md) [og andre tjenester](groups-services-interactions.md). Sørg for at forstå disse interaktioner, når du planlægger din styringsstrategi.
3. Planlæg at administrere brugeradgang – [planlæg det adgangsniveau, du vil tildele brugere i grupper, SharePoint og Teams](groups-teams-access-governance.md).
4. Planlæg at administrere indstillinger for overholdelse – gennemse de tilgængelige indstillinger [for overholdelse Microsoft 365 grupper, Teams og SharePoint samarbejde](groups-teams-compliance-governance.md).
5. Planlæg at administrere kommunikation – gennemgå de tilgængelige [indstillinger for kommunikationsstyring for samarbejdsscenarier](groups-teams-communication-governance.md).
6. Planlæg styring af organisation og livscyklus – vælg de politikker, du vil bruge til gruppe- og [teamoprettelse, navngivning, udløbsdato og arkivering](plan-organization-lifecycle-governance.md). Forstå også slutningen [af indstillinger for livscyklus for grupper, teams og Yammer](end-life-cycle-groups-teams-sites-yammer.md)

![Illustration af anbefalede styringstrin.](../media/collaboration-governance-steps.png)

## <a name="training-for-administrators"></a>Kurser til administratorer

Disse kursusmoduler fra Microsoft Learn kan hjælpe dig med at lære styringsfunktionerne i Microsoft 365.

#### <a name="information-protection"></a>Beskyttelse af oplysninger

|Kursus:|Administrer beskyttelse og styring af oplysninger|
|:---|:---|
|![Ikon for uddannelse i beskyttelse af oplysninger.](../media/information-protection-governance.svg)|Mængden af data, der genereres i dag, vokser hurtigere end nogensinde før, medarbejdere ønsker at få arbejdet udført overalt, og det lovgivningsmæssige landskab ændres hele tiden. Microsofts løsninger til beskyttelse af oplysninger og styring hjælper organisationer med at opnå den rette balance mellem at holde deres data beskyttede og deres personer produktive. Denne læringssti kan hjælpe dig med at forberede dig til Microsoft 365 certificeret: Security Administrator Associate og Microsoft 365 Certified: Enterprise Administration Expert-certificeringer.<br><br>5 timer 13 min - Learning Sti - 7 moduler|

> [!div class="nextstepaction"]
> [Start >](/learn/modules/m365-compliance-information-governance/introduction/)

<br><br>

|Kursus:|Beskyt virksomhedsoplysninger med Microsoft 365|
|:---|:---|
|![Teams kursusikon.](../media/protect-enterprise-information-microsoft-365.svg)|At beskytte og sikre din organisations oplysninger er mere udfordrende end nogensinde før. I læringsstien Beskyt virksomhedsoplysninger med Microsoft 365 beskrives det, hvordan du beskytter dine følsomme oplysninger mod utilsigtet overdeling eller misbrug, hvordan du finder og klassificerer data, hvordan du beskytter dem med følsomhedsmærkater, og hvordan du både overvåger og analyserer dine følsomme oplysninger for at beskytte dig mod tab. Denne læringssti kan hjælpe dig med at forberede dig til Microsoft 365 certificeret: Security Administrator Associate og Microsoft 365 Certified: Enterprise Administration Expert-certificeringer.<br><br>1 timer - Learning Sti - 5 moduler|

> [!div class="nextstepaction"]
> [Start >](/learn/modules/m365-security-info-overview/introduction/)

#### <a name="security-and-compliance"></a>Sikkerhed og overholdelse af regler og standarder

|Kursus:|Demonstrere grundlæggende viden om Microsoft 365 og overholdelse af regler og standarder|
|:---|:---|
|![Ikon for uddannelse i sikkerhed og overholdelse af regler og standarder.](../media/microsoft-365-security-and-compliance-capabilities.svg)|Få mere at vide Microsoft 365 inden for sikkerheds- og overholdelsesløsninger og de funktioner, der er tilgængelige for at hjælpe virksomheder med at sikre deres virksomhed og opfylde lovmæssige krav. Hvis du ikke er bekendt med grundlæggende begreber inden for cloud computing, anbefaler vi, at du [tager skykoncepter – principper for cloud computing](/learn/modules/principles-cloud-computing/index).<br><br>3 timer 11 min - Learning Sti - 8 moduler|

> [!div class="nextstepaction"]
> [Start >](/learn/modules/what-is-m365/1-introduction/)

## <a name="illustrations"></a>Illustrationer

Disse illustrationer hjælper dig med at forstå, hvordan grupper og teams interagerer med andre tjenester i Microsoft 365 og hvilke funktioner til styring og overholdelse, der er tilgængelige til at hjælpe dig med at administrere disse tjenester i organisationen.

### <a name="groups-in-microsoft-365-for-it-architects"></a>Grupper i Microsoft 365 til IT-arkitekter
Hvad it-arkitekter har brug for at vide om grupper i Microsoft 365

|**Element**|**Beskrivelse**|
|:-----|:-----|
|[![Miniaturebillede til gruppe infografik.](../downloads/msft-m365-groups-architecture-thumb.png)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/msft-m365-groups.pdf) <br/> [PDF](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/msft-m365-groups.pdf) \| [Visio](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/msft-m365-groups.vsdx) <br> Opdateret juni 2019|Disse illustrationer beskriver de forskellige typer grupper, hvordan de oprettes og administreres, og nogle få anbefalinger om styring.|

### <a name="microsoft-teams-and-related-productivity-services-in-microsoft-365-for-it-architects"></a>Microsoft Teams og relaterede produktivitetstjenester i Microsoft 365 til IT-arkitekter
Den logiske arkitektur for produktivitetstjenester i Microsoft 365, der har Microsoft Teams.

|**Element**|**Beskrivelse**|
|:-----|:-----|
|[![Miniaturebillede til Teams logisk arkitekturplakat.](../downloads/msft-teams-logical-architecture-thumb.png)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/msft-m365-teams-logical-architecture.pdf) <br/> [PDF](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/msft-m365-teams-logical-architecture.pdf) \| [Visio](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/msft-m365-teams-logical-architecture.vsdx)  <br>Opdateret april 2019   |Microsoft leverer en pakke med produktivitetstjenester, der arbejder sammen for at give samarbejdsoplevelser med datastyring, sikkerhed og overholdelse af regler og standarder. <br/> <br/>Denne serie af illustrationer giver et indblik i den logiske arkitektur i produktivitetstjenester for virksomhedsarkitekter, der er førende med Microsoft Teams.|

### <a name="microsoft-365-information-protection-and-compliance-capabilities"></a>Microsoft 365 funktioner til beskyttelse af oplysninger og overholdelse af regler og standarder

Microsoft 365 omfatter et bredt sæt funktioner til beskyttelse af oplysninger og overholdelse af regler og standarder. Sammen med Microsofts produktivitetsværktøjer er disse funktioner designet til at hjælpe organisationer med at samarbejde i realtid og samtidig overholde strenge lovgivningsmæssige rammer for overholdelse. 

Dette sæt illustrationer bruger en af de fleste regulerede brancher, finansielle tjenester, til at demonstrere, hvordan disse funktioner kan anvendes til at løse almindelige lovmæssige krav. Du er velkommen til at tilpasse disse illustrationer til eget brug. 


| Element | Beskrivelse |
|:-----|:-----|
|[![Modelplakat: Microsoft 365 funktioner til beskyttelse af oplysninger og overholdelse af regler og standarder.](../media/solutions-architecture-center/m365-compliance-illustrations-thumb.png)](https://download.microsoft.com/download/3/a/6/3a6ab1a3-feb0-4ee2-8e77-62415a772e53/m365-compliance-illustrations.pdf) <br/> Engelsk: [Download som PDF-download](https://download.microsoft.com/download/3/a/6/3a6ab1a3-feb0-4ee2-8e77-62415a772e53/m365-compliance-illustrations.pdf)\| [som Visio](https://download.microsoft.com/download/3/a/6/3a6ab1a3-feb0-4ee2-8e77-62415a772e53/m365-compliance-illustrations.vsdx)   <br/> Japansk: [Download som PDF-download](https://download.microsoft.com/download/6/f/1/6f1a7d0e-dd8e-442e-b073-8e94327ae4f8/m365-compliance-illustrations.pdf)\| [som Visio](https://download.microsoft.com/download/6/f/1/6f1a7d0e-dd8e-442e-b073-8e94327ae4f8/m365-compliance-illustrations.vsdx)   <br/> Opdateret i november 2020|Omfatter: <ul><li>  Microsoft-beskyttelse af oplysninger og forebyggelse af datatab</li><li>Opbevaringspolitikker og opbevaringsnavne </li><li>Informationsbarrierer</li><li>Kommunikationsoverholdelse</li><li>Insider-risiko</li><li>Tredjepartsdataindtrindelse</li>|

## <a name="conference-sessions"></a>Mødesessioner

Se disse mødesessioner for at få mere at vide om styring Microsoft 365 grupper og Teams.

**Grundlæggende oplysninger**

Lær de grundlæggende og nye innovationer i Microsoft 365 Groups, herunder administration og styring på skala, bedste fremgangsmåder til at fremme brug og indføring og selvbetjening.

- [Forskellige Microsoft 365 grupper](https://www.youtube.com/watch?v=dAamBF1gb7M)

**Styring**

Få mere at vide om, hvordan du konfigurerer udløbsdato for dine grupper, navngivningspolitikker, klassificeringsetiketter, samarbejde med eksterne gæster og administrerer tilladelser til oprettelse af grupper.

- [Transformér samarbejde, og udskyd skygger fra it Office 365 grupper](https://www.youtube.com/watch?v=Bhf_bKx3lAg)

**Kundeeksememem**

Se et eksempel i baggrunden på, hvordan Microsoft 365 grupper, SharePoint, Teams og Yammer arbejder sammen om at levere en global samarbejdsplatform.

- [Find dit samarbejde på det helt eget sted Office 365 grupper, SharePoint, Teams og Yammer](https://www.youtube.com/watch?v=Rx9eVwqXeQk)

## <a name="see-also"></a>Se også

[Microsoft 365 sikkerhedsdokumentation](../security/index.yml)

[Microsoft 365 om overholdelse af regler og standarder](../compliance/index.yml)