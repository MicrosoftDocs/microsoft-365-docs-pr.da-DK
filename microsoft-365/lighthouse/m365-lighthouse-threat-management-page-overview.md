---
title: Microsoft 365 oversigt over siden til administration af fyrtårne
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: For administrerede tjenesteudbydere ved hjælp af Microsoft 365 Lighthouse kan du få mere at vide om siden til administration af trusler.
ms.openlocfilehash: e57163ba462e241c74a96db78fe701c024a037ff
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63606625"
---
# <a name="microsoft-365-lighthouse-threat-management-page-overview"></a>Microsoft 365 oversigt over siden til administration af fyrtårne 

**Gælder for:**

- Windows 10

Microsoft Defender Antivirus beskytter lejere, brugere og enheder mod softwaretrusler, herunder virus, malware og spyware. Det er robust, løbende beskyttelse, der er indbygget i Windows 10 og inkluderet Microsoft 365 Business Premium og Microsoft365E3&nbsp;&nbsp;.  
  
For at få adgang til siden trusselsadministration i Microsoft 365 Lighthouse skal du  vælge Trusselsadministration i venstre navigationsrude for at få vist dine kundelejere sikkerhedstilstand over for trusler. Du får vist lejere, brugere og enheder, der kræver din opmærksomhed, og anbefalinger, der kan hjælpe dig med at reducere risikoen.  
  
## <a name="overview-tab"></a>Fanen Oversigt  
  
På fanen Oversigt på siden Trusselsadministration kan du overvåge antivirustilstanden på tværs af alle dine lejere for at identificere de områder, der kræver opmærksomhed.

:::image type="content" source="../media/m365-lighthouse-threat-management-page-overview/threatmanagement-overview-tab.png" alt-text="Skærmbillede af fanen Oversigt.":::

## <a name="threats-tab"></a>Fanen Trusler

På fanen Trusler på siden Administration af trusler kan du se trusler som Aktive, Reducerede, Løste og Tilladte trusler på tværs af alle dine lejere. Du kan også løse flere trusler på samme tid på tværs af alle dine lejere ved at filtrere og analysere hver enkelt trussel for at finde ud af, hvilke enheder, brugere eller lejere, der påvirkes.

:::image type="content" source="../media/m365-lighthouse-threat-management-page-overview/threatmanagement-threats-tab.png" alt-text="Skærmbillede af siden Standard for grundlinje.":::
  
Du kan filtrere trusler ved at:

- Trusselsstatus
- Alvorlighed af trusler
- Trusselstype
- Datointerval

I følgende tabel vises de forskellige trusselsstatusser og deres definition:<br><br>

| Trusselsstatus | Definition |
|--|--|
| Aktiv | Trussel er aktiv på enheden. |
| Ingen status | Status for trussel er ikke tilgængelig. Kør en komplet scanning på enheden for at Microsoft Defender Antivirus for at ombygge truslerne. |
| Handlingen mislykkedes | Enheden er ikke i fare. En handling mislykkedes, men en potentiel trussel er stoppet og er ikke aktiv på enheden. Kør en fuld scanning på enheden. |
| Manuelle trin påkrævet | Trussel er blevet stoppet, men det kræver, at du fuldfører et manuelt trin, f.eks. en fuld scanning eller en genstart af enheden. |
| Fuld scanning påkrævet | Der kræves en komplet scanning af enheden. |
| Genstart er påkrævet | Du skal genstarte enheden. |
| Løst med ikke-kritiske fejl | Truslerne er blevet løst, og der kræves ingen yderligere handlinger. |
| Karantæne | Truslerne er blevet sat i karantæne. Der kræves ingen yderligere handlinger. |
| Fjernet | Trussel er blevet fjernet fra enheden. Der kræves ingen yderligere handlinger. |
| Ryddet | Microsoft Defender Antivirus har gendannede og slettede filer. Der kræves ingen yderligere handlinger. |
| Tilladt | En administrator tillader, at truslerne forbliver på enheden. | 

## <a name="antivirus-protection-tab"></a>Fanen Antivirusbeskyttelse

Fanen Antivirusbeskyttelse på siden Administration af trusler viser enhederne på tværs af alle dine lejere og deres Microsoft Defender Antivirus beskyttelsestilstand. Du kan vurdere status og handle på en eller flere enheder, der kan være sårbar. Du kan også vælge en enhed for at få vist flere oplysninger, f.eks. Enhedsoversigt, Aktuelle trusler og Status for enhedshandling.

:::image type="content" source="../media/m365-lighthouse-threat-management-page-overview/threatmanagement-antivirus-tab.png" alt-text="Skærmbillede af fanen Antivirus.":::

## <a name="related-content"></a>Relateret indhold

[Installér Microsoft 365 Lighthouse-grundlinjer](m365-lighthouse-deploy-baselines.md) (artikel)\
[Microsoft 365 ofte stillede spørgsmål om fyrtårn](m365-lighthouse-faq.yml) (artikel)
