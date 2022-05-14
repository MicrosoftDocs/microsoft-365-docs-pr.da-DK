---
title: Blokering af feedbackløkker
description: Blokering af feedbackløkke, også kaldet hurtig beskyttelse, er en del af funktionsblokering og indeslutningsfunktioner i Microsoft Defender for Endpoint
keywords: adfærdsblokering, hurtig beskyttelse, blokering af feedback, Microsoft Defender for Endpoint
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
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: da3f16837b8715fe791fbd8abf48acb657fd4963
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/14/2022
ms.locfileid: "65416766"
---
# <a name="feedback-loop-blocking"></a>Blokering af feedbackløkker

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- Microsoft Defender Antivirus

**Platforme**
- Windows

## <a name="overview"></a>Oversigt

Blokering af feedbackløkke, også kaldet hurtig beskyttelse, er en komponent i [funktionsblokering og indeslutningsfunktioner](/microsoft-365/security/defender-endpoint/behavioral-blocking-containment) i [Microsoft Defender for Endpoint](/windows/security/threat-protection/). Med blokering af feedbackløkke er enheder på tværs af din organisation bedre beskyttet mod angreb. 

## <a name="how-feedback-loop-blocking-works"></a>Sådan fungerer blokering af feedbackløkke

Når der registreres en mistænkelig funktionsmåde eller fil, f.eks. af [Microsoft Defender Antivirus](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-in-windows-10), sendes oplysninger om dette artefakt til flere klassificeringer. Programmet til hurtig beskyttelse af løkker undersøger og korrelerer oplysningerne med andre signaler for at nå frem til en beslutning om, hvorvidt en fil skal blokeres. Kontrol og klassificering af artefakter sker hurtigt. Det resulterer i hurtig blokering af bekræftet malware og driver beskyttelse på tværs af hele økosystemet. 

Med hurtig beskyttelse på plads kan et angreb stoppes på en enhed, andre enheder i organisationen og enheder i andre organisationer, da et angreb forsøger at udvide sin fodfæste.


## <a name="configuring-feedback-loop-blocking"></a>Konfiguration af blokering af feedbackløkke

Hvis din organisation bruger Defender for Endpoint, er blokering af feedbackløkke som standard aktiveret. Hurtig beskyttelse sker dog via en kombination af Defender for Endpoint-funktioner, funktioner til beskyttelse af maskinel indlæring og signaldeling på tværs af Microsoft-sikkerhedstjenester. Sørg for, at følgende funktioner og funktioner i Defender for Endpoint er aktiveret og konfigureret:

- [Microsoft Defender for Endpoint oprindelige planer](/microsoft-365/security/defender-endpoint/configure-machines-security-baseline)

- [Enheder, der er onboardet til Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/onboard-configure)

- [EDR i bloktilstand](/microsoft-365/security/defender-endpoint/edr-in-block-mode)

- [Reduktion af angrebsoverfladen](/microsoft-365/security/defender-endpoint/attack-surface-reduction)

- [Næste generations beskyttelse](/windows/security/threat-protection/microsoft-defender-antivirus/configure-microsoft-defender-antivirus-features) (antivirus)

> [!TIP]
> Hvis du leder efter antivirusrelaterede oplysninger til andre platforme, kan du se:
> - [Angiv indstillinger for Microsoft Defender for Endpoint på macOS-](mac-preferences.md)
> - [Microsoft Defender for Endpoint på Mac](microsoft-defender-endpoint-mac.md)
> - [Politikindstillinger for macOS Antivirus for Microsoft Defender Antivirus for Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Angiv indstillinger for Microsoft Defender for Endpoint på Linux](linux-preferences.md)
> - [Microsoft Defender for Endpoint på Linux](microsoft-defender-endpoint-linux.md)
> - [Konfigurer Defender for Endpoint på Android-funktioner](android-configure.md)
> - [Konfigurer Microsoft Defender for Endpoint på iOS-funktioner](ios-configure-features.md)

## <a name="related-articles"></a>Relaterede artikler

- [Blokering og opbevaring af funktionsmåder](behavioral-blocking-containment.md)

- [(Blog) Adfærdsblokering og -opbevaring: Omdan optik til beskyttelse](https://www.microsoft.com/security/blog/2020/03/09/behavioral-blocking-and-containment-transforming-optics-into-protection/)

- [Nyttige Microsoft Defender for Endpoint ressourcer](/microsoft-365/security/defender-endpoint/helpful-resources)
