---
title: Microsoft Defender Offline i Windows
description: Du kan bruge Microsoft Defender Offline direkte fra Windows Defender Antivirus app. Du kan også administrere, hvordan det installeres i dit netværk.
keywords: scan, defender, offline
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.topic: article
ms.collection: M365-security-compliance
ms.openlocfilehash: ccb65b865afdf2a0ec0210c3593daee1cb5c09b6
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64476835"
---
# <a name="run-and-review-the-results-of-a-microsoft-defender-offline-scan"></a>Kør og gennemse resultaterne af en Microsoft Defender Offline scanning

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Microsoft Defender Offline er et scanningsværktøj til antimalware, der gør det muligt at starte og køre en scanning fra et sikkert miljø. Scanningen kører uden for den normale Windows-kerne, så den kan målrette malware, der forsøger at omgå Windows-shellen, f.eks. virus og rootkits, der inficerer eller overskriver MASTER boot-posten (MBR).

Du kan bruge Microsoft Defender Offline hvis du har mistanke om malware inficeret, eller du vil bekræfte en grundig oprydning af slutpunktet efter et malwareudbrud.

I Windows 10 og Windows 11 kan Microsoft Defender Offline køres med ét klik direkte [fra Windows Sikkerhed app](microsoft-defender-security-center-antivirus.md). I tidligere versioner af Windows skulle en bruger installere Microsoft Defender Offline til startbare medier, genstarte slutpunktet og indlæse de opstartbare medier.

## <a name="prerequisites-and-requirements"></a>forudsætninger og krav

Microsoft Defender Offline i Windows 10 og Windows 11 har de samme hardwarekrav som Windows 10.

Du kan finde flere Windows 10 og Windows 11 i følgende emner:

- [Minimumskrav til hardware](/windows-hardware/design/minimum/minimum-hardware-requirements-overview)

- [Retningslinjer for hardwarekomponenter](/windows-hardware/design/component-guidelines/components)

> [!NOTE]
> Microsoft Defender Offline ikke på maskiner med ARM eller processorer på Windows Server Stock Keeping Units.

For at Microsoft Defender Offline fra slutpunktet skal brugeren være logget på med administratorrettigheder.

## <a name="microsoft-defender-offline-updates"></a>Microsoft Defender Offline opdateringer

Microsoft Defender Offline bruger de nyeste sikkerhedsopdateringer, der er tilgængelige på slutpunktet. De opdateres, når Windows Defender Antivirus opdateres.

> [!NOTE]
> Før du kører en offline-scanning, skal du forsøge at opdatere Microsoft Defender AV-beskyttelse. Du kan enten gennemtvinge en opdatering med Gruppepolitik, eller hvordan du normalt installerer opdateringer på slutpunkter, eller du kan manuelt downloade og installere de nyeste sikkerhedsopdateringer [fra Microsoft Malware Protection Center](https://www.microsoft.com/security/portal/definitions/adl.aspx).

Se emnet [Administrer Microsoft Defender Antivirus security intelligence-opdateringer](manage-protection-updates-microsoft-defender-antivirus.md) for at få flere oplysninger.

## <a name="usage-scenarios"></a>Anvendelsesscenarier

I Windows 10 version 1607 kan du manuelt gennemtvinge en offlinescanning. Alternativt, hvis Windows Defender finder ud af, Microsoft Defender Offline skal køre, bliver brugeren bedt om at køre på slutpunktet.

Behovet for at udføre en offline scanning vil også blive afsløret i Microsoft Endpoint Manager, hvis du bruger den til at administrere dine slutpunkter.

Prompten kan forekomme via en meddelelse, der minder om følgende:

:::image type="content" source="../../media/notification.png" alt-text="Meddelelse om at køre Microsoft Defender Offline" lightbox="../../media/notification.png":::

Brugeren får også besked i Windows Defender klient.

I Configuration Manager kan du identificere status for slutpunkter ved at gå til **Overvågningsoversigt > > Sikkerhedsstatus > Endpoint Protection status > System Center Endpoint Protection Status**.

Microsoft Defender Offline er angivet under Status **for afhjælpning af malware som** **påkrævet offlinescanning**.

:::image type="content" source="../../media/sccm-wdo.png" alt-text="Indikatoren for en scanning af Microsoft Defender Offline" lightbox="../../media/sccm-wdo.png":::

## <a name="configure-notifications"></a>Konfigurer meddelelser

Microsoft Defender Offline meddelelser er konfigureret i den samme politikindstilling som andre Microsoft Defender AV-meddelelser.

Du kan finde flere oplysninger Windows Defender meddelelser i Windows Defender [i emnet Konfigurer de meddelelser, der vises på slutpunkter](configure-notifications-microsoft-defender-antivirus.md).

## <a name="run-a-scan"></a>Kør en scanning

> [!IMPORTANT]
> Før du bruger Microsoft Defender Offline, skal du sørge for at gemme alle filer og lukke kørende programmer. Det Microsoft Defender Offline 15 minutter at køre scanningen. Det genstarter slutpunktet, når scanningen er fuldført. Scanningen udføres uden for det sædvanlige Windows i driftsmiljøet. Brugergrænsefladen ser anderledes ud end en normal scanning, der udføres ved Windows Defender. Når scanningen er fuldført, genstartes slutpunktet, og Windows indlæses normalt.

Du kan køre en Microsoft Defender Offline scanning med følgende:

- PowerShell
- Windows WMI (Management Instrumentation)
- Den Windows Sikkerhed app



### <a name="use-powershell-cmdlets-to-run-an-offline-scan"></a>Brug PowerShell-cmdlet'er til at køre en offlinescanning

Brug følgende cmdlet'er:

```PowerShell
Start-MpWDOScan
```

Se [Brug PowerShell-cmdlet'er](use-powershell-cmdlets-microsoft-defender-antivirus.md) til at konfigurere og køre Microsoft Defender Antivirus- og [Defender Antivirus-cmdlet'er](/powershell/module/defender/) for at få mere at vide om, hvordan du bruger PowerShell Microsoft Defender Antivirus.

### <a name="use-windows-management-instruction-wmi-to-run-an-offline-scan"></a>Brug Windows (WMI) til at køre en offlinescanning

Brug klassen [**MSFT_MpWDOScan**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) til at køre en offlinescanning.

Følgende WMI-scriptstykke kører straks en Microsoft Defender Offline-scanning, hvilket får slutpunktet til at genstarte, køre offlinescanningen og derefter genstarte og starte Windows.

```console
wmic /namespace:\\root\Microsoft\Windows\Defender path MSFT_MpWDOScan call Start
```

Se følgende for at få flere oplysninger:

- [Windows Defender WMIv2-API'er](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

### <a name="use-the-windows-defender-security-app-to-run-an-offline-scan"></a>Brug appen Windows Defender til at køre en offlinescanning

1. Åbn Windows Sikkerhed-appen ved at klikke på skjoldet på proceslinjen eller søge i startmenuen efter **Defender for Cloud**.

2. Klik på **feltet & for trusselsbeskyttelse** (eller skjoldikonet på den venstre menulinje) og derefter på **etiketten Avanceret** scanning:

3. Vælg **Microsoft Defender Offline scanningen,** og klik på **Scan nu**.

    > [!NOTE]
    > I Windows 10 version 1607 kan offlinescanningen køres under **Windows Indstillinger** \> **Update & sikkerhedsdata** \> **Windows Defender** eller fra Windows Defender klienten.

## <a name="review-scan-results"></a>Gennemse scanningsresultater

Microsoft Defender Offline vises i sektionen [Scanningsoversigt i appen Windows Sikkerhed scanning](microsoft-defender-security-center-antivirus.md).

## <a name="related-articles"></a>Relaterede artikler

- [Tilpas, initier og gennemse resultaterne af scanninger og afhjælpning](customize-run-review-remediate-scans-microsoft-defender-antivirus.md)
- [Microsoft Defender Antivirus i Windows 10](microsoft-defender-antivirus-in-windows-10.md)
