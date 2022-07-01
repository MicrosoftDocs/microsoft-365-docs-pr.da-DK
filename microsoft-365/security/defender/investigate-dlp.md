---
title: Undersøg datatabshændelser med Microsoft 365 Defender
description: Undersøg tab af data i Microsoft 365 Defender.
keywords: Forebyggelse af datatab, hændelser, beskeder, undersøge, analysere, svar, korrelation, angreb, maskiner, enheder, brugere, identitet, identitet, postkasse, mail, 365, microsoft, m365
f1.keywords:
- NOCSH
ms.prod: m365-security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
ms.technology: m365d
ms.openlocfilehash: a92e3b206b10b68ecc3ff2f94870a9174185b63b
ms.sourcegitcommit: 85799f0efc06037c1ff309fe8e609bbd491f9b68
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/01/2022
ms.locfileid: "66574291"
---
# <a name="investigate-data-loss-incidents-with-microsoft-365-defender"></a>Undersøg datatabshændelser med Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**

- Microsoft 365 Defender

Hændelser for Microsoft Purview Forebyggelse af datatab (DLP) kan nu administreres på Microsoft 365 Defender-portalen. Du kan administrere DLP-hændelser sammen med sikkerhedshændelser fra **hændelser & beskeder** \> **Hændelser** på hurtig start af <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender-portalen</a>. Fra denne side kan du:

- Få vist alle dine DLP-beskeder grupperet under hændelser i Microsoft 365 Defender hændelseskø.
- Få vist intelligente mellemløsningsbeskeder (DLP-MDE, DLP-MDO) og DLP-DLP-indbyrdes forbundne beskeder under en enkelt hændelse.
- Gå på jagt efter overholdelseslogge sammen med sikkerhed under Avanceret jagt.
- Handlinger til lokal administratorafhjælpning på bruger, fil og enhed. 
- Knyt brugerdefinerede mærker til DLP-hændelser, og filtrer efter dem.
- Filtrer efter DLP-politiknavn, kode, dato, tjenestekilde, hændelsesstatus og bruger på den samlede hændelseskø. 

Du kan også bruge connectoren Microsoft 365 Defender i Microsoft Sentinel til at trække DLP-hændelser sammen med hændelser og beviser til Microsoft Sentinel til undersøgelse og afhjælpning.

## <a name="licensing-requirements"></a>Licenskrav

Hvis du vil undersøge Microsoft Purview Forebyggelse af datatab hændelser på Microsoft 365 Defender-portalen, skal du have en licens fra et af følgende abonnementer: 

- Microsoft Office 365 E5/A5
- Microsoft 365 E5/A5
- overholdelse af Microsoft 365 E5/A5
- sikkerhed Microsoft 365 E5/A5
- Microsoft 365 E5/A5 Information Protection og styring

> [!NOTE] 
> Når du er licenseret og berettiget til denne funktion, overføres DLP-beskeder automatisk til Microsoft 365 Defender. Åbn en supportsag, hvis du vil deaktivere denne funktion. 

## <a name="dlp-investigation-experience-in-the-microsoft-365-defender-portal"></a>DLP-undersøgelsesoplevelse på Microsoft 365 Defender-portalen

Før du starter, [skal du aktivere beskeder for alle dine DLP-politikker](/microsoft-365/compliance/dlp-configure-view-alerts-policies#alert-configuration-experience) i <a href="https://purview.microsoft.com" target="_blank">Microsoft Purview-compliance-portal</a>.

1. Gå til Microsoft 365 Defender-portalen, og vælg **Hændelser** i navigationsmenuen til venstre for at åbne siden med hændelser.

2. Vælg **Filtre** øverst til højre, og vælg **Tjenestekilde: Forebyggelse af datatab** for at få vist alle hændelser med DLP-beskeder.

3. Søg efter navnet på DLP-politikken for de beskeder og hændelser, du er interesseret i.

4. Hvis du vil have vist oversigtssiden for hændelser, skal du vælge hændelsen i køen. På samme måde skal du vælge beskeden for at få vist DLP-beskedsiden.

5. Få vist **historien Besked** for at få oplysninger om politik og de følsomme oplysningstyper, der er registreret i beskeden. Vælg hændelsen i afsnittet **Relaterede hændelser** for at få vist oplysninger om brugeraktivitet.

6. Få vist det tilsvarende følsomme indhold under fanen **Typer af følsomme oplysninger** og filindholdet under fanen **Kilde** , hvis du har den nødvendige tilladelse (se detaljer <a href="/microsoft-365/compliance/dlp-alerts-dashboard-get-started#roles" target="_blank">her</a>).

7. Du kan også bruge Avanceret jagt til at søge i overvågningslogge over brugere, filer og webstedsplaceringer for din undersøgelse. Tabellen **CloudAppEvents** indeholder alle overvågningslogge på tværs af alle placeringer, f.eks. Sharepoint, OneDrive, Exchange og enheder.

8. Du kan også downloade mailen ved at vælge **Handlinger** \> **Download mail**. 

9. For afhjælpningshandlinger på filer på SPO- eller ODB-websteder kan du se handlinger som:

    - Anvend opbevaringsmærkat
    - Anvend følsomhedsmærkat
    - Annuller deling af fil
    - Slette

   For afhjælpningshandlinger skal du vælge **kortet Bruger** øverst på beskedsiden for at åbne brugeroplysningerne.

   For DLP-beskeder for enheder skal du vælge enhedskortet øverst på beskedsiden for at få vist enhedsoplysningerne og udføre afhjælpningshandlinger på enheden.

10. Gå til siden med oversigt over hændelser, og vælg **Administrer hændelse** for at tilføje hændelseskoder, tildele eller løse en hændelse.

## <a name="dlp-investigation-experience-in-microsoft-sentinel"></a>DLP-undersøgelsesoplevelse i Microsoft Sentinel

Du kan bruge connectoren Microsoft 365 Defender i Microsoft Sentinel til at importere alle DLP-hændelser i Sentinel for at udvide din korrelation, registrering og undersøgelse på tværs af andre datakilder og udvide dine automatiserede orkestreringsflows ved hjælp af Sentinels oprindelige SOAR-funktioner. 

1. Følg vejledningen på Opret forbindelse mellem data fra Microsoft 365 Defender og Microsoft Sentinel for at importere alle hændelser, herunder DLP-hændelser og beskeder i Sentinel. Aktivér `CloudAppEvents` hændelsesconnectoren for at trække alle O365-overvågningslogge til Sentinel.

   Du bør kunne se dine DLP-hændelser i Sentinel, når ovenstående connector er konfigureret.

2. Vælg **Beskeder** for at få vist beskedsiden.

3. Du kan bruge **AlertType**, **startTime** og **endTime** til at forespørge tabellen **CloudAppEvents** for at få alle de brugeraktiviteter, der har bidraget til beskeden. Brug denne forespørgsel til at identificere de underliggende aktiviteter:

```kusto
let Alert = SecurityAlert 
| where TimeGenerated  > ago(30d) 
| where SystemAlertId == "" // insert the systemAlertID here 
CloudAppEvents 
| extend correlationId = parse_json(tostring(RawEventData.Data)).cid
| join kind=inner Alert on $left.correlationId == $right.AlertType 
| where RawEventData.CreationTime > StartTime and RawEventData.CreationTime < EndTime
```

## <a name="related-articles"></a>Relaterede artikler

- [Oversigt over hændelser](incidents-overview.md)
- [Prioriter hændelser](incident-queue.md)
- [Administrer hændelser](manage-incidents.md)
