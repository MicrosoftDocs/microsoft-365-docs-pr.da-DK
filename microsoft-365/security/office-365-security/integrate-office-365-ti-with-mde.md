---
title: Brug Microsoft Defender for Office 365 sammen med Microsoft Defender for Endpoint
f1.keywords:
- NOCSH
keywords: integrate, Microsoft Defender, Microsoft Defender for Endpoint
ms.author: deniseb
author: denisebmsft
manager: dansimp
ms.date: 12/02/2021
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
description: Brug Microsoft Defender for Office 365 sammen med Microsoft Defender for Endpoint til at få mere detaljerede oplysninger om trusler mod dine enheder og mailindhold.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 8df364538e6a799557956a8d624b0561c626e4fd
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/20/2022
ms.locfileid: "64971104"
---
# <a name="use-microsoft-defender-for-office-365-together-with-microsoft-defender-for-endpoint"></a>Brug Microsoft Defender for Office 365 sammen med Microsoft Defender for Endpoint

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

[Microsoft Defender for Office 365](defender-for-office-365.md) kan konfigureres til at arbejde med [Microsoft Defender for Endpoint](/windows/security/threat-protection).

Integration af Microsoft Defender for Office 365 med Microsoft Defender for Endpoint kan hjælpe dit team med sikkerhedshandlinger med at overvåge og handle hurtigt, hvis brugernes enheder er i fare. Når integration er aktiveret, kan dit team for sikkerhedshandlinger f.eks. se de enheder, der potentielt påvirkes af en registreret mail, samt hvor mange seneste beskeder der er genereret for disse enheder i Microsoft Defender for Endpoint.

På følgende billede vises, hvordan fanen **Enheder** ser ud, når integration af Microsoft Defender for Endpoint er aktiveret:

:::image type="content" source="../../media/fec928ea-8f0c-44d7-80b9-a2e0a8cd4e89.PNG" alt-text="En liste over enheder med beskeder" lightbox="../../media/fec928ea-8f0c-44d7-80b9-a2e0a8cd4e89.PNG":::

I dette eksempel kan du se, at modtagerne af den registrerede mail har fire enheder, og én har en besked. Når du klikker på linket til en enhed, åbnes siden på [Microsoft 365 Defender-portalen](/microsoft-365/security/defender/microsoft-365-defender).

> [!TIP]
> Microsoft 365 Defender-portalen erstatter Microsoft Defender Security Center. Se [Microsoft Defender for Endpoint i Microsoft 365 Defender](../defender/microsoft-365-security-center-mde.md).

## <a name="requirements"></a>Krav

- Organisationen skal have Microsoft Defender for Office 365 (eller Office 365 E5) og Microsoft Defender for Endpoint.

- Du skal enten have tildelt rollen global administrator eller sikkerhedsadministrator i Microsoft 365. Du kan få flere oplysninger [under Tilladelser på Microsoft 365 Defender-portalen](permissions-microsoft-365-security-center.md).

- Du skal have adgang til [Stifinder (eller registreringer i realtid).](threat-explorer.md)

## <a name="to-integrate-microsoft-defender-for-office-365-with-microsoft-defender-for-endpoint"></a>Sådan integrerer du Microsoft Defender for Office 365 med Microsoft Defender for Endpoint

Integration af Microsoft Defender for Office 365 med Microsoft Defender for Endpoint er konfigureret både i Defender for Endpoint og Defender for Office 365.

1. Gå til Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på.

2. Gå til **Mail & samarbejdsoversigt**\>.

3. Vælg **MDE-Indstillinger** i øverste højre hjørne af skærmen på siden **Stifinder**.

3. I pop op-vinduet **Microsoft Defender for Endpoint forbindelse**, der vises, skal du slå **Forbind til for at Microsoft Defender for Endpoint** (![Til/fra](../../media/scc-toggle-on.png)) og derefter vælge **Luk**.

   :::image type="content" source="../../media/explorer-mdeconnection-dialognew.png" alt-text="Siden MDE-forbindelse" lightbox="../../media/explorer-mdeconnection-dialognew.png":::

4. Vælg **Indstillinger** i navigationsruden. Vælg **Slutpunkter** på siden **Indstillinger**

5. Vælg **Avancerede funktioner** på siden **Slutpunkter**, der åbnes.

6. Rul ned for at **Office 365 Threat Intelligence-forbindelse**, og slå den til (![Slå til).](../../media/scc-toggle-on.png)

   Når du er færdig, skal du vælge **Gem indstillinger**.

## <a name="see-also"></a>Se også

[Trusselsundersøgelses- og svarfunktioner i Office 365](office-365-ti.md)

[Microsoft Defender for Office 365](defender-for-office-365.md)

[Microsoft Defender for Endpoint](/windows/security/threat-protection)
