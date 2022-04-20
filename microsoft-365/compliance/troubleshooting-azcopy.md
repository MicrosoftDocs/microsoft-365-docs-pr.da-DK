---
title: Foretag fejlfinding af AzCopy i eDiscovery (Premium)
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: troubleshooting
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Foretag fejlfinding af fejl i Azure AzCopy ved indlæsning af data, der ikke er Office 365, for fejlafhjælpning i eDiscovery (Premium).
ms.custom:
- seo-marvel-mar2020
- seo-marvel-apr2020
ms.openlocfilehash: ff8f69e6efeab3e0f0e9d8ee2f739caaa40d7c85
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/20/2022
ms.locfileid: "64991792"
---
# <a name="troubleshoot-azcopy-in-ediscovery-premium"></a>Foretag fejlfinding af AzCopy i eDiscovery (Premium)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Når du indlæser ikke-Microsoft 365 data eller dokumenter til fejlafhjælpning i Microsoft Purview eDiscovery (Premium), leverer brugergrænsefladen en Azure AzCopy-kommando, der indeholder parametre med placeringen af, hvor de filer, du vil overføre, gemmes, og den Azure Storage-placering, som filerne overføres til. Hvis du vil overføre dine dokumenter, skal du kopiere denne kommando og derefter køre den i en kommandoprompt på din lokale computer.  På følgende skærmbillede vises et eksempel på en AzCopy-kommando:

![Overfør filer, der ikke er Microsoft 365.](../media/46ba68f6-af11-4e70-bb91-5fc7973516e3.png)

Normalt fungerer den kommando, der er angivet, når du kører den. Der kan dog være tilfælde, hvor den viste kommando ikke kan køres korrekt. Her er nogle mulige årsager.

## <a name="the-supported-version-of-azcopy-isnt-installed-on-the-local-computer"></a>Den understøttede version af AzCopy er ikke installeret på den lokale computer

På nuværende tidspunkt skal du bruge AzCopy v8.1 til at indlæse ikke-Microsoft 365 data i eDiscovery (Premium). Kommandoen AzCopy, der vises på siden **Overfør filer** , som vises på det forrige skærmbillede, returnerer en fejl, hvis du ikke bruger AzCopy v8.1. Hvis du vil installere denne version, skal du se [Overfør data med AzCopy v8.1 på Windows](/previous-versions/azure/storage/storage-use-azcopy).

## <a name="azcopy-isnt-installed-on-the-local-computer-or-its-not-installed-in-the-default-location"></a>AzCopy er ikke installeret på den lokale computer, eller den er ikke installeret på standardplaceringen

Hvis AzCopy ikke er installeret, eller den er installeret på en anden placering end standardinstallationsplaceringen (dvs `%ProgramFiles(x86)%`. ), får du muligvis vist følgende fejl, når du kører kommandoen AzCopy:

> Systemet kan ikke finde den angivne sti.

Hvis AzCopy ikke er installeret på den lokale computer, kan du finde installationsoplysninger i [Overfør data med AzCopy v8.1 på Windows](/previous-versions/azure/storage/storage-use-azcopy). Sørg for at installere den på standardplaceringen.

Hvis AzCopy er installeret, men den er installeret på en anden placering end standardplaceringen, kan du kopiere kommandoen, indsætte den i en tekstfil og derefter ændre stien til den placering, hvor AzCopy er installeret. Hvis Azcopy f.eks. er placeret i `%ProgramFiles%`, kan du ændre den første del af kommandoen fra `%ProgramFiles(x86)%\Microsoft SDKs\Azure\AzCopy.exe` til `%ProgramFiles%\Microsoft SDKs\Azure\AzCopy`. Når du har foretaget denne ændring, skal du kopiere den fra tekstfilen og derefter køre den en kommandoprompt.

> [!TIP]
> Hvis AzCopy er installeret et andet sted end standardinstallationsplaceringen, kan du overveje at fjerne den og derefter geninstallere den på standardplaceringen. Dette vil hjælpe med at forhindre dette problem i fremtiden.