---
title: Foretag fejlfinding af problemer med regler for reduktion af angrebsoverfladen
description: Ressourcer og eksempelkode til fejlfinding af problemer med regler for reduktion af angrebsoverfladen i Microsoft Defender for Endpoint.
keywords: fejlfinding, fejl, rettelse, Windows Defender f.eks. asr, regler, hofter, fejlfinding, overvågning, udeladelse, falsk positiv, brudt, blokerende, Microsoft Defender for Endpoint
ms.pagetype: security
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
audience: ITPro
author: jweston-1
ms.author: v-jweston
ms.date: 03/27/2019
ms.reviewer: ''
manager: dansimp
ms.custom: asr
ms.technology: mde
ms.topic: how-to
ms.collection: M365-security-compliance
ms.openlocfilehash: 9c884ab9a4ee2180d3c491c4257fb04129c40bc9
ms.sourcegitcommit: c314e989202dc1c9c260fffd459d53bc1f08514e
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/12/2022
ms.locfileid: "66717208"
---
# <a name="troubleshoot-attack-surface-reduction-rules"></a>Fejlfinding af regler for reduktion af angrebsoverflade

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)

Når du bruger [regler for reduktion af angrebsoverfladen](attack-surface-reduction.md) , kan du støde på problemer, f.eks.:

- En regel blokerer en fil, proces eller udfører en anden handling, som den ikke skal (falsk positiv)
- En regel fungerer ikke som beskrevet, eller blokerer ikke en fil eller proces, som den skal (falsk negativ)

Der er fire trin til fejlfinding af disse problemer:

1. [Bekræft forudsætninger](#confirm-prerequisites)
2. [Brug overvågningstilstand til at teste reglen](#use-audit-mode-to-test-the-rule)
3. [Tilføj udeladelser for den angivne regel](#add-exclusions-for-a-false-positive) (for falske positiver)
4. [Send supportlogge](#collect-diagnostic-data-for-file-submissions)

## <a name="confirm-prerequisites"></a>Bekræft forudsætninger

Regler for reduktion af angrebsoverfladen fungerer kun på enheder med følgende betingelser:

- Slutpunkter kører Windows 10 Enterprise version 1709 (også kendt som Fall Creators Update).

- Slutpunkter bruger Microsoft Defender Antivirus som den eneste antivirusbeskyttelsesapp. [Hvis du bruger en hvilken som helst anden antivirusapp, vil Microsoft Defender Antivirus deaktivere sig selv](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-compatibility).

- [Beskyttelse i realtid](/windows/security/threat-protection/microsoft-defender-antivirus/configure-real-time-protection-microsoft-defender-antivirus) er aktiveret.

- Overvågningstilstand er ikke aktiveret. Brug Gruppepolitik til at angive reglen til **Deaktiveret** (værdi: **0**) som beskrevet i [Aktivér regler for reduktion af angrebsoverflade](enable-attack-surface-reduction.md).

Hvis alle disse forudsætninger er opfyldt, skal du gå videre til næste trin for at teste reglen i overvågningstilstand.

## <a name="use-audit-mode-to-test-the-rule"></a>Brug overvågningstilstand til at teste reglen

Følg disse instruktioner i [Brug demoværktøjet til at se, hvordan regler for reduktion af angreb fungerer](evaluate-attack-surface-reduction.md) for at teste den specifikke regel, du støder på problemer med.

1. Aktivér overvågningstilstand for den specifikke regel, du vil teste. Brug Gruppepolitik til at angive reglen til **Overvågningstilstand** (værdi: **2**) som beskrevet i [Aktivér regler for reduktion af angrebsoverfladen](enable-attack-surface-reduction.md). Overvågningstilstand gør det muligt for reglen at rapportere filen eller processen, men tillader stadig, at den kører.

2. Udfør den aktivitet, der forårsager et problem (f.eks. åbn eller udfør den fil eller proces, der skal blokeres, men som er tilladt).

3. [Gennemse hændelsesloggene for reglen for reduktion af angrebsoverfladen](attack-surface-reduction.md) for at se, om reglen ville have blokeret filen eller processen, hvis reglen var angivet til **Aktiveret**.

Hvis en regel ikke blokerer en fil eller proces, som du forventer, at den skal blokere, skal du først kontrollere, om overvågningstilstand er aktiveret.

Overvågningstilstanden kan være blevet aktiveret til test af en anden funktion eller af et automatiseret PowerShell-script, og den er muligvis ikke blevet deaktiveret, efter at testene er fuldført.

Hvis du har testet reglen med demoværktøjet og med overvågningstilstand, og regler for reduktion af angrebsoverfladen fungerer på forudkonfigurerede scenarier, men reglen ikke fungerer som forventet, skal du gå til et af følgende afsnit baseret på din situation:

1. Hvis reglen for reduktion af angrebsoverfladen blokerer noget, som den ikke bør blokere (også kendt som falsk positiv), kan du [først tilføje en udeladelse af reglen for reduktion af angrebsoverfladen](#add-exclusions-for-a-false-positive).

2. Hvis reglen for reduktion af angrebsoverfladen ikke blokerer noget, som den skal blokere (også kendt som et falsk negativt), kan du fortsætte med det samme til det sidste trin, [indsamle diagnosticeringsdata og sende problemet til os](#collect-diagnostic-data-for-file-submissions).

## <a name="add-exclusions-for-a-false-positive"></a>Tilføj udeladelser for falsk positiv

Hvis reglen for reduktion af angrebsoverfladen blokerer noget, som den ikke bør blokere (også kendt som falsk positiv), kan du tilføje undtagelser for at forhindre, at regler for reduktion af angrebsoverfladen evaluerer de udeladte filer eller mapper.

Hvis du vil tilføje en udeladelse, skal du se [Tilpas overfladereduktion af angreb](attack-surface-reduction-rules-deployment-implement.md#customize-attack-surface-reduction-rules).

> [!IMPORTANT]
> Du kan angive individuelle filer og mapper, der skal udelades, men du kan ikke angive individuelle regler.
> Det betyder, at alle filer eller mapper, der udelades, udelades fra alle ASR-regler.

## <a name="report-a-false-positive-or-false-negative"></a>Rapportér en falsk positiv eller falsk negativ

Brug den [webbaserede indsendelsesformular til Windows Defender Security Intelligence](https://www.microsoft.com/wdsi/filesubmission) til at rapportere falsk negativ eller falsk positiv til netværksbeskyttelse. Med et Windows E5-abonnement kan du også [angive et link til alle tilknyttede beskeder](alerts-queue.md).

## <a name="collect-diagnostic-data-for-file-submissions"></a>Indsaml diagnosticeringsdata til filindsendelser

Når du rapporterer et problem med regler for reduktion af angrebsoverfladen, bliver du bedt om at indsamle og indsende diagnosticeringsdata, der kan bruges af Microsofts support- og teknikerteams til at foretage fejlfinding af problemer.

1. Åbn en kommandoprompt med administratorrettigheder, og skift til mappen Windows Defender:

   ```console
   cd "c:\program files\windows defender"
   ```

2. Kør denne kommando for at generere diagnosticeringslogfilerne:

   ```console
   mpcmdrun -getfiles
   ```

3. Som standard gemmes de i `C:\ProgramData\Microsoft\Windows Defender\Support\MpSupportFiles.cab`. Vedhæft filen til afsendelsesformularen.

## <a name="related-articles"></a>Relaterede artikler

- [Regler for reduktion af angrebsoverflade](attack-surface-reduction.md)
- [Aktivér regler for reduktion af angrebsoverflade](enable-attack-surface-reduction.md)
- [Evaluer regler for reduktion af angrebsoverfladen](evaluate-attack-surface-reduction.md)
