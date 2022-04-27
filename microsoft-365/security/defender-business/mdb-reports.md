---
title: Rapporter i Microsoft Defender til virksomheder
description: Få et overblik over de rapporter, der er tilgængelige i Microsoft Defender til virksomheder
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 04/14/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 5b3a21a45e1b9e90cf5a8a7f666861502205552e
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093256"
---
# <a name="reports-in-microsoft-defender-for-business"></a>Rapporter i Microsoft Defender til virksomheder

> [!NOTE]
> Microsoft Defender til virksomheder er nu inkluderet i [Microsoft 365 Business Premium](../../business-premium/index.md). 

Der findes flere rapporter på Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)). I denne artikel beskrives disse rapporter, hvordan du kan bruge dem, og hvordan du finder dem.

## <a name="reports-in-defender-for-business"></a>Rapporter i Defender for Business

|Rapport  |Beskrivelse  |
|---------|---------|
| **Sikkerhedsrapport**  | Sikkerhedsrapporten indeholder oplysninger om din virksomheds identiteter, enheder og apps. Hvis du vil have adgang til denne rapport, skal du vælge **RapporterGenereltSikkerhedsrapport** >  >  i navigationsruden. <br/><br/>**TIP** Du kan få vist lignende oplysninger på startsiden på Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)). |
| **Trusselsbeskyttelse**  | Rapporten om trusselsbeskyttelse indeholder oplysninger om tendenser for beskeder og beskeder. Brug kolonnen **Tendenser for beskeder** til at få vist oplysninger om beskeder, der er udløst i løbet af de sidste 30 dage. Brug kolonnen **Status for besked** til at få vist aktuelle snapshotoplysninger om beskeder, f.eks. kategorier af uløste beskeder og deres klassificering. Hvis du vil have adgang til denne rapport, skal du vælge **ReportsEndpointsThreat** >  >  **Protection** i navigationsruden. <br/><br/>**Tip**: Du kan også bruge listen **Hændelser** til at få vist oplysninger om beskeder. I navigationsruden skal du vælge **Hændelser** for at få vist og administrere aktuelle hændelser. Du kan få mere at vide under [Få vist og administrer hændelser i Microsoft Defender til virksomheder](mdb-view-manage-incidents.md). |
| **Enhedens tilstand og overholdelse af angivne standarder** | Rapporten over enhedens tilstand og overholdelse af angivne standarder indeholder oplysninger om enhedens tilstand og tendenser. Du kan bruge denne rapport til at afgøre, om Defender for Business-sensorer fungerer korrekt på enheder og den aktuelle status for Microsoft Defender Antivirus. Hvis du vil have adgang til denne rapport, skal du vælge **ReportsEndpointsDevice** >  >  **health and compliance** i navigationsruden. <br/><br/>**TIP**! Du kan bruge **enhedsoversigten** til at få vist oplysninger om virksomhedens enheder. Vælg **Enhedslager** i navigationsruden. Du kan få mere at vide under [Administrer enheder i Microsoft Defender til virksomheder](mdb-manage-devices.md). |
| **Sårbare enheder** | Rapporten over sårbare enheder indeholder oplysninger om enheder og tendenser. Brug kolonnen **Tendenser** til at få vist oplysninger om enheder, der havde beskeder i løbet af de sidste 30 dage. Brug kolonnen **Status** til at få vist aktuelle snapshotoplysninger om enheder, der har beskeder. Hvis du vil have adgang til denne rapport, skal du vælge **ReportsEndpointsVulnerable** >  >  **enheder** i navigationsruden.<br/><br/>**TIP**! Du kan bruge **enhedsoversigten** til at få vist oplysninger om virksomhedens enheder. Vælg **Enhedslager** i navigationsruden. Du kan få mere at vide under [Administrer enheder i Microsoft Defender til virksomheder](mdb-manage-devices.md). |
| **Webbeskyttelse** | Rapporten om webbeskyttelse viser forsøg på at få adgang til phishing-websteder, malwarevektorer, udnyttelseswebsteder, websteder, der ikke er tillid til, eller websteder med lavt omdømme og websteder, der udtrykkeligt er blokeret. Kategorier af blokerede websteder omfatter indhold til voksne, fritidswebsteder, websteder med juridisk ansvar m.m. Hvis du vil have adgang til denne rapport, skal du vælge **RapporterEndpointsWebbeskyttelse** >  >  i navigationsruden.<br/><br/>**TIP**! Hvis du endnu ikke har konfigureret webbeskyttelse for din virksomhed, skal du vælge knappen **Indstillinger** i en rapportvisning. Vælg derefter **filtrering af webindhold** under **Regler**. Du kan få mere at vide om filtrering af webindhold under [Filtrering af webindhold](../defender-endpoint/web-content-filtering.md). |

>
> **Har du et øjeblik?**
> Tag vores <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">korte undersøgelse om sikkerhed</a>. Vi vil meget gerne høre fra dig!
>

## <a name="see-also"></a>Se også

- [Kom i gang med at bruge Microsoft Defender til virksomheder](mdb-get-started.md)
- [Få vist og administrer hændelser i Microsoft Defender til virksomheder](mdb-view-manage-incidents.md)
- [Administrer enheder i Microsoft Defender til virksomheder](mdb-manage-devices.md)
