---
title: Aktivér den begrænsede Microsoft Defender Antivirus scanningsfunktion
description: Begrænset periodisk scanning lader dig bruge Microsoft Defender Antivirus ud over dine andre installerede udbydere af av-programmer
keywords: lps, begrænset, periodisk, scanning, scanning, kompatibilitet, tredjepartsprogram, anden av, deaktiver
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 10/18/2018
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: e0a8293709da44dc3a46cf565ad099666e8dae24
ms.sourcegitcommit: dfa9f28a5a5055a9530ec82c7f594808bf28d0dc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/29/2021
ms.locfileid: "63595885"
---
# <a name="use-limited-periodic-scanning-in-microsoft-defender-antivirus"></a>Brug begrænset periodisk scanner i Microsoft Defender Antivirus

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**

- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Begrænset periodisk scanning er en særlig type trusselsregistrering og afhjælpning, der kan aktiveres, når du har installeret et andet antivirusprodukt på en Windows 10 eller Windows 11-enhed.

Den kan kun aktiveres i visse situationer. Du kan finde flere oplysninger om begrænset periodisk scanning, Microsoft Defender Antivirus fungerer med andre antivirusprodukter, [under Microsoft Defender Antivirus kompatibilitet](microsoft-defender-antivirus-compatibility.md).

**Microsoft anbefaler ikke at bruge denne funktion i virksomhedsmiljøer. Dette er en funktion, der primært er beregnet til forbrugere.** Denne funktion anvender kun et begrænset antal Microsoft Defender Antivirus-funktioner til at registrere malware og vil ikke kunne registrere de fleste malwares og potentielt uønsket software. Desuden vil administrations- og rapporteringsfunktionerne være begrænsede. Microsoft anbefaler virksomheder at vælge deres primære antivirusløsning og udelukkende bruge den.

## <a name="how-to-enable-limited-periodic-scanning"></a>Sådan aktiveres begrænset periodisk scanner

Som standard aktiverer Microsoft Defender Antivirus sig selv på en Windows 10- eller Windows 11-enhed, hvis der ikke er installeret noget andet antivirusprodukt, eller hvis det andet produkt er forældet, udløbet eller ikke fungerer korrekt.

Hvis Microsoft Defender Antivirus er aktiveret, vises de sædvanlige indstillinger for at konfigurere den på den pågældende enhed:

![Windows Sikkerhed, der viser Microsoft Defender AV-indstillinger, herunder scanningsindstillinger, indstillinger og opdateringsindstillinger.](images/vtp-wdav.png)

Hvis et andet antivirusprodukt er installeret og fungerer korrekt, Microsoft Defender Antivirus deaktiveres automatisk. Appen Windows Sikkerhed ændrer sektionen **virus- &-trusselsbeskyttelse** for at vise status for AV-produktet og give et link til produktets konfigurationsindstillinger.

Under eventuelle tredjeparts AV-produkter, vises et nyt link som **Microsoft Defender Antivirus indstillinger**. Når du klikker på dette link, udvides det for at få vist den til/fra-knap, der muliggør begrænset periodisk scanner. Bemærk, at den begrænsede periodiske indstilling er en til/fra-knap til at aktivere eller deaktivere periodisk scanner. 

Hvis du skubber knappen **til Til** , vises de almindelige Microsoft Defender AV-indstillinger under tredjeparts-AV-produktet. Indstillingen Begrænset periodisk scanner vises nederst på siden.

## <a name="related-articles"></a>Relaterede artikler

- [Konfigurer funktionsmåde-, heuristisk- og realtidsbeskyttelse](configure-protection-features-microsoft-defender-antivirus.md)
- [Microsoft Defender Antivirus i Windows 10](microsoft-defender-antivirus-in-windows-10.md)