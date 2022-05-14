---
title: Konfigurer timeoutperioden for Microsoft Defender Antivirus cloudblokering
description: Du kan konfigurere, hvor længe Microsoft Defender Antivirus blokerer en fil fra at køre, mens du venter på en cloudbestemmelse.
keywords: Microsoft Defender Antivirus, antimalware, sikkerhed, defender, cloud, timeout, blok, periode, sekunder
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
ms.openlocfilehash: 0ad46ff70ed2542ebed423a02eba6cc0810a99ca
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/14/2022
ms.locfileid: "65418756"
---
# <a name="configure-the-cloud-block-timeout-period"></a>Konfigurer timeoutperioden for skyblokering

**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Antivirus

**Platforme**
- Windows

Når Microsoft Defender Antivirus finder en mistænkelig fil, kan det forhindre filen i at køre, mens den forespørger [Microsoft Defender Antivirus cloudtjenesten](cloud-protection-microsoft-defender-antivirus.md).

Standardperioden for, at filen [er blokeret](configure-block-at-first-sight-microsoft-defender-antivirus.md) , er 10 sekunder. Hvis du er sikkerhedsadministrator, kan du angive, at der skal ventes mere, før filen kan køre. Hvis du forlænger timeoutperioden for cloudblokering, kan det hjælpe med at sikre, at der er tilstrækkelig tid til at modtage en korrekt bestemmelse fra Microsoft Defender Antivirus cloudtjenesten.

## <a name="prerequisites-to-use-the-extended-cloud-block-timeout"></a>Forudsætninger for at bruge den udvidede timeout for cloudblokering

[Blok ved første øjekast](configure-block-at-first-sight-microsoft-defender-antivirus.md) , og dens forudsætninger skal være aktiveret, før du kan angive en udvidet timeoutperiode.

## <a name="specify-the-extended-timeout-period-using-microsoft-endpoint-manager"></a>Angiv den forlængede timeoutperiode ved hjælp af Microsoft Endpoint Manager

Du kan angive timeoutperioden for skyblokering med en [sikkerhedspolitik for slutpunkter i Microsoft Endpoint Manager](/mem/intune/protect/endpoint-security-policy).

1. Gå til Endpoint Manager Administration ([https://endpoint.microsoft.com/](https://endpoint.microsoft.com/)), og log på.

2. Vælg **Slutpunktssikkerhed**, og vælg derefter **Antivirus** under **Administrer**.

3. Vælg (eller opret) en antiviruspolitik.

4. I afsnittet **Konfigurationsindstillinger** skal du udvide **Cloudbeskyttelse**. I feltet **udvidet timeout i sekunder i Microsoft Defender Antivirus** skal du derefter angive, hvor lang tid der skal gå, i sekunder, fra 1 sekund til 50 sekunder. Uanset hvad du angiver, føjes til standarden 10 sekunder.

5. (Dette trin er valgfrit) Foretag andre ændringer af antiviruspolitikken. (Har du brug for hjælp? Se [Indstillinger for Microsoft Defender Antivirus politik i Microsoft Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-windows).)

6. Vælg **Næste**, og afslut konfigurationen af politikken.

## <a name="specify-the-extended-timeout-period-using-group-policy"></a>Angiv den forlængede timeoutperiode ved hjælp af Gruppepolitik

Du kan bruge Gruppepolitik til at angive en udvidet timeout for cloudkontroller.

1. Åbn [administrationskonsollen Gruppepolitik Gruppepolitik](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))

2. Højreklik på det Gruppepolitik objekt, du vil konfigurere, og vælg derefter **Rediger**.

3. I **Gruppepolitik Management Editor** skal du gå til **Computerkonfiguration** og derefter vælge **Administrative skabeloner**.

3. Udvid træet for at **Windows komponenter** \> **Microsoft Defender Antivirus** \> **MpEngine**.

4. Dobbeltklik på **Konfigurer udvidet skykontrol** , og kontrollér, at indstillingen er aktiveret. 

   Angiv den ekstra mængde tid, der skal til for at forhindre, at filen kører, mens der afventes en bestemmelse i skyen. Angiv den ekstra tid i sekunder fra 1 sekund til 50 sekunder. Uanset hvad du angiver, føjes til standarden 10 sekunder.

5. Vælg **OK**.

> [!TIP]
> Hvis du leder efter antivirusrelaterede oplysninger til andre platforme, kan du se:
> - [Angiv indstillinger for Microsoft Defender for Endpoint på macOS-](mac-preferences.md)
> - [Microsoft Defender for Endpoint på Mac](microsoft-defender-endpoint-mac.md)
> - [Politikindstillinger for macOS Antivirus for Microsoft Defender Antivirus for Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Angiv indstillinger for Microsoft Defender for Endpoint på Linux](linux-preferences.md)
> - [Microsoft Defender for Endpoint på Linux](microsoft-defender-endpoint-linux.md)
> - [Konfigurer Defender for Endpoint på Android-funktioner](android-configure.md)
> - [Konfigurer Microsoft Defender for Endpoint på iOS-funktioner](ios-configure-features.md) 
