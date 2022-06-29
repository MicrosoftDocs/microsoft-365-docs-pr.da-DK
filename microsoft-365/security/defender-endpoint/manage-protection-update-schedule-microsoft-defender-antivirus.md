---
title: Planlæg opdateringer til Microsoft Defender Antivirus-beskyttelse
description: Planlæg dag, klokkeslæt og interval for, hvornår beskyttelsesopdateringer skal downloades
keywords: opdateringer, grundlæggende sikkerhedsopdateringer, planlægningsopdateringer
ms.prod: m365-security
search.appverid: met150
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: pahuijbr
manager: dansimp
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: 35f9329756fde82a6ac0762d30041a3d30cd2c8b
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/29/2022
ms.locfileid: "66492463"
---
# <a name="manage-the-schedule-for-when-protection-updates-should-be-downloaded-and-applied"></a>Administrer tidsplanen for, hvornår beskyttelsesopdateringer skal downloades og anvendes

> [!IMPORTANT]
> Kunder, der anvendte opdateringen til Microsoft Defender-programmet fra marts 2022 (**1.1.19100.5**), kan have oplevet høj ressourceudnyttelse (CPU og/eller hukommelse). Microsoft har udgivet en opdatering (**1.1.19200.5**), der løser de fejl, der blev introduceret i den tidligere version. Kunder anbefales at opdatere til denne nye motor build af Antivirus Engine (**1.1.19200.5**). Hvis du vil sikre, at eventuelle problemer med ydeevnen er fuldt løst, anbefales det at genstarte maskiner efter anvendelse af opdatering. Du kan få flere oplysninger under [Månedlige platform- og programversioner](manage-updates-baselines-microsoft-defender-antivirus.md#monthly-platform-and-engine-versions).

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Antivirus

**Platforme**
- Windows

Med Microsoft Defender Antivirus kan du afgøre, hvornår den skal søge efter og downloade opdateringer.

Du kan planlægge opdateringer for dine slutpunkter ved at:

- Angivelse af den ugedag, hvor der skal søges efter beskyttelsesopdateringer
- Angivelse af det interval, der skal kontrolleres for beskyttelsesopdateringer
- Angivelse af det tidspunkt, hvor det skal kontrolleres, om der er opdateringer til beskyttelse

Du kan også randomisere de tidspunkter, hvor hvert slutpunkt kontrollerer og downloader beskyttelsesopdateringer. Se emnet [Planlæg scanninger](scheduled-catch-up-scans-microsoft-defender-antivirus.md) for at få flere oplysninger.

## <a name="use-configuration-manager-to-schedule-protection-updates"></a>Brug Configuration Manager til at planlægge beskyttelsesopdateringer

1. Åbn den antimalwarepolitik, du vil ændre, i Microsoft Endpoint Manager-konsollen (klik på **Assets and Compliance** i navigationsruden til venstre, og udvid derefter træet til **Overview** \> **Endpoint Protection** \> **Antimalware Policies**)

2. Gå til afsnittet **Opdateringer til sikkerhedsintelligens** .

3. Sådan kontrollerer og downloader du opdateringer på et bestemt tidspunkt:
      1. Angiv **Kontrollér for Endpoint Protection-sikkerhedsintelligensopdateringer med et bestemt interval...** til **0**.
      2. Angiv **Kontrollér for Endpoint Protection security intelligence-opdateringer dagligt på...** til det tidspunkt, hvor opdateringer skal kontrolleres.
      3
4. Hvis du vil kontrollere og downloade opdateringer i et løbende interval, skal du angive **Kontrollér for Sikkerhedsintelligensopdateringer for Endpoint Protection med et bestemt interval...** til det antal timer, der skal forekomme mellem opdateringer.

5. [Installer den opdaterede politik som normalt](/sccm/protect/deploy-use/endpoint-antimalware-policies#deploy-an-antimalware-policy-to-client-computers).

## <a name="use-group-policy-to-schedule-protection-updates"></a>Brug Gruppepolitik til at planlægge beskyttelsesopdateringer

> [!IMPORTANT]
> Som standard er "SignatureScheduleDay" angivet som "8", og "SignatureUpdateInterval" er angivet som "0", så Microsoft Defender Antivirus planlægger ikke beskyttelsesopdateringer.
Aktivering af disse indstillinger tilsidesætter denne standardindstilling.

1. Åbn [administrationskonsollen Gruppepolitik Gruppepolitik](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)), højreklik på det Gruppepolitik objekt, du vil konfigurere, og klik på **Rediger**.

2. Gå til **Computerkonfiguration** i **administrationseditoren Gruppepolitik**.

3. Klik på **Politikker** og derefter **Administrative skabeloner**.

4. Udvid træet til **Windows-komponenter** \> \> **Windows Defender Antivirus** **Signature Opdateringer** og konfigurer følgende indstillinger:

    1. Dobbeltklik på indstillingen **Angiv den ugedag, hvor der skal søges efter opdateringer til sikkerhedsintelligens** , og angiv indstillingen til **Aktiveret**. Angiv den ugedag, hvor der skal søges efter opdateringer. Klik på **OK**.

    2. Dobbeltklik på indstillingen **Angiv det interval, der skal kontrolleres for definitionsopdateringer** , og angiv indstillingen til **Aktiveret**. Angiv antallet af timer mellem opdateringer. Klik på **OK**.

    3. Dobbeltklik på indstillingen **Angiv det tidspunkt, hvor der skal søges efter definitionsopdateringer** , og angiv indstillingen til **Aktiveret**. Angiv det tidspunkt, hvor opdateringer skal kontrolleres. Klokkeslættet er baseret på slutpunktets lokale klokkeslæt. Klik på **OK**.

## <a name="use-powershell-cmdlets-to-schedule-protection-updates"></a>Brug PowerShell-cmdlet'er til at planlægge beskyttelsesopdateringer

Brug følgende cmdlet'er:

```PowerShell
Set-MpPreference -SignatureScheduleDay
Set-MpPreference -SignatureScheduleTime
Set-MpPreference -SignatureUpdateInterval
```

Se [Brug PowerShell-cmdlet'er til at konfigurere og køre Microsoft Defender Antivirus](use-powershell-cmdlets-microsoft-defender-antivirus.md)  - og [Defender Antivirus-cmdlet'er](/powershell/module/defender/) for at få flere oplysninger om, hvordan du bruger PowerShell med Microsoft Defender Antivirus.

## <a name="use-windows-management-instruction-wmi-to-schedule-protection-updates"></a>Brug WMI (Windows Management Instruction) til at planlægge beskyttelsesopdateringer

Brug [metoden **Set** for klassen **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) til følgende egenskaber:

```WMI
SignatureScheduleDay
SignatureScheduleTime
SignatureUpdateInterval
```

Se følgende for at få flere oplysninger og tilladte parametre:

- [Windows Defender WMIv2 API'er](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

> [!TIP]
> Hvis du leder efter antivirusrelaterede oplysninger til andre platforme, skal du se:
> - [Angiv indstillinger for Microsoft Defender for Endpoint på macOS-](mac-preferences.md)
> - [Microsoft Defender for Endpoint på Mac](microsoft-defender-endpoint-mac.md)
> - [Politikindstillinger for macOS Antivirus for Microsoft Defender Antivirus for Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Konfigurer Microsoft Defender for Endpoint på iOS-funktioner](ios-configure-features.md)
> - [Konfigurer Defender for Endpoint på Android-funktioner](android-configure.md)
> - [Angiv indstillinger for Microsoft Defender for Endpoint på Linux](linux-preferences.md)
> - [Microsoft Defender for Endpoint på Linux](microsoft-defender-endpoint-linux.md)

## <a name="related-articles"></a>Relaterede artikler

- [Installér Microsoft Defender Antivirus](deploy-manage-report-microsoft-defender-antivirus.md)
- [Administrer Opdateringer til Microsoft Defender Antivirus, og anvend grundlinjer](manage-updates-baselines-microsoft-defender-antivirus.md)
- [Administrer opdateringer for slutpunkter, der er forældede](manage-outdated-endpoints-microsoft-defender-antivirus.md)
- [Administrer begivenhedsbaserede gennemtvungne opdateringer](manage-event-based-updates-microsoft-defender-antivirus.md)
- [Administrer opdateringer til mobilenheder og virtuelle maskiner (VMs)](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)
- [Microsoft Defender Antivirus i Windows 10 og 11](microsoft-defender-antivirus-in-windows-10.md)
