---
title: Blokering af klientfunktionsmåde
description: Blokering af klientfunktionsmåden er en del af funktionaliteten til blokering af funktionsmåder og Microsoft Defender for Endpoint
keywords: blokering af funktionsmåder, hurtig beskyttelse, klientfunktionsmåde Microsoft Defender for Endpoint
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
ms.openlocfilehash: 8da3f04af66568bbe79dd6a74c38b30a8a1ab891
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64470213"
---
# <a name="client-behavioral-blocking"></a>Blokering af klientfunktionsmåde

**Gælder for:**
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

## <a name="overview"></a>Oversigt

Blokering af klientfunktionsmåden er en komponent [af egenskaber til blokering af funktionsmåder og spærring](behavioral-blocking-containment.md) i Defender til slutpunkt. Da mistænkelige funktionsmåder registreres på enheder (også kaldet klienter eller slutpunkter), blokeres, kontrolleres og afhjælpes artefakter (f.eks. filer eller programmer) automatisk.

:::image type="content" source="images/pre-execution-and-post-execution-detection-engines.png" alt-text="Sky- og klientbeskyttelse" lightbox="images/pre-execution-and-post-execution-detection-engines.png":::

Antivirusbeskyttelse fungerer bedst, når de parres med skybeskyttelse.

## <a name="how-client-behavioral-blocking-works"></a>Sådan fungerer blokering af klientfunktionsmåden

[Microsoft Defender Antivirus](microsoft-defender-antivirus-in-windows-10.md) kan registrere mistænkelig adfærd, skadelig kode, filløse og in-memory-angreb og meget mere på en enhed. Når der registreres mistænkelige funktionsmåder, Microsoft Defender Antivirus overvåger og sender disse mistænkelige funktionsmåder og deres procestræer til skybeskyttelsestjenesten. Maskinel indlæring skelner mellem skadelige programmer og gode funktionsmåder i millisekunder og klassificerer hver artefakt. I næsten realtid blokeres en artefakt på enheden, så snart en artefakt findes skadelig.

Når der registreres en mistænkelig adfærd, genereres der en besked, og den er synlig i [Microsoft 365 Defender-portalen](/microsoft-365/security/defender/microsoft-365-defender) (tidligere Microsoft 365 Defender).[](alerts-queue.md)

Blokering af klientfunktionsmåden er effektiv, fordi det ikke kun er med til at forhindre et angreb i at starte, det kan hjælpe med at stoppe et angreb, der er begyndt at blive udført. Og med blokering [af feedbackløkker](feedback-loop-blocking.md) (andre muligheder for blokering og inddæmmelse af adfærd) forhindres angreb på andre enheder i organisationen.

## <a name="behavior-based-detections"></a>Adfærdsbaserede registreringer

Adfærdsbaserede registreringer er navngivet i henhold til [MITRE ATT&CK-matrix til Enterprise](https://attack.mitre.org/matrices/enterprise). Navngivningskonventionen hjælper med at identificere angrebsfasen, hvor den ondsindede adfærd er blevet observeret:

|Tactic|Registrering af trusselsnavn|
|---|---|
|Startadgang|`Behavior:Win32/InitialAccess.*!ml`|
|Eksekvering|`Behavior:Win32/Execution.*!ml`|
|Vedholdenhed|`Behavior:Win32/Persistence.*!ml`|
|Rettighedseskalering|`Behavior:Win32/PrivilegeEscalation.*!ml`|
|Forsvar|`Behavior:Win32/DefenseEvasion.*!ml`|
|Adgang til legitimationsoplysninger|`Behavior:Win32/CredentialAccess.*!ml`|
|Discovery|`Behavior:Win32/Discovery.*!ml`|
|Lateral Movement|`Behavior:Win32/LateralMovement.*!ml`|
|Samling|`Behavior:Win32/Collection.*!ml`|
|Kommando og styring|`Behavior:Win32/CommandAndControl.*!ml`|
|Udfyldning|`Behavior:Win32/Exfiltration.*!ml`|
|Virkning|`Behavior:Win32/Impact.*!ml`|
|Ikke kategoriseret|`Behavior:Win32/Generic.*!ml`|

> [!TIP]
> Du kan få mere at vide om specifikke trusler i **[den seneste globale trusselsaktivitet](https://www.microsoft.com/wdsi/threats)**.

## <a name="configuring-client-behavioral-blocking"></a>Konfiguration af blokering af klientfunktionsmåde

Hvis din organisation bruger Defender til slutpunkt, er blokering af klientfunktionsmåden aktiveret som standard. Men hvis du vil have fordel af alle Defender til slutpunkt-funktioner, herunder blokering og blokering af [funktionsmåder,](behavioral-blocking-containment.md) skal du sørge for, at følgende funktioner og egenskaber for Defender til Slutpunkt er aktiveret og konfigureret:

- [Defender for grundlinjer for slutpunkter](configure-machines-security-baseline.md)
- [Enheder, der er onboardet til Defender til Slutpunkt](onboard-configure.md)
- [Slutpunktsregistrering og -svar i bloktilstand](edr-in-block-mode.md)
- [Reduktion af angrebsoverfladen](attack-surface-reduction.md)
- [Næste generations beskyttelse](configure-microsoft-defender-antivirus-features.md) (antivirus, antimalware og andre muligheder for trusselsbeskyttelse)
