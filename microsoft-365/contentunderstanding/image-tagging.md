---
title: Billedmarkering i SharePoint Syntex
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
description: Få mere at vide om billedmarkering i SharePoint Syntex
ms.openlocfilehash: e0b9b1669efb069942b81aaad7fb5e7e3aa57c1c
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/14/2022
ms.locfileid: "65415876"
---
# <a name="image-tagging-in-sharepoint-syntex"></a>Billedmarkering i SharePoint Syntex

(Kommer snart)

Med billedmarkering i SharePoint Syntex kan brugerne finde billeder via søgning ved at søge efter billedtags og oprette arbejdsprocesser baseret på billedkoder. Grundlæggende billedmarkering er som standard slået til for SharePoint og OneDrive. Billeder, der uploades til en af placeringerne, scannes automatisk, og relevante mærker anvendes, hvis de er tilgængelige, fra en liste over 37 grundlæggende tags. Brugerne kan finde billeder via søgning ved at søge i billedkoderne.

Når en bruger uploader et billede, kører mærkningsprocessen automatisk. Hvis et billede redigeres, køres mærkningsprocessen igen for at opdatere koderne.

Brugere med tilladelser til billedfilen kan se og redigere mærkerne i panelet med filoplysninger eller på siden med søgeresultater. Når en bruger redigerer et billedes mærker, koder systemet ikke længere billedet automatisk, selvom det er redigeret.

Hvis du slår mærkning fra, mærkes billeder ikke længere automatisk. Eksisterende mærker fjernes ikke.

> [!NOTE]
> Systemgenererede mærker kan ændres med opdateringer til billedet eller vores kodeteknologi.

## <a name="configure-image-tagging"></a>Konfigurer billedmarkering

Når du [har konfigureret SharePoint Syntex](set-up-content-understanding.md), kan du konfigurere billedmarkering i Microsoft 365 Administration.

Sådan slår du billedmarkering til eller fra

1. Vælg <a href="https://go.microsoft.com/fwlink/p/?linkid=2171997" target="_blank">**Konfigurer**</a> i Microsoft 365 Administration.

2. Klik på **Automatiser forståelse af indhold** under **Organisationsviden**.

3. Klik på **Administrer**.

4. Klik på **Rediger** under fanen **Billedmarkering**.

5. Vælg at tillade **grundlæggende mærkning** eller slå mærkning **fra**.

6. Klik på **Gem**.

    ![Skærmbillede af kontrolelementet til billedmarkering.](../media/content-understanding/sharepoint-syntex-image-tagging-control.png)
