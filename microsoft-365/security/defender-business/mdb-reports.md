---
title: Rapporter i Microsoft Defender til virksomheder
description: Få et overblik over sikkerhedsrapporter i Defender for Business. Rapporter viser registrerede trusler, beskeder, sikkerhedsrisici og enhedsstatus.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 21a8bcca2e0b4bfb58e1209810bb35a7c25cdc2d
ms.sourcegitcommit: fa90763559239c4c46c5e848939126763879d8e4
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/13/2022
ms.locfileid: "66772855"
---
# <a name="reports-in-microsoft-defender-for-business"></a>Rapporter i Microsoft Defender til virksomheder

Der findes flere rapporter på Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)). I denne artikel beskrives disse rapporter, hvordan du kan bruge dem, og hvordan du finder dem.

## <a name="reports-in-defender-for-business"></a>Rapporter i Defender for Business

|Rapport  |Beskrivelse  |
|---------|---------|
| **Sikkerhedsrapport**  | Sikkerhedsrapporten indeholder oplysninger om din virksomheds identiteter, enheder og apps. Hvis du vil have adgang til denne rapport, skal du vælge **Rapporter** > **Generel** > **sikkerhed-rapport** i navigationsruden. <br/><br/>**TIP** Du kan få vist lignende oplysninger på startsiden på Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)). |
| **Trusselsbeskyttelse**  | Rapporten om trusselsbeskyttelse indeholder oplysninger om tendenser for beskeder og beskeder. Brug kolonnen **Tendenser for beskeder** til at få vist oplysninger om beskeder, der er udløst i løbet af de sidste 30 dage. Brug kolonnen **Status for besked** til at få vist aktuelle snapshotoplysninger om beskeder, f.eks. kategorier af uløste beskeder og deres klassificering. Hvis du vil have adgang til denne rapport, skal du vælge **Rapporter** > **Endpoints** > **Threat Protection** i navigationsruden. <br/><br/>**Tip**: Du kan også bruge listen **Hændelser** til at få vist oplysninger om beskeder. I navigationsruden skal du vælge **Hændelser** for at få vist og administrere aktuelle hændelser. Du kan få mere at vide under [Få vist og administrer hændelser i Defender for Business](mdb-view-manage-incidents.md). |
| **Enhedens tilstand og overholdelse af angivne standarder** | Rapporten over enhedens tilstand og overholdelse af angivne standarder indeholder oplysninger om enhedens tilstand og tendenser. Du kan bruge denne rapport til at afgøre, om Defender for Business-sensorer fungerer korrekt på enheder og den aktuelle status for Microsoft Defender Antivirus. Hvis du vil have adgang til denne rapport, skal du i navigationsruden vælge **Rapporter** > **Slutpunkter Enhedens** > **tilstand og overholdelse af angivne standarder**. <br/><br/>**TIP**! Du kan bruge **enhedsoversigten** til at få vist oplysninger om virksomhedens enheder. Vælg **Enhedslager** i navigationsruden. Du kan få mere at vide [under Administrer enheder i Defender for Business](mdb-manage-devices.md). |
| **Sårbare enheder** | Rapporten over sårbare enheder indeholder oplysninger om enheder og tendenser. Brug kolonnen **Tendenser** til at få vist oplysninger om enheder, der havde beskeder i løbet af de sidste 30 dage. Brug kolonnen **Status** til at få vist aktuelle snapshotoplysninger om enheder, der har beskeder. Hvis du vil have adgang til denne rapport, skal du vælge **Rapporter** > **Slutpunkter** > **Sårbare enheder** i navigationsruden.<br/><br/>**TIP**! Du kan bruge **enhedsoversigten** til at få vist oplysninger om virksomhedens enheder. Vælg **Enhedslager** i navigationsruden. Du kan få mere at vide [under Administrer enheder i Defender for Business](mdb-manage-devices.md). |
| **Webbeskyttelse** | Rapporten om webbeskyttelse viser forsøg på at få adgang til phishing-websteder, malwarevektorer, udnyttelseswebsteder, websteder, der ikke er tillid til, eller websteder med lavt omdømme og websteder, der udtrykkeligt er blokeret. Kategorier af blokerede websteder omfatter indhold til voksne, fritidswebsteder, websteder med juridisk ansvar m.m. Hvis du vil have adgang til denne rapport, skal du vælge **Rapporter** > **Slutpunkter** > **Webbeskyttelse** i navigationsruden.<br/><br/>Hvis du endnu ikke har konfigureret webbeskyttelse for din virksomhed, skal du vælge knappen **Indstillinger** i en rapportvisning. Vælg derefter **filtrering af webindhold** under **Regler**. Du kan få mere at vide om filtrering af webindhold under [Filtrering af webindhold](../defender-endpoint/web-content-filtering.md). |
| **Firewall** | Firewallrapporten viser blokerede indgående, udgående og appforbindelser. I denne rapport vises også fjern-IP'er, der er tilsluttet af flere enheder, og fjern-IP'er med de fleste forsøg på at oprette forbindelse. <br/><br/>Hvis du endnu ikke har konfigureret firewallbeskyttelsen, skal du vælge **Slutpunkter** > **Konfigurationsstyring** > **Enhedskonfiguration** i navigationsruden. Du kan få mere at vide [under Firewall i Defender for Business](mdb-firewall.md). |
| **Enhedsstyring** | Rapporten over enhedskontrol viser oplysninger om medieforbrug, f.eks. brugen af flytbare lagerenheder i din organisation. |


## <a name="see-also"></a>Se også

- [Kom i gang med at bruge Defender for Business](mdb-get-started.md)
- [Få vist og administrer hændelser i Defender for Business](mdb-view-manage-incidents.md)
- [Administrer enheder i Defender for Business](mdb-manage-devices.md)
