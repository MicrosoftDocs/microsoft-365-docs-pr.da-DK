---
title: Tag skridtet videre med avancerede resultater af forespørgselsforespørgsel Microsoft 365 Defender
description: Håndter hurtigt trusler og påvirkede aktiver i dine avancerede resultater af en forespørgsel
keywords: avanceret jagt, trusselssøgning, cybertrusler på jagt, Microsoft 365 Defender, microsoft 365, m365, søg, forespørgsel, telemetri, handling
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: cd4423ab63019b554157de3a05da3c6c7e7d3d4c
ms.sourcegitcommit: ab5368888876d8796da7640553fc8426d040f470
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/04/2021
ms.locfileid: "63603111"
---
# <a name="take-action-on-advanced-hunting-query-results"></a>Tag skridtet videre med avancerede resultater af en forespørgsel

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender
- Microsoft Defender til Slutpunkt

[!INCLUDE [Prerelease information](../includes/prerelease.md)]

Du kan hurtigt indeholde trusler eller håndtere kompromitterede aktiver, som du finder på avanceret [jagt ved hjælp](advanced-hunting-overview.md) af effektive og omfattende handlingsmuligheder. Med disse indstillinger kan du:

- Udføre forskellige handlinger på enheder
- Karantæne af filer

## <a name="required-permissions"></a>Påkrævede tilladelser
Hvis du vil handle gennem avanceret jagt, skal du have en rolle i Microsoft Defender til slutpunkt med tilladelse til [at indsende afhjælpningshandlinger på enheder](/windows/security/threat-protection/microsoft-defender-atp/user-roles#permission-options). Hvis du ikke kan gøre noget, skal du kontakte en global administrator for at få følgende tilladelse:

*Aktive afhjælpningshandlinger > trussel og håndtering af sikkerhedsrisici – afhjælpningshåndtering*

## <a name="take-various-actions-on-devices"></a>Udføre forskellige handlinger på enheder
Du kan udføre følgende handlinger på enheder, der er identificeret af kolonnen `DeviceId` i dine forespørgselsresultater:

- Isolere påvirkede enheder, så de indeholder en virus eller forhindrer angreb i at bevæge sig side om side
- Indsamle undersøgelsespakke for at indhente mere information om sagen
- Kør en antivirusscanning for at finde og fjerne trusler ved hjælp af de nyeste sikkerhedsopdateringer
- Initier en automatisk undersøgelse for at kontrollere og afhjælpe trusler på enheden og muligvis andre påvirkede enheder
- Begræns udførelse af apps til kun eksekverbare Microsoft-filer, hvilket forhindrer efterfølgende trusselsaktivitet via malware eller andre upålidelige eksekverbare filer

Du kan få mere at vide om, hvordan disse svarhandlinger udføres via Microsoft Defender til slutpunkt, [ved at læse om svarhandlinger på enheder](/windows/security/threat-protection/microsoft-defender-atp/respond-machine-alerts).
   
## <a name="quarantine-files"></a>Karantæne af filer
Du kan installere *karantænehandlingen* på filer, så de automatisk er i karantæne, når de stødes. Når du vælger denne handling, kan du vælge mellem følgende kolonner for at identificere, hvilke filer i forespørgslen, der skal karantæne:

- `SHA1` – I de fleste avancerede jagttabeller er dette SHA-1 i filen, der blev påvirket af den registrerede handling. Hvis f.eks. en fil blev kopieret, ville dette være den kopierede fil.
- `InitiatingProcessSHA1` – I de fleste avancerede jagttabeller er dette filen, der er ansvarlig for at starte den registrerede handling. Hvis eksempelvis en underordnet proces blev startet, ville dette være den overordnede proces. 
- `SHA256` – Dette er SHA-256-svarende til den fil, der identificeres af `SHA1` kolonnen.
- `InitiatingProcessSHA256` – Dette er SHA-256-svarende til den fil, der identificeres af `InitiatingProcessSHA1` kolonnen.

Hvis du vil have mere at vide om, hvordan der skal oprettes karantænehandlinger, og hvordan filer kan gendannes, kan du [læse om svarhandlinger for filer](/windows/security/threat-protection/microsoft-defender-atp/respond-file-alerts).

>[!NOTE]
>For at finde filer og sætte dem i karantæne skal forespørgselsresultaterne også indeholde `DeviceId` værdier som enheds-id'er.  

## <a name="take-action"></a>Gør noget
Hvis du vil udføre en af de beskrevne handlinger, skal du vælge en eller flere poster i forespørgselsresultaterne og derefter **vælge Udføre handlinger**. En guide vejleder dig gennem processen med at vælge og derefter indsende dine foretrukne handlinger.

![Billede af valgt post med panel til undersøgelse af posten.](../../media/take-action-multiple.png)

## <a name="review-actions-taken"></a>Gennemse handlinger, der er foretaget
Hver handling optages individuelt i [handlingscenteret](m365d-action-center.md) under **HandlingscenterHistory**  >  ([security.microsoft.com/action-center/history](https://security.microsoft.com/action-center/history)). Gå til handlingscenter for at kontrollere status for hver handling.
 
>[!NOTE]
>Nogle tabeller i denne artikel er muligvis ikke tilgængelige i Microsoft Defender til slutpunkt. [Slå en Microsoft 365 Defender til](m365d-enable.md) for at lede efter trusler ved hjælp af flere datakilder. Du kan flytte dine avancerede arbejdsprocesser på jagt fra Microsoft Defender for Endpoint til Microsoft 365 Defender ved at følge trinnene i Overfør avancerede [forespørgselsforespørgsler fra Microsoft Defender til slutpunkt](advanced-hunting-migrate-from-mde.md).

## <a name="related-topics"></a>Relaterede emner
- [Avanceret jagtoversigt](advanced-hunting-overview.md)
- [Lær forespørgselssproget](advanced-hunting-query-language.md)
- [Arbejd med forespørgselsresultater](advanced-hunting-query-results.md)
- [Forstå skemaet](advanced-hunting-schema-tables.md)
- [Oversigt over handlingscenter](m365d-action-center.md)
