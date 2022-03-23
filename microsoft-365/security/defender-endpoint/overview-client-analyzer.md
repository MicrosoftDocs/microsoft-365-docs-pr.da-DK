---
title: Fejlfinding af sensorens tilstand ved hjælp af Microsoft Defender til Endpoint Client Analyzer
description: Fejlfinding af sensorens tilstand på enheder for at identificere potentielle problemer med konfiguration, miljø, forbindelse eller telemetri, der påvirker sensordata eller -funktionalitet.
keywords: sensor, sensor sundhed, forkert konfigureret, inaktiv, ingen sensordata, sensordata, forringet kommunikation, kommunikation
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 0de2fbe98527d8fe36f2b8c5d5db0453988501a7
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63593971"
---
# <a name="troubleshoot-sensor-health-using-microsoft-defender-for-endpoint-client-analyzer"></a>Fejlfinding af sensorens tilstand ved hjælp af Microsoft Defender til Endpoint Client Analyzer

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Microsoft Defender til Endpoint Client Analyzer (MDECA) kan være nyttig, når du diagnosticerer problemer med sensorens tilstand eller pålidelighed på [onboardede](/microsoft-365/security/defender-endpoint/onboard-configure) enheder, der kører enten Windows, Linux eller macOS. Det kan f.eks. være, at du vil køre analyseenheden på en computer, der ser ud til at være usund i henhold til den viste [tilstand for sensoren](/microsoft-365/security/defender-endpoint/fix-unhealthy-sensors) (Inaktiv, Ingen sensordata eller Forringet kommunikation) på sikkerhedsportalen.

Ud over indlysende problemer med sensorens tilstand kan MDECA indsamle andre sporinger, logfiler og diagnostiske oplysninger til fejlfinding af komplekse scenarier som f.eks.:

- Programkompatibilitet (AppCompat), ydeevne, netværksforbindelse eller
- Uventet adfærd relateret til [forebyggelse af datatab på slutpunkter](/microsoft-365/compliance/endpoint-dlp-learn-about).

## <a name="privacy-notice"></a>Meddelelse om beskyttelse af personlige oplysninger

- Værktøjet Microsoft Defender for Endpoint Client Analyzer bruges regelmæssigt af Microsofts kundesupporttjenester (CSS) til at indsamle oplysninger, der kan hjælpe dig med at foretage fejlfinding af de problemer, du oplever med Microsoft Defender til slutpunktet.

- De indsamlede data kan indeholde personidentificerbare oplysninger (PII) og/eller følsomme data, f.eks. (men ikke begrænset til) IP-adresser, pc-navne og brugernavne.

- Når dataindsamlingen er fuldført, gemmer værktøjet dataene lokalt på computeren i en undermappe og komprimeret zip-fil.

- Der sendes ingen data til Microsoft automatisk. Hvis du bruger værktøjet under samarbejde om et supportproblem, kan du blive bedt om at sende de komprimerede data til Microsoft CSS ved hjælp af Secure File Exchange for at lette undersøgelsen af problemet.

Du kan finde flere oplysninger om secure file Exchange i Sådan bruger du [Secure File Exchange til at udveksle filer med Microsoft Support](/troubleshoot/azure/general/secure-file-exchange-transfer-files)

Du kan finde flere oplysninger om vores erklæring om beskyttelse af personlige oplysninger [i Microsofts erklæring om beskyttelse af personlige oplysninger](https://privacy.microsoft.com/privacystatement).

## <a name="requirements"></a>Krav

- Før du kører analyseprogrammet, anbefaler vi, at du sikrer, at din proxy- eller firewallkonfiguration tillader adgang til [URL-adresser for Microsoft Defender for Endpoint-tjenesten](configure-proxy-internet.md#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server).

- Analyseanalysen kan køre på understøttede udgaver [af Windows](minimum-requirements.md#supported-windows-versions), [Linux](microsoft-defender-endpoint-linux.md#system-requirements) eller [macOS](microsoft-defender-endpoint-mac.md#system-requirements), enten før efter onboarding til Microsoft Defender til slutpunkt.

- For Windows enheder skal SysInternalsPsExec.exehave tilladelse til (i hvert fald midlertidigt) at køre, hvis du kører analysatoren direkte på [ bestemte ](/sysinternals/downloads/psexec) computere og ikke eksternt via [Live Response](/microsoft-365/security/defender-endpoint/troubleshoot-collect-support-log). Analyseværktøjet ringer op PsExec.exe forbindelsesværktøjet til at køre forbindelseskontroller i skyen som lokalt system og emulere FUNKTIONSMÅDEn for SENSE-tjenesten.

    > [!NOTE]
    > På Windows-enheder vil du, hvis du bruger ASR-reglen Bloker procesoprettelser, der stammer fra [PSExec- og WMI-kommandoer](attack-surface-reduction-rules-reference.md#block-process-creations-originating-from-psexec-and-wmi-commands), muligvis deaktivere reglen midlertidigt eller konfigurere en udelukkelse til [ASR-reglen](enable-attack-surface-reduction.md#exclude-files-and-folders-from-asr-rules) for at tillade analyseator at køre forbindelseskontrol til skyen som forventet.
