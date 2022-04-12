---
title: Foretag fejlfinding af problemer med netværksbeskyttelse
description: Ressourcer og eksempelkode til fejlfinding af problemer med netværksbeskyttelse i Microsoft Defender for Endpoint.
keywords: fejlfinding, fejl, rettelse, Windows Defender f.eks. asr, regler, hofter, fejlfinding, overvågning, udeladelse, falsk positiv, brudt, blokerende, Microsoft Defender for Endpoint
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
author: dansimp
ms.author: dansimp
ms.reviewer: oogunrinde
manager: dansimp
ms.technology: mde
ms.topic: how-to
ms.collection: M365-security-compliance
ms.openlocfilehash: fbb3a9e038dcd9f342065d538762b41c0673f7e6
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/12/2022
ms.locfileid: "64783155"
---
# <a name="troubleshoot-network-protection"></a>Foretag fejlfinding af netværksbeskyttelse

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!TIP]
> Vil du gerne opleve Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)

Denne artikel indeholder fejlfindingsoplysninger i forbindelse med [netværksbeskyttelse](network-protection.md), f.eks.:

- Netværksbeskyttelse blokerer et websted, der er sikkert (falsk positivt)
- Netværksbeskyttelse kan ikke blokere et mistænkeligt eller kendt skadeligt websted (falsk negativt)

Der er fire trin til fejlfinding af disse problemer:

1. Bekræft forudsætninger
2. Brug overvågningstilstand til at teste reglen
3. Tilføj udeladelser for den angivne regel (for falske positiver)
4. Send supportlogge

## <a name="confirm-prerequisites"></a>Bekræft forudsætninger

Netværksbeskyttelse fungerer kun på enheder med følgende betingelser:

> [!div class="checklist"]
>
> - Slutpunkter kører Windows 10 Pro eller Enterprise-udgaven, version 1709 eller nyere.
> - Slutpunkter bruger Microsoft Defender Antivirus som den eneste antivirusbeskyttelsesapp. [Se, hvad der sker, når du bruger en antivirusløsning, der ikke er fra Microsoft](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-compatibility).
> - [Beskyttelse i realtid](/windows/security/threat-protection/microsoft-defender-antivirus/configure-real-time-protection-microsoft-defender-antivirus) er aktiveret.
> - [Skybaseret beskyttelse](/windows/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus) er aktiveret.
> - Overvågningstilstand er ikke aktiveret. Brug [Gruppepolitik](enable-network-protection.md#group-policy) til at angive reglen til **Disabled** (værdi: **0**).

## <a name="use-audit-mode"></a>Brug overvågningstilstand

Du kan aktivere netværksbeskyttelse i overvågningstilstand og derefter besøge et websted, som vi har oprettet, for at demonstrere funktionen. Alle webstedsforbindelser tillades af netværksbeskyttelse, men der logføres en hændelse for at angive en forbindelse, der ville være blevet blokeret, hvis netværksbeskyttelse blev aktiveret.

1. Angiv netværksbeskyttelse til **Overvågningstilstand**.

   ```PowerShell
   Set-MpPreference -EnableNetworkProtection AuditMode
   ```

2. Udfør den forbindelsesaktivitet, der forårsager et problem (f.eks. forsøg at besøge webstedet, eller opret forbindelse til den IP-adresse, du gør eller ikke vil blokere).

3. [Gennemse logfilerne for netværksbeskyttelseshændelser](network-protection.md#review-network-protection-events-in-windows-event-viewer) for at se, om funktionen ville have blokeret forbindelsen, hvis den var indstillet til **Aktiveret**.

   Hvis netværksbeskyttelse ikke blokerer en forbindelse, som du forventer, at den skal blokere, skal du aktivere funktionen.

   ```PowerShell
   Set-MpPreference -EnableNetworkProtection Enabled
   ```

## <a name="report-a-false-positive-or-false-negative"></a>Rapportér en falsk positiv eller falsk negativ

Hvis du har testet funktionen på demowebstedet og med overvågningstilstand, og netværksbeskyttelse fungerer på forudkonfigurerede scenarier, men ikke fungerer som forventet for en bestemt forbindelse, kan du bruge [den webbaserede indsendelsesformular til Windows Defender Security Intelligence](https://www.microsoft.com/wdsi/filesubmission) til at rapportere falsk negativ eller falsk positiv til netværksbeskyttelse. Med et E5-abonnement kan du også [angive et link til en tilknyttet besked](alerts-queue.md).

Se [Address false positive/negatives in Microsoft Defender for Endpoint](defender-endpoint-false-positives-negatives.md).

## <a name="add-exclusions"></a>Tilføj udeladelser

De aktuelle indstillinger for udeladelse er:

1. Konfiguration af en brugerdefineret tilladelsesindikator.
2. Brug af IP-udeladelser: `Add-MpPreference -ExclusionIpAddress 192.168.1.1`
3. Udelader en hel proces. Du kan få flere oplysninger under [Microsoft Defender Antivirus udeladelser](configure-exclusions-microsoft-defender-antivirus.md). 

## <a name="collect-diagnostic-data-for-file-submissions"></a>Indsaml diagnosticeringsdata til filindsendelser

Når du rapporterer et problem med netværksbeskyttelse, bliver du bedt om at indsamle og sende diagnosticeringsdata, der kan bruges af Microsofts support- og teknikerteams til at hjælpe med fejlfinding af problemer.

1. Åbn en kommandoprompt med administratorrettigheder, og skift til mappen Windows Defender:

   ```console
   cd c:\program files\windows defender
   ```

2. Kør denne kommando for at generere diagnosticeringslogfilerne:

   ```console
   mpcmdrun -getfiles
   ```

3. Vedhæft filen til afsendelsesformularen. Diagnosticeringslogge gemmes som standard på `C:\ProgramData\Microsoft\Windows Defender\Support\MpSupportFiles.cab`.

## <a name="resolve-connectivity-issues-with-network-protection-for-e5-customers"></a>Løs forbindelsesproblemer med netværksbeskyttelse (for E5-kunder)

På grund af det miljø, hvor netværksbeskyttelse kører, kan Microsoft ikke se operativsystemets proxyindstillinger. I nogle tilfælde kan klienter til netværksbeskyttelse ikke oprette forbindelse til cloudtjenesten. Hvis du vil løse forbindelsesproblemer med netværksbeskyttelse, skal du konfigurere en af følgende registreringsdatabasenøgler, så netværksbeskyttelse bliver opmærksom på proxykonfigurationen:

```powershell
Set-MpPreference -ProxyServer <proxy IP address: Port>
```

---OR---

```powershell
Set-MpPreference -ProxyPacUrl <Proxy PAC url>
```

Du kan konfigurere registreringsdatabasenøglen ved hjælp af PowerShell, Microsoft Endpoint Manager eller Gruppepolitik. Her er nogle ressourcer, der kan hjælpe:

- [Arbejde med registreringsdatabasenøgler](/powershell/scripting/samples/working-with-registry-keys)
- [Konfigurer brugerdefinerede klientindstillinger for Endpoint Protection](/mem/configmgr/protect/deploy-use/endpoint-protection-configure-client)
- [Brug Gruppepolitik indstillinger til at administrere Endpoint Protection](/mem/configmgr/protect/deploy-use/endpoint-protection-group-policies)

## <a name="see-also"></a>Se også

- [Netværksbeskyttelse](network-protection.md)
- [Netværksbeskyttelse og TCP-trevejs-håndtryk](network-protection.md#network-protection-and-the-tcp-three-way-handshake)
- [Evaluer netværksbeskyttelse](evaluate-network-protection.md)
- [Aktivér netværksbeskyttelse](enable-network-protection.md)
- [Løs falske positiver/negativer i Defender for Endpoint](defender-endpoint-false-positives-negatives.md)
