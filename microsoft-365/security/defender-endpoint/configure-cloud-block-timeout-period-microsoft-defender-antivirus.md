---
title: Konfigurere tidsperioden Microsoft Defender Antivirus skyblokering
description: Du kan konfigurere, hvor længe Microsoft Defender Antivirus vil forhindre en fil i at køre, mens du venter på en bestemmelse i skyen.
keywords: Microsoft Defender Antivirus, antimalware, sikkerhed, defender, sky, timeout, blok, periode, sekunder
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
ms.date: 10/18/2021
ms.collection: M365-security-compliance
ms.openlocfilehash: 1acd1a95ddc3aa679f0e5f1295e14cf33b4f97a0
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2021
ms.locfileid: "63599354"
---
# <a name="configure-the-cloud-block-timeout-period"></a>Konfigurere tidsperioden for skyblokering

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Når Microsoft Defender Antivirus finder en mistænkelig fil, kan den forhindre filen i at køre, mens den forespørger [på Microsoft Defender Antivirus skytjenesten](cloud-protection-microsoft-defender-antivirus.md).

Standardperioden for, at filen [blokeres,](configure-block-at-first-sight-microsoft-defender-antivirus.md) er 10 sekunder. Hvis du er sikkerhedsadministrator, kan du angive mere tid, der skal ventes, før filen får tilladelse til at køre. En forlængelse af tidsperioden for skyen kan hjælpe med at sikre, at der er tilstrækkelig tid til at modtage en passende bestemmelse Microsoft Defender Antivirus skytjenesten.

## <a name="prerequisites-to-use-the-extended-cloud-block-timeout"></a>Forudsætninger for at bruge den udvidede timeout for skyblokering

[Bloker ved første syn](configure-block-at-first-sight-microsoft-defender-antivirus.md) og dens forudsætninger skal aktiveres, før du kan angive en udvidet timeoutperiode.

## <a name="specify-the-extended-timeout-period-using-microsoft-endpoint-manager"></a>Angiv den udvidede timeoutperiode med Microsoft Endpoint Manager

Du kan angive tidsperioden for skyblokering med [en slutpunktssikkerhedspolitik i Microsoft Endpoint Manager](/mem/intune/protect/endpoint-security-policy).

1. Gå til Endpoint Manager Administration ([https://endpoint.microsoft.com/](https://endpoint.microsoft.com/)), og log på.

2. Vælg **Slutpunktssikkerhed**, og vælg **derefter** **Antivirus under Administrer**.

3. Vælg (eller opret) en antiviruspolitik.

4. I sektionen **Konfigurationsindstillinger** skal du udvide **Skybeskyttelse**. I feltet Microsoft Defender Antivirus **Timeout** i sekunder skal du angive mere tid, i sekunder, fra 1 sekund til 50 sekunder. Det, du angiver, føjes til de 10 standardsekunder.

5. (Dette trin er valgfrit) Foretag andre ændringer af din antiviruspolitik. (Har du brug for hjælp? Se [Indstillinger for Microsoft Defender Antivirus politik i Microsoft Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-windows)).

6. Vælg **Næste**, og afslut konfigurationen af din politik.

## <a name="specify-the-extended-timeout-period-using-group-policy"></a>Angiv den udvidede timeoutperiode med Gruppepolitik

Du kan bruge Gruppepolitik til at angive en udvidet timeout for skykontroller.

1. På Gruppepolitik administrationscomputer skal du åbne [Gruppepolitik administrationskonsollen](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))

2. Højreklik på det Gruppepolitik objekt, du vil konfigurere, og vælg derefter **Rediger**.

3. I **administrationseditoren Gruppepolitik** skal du gå **til Computerkonfiguration** og derefter vælge **Administrative skabeloner**.

3. Udvid træet til **Windows komponenter** \> **Microsoft Defender Antivirus** \> **MpEngine**.

4. Dobbeltklik på Konfigurer **udvidet skykontrol, og** sørg for, at indstillingen er aktiveret. 

   Angiv den ekstra tid, der skal være for at forhindre filen i at køre, mens du venter på en bestemmelse i skyen. Angiv den ekstra tid i sekunder fra 1 sekund til 50 sekunder. Det, du angiver, føjes til de 10 standardsekunder.

5. Vælg **OK**.

 
