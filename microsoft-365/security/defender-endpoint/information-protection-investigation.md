---
title: Brug følsomhedsmærkater til at prioritere hændelsesrespons
description: Få mere at vide om, hvordan du bruger følsomhedsmærkater til at prioritere og undersøge hændelser
keywords: oplysninger, beskyttelse, data, tab, forebyggelse,mærkater, dlp, hændelse, undersøgelse, undersøgelse
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 8a1cafe4cd54b7313e0555127221173e23a41bbf
ms.sourcegitcommit: dfa9f28a5a5055a9530ec82c7f594808bf28d0dc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/29/2021
ms.locfileid: "63592727"
---
# <a name="use-sensitivity-labels-to-prioritize-incident-response"></a>Brug følsomhedsmærkater til at prioritere hændelsesrespons

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

En typisk avanceret livscyklus for vedvarende trusler indebærer dataudfyldning. I en sikkerhedshændelse er det vigtigt, at du har mulighed for at prioritere undersøgelser, hvor følsomme filer kan være følsomme, så virksomhedens data og oplysninger beskyttes.

Defender til Slutpunkt hjælper med at gøre prioritering af sikkerhedshændelser meget enklere med brugen af følsomhedsmærkater. Følsomhedsmærkater identificerer hurtigt hændelser, der kan involvere enheder med følsomme oplysninger, f.eks fortrolige oplysninger.

## <a name="investigate-incidents-that-involve-sensitive-data"></a>Undersøg hændelser, der involverer følsomme data

Få mere at vide om, hvordan du bruger datafølsomhedsetiketter til at prioritere undersøgelse af hændelser.

> [!NOTE]
> Navne registreres for Windows 10, version 1809 eller nyere, og Windows 11.

1. I Microsoft 365 Defender portal skal du **vælge Hændelser & beskeder om** \> **hændelser**.

2. Rul til højre for at se **kolonnen Datafølsomhed** . Denne kolonne afspejler følsomhedsmærkater, der er blevet observeret på enheder, der er relateret til hændelserne, hvilket viser, om følsomme filer kan blive påvirket af hændelsen.

    ![Billede af kolonnen datafølsomhed.](images/data-sensitivity-column.png)

    Du kan også filtrere baseret på **datafølsomhed**

    ![Billede af datafølsomhedsfilter.](images/data-sensitivity-filter.png)

3. Åbn hændelsessiden for at undersøge det yderligere.

    ![Billede af oplysninger om hændelsesside.](images/incident-page.png)

4. Vælg fanen **Enheder** for at identificere enheder, der lagrer filer med følsomhedsmærkater.

    ![Billede af fanen Enhed.](images/investigate-devices-tab.png)

5. Vælg de enheder, der gemmer følsomme data, og søg gennem tidslinjen for at identificere, hvilke filer der kan blive påvirket, og tag derefter de nødvendige handlinger for at sikre, at dataene er beskyttet.

   Du kan indsnævre de hændelser, der vises på enhedens tidslinje, ved at søge efter datafølsomhedsmærkater. Når du gør dette, vises kun begivenheder, der er knyttet til filer, der har det nævnte etiketnavn.

    ![Billede af enhedens tidslinje med indsnævrede søgeresultater baseret på etiket.](images/machine-timeline-labels.png)

> [!TIP]
> Disse datapunkter vises også via "DeviceFileEvents" ved avanceret jagt, så avancerede forespørgsler og registrering af tidsplaner kan tage højde for følsomhedsmærkater og filbeskyttelsesstatus.
