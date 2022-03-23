---
title: Windows rapport over sikkerhedsopdateringer
description: Forklarer de oplysninger, der præsenteres i denne rapport
keywords: Microsoft-administreret skrivebord, Microsoft 365, tjeneste, dokumentation
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: d20a10fa1fb645763f6eec20f52b4c9e4fe294a1
ms.sourcegitcommit: bae72428d229827cba4c807d9cd362417afbcccb
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/02/2022
ms.locfileid: "63594590"
---
# <a name="windows-security-updates-report"></a>Windows rapport over sikkerhedsopdateringer

Denne rapport indeholder en oversigt over installations status for en given Windows til dine Microsoft-administrerede skrivebordsenheder.

I starten af hver sikkerhedsopdateringsudgivelsescyklus tager Microsoft Managed Desktop et øjebliksbillede af alle de tilmeldte enheder. Installationsmålet er angivet til 95 % af **aktive enheder** fra den pågældende population. Grafen viser din installation status for en valgt udgivelsesdato sammenlignet med gennemsnittet for Microsoft Managed Desktop.

Mens vi fokuserer på den aktive population, kan du også pivotér denne rapport for at vise dine populationer af Aktive **+** synkroniserede og Ikke **synkroniserede** enheder. Du kan få vist installation status for tidligere versioner ved at ændre de tilgængelige filtre, men detaljer på enhedsniveau er kun tilgængelige for den aktuelle version. Enhedsoplysninger i tabellen, der følger grafen, kan også eksporteres til offlineanalyse.

:::image type="content" source="../../media/mmd-security-updates.png" alt-text="Rapport, der viser status for installation af opdateringer over tid øverst til venstre, filtre øverst til højre med en knap til at generere rapporten, og tabel over rapportdetaljer langs bunden":::

Typisk udgiver Microsoft sikkerhedsopdateringer hver anden tirsdag i måneden. De kan dog frigives på andre tidspunkter, når der er behov for det. Hver version tilføjer vigtige opdateringer til kendte sikkerhedsrisici

Microsoft Managed Desktop sikrer, at 95 % af dets aktive enheder opdateres med den nyeste tilgængelige sikkerhedsopdatering hver måned. Når der frigives sikkerhedsopdateringer, og nye trusler haster, installerer Microsoft Managed Desktop ligeledes disse opdateringer.

## <a name="status-categories"></a>Statuskategorier

Vi kategoriserer status for versioner af sikkerhedsopdateringer ved at bruge følgende udtryk:

| Status for sikkerhedsopdatering | Beskrivelse |
| ------ | ------ |
| Aktuel | Enheder, der kører den opdatering, der er udgivet i den aktuelle måned. |
| Forrige | Enheder, der kører den opdatering, der blev udgivet i den forrige måned. |
| Ældre | Enheder, der kører en sikkerhedsopdatering, der er udgivet før den forrige måned. |

> [!NOTE]
> Der bør kun være nogle få enheder i **kategorien** Ældre. En stor eller voksende **Ældre befolkning** angiver sandsynligvis et omfattende problem, som du bør rapportere til Microsoft Managed Desktop til undersøgelse.
