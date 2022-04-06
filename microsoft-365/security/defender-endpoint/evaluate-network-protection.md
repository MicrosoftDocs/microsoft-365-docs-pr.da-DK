---
title: Evaluer netværksbeskyttelse
description: Se, hvordan netværksbeskyttelse fungerer ved at teste almindelige scenarier, som det beskytter mod.
keywords: Netværksbeskyttelse, udnyttelse, skadeligt websted, ip, domæne, domæner, evaluer, test, demo
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
audience: ITPro
ms.topic: conceptual
author: dansimp
ms.author: dansimp
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.collection:
- m365solution-scenario
- M365-security-compliance
ms.date: ''
ms.openlocfilehash: df79062d1dafcd8d82dfa4ff9b9847ff4fad1775
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64476131"
---
# <a name="evaluate-network-protection"></a>Evaluer netværksbeskyttelse

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[Netværksbeskyttelse hjælper](network-protection.md) med at forhindre medarbejdere i at bruge et hvilket som helst program til at få adgang til skadelige domæner, der kan hoste forsøg på phishing, udnyttelse og andet skadeligt indhold på internettet.

Denne artikel hjælper dig med at evaluere netværksbeskyttelse ved at aktivere funktionen og guide dig til et testwebsted. Webstederne i denne evalueringsartikel er ikke skadelige. De er specialoprettede websteder, der udgiver sig for at være skadelige. Webstedet replikerer den funktionsmåde, der ville ske, hvis en bruger besøgte et skadeligt websted eller domæne.

> [!TIP]
> Du kan også besøge webstedet for Microsoft Defender-demoscenarier på [demo.wd.microsoft.com](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) for at se, hvordan andre beskyttelsesfunktioner fungerer.

> [!NOTE]
> Defender for Endpoint-demowebstedet demo.wd.microsoft.com forældet og fjernes fremover.

## <a name="enable-network-protection-in-audit-mode"></a>Aktivér netværksbeskyttelse i overvågningstilstand

Aktivér netværksbeskyttelse i overvågningstilstand for at se, hvilke IP-adresser og domæner der ville være blevet blokeret. Du kan sikre dig, at det ikke påvirker line of business-apps, eller du kan få en ide om, hvor ofte blokke forekommer.

1. Skriv **powershell** i menuen Start, højreklik på **Windows PowerShell** vælg **Kør som administrator**
2. Angiv følgende cmdlet:

    ```PowerShell
    Set-MpPreference -EnableNetworkProtection AuditMode
    ```

### <a name="visit-a-fake-malicious-domain"></a>Besøg et (falsk) skadeligt domæne

1. Åbn Internet Explorer, Google Chrome eller en anden browser efter eget valg.

2. Gå til [https://smartscreentestratings2.net](https://smartscreentestratings2.net).

    Netværksforbindelsen tillades, og der vises en testmeddelelse.
    
    :::image type="content" source="images/np-notif.png" alt-text="Meddelelse om blokering af forbindelse" lightbox="images/np-notif.png":::

> [!NOTE]
> Netværksforbindelser kan blive gennemført, selvom et websted er blokeret af netværksbeskyttelse. Du kan få mere at [vide under Netværksbeskyttelse og TCP trevejs-handshake](network-protection.md#network-protection-and-the-tcp-three-way-handshake).

## <a name="review-network-protection-events-in-windows-event-viewer"></a>Gennemse netværksbeskyttelseshændelser i Windows Logbog

Hvis du vil gennemse apps, der ville være blevet blokeret, skal du åbne Logbog og filtrere efter Hændelses-id 1125 i Microsoft-Windows-Windows Defender/driftsloggen. I følgende tabel vises alle netværksbeskyttelseshændelser.

| Hændelses-id | Angiv/kilde | Beskrivelse |
|---|---|---|
| 5007 | Windows Defender (drift) | Hændelse, når indstillingerne ændres |
| 1125 | Windows Defender (drift) | Hændelse, når en netværksforbindelse overvåges |
| 1126 | Windows Defender (drift) | Hændelse, når en netværksforbindelse er blokeret |

## <a name="see-also"></a>Se også

- [Netværksbeskyttelse](network-protection.md)

- [Netværksbeskyttelse og TCP trevejs-handshake](network-protection.md#network-protection-and-the-tcp-three-way-handshake)

- [Aktivér netværksbeskyttelse](enable-network-protection.md)

- [Fejlfinding af netværksbeskyttelse](troubleshoot-np.md)
