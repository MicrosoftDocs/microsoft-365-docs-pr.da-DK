---
title: Billedmærkning i SharePoint-syntex
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.custom: admindeeplinkMAC
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: medium
ROBOTS: NOINDEX, NOFOLLOW
description: Få mere at vide om billedmærkning i SharePoint-syntex
ms.openlocfilehash: 79df10f80dd02930dc49f56274b00664c6f1d3d2
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63601688"
---
# <a name="image-tagging-in-sharepoint-syntex"></a>Billedmærkning i SharePoint-syntex

(Kommer snart)

Med billedmærkning i SharePoint-syntekst kan brugerne finde billeder via søgning ved at søge efter billedmærker og oprette arbejdsprocesser baseret på billedmærker. Grundlæggende billedmærkning er som standard slået til i SharePoint og OneDrive. Billeder, der uploades til begge placeringer, scannes automatisk, og relevante mærker anvendes, hvis de er tilgængelige, fra en liste over 37 grundlæggende mærker. Brugerne kan finde billeder gennem søgning ved at søge efter billedmærkerne.

Når en bruger overfører et billede, kører mærkningsprocessen automatisk. Hvis et billede redigeres, kører mærkningsprocessen igen for at opdatere mærkerne.

Brugere med tilladelser til billedfilen kan se og redigere mærkerne i panelet med filoplysninger eller på siden med søgeresultater. Når en bruger redigerer et billedes mærker, mærker systemet ikke længere automatisk billedet, heller ikke selvom det er redigeret.

Hvis du slår mærkning fra, mærkes billeder ikke længere automatisk. Eksisterende mærker fjernes ikke.

> [!NOTE]
> Systemgenererede mærker kan blive ændret med opdateringer af billedet eller vores mærketeknologi.


## <a name="configure-image-tagging"></a>Konfigurere billedmærkning

Når du [har konfigureret SharePoint-syntex](set-up-content-understanding.md), kan du konfigurere billedmærkning i Microsoft 365 Administration.  

Sådan slår du billedmærkning til eller fra

1. Vælg Konfiguration i Microsoft 365 <a href="https://go.microsoft.com/fwlink/p/?linkid=2171997" target="_blank">**Administration**</a>.

2. Klik **på Automatiser** **indholdsforståelse under Organisatorisk viden**.

3. Klik **på Administrer**.

4. Klik på **Rediger under** **fanen Billedmærkning**.

5. Vælg at tillade **Grundlæggende mærkning eller** slå mærkning **Fra**.

6. Klik på **Gem**.

    ![Skærmbillede af kontrolelementet til billedmærkning.](../media/content-understanding/sharepoint-syntex-image-tagging-control.png)
