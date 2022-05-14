---
title: Microsoft Defender Offline i Windows
description: Du kan bruge Microsoft Defender Offline direkte fra appen Windows Defender Antivirus. Du kan også administrere, hvordan den installeres på dit netværk.
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
ms.openlocfilehash: 690437de177ce1f6c466166970a8b7143d230916
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/14/2022
ms.locfileid: "65415634"
---
# <a name="run-and-review-the-results-of-a-microsoft-defender-offline-scan"></a>Kør og gennemse resultaterne af en Microsoft Defender Offline scanning

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Antivirus

**Platforme**
- Windows

Microsoft Defender Offline er et antimalwarescanningsværktøj, der giver dig mulighed for at starte og køre en scanning fra et miljø, du har tillid til. Scanningen kører uden for den normale Windows kerne, så den kan målrette malware, der forsøger at omgå Windows shell, såsom virus og rootkits, der inficerer eller overskriver master boot record (MBR).

Du kan bruge Microsoft Defender Offline hvis du har mistanke om en malware infektion, eller du ønsker at bekræfte en grundig ren af slutpunktet efter et malware udbrud.

I Windows 10 og Windows 11 kan Microsoft Defender Offline køres med et enkelt klik direkte fra [appen Windows Sikkerhed](microsoft-defender-security-center-antivirus.md). I tidligere versioner af Windows skulle en bruger installere Microsoft Defender Offline til startmedier, genstarte slutpunktet og indlæse det startbare medie.

## <a name="prerequisites-and-requirements"></a>forudsætninger og krav

Microsoft Defender Offline i Windows 10 og Windows 11 har de samme hardwarekrav som Windows 10.

Du kan få flere oplysninger om krav til Windows 10 og Windows 11 i følgende emner:

- [Minimumkrav til hardware](/windows-hardware/design/minimum/minimum-hardware-requirements-overview)

- [Retningslinjer for hardwarekomponenter](/windows-hardware/design/component-guidelines/components)

> [!NOTE]
> Microsoft Defender Offline understøttes ikke på maskiner med ARM-processorer eller på Windows serverlagerenheder.

Hvis du vil køre Microsoft Defender Offline fra slutpunktet, skal brugeren være logget på med administratorrettigheder.

## <a name="microsoft-defender-offline-updates"></a>Microsoft Defender Offline opdateringer

Microsoft Defender Offline bruger de nyeste tilgængelige beskyttelsesopdateringer på slutpunktet. De opdateres, når Windows Defender Antivirus opdateres.

> [!NOTE]
> Før du kører en offlinescanning, skal du forsøge at opdatere Microsoft Defender AV-beskyttelse. Du kan enten gennemtvinge en opdatering med Gruppepolitik eller på den måde, du normalt installerer opdateringer på slutpunkter på, eller du kan manuelt downloade og installere de nyeste beskyttelsesopdateringer fra [Microsoft Malware Protection Center](https://www.microsoft.com/security/portal/definitions/adl.aspx).

Se emnet [Administrer Microsoft Defender Antivirus Opdateringer til sikkerhedsintelligens](manage-protection-updates-microsoft-defender-antivirus.md) for at få flere oplysninger.

## <a name="usage-scenarios"></a>Forbrugsscenarier

I Windows 10 version 1607 kan du gennemtvinge en offlinescanning manuelt. Hvis Windows Defender bestemmer, at Microsoft Defender Offline skal køre, bliver brugeren også bedt om at angive slutpunktet.

Behovet for at udføre en offlinescanning vises også i Microsoft Endpoint Manager hvis du bruger den til at administrere dine slutpunkter.

Prompten kan forekomme via en meddelelse, der ligner følgende:

:::image type="content" source="../../media/notification.png" alt-text="Meddelelse om kørsel af Microsoft Defender Offline" lightbox="../../media/notification.png":::

Brugeren får også besked i den Windows Defender klient.

I Configuration Manager kan du identificere status for slutpunkter ved at gå til **Overvågning > Oversigt > Sikkerhed > Endpoint Protection Status > System Center Endpoint Protection Status**.

Microsoft Defender Offline scanninger er angivet under **Afhjælpningsstatus for malware**, da **offlinescanning er påkrævet**.

:::image type="content" source="../../media/sccm-wdo.png" alt-text="Indikatoren for en scanning efter Microsoft Defender Offline" lightbox="../../media/sccm-wdo.png":::

## <a name="configure-notifications"></a>Konfigurer meddelelser

Microsoft Defender Offline meddelelser konfigureres i den samme politikindstilling som andre Microsoft Defender AV-meddelelser.

Du kan finde flere oplysninger om meddelelser i Windows Defender i emnet [Konfigurer de meddelelser, der vises på slutpunkter](configure-notifications-microsoft-defender-antivirus.md).

## <a name="run-a-scan"></a>Kør en scanning

> [!IMPORTANT]
> Før du bruger Microsoft Defender Offline, skal du sørge for at gemme filer og lukke kørende programmer. Det tager ca. 15 minutter at køre den Microsoft Defender Offline scanning. Det genstarter slutpunktet, når scanningen er fuldført. Scanningen udføres uden for det sædvanlige Windows driftsmiljø. Brugergrænsefladen ser anderledes ud end en normal scanning, der udføres af Windows Defender. Når scanningen er fuldført, genstartes slutpunktet, og Windows indlæses normalt.

Du kan køre en Microsoft Defender Offline scanning med følgende:

- PowerShell
- WMI (Windows Management Instrumentation)
- Appen Windows Sikkerhed



### <a name="use-powershell-cmdlets-to-run-an-offline-scan"></a>Brug PowerShell-cmdlet'er til at køre en offlinescanning

Brug følgende cmdlet'er:

```PowerShell
Start-MpWDOScan
```

Se [Brug PowerShell-cmdlet'er til at konfigurere og køre Microsoft Defender Antivirus](use-powershell-cmdlets-microsoft-defender-antivirus.md)- og [Defender Antivirus-cmdlet'er](/powershell/module/defender/) for at få flere oplysninger om, hvordan du bruger PowerShell med Microsoft Defender Antivirus.

### <a name="use-windows-management-instruction-wmi-to-run-an-offline-scan"></a>Brug WMI (Windows Management Instruction) til at køre en offlinescanning

Brug klassen [**MSFT_MpWDOScan**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) til at køre en offlinescanning.

Følgende WMI-scriptstykke kører straks en Microsoft Defender Offline scanning, som medfører, at slutpunktet genstartes, kører offlinescanningen og derefter genstarter og starter i Windows.

```console
wmic /namespace:\\root\Microsoft\Windows\Defender path MSFT_MpWDOScan call Start
```

Se følgende for at få flere oplysninger:

- [Windows Defender WMIv2 API'er](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

### <a name="use-the-windows-defender-security-app-to-run-an-offline-scan"></a>Brug Windows Defender Security-appen til at køre en offlinescanning

1. Åbn appen Windows Sikkerhed ved at klikke på skjoldikonet på proceslinjen eller ved at søge i menuen Start efter **Defender for Cloud**.

2. Klik på feltet **Virus & threat protection** (eller skjoldikonet på menulinjen til venstre) og derefter på etiketten **Avanceret scanning** :

3. Vælg **Microsoft Defender Offline scanne**, og klik på **Scan nu**.

    > [!NOTE]
    > I Windows 10 version 1607 kan offlinescanningen køres fra under **Windows Indstillinger** \> **& sikkerheds-Windows Defender** \> eller fra den Windows Defender klient.

## <a name="review-scan-results"></a>Gennemse scanningsresultater

Microsoft Defender Offline scanningsresultater vises i [sektionen Scanningsoversigt i appen Windows Sikkerhed](microsoft-defender-security-center-antivirus.md).

> [!TIP]
> Hvis du leder efter antivirusrelaterede oplysninger til andre platforme, kan du se:
> - [Angiv indstillinger for Microsoft Defender for Endpoint på macOS-](mac-preferences.md)
> - [Microsoft Defender for Endpoint på Mac](microsoft-defender-endpoint-mac.md)
> - [Politikindstillinger for macOS Antivirus for Microsoft Defender Antivirus for Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Angiv indstillinger for Microsoft Defender for Endpoint på Linux](linux-preferences.md)
> - [Microsoft Defender for Endpoint på Linux](microsoft-defender-endpoint-linux.md)
> - [Konfigurer Defender for Endpoint på Android-funktioner](android-configure.md)
> - [Konfigurer Microsoft Defender for Endpoint på iOS-funktioner](ios-configure-features.md)

## <a name="related-articles"></a>Relaterede artikler

- [Tilpas, start og gennemse resultaterne af scanninger og afhjælpning](customize-run-review-remediate-scans-microsoft-defender-antivirus.md)
- [Microsoft Defender Antivirus i Windows 10](microsoft-defender-antivirus-in-windows-10.md)
