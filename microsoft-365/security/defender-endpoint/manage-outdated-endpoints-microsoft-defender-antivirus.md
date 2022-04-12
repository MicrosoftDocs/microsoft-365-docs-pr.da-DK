---
title: Anvend opdateringer til Microsoft Defender AV Protection på forældede slutpunkter
description: Definer, hvornår og hvordan opdateringer skal anvendes for slutpunkter, der ikke er blevet opdateret i et stykke tid.
keywords: opdateringer, beskyttelse, forældet, forældet, gammel, indhente
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
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
ms.openlocfilehash: 0f7f42662bf698f6e3a092539e58a8a9de529b24
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/12/2022
ms.locfileid: "64789464"
---
# <a name="manage-microsoft-defender-antivirus-updates-and-scans-for-endpoints-that-are-out-of-date"></a>Administrer Microsoft Defender Antivirus opdateringer og scanninger for slutpunkter, der er forældede

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Antivirus

**Platforme**
- Windows

Microsoft Defender Antivirus giver dig mulighed for at definere, hvor længe et slutpunkt kan undgå en opdatering, eller hvor mange scanninger det kan gå glip af, før det er nødvendigt at opdatere og scanne sig selv. Dette er især nyttigt i miljøer, hvor enheder ikke ofte er forbundet til en virksomheds eller et eksternt netværk, eller enheder, der ikke bruges dagligt.

En medarbejder, der bruger en bestemt pc, er f.eks. på pause i tre dage og ikke logger på sin pc i den pågældende periode.

Når brugeren vender tilbage til arbejdet og logger på sin pc, kontrollerer og downloader Microsoft Defender Antivirus straks de seneste beskyttelsesopdateringer og kører en scanning.

## <a name="set-up-catch-up-protection-updates-for-endpoints-that-havent-updated-for-a-while"></a>Konfigurer opdateringer til registrering af beskyttelse for slutpunkter, der ikke er opdateret i et stykke tid

Hvis Microsoft Defender Antivirus ikke har downloadet beskyttelsesopdateringer for en bestemt periode, kan du konfigurere den til automatisk at kontrollere og downloade den seneste opdatering ved næste logon. Dette er nyttigt, hvis du [globalt har deaktiveret downloads af automatiske opdateringer ved start](manage-event-based-updates-microsoft-defender-antivirus.md).

### <a name="use-configuration-manager-to-configure-catch-up-protection-updates"></a>Brug Configuration Manager til at konfigurere opdateringer til opfanget beskyttelse

1. Åbn den antimalwarepolitik, du vil ændre, på din Microsoft Endpoint Manager konsol (klik på **Assets and Compliance** i navigationsruden til venstre, og udvid derefter træet til **Overview** \> **Endpoint Protection** \> **Antimalware Policies**)

2. Gå til afsnittet **Opdateringer til sikkerhedsintelligens** , og konfigurer følgende indstillinger:

    1. Angiv **Gennemtving en sikkerhedsintelligensopdatering, hvis klientcomputeren er offline i mere end to efterfølgende planlagte opdateringer** , til **Ja**.
    2. For **If Configuration Manager bruges som en kilde til sikkerhedsintelligensopdateringer...**, skal du angive, inden hvilke timer de beskyttelsesopdateringer, der leveres af Configuration Manager, skal anses for at være forældede. Dette medfører, at den næste opdateringsplacering bruges baseret på den definerede [reservekilderækkefølge](manage-protection-updates-microsoft-defender-antivirus.md#fallback-order).

3. Klik på **OK**.

4. [Installer den opdaterede politik som normalt](/sccm/protect/deploy-use/endpoint-antimalware-policies#deploy-an-antimalware-policy-to-client-computers).

### <a name="use-group-policy-to-enable-and-configure-the-catch-up-update-feature"></a>Brug Gruppepolitik til at aktivere og konfigurere funktionen til opfanging af opdateringer

1. Åbn [administrationskonsollen Gruppepolitik Gruppepolitik](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)), højreklik på det Gruppepolitik objekt, du vil konfigurere, og klik på **Rediger**.

2. Gå til **Computerkonfiguration** i **administrationseditoren Gruppepolitik**.

3. Klik på **Politikker** og derefter **Administrative skabeloner**.

4. Udvid træet for at **Windows komponenter > Microsoft Defender Antivirus > Signaturopdateringer**.

5. Dobbeltklik på indstillingen **Definer det antal dage, hvorefter der kræves en opdatering til sikkerhedsintelligens** , og angiv indstillingen til **Aktiveret**. Angiv det antal dage, hvorefter Microsoft Defender AV skal søge efter og downloade den seneste beskyttelsesopdatering.

6. Klik på **OK**.

### <a name="use-powershell-cmdlets-to-configure-catch-up-protection-updates"></a>Brug PowerShell-cmdlet'er til at konfigurere opdateringer til opfangningsbeskyttelse

Brug følgende cmdlet'er:

```PowerShell
Set-MpPreference -SignatureUpdateCatchupInterval
```

Se [Brug PowerShell-cmdlet'er til at konfigurere og køre Microsoft Defender Antivirus](use-powershell-cmdlets-microsoft-defender-antivirus.md)- og [Defender Antivirus-cmdlet'er](/powershell/module/defender/) for at få flere oplysninger om, hvordan du bruger PowerShell med Microsoft Defender Antivirus.

### <a name="use-windows-management-instruction-wmi-to-configure-catch-up-protection-updates"></a>Brug WMI (Windows Management Instruction) til at konfigurere opdateringer til opfanget beskyttelse

Brug [metoden **Set** for klassen **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) til følgende egenskaber:

```WMI
SignatureUpdateCatchupInterval
```

Se følgende for at få flere oplysninger og tilladte parametre:

- [Windows Defender WMIv2 API'er](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

## <a name="set-the-number-of-days-before-protection-is-reported-as-out-of-date"></a>Angiv antallet af dage, før beskyttelse rapporteres som forældet

Du kan også angive det antal dage, hvorefter Microsoft Defender Antivirus beskyttelse betragtes som gammel eller forældet. Efter det angivne antal dage rapporterer klienten sig selv som forældet og viser en fejl til brugeren af pc'en. Det kan også medføre, at Microsoft Defender Antivirus forsøger at downloade en opdatering fra andre kilder (baseret på den definerede [reservekilderækkefølge](manage-protection-updates-microsoft-defender-antivirus.md#fallback-order)), f.eks. når du bruger MMPC som sekundær kilde, efter at WSUS eller Microsoft Update er angivet som den første kilde.

### <a name="use-group-policy-to-specify-the-number-of-days-before-protection-is-considered-out-of-date"></a>Brug Gruppepolitik til at angive antallet af dage, før beskyttelse anses for at være forældet

1. Åbn [administrationskonsollen Gruppepolitik Gruppepolitik](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)), højreklik på det Gruppepolitik objekt, du vil konfigurere, og klik på **Rediger**.

2. Gå til **Computerkonfiguration** i **administrationseditoren Gruppepolitik**.

3. Klik på **Politikker** og derefter **Administrative skabeloner**.

4. Udvid træet for at **Windows komponenter > Microsoft Defender Antivirus > Signaturopdateringer**, og konfigurer følgende indstillinger:

    1. Dobbeltklik på **Definer antallet af dage, før spyware-definitioner anses for at være forældede** , og angiv indstillingen til **Aktiveret**. Angiv det antal dage, hvorefter Microsoft Defender AV skal betragte spyware Security Intelligence som forældet.

    2. Klik på **OK**.

    3. Dobbeltklik på **Definer antallet af dage, før virusdefinitioner anses for at være forældede** , og angiv indstillingen til **Aktiveret**. Angiv det antal dage, hvorefter Microsoft Defender AV skal betragte virussikkerhedsintelligens som forældet.

    4. Klik på **OK**.

## <a name="set-up-catch-up-scans-for-endpoints-that-have-not-been-scanned-for-a-while"></a>Konfigurer opsummeringsscanninger for slutpunkter, der ikke er blevet scannet i et stykke tid

Du kan angive antallet af efterfølgende planlagte scanninger, der kan gå glip af, før Microsoft Defender Antivirus gennemtvinger en scanning.

Processen til aktivering af denne funktion er:

1. Konfigurer mindst én planlagt scanning (se emnet [Planlæg scanninger](scheduled-catch-up-scans-microsoft-defender-antivirus.md) ).
2. Aktivér funktionen til opfangning af scanning.
3. Definer det antal scanninger, der kan springes over, før der opstår en opsummeringsscanning.

Denne funktion kan aktiveres for både komplette og hurtige scanninger.

### <a name="use-group-policy-to-enable-and-configure-the-catch-up-scan-feature"></a>Brug Gruppepolitik til at aktivere og konfigurere funktionen til opfangning af scanning

1. Sørg for, at du har konfigureret mindst én planlagt scanning.

2. Åbn [administrationskonsollen Gruppepolitik Gruppepolitik](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)), højreklik på det Gruppepolitik objekt, du vil konfigurere, og klik på **Rediger**.

3. Gå til **Computerkonfiguration** i **administrationseditoren Gruppepolitik**.

4. Klik på **Politikker** og derefter **Administrative skabeloner**.

5. Udvid træet for at **Windows komponenter > Microsoft Defender Antivirus > Scan**, og konfigurer følgende indstillinger:

    1. Hvis du har konfigureret planlagte hurtigscanninger, skal du dobbeltklikke på indstillingen **Slå hurtigsøgning** til og angive indstillingen til **Aktiveret**.
    2. Hvis du har konfigureret planlagte komplette scanninger, skal du dobbeltklikke på indstillingen **Aktivér indfangning af fuld scanning** og angive indstillingen til **Aktiveret**. Klik på **OK**.
    3. Dobbeltklik på indstillingen **Definer det antal dage, hvorefter en indfangningsscanning gennemtvinges** , og angiv indstillingen til **Aktiveret**.
    4. Angiv det antal scanninger, der kan gås glip af, før en scanning køres automatisk, når brugeren næste logger på pc'en. Den type scanning, der køres, bestemmes af emnet **Angiv den scanningstype, der skal bruges til en planlagt scanning** (se emnet [Planlæg scanninger](scheduled-catch-up-scans-microsoft-defender-antivirus.md) ). Klik på **OK**.

> [!NOTE]
> Den Gruppepolitik indstillingstitel refererer til antallet af dage. Indstillingen anvendes dog på antallet af scanninger (ikke dage), før indfangningsscanningen køres.

### <a name="use-powershell-cmdlets-to-configure-catch-up-scans"></a>Brug PowerShell-cmdlet'er til at konfigurere opfangningsscanninger

Brug følgende cmdlet'er:

```PowerShell
Set-MpPreference -DisableCatchupFullScan
Set-MpPreference -DisableCatchupQuickScan

```

Se [Brug PowerShell-cmdlet'er til at administrere Microsoft Defender Antivirus](use-powershell-cmdlets-microsoft-defender-antivirus.md)- og [Defender Antivirus-cmdlet'er](/powershell/module/defender/) for at få flere oplysninger om, hvordan du bruger PowerShell med Microsoft Defender Antivirus.

### <a name="use-windows-management-instruction-wmi-to-configure-catch-up-scans"></a>Brug WMI (Windows Management Instruction) til at konfigurere opfangningsscanninger

Brug [metoden **Set** for klassen **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) til følgende egenskaber:

```WMI
DisableCatchupFullScan
DisableCatchupQuickScan
```

Se følgende for at få flere oplysninger og tilladte parametre:

- [Windows Defender WMIv2 API'er](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

### <a name="use-configuration-manager-to-configure-catch-up-scans"></a>Brug Configuration Manager til at konfigurere opfangningsscanninger

1. Åbn den antimalwarepolitik, du vil ændre, på din Microsoft Endpoint Manager konsol (klik på **Assets and Compliance** i navigationsruden til venstre, og udvid derefter træet til **Overview** \> **Endpoint Protection** \> **Antimalware Policies**)

2. Gå til afsnittet **Planlagte scanninger** og **Gennemtving en scanning af den valgte scanningstype, hvis klientcomputeren er offline...** til **Ja**.

3. Klik på **OK**.

4. [Installer den opdaterede politik som normalt](/sccm/protect/deploy-use/endpoint-antimalware-policies#deploy-an-antimalware-policy-to-client-computers).

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

- [Installer Microsoft Defender Antivirus](deploy-manage-report-microsoft-defender-antivirus.md)
- [Administrer Microsoft Defender Antivirus opdateringer, og anvend oprindelige planer](manage-updates-baselines-microsoft-defender-antivirus.md)
- [Administrer, hvornår beskyttelsesopdateringer skal downloades og anvendes](manage-protection-update-schedule-microsoft-defender-antivirus.md)
- [Administrer begivenhedsbaserede gennemtvungne opdateringer](manage-event-based-updates-microsoft-defender-antivirus.md)
- [Administrer opdateringer til mobilenheder og virtuelle maskiner (VMs)](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)
- [Microsoft Defender Antivirus i Windows 10](microsoft-defender-antivirus-in-windows-10.md)
