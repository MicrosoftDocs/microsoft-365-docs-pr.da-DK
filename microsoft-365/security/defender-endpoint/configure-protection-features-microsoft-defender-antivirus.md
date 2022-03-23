---
title: Aktivér og konfigurer Microsoft Defender Antivirus beskyttelsesfunktioner
description: Aktivér behavior-based, heuristic, and real-time protection in Microsoft Defender AV.
keywords: heuristisk, maskinel indlæring, overvågning af adfærd, beskyttelse i realtid, altid tændt, Microsoft Defender Antivirus, antimalware, sikkerhed, defender
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.topic: article
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.collection: M365-security-compliance
ms.openlocfilehash: f949623b7d0647d71f4c665ed2016ee14a765e5f
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/14/2022
ms.locfileid: "63592361"
---
# <a name="configure-behavioral-heuristic-and-real-time-protection"></a>Konfigurer funktionsmåde-, heuristisk- og realtidsbeskyttelse


**Gælder for:**

- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Microsoft Defender Antivirus bruger flere forskellige metoder til at yde trusselsbeskyttelse:

- Skybeskyttelse til øjeblikkelig registrering og blokering af nye og nye trusler
- Altid til scanning ved hjælp af overvågning af fil- og procesfunktionsmåder og anden heuristics (også kaldet "beskyttelse i realtid")
- Dedikerede opdateringer til beskyttelse, der er baseret på maskinlæring, mennesker og automatiseret analyse af big-data og dybdegående forskning om trusselsmodstand

Du kan konfigurere, hvordan Microsoft Defender Antivirus bruger disse metoder med Gruppepolitik, System Center Configuration Manage, PowerShell-cmdlet'er og Windows Management Instrumentation (WMI).

Dette afsnit omhandler konfiguration til altid-on-scanning, herunder hvordan du registrerer og blokerer apps, der anses for at være usikre, men som muligvis ikke registreres som malware.

Se [Brug næste generations teknologi Microsoft Defender Antivirus skybeskyttelse for at](cloud-protection-microsoft-defender-antivirus.md) få mere at vide om, hvordan du aktiverer og konfigurerer Microsoft Defender Antivirus skybeskyttelse.

## <a name="in-this-section"></a>I dette afsnit

| Emne|Beskrivelse |
|---|---|
| [Find og bloker potentielt uønskede programmer](detect-block-potentially-unwanted-apps-microsoft-defender-antivirus.md)| Find og bloker apps, der kan være uønskede i dit netværk, f.eks. browsermoderatorer og værktøjslinjer samt programmer til problemer eller falske antivirusprogrammer |
| [Aktivere og Microsoft Defender Antivirus egenskaber for beskyttelse](configure-real-time-protection-microsoft-defender-antivirus.md)|Aktivér og konfigurer beskyttelse i realtid, heuristics og andre funktioner til altid Microsoft Defender Antivirus realtidsovervågningsfunktioner |
