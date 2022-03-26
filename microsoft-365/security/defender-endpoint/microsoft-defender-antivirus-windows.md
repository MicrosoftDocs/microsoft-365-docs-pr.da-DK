---
title: Microsoft Defender Antivirus i Windows
description: Få mere at vide om, hvordan du administrerer, konfigurerer Microsoft Defender Antivirus, indbygget antimalware og antivirusbeskyttelse.
keywords: Microsoft Defender Antivirus, windows defender, antimalware, scep, system center endpoint protection, system center configuration manager, virus, malware, trussel, registrering, beskyttelse, sikkerhed
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: high
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.reviewer: mkaminska
manager: dansimp
ms.custom: nextgen
ms.technology: mde
ms.collection:
- M365-security-compliance
- m365initiative-defender-endpoint
ms.openlocfilehash: b6eabc3527742b6cc7f06d23207db813b827e5f5
ms.sourcegitcommit: aac7e002ec6e10a41baa2d0bd38614b0ed471a70
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/27/2022
ms.locfileid: "63595991"
---
# <a name="microsoft-defender-antivirus-in-windows"></a>Microsoft Defender Antivirus i Windows

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Antivirus

Microsoft Defender Antivirus findes i Windows 10 og Windows 11 og i versioner af Windows Server.

Microsoft Defender Antivirus er en vigtig komponent i din næste generations beskyttelse i Microsoft Defender til slutpunkt. Denne beskyttelse samler maskinlæring, big-data-analyse, dybdegående research af trusselsbeskyttelse og Microsofts skyinfrastruktur til beskyttelse af enheder (eller slutpunkter) i din organisation. Microsoft Defender Antivirus er indbygget i Windows, og det fungerer sammen med Microsoft Defender for Endpoint for at yde beskyttelse på din enhed og i skyen.

## <a name="compatibility-with-other-antivirus-products"></a>Kompatibilitet med andre antivirusprodukter

Hvis du bruger et ikke-Microsoft-antivirus-/antimalwareprodukt på din enhed, kan du muligvis køre Microsoft Defender Antivirus i passiv tilstand sammen med den ikke-Microsoft-antivirusløsning. Det afhænger af det anvendte operativsystem, og om enheden er onboardet til Defender til slutpunkt. Du kan få mere at vide [Microsoft Defender Antivirus kompatibilitet](microsoft-defender-antivirus-compatibility.md).

## <a name="comparing-active-mode-passive-mode-and-disabled-mode"></a>Sammenligning af aktiv tilstand, passiv tilstand og deaktiveret tilstand

I følgende tabel beskrives, hvad du kan forvente, når Microsoft Defender Antivirus er i aktiv tilstand, passiv tilstand eller deaktiveret.

<br/><br/>

| Tilstand | Hvad sker der? |
|---|---|
| Aktiv tilstand | I aktiv tilstand Microsoft Defender Antivirus bruges som den primære antivirusapp på enheden. Filer scannes, trusler afhjælpes, og registrerede trusler vises i organisationens sikkerhedsrapporter og i din Windows Sikkerhed-app. |
| Passiv tilstand | I passiv tilstand Microsoft Defender Antivirus bruges ikke som den primære antivirusapp på enheden. Filer scannes og registrerede trusler rapporteres, men trusler afhjælpes ikke af Microsoft Defender Antivirus. <br/><br/> **VIGTIGT**: Microsoft Defender Antivirus kan kun køre i passiv tilstand på slutpunkter, der er onboardet til Microsoft Defender til slutpunkt. Se [Krav til, Microsoft Defender Antivirus skal køre i passiv tilstand](microsoft-defender-antivirus-compatibility.md#requirements-for-microsoft-defender-antivirus-to-run-in-passive-mode). |
| Deaktiveret eller fjernet | Når deaktiveret eller fjernet, Microsoft Defender Antivirus bruges ikke. Filer scannes ikke, og trusler bliver ikke løst. Generelt anbefaler vi ikke deaktivering eller fjernelse af Microsoft Defender Antivirus. |

Du kan få mere at vide [Microsoft Defender Antivirus kompatibilitet](microsoft-defender-antivirus-compatibility.md).

## <a name="check-the-state-of-microsoft-defender-antivirus-on-your-device"></a>Kontrollér tilstanden for Microsoft Defender Antivirus på din enhed

Hvis du vil kontrollere tilstanden for Microsoft Defender Antivirus på din enhed, kan du bruge en af flere metoder, f.eks. Windows Sikkerhed app eller Windows PowerShell.

### <a name="use-the-windows-security-app-to-check-status-of-microsoft-defender-antivirus"></a>Brug appen Windows Sikkerhed til at kontrollere status for Microsoft Defender Antivirus

1. På din Windows enhed skal du vælge menuen Start og begynde at skrive `Security`. Åbn derefter Windows Sikkerhed i resultaterne.

2. Vælg **Virus- & trusselsbeskyttelse**.

3. Vælg **Administrer & under Indstillinger** for **trusselsbeskyttelse under Virusbeskyttelse**.

Du får vist navnet på din antivirus/antimalwareløsning på siden med indstillinger.

### <a name="use-powershell-to-check-status-of-microsoft-defender-antivirus"></a>Brug PowerShell til at kontrollere status for Microsoft Defender Antivirus

1. Markér fanen menuen Start, og begynd at skrive `PowerShell`. Åbn derefter Windows PowerShell i resultaterne.

2. Skriv `Get-MpComputerStatus`.

3. Kig på rækken **AMRunningMode på listen** over resultater.

   - **Normal** betyder Microsoft Defender Antivirus kører i aktiv tilstand.

   - **Passiv tilstand** betyder, Microsoft Defender Antivirus kører, men ikke er det primære antivirus-/antimalwareprodukt på din enhed. Passiv tilstand er kun tilgængelig for enheder, der er onboardet til Microsoft Defender til slutpunkt, og som opfylder visse krav. Du kan få mere at vide [under Krav til Microsoft Defender Antivirus at køre i passiv tilstand](microsoft-defender-antivirus-compatibility.md#requirements-for-microsoft-defender-antivirus-to-run-in-passive-mode).

   - **Slutpunktsregistrering og -svar bloktilstand** betyder, at Microsoft Defender Antivirus kører, og at slutpunktsregistrering og [-svar (Slutpunktsregistrering og -svar)](edr-in-block-mode.md) i bloktilstand er aktiveret. En funktion i Microsoft Defender til slutpunkt er aktiveret.

   - **SxS Passiv tilstand betyder**, Microsoft Defender Antivirus kører sammen med et andet antivirus-/antimalwareprodukt, og [der anvendes begrænset periodisk scanner](limited-periodic-scanning-microsoft-defender-antivirus.md).

> [!TIP]
> Du kan få mere at Get-MpComputerStatus om PowerShell-cmdlet'en i referenceartikel [Get-MpComputerStatus](/powershell/module/defender/get-mpcomputerstatus).

## <a name="get-your-antivirusantimalware-platform-updates"></a>Hent opdateringer til din antivirus-/antimalwareplatform

Det er vigtigt at holde Microsoft Defender Antivirus, eller en antivirus-/antimalwareløsning, opdateret. Microsoft udgiver regelmæssige opdateringer for at sikre, at dine enheder har den nyeste teknologi til beskyttelse mod nye malware- og angrebsteknikker. Du kan få mere at vide [under Administrere Microsoft Defender Antivirus opdateringer og anvende oprindelige planer](manage-updates-baselines-microsoft-defender-antivirus.md).

## <a name="see-also"></a>Se også

- [Microsoft Defender Antivirus administration og konfiguration](configuration-management-reference-microsoft-defender-antivirus.md)
- [Evaluer Microsoft Defender Antivirus beskyttelse](evaluate-microsoft-defender-antivirus.md)
