---
title: Microsoft Teams
description: Sådan Teams installeres på enheder og opdateres bagefter
keywords: Microsoft Managed Desktop, Microsoft 365, service, dokumentation, apps, line of business-apps, LOB-apps
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
audience: ITPro
ms.openlocfilehash: 469edf3e8ae856ea6e94bada8ffb9d6c97ba8b66
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/04/2022
ms.locfileid: "64634465"
---
# <a name="microsoft-teams"></a>Microsoft Teams

[Teams](https://www.microsoft.com/microsoft-365/microsoft-teams/group-chat-software) er en [besked-app](https://support.microsoft.com/office/microsoft-teams-basics-6d5f52e6-5306-4096-ac24-c3082b79eaf0), der også giver et arbejdsområde til samarbejde og kommunikation i realtid, møder og fil- og appdeling.

## <a name="initial-deployment"></a>Indledende installation

De fleste hardwareleverandører har endnu ikke inkluderet Teams som en del af deres billeder. Microsoft Managed Desktop installerer Teams på dine enheder ved hjælp af Microsoft Intune. Alle administrerede enheder har [Teams .msi-pakken](/MicrosoftTeams/msi-deployment#how-the-microsoft-teams-msi-package-works) installeret. Pakken .msi sikrer, at alle brugere, der logger på en enhed, Microsoft Teams klar til brug. Når pakken først er færdig med at installere, Teams automatisk og tilføjer en genvej til skrivebordet.

### <a name="microsoft-intune-changes"></a>Microsoft Intune ændringer

Microsoft Managed Desktop føjer Microsoft Teams til din lejer: Moderne arbejdsplads – Teams Machine Wide Installer x64  

## <a name="updates"></a>Opdateringer

Teams følger en separat opdateringssti Microsoft 365 Apps for enterprise. Computerklienten opdateres automatisk. Teams søger efter opdateringer med få timer, downloader dem og venter derefter på, at computeren er inaktiv, før du installerer opdateringen automatisk.  

Den Teams-produktgruppe tillader ikke, at administratorer kan kontrollere opdateringer, så Microsoft Managed Desktop den [almindelige kanal for automatiske opdateringer](/microsoftteams/teams-client-update#can-admins-deploy-updates-instead-of-teams-auto-updating).

### <a name="manually-updating-teams"></a>Manuel opdatering af Teams

Individuelle brugere kan også hente opdateringer. Vælg Søg efter opdateringer på rullelisten Profil øverst **til højre i appen**. Hvis der findes en opdatering, downloades og installeres den automatisk, når computeren er inaktiv.

## <a name="delivery-optimization-of-updates"></a>Leveringsoptimering af opdateringer

Leveringsoptimering for Teams opdateringer er som standard slået til og kræver ingen handling fra administratorer eller brugere.
