---
title: Anvend opdateringer til Microsoft Defender AV-beskyttelse på forældede slutpunkter
description: Definer, hvornår og hvordan opdateringer skal anvendes for slutpunkter, der ikke er opdateret i et stykke tid.
keywords: opdateringer, beskyttelse, forældede, forældede, gamle, seneste opdateringer
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
ms.openlocfilehash: a708bf6ef34767b338c40cf8004e4c497658fc36
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2021
ms.locfileid: "63593823"
---
# <a name="manage-microsoft-defender-antivirus-updates-and-scans-for-endpoints-that-are-out-of-date"></a>Administrere Microsoft Defender Antivirus opdateringer og scanninger for slutpunkter, der er forældede

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Microsoft Defender Antivirus kan du definere, hvor lang tid et slutpunkt kan undgå en opdatering, eller hvor mange scanninger det kan overse, før det er nødvendigt at opdatere og scanne sig selv. Dette er især nyttigt i miljøer, hvor enheder ikke ofte har forbindelse til virksomhedens eller eksterne netværk eller enheder, der ikke bruges dagligt.

En medarbejder, der bruger en bestemt pc, er f.eks. på pause i tre dage og logger ikke på sin pc i den periode.

Når brugeren vender tilbage til arbejde og logger på sin pc, søger Microsoft Defender Antivirus straks efter og downloader de nyeste opdateringer til beskyttelse, og kører en scanning.

## <a name="set-up-catch-up-protection-updates-for-endpoints-that-havent-updated-for-a-while"></a>Konfigurere opdateringer til catch-up-beskyttelse for slutpunkter, der ikke er opdateret i et stykke tid

Hvis Microsoft Defender Antivirus har hentet beskyttelsesopdateringer i en bestemt periode, kan du konfigurere den til automatisk at kontrollere og hente den seneste opdatering ved næste logon. Dette er nyttigt, hvis du [har globalt deaktiveret downloads af automatiske opdateringer ved start](manage-event-based-updates-microsoft-defender-antivirus.md).

### <a name="use-configuration-manager-to-configure-catch-up-protection-updates"></a>Brug Konfigurationsstyring til at konfigurere opdateringer til beskyttelse af oplysninger

1. På din Microsoft Endpoint Manager-konsol skal du åbne den antimalwarepolitik, du vil ændre (klik på  Aktiver og overholdelse af regler og standarder i navigationsruden til venstre,  \> og udvid derefter træet til Oversigt **Endpoint Protection** \> **Antimalwarepolitikker**)

2. Gå til sektionen **Sikkerhedsintelligensopdateringer** , og konfigurer følgende indstillinger:

    1. Angiv **Gennemtving en sikkerhedsintelligensopdatering, hvis klientcomputeren er offline i mere end to fortløbende planlagte opdateringer** til **Ja**.
    2. Ud for  **hvis Konfigurationsstyring** bruges som en kilde til sikkerhedsintelligensopdateringer..., skal du angive de timer, før de sikkerhedsopdateringer, der leveres af Konfigurationsstyring, skal betragtes som forældede. Dette medfører, at den næste opdateringsplacering bruges baseret på den definerede [fallback-kilderækkefølge](manage-protection-updates-microsoft-defender-antivirus.md#fallback-order).

3. Klik på **OK**.

4. [Installér den opdaterede politik som normalt](/sccm/protect/deploy-use/endpoint-antimalware-policies#deploy-an-antimalware-policy-to-client-computers).

### <a name="use-group-policy-to-enable-and-configure-the-catch-up-update-feature"></a>Brug Gruppepolitik til at aktivere og konfigurere funktionen til opdatering af opdateringer

1. På Gruppepolitik administrationscomputer skal du åbne Gruppepolitik [Administrationskonsol](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)), højreklikke på det Gruppepolitik objekt, du vil konfigurere, og klikke på **Rediger**.

2. I Gruppepolitik **skal du** gå til **Computerkonfiguration**.

3. Klik **på Politikker** og **derefter på Administrative skabeloner**.

4. Udvid træet for **at Windows komponenter > Microsoft Defender Antivirus > signaturopdateringer**.

5. Dobbeltklik på indstillingen **Definer det antal** dage, efter hvilken en sikkerhedsintelligensopdatering er påkrævet, og angiv indstillingen til **Aktiveret**. Angiv det antal dage, efter hvilken Microsoft Defender AV skal søge efter, og download den seneste opdatering til beskyttelse.

6. Klik på **OK**.

### <a name="use-powershell-cmdlets-to-configure-catch-up-protection-updates"></a>Brug PowerShell-cmdlet'er til at konfigurere opdateringer til catch-up-beskyttelse

Brug følgende cmdlet'er:

```PowerShell
Set-MpPreference -SignatureUpdateCatchupInterval
```

Se [Brug PowerShell-cmdlet'er](use-powershell-cmdlets-microsoft-defender-antivirus.md) til at konfigurere og køre Microsoft Defender Antivirus- og [Defender Antivirus-cmdlet'er](/powershell/module/defender/) for at få mere at vide om, hvordan du bruger PowerShell Microsoft Defender Antivirus.

### <a name="use-windows-management-instruction-wmi-to-configure-catch-up-protection-updates"></a>Brug Windows (WMI) til at konfigurere opdateringer til catch-up-beskyttelse

Brug [**metoden Angiv** for **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) til følgende egenskaber:

```WMI
SignatureUpdateCatchupInterval
```

Se følgende for at få flere oplysninger og tilladte parametre:

- [Windows Defender WMIv2-API'er](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

## <a name="set-the-number-of-days-before-protection-is-reported-as-out-of-date"></a>Angiv antallet af dage, før beskyttelsen rapporteres som forældet

Du kan også angive antallet af dage, Microsoft Defender Antivirus beskyttelse betragtes som gammel eller forældet. Efter det angivne antal dage rapporterer klienten sig selv som forældet og viser en fejl til brugeren af pc'en. Det kan også medføre Microsoft Defender Antivirus forsøger at hente en opdatering fra andre kilder (baseret på den definerede [fallback-kilderækkefølge](manage-protection-updates-microsoft-defender-antivirus.md#fallback-order)), f.eks. når du bruger MMPC som en sekundær kilde efter indstilling af WSUS eller Microsoft Update som den første kilde.

### <a name="use-group-policy-to-specify-the-number-of-days-before-protection-is-considered-out-of-date"></a>Brug Gruppepolitik til at angive, hvor mange dage før beskyttelsen betragtes som forældet

1. På din Gruppepolitik administrationsmaskine skal du åbne [Gruppepolitik Administrationskonsol](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)), højreklikke på det Gruppepolitik objekt, du vil konfigurere, og klikke på **Rediger**.

2. I Gruppepolitik **skal du** gå til **Computerkonfiguration**.

3. Klik **på Politikker** og **derefter på Administrative skabeloner**.

4. Udvid træet for **at Windows komponenter > Microsoft Defender Antivirus > signaturopdateringer**, og konfigurer følgende indstillinger:

    1. Dobbeltklik på **Definer antallet af dage, før spywaredefinitioner betragtes som forældede, og** angiv indstillingen til **Aktiveret**. Angiv det antal dage, efter du ønsker, at Microsoft Defender AV skal overveje, at spywareSikkerhedsintelligens er forældet.

    2. Klik på **OK**.

    3. Dobbeltklik på **Definer antallet af dage, før virusdefinitioner opfattes som forældede, og** angiv indstillingen til **Aktiveret**. Angiv det antal dage, hvorefter Microsoft Defender AV skal overveje, at virussikkerhedsintelligens skal være forældede.

    4. Klik på **OK**.

## <a name="set-up-catch-up-scans-for-endpoints-that-have-not-been-scanned-for-a-while"></a>Konfigurere indfangningsscanninger for slutpunkter, der ikke er scannet i et stykke tid

Du kan angive antallet af efterfølgende planlagte scanninger, der kan overse, Microsoft Defender Antivirus efterfølgende vil gennemtvinge en scanning.

Processen for aktivering af denne funktion er:

1. Konfigurer mindst én planlagt scanning (se emnet [Planlægge scanninger](scheduled-catch-up-scans-microsoft-defender-antivirus.md) ).
2. Aktivér funktionen til indfangning af scanning.
3. Definer antallet af scanninger, der kan springes over, før en opscanning finder sted.

Denne funktion kan aktiveres for både fulde og hurtige scanninger.

### <a name="use-group-policy-to-enable-and-configure-the-catch-up-scan-feature"></a>Brug Gruppepolitik til at aktivere og konfigurere funktionen til scanning af indfangning

1. Sørg for, at du har konfigureret mindst én planlagt scanning.

2. På din Gruppepolitik administrationsmaskine skal du åbne [Gruppepolitik Administrationskonsol](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)), højreklikke på det Gruppepolitik objekt, du vil konfigurere, og klikke på **Rediger**.

3. I Gruppepolitik **skal du** gå til **Computerkonfiguration**.

4. Klik **på Politikker** og **derefter på Administrative skabeloner**.

5. Udvid træet for **Windows komponenter > Microsoft Defender Antivirus > Scan**, og konfigurer følgende indstillinger:

    1. Hvis du har konfigureret planlagte hurtige scanninger, skal du dobbeltklikke  på indstillingen Slå hurtig scanning til og angive indstillingen til **Aktiveret**.
    2. Hvis du har konfigureret planlagte fulde scanninger, skal du dobbeltklikke  på indstillingen Slå fuld scanning til og angive indstillingen til **Aktiveret**. Klik på **OK**.
    3. Dobbeltklik på indstillingen **Definer det antal** dage, en opscanning er gennemtvunget, og angiv indstillingen til **Aktiveret**.
    4. Angiv antallet af scanninger, der kan gå glip af, før en scanning køres automatisk, når brugeren næste gang logger på pc'en. Typen af scanning, der køres, bestemmes af Angiv den scanningstype, der skal bruges til en planlagt **scanning (se** emnet [Tidsplan for scanninger](scheduled-catch-up-scans-microsoft-defender-antivirus.md) ). Klik på **OK**.

> [!NOTE]
> Titlen Gruppepolitik indstilling henviser til antallet af dage. Indstillingen anvendes dog på antallet af scanninger (ikke dage), før indfangningsscanningen skal køres.

### <a name="use-powershell-cmdlets-to-configure-catch-up-scans"></a>Brug PowerShell-cmdlet'er til at konfigurere indfangningsscanninger

Brug følgende cmdlet'er:

```PowerShell
Set-MpPreference -DisableCatchupFullScan
Set-MpPreference -DisableCatchupQuickScan

```

Se [Brug PowerShell-cmdlet'er](use-powershell-cmdlets-microsoft-defender-antivirus.md) til at administrere Microsoft Defender Antivirus[- og Defender Antivirus-cmdlet'er](/powershell/module/defender/) for at få mere at vide om, hvordan du bruger PowerShell Microsoft Defender Antivirus.

### <a name="use-windows-management-instruction-wmi-to-configure-catch-up-scans"></a>Brug Windows administrationsvejledning (WMI) til konfiguration af opsnævningsscanninger

Brug [**metoden Angiv** for **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) til følgende egenskaber:

```WMI
DisableCatchupFullScan
DisableCatchupQuickScan
```

Se følgende for at få flere oplysninger og tilladte parametre:

- [Windows Defender WMIv2-API'er](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

### <a name="use-configuration-manager-to-configure-catch-up-scans"></a>Brug Konfigurationsstyring til at konfigurere indfangningsscanninger

1. På din Microsoft Endpoint Manager-konsol skal du åbne den antimalwarepolitik, du vil ændre (klik på  Aktiver og overholdelse af regler og standarder i navigationsruden til venstre,  \> og udvid derefter træet til Oversigt **Endpoint Protection** \> **Antimalwarepolitikker**)

2. Gå til sektionen **Planlagte scanninger** , og **gennemtving en scanning af den valgte scanningstype, hvis klientcomputeren er offline...** til **Ja**.

3. Klik på **OK**.

4. [Installér den opdaterede politik som normalt](/sccm/protect/deploy-use/endpoint-antimalware-policies#deploy-an-antimalware-policy-to-client-computers).

## <a name="related-articles"></a>Relaterede artikler

- [Installér Microsoft Defender Antivirus](deploy-manage-report-microsoft-defender-antivirus.md)
- [Administrere Microsoft Defender Antivirus opdateringer og anvende oprindelige planer](manage-updates-baselines-microsoft-defender-antivirus.md)
- [Administrer, hvornår sikkerhedsopdateringer skal downloades og anvendes](manage-protection-update-schedule-microsoft-defender-antivirus.md)
- [Administrer begivenhedsbaserede gennemtvungne opdateringer](manage-event-based-updates-microsoft-defender-antivirus.md)
- [Administrer opdateringer til mobilenheder og virtuelle maskiner (VMs)](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)
- [Microsoft Defender Antivirus i Windows 10](microsoft-defender-antivirus-in-windows-10.md)
