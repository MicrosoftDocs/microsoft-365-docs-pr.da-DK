---
title: blokering af klientfunktionsmåder
description: Blokering af klientens funktionsmåde er en del af funktionsmådeblokering og funktionalitet til opbevaring på Microsoft Defender for Endpoint
keywords: adfærdsblokering, hurtig beskyttelse, klientfunktionsmåde Microsoft Defender for Endpoint
ms.pagetype: security
author: denisebmsft
ms.author: deniseb
manager: dansimp
ms.reviewer: shwetaj
audience: ITPro
ms.topic: article
ms.prod: m365-security
ms.localizationpriority: medium
ms.custom:
- next-gen
- edr
ms.collection: m365-security-compliance
ms.technology: mde
ms.openlocfilehash: f19e354a23af03abd905591993197ff8f484ceff
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/12/2022
ms.locfileid: "64788386"
---
# <a name="client-behavioral-blocking"></a>blokering af klientfunktionsmåder

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Microsoft Defender Antivirus

**Platform**
- Windows

> Vil du gerne opleve Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

## <a name="overview"></a>Oversigt

Blokering af klientfunktionsmåden er en komponent i [funktionsblokering og opbevaringsfunktioner](behavioral-blocking-containment.md) i Defender for Endpoint. Da mistænkelig adfærd registreres på enheder (også kaldet klienter eller slutpunkter), blokeres, kontrolleres og afhjælpes artefakter (f.eks. filer eller programmer) automatisk.

:::image type="content" source="images/pre-execution-and-post-execution-detection-engines.png" alt-text="Cloud- og klientbeskyttelse" lightbox="images/pre-execution-and-post-execution-detection-engines.png":::

Antivirusbeskyttelse fungerer bedst, når den kombineres med cloudbeskyttelse.

## <a name="how-client-behavioral-blocking-works"></a>Sådan fungerer blokering af klientens funktionsmåde

[Microsoft Defender Antivirus](microsoft-defender-antivirus-in-windows-10.md) kan registrere mistænkelig adfærd, skadelig kode, filuafhængige angreb og angreb i hukommelsen m.m. på en enhed. Når der registreres mistænkelig adfærd, overvåger Microsoft Defender Antivirus og sender disse mistænkelige funktionsmåder og deres procestræer til cloudbeskyttelsestjenesten. Maskinel indlæring skelner mellem skadelige programmer og god funktionsmåde i millisekunder og klassificerer hver artefakt. Så snart en artefakt er ondsindet i næsten realtid, blokeres den på enheden.

Når der registreres en mistænkelig funktionsmåde, genereres der en [besked](alerts-queue.md), som er synlig, mens angrebet blev registreret og stoppet. beskeder, f.eks. en "indledende adgangsbesked", udløses og vises på [Microsoft 365 Defender-portalen](/microsoft-365/security/defender/microsoft-365-defender) (tidligere Microsoft 365 Defender).

Blokering af klientens funktionsmåde er effektiv, fordi det ikke kun hjælper med at forhindre et angreb i at starte. Det kan hjælpe med at stoppe et angreb, der er begyndt at blive udført. Og med [blokering af feedbackløkke](feedback-loop-blocking.md) (en anden funktion til adfærdsblokering og indeslutning) forhindres angreb på andre enheder i din organisation.

## <a name="behavior-based-detections"></a>Adfærdsbaserede registreringer

Funktionsbaserede registreringer navngives i henhold til [MITRE ATT-&CK-matrixen for Enterprise](https://attack.mitre.org/matrices/enterprise). Navngivningskonventionen hjælper med at identificere den angrebsfase, hvor den skadelige funktionsmåde blev observeret:

|Taktik|Navn på opdagelsestrussel|
|---|---|
|Indledende adgang|`Behavior:Win32/InitialAccess.*!ml`|
|Udførelse|`Behavior:Win32/Execution.*!ml`|
|Persistens|`Behavior:Win32/Persistence.*!ml`|
|Rettighedseskalering|`Behavior:Win32/PrivilegeEscalation.*!ml`|
|Forsvarsunddragelse|`Behavior:Win32/DefenseEvasion.*!ml`|
|Adgang til legitimationsoplysninger|`Behavior:Win32/CredentialAccess.*!ml`|
|Opdagelse|`Behavior:Win32/Discovery.*!ml`|
|Tværgående bevægelse|`Behavior:Win32/LateralMovement.*!ml`|
|Samling|`Behavior:Win32/Collection.*!ml`|
|Kommando og kontrolelement|`Behavior:Win32/CommandAndControl.*!ml`|
|Eksfiltration|`Behavior:Win32/Exfiltration.*!ml`|
|Indvirkning|`Behavior:Win32/Impact.*!ml`|
|Uncategorized|`Behavior:Win32/Generic.*!ml`|

> [!TIP]
> Hvis du vil vide mere om specifikke trusler, kan **[du se den seneste globale trusselsaktivitet](https://www.microsoft.com/wdsi/threats)**.

## <a name="configuring-client-behavioral-blocking"></a>Konfiguration af blokering af klientfunktionsmåde

Hvis din organisation bruger Defender for Endpoint, er blokering af klientens funktionsmåde som standard aktiveret. Hvis du vil drage fordel af alle Defender for Endpoint-funktioner, herunder [funktionsblokering og indeslutning](behavioral-blocking-containment.md), skal du dog sørge for, at følgende funktioner og funktioner i Defender for Endpoint er aktiveret og konfigureret:

- [Defender for endpoint baselines](configure-machines-security-baseline.md)
- [Enheder, der er onboardet til Defender for Endpoint](onboard-configure.md)
- [EDR i bloktilstand](edr-in-block-mode.md)
- [Reduktion af angrebsoverfladen](attack-surface-reduction.md)
- [Næste generations beskyttelse](configure-microsoft-defender-antivirus-features.md) (antivirus, antimalware og andre trusselsbeskyttelsesfunktioner)

> [!TIP]
> Hvis du leder efter antivirusrelaterede oplysninger til andre platforme, kan du se:
> - [Angiv indstillinger for Microsoft Defender for Endpoint på macOS](mac-preferences.md)
> - [Microsoft Defender for Endpoint på Mac](microsoft-defender-endpoint-mac.md)
> - [macOS Antivirus politikindstillinger for Microsoft Defender Antivirus til Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Angiv indstillinger for Microsoft Defender for Endpoint på Linux](linux-preferences.md)
> - [Microsoft Defender for Endpoint på Linux](microsoft-defender-endpoint-linux.md)
> - [Konfigurer Defender for Endpoint på Android-funktioner](android-configure.md)
> - [Konfigurer Microsoft Defender for Endpoint på iOS-funktioner](ios-configure-features.md)
