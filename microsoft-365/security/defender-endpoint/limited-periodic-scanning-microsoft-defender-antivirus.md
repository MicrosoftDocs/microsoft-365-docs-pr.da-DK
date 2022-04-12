---
title: Aktivér den begrænsede periodiske Microsoft Defender Antivirus scanningsfunktion
description: Med begrænset periodisk scanning kan du bruge Microsoft Defender Antivirus ud over dine andre installerede AV-udbydere
keywords: lps, begrænset, periodisk, scanning, scanning, kompatibilitet, tredjepart, anden av, deaktiver
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
ms.openlocfilehash: 5201366ee003efab1edd5a0a536c45db4ec7aabc
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/12/2022
ms.locfileid: "64788892"
---
# <a name="use-limited-periodic-scanning-in-microsoft-defender-antivirus"></a>Brug begrænset periodisk scanning i Microsoft Defender Antivirus

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**

- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Antivirus

**Platforme**
- Windows

Begrænset periodisk scanning er en særlig type trusselsregistrering og -afhjælpning, der kan aktiveres, når du har installeret et andet antivirusprogram på en Windows 10 eller Windows 11 enhed.

Den kan kun aktiveres i visse situationer. Du kan få flere oplysninger om begrænset periodisk scanning, og hvordan Microsoft Defender Antivirus fungerer sammen med andre antivirusprogrammer, [under Microsoft Defender Antivirus kompatibilitet](microsoft-defender-antivirus-compatibility.md).

**Microsoft anbefaler ikke, at du bruger denne funktion i virksomhedsmiljøer. Dette er en funktion, der primært er beregnet til forbrugere.** Denne funktion bruger kun et begrænset undersæt af de Microsoft Defender Antivirus funktioner til at registrere malware og vil ikke være i stand til at registrere mest malware og potentielt uønsket software. Desuden vil administrations- og rapporteringsfunktionerne være begrænset. Microsoft anbefaler virksomheder at vælge deres primære antivirusløsning og udelukkende bruge den.

## <a name="how-to-enable-limited-periodic-scanning"></a>Sådan aktiverer du begrænset periodisk scanning

Som standard aktiverer Microsoft Defender Antivirus sig selv på en Windows 10 eller en Windows 11 enhed, hvis der ikke er installeret andre antivirusprogrammer, eller hvis det andet produkt er forældet, udløbet eller ikke fungerer korrekt.

Hvis Microsoft Defender Antivirus er aktiveret, ser de sædvanlige indstillinger ud til at konfigurere det på den pågældende enhed:

:::image type="content" source="images/vtp-wdav.png" alt-text="Appen Windows Sikkerhed, der viser Microsoft Defender AV-indstillinger, herunder scanningsindstillinger, indstillinger og opdateringsindstillinger" lightbox="images/vtp-wdav.png":::

Hvis et andet antivirusprogram er installeret og fungerer korrekt, deaktiverer Microsoft Defender Antivirus sig selv. Den Windows Sikkerhed app ændrer afsnittet **Virus & threat Protection** for at få vist status for AV-produktet og giver et link til produktets konfigurationsindstillinger.

Under alle AV-produkter fra tredjepart vises et nyt link som **Microsoft Defender Antivirus muligheder**. Hvis du klikker på dette link, udvides det for at vise til/fra-knappen, der muliggør begrænset periodisk scanning. Bemærk, at den begrænsede periodiske indstilling er en til/fra-knap til aktivering eller deaktivering af periodisk scanning. 

Hvis du flytter kontakten til **Til** , vises standardindstillingerne for Microsoft Defender AV under tredjeparts-AV-produktet. Den begrænsede periodiske scanningsindstilling vises nederst på siden.

## <a name="related-articles"></a>Relaterede artikler

- [Konfigurer funktionsmåde-, heuristisk- og realtidsbeskyttelse](configure-protection-features-microsoft-defender-antivirus.md)
- [Microsoft Defender Antivirus i Windows 10](microsoft-defender-antivirus-in-windows-10.md)

> [!TIP]
> Hvis du leder efter antivirusrelaterede oplysninger til andre platforme, kan du se:
> - [Angiv indstillinger for Microsoft Defender for Endpoint på macOS](mac-preferences.md)
> - [Microsoft Defender for Endpoint på Mac](microsoft-defender-endpoint-mac.md)
> - [macOS Antivirus politikindstillinger for Microsoft Defender Antivirus til Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Angiv indstillinger for Microsoft Defender for Endpoint på Linux](linux-preferences.md)
> - [Microsoft Defender for Endpoint på Linux](microsoft-defender-endpoint-linux.md)
> - [Konfigurer Defender for Endpoint på Android-funktioner](android-configure.md)
> - [Konfigurer Microsoft Defender for Endpoint på iOS-funktioner](ios-configure-features.md)