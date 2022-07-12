---
title: Evaluer netværksbeskyttelse
description: Se, hvordan netværksbeskyttelse fungerer, ved at teste almindelige scenarier, som den beskytter mod.
keywords: Netværksbeskyttelse, udnyttelser, skadeligt websted, ip, domæne, domæner, evaluere, teste, demo
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
- M365-security-compliance
ms.date: ''
ms.openlocfilehash: 4c9c0618db34df38168dca881117288832abf4a5
ms.sourcegitcommit: c314e989202dc1c9c260fffd459d53bc1f08514e
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/12/2022
ms.locfileid: "66717840"
---
# <a name="evaluate-network-protection"></a>Evaluer netværksbeskyttelse

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[Netværksbeskyttelse](network-protection.md) hjælper med at forhindre medarbejdere i at bruge alle programmer til at få adgang til farlige domæner, der kan hoste phishing-svindel, udnyttelser og andet skadeligt indhold på internettet.

Denne artikel hjælper dig med at evaluere netværksbeskyttelse ved at aktivere funktionen og føre dig til et testwebsted. Webstederne i denne evalueringsartikel er ikke skadelige. De er specielt oprettede websteder, der foregiver at være ondsindede. Webstedet replikerer den funktionsmåde, der ville ske, hvis en bruger besøgte et skadeligt websted eller domæne.

## <a name="enable-network-protection-in-audit-mode"></a>Aktivér netværksbeskyttelse i overvågningstilstand

Aktivér netværksbeskyttelse i overvågningstilstand for at se, hvilke IP-adresser og domæner der ville være blevet blokeret. Du kan sikre dig, at det ikke påvirker line of business-apps, eller du kan få en idé om, hvor ofte der forekommer blokke.

1. Skriv **powershell** i menuen Start, højreklik **Windows PowerShell**, og vælg **Kør som administrator**
2. Angiv følgende cmdlet:

    ```PowerShell
    Set-MpPreference -EnableNetworkProtection AuditMode
    ```

### <a name="visit-a-fake-malicious-domain"></a>Besøg et (falsk) skadeligt domæne

1. Åbn Internet Explorer, Google Chrome eller en hvilken som helst anden browser efter eget valg.

2. Gå til [https://smartscreentestratings2.net](https://smartscreentestratings2.net).

    Netværksforbindelsen tillades, og der vises en testmeddelelse.
    
    :::image type="content" source="images/np-notif.png" alt-text="Meddelelsen om blokering af forbindelsen" lightbox="images/np-notif.png":::

> [!NOTE]
> Netværksforbindelser kan lykkes, selvom et websted er blokeret af netværksbeskyttelse. Du kan få mere at vide under [Netværksbeskyttelse og TCP-trevejshandsket](network-protection.md#network-protection-and-the-tcp-three-way-handshake).

## <a name="review-network-protection-events-in-windows-event-viewer"></a>Gennemse netværksbeskyttelseshændelser i Windows Logbog

Hvis du vil gennemse apps, der ville være blevet blokeret, skal du åbne Logbog og filtrere efter Event ID 1125 i Microsoft-Windows-Windows Defender/Operational-logfilen. I følgende tabel vises alle netværksbeskyttelseshændelser.

| Hændelses-id | Angiv/kilde | Beskrivelse |
|---|---|---|
| 5007 | Windows Defender (driftsklar) | Hændelse, når indstillingerne ændres |
| 1125 | Windows Defender (driftsklar) | Hændelse, når en netværksforbindelse overvåges |
| 1126 | Windows Defender (driftsklar) | Hændelse, når en netværksforbindelse er blokeret |

## <a name="see-also"></a>Se også

- [Netværksbeskyttelse](network-protection.md)

- [Netværksbeskyttelse og TCP-trevejs-håndtryk](network-protection.md#network-protection-and-the-tcp-three-way-handshake)

- [Aktivér netværksbeskyttelse](enable-network-protection.md)

- [Foretag fejlfinding af netværksbeskyttelse](troubleshoot-np.md)
