---
title: Oversigt over Microsoft 365 grupper til administratorer
ms.reviewer: arvaradh
f1.keywords: NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
- admindeeplinkMAC
search.appverid:
- BCS160
- MET150
- MOE150
description: Med Microsoft 365 grupper kan du fremme teamwork på tværs Microsoft 365 at give en gruppe personer adgang til en samling af delte ressourcer.
ms.openlocfilehash: 5aaf7598f3591efb330618f0be98ea3376816eca
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63599701"
---
# <a name="overview-of-microsoft-365-groups-for-administrators"></a>Oversigt over Microsoft 365 grupper til administratorer

Microsoft 365 Groups er den grundlæggende medlemskabstjeneste, der driver alt teamwork på tværs Microsoft 365. Med Microsoft 365 grupper kan du give en gruppe personer adgang til en samling af delte ressourcer. Disse ressourcer omfatter:

- En delt Outlook indbakke
- En delt kalender
- Et SharePoint dokumentbibliotek
- En Planner
- En OneNote notesbog
- Power BI
- Yammer (hvis gruppen blev oprettet ud fra Yammer)
- Et team (hvis gruppen blev oprettet ud fra Teams)
- Roadmap (hvis du har Project til internettet)
- Stream

Med en Microsoft 365 gruppe behøver du ikke at tildele tilladelser til hver af disse ressourcer manuelt. Når du føjer personer til gruppen, får de automatisk de nødvendige tilladelser.

Alle brugere kan oprette en gruppe, medmindre [du begrænser oprettelse af grupper til et bestemt sæt personer](../../solutions/manage-creation-of-groups.md). Hvis du begrænser oprettelse af grupper, vil brugere, der ikke kan oprette grupper, ikke kunne oprette SharePoint-websteder, planners, teams, Outlook-gruppekalendere, Stream-grupper, Yammer-grupper, Delte biblioteker i OneDrive eller delte Power BI-arbejdsområder. Disse tjenester kræver, at de personer, der opretter dem, skal kunne oprette en gruppe. Brugere kan stadig deltage i gruppeaktiviteter, f.eks. oprette opgaver i Planner eller bruge Teams chat, hvis de er medlem af gruppen.

Grupper har følgende roller:

- **Ejere** – Gruppeejere kan tilføje eller fjerne medlemmer og have separate tilladelser som f.eks. muligheden for at slette samtaler fra den delte indbakke eller ændre de forskellige indstillinger for gruppen. Gruppeejere kan omdøbe gruppen, opdatere beskrivelsen eller billedet og meget mere.
- **Medlemmer** – Medlemmer kan få adgang til alt i gruppen, men kan ikke ændre indstillingerne for gruppen. Som standard kan gruppemedlemmer invitere gæster til at deltage i din gruppe, men du kan [styre denne indstilling](manage-guest-access-in-groups.md).
- **Gæster** – gruppe gæster er medlemmer, der er uden for organisationen.

Kun globale administratorer, brugeradministratorer og gruppeadministratorer kan oprette og administrere grupper i <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">Microsoft 365 Administration</a>. Du kan ikke være delegeret administrator (f.eks. en konsulent, der er administrator på vegne af en anden).

Som administrator kan du:

- [Angive, hvem der kan oprette grupper](../../solutions/manage-creation-of-groups.md)
- [Opret en navngivningspolitik for grupper i organisationen](../../solutions/groups-naming-policy.md)
- [Vælg, hvilket domæne du vil bruge, når du opretter en gruppe](../../solutions/choose-domain-to-create-groups.md)
- [Administrer gæsteadgang til grupper](manage-guest-access-in-groups.md)
- [Gendan en slettet gruppe](restore-deleted-group.md) (inden for 30 dage efter sletningen)

Hvis du foretrækker en mere automatiseret metode til at administrere livscyklussen for dine Microsoft 365-grupper, kan du bruge udløbspolitikker til at udløbe grupper på et bestemt tidsinterval. Gruppens ejere får en mail 30, 15 og 1 dag før gruppens udløbsdato, der giver dem mulighed for at forny gruppen, hvis det stadig er nødvendigt. Se: [Microsoft 365 gruppes udløbspolitik](../../solutions/microsoft-365-groups-expiration-policy.md).

Du kan administrere dine grupper fra Microsoft 365 Administration ved [hjælp af PowerShell](../../enterprise/manage-microsoft-365-groups-with-powershell.md).

Hvis du har mange brugere, f.eks. i en stor virksomhed eller virksomhed, kan der være mange brugere, der opretter grupper til forskellige formål. Vi anbefaler, at du gennemgår [Plan for styring i Microsoft 365 for bedste](../../solutions/collaboration-governance-overview.md) praksis.

## <a name="group-limits"></a>Begrænsninger for gruppe

Følgende begrænsninger gælder for Microsoft 365 grupper:

|Maksimum...|Værdi|
|:---------|:----|
|Ejere pr. gruppe|100|
|Grupper, som en bruger kan oprette|250|
|Grupper, som en administrator kan oprette|Op til standardgrænsen for lejere på 500 K|
|Antal medlemmer|Mere end 1.000, men kun 1.000 kan få adgang til gruppesamtaler samtidigt. <br>Brugere vil muligvis opleve forsinkelser ved åbning af kalenderen og samtaler i store grupper Outlook.|
|Antal grupper, en bruger kan være medlem af|7,000|
|Fillager|1 terabyte + 10 GB pr. bruger med abonnement + ethvert andet købt lager. Du kan købe en ubegrænset mængde ekstra lagerplads.|
|Størrelse på gruppepostkasse|50 GB|

Det maksimale standardtal for Microsoft 365, som en organisation kan have, er 500.000. Hvis du vil gå ud over standardgrænsen, skal du kontakte Microsoft Support. Du kan finde flere Microsoft 365 om begrænsninger for grupper under [Microsoft 365 Grupper – Hjælp til administratorer](https://support.microsoft.com/office/b565caa1-5c40-40ef-9915-60fdb2d97fa2).

Administration af Microsoft 365 grupper er mere effektivt, når du har brugbare oplysninger om brugen af grupper. Gruppen Microsoft 365 Administration har et rapporteringsværktøj, hvor du kan se lagerbrug, hvor mange aktive grupper du har, og hvordan brugerne bruger grupperne. Se: [Microsoft 365 Rapporter i Administration for at få](../activity-reports/office-365-groups.md) flere oplysninger.

## <a name="sensitivity-labels"></a>Følsomhedsmærkater

Du kan oprette følsomhedsmærkater, som brugerne i organisationen kan angive, når de opretter en Microsoft 365 gruppe. Med følsomhedsmærkater kan du konfigurere: 

- Beskyttelse af personlige oplysninger (offentlig eller privat)
- Adgang for eksterne brugere
- Ikke-administreret enhedsadgang

Du kan f.eks. oprette en etiket  kaldet Meget fortrolig og angive, at en gruppe, der er oprettet med denne etiket, vil være privat og ikke tillade eksterne brugere. Når brugerne i organisationen vælger dette navn ved oprettelse af grupper, angives gruppen til private, og gruppemedlemmer vil ikke have tilladelse til at føje eksterne brugere til gruppen.

> [!IMPORTANT]
> Hvis du aktuelt bruger klassificeringsmærkater, vil de ikke længere være tilgængelige for brugere, der opretter grupper, når følsomhedsmærkater er aktiveret. 

Du kan finde oplysninger om oprettelse, administration og brug af følsomhedsmærkater under Brug følsomhedsmærkater til at beskytte indhold [Microsoft Teams, Microsoft 365 grupper og SharePoint websteder](../../compliance/sensitivity-labels-teams-groups-sites.md).

## <a name="which-microsoft-365-plans-include-groups"></a>Hvilke Microsoft 365 omfatter grupper?

Alle Microsoft 365-abonnementer, der Exchange Online og SharePoint Online, understøtter grupper. Det omfatter Business Essentials- og Business Premium-planerne og Enterprise E1-, E3- og E5-planerne. Gruppen overtager licensering for den person, der opretter gruppen (også kaldet "arrangøren" for gruppen). Så længe arrangøren har den korrekte licens til de funktioner, du ønsker, at gruppen skal have, vil denne licens formidle til gruppen.

> [!NOTE]
> Du kan finde flere Microsoft 365 om tjenestefamilier og -planer [i Microsoft 365 i Planindstillinger](/office365/servicedescriptions/office-365-platform-service-description/office-365-plan-options).

Hvis du har en plan, der kun er Exchange, kan du stadig få adgang til den delte indbakke og de delte kalenderfunktioner i grupper i Outlook men du får ikke dokumentbiblioteket, Planner eller nogen af de andre funktioner.

Microsoft 365 kan arbejde med Azure Active Directory. De gruppefunktioner, du får, afhænger af, Azure Active Directory du har, og hvilke licenser der er tildelt til arrangøren af gruppen.

> [!IMPORTANT]
> For alle gruppefunktionerne kan brugere, hvis du har et Azure AD Premium-abonnement, deltage i gruppen, uanset om de har fået tildelt AAD P1-licens. Licensering gennemtvinges ikke.
> Med jævne mellemrum genererer vi brugsrapporter, der fortæller dig, hvilke brugere der mangler en licens, og som skal have en tildelt for at overholde licenskravene. Lad os f.eks. sige, at en bruger ikke har en licens, og at han/hun er føjet til en gruppe, hvor navngivningspolitikken håndhæves. Rapporten markerer for dig, at de skal bruge en licens.

## <a name="related-content"></a>Relateret indhold

[Få mere at Microsoft 365 om grupper](https://support.microsoft.com/office/b565caa1-5c40-40ef-9915-60fdb2d97fa2) (artikel)\
[Opgrader distributionslister Microsoft 365 Grupper](../manage/upgrade-distribution-lists.md) (artikel)\
[Administrer Microsoft 365 grupper med PowerShell](../../enterprise/manage-microsoft-365-groups-with-powershell.md) (artikel)\
[SharePoint Onlinegrænser](/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-limits) (artikel)\
[Organiser grupper og kanaler i Microsoft Stream](/stream/groups-channels-organization) (artikel)
