---
title: Planlæg Microsoft Defender Antivirus opdateringer til beskyttelse
description: Planlæg dag, klokkeslæt og interval for, hvornår der skal downloades beskyttelsesopdateringer
keywords: opdateringer, grundlinjer for sikkerhed, planlæg opdateringer
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
ms.openlocfilehash: fa67ff12ecfc2fb97bbc50642a5d7db99df91819
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2021
ms.locfileid: "63597883"
---
# <a name="manage-the-schedule-for-when-protection-updates-should-be-downloaded-and-applied"></a>Administrer tidsplanen for, hvornår beskyttelsesopdateringer skal downloades og anvendes

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Microsoft Defender Antivirus gør det muligt at bestemme, hvornår den skal søge efter og hente opdateringer.

Du kan planlægge opdateringer for dine slutpunkter ved at:

- Angivelse af ugedagen, hvor der skal søges efter sikkerhedsopdateringer
- Angivelse af intervallet, der skal søges efter sikkerhedsopdateringer
- Angive tiden, der skal søges efter sikkerhedsopdateringer

Du kan også tilfældigt se de tidspunkter, hvor hvert slutpunkt kontrollerer og downloader beskyttelsesopdateringer. Se emnet [Planlæg scanninger](scheduled-catch-up-scans-microsoft-defender-antivirus.md) for at få mere at vide.

## <a name="use-configuration-manager-to-schedule-protection-updates"></a>Brug Konfigurationsstyring til at planlægge opdateringer til beskyttelse

1. På din Microsoft Endpoint Manager-konsol skal du åbne den antimalwarepolitik, du vil ændre (klik på  Aktiver og overholdelse af regler og standarder i navigationsruden til venstre,  \> og udvid derefter træet til Oversigt **Endpoint Protection** \> **Antimalwarepolitikker**)

2. Gå til afsnittet **Sikkerhedsintelligensopdateringer** .

3. Sådan kontrollerer og henter du opdateringer på et bestemt tidspunkt:
      1. Angiv **Søg efter Endpoint Protection sikkerhedsintelligensopdateringer i et bestemt interval ...** **til 0**.
      2. **Indstil Kontrollér, Endpoint Protection sikkerhedsoplysninger opdateres dagligt på ...** til det tidspunkt, hvor opdateringer skal kontrolleres.
      3
4. For at kontrollere og hente opdateringer på et løbende interval skal du Angive Kontrollér **, om Endpoint Protection** sikkerhedsintelligensopdateringer med et bestemt interval ... til det antal timer, der bør forekomme mellem opdateringer.

5. [Installér den opdaterede politik som normalt](/sccm/protect/deploy-use/endpoint-antimalware-policies#deploy-an-antimalware-policy-to-client-computers).

## <a name="use-group-policy-to-schedule-protection-updates"></a>Brug Gruppepolitik til at planlægge opdateringer til beskyttelse

> [!IMPORTANT]
> Som standard søger Microsoft Defender Antivirus efter en opdatering 15 minutter før tidspunktet for eventuelle planlagte scanninger. Aktivering af disse indstillinger tilsidesætter denne standard.

1. På din Gruppepolitik administrationsmaskine skal du åbne [Gruppepolitik Administrationskonsol](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)), højreklikke på det Gruppepolitik objekt, du vil konfigurere, og klikke på **Rediger**.

2. I Gruppepolitik **skal du** gå til **Computerkonfiguration**.

3. Klik **på Politikker** og **derefter på Administrative skabeloner**.

4. Udvid træet for **at Windows komponenter** \> **Microsoft Defender Antivirus** \> **Signature Intelligence-opdateringer**, og konfigurer følgende indstillinger:

    1. Dobbeltklik på indstillingen **Angiv ugedagen for at se, om der er sikkerhedsintelligensopdateringer** , og angiv indstillingen til **Aktiveret**. Angiv ugedagen for at søge efter opdateringer. Klik på **OK**.
    2. Dobbeltklik på indstillingen Angiv **intervallet for at søge efter sikkerhedsintelligensopdateringer** , og angiv indstillingen til **Aktiveret**. Angiv antallet af timer mellem opdateringer. Klik på **OK**.
    3. Dobbeltklik på indstillingen Angiv **tidspunktet for kontrol af sikkerhedsintelligensopdateringer** , og angiv indstillingen til **Aktiveret**. Angiv det tidspunkt, hvor opdateringerne skal kontrolleres. Klokkeslætet er baseret på slutpunkts lokale klokkeslæt. Klik på **OK**.

## <a name="use-powershell-cmdlets-to-schedule-protection-updates"></a>Brug PowerShell-cmdlet'er til at planlægge sikkerhedsopdateringer

Brug følgende cmdlet'er:

```PowerShell
Set-MpPreference -SignatureScheduleDay
Set-MpPreference -SignatureScheduleTime
Set-MpPreference -SignatureUpdateInterval
```

Se [Brug PowerShell-cmdlet'er](use-powershell-cmdlets-microsoft-defender-antivirus.md) til at konfigurere og køre Microsoft Defender Antivirus- og [Defender Antivirus-cmdlet'er](/powershell/module/defender/) for at få mere at vide om, hvordan du bruger PowerShell Microsoft Defender Antivirus.

## <a name="use-windows-management-instruction-wmi-to-schedule-protection-updates"></a>Brug Windows (WMI) til planlægning af sikkerhedsopdateringer

Brug [**metoden Angiv** for **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) til følgende egenskaber:

```WMI
SignatureScheduleDay
SignatureScheduleTime
SignatureUpdateInterval
```

Se følgende for at få flere oplysninger og tilladte parametre:

- [Windows Defender WMIv2-API'er](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

## <a name="related-articles"></a>Relaterede artikler

- [Installér Microsoft Defender Antivirus](deploy-manage-report-microsoft-defender-antivirus.md)
- [Administrere Microsoft Defender Antivirus opdateringer og anvende oprindelige planer](manage-updates-baselines-microsoft-defender-antivirus.md)
- [Administrere opdateringer for slutpunkter, der er forældede](manage-outdated-endpoints-microsoft-defender-antivirus.md)
- [Administrer begivenhedsbaserede gennemtvungne opdateringer](manage-event-based-updates-microsoft-defender-antivirus.md)
- [Administrer opdateringer til mobilenheder og virtuelle maskiner (VMs)](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)
- [Microsoft Defender Antivirus i Windows 10](microsoft-defender-antivirus-in-windows-10.md)
