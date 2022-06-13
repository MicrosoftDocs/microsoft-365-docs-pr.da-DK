---
title: Opret forbindelse mellem Microsoft Defender for Office 365 og Microsoft Sentinel
description: Trinnene til at oprette forbindelse Microsoft Defender for Office 365 til Sentinel. Føj dine Microsoft Defender for Office 365 data (*og* data fra resten af Microsoft 365 Defender-pakken), herunder hændelser, til Microsoft Sentinel for at få et enkelt glasrude i din sikkerhed.
search.product: ''
search.appverid: ''
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-guidance-templates
ms.topic: how-to
ms.technology: mdo
ms.openlocfilehash: dbdb4c93ea010959c8f2eae61f9add8ea853d2b1
ms.sourcegitcommit: a7c1acfb3d2cbba913e32493b16ebd8cbfeee456
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/13/2022
ms.locfileid: "66043744"
---
# <a name="connect-microsoft-defender-for-office-365-to-microsoft-sentinel"></a>Opret forbindelse mellem Microsoft Defender for Office 365 og Microsoft Sentinel

Du kan overføre dine Microsoft Defender for Office 365 data (*og* data fra resten af Microsoft 365 Defender-pakken), herunder hændelser, til Microsoft Sentinel.

Udnyt den omfattende administration af sikkerhedsoplysninger (SIEM) kombineret med data fra andre Microsoft 365 kilder, synkronisering af hændelser og beskeder og avanceret jagt.

> [!IMPORTANT]
> Den Microsoft 365 Defender connector er i øjeblikket **en prøveversion**. Se Supplerende vilkår for anvendelse for Microsoft Azure-prøveversioner for at få yderligere juridiske vilkår, der gælder for Azure-funktioner, der er i beta, prøveversion eller på anden måde endnu ikke er offentligt tilgængelige.>

## <a name="what-you-will-need"></a>Det skal du bruge
- Microsoft Defender for Office 365 Plan 2 eller nyere. (Inkluderet i E5-planer)
- Microsoft Sentinel [Quickstart-vejledning](/azure/sentinel/quickstart-onboard).
- Tilstrækkelige tilladelser (sikkerhedsadministrator i M365 & læse-/skrivetilladelser i Sentinel).

## <a name="add-the-microsoft-365-defender-connector"></a>Tilføj Microsoft 365 Defender-connectoren
1. [Log på Azure Portal,](https://portal.azure.com) og naviger til **Microsoft Sentinel** > Vælg det relevante arbejdsområde, der skal integreres med Microsoft 365 Defender
    1. Vælg **Dataconnectors** i navigationsmenuen til venstre under overskriften **Konfiguration** >.
2. Når siden indlæses, skal du **søge efter** Microsoft 365 Defender **og vælge connectoren Microsoft 365 Defender (prøveversion).**
3. Vælg **Åbn forbindelsesside** i pop op-vinduet til højre.
4. Under afsnittet **Konfiguration** på den side, der indlæses, skal du vælge **Forbind hændelser & beskeder** og lade Slå alle Regler for Oprettelse af Microsoft-hændelser for disse produkter fra.
5. Rul til **Microsoft Defender for Office 365** i sektionen **Forbind hændelser** på siden. Vælg **EmailEvents, EmailUrlInfo, EmailAttachmentInfo & EmailPostDeliveryEvents** og derefter  **Anvend ændringer** nederst på siden. (Vælg tabeller fra andre Defender-produkter, hvis det er nyttigt og relevant under dette trin).

## <a name="next-steps"></a>Næste trin

Administratorer kan nu se hændelser, beskeder og rådata i Microsoft Sentinel og bruge disse data til *avanceret jagt* og pivotere på eksisterende og nye data fra Microsoft Defender.

## <a name="more-information"></a>Flere oplysninger

[Forbind Microsoft 365 Defender data til Microsoft Sentinel | Microsoft Docs](/azure/sentinel/connect-microsoft-365-defender?tabs=MDE)

[Forbind Microsoft Teams til Microsoft Sentinel](/microsoftteams/teams-sentinel-guide)
