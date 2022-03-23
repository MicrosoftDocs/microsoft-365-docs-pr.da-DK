---
title: Brug Microsoft Defender til Office 365 med Microsoft Defender til slutpunkt
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
description: Brug Microsoft Defender til Office 365 med Microsoft Defender til Endpoint for at få mere detaljerede oplysninger om trusler mod dine enheder og dit mailindhold.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 67406984e73f39858f4a7329a8c8520fcd35ac5c
ms.sourcegitcommit: 4c207a9bdbb6c8ba372ae37907ccefca031a49f8
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/09/2022
ms.locfileid: "63593192"
---
# <a name="use-microsoft-defender-for-office-365-together-with-microsoft-defender-for-endpoint"></a>Brug Microsoft Defender til Office 365 med Microsoft Defender til slutpunkt

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


[Microsoft Defender for Office 365](defender-for-office-365.md) konfigureres til at fungere sammen [med Microsoft Defender til slutpunkt](/windows/security/threat-protection).

Integrering af Microsoft Defender for Office 365 med Microsoft Defender til Slutpunkt kan hjælpe dit sikkerhedsteam med at overvåge og reagere hurtigt, hvis brugeres enheder er i fare. Når integration er aktiveret, kan dit sikkerhedsteam f.eks. se de enheder, der kan påvirkes af en registreret mail, samt hvor mange nye beskeder, der er genereret for disse enheder i Microsoft Defender til slutpunkt.

Følgende billede viser, hvordan fanen **Enheder ser** ud, når du har aktiveret Microsoft Defender til slutpunktsintegration:

![Når Microsoft Defender til slutpunkt er aktiveret, kan du se en liste over enheder med beskeder.](../../media/fec928ea-8f0c-44d7-80b9-a2e0a8cd4e89.PNG)

I dette eksempel kan du se, at modtagerne af den registrerede mail har fire enheder, og én har en besked. Når du klikker på linket for en enhed, åbnes dens side [Microsoft 365 Defender portalen](/microsoft-365/security/defender/microsoft-365-defender).

> [!TIP]
> Den Microsoft 365 Defender portal erstatter Microsoft Defender Security Center. Se [Microsoft Defender til slutpunkt i Microsoft 365 Defender](../defender/microsoft-365-security-center-mde.md).

## <a name="requirements"></a>Krav

- Din organisation skal have Microsoft Defender til Office 365 (eller Office 365 E5) og Microsoft Defender til slutpunkt.

- Du skal have enten den globale administrator- eller sikkerhedsadministratorrolle tildelt Microsoft 365. Du kan finde flere [oplysninger i Tilladelser i Microsoft 365 Defender portal](permissions-microsoft-365-security-center.md).

- Du skal have adgang [til Stifinder (eller registreringer i realtid)](threat-explorer.md).

## <a name="to-integrate-microsoft-defender-for-office-365-with-microsoft-defender-for-endpoint"></a>Sådan integreres Microsoft Defender for Office 365 med Microsoft Defender til Endpoint

Integrering af Microsoft Defender for Office 365 med Microsoft Defender til slutpunkt er konfigureret i både Defender til Endpoint og Defender Office 365.

1. Gå til Microsoft 365 Defender -portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på.

2. Gå til **Mail & Samarbejdsstifinder**\>. 

3. På siden **Stifinder** i øverste højre hjørne af skærmen skal du vælge **MDE Indstillinger**.

3. I pop op-vindue'en **Microsoft Defender for Endpoint-forbindelse**, **der vises, skal du slå Forbind til Microsoft Defender for Endpoint** (![Til/](../../media/scc-toggle-on.png)fra). Vælg derefter **Luk**.

    :::image type="content" source="../../media/explorer-mdeconnection-dialognew.png" alt-text="MDE-forbindelse.":::

4. I navigationsruden skal du **vælge Indstillinger**. På **Indstillinger** skal du **vælge Slutpunkter**

5. På siden **Slutpunkter, der** åbnes, skal du vælge **Avancerede funktioner**.

6. Rul ned **til Office 365 Threat Intelligence-forbindelsen**, og slå den til (![Slå til).](../../media/scc-toggle-on.png).

   Når du er færdig, skal du vælge **Gem indstillinger**.

## <a name="see-also"></a>Se også

[Muligheder for trusselsundersøgelse og svar i Office 365](office-365-ti.md)

[Microsoft Defender til Office 365](defender-for-office-365.md)

[Microsoft Defender til Slutpunkt](/windows/security/threat-protection)
