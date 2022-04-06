---
title: Spor din Microsoft Secure Score-historik, og opdr. mål
description: Få indsigt i aktiviteter, der har påvirket din Microsoft Secure Score. Se tendenser, og angiv mål.
keywords: microsoft secure score, secure score, office 365 secure score, microsoft security score, Microsoft 365 Defender portal, forbedringshandlinger
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
ms.topic: article
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
- seo-marvel-jun2020
ms.technology: m365d
ms.openlocfilehash: 03a7a070d574ec18a12c3e70d5cef20d2161490b
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/06/2022
ms.locfileid: "64663748"
---
# <a name="track-your-microsoft-secure-score-history-and-meet-goals"></a>Spor din Microsoft Secure Score-historik, og opdr. mål

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

[Microsoft Secure Score](microsoft-secure-score.md) er en måling af en organisations sikkerhedsholdning, hvor et højere antal angiver, at der er foretaget flere forbedringshandlinger. Du kan finde den på https://security.microsoft.com/securescore [Microsoft 365 Defender-portalen](microsoft-365-defender.md#the-microsoft-365-defender-portal).

## <a name="gain-insights-into-activity-that-has-affected-your-score"></a>Få indsigt i aktiviteter, der har påvirket din score

Få vist en graf over din organisations resultat over tid under fanen **Historik** .

Under grafen er der en liste over alle de handlinger, der udføres i det valgte tidsinterval, og deres attributter, f.eks. resultatpunkter og kategori. Du kan tilpasse et datointerval og filtrere efter kategori.

:::image type="content" source="../../media/secure-score/secure-score-history-activity.png" alt-text="Et eksempel på den side, der beskriver aktivitetsoversigten på portalen Microsoft 365 Defender" lightbox="../../media/secure-score/secure-score-history-activity.png":::

Hvis du vælger den forbedringshandling, der er knyttet til en aktivitet, vises pop op-vinduet med handlingen til fuld forbedring.

Hvis du vil have vist al historik for denne specifikke forbedringshandling, skal du vælge linket Oversigt i pop op-vinduet.

:::image type="content" source="../../media/secure-score/secure-score-history-flyout.png" alt-text="Ruden Oversigt vedrørende forbedringshandling på Microsoft 365 Defender-portalen" lightbox="../../media/secure-score/secure-score-history-flyout.png":::

## <a name="discover-trends-and-set-goals"></a>Se tendenser, og angiv mål

Under fanen **Målepunkter & tendenser** er der flere grafer og diagrammer, der giver dig mere indsigt i tendenser og angive mål. Du kan angive datointervallet for hele siden med visualiseringer. Visualiseringerne omfatter:

* **Zonen Sikker score** – tilpasset på baggrund af organisationens mål og definitioner på gode, okay og forkerte scoreintervaller.
* **Regressionstendens** – En tidslinje over punkter, der er regressioneret på grund af konfigurations-, bruger- eller enhedsændringer.  
* **Sammenligningstendens** – hvordan din organisations Secure Score sammenlignes med andres over tid. Denne visning kan indeholde linjer, der repræsenterer scoregennemsnittet for organisationer med lignende antal pladser og en brugerdefineret sammenligningsvisning, som du kan angive.
* **Tendens for risikoaccept** – Tidslinje for forbedringshandlinger markeret som "accepteret risiko".
* **Scoreændringer** – antallet af opnåede point, point regression og ændringer af din score i det angivne datointerval.

### <a name="compare-your-score-to-organizations-like-yours"></a>Sammenlign din score med organisationer som din

Der er to steder, hvor du kan se, hvordan din score er sammenlignet med organisationer, der ligner din.

#### <a name="comparison-bar-chart"></a>Liggende søjlediagram til sammenligning

Det liggende søjlediagram til sammenligning er tilgængeligt under fanen **Oversigt** . Peg på diagrammet for at få vist scoren og score salgsmuligheden. 

:::image type="content" source="../../media/secure-score/secure-score-comparison-bar.png" alt-text="Et eksempel på søjlediagrammet over lignende organisationsresultater på Microsoft 365 Defender portalen" lightbox="../../media/secure-score/secure-score-comparison-bar.png":::

Sammenligningsdataene anonymiseres, så vi ved ikke præcist, hvilke andre lejere der er i blandingen.

![Søjlediagram over lignende organisationsresultater.](../../media/secure-score/secure-score-comparison-screenshot.png)

#### <a name="comparison-trend"></a>Sammenligningstendens

På fanen **Metrikværdier & tendenser** kan du se, hvordan din organisations Secure Score sammenlignes med andres over tid.

:::image type="content" source="../../media/secure-score/secure-score-comparison-trend.png" alt-text="Et eksempel på et kurvediagram over lignende organisations scorer over tid på Microsoft 365 Defender portalen" lightbox="../../media/secure-score/secure-score-comparison-trend.png":::

## <a name="we-want-to-hear-from-you"></a>Vi vil gerne høre fra dig

Hvis du har problemer, kan du fortælle os det ved at slå op i community'et [Sikkerhed, Beskyttelse af personlige oplysninger & Overholdelse.](https://techcommunity.microsoft.com/t5/Security-Privacy-Compliance/bd-p/security_privacy) Vi overvåger community'et og yder hjælp.

## <a name="related-resources"></a>Relaterede ressourcer

- [Oversigt over Microsoft Secure Score](microsoft-secure-score.md)
- [Vurder dit sikkerhedsniveau](microsoft-secure-score-improvement-actions.md)
- [Hvad kommer der](microsoft-secure-score-whats-coming.md)
- [Nyheder](microsoft-secure-score-whats-new.md)
