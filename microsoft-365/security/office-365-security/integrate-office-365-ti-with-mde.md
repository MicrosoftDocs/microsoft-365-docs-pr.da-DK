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
description: Brug Microsoft Defender for Office 365 sammen med Microsoft Defender for Endpoint for at få mere detaljerede oplysninger om trusler mod dine enheder og mailindhold.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: ef1f89a9b218e559855789d0beabad1bc947dad1
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64465921"
---
# <a name="use-microsoft-defender-for-office-365-together-with-microsoft-defender-for-endpoint"></a>Brug Microsoft Defender for Office 365 sammen med Microsoft Defender for Endpoint

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


[Microsoft Defender for Office 365](defender-for-office-365.md) konfigureres til at arbejde med [Microsoft Defender for Endpoint](/windows/security/threat-protection).

Integrering af Microsoft Defender for Office 365 med Microsoft Defender for Endpoint kan hjælpe dit sikkerhedsteam med at overvåge og reagere hurtigt, hvis brugeres enheder er i fare. Når integration er aktiveret, kan dit sikkerhedsteam f.eks. se de enheder, der kan påvirkes af en registreret mail, samt hvor mange nye beskeder, der er genereret for disse enheder i Microsoft Defender for Endpoint.

Følgende billede viser, hvordan fanen **Enheder ser** ud, når du har aktiveret Microsoft Defender for Endpoint integration:

:::image type="content" source="../../media/fec928ea-8f0c-44d7-80b9-a2e0a8cd4e89.PNG" alt-text="En liste over enheder med beskeder" lightbox="../../media/fec928ea-8f0c-44d7-80b9-a2e0a8cd4e89.PNG":::

I dette eksempel kan du se, at modtagerne af den registrerede mail har fire enheder, og én har en besked. Når du klikker på linket for en enhed, åbnes dens side [Microsoft 365 Defender portalen](/microsoft-365/security/defender/microsoft-365-defender).

> [!TIP]
> Den Microsoft 365 Defender portal erstatter Microsoft Defender Security Center. Se [Microsoft Defender for Endpoint i Microsoft 365 Defender](../defender/microsoft-365-security-center-mde.md).

## <a name="requirements"></a>Krav

- Din organisation skal have Microsoft Defender for Office 365 (eller Office 365 E5) og Microsoft Defender for Endpoint.

- Du skal have enten den globale administrator- eller sikkerhedsadministratorrolle tildelt Microsoft 365. Du kan finde flere [oplysninger i Tilladelser i Microsoft 365 Defender portal](permissions-microsoft-365-security-center.md).

- Du skal have adgang [til Stifinder (eller registreringer i realtid)](threat-explorer.md).

## <a name="to-integrate-microsoft-defender-for-office-365-with-microsoft-defender-for-endpoint"></a>Sådan integreres Microsoft Defender for Office 365 med Microsoft Defender for Endpoint

Integrering af Microsoft Defender for Office 365 med Microsoft Defender for Endpoint er konfigureret i både Defender til slutpunkt og Defender for Office 365.

1. Gå til Microsoft 365 Defender -portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på.

2. Gå til **Mail & Samarbejdsstifinder**\>. 

3. På siden **Stifinder** i øverste højre hjørne af skærmen skal du vælge **MDE Indstillinger**.

3. I pop **Microsoft Defender for Endpoint,** der vises, skal du slå **Forbind til Microsoft Defender for Endpoint** (![Til/fra).](../../media/scc-toggle-on.png) Vælg derefter **Luk**.

   :::image type="content" source="../../media/explorer-mdeconnection-dialognew.png" alt-text="Siden MDE-forbindelse" lightbox="../../media/explorer-mdeconnection-dialognew.png":::

4. I navigationsruden skal du **vælge Indstillinger**. På **Indstillinger** skal du **vælge Slutpunkter**

5. På siden **Slutpunkter, der** åbnes, skal du vælge **Avancerede funktioner**.

6. Rul ned **til Office 365 Threat Intelligence-forbindelsen**, og slå den til (![Slå til).](../../media/scc-toggle-on.png).

   Når du er færdig, skal du vælge **Gem indstillinger**.

## <a name="see-also"></a>Se også

[Muligheder for trusselsundersøgelse og svar i Office 365](office-365-ti.md)

[Microsoft Defender for Office 365](defender-for-office-365.md)

[Microsoft Defender for Endpoint](/windows/security/threat-protection)
