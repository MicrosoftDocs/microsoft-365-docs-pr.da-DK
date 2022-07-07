---
title: Foretag fejlfinding af sensortilstand ved hjælp af Microsoft Defender for Endpoint Klientanalyse
description: Foretag fejlfinding af sensortilstand på enheder for at identificere potentielle problemer med konfiguration, miljø, forbindelse eller telemetri, der påvirker sensordata eller -funktionalitet.
keywords: sensor, sensortilstand, forkert konfigureret, inaktiv, ingen sensordata, sensordata, nedsat kommunikation, kommunikation
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
ms.openlocfilehash: cad957dff57da6598e7b7db470998979d2bd0f63
ms.sourcegitcommit: 1734c95ce72d9c8af695cb4b49b1e40d921a1fee
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/07/2022
ms.locfileid: "66685586"
---
# <a name="troubleshoot-sensor-health-using-microsoft-defender-for-endpoint-client-analyzer"></a>Foretag fejlfinding af sensortilstand ved hjælp af Microsoft Defender for Endpoint Klientanalyse

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

MDECA (Microsoft Defender for Endpoint Client Analyzer) kan være nyttig, når du diagnosticerer problemer med sensortilstand eller pålidelighed på [onboardede enheder](/microsoft-365/security/defender-endpoint/onboard-configure), der kører enten Windows, Linux eller macOS. Det kan f.eks. være, at du vil køre analysen på en maskine, der ser ud til at være usund i henhold til den viste [sensortilstandsstatus](/microsoft-365/security/defender-endpoint/fix-unhealthy-sensors) (Inaktiv, Ingen sensordata eller Nedsat kommunikation) på sikkerhedsportalen.

Ud over indlysende problemer med sensortilstand kan MDECA indsamle andre sporinger, logge og diagnosticeringsoplysninger til fejlfinding af komplekse scenarier, f.eks.:

- Programkompatibilitet (AppCompat), ydeevne, netværksforbindelse eller
- Uventet funktionsmåde relateret til [Forebyggelse af datatab for slutpunkt](/microsoft-365/compliance/endpoint-dlp-learn-about).

## <a name="privacy-notice"></a>Meddelelse om beskyttelse af personlige oplysninger

- Værktøjet Microsoft Defender for Endpoint Client Analyzer bruges jævnligt af Microsoft Customer Support Services (CSS) til at indsamle oplysninger, der kan hjælpe med fejlfinding af problemer, du kan opleve med Microsoft Defender for Endpoint.

- De indsamlede data kan indeholde personidentificerbare oplysninger og/eller følsomme data, f.eks. (men ikke begrænset til) IP-adresser, pc-navne og brugernavne.

- Når dataindsamlingen er fuldført, gemmer værktøjet dataene lokalt på computeren i en undermappe og en komprimeret ZIP-fil.

- Der sendes automatisk ingen data til Microsoft. Hvis du bruger værktøjet under samarbejdet om et supportproblem, bliver du muligvis bedt om at sende de komprimerede data til Microsoft CSS ved hjælp af Secure File Exchange for at lette undersøgelsen af problemet.

Du kan få flere oplysninger om Sikker filudveksling under [Sådan bruger du Sikker filudveksling til at udveksle filer med Microsoft Support](/troubleshoot/azure/general/secure-file-exchange-transfer-files)

Du kan få flere oplysninger om vores erklæring om beskyttelse [af personlige oplysninger under Microsofts erklæring om beskyttelse af personlige oplysninger](https://privacy.microsoft.com/privacystatement).

## <a name="requirements"></a>Krav

- Før du kører analysen, anbefaler vi, at du sikrer, at din proxy- eller firewallkonfiguration giver adgang til [Microsoft Defender for Endpoint tjeneste-URL-adresser](configure-proxy-internet.md#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server).

- Analysefunktionen kan køre på understøttede udgaver af [Windows](minimum-requirements.md#supported-windows-versions), [Linux](microsoft-defender-endpoint-linux.md#system-requirements) eller [macOS](microsoft-defender-endpoint-mac.md#system-requirements) enten før efter onboarding til Microsoft Defender for Endpoint.

- Hvis du kører analysefunktionen direkte på bestemte computere og ikke eksternt via [Live Response](/microsoft-365/security/defender-endpoint/troubleshoot-collect-support-log) på Windows-enheder, skal SysInternals [ -PsExec.exe](/sysinternals/downloads/psexec) have tilladelse til at køre (i det mindste midlertidigt). Analysefunktionen kalder PsExec.exe værktøj for at køre kontrol af cloudforbindelsen som Lokalt system og emulere funktionsmåden for SENSE-tjenesten.

    > [!NOTE]
    > Hvis du på Windows-enheder bruger ASR-regel (Attack Surface Reduction) [Bloker procesoprettelser, der stammer fra PSExec- og WMI-kommandoer](attack-surface-reduction-rules-reference.md#block-process-creations-originating-from-psexec-and-wmi-commands), kan det være en god idé midlertidigt at deaktivere reglen eller [konfigurere en udeladelse af ASR-reglen](enable-attack-surface-reduction.md#exclude-files-and-folders-from-asr-rules) for at gøre det muligt for analysefunktionen at køre forbindelseskontrol til clouden som forventet.
