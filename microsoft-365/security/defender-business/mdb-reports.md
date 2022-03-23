---
title: Rapporter i Microsoft Defender for Business
description: Få et overblik over de rapporter, der er tilgængelige i Microsoft Defender for Business
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 03/15/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 68b5c15b69c1f485bb9ed90bab06c2ceaa2978d9
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/17/2022
ms.locfileid: "63593674"
---
# <a name="reports-in-microsoft-defender-for-business"></a>Rapporter i Microsoft Defender for Business

> [!IMPORTANT]
> Microsoft Defender for Business udrulles til [Microsoft 365 Business Premium](../../business-premium/index.md) kunder fra d. 1. marts 2022. Defender for Business som et enkeltstående abonnement er i preview, og den udrulles gradvist til kunder og [it-partnere](https://aka.ms/mdb-preview) , der tilmelder sig her for at anmode om det. [Forhåndsvisning indeholder et indledende sæt scenarier](mdb-tutorials.md#try-these-preview-scenarios), og vi tilføjer funktioner regelmæssigt.
> 
> Nogle oplysninger i denne artikel relaterer til foreløbige produkter/tjenester, der kan være væsentligt ændret, før de frigives kommercielt. Microsoft giver ingen garantier, udtrykkelige eller underforståede, for de oplysninger, du har angivet her. 

Der findes flere rapporter i Microsoft 365 Defender portal ([https://security.microsoft.com](https://security.microsoft.com)). I denne artikel beskrives disse rapporter, hvordan du kan bruge dem, og hvordan du finder dem.

<br/><br/>

## <a name="reports-in-defender-for-business"></a>Rapporter i Defender for Business

|Rapport  |Beskrivelse  |
|---------|---------|
| **Sikkerhedsrapport**  | Sikkerhedsrapporten indeholder oplysninger om dit firmas identiteter, enheder og apps. For at få adgang til denne rapport skal du i navigationsruden **vælge** **ReportsGeneralSecurity-rapport** >  > . <br/><br/>**Tip** Du kan få vist lignende oplysninger på startsiden på Microsoft 365 Defender portal ([https://security.microsoft.com](https://security.microsoft.com)). |
| **Trusselsbeskyttelse**  | Rapporten om trusselsbeskyttelse indeholder oplysninger om vigtige beskeder og tendenser. Brug kolonnen **Beskedtendenser** til at få vist oplysninger om beskeder, der er blevet udløst i løbet af de seneste 30 dage. Brug kolonnen **Beskedstatus** til at få vist aktuelle øjebliksbilleder af beskeder, f.eks. kategorier af ikke-afklarede beskeder og deres klassificering. For at få adgang til denne rapport skal du i **navigationsruden vælge ReportsEndpointsThreat** >  >  **Protection**. <br/><br/>**Tip**: Du kan også bruge listen **Hændelser til** at få vist oplysninger om beskeder. I navigationsruden skal du vælge **Hændelser for** at få vist og administrere aktuelle hændelser. Du kan få mere at [vide under Få vist og administrer hændelser i Microsoft Defender for Business](mdb-view-manage-incidents.md). |
| **Enhedstilstand og overholdelse af regler og standarder** | Rapporten om enhedens tilstand og overholdelse giver oplysninger om enhedens tilstand og tendenser. Du kan bruge denne rapport til at afgøre, om defender for Business-sensorerne fungerer korrekt på enheder, og om den aktuelle status for Microsoft Defender Antivirus. For at få adgang til denne rapport skal du i **navigationsruden vælge ReportsEndpointsDevice** >  >  **health and compliance**. <br/><br/>**Tip**: Du kan bruge **lagerlisten for** enheder til at få vist oplysninger om virksomhedens enheder. Vælg Lagerliste for enhed i **navigationsruden**. Du kan få mere at vide [under Administrer enheder i Microsoft Defender for Business](mdb-manage-devices.md). |
| **Sårbar enheder** | Rapporten over følsomme enheder indeholder oplysninger om enheder og tendenser. Brug kolonnen **Tendenser** til at få vist oplysninger om enheder, der har haft beskeder i løbet af de seneste 30 dage. Brug kolonnen **Status** til at få vist aktuelle øjebliksbilleder af enheder, der har beskeder. For at få adgang til denne rapport skal du i **navigationsruden vælge ReportsEndpointsVulnerable** >  >  **devices**.<br/><br/>**Tip**: Du kan bruge **lagerlisten for** enheder til at få vist oplysninger om virksomhedens enheder. Vælg Lagerliste for enhed i **navigationsruden**. Du kan få mere at vide [under Administrer enheder i Microsoft Defender for Business](mdb-manage-devices.md). |
| **Webbeskyttelse** | Rapporten om webbeskyttelse viser forsøg på at få adgang til phishingwebsteder, malwarevektorer, udnyttelseswebsteder, upålidelige websteder eller websteder med dårligt ry og websteder, der udtrykkeligt er blokeret. Kategorier af blokerede websteder omfatter indhold beregnet til voksne, websteder med ferie, juridiske ansvarswebsteder og meget mere. For at få adgang til denne rapport skal du vælge **ReportsEndpointsWeb** >  **protection i navigationsruden** > .<br/><br/>**Tip**: Hvis du endnu ikke har konfigureret webbeskyttelse for din virksomhed, skal du **vælge Indstillinger** i en rapportvisning. Derefter skal du under **Regler** vælge **Filtrering af webindhold**. Hvis du vil have mere at vide om filtrering af webindhold, skal [du se Filtrering af webindhold](../defender-endpoint/web-content-filtering.md). |

>
> **Har du et minut?**
> Tag vores korte <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">undersøgelse om Microsoft Defender for Business</a>. Vi vil meget gerne høre fra dig!
>

## <a name="see-also"></a>Se også

- [Kom i gang med at bruge Microsoft Defender for Business](mdb-get-started.md)

- [Få vist og administrer hændelser i Microsoft Defender for Business](mdb-view-manage-incidents.md)

- [Administrer enheder i Microsoft Defender for Business](mdb-manage-devices.md)