---
title: Definer, hvordan mobilenheder opdateres af Microsoft Defender Antivirus
description: Administrer, hvordan mobilenheder, f.eks. bærbare computere, skal opdateres med Microsoft Defender Antivirus beskyttelsesopdateringer.
keywords: opdateringer, beskyttelse, tidsplanopdateringer, batteri, mobilenhed, bærbar, notesbog, tilvalg, Microsoft update, wsus, tilsidesættelse
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.collection: M365-security-compliance
ms.openlocfilehash: f582e33f2d77c8560b773b79d54026e38bcde8c9
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/12/2022
ms.locfileid: "64790366"
---
# <a name="manage-updates-for-mobile-devices-and-virtual-machines-vms"></a>Administrer opdateringer til mobilenheder og virtuelle maskiner (VMs)

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**

- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Antivirus

**Platforme**
- Windows

Mobilenheder og VM'er kan kræve mere konfiguration for at sikre, at ydeevnen ikke påvirkes af opdateringer.

Der er to indstillinger, der er nyttige til disse enheder:

- Tilmeld dig Microsoft Update på bærbare computere uden en WSUS-forbindelse
- Undgå opdateringer af sikkerhedsintelligens, når du kører på batteri

Følgende artikler kan også være nyttige i disse situationer:
- [Konfiguration af planlagte scanninger og opfangning af scanninger](scheduled-catch-up-scans-microsoft-defender-antivirus.md)
- [Administrer opdateringer for slutpunkter, der er forældede](manage-outdated-endpoints-microsoft-defender-antivirus.md)
- [Udrulningsvejledning til Microsoft Defender Antivirus i et VDI-miljø (Virtual Desktop Infrastructure)](deployment-vdi-microsoft-defender-antivirus.md)

## <a name="opt-in-to-microsoft-update-on-mobile-computers-without-a-wsus-connection"></a>Tilmeld dig Microsoft Update på bærbare computere uden en WSUS-forbindelse

Du kan bruge Microsoft Update til at holde Sikkerhedsintelligens på mobilenheder kørende Microsoft Defender Antivirus opdateret, når de ikke har forbindelse til virksomhedens netværk eller på anden måde ikke har en WSUS-forbindelse.

Det betyder, at beskyttelsesopdateringer kan leveres til enheder (via Microsoft Update), selvom du har angivet WSUS til at tilsidesætte Microsoft Update.

Du kan vælge Microsoft Update på mobilenheden på en af følgende måder:

- Rediger indstillingen med Gruppepolitik.
- Brug en VBScript til at oprette et script og derefter køre det på hver computer i netværket.
- Tilmelder manuelt alle computere på netværket via **menuen Indstillinger**.

### <a name="use-group-policy-to-opt-in-to-microsoft-update"></a>Brug Gruppepolitik til at tilmelde dig Microsoft Update

1. Åbn [administrationskonsollen Gruppepolitik Gruppepolitik](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)), højreklik på det Gruppepolitik objekt, du vil konfigurere, og vælg **Rediger**.

2. Gå til **Computerkonfiguration** i **administrationseditoren Gruppepolitik**.

3. Vælg **Politikker** og derefter **Administrative skabeloner**.

4. Udvid træet for at **Windows komponenter** \> **Microsoft Defender Antivirus** \> **Signaturopdateringer**.

5. Angiv **Tillad opdateringer af sikkerhedsintelligens fra Microsoft Update** til **Aktiveret**, og vælg derefter  **OK**.

### <a name="use-a-vbscript-to-opt-in-to-microsoft-update"></a>Brug en VBScript til at tilmelde dig Microsoft Update

1. Brug vejledningen i [MSDN-artiklen Tilmeld dig Microsoft Update](/windows/win32/wua_sdk/opt-in-to-microsoft-update) for at oprette VBScript.

2. Kør den VBScript, du har oprettet på hver computer i netværket.

### <a name="manually-opt-in-to-microsoft-update"></a>Tilmeld dig Microsoft Update manuelt

1. Åbn **Windows Update** i **Opdater & sikkerhedsindstillinger** på den computer, du vil tilmelde dig.

2. Vælg **Avancerede** indstillinger.

3. Markér afkrydsningsfeltet for **Giv mig opdateringer til andre Microsoft-produkter, når jeg opdaterer Windows**.

## <a name="prevent-security-intelligence-updates-when-running-on-battery-power"></a>Undgå opdateringer af sikkerhedsintelligens, når du kører på batteri

Du kan konfigurere Microsoft Defender Antivirus til kun at downloade opdateringer til beskyttelse, når pc'en har forbindelse til en kablet strømkilde.

### <a name="use-group-policy-to-prevent-security-intelligence-updates-on-battery-power"></a>Brug Gruppepolitik til at forhindre opdateringer af sikkerhedsintelligens på batteri

1. Åbn [administrationskonsollen Gruppepolitik Gruppepolitik](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)), vælg det Gruppepolitik objekt, du vil konfigurere, og åbn det til redigering.

2. Gå til **Computerkonfiguration** i **administrationseditoren Gruppepolitik**.

3. Vælg **Politikker** og derefter **Administrative skabeloner**.

4. Udvid træet for at **Windows komponenter** \> **Microsoft Defender Antivirus** \> **Signaturopdateringer**, og angiv derefter **Tillad opdateringer af sikkerhedsintelligens, når du kører på batteri til** **Deaktiveret**. Vælg derefter **OK**.

Denne handling forhindrer, at opdateringer til beskyttelse downloades, når pc'en er på batteri.

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

- [Administrer Microsoft Defender Antivirus opdateringer, og anvend oprindelige planer](manage-updates-baselines-microsoft-defender-antivirus.md)
- [Opdater og administrer Microsoft Defender Antivirus i Windows 10](deploy-manage-report-microsoft-defender-antivirus.md)