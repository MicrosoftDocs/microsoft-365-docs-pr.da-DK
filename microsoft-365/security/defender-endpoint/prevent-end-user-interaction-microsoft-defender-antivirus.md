---
title: Skjul grænsefladen Microsoft Defender Antivirus
description: Du kan skjule feltet til beskyttelse af virus og trusler i Windows Sikkerhed-appen.
keywords: ui lockdown, hovedløs tilstand, skjule app, skjule indstillinger, skjule grænseflade
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 10/18/2021
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.topic: article
ms.collection: M365-security-compliance
ms.openlocfilehash: fdd212efd50d55bbcdae80275f5d2ca8a97cdeb3
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/12/2022
ms.locfileid: "64787660"
---
# <a name="prevent-users-from-seeing-or-interacting-with-the-microsoft-defender-antivirus-user-interface"></a>Undgå, at brugerne får vist eller interagerer med den Microsoft Defender Antivirus brugergrænseflade

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Antivirus

**Platforme**
- Windows

Du kan bruge Gruppepolitik til at forhindre brugere på slutpunkter i at se den Microsoft Defender Antivirus grænseflade. Du kan også forhindre dem i at afbryde scanningerne midlertidigt.

## <a name="hide-the-microsoft-defender-antivirus-interface"></a>Skjul grænsefladen Microsoft Defender Antivirus

I Windows 10 vil version 1703 skjule Microsoft Defender Antivirus meddelelser og forhindre, at feltet Virus & trusselsbeskyttelse vises i Windows Sikkerhed-appen.

Når indstillingen er angivet til **Aktiveret**:

:::image type="content" source="../../media/wdav-headless-mode-off-1703.png" alt-text="Den Windows Sikkerhed uden skjoldikonet og afsnittene om beskyttelse mod virus og trusler" lightbox="../../media/wdav-headless-mode-off-1703.png":::

Når indstillingen er angivet til **Deaktiveret** eller ikke konfigureret:

:::image type="content" source="../../media/wdav-headless-mode-1703.png" alt-text="Den Windows Sikkerhed med skjoldikon- og trusselsbeskyttelsessektioner" lightbox="../../media/wdav-headless-mode-1703.png":::

> [!NOTE]
> Hvis du skjuler grænsefladen, forhindres Microsoft Defender Antivirus meddelelser også i at blive vist på slutpunktet. Microsoft Defender for Endpoint meddelelser vises stadig. Du kan også [konfigurere de meddelelser, der vises på slutpunkter](configure-notifications-microsoft-defender-antivirus.md), individuelt

I tidligere versioner af Windows 10 skjuler indstillingen den Windows Defender klientgrænseflade. Hvis brugeren forsøger at åbne den, får vedkommende vist en advarsel om, at "Systemadministratoren har begrænset adgang til denne app".

:::image type="content" source="../../media/wdav-headless-mode-1607.png" alt-text="Advarselsmeddelelsen, når hovedløs tilstand er aktiveret i Windows 10 versioner, der er ældre end 1703" lightbox="../../media/wdav-headless-mode-1607.png":::

## <a name="use-group-policy-to-hide-the-microsoft-defender-av-interface-from-users"></a>Brug Gruppepolitik til at skjule Microsoft Defender AV-grænsefladen for brugere

1. Åbn [administrationskonsollen Gruppepolitik Gruppepolitik](/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal), højreklik på det Gruppepolitik objekt, du vil konfigurere, og klik på **Rediger**.

2. Ved hjælp af **administrationseditoren Gruppepolitik** gå til **Computerkonfiguration**.

3. Klik på **Administrative skabeloner**.

4. Udvid træet for at **Windows komponenter > Microsoft Defender Antivirus > klientgrænsefladen**.

5. Dobbeltklik på indstillingen **Aktivér hovedløs brugergrænsefladetilstand** , og angiv indstillingen til **Aktiveret**. Klik på **OK**.

Se [Forhindre brugere i at ændre politikindstillinger lokalt](configure-local-policy-overrides-microsoft-defender-antivirus.md) for at få flere indstillinger til at forhindre brugere i at ændre beskyttelse på deres pc'er.

## <a name="prevent-users-from-pausing-a-scan"></a>Forhindre brugere i at afbryde en scanning midlertidigt

Du kan forhindre brugere i at afbryde scanningerne midlertidigt, hvilket kan være nyttigt for at sikre, at planlagte scanninger eller scanninger efter behov ikke afbrydes af brugerne.

> [!NOTE]
> Denne indstilling understøttes ikke på Windows 10.

### <a name="use-group-policy-to-prevent-users-from-pausing-a-scan"></a>Brug Gruppepolitik til at forhindre brugere i at afbryde en scanning midlertidigt

1. Åbn [administrationskonsollen Gruppepolitik Gruppepolitik](/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal), højreklik på det Gruppepolitik objekt, du vil konfigurere, og klik på **Rediger**.

2. Ved hjælp af **administrationseditoren Gruppepolitik** gå til **Computerkonfiguration**.

3. Klik på **Administrative skabeloner**.

4. Udvid træet for at **Windows komponenter** \> **Microsoft Defender Antivirus** \> **Scan**.

5. Dobbeltklik på indstillingen **Tillad, at brugere afbryder scanning midlertidigt** , og angiv indstillingen til **Deaktiveret**. Klik på **OK**.

> [!TIP]
> Hvis du leder efter antivirusrelaterede oplysninger til andre platforme, kan du se:
> - [Angiv indstillinger for Microsoft Defender for Endpoint på macOS](mac-preferences.md)
> - [Microsoft Defender for Endpoint på Mac](microsoft-defender-endpoint-mac.md)
> - [macOS Antivirus politikindstillinger for Microsoft Defender Antivirus til Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Angiv indstillinger for Microsoft Defender for Endpoint på Linux](linux-preferences.md)
> - [Microsoft Defender for Endpoint på Linux](microsoft-defender-endpoint-linux.md)
> - [Konfigurer Defender for Endpoint på Android-funktioner](android-configure.md)
> - [Konfigurer Microsoft Defender for Endpoint på iOS-funktioner](ios-configure-features.md)

## <a name="related-articles"></a>Relaterede artikler

- [Konfigurer de meddelelser, der vises på slutpunkter,](configure-notifications-microsoft-defender-antivirus.md)
- [Konfigurer slutbrugerinteraktion med Microsoft Defender Antivirus](configure-end-user-interaction-microsoft-defender-antivirus.md)
- [Microsoft Defender Antivirus i Windows 10](microsoft-defender-antivirus-in-windows-10.md)
