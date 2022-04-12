---
title: Microsoft Defender Antivirus i Windows
description: Få mere at vide om, hvordan du administrerer, konfigurerer og bruger Microsoft Defender Antivirus indbygget antimalware- og antivirusbeskyttelse.
keywords: Microsoft Defender Antivirus, Windows Defender, antimalware, scep, system center endpoint protection, System Center Configuration Manager, virus, malware, trussel, opdagelse, beskyttelse, sikkerhed
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
ms.openlocfilehash: 352b60caa3af581a5d1162b1896b255bfcea873c
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/12/2022
ms.locfileid: "64790234"
---
# <a name="microsoft-defender-antivirus-in-windows"></a>Microsoft Defender Antivirus i Windows

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Antivirus

**Platforme**
- Windows 

Microsoft Defender Antivirus er tilgængelig i Windows 10 og Windows 11 og i versioner af Windows Server.

Microsoft Defender Antivirus er en vigtig komponent i din næste generation af beskyttelse i Microsoft Defender for Endpoint. Denne beskyttelse samler maskinel indlæring, analyse af big data, dybdegående forskning i trusselsresistens og Microsofts cloudinfrastruktur for at beskytte enheder (eller slutpunkter) i din organisation. Microsoft Defender Antivirus er indbygget i Windows, og det fungerer sammen med Microsoft Defender for Endpoint til at yde beskyttelse på din enhed og i cloudmiljøet.

## <a name="compatibility-with-other-antivirus-products"></a>Kompatibilitet med andre antivirusprodukter

Hvis du bruger et antivirus-/antimalwareprodukt, der ikke er fra Microsoft, på din enhed, kan du muligvis køre Microsoft Defender Antivirus i passiv tilstand sammen med den ikke-Microsoft-antivirusløsning. Det afhænger af det anvendte operativsystem, og om din enhed er onboardet til Defender for Endpoint. Du kan få mere at vide under [Microsoft Defender Antivirus kompatibilitet](microsoft-defender-antivirus-compatibility.md).

## <a name="comparing-active-mode-passive-mode-and-disabled-mode"></a>Sammenligning af aktiv tilstand, passiv tilstand og deaktiveret tilstand

I følgende tabel beskrives det, hvad du kan forvente, når Microsoft Defender Antivirus er i aktiv tilstand, passiv tilstand eller deaktiveret.

<br/><br/>

| Tilstand | Hvad sker der? |
|---|---|
| Aktiv tilstand | I aktiv tilstand bruges Microsoft Defender Antivirus som den primære antivirusapp på enheden. Filer scannes, trusler afhjælpes, og registrerede trusler vises i organisationens sikkerhedsrapporter og i din Windows Sikkerhed app. |
| Passiv tilstand | I passiv tilstand bruges Microsoft Defender Antivirus ikke som den primære antivirusapp på enheden. Filer scannes, og registrerede trusler rapporteres, men trusler afhjælpes ikke af Microsoft Defender Antivirus. <br/><br/> **VIGTIGT!** Microsoft Defender Antivirus kan kun køre i passiv tilstand på slutpunkter, der er onboardet til Microsoft Defender for Endpoint. Se [Krav til, Microsoft Defender Antivirus skal køre i passiv tilstand](microsoft-defender-antivirus-compatibility.md#requirements-for-microsoft-defender-antivirus-to-run-in-passive-mode). |
| Deaktiveret eller fjernet | Når Microsoft Defender Antivirus er deaktiveret eller fjernet, bruges ikke. Filerne scannes ikke, og trusler afhjælpes ikke. Generelt anbefaler vi ikke, at du deaktiverer eller fjerner Microsoft Defender Antivirus. |

Du kan få mere at vide under [Microsoft Defender Antivirus kompatibilitet](microsoft-defender-antivirus-compatibility.md).

## <a name="check-the-state-of-microsoft-defender-antivirus-on-your-device"></a>Kontrollér tilstanden for Microsoft Defender Antivirus på enheden

Hvis du vil kontrollere tilstanden for Microsoft Defender Antivirus på din enhed, kan du bruge en af flere metoder, f.eks. Windows Sikkerhed-appen eller Windows PowerShell.

### <a name="use-the-windows-security-app-to-check-status-of-microsoft-defender-antivirus"></a>Brug appen Windows Sikkerhed til at kontrollere status for Microsoft Defender Antivirus

1. Vælg menuen Start på din Windows enhed, og begynd at skrive `Security`. Åbn derefter appen Windows Sikkerhed i resultaterne.

2. Vælg **Virus & trusselsbeskyttelse**.

3. Under **Indstillinger for virus & trusselsbeskyttelse** skal du vælge **Administrer indstillinger**.

Du kan se navnet på din antivirus-/antimalwareløsning på indstillingssiden.

### <a name="use-powershell-to-check-status-of-microsoft-defender-antivirus"></a>Brug PowerShell til at kontrollere status for Microsoft Defender Antivirus

1. Vælg menuen Start, og begynd at skrive `PowerShell`. Åbn derefter Windows PowerShell i resultaterne.

2. Skriv `Get-MpComputerStatus`.

3. På listen over resultater skal du se på rækken **AMRunningMode** .

   - **Normal** betyder, at Microsoft Defender Antivirus kører i aktiv tilstand.

   - **Passiv tilstand** betyder, at Microsoft Defender Antivirus kører, men det er ikke det primære antivirus-/antimalwareprodukt på din enhed. Passiv tilstand er kun tilgængelig for enheder, der er onboardet til Microsoft Defender for Endpoint, og som opfylder visse krav. Du kan få mere at vide under [Krav til, Microsoft Defender Antivirus skal køre i passiv tilstand](microsoft-defender-antivirus-compatibility.md#requirements-for-microsoft-defender-antivirus-to-run-in-passive-mode).

   - **Slutpunktsregistrering og -svar bloktilstand** betyder, at Microsoft Defender Antivirus kører, og at [slutpunktsregistrering og -svar (Slutpunktsregistrering og -svar) er](edr-in-block-mode.md) en funktion i Microsoft Defender for Endpoint , er aktiveret.

   - **SxS Passive Mode** betyder, at Microsoft Defender Antivirus kører sammen med et andet antivirus-/antimalwareprodukt, og [der bruges begrænset periodisk scanning](limited-periodic-scanning-microsoft-defender-antivirus.md).

> [!TIP]
> Du kan få mere at vide om Get-MpComputerStatus PowerShell-cmdlet'en i referenceartiklen [Get-MpComputerStatus](/powershell/module/defender/get-mpcomputerstatus).

## <a name="get-your-antivirusantimalware-platform-updates"></a>Få opdateringer til din antivirus-/antimalwareplatform

Det er vigtigt at holde Microsoft Defender Antivirus eller enhver antivirus-/antimalwareløsning opdateret. Microsoft udgiver regelmæssige opdateringer for at sikre, at dine enheder har den nyeste teknologi til at beskytte mod ny malware og angrebsteknikker. Du kan få mere at vide under [Administrer Microsoft Defender Antivirus opdateringer og anvende grundlinjer](manage-updates-baselines-microsoft-defender-antivirus.md).

> [!TIP]
> Hvis du leder efter antivirusrelaterede oplysninger til andre platforme, kan du se:
> - [Angiv indstillinger for Microsoft Defender for Endpoint på macOS](mac-preferences.md)
> - [Microsoft Defender for Endpoint på Mac](microsoft-defender-endpoint-mac.md)
> - [macOS Antivirus politikindstillinger for Microsoft Defender Antivirus til Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Angiv indstillinger for Microsoft Defender for Endpoint på Linux](linux-preferences.md)
> - [Microsoft Defender for Endpoint på Linux](microsoft-defender-endpoint-linux.md)
> - [Konfigurer Defender for Endpoint på Android-funktioner](android-configure.md)
> - [Konfigurer Microsoft Defender for Endpoint på iOS-funktioner](ios-configure-features.md)

## <a name="see-also"></a>Se også

- [Microsoft Defender Antivirus administration og konfiguration](configuration-management-reference-microsoft-defender-antivirus.md)
- [Evaluer Microsoft Defender Antivirus beskyttelse](evaluate-microsoft-defender-antivirus.md)
