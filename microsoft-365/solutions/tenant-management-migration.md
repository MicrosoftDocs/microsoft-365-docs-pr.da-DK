---
title: Trin 4. Overførsel for dine Microsoft 365 for virksomhedslejere
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
- m365solution-tenantmanagement
- tenant-management
- m365solution-scenario
ms.custom:
- Ent_Solutions
description: Overfør Windows enheder, Office klientapps og Office servere til dine Microsoft 365 lejere.
ms.openlocfilehash: 1892ae3da900f1c940866a2b2a3c70c1d6cb5db3
ms.sourcegitcommit: 22cae7ec541268d519d45518c32f22bf5811aec1
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/10/2022
ms.locfileid: "63589875"
---
# <a name="step-4-migration-for-your-microsoft-365-for-enterprise-tenants"></a>Trin 4. Overførsel for dine Microsoft 365 for virksomhedslejere

De fleste virksomhedsorganisationer har et hetergene miljø, der indeholder flere versioner af operativsystemer, klientsoftware og serversoftware. Microsoft 365 til virksomheder indeholder de mest sikre versioner af de vigtigste komponenter i din it-infrastruktur. Den indeholder også produktivitetsfunktioner, der er udviklet til at drage fordel af skyteknologier.

For at maksimere forretningsværdien af Microsoft 365 for virksomhedsintegrerede produktpakker skal du begynde at planlægge og implementere en strategi for at overføre disse versioner:

| Fra | Hvis du vil |
|:-------|:-----|
| Windows 7 og Windows 8.1 | Windows 10 Enterprise |
| Office klientprodukter, der er installeret på din medarbejders enheder | Microsoft 365 Apps for enterprise |
| Office serverprodukter, der er installeret på lokale servere | Deres tilsvarende skybaserede tjenester i Microsoft 365 |
|  |  |

## <a name="migrating-to-windows-10"></a>Overførsel til Windows 10

Hver Microsoft 365 for Enterprise-licens omfatter en licens til Windows 10 Enterprise. Hvis du vil overføre dine enheder, Windows 7 eller Windows 8.1, kan du udføre en direkte opgradering. Support sluttede for Windows 7 *den 14. januar 2020*. 

Du kan finde flere metoder Windows 10 Enterprise installation end en opgradering på stedet under [Windows 10 med installation](/windows/deployment/windows-10-deployment-scenarios). Du kan også [planlægge Windows 10 din](/windows/deployment/planning/) egen installation.

## <a name="migrating-to-microsoft-365-apps-for-enterprise"></a>Overførsel til Microsoft 365 Apps for enterprise

Microsoft 365 til virksomheder omfatter Microsoft 365 Apps for enterprise, en version af Office-klientprodukterne (Word, PowerPoint, Excel og Outlook), der er installeret og opdateret fra Microsoft-skyen. Du kan finde flere oplysninger [under Om Microsoft 365 Apps for enterprise](/deployoffice/about-microsoft-365-apps).

I stedet for at holde dine computere opdateret Office 2019 eller ældre versioner, skal du gøre følgende:

1. Hent og tildel Microsoft 365 licens til dine brugere.
2. Fjern Office 2013 eller Office 2016 på computeren.
3. Installér Microsoft 365 Apps for enterprise, enten individuelt eller under en it-udrulning. Du kan finde flere oplysninger [i Installationsvejledning til Microsoft 365 Apps](/deployoffice/deployment-guide-microsoft-365-apps).

Microsoft 365 Apps for enterprise installerer automatisk både sikkerhedsopdateringer og nye funktionsopdateringer og kan drage fordel af skybaserede tjenester i Microsoft 365 for øget sikkerhed og produktivitet.

## <a name="migrating-on-premises-servers-and-data-to-microsoft-365"></a>Overførsel af lokale servere og data til Microsoft 365

Microsoft 365 til virksomheder omfatter skybaserede versioner af Office-servertjenester, der bruger nogle af de samme værktøjer som lokale versioner af Office-serversoftware, f.eks. webbrowsere og Outlook-klienten. Disse skybaserede tjenester opdateres automatisk med henblik på sikkerhed og nye funktioner. Efter overførslen kan din it-afdeling spare tid, det tager at vedligeholde og opdatere lokale servere.

Brug følgende ressourcer til oplysninger om overførsel af brugere og data for bestemte Microsoft 365 arbejdsbelastninger:

- [Flyt postkasser fra lokale Exchange Server til Exchange Online](/exchange/hybrid-deployment/move-mailboxes)
- [Overfør SharePoint data fra SharePoint Server til SharePoint Online](/sharepointmigration/migrate-to-sharepoint-online)
- [Overfør Skype for Business Online til Microsoft Teams](/microsoftteams/migration-interop-guidance-for-teams-with-skype)

## <a name="transition-your-entire-organization"></a>Overgå hele organisationen

Hent denne overgangsplakat for at få et bedre billede af, hvordan du flytter hele organisationen til produkterne og tjenesterne i Microsoft 365 til virksomheder:

[![Billede, der viser overgang til Microsoft 365 plakat.](../media/microsoft-365-overview/transition-org-to-m365.png)](https://download.microsoft.com/download/2/c/7/2c7bcc04-aae3-4604-9707-1ffff66b9851/transition-org-to-m365.pdf)

Denne tosidede plakat er en hurtig måde til at lagerfortegne din eksisterende infrastruktur. Brug den til at få vejledning i at flytte til et produkt eller en tjeneste Microsoft 365 til virksomheder. Den viser Windows og Office og andre infrastruktur- og sikkerhedselementer som administration af enheder, identitet og trusselsbeskyttelse samt beskyttelse af oplysninger og overholdelse af regler og standarder.

## <a name="results-of-step-4"></a>Resultater af trin 4

For overførsel for din Microsoft 365 lejer har du fastlagt:

- Hvilke enheder der kører Windows 7 eller Windows 8.1, og planen er at opdatere dem til Windows 10 Enterprise.
- Hvilke enheder, der kører Office-klientapps, og planen er at opdatere dem til Microsoft 365-apps til virksomheder.
- Hvilke lokale Office skal overføres til deres tilsvarende Microsoft 365 planen om at overføre dem og deres data.

Her er et eksempel på en lejer med en færdiggjort overførsel af lokale servere.

![Eksempel på en lejer med en fuldført overførsel af lokale servere.](../media/tenant-management-overview/tenant-management-tenant-build-step4.png)

I denne illustration har organisationen:

- Dens lokale postkasser blev Exchange Server til Exchange Online.
- Overflyttede dens lokale SharePoint serverwebsteder og data SharePoint i Microsoft 365.

## <a name="ongoing-maintenance-for-migration"></a>Løbende vedligeholdelse til overførsel

Du kan løbende få brug for at:

- Afhængigt af tilstanden for din Exchange skal du fortsætte med at rulle overgangen Exchange Online ud til din organisation.
- Afhængigt af tilstanden for din lokale SharePoint for webstedsoverflytningen skal du fortsætte med at rulle overgangen SharePoint at Microsoft 365 ud til din organisation.

## <a name="next-step"></a>Næste trin

[![Trin 5. Installér enheds- og appadministration.](../media/tenant-management-overview/tenant-management-step-grid-device-mgmt.png)](tenant-management-device-management.md)

Fortsæt med [enheds- og appadministration for](tenant-management-device-management.md) at installere enheds- og appadministration.