---
title: Fejlfinding af AzCopy i Advanced eDiscovery
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
description: Fejlfinding af fejl i Azure AzCopy ved indlæsning af ikke-Office 365 for fejl afhjælpning i Advanced eDiscovery.
ms.custom:
- seo-marvel-mar2020
- seo-marvel-apr2020
ms.openlocfilehash: 45f82482f92e740383eca774671f1abd55535675
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63587721"
---
# <a name="troubleshoot-azcopy-in-advanced-ediscovery"></a>Fejlfinding af AzCopy i Advanced eDiscovery

Når du indlæser ikke-Microsoft 365-data eller -dokumenter for at afhjælpe fejlen i Advanced eDiscovery, leverer brugergrænsefladen en Azure AzCopy-kommando, der indeholder parametre med placeringen af, hvor de filer, du vil overføre, er gemt, og den Azure-lagerplacering, som filerne skal uploades til. Hvis du vil overføre dine dokumenter, skal du kopiere denne kommando og derefter køre den i en kommandoprompt på din lokale computer.  Det følgende skærmbillede viser et eksempel på en AzCopy-kommando:

![Upload ikke-Microsoft 365-filer.](../media/46ba68f6-af11-4e70-bb91-5fc7973516e3.png)

Som regel fungerer den angivne kommando, når du kører den. Der kan dog være tilfælde, hvor den kommando, der vises, ikke kører korrekt. Her er et par mulige årsager.

## <a name="the-supported-version-of-azcopy-isnt-installed-on-the-local-computer"></a>Den understøttede version af AzCopy er ikke installeret på den lokale computer

På nuværende tidspunkt skal du bruge AzCopy v8.1 til at indlæse ikke-Microsoft 365 data Advanced eDiscovery. Kommandoen AzCopy, der vises på siden **Upload-filer**, der vises i det forrige skærmbillede, returnerer en fejl, hvis du ikke bruger AzCopy v8.1. Hvis du vil installere denne version, [skal du se Overfør data med AzCopy v8.1 Windows](/previous-versions/azure/storage/storage-use-azcopy).

## <a name="azcopy-isnt-installed-on-the-local-computer-or-its-not-installed-in-the-default-location"></a>AzCopy er ikke installeret på den lokale computer, eller den er ikke installeret på standardplaceringen

Hvis AzCopy ikke er installeret, eller den er installeret på en anden placering end standardplaceringen for installationen ( `%ProgramFiles(x86)%`som er ), modtager du muligvis følgende fejlmeddelelse, når du kører kommandoen AzCopy:

> Systemet kan ikke finde den angivne sti.

Hvis AzCopy ikke er installeret på den lokale computer, kan du finde installationsoplysninger i [Overfør data med AzCopy v8.1 på Windows](/previous-versions/azure/storage/storage-use-azcopy). Sørg for at installere den på standardplaceringen.

Hvis AzCopy er installeret, men det er installeret på en anden placering end standardplaceringen, kan du kopiere kommandoen, indsætte den i en tekstfil og derefter ændre stien til den placering, hvor AzCopy er installeret. Hvis Azcopy f.eks. er placeret i `%ProgramFiles%`, kan du ændre den første del af kommandoen fra `%ProgramFiles(x86)%\Microsoft SDKs\Azure\AzCopy.exe` til `%ProgramFiles%\Microsoft SDKs\Azure\AzCopy`. Når du har ændret denne ændring, skal du kopiere den fra tekstfilen og derefter køre den med en kommandoprompt.

> [!TIP]
> Hvis AzCopy er installeret på en anden placering end standardplaceringen, bør du overveje at fjerne den og derefter geninstallere den på standardplaceringen. Dette er med til at forhindre dette problem i fremtiden.