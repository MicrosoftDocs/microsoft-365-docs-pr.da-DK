---
title: Konfigurer sikker fil- og dokumentdeling og samarbejde med Teams i Microsoft 365
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-collaboration
- m365solution-securecollab
- m365solution-overview
ms.custom:
- M365solutions
- seo-marvel-jun2020
f1.keywords: NOCSH
recommendations: false
description: Få mere at vide om de bedste fremgangsmåder til at konfigurere sikkert filsamarbejde og -deling Teams at beskytte dine data baseret på deres følsomhed.
ms.openlocfilehash: db1ad7d6d5c62775c696da89c3d771114d48e67e
ms.sourcegitcommit: 46456ca009c9d50622e57e24269be74986184654
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/22/2022
ms.locfileid: "63714947"
---
# <a name="set-up-secure-file-sharing-and-collaboration-with-microsoft-teams"></a>Konfigurer sikker fildeling og samarbejde med Microsoft Teams

At kunne nemt dele filer og dokumenter med de rette personer og samtidig forhindre overdeling er afgørende for en organisations succes. Dette omfatter at kunne dele fortrolige eller andre følsomme data sikkert med kun dem, der skal have adgang til den. Afhængigt af projektet kan dette omfatte deling af følsomme data med personer uden for organisationen.

Denne vejledning til samarbejdsløsning omfatter to komponenter, der kan hjælpe dig:

- Installér Teams det rette beskyttelsesniveau for hvert projekt
- Konfigurer ekstern deling med relevante sikkerhedsindstillinger for hvert projekt

![Installér Teams med passende beskyttelse, og konfigurer ekstern deling med relevante sikkerhedsindstillinger.](..\media\solutions-architecture-center\secure-collaboration-overview.png)

Hvis der ikke er alsidige og brugervenlige filsamarbejdeværktøjer tilgængelige, samarbejder brugerne ofte ved at sende dokumenter via mail. Dette er en kedelig og fejlbetonet metode til samarbejde, og det kan øge risikoen for upassende deling af oplysninger. Hvis folk synes, at det er for svært at dele filer, kan de gå tilbage til at bruge forbrugerprodukter, der ikke er underlagt it. Dette kan udgøre en endnu større risiko.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWxMmL?autoplay=false]

Med Microsoft 365 kan du installere Teams en række forskellige konfigurationer, der hjælper:

- Beskyt din immaterielle ejendom
- Gør det nemt at samarbejde med dokumenter og andre filer
- Opret en balance mellem sikkerhed og brugbarhed, som øger brugertilfredsheden og reducerer risikoen for skygge it

De fleste organisationer har en række forskellige oplysninger med forskellige følsomhedsgrader og forskellige forretningsmæssige indvirkninger, hvis oplysningerne deles upassende. Afhængigt af følsomheden af en given oplysning kan du tillade deling med:

- Alle (ikke godkendt)
- Personer i organisationen
- Bestemte personer i organisationen
- Bestemte personer i og uden for organisationen

Oplysninger som marketingbrochurer er beregnet til at blive delt bredt uden for organisationen. Oplysninger som f.eks. genvejsmenuer er ikke beregnet til ekstern deling, men vil ikke have nogen betydning for virksomheden, hvis de blev delt eksternt. Disse typer oplysninger kræver kun lidt eller slet ingen beskyttelse.

De samme marketingbrochurer, mens de er under udvikling, kan kun deles inden for organisationen. I dette tilfælde kan standardindstillingerne for deling Teams være tilstrækkelige.

Oplysninger om et nyt produkt, der er under udvikling, kan betragtes som følsomme , selv inden for organisationen. I dette tilfælde kan det være hensigtsmæssigt med en større grad af beskyttelse. Du kan f.eks. begrænse adgangen til disse oplysninger til medlemmer af et bestemt team. Afhængigt af projektet kan det være nødvendigt at samarbejde med personer uden for organisationen, f.eks. en leverandør eller en partnerorganisation.

Oplysninger, der er vigtige for organisationens succes, eller som har strenge sikkerheds- eller overholdelseskrav, kan kræve endnu flere beskyttelsesniveauer.

![Risikoskala fra lav (udgivet brochure) til høj (følsomme forretningsdata).](../media/solutions-architecture-center/SecureCollaboration-SensitivityAndBusinessImpactofSharing-fromVisio.png)

For alle de scenarier, der er nævnt ovenfor, kan du bruge teams Microsoft Teams at gemme, dele og samarbejde om oplysningerne.

For at konfigurere sikkert samarbejde skal du bruge Microsoft 365 funktioner.

|Produkt eller komponent|Funktionalitet eller funktion|Licensering|
|---|---|---|
|Microsoft Defender til Office 365|Pengeskab vedhæftede filer til SPO, OneDrive og Teams; Pengeskab Dokumenter; Pengeskab Links til Teams|Microsoft 365 E1, E3 og E5|
|SharePoint|Politikker for websteds- og fildeling, tilladelser for webstedsdeling, delingslinks, anmodninger om adgang, indstillinger for gæstedeling på webstedet|Microsoft 365 E1, E3 og E5|
|Microsoft Teams|Gæsteadgang, private teams, private kanaler, delte kanaler|Microsoft 365 E1, E3 og E5|
|Microsoft 365 overholdelse af regler og standarder|Følsomhedsmærkater|Microsoft 365 E3 og E5|

## <a name="collaboration-governance-framework-for-teams-and-microsoft-365"></a>Samarbejdsstyringsrammer for Teams og Microsoft 365

Microsoft 365 indeholder mange muligheder for at styre din samarbejdsløsning. Vi anbefaler, at du bruger dette installationsindhold sammen med [indholdet til styring af samarbejde](collaboration-governance-overview.md) for at skabe den bedste samarbejdsløsning for organisationen.

### <a name="securing-teams-for-sensitive-and-highly-sensitive-data"></a>Beskyttelse Teams følsomme og meget følsomme data

For at administrere adgang til oplysninger med forskellige følsomheder har vi udviklet [tre forskellige niveauer af beskyttelse til Teams](configure-teams-three-tiers-protection.md). Du kan tilpasse et hvilket som helst af disse niveau for bedre at imødekomme behovene eller for din virksomhed.

![Grafik med tre niveauer af beskyttelse til Teams.](../media/solutions-architecture-center/Teams-tiers-of-protection-1.png)

Disse niveauer – grundlinje *, følsom* og meget *følsom – øger* gradvist beskyttelserne, der hjælper med at forhindre overdeling og potentiel lækage af oplysninger, som vist i følgende tabel. 

|-|Niveau for oprindelig plan|Følsomt niveau|Meget følsomt niveau|
|---|---|---|---|
|Offentligt eller privat team|Enten|Privat|Privat|
|Ikke-godkendt deling|Blokeret|Blokeret|Blokeret|
|Fildeling|Tilladt|Tilladt|Kun teamejere kan dele.|
|Teammedlemskab|Alle kan deltage i offentlige teams.<br>Teamejergodkendelse kræves for at deltage i private teams.|Godkendelse af teamejer kræves for at deltage.|Godkendelse af teamejer kræves for at deltage.|
|Dokumentkryptering|||Tilgængelig med følsomhedsmærkat|
|Gæstedeling|Tilladt|Kan tillades eller blokeres|Kan tillades eller blokeres|
|Ikke-administrerede enheder|Ingen begrænsning|Adgang kun til internettet|Blokeret|

Konfiguration af disse niveauer indebærer:

- Konfiguration af indstillinger i Teams for gæsteadgang og private kanaler
- Konfiguration af indstillinger i et teams tilknyttede SharePoint for intern deling og gæstedeling, anmodninger om adgang og deling af links
- For de *følsomme* og *meget følsomme* niveauer, konfigurering af følsomhedsmærkater til at klassificere teams, og kontrollere gæstedeling og adgang fra ikke-administrerede enheder
- For det *meget følsomme* niveau kan du konfigurere en følsomhedsmærkat til at kryptere de dokumenter, den er anvendt på

Start med det oprindelige niveau, og tilføj derefter teams, der bruger  de følsomme  og meget følsomme niveauer efter behov for at beskytte oplysningerne i organisationen. Se disse ressourcer for at komme i gang:

- [Konfigurer teams med beskyttelse mod grundlinjer](configure-teams-baseline-protection.md)
- [Konfigurer teams med beskyttelse af følsomme data](configure-teams-sensitive-protection.md)
- [Konfigurer teams med beskyttelse til meget følsomme data](configure-teams-highly-sensitive-protection.md)

Hvis du har et meget følsomt projekt, der kræver yderligere beskyttelse mod deling, selv inden for din organisation, kan du konfigurere et team, der bruger sin egen følsomhedsmærkat til at kryptere filer, så kun teammedlemmer kan læse dem. Se [Konfigurere et team med sikkerhedsisolation](secure-teams-security-isolation.md) for at få flere oplysninger.

### <a name="sharing-with-people-outside-your-organization"></a>Dele med personer uden for organisationen

Det kan være nødvendigt [at dele oplysninger om følsomhed med personer uden for organisationen](collaborate-with-people-outside-your-organization.md). Dette kan variere fra at dele et enkelt dokument med en enkelt person til at samarbejde om et større projekt med en stor partnerorganisation eller partnere fra hele verden. I Microsoft 365 kan denne række af ekstern deling nemt gøres med de relevante sikkerhedsforanstaltninger for at beskytte dine følsomme oplysninger.

Disse ressourcer kan hjælpe dig med at komme i gang med at konfigurere dit miljø til samarbejde med personer uden for organisationen:

- [Samarbejd om dokumenter](collaborate-on-documents.md) til deling af individuelle filer i mapper.
- [Samarbejd på et websted](collaborate-in-site.md) om at samarbejde med gæster på et SharePoint websted.
- [Samarbejd som et team](collaborate-as-team.md) om at samarbejde med gæster i et team.
- [Samarbejd med eksterne deltagere i en kanal](/microsoft-365/solutions/collaborate-teams-direct-connect) for at samarbejde med personer uden for organisationen i en delt kanal.

Afhængigt af følsomheden af de oplysninger, der deles, kan du tilføje sikkerhedsforanstaltninger for at forhindre overdeling. Disse ressourcer kan hjælpe dig med at konfigurere de beskyttelser, du har brug for i din organisation:

- [Bedste fremgangsmåder for deling af filer og mapper med ikke-godkendte brugere](best-practices-anonymous-sharing.md)
- [Begræns utilsigtet eksponering af filer ved deling med personer uden for organisationen](share-limit-accidental-exposure.md)
- [Opret et sikkert miljø for gæstedeling](create-secure-guest-sharing-environment.md)

Hvis du har et større projekt med en partnerorganisation, kan du bruge enten [](/microsoft-365/solutions/collaborate-teams-direct-connect) delte kanaler eller [administration af Azure-rettighed](b2b-extranet.md) til at administrere de personer uden for organisationen, som du skal samarbejde med.

## <a name="training-for-administrators"></a>Kurser til administratorer

Disse kursusmoduler fra Microsoft Learn kan hjælpe dig med at lære funktionerne samarbejde, styring og identitet i Teams og SharePoint.

### <a name="teams"></a>Teams

|Kursus:|Administrer teamsamarbejde med Microsoft Teams|
|---|---|
|![Teams ikon for samarbejdskursus.](../media/manage-team-collaboration-with-microsoft-teams.svg)|Administrer teamsamarbejde med Microsoft Teams introducerer dig for funktionerne og egenskaberne i Microsoft Teams, som er den centrale hub for teamsamarbejde Microsoft 365. Du lærer, hvordan du kan bruge Teams til at lette teamwork og kommunikation i din organisation, både lokalt og lokalt, på en lang række enheder – fra stationære computere til tablets til telefoner – og samtidig drage fordel af alle de omfattende funktioner i Office 365-programmer. Du får en forståelse af, hvordan Teams giver et omfattende og fleksibelt miljø til samarbejde på tværs af programmer og enheder. Denne læringssti kan hjælpe dig med at forberede dig til Microsoft 365 certificeret: Teams administratorpartnercertificering.<p>2 timer 17 min - Learning Sti - 5 moduler|

> [!div class="nextstepaction"]
> [Start >](/learn/modules/m365-teams-collab-prepare-deployment/introduction/)

### <a name="sharepoint"></a>SharePoint

|Kursus:|Samarbejd med SharePoint i Microsoft 365|
|---|---|
|![SharePoint kursusikon.](../media/collaborate-with-sharepoint-in-microsoft-365.svg)|Administrer delt indhold med Microsoft SharePoint introducerer dig for funktionerne og egenskaberne i SharePoint, og hvordan det fungerer med Microsoft 365. Du kan få mere at vide om de forskellige SharePoint websteder, herunder hubwebsteder samt beskyttelse af oplysninger, rapportering og overvågning. Du lærer også, hvordan du bruger SharePoint-fil- og mappedeling til at optimere samarbejde, hvordan du deler filer eksternt, og hvordan du administrerer SharePoint-websteder i SharePoint Administration. Denne læringssti kan hjælpe dig med at forberede dig til Microsoft 365 certificeret: Teamadministrator associate-certificering.<p>1 time 14 min - Learning Sti - 4 moduler|

> [!div class="nextstepaction"]
> [Start >](/learn/modules/m365-teams-sharepoint-plan-sharepoint/introduction/)

### <a name="information-protection"></a>Beskyttelse af oplysninger

|Kursus:|Beskyt virksomhedsoplysninger med Microsoft 365|
|---|---|
|![Teams for uddannelse i beskyttelse af oplysninger.](../media/protect-enterprise-information-microsoft-365.svg)|At beskytte og sikre din organisations oplysninger er mere udfordrende end nogensinde før. I læringsstien Beskyt virksomhedsoplysninger med Microsoft 365 beskrives det, hvordan du beskytter dine følsomme oplysninger mod utilsigtet overdeling eller misbrug, hvordan du finder og klassificerer data, hvordan du beskytter dem med følsomhedsmærkater, og hvordan du både overvåger og analyserer dine følsomme oplysninger for at beskytte dig mod tab. Denne læringssti kan hjælpe dig med at forberede dig til Microsoft 365 certificeret: Security Administrator Associate og Microsoft 365 Certified: Enterprise Administration Expert-certificeringer.<p>1 timer - Learning Sti - 5 moduler|

> [!div class="nextstepaction"]
> [Start >](/learn/modules/m365-security-info-overview/introduction/)

### <a name="identity-and-access"></a>Identitet og adgang

|Kursus:|Beskyt identitet og adgang med Azure Active Directory|
|---|---|
|![Ikonet Identitets- og adgangskursus.](../media/protect-identity-and-access-with-microsoft-365.svg)|Identitets- og Access-læringsstien dækker de nyeste identitets- og adgangsteknologier, værktøjer til godkendelse med henblik på godkendelse og vejledning til identitetsbeskyttelse inden for organisationen. Microsofts adgangs- og identitetsteknologier giver dig mulighed for at sikre din organisations identitet, uanset om den er lokal eller i skyen, og give dine brugere mulighed for at arbejde sikkert fra et hvilket som helst sted. Denne læringssti kan hjælpe dig med at forberede dig til Microsoft 365 certificeret: Security Administrator Associate og Microsoft 365 Certified: Enterprise Administration Expert-certificeringer.<p>2 timer 52 min - Learning Sti - 6 moduler|

> [!div class="nextstepaction"]
> [Start >](/learn/modules/m365-identity-overview/introduction/)

## <a name="training-for-end-users"></a>Kurser til slutbrugere

Disse kursusmoduler kan hjælpe brugerne med at bruge Teams, grupper og SharePoint til samarbejde Microsoft 365.

|Teams|SharePoint|
|---|---|
|![Konfigurer og tilpas dit teams kursusikon.](../media/set-up-customize-team-training.png)<br>**[Konfigurere og tilpasse dit team](https://support.microsoft.com/office/702a2977-e662-4038-bef5-bdf8ee47b17b)**|![SharePoint delings- og synkroniseringskursusikon](../media/sharepoint-share-sync-training.png)<br>**[Del og synkroniser](https://support.microsoft.com/office/98cb2ff2-c27e-42ea-b055-c2d895f8a5de)**|
|![Teams til at overføre og finde filer.](../media/smc-teams-upload-find-files-training.png)<br>**[Upload og find filer](https://support.microsoft.com/office/57b669db-678e-424e-b0a0-15d19215cb12)**||
|![Ikonet Samarbejd i teams og kanaler.](../media/teams-collaborate-channels-training.png)<br>**[Samarbejd i teams og kanaler](https://support.microsoft.com/office/c3d63c10-77d5-4204-a566-53ddcf723b46)**||

## <a name="illustrations"></a>Illustrationer

Disse illustrationer hjælper dig med at forstå, hvordan grupper og teams interagerer med andre tjenester i Microsoft 365 og hvilke funktioner til styring og overholdelse, der er tilgængelige til at hjælpe dig med at administrere disse tjenester i organisationen.

### <a name="groups-in-microsoft-365-for-it-architects"></a>Grupper i Microsoft 365 til IT-arkitekter

Hvad it-arkitekter har brug for at vide om grupper i Microsoft 365

|**Element**|**Beskrivelse**|
|---|---|
|[![Miniaturebillede til gruppe infografik.](../downloads/msft-m365-groups-architecture-thumb.png)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/msft-m365-groups.pdf) <br/> [PDF](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/msft-m365-groups.pdf) \| [Visio](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/msft-m365-groups.vsdx) <br> Opdateret juni 2019|Disse illustrationer beskriver de forskellige typer grupper, hvordan de oprettes og administreres, og nogle få anbefalinger om styring.|

### <a name="microsoft-teams-and-related-productivity-services-in-microsoft-365-for-it-architects"></a>Microsoft Teams og relaterede produktivitetstjenester i Microsoft 365 til IT-arkitekter

Den logiske arkitektur for produktivitetstjenester i Microsoft 365, der har Microsoft Teams.

|**Element**|**Beskrivelse**|
|---|---|
|[![Miniaturebillede til Teams logisk arkitekturplakat.](../downloads/msft-teams-logical-architecture-thumb.png)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/msft-m365-teams-logical-architecture.pdf) <br/> [PDF](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/msft-m365-teams-logical-architecture.pdf) \| [Visio](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/msft-m365-teams-logical-architecture.vsdx)  <br>Opdateret april 2019|Microsoft leverer en pakke med produktivitetstjenester, der arbejder sammen for at give samarbejdsoplevelser med datastyring, sikkerhed og overholdelse af regler og standarder. <p>Denne serie af illustrationer giver et indblik i den logiske arkitektur i produktivitetstjenester for virksomhedsarkitekter, der er førende med Microsoft Teams.|

## <a name="deploy-the-secure-collaboration-solution"></a>Installér løsningen sikkert samarbejde

Når du er klar til at implementere denne løsning, skal du fortsætte med disse trin:

1. Konfigurer de [tre forskellige niveauer af beskyttelse til Teams](configure-teams-three-tiers-protection.md).
2. Konfigurer indstillinger for [deling af oplysninger om følsomhed med personer uden for organisationen](collaborate-with-people-outside-your-organization.md).

## <a name="see-also"></a>Se også

[Microsoft 365 sikkerhedsdokumentation](../security/index.yml)

[Microsoft 365 om overholdelse af regler og standarder](../compliance/index.yml)

[Velkommen til Microsoft Teams](/MicrosoftTeams/Teams-overview)
