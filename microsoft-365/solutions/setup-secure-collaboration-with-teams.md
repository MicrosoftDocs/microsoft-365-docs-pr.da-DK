---
title: Konfigurer sikker fil- og dokumentdeling og -samarbejde med Teams i Microsoft 365
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
description: Få mere at vide om bedste praksis for konfiguration af sikkert filsamarbejde og -deling i Teams for at beskytte dine data baseret på dataenes følsomhed.
ms.openlocfilehash: 54bfe4bce20687474526916fe7b11ca0e5bb1b72
ms.sourcegitcommit: 5c64002236561000c5bd63c71423e8099e803c2d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/09/2022
ms.locfileid: "65286532"
---
# <a name="set-up-secure-file-sharing-and-collaboration-with-microsoft-teams"></a>Konfigurer sikker fildeling og samarbejde med Microsoft Teams

Det er vigtigt for en organisations succes, at du nemt kan dele filer og dokumenter med de rette personer, samtidig med at du forhindrer overdeling. Dette omfatter kun at kunne dele fortrolige eller andre følsomme data sikkert med dem, der skal have adgang til dem. Afhængigt af projektet kan dette omfatte deling af følsomme data med personer uden for din organisation.

Denne vejledning til samarbejdsløsning indeholder to komponenter, der kan hjælpe dig:

- Udrul Teams med det rette beskyttelsesniveau for hvert projekt
- Konfigurer ekstern deling med de relevante sikkerhedsindstillinger for hvert projekt

![Udrul Teams med passende beskyttelse, og konfigurer ekstern deling med de relevante sikkerhedsindstillinger.](..\media\solutions-architecture-center\secure-collaboration-overview.png)

Hvis alsidige og brugervenlige værktøjer til filsamarbejde ikke er tilgængelige, samarbejder brugerne ofte ved at sende dokumenter via mail. Dette er en kedelig og fejlbehæftet metode til samarbejde, og det kan øge risikoen for upassende deling af oplysninger. Hvis det er for svært at dele filer, kan de vende tilbage til at bruge forbrugerprodukter, der ikke er underlagt it-regler. Dette kan udgøre en endnu større risiko.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWxMmL?autoplay=false]

Med Microsoft 365 kan du udrulle Teams med en række konfigurationer, der hjælper:

- Beskyt dine immaterielle rettigheder
- Gør det nemt at samarbejde med dokumenter og andre filer
- Opret en balance mellem sikkerhed og anvendelighed, der øger brugertilfredsheden og reducerer risikoen for skygge-it

De fleste organisationer har en række oplysninger med forskellige grader af følsomhed og varierende grader af forretningsindvirkning, hvis oplysningerne deles på en forkert måde. Afhængigt af følsomheden af en given oplysning kan det være en god idé at tillade deling med:

- Alle (ikke-godkendte)
- Personer i organisationen
- Bestemte personer i organisationen
- Bestemte personer i og uden for organisationen

Oplysninger som marketingbrochure er beregnet til at blive delt bredt uden for organisationen. Oplysninger som cafeteriamenuer er ikke beregnet til ekstern deling, men har ingen forretningsmæssig indvirkning, hvis de deles eksternt. Disse typer oplysninger kræver kun lidt eller ingen beskyttelse.

De samme markedsføring brochurer, mens under udvikling, kan kun deles i organisationen. I dette tilfælde kan standardindstillingerne for deling i Teams være tilstrækkelige.

Oplysninger om et nyt produkt, der er under udvikling, kan betragtes som følsomme, selv i organisationen. En større grad af beskyttelse kan være passende i dette tilfælde. Du kan f.eks. begrænse adgangen til disse oplysninger til medlemmer af et bestemt team. Afhængigt af projektet skal du muligvis samarbejde med personer uden for din organisation, f.eks. en leverandør eller partnerorganisation.

Oplysninger, der er vigtige for din organisations succes, eller som har strenge krav til sikkerhed eller overholdelse af angivne standarder, kan kræve endnu større beskyttelsesniveauer.

![Risikoskala fra lav (udgivet brochure) til høj (følsomme forretningsdata).](../media/solutions-architecture-center/SecureCollaboration-SensitivityAndBusinessImpactofSharing-fromVisio.png)

I alle de scenarier, der er nævnt ovenfor, kan du bruge teams i Microsoft Teams til at gemme, dele og samarbejde om oplysningerne.

Hvis du vil konfigurere sikkert samarbejde, skal du bruge disse Microsoft 365 funktioner.

|Produkt eller komponent|Funktionalitet eller funktion|Licensering|
|---|---|---|
|Microsoft Defender for Office 365|Pengeskab vedhæftede filer til SPO, OneDrive og Teams; Pengeskab dokumenter; Pengeskab links til Teams|Microsoft 365 E1, E3 og E5|
|SharePoint|Politikker for deling af websteder og filer, Tilladelser til deling af websted, Delingslinks, Adgangsanmodninger, Indstillinger for gæstedeling af websted|Microsoft 365 E1, E3 og E5|
|Microsoft Teams|Gæsteadgang, private teams, private kanaler, delte kanaler|Microsoft 365 E1, E3 og E5|
|Microsoft Purview|Følsomhedsmærkater|Microsoft 365 E3 og E5|

## <a name="collaboration-governance-framework-for-teams-and-microsoft-365"></a>Samarbejdsstyringsrammer for Teams og Microsoft 365

Microsoft 365 giver dig mange muligheder for at styre din samarbejdsløsning. Vi anbefaler, at du bruger dette udrulningsindhold sammen med [samarbejdsstyringsindholdet](collaboration-governance-overview.md) for at oprette den bedste samarbejdsløsning for din organisation.

### <a name="securing-teams-for-sensitive-and-highly-sensitive-data"></a>Sikring af Teams til følsomme og meget følsomme data

For at administrere adgang til oplysninger med forskellige følsomheder har vi udviklet [tre forskellige beskyttelsesniveauer for Teams](configure-teams-three-tiers-protection.md). Du kan tilpasse et af disse niveauer for bedre at imødekomme behovene eller din virksomhed.

![Grafik af tre beskyttelsesniveauer for Teams.](../media/solutions-architecture-center/Teams-tiers-of-protection-1.png)

Disse niveauer – *baseline*, *følsomme* og *meget følsomme* – øger gradvist beskyttelsen, der hjælper med at forhindre overdeling og potentiel informationsfejl, som vist i følgende tabel.

|-|Oprindelig plan|Følsomt niveau|Meget følsomt niveau|
|---|---|---|---|
|Offentligt eller privat team|Enten|Privat|Privat|
|Ikke-godkendt deling|Blokeret|Blokeret|Blokeret|
|Fildeling|Tilladt|Tilladt|Det er kun teamejere, der kan dele.|
|Teammedlemskab|Alle kan deltage i offentlige teams.<br>Godkendelse af teamejer kræves for at deltage i private teams.|Godkendelse af teamejer kræves for at deltage.|Godkendelse af teamejer kræves for at deltage.|
|Dokumentkryptering|||Tilgængelig med følsomhedsmærkat|
|Gæstedeling|Tilladt|Kan tillades eller blokeres|Kan tillades eller blokeres|
|Ikke-administrerede enheder|Ingen begrænsninger|Kun webadgang|Blokeret|

Konfiguration af disse niveauer omfatter:

- Konfiguration af indstillinger i Teams for gæsteadgang og private kanaler
- Konfiguration af indstillinger på et teams tilknyttede SharePoint websted til intern deling og gæstedeling, adgangsanmodninger og delingslinks
- For de *følsomme* og *meget følsomme* niveauer skal du konfigurere følsomhedsmærkater for at klassificere teams og styre gæstedeling og -adgang fra ikke-administrerede enheder
- For det *meget følsomme* niveau skal du konfigurere en følsomhedsmærkat for at kryptere de dokumenter, som det er anvendt på

Start med det oprindelige niveau, og tilføj derefter teams, der bruger de *følsomme* og *meget følsomme* niveauer efter behov for at beskytte oplysningerne i din organisation. Se disse ressourcer for at komme i gang:

- [Konfigurer teams med grundlæggende beskyttelse](configure-teams-baseline-protection.md)
- [Konfigurer teams med beskyttelse af følsomme data](configure-teams-sensitive-protection.md)
- [Konfigurer teams med beskyttelse af meget følsomme data](configure-teams-highly-sensitive-protection.md)

Hvis du har et meget følsomt projekt, der kræver yderligere beskyttelse mod deling, selv i din organisation, kan du konfigurere et team, der bruger sin egen følsomhedsmærkat til at kryptere filer, så det kun er gruppemedlemmer, der kan læse dem. Se [Konfigurer et team med sikkerhedsisolation](secure-teams-security-isolation.md) for at få flere oplysninger.

### <a name="sharing-with-people-outside-your-organization"></a>Deling med personer uden for din organisation

Du skal muligvis [dele oplysninger om enhver følsomhed med personer uden for din organisation](collaborate-with-people-outside-your-organization.md). Dette kan variere fra deling af et enkelt dokument med en enkelt person til samarbejde om et større projekt med en stor partnerorganisation eller freelancere fra hele verden. I Microsoft 365 kan denne række eksterne delinger nemt og med de relevante sikkerhedsforanstaltninger hjælpe med at beskytte dine følsomme oplysninger.

Disse ressourcer hjælper dig med at komme i gang med at konfigurere dit miljø til samarbejde med personer uden for organisationen:

- [Samarbejd om dokumenter](collaborate-on-documents.md) for at dele individuelle filer med mapper.
- [Samarbejd på et websted](collaborate-in-site.md) for at samarbejde med gæster på et SharePoint websted.
- [Samarbejd som et team](collaborate-as-team.md) for at samarbejde med gæster i et team.
- [Samarbejd med eksterne deltagere i en kanal](/microsoft-365/solutions/collaborate-teams-direct-connect) for at samarbejde med personer uden for organisationen i en delt kanal.

Afhængigt af følsomheden af de oplysninger, der deles, kan du tilføje sikkerhedsforanstaltninger for at forhindre overdeling. Disse ressourcer hjælper dig med at konfigurere den beskyttelse, du har brug for til din organisation:

- [Bedste praksis for deling af filer og mapper med ikke-godkendte brugere](best-practices-anonymous-sharing.md)
- [Begræns utilsigtet eksponering af filer, når der deles med personer uden for din organisation](share-limit-accidental-exposure.md)
- [Opret et sikkert gæstedelingsmiljø](create-secure-guest-sharing-environment.md)

Hvis du har et større projekt med en partnerorganisation, kan du bruge enten [delte kanaler](/microsoft-365/solutions/collaborate-teams-direct-connect) eller [Azure Entitlement Management](b2b-extranet.md) til at administrere de personer uden for din organisation, som du har brug for at samarbejde med.

## <a name="training-for-administrators"></a>Oplæring af administratorer

Disse træningsmoduler fra Microsoft Learn kan hjælpe dig med at lære funktionerne til samarbejde, styring og identitet at kende i Teams og SharePoint.

### <a name="teams"></a>Teams

|Uddannelse:|Administrer teamsamarbejde med Microsoft Teams|
|---|---|
|![Teams ikonet for samarbejdstræning.](../media/manage-team-collaboration-with-microsoft-teams.svg)|Administrer teamsamarbejde med Microsoft Teams introducerer dig til funktionerne og egenskaberne i Microsoft Teams, som er den centrale hub til teamsamarbejde i Microsoft 365. Du lærer, hvordan du kan bruge Teams til at facilitere teamwork og kommunikation i din organisation, både til og fra det lokale miljø, på en lang række enheder – fra stationære computere til tablets til telefoner – samtidig med at du drager fordel af alle de omfattende funktioner i Office 365 programmer. Du får en forståelse af, hvordan Teams giver et omfattende og fleksibelt miljø til samarbejde på tværs af programmer og enheder. Dette læringsforløb kan hjælpe dig med at forberede dig på certificeringen Microsoft 365 Certificeret: Teams Administrator Associate.<p>2 t. 17 min. - Learning sti - 5 moduler|

> [!div class="nextstepaction"]
> [Start >](/learn/modules/m365-teams-collab-prepare-deployment/introduction/)

### <a name="sharepoint"></a>SharePoint

|Uddannelse:|Samarbejd med SharePoint i Microsoft 365|
|---|---|
|![SharePoint træningsikon.](../media/collaborate-with-sharepoint-in-microsoft-365.svg)|Administrer delt indhold med Microsoft SharePoint introducerer dig til funktionerne og egenskaberne i SharePoint, og hvordan det fungerer med Microsoft 365. Du får mere at vide om de forskellige typer SharePoint websteder, herunder hubwebsteder, samt information beskyttelse, rapportering og overvågning. Du får også mere at vide om, hvordan du bruger SharePoint fil- og mappedeling til at optimere samarbejde, hvordan du deler filer eksternt, og hvordan du administrerer SharePoint websteder i SharePoint Administration. Dette læringsforløb kan hjælpe dig med at forberede dig på certificeringen Microsoft 365 Certificeret: Teamwork Administrator Associate.<p>1 t. 14 min. - Learning sti - 4 moduler|

> [!div class="nextstepaction"]
> [Start >](/learn/modules/m365-teams-sharepoint-plan-sharepoint/introduction/)

### <a name="information-protection"></a>Beskyttelse af oplysninger

|Uddannelse:|Beskyt virksomhedsoplysninger med Microsoft 365|
|---|---|
|![Teams træningsikon for infobeskyttelse.](../media/protect-enterprise-information-microsoft-365.svg)|Det er mere udfordrende end nogensinde før at beskytte og beskytte din organisations oplysninger. Læringsforløbet Beskyt virksomhedsoplysninger med Microsoft 365 beskriver, hvordan du beskytter dine følsomme oplysninger mod utilsigtet overdeling eller misbrug, hvordan du finder og klassificerer data, hvordan du beskytter dem med følsomhedsmærkater, og hvordan du både overvåger og analyserer dine følsomme oplysninger for at beskytte mod tab. Dette læringsforløb kan hjælpe dig med at forberede dig på Microsoft 365 Certificeret: Sikkerhedsadministratormedarbejder og Microsoft 365 Certificeret: Certificeringer fra virksomhedsadministrationseksperter.<p>1 t. – Learning sti – 5 moduler|

> [!div class="nextstepaction"]
> [Start >](/learn/modules/m365-security-info-overview/introduction/)

### <a name="identity-and-access"></a>Identitet og adgang

|Uddannelse:|Beskyt identitet og adgang med Azure Active Directory|
|---|---|
|![Ikon for oplæring af identitet og adgang.](../media/protect-identity-and-access-with-microsoft-365.svg)|Læringsforløbet Identitet og adgang dækker de nyeste identitets- og adgangsteknologier, værktøjer til styrkelse af godkendelse og vejledning om identitetsbeskyttelse i din organisation. Microsofts adgangs- og identitetsteknologier gør det muligt for dig at sikre din organisations identitet, uanset om det er i det lokale miljø eller i cloudmiljøet, og gøre det muligt for dine brugere at arbejde sikkert fra enhver placering. Dette læringsforløb kan hjælpe dig med at forberede dig på Microsoft 365 Certificeret: Sikkerhedsadministratormedarbejder og Microsoft 365 Certificeret: Certificeringer fra virksomhedsadministrationseksperter.<p>2 t. 52 min. - Learning sti - 6 moduler|

> [!div class="nextstepaction"]
> [Start >](/learn/modules/m365-identity-overview/introduction/)

## <a name="training-for-end-users"></a>Oplæring af slutbrugere

Disse træningsmoduler kan hjælpe dine brugere med at bruge Teams, grupper og SharePoint til samarbejde i Microsoft 365.

|Teams|SharePoint|
|---|---|
|![Konfigurer og tilpas ikonet for teamtræning.](../media/set-up-customize-team-training.png)<br>**[Konfigurer og tilpas dit team](https://support.microsoft.com/office/702a2977-e662-4038-bef5-bdf8ee47b17b)**|![SharePoint delings- og synkroniseringsikon](../media/sharepoint-share-sync-training.png)<br>**[Del og synkroniser](https://support.microsoft.com/office/98cb2ff2-c27e-42ea-b055-c2d895f8a5de)**|
|![Teams ikonet for oplæring af filer, og find dem.](../media/smc-teams-upload-find-files-training.png)<br>**[Upload og søg efter filer](https://support.microsoft.com/office/57b669db-678e-424e-b0a0-15d19215cb12)**||
|![Ikonet Samarbejd i teams og kanaler.](../media/teams-collaborate-channels-training.png)<br>**[Samarbejd i teams og kanaler](https://support.microsoft.com/office/c3d63c10-77d5-4204-a566-53ddcf723b46)**||

## <a name="illustrations"></a>Illustrationer

Disse illustrationer hjælper dig med at forstå, hvordan grupper og teams interagerer med andre tjenester i Microsoft 365, og hvilke funktioner til styring og overholdelse af angivne standarder der er tilgængelige, som kan hjælpe dig med at administrere disse tjenester i din organisation.

### <a name="groups-in-microsoft-365-for-it-architects"></a>Grupper i Microsoft 365 for it-arkitekter

Det har it-arkitekter brug for at vide om grupper i Microsoft 365

|**Element**|**Beskrivelse**|
|---|---|
|[![Miniaturebillede for gruppers infografik.](../downloads/msft-m365-groups-architecture-thumb.png)](https://download.microsoft.com/download/6/3/0/6309218f-a169-4f2d-af4c-2fe49e30ba17/msft-m365-groups.pdf) <br/> [PDF](https://download.microsoft.com/download/6/3/0/6309218f-a169-4f2d-af4c-2fe49e30ba17/msft-m365-groups.pdf) \| [Visio](https://download.microsoft.com/download/6/3/0/6309218f-a169-4f2d-af4c-2fe49e30ba17/msft-m365-groups.vsdx) <br> Opdateret i maj 2022|Disse illustrationer beskriver de forskellige typer af grupper, hvordan de oprettes og administreres, og nogle få anbefalinger til styring.|

### <a name="microsoft-teams-and-related-productivity-services-in-microsoft-365-for-it-architects"></a>Microsoft Teams og relaterede produktivitetstjenester i Microsoft 365 for it-arkitekter

Den logiske arkitektur af produktivitetstjenester i Microsoft 365, der fører med Microsoft Teams.

|**Element**|**Beskrivelse**|
|---|---|
|[![Thumb image for Teams logisk arkitektur plakat.](../downloads/msft-teams-logical-architecture-thumb.png)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/msft-m365-teams-logical-architecture.pdf) <br/> [PDF](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/msft-m365-teams-logical-architecture.pdf) \| [Visio](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/msft-m365-teams-logical-architecture.vsdx)  <br>Opdateret i april 2019|Microsoft leverer en pakke med produktivitetstjenester, der arbejder sammen om at levere samarbejdsoplevelser med datastyring, sikkerhed og funktionalitet til overholdelse af angivne standarder. <p>Denne serie illustrationer giver et overblik over den logiske arkitektur af produktivitetstjenester for virksomhedsarkitekter, der fører an i Microsoft Teams.|

## <a name="deploy-the-secure-collaboration-solution"></a>Udrul den sikre samarbejdsløsning

Når du er klar til at installere denne løsning, skal du fortsætte med disse trin:

1. Konfigurer de [tre forskellige beskyttelsesniveauer for Teams](configure-teams-three-tiers-protection.md).
2. Konfigurer indstillinger for [deling af oplysninger om følsomhed med personer uden for din organisation](collaborate-with-people-outside-your-organization.md).

## <a name="see-also"></a>Se også

[Microsoft 365 sikkerhedsdokumentation](../security/index.yml)

[Dokumentation til Microsoft Purview](../compliance/index.yml)

[Velkommen til Microsoft Teams](/MicrosoftTeams/Teams-overview)
