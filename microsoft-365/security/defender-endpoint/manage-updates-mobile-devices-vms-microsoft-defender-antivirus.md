---
title: Definer, hvordan mobilenheder opdateres, Microsoft Defender Antivirus
description: Administrer, hvordan mobilenheder, f.eks. bærbare computere, skal opdateres Microsoft Defender Antivirus opdateringer til beskyttelse.
keywords: opdateringer, beskyttelse, planlæg opdateringer, batteri, mobilenhed, bærbar computer, notesbog, tilmelding, microsoft update, wsus, override
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
ms.openlocfilehash: 3fc6d5a8b8fa7889f65f21111b3af82e124516b4
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2021
ms.locfileid: "63606496"
---
# <a name="manage-updates-for-mobile-devices-and-virtual-machines-vms"></a>Administrer opdateringer til mobilenheder og virtuelle maskiner (VMs)

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**

- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Mobilenheder og VM'er kræver muligvis mere konfiguration for at sikre, at ydeevnen ikke påvirkes af opdateringer.

Der er to indstillinger, der er nyttige for disse enheder:

- Tilmelde dig Microsoft Update på mobilenheder uden en WSUS-forbindelse
- Undgå sikkerhedsintelligensopdateringer, når der køres på batteristrøm

Følgende artikler kan også være nyttige i disse situationer:
- [Konfiguration af planlagte scanninger og indfangningsscanninger](scheduled-catch-up-scans-microsoft-defender-antivirus.md)
- [Administrere opdateringer for slutpunkter, der er forældede](manage-outdated-endpoints-microsoft-defender-antivirus.md)
- [Installationsvejledning til Microsoft Defender Antivirus et VDI-miljø (Virtual Desktop Infrastructure)](deployment-vdi-microsoft-defender-antivirus.md)

## <a name="opt-in-to-microsoft-update-on-mobile-computers-without-a-wsus-connection"></a>Tilmelde dig Microsoft Update på mobilenheder uden en WSUS-forbindelse

Du kan bruge Microsoft Update til at holde sikkerhedsintelligens på mobilenheder, der kører Microsoft Defender Antivirus opdateret, når de ikke har forbindelse til virksomhedens netværk eller ellers ikke har en WSUS-forbindelse.

Det betyder, at sikkerhedsopdateringer kan leveres til enheder (via Microsoft Update), også selvom du har indstillet WSUS til at tilsidesætte Microsoft Update.

Du kan tilmelde dig Microsoft Update på mobilenheden på en af følgende måder:

- Rediger indstillingen med Gruppepolitik.
- Brug et VBScript til at oprette et script, og kør det derefter på hver enkelt computer i netværket.
- Du kan manuelt tilmelde alle computere på dit netværk **via Indstillinger** netværksmenuen.

### <a name="use-group-policy-to-opt-in-to-microsoft-update"></a>Brug Gruppepolitik til at tilmelde dig Microsoft Update

1. På din Gruppepolitik administrationsmaskine skal du åbne [Gruppepolitik Administrationskonsol](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)), højreklikke på det Gruppepolitik objekt, du vil konfigurere, og vælge **Rediger**.

2. I Gruppepolitik **skal du** gå til **Computerkonfiguration**.

3. Vælg **Politikker** og derefter **Administrative skabeloner**.

4. Udvid træet for **at Windows komponenter** \> **Microsoft Defender Antivirus signaturopdateringer**\>.

5. Angiv **Tillad sikkerhedsintelligensopdateringer fra Microsoft Update** til **Aktiveret**, og vælg derefter  **OK**.

### <a name="use-a-vbscript-to-opt-in-to-microsoft-update"></a>Brug en VBScript til at tilmelde dig Microsoft Update

1. Følg vejledningen i [MSDN-artiklen Tilmeld dig Microsoft Update for](/windows/win32/wua_sdk/opt-in-to-microsoft-update) at oprette VBScript.

2. Kør det VBScript, du har oprettet på hver computer i netværket.

### <a name="manually-opt-in-to-microsoft-update"></a>Manuelt tilmelde dig Microsoft Update

1. Åbn **Windows Opdater** i **& sikkerhedsindstillinger** på den computer, du vil tilmelde dig.

2. Vælg **Avancerede** indstillinger.

3. Markér afkrydsningsfeltet for **Giv mig opdateringer til andre Microsoft-produkter, når jeg opdaterer Windows**.

## <a name="prevent-security-intelligence-updates-when-running-on-battery-power"></a>Undgå sikkerhedsintelligensopdateringer, når der køres på batteristrøm

Du kan konfigurere Microsoft Defender Antivirus til kun at hente beskyttelsesopdateringer, når pc'en er tilsluttet en kablet strømkilde.

### <a name="use-group-policy-to-prevent-security-intelligence-updates-on-battery-power"></a>Brug Gruppepolitik at forhindre sikkerhedsintelligensopdateringer på batteristrøm

1. På Gruppepolitik administrationsmaskine skal du åbne [Gruppepolitik administrationskonsollen](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)), vælge det Gruppepolitik objekt, du vil konfigurere, og åbne det til redigering.

2. I Gruppepolitik **skal du** gå til **Computerkonfiguration**.

3. Vælg **Politikker** og derefter **Administrative skabeloner**.

4. Udvid træet for at **Windows komponenter** \> **Microsoft Defender Antivirus** \> **signaturopdateringer**, og angiv derefter Tillad sikkerhedsvidensopdateringer, når der **kører på batteristrøm, til** **Deaktiveret**. Vælg derefter **OK**.

Denne handling forhindrer, at der downloades beskyttelsesopdateringer, når pc'en er på batteristrøm.

## <a name="related-articles"></a>Relaterede artikler

- [Administrere Microsoft Defender Antivirus opdateringer og anvende oprindelige planer](manage-updates-baselines-microsoft-defender-antivirus.md)
- [Opdater og administrer Microsoft Defender Antivirus i Windows 10](deploy-manage-report-microsoft-defender-antivirus.md)