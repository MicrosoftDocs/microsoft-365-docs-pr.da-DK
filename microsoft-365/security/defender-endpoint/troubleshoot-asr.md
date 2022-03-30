---
title: Fejlfinding af problemer med regler for reduktion af angrebsoverfladen
description: Ressourcer og eksempelkode til fejlfinding af problemer med begrænsningsregler for angrebsoverfladen i Microsoft Defender til slutpunkt.
keywords: fejlfinding, fejl, rettelse, windows defender f.eks. asr, regler, hips, fejlfinding, overvågning, udelukkelse, falsk positiv, ødelagt, blokering, Microsoft Defender til slutpunkt
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
ms.openlocfilehash: c503c3ed4cfea4ed0645cf18a9c9bf4ebe4a5ade
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/14/2022
ms.locfileid: "63599282"
---
# <a name="troubleshoot-attack-surface-reduction-rules"></a>Fejlfinding af regler for reduktion af angrebsoverfladen

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)

Når du bruger [reduktionsregler for angrebsoverfladen](attack-surface-reduction.md) , kan du løbe ind i problemer, f.eks.:

- En regel blokerer en fil, proces eller udfører en anden handling, som den ikke bør (falsk positiv)
- En regel virker ikke som beskrevet eller blokerer ikke en fil eller proces, som den skal (falsk negativ)

Der er fire trin til fejlfinding af disse problemer:

1. [Bekræft forudsætninger](#confirm-prerequisites)
2. [Brug overvågningstilstand til at teste reglen](#use-audit-mode-to-test-the-rule)
3. [Tilføj udeladelse for den angivne regel](#add-exclusions-for-a-false-positive) (for falske positive)
4. [Sende supportlogfiler](#collect-diagnostic-data-for-file-submissions)

## <a name="confirm-prerequisites"></a>Bekræft forudsætninger

Regler for reduktion af angrebsoverfladen fungerer kun på enheder med følgende betingelser:

- Slutpunkter kører i Windows 10 Enterprise, version 1709 (også kaldet Fall Creators Update).

- Slutpunkter bruger Microsoft Defender Antivirus som den eneste antivirusbeskyttelsesapp. [Hvis du bruger et hvilket som helst andet antivirusprogram, Microsoft Defender Antivirus deaktivere sig selv](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-compatibility).

- [Beskyttelse i realtid er](/windows/security/threat-protection/microsoft-defender-antivirus/configure-real-time-protection-microsoft-defender-antivirus) aktiveret.

- Overvågningstilstand er ikke aktiveret. Brug Gruppepolitik til at angive reglen til **Deaktiveret** (værdi: **0**) som beskrevet i [Aktivér regler for reduktion af angrebsoverfladen](enable-attack-surface-reduction.md).

Hvis disse forudsætninger alle er opfyldt, skal du fortsætte til næste trin for at teste reglen i overvågningstilstand.

## <a name="use-audit-mode-to-test-the-rule"></a>Brug overvågningstilstand til at teste reglen

Du kan besøge webstedet Windows Defender Test i [demo.wd.microsoft.com](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) for at bekræfte, at reglerne for reduktion af angrebsoverfladen generelt fungerer for forudkonfigurerede scenarier og processer på en enhed, eller du kan bruge overvågningstilstand, der kun aktiverer regler for rapportering.

> [!NOTE]
> Defender for Endpoint-demowebstedet demo.wd.microsoft.com forældet og fjernes fremover.

Følg disse instruktioner i Brug [demonstrationsværktøjet](evaluate-attack-surface-reduction.md) til at se, hvordan regler for reduktion af angrebsoverfladen fungerer for at teste den specifikke regel, du støder på problemer med.

1. Aktivér overvågningstilstand for den bestemte regel, du vil teste. Brug Gruppepolitik til at indstille reglen til Overvågningstilstand **(værdi** : **2) som** beskrevet i [Aktivér regler for reduktion af angrebsoverfladen](enable-attack-surface-reduction.md). Overvågningstilstand tillader reglen at rapportere filen eller processen, men tillader stadig at køre den.

2. Udfør den aktivitet, der forårsager et problem (f.eks. åbne eller udføre filen eller processen, der skal blokeres, men tillades).

3. [Gennemse hændelseslogfilerne](attack-surface-reduction.md) for reduktion af angrebsoverfladen for at se, om reglen ville have blokeret filen eller processen, hvis reglen var blevet indstillet til **Aktiveret**.

Hvis en regel ikke blokerer en fil eller proces, som du forventer, at den skal blokere, skal du først kontrollere, om overvågningstilstand er aktiveret.

Overvågningstilstand er muligvis blevet aktiveret til test af en anden funktion eller af et automatiseret PowerShell-script, og den er muligvis ikke blevet deaktiveret, når testene er fuldført.

Hvis du har testet reglen med demoværktøjet og med overvågningstilstand, og regler for reduktion af angrebsoverfladen fungerer på forudkonfigurerede scenarier, men reglen ikke fungerer som forventet, skal du fortsætte til et af de følgende afsnit baseret på din situation:

1. Hvis reduktionsreglen for angrebsoverfladen blokerer noget, som den ikke bør blokere (også kaldet en falsk positiv), kan du først tilføje udelukkelse af reduktionsreglen for [angrebsoverfladen](#add-exclusions-for-a-false-positive).

2. Hvis reduktionsreglen for angrebsoverfladen ikke blokerer noget, som den bør blokere (også kaldet en falsk negativ), kan du fortsætte straks til det sidste trin og indsamle diagnostiske data og sende problemet til [os](#collect-diagnostic-data-for-file-submissions).

## <a name="add-exclusions-for-a-false-positive"></a>Tilføj udeladelse for en falsk positiv

Hvis reglen for reduktion af angrebsoverfladen blokerer noget, som det ikke bør blokere (også kaldet en falsk positiv), kan du tilføje udeladelsesforanstaltninger for at forhindre, at regler for reduktion af angrebsoverfladen evaluerer de ekskluderede filer eller mapper.

Hvis du vil tilføje en udelukkelse, skal du [se Tilpas reduktion af angrebsoverfladen](attack-surface-reduction-rules-deployment-implement.md#customize-attack-surface-reduction-rules).

> [!IMPORTANT]
> Du kan angive individuelle filer og mapper, der skal udelades, men du kan ikke angive individuelle regler.
> Det betyder, at alle filer eller mapper, der er udeladt, udelades fra alle asr-regler.

## <a name="report-a-false-positive-or-false-negative"></a>Rapportere en falsk positiv eller falsk negativ

Brug den [Windows Defender webbaserede indsendelsesformular til sikkerhedsintelligens](https://www.microsoft.com/wdsi/filesubmission) til at rapportere en falsk negativ eller falsk positiv for netværksbeskyttelse. Med et Windows E5-abonnement kan du også [angive et link til en tilknyttet besked](alerts-queue.md).

## <a name="collect-diagnostic-data-for-file-submissions"></a>Indsaml diagnostiske data til filindsendelser

Når du rapporterer et problem med regler for reduktion af angrebsoverfladen, bliver du bedt om at indsamle og indsende diagnostiske data, der kan bruges af Microsoft-support og tekniske teams til at foretage fejlfinding af problemer.

1. Åbn en kommandoprompt med administrator administrator og skift til Windows Defender mappe:

   ```console
   cd "c:\program files\windows defender"
   ```

2. Kør denne kommando for at generere diagnosticeringslogfilerne:

   ```console
   mpcmdrun -getfiles
   ```

3. Som standard gemmes de på `C:\ProgramData\Microsoft\Windows Defender\Support\MpSupportFiles.cab`. Vedhæft filen til indsendelsesformularen.

## <a name="related-articles"></a>Relaterede artikler

- [Regler for reduktion af angrebsoverflade](attack-surface-reduction.md)
- [Aktivér regler for reduktion af angrebsoverfladen](enable-attack-surface-reduction.md)
- [Evaluer regler for reduktion af angrebsoverfladen](evaluate-attack-surface-reduction.md)
