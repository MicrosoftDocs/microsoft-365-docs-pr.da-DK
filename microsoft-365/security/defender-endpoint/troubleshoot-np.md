---
title: Fejlfinding af problemer med netværksbeskyttelse
description: Ressourcer og eksempelkode til fejlfinding af problemer med netværksbeskyttelse i Microsoft Defender til slutpunkt.
keywords: fejlfinding, fejl, rettelse, windows defender f.eks. asr, regler, hips, fejlfinding, overvågning, udelukkelse, falsk positiv, ødelagt, blokering, Microsoft Defender til slutpunkt
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
ms.openlocfilehash: 169a05fdde96ec780bf5e626d81846c9c2d37f26
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2021
ms.locfileid: "63592107"
---
# <a name="troubleshoot-network-protection"></a>Fejlfinding af netværksbeskyttelse

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!TIP]
> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)

Denne artikel indeholder fejlfindingsoplysninger til [netværksbeskyttelse](network-protection.md), i tilfælde, f.eks.:

- Netværksbeskyttelse blokerer et sikkert websted (falsk positiv)
- Netværksbeskyttelse blokerer ikke et mistænkeligt eller kendt skadeligt websted (falsk negativ)

Der er fire trin til fejlfinding af disse problemer:

1. Bekræft forudsætninger
2. Brug overvågningstilstand til at teste reglen
3. Tilføj udeladelse for den angivne regel (for falske positive)
4. Sende supportlogfiler

## <a name="confirm-prerequisites"></a>Bekræft forudsætninger

Netværksbeskyttelse fungerer kun på enheder med følgende betingelser:

> [!div class="checklist"]
>
> - Slutpunkter kører i Windows 10 Pro Enterprise-version, version 1709 eller nyere.
> - Slutpunkter bruger Microsoft Defender Antivirus som den eneste antivirusbeskyttelsesapp. [Se, hvad der sker, når du bruger en antivirusløsning, der ikke er Microsoft](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-compatibility).
> - [Beskyttelse i realtid er](/windows/security/threat-protection/microsoft-defender-antivirus/configure-real-time-protection-microsoft-defender-antivirus) aktiveret.
> - [Beskyttelse, der leveres i skyen](/windows/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus) , er aktiveret.
> - Overvågningstilstand er ikke aktiveret. Brug [Gruppepolitik](enable-network-protection.md#group-policy) til at angive reglen til **Deaktiveret** (værdi: **0**).

## <a name="use-audit-mode"></a>Brug overvågningstilstand

Du kan aktivere netværksbeskyttelse i overvågningstilstand og derefter besøge et websted, som vi har oprettet for at demoe funktionen. Netværksbeskyttelse tillader alle webstedsforbindelser, men en hændelse logføres for at angive en forbindelse, der ville være blevet blokeret, hvis netværksbeskyttelse var aktiveret.

1. Angiv netværksbeskyttelse til **overvågningstilstand**.

   ```PowerShell
   Set-MpPreference -EnableNetworkProtection AuditMode
   ```

2. Udfør den forbindelsesaktivitet, der forårsager et problem (f.eks. forsøg at besøge webstedet, eller opret forbindelse til den IP-adresse, du gør eller ikke vil blokere).

3. [Gennemse hændelseslogfilerne for netværksbeskyttelse for](network-protection.md#review-network-protection-events-in-windows-event-viewer) at se, om funktionen ville have blokeret forbindelsen, hvis den var indstillet til **Aktiveret**.

   Hvis netværksbeskyttelse ikke blokerer en forbindelse, som du forventer, at den skal blokere, skal du aktivere funktionen.

   ```PowerShell
   Set-MpPreference -EnableNetworkProtection Enabled
   ```

## <a name="report-a-false-positive-or-false-negative"></a>Rapportere en falsk positiv eller falsk negativ

Hvis du har testet funktionen med demowebstedet og med overvågningstilstand, og netværksbeskyttelse arbejder på forudkonfigurerede scenarier, men ikke fungerer som forventet for en bestemt forbindelse, kan du bruge [den Windows Defender Security Intelligence-webbaserede](https://www.microsoft.com/wdsi/filesubmission) indsendelsesformular til at rapportere en falsk negativ eller falsk positiv til netværksbeskyttelse. Med et E5-abonnement kan du også [angive et link til en tilknyttet besked](alerts-queue.md).

Se [Address false positive/negatives in Microsoft Defender for Endpoint](defender-endpoint-false-positives-negatives.md).

## <a name="add-exclusions"></a>Tilføj udeladelse
De aktuelle udeladelsesindstillinger er:

1.  Konfiguration af en brugerdefineret tilladelsesindikator.
2.  Brug af IP-udeladelse: `Add-MpPreference -ExclusionIpAddress 192.168.1.1`
3.  Udelukke en hel proces. Du kan finde flere oplysninger [Microsoft Defender Antivirus udeladelse.](configure-exclusions-microsoft-defender-antivirus.md) 


## <a name="collect-diagnostic-data-for-file-submissions"></a>Indsaml diagnostiske data til filindsendelser

Når du rapporterer om et problem med netværksbeskyttelse, bliver du bedt om at indsamle og indsende diagnostiske data, der kan bruges af Microsoft-support og tekniske teams til at foretage fejlfinding af problemer.

1. Åbn en kommandoprompt med administrator administrator og skift til Windows Defender mappe:

   ```console
   cd c:\program files\windows defender
   ```

2. Kør denne kommando for at generere diagnosticeringslogfilerne:

   ```console
   mpcmdrun -getfiles
   ```

3. Vedhæft filen til indsendelsesformularen. Diagnosticeringslogfiler gemmes som standard på `C:\ProgramData\Microsoft\Windows Defender\Support\MpSupportFiles.cab`.

## <a name="resolve-connectivity-issues-with-network-protection-for-e5-customers"></a>Løse forbindelsesproblemer med netværksbeskyttelse (for E5-kunder)

På grund af det miljø, hvor netværksbeskyttelse kører, kan Microsoft ikke se proxyindstillingerne for dit operativsystem. I nogle tilfælde kan netværkbeskyttelsesklienter ikke oprette forbindelse til skytjenesten. Du kan løse forbindelsesproblemer med netværksbeskyttelse ved at konfigurere en af følgende registreringsdatabasenøgler, så netværksbeskyttelse bliver opmærksom på proxykonfigurationen:

```powershell
Set-MpPreference -ProxyServer <proxy IP address: Port>
```

---ELLER---

```powershell
Set-MpPreference -ProxyPacUrl <Proxy PAC url>
```

Du kan konfigurere registreringsdatabasenøglen ved hjælp af PowerShell, Microsoft Endpoint Manager eller Gruppepolitik. Her er nogle ressourcer, der kan hjælpe:

- [Arbejde med registreringsdatabasenøgler](/powershell/scripting/samples/working-with-registry-keys)
- [Konfigurere brugerdefinerede klientindstillinger for Endpoint Protection](/mem/configmgr/protect/deploy-use/endpoint-protection-configure-client)
- [Brug Gruppepolitik til at administrere Endpoint Protection](/mem/configmgr/protect/deploy-use/endpoint-protection-group-policies)

## <a name="see-also"></a>Se også

- [Netværksbeskyttelse](network-protection.md)
- [Netværksbeskyttelse og TCP trevejs-handshake](network-protection.md#network-protection-and-the-tcp-three-way-handshake)
- [Evaluer netværksbeskyttelse](evaluate-network-protection.md)
- [Aktivér netværksbeskyttelse](enable-network-protection.md)
- [Adressere falske positive/negativer i Defender til slutpunkt](defender-endpoint-false-positives-negatives.md)
