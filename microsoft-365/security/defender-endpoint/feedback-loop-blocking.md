---
title: Blokering af feedbackløkker
description: Blokering af feedbackløkker, også kaldet hurtig beskyttelse, er en del af funktionaliteten til blokering af funktionsmåder og inddæmmelse i Microsoft Defender til slutpunkt
keywords: blokering af funktionsmåder, hurtig beskyttelse, blokering af feedback, Microsoft Defender til slutpunkt
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
ms.openlocfilehash: 82d5fb32a9535a5b341bca8e5bee989d88ad8232
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2021
ms.locfileid: "63591925"
---
# <a name="feedback-loop-blocking"></a>Blokering af feedbackløkker

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

## <a name="overview"></a>Oversigt

Blokering af feedbackløkker, også kaldet hurtig beskyttelse, er en komponent af egenskaber [](/microsoft-365/security/defender-endpoint/behavioral-blocking-containment) til blokering af funktionsmåder og blokering i [Microsoft Defender til slutpunkt](/windows/security/threat-protection/). Med blokering af feedbackløkker er enheder i hele organisationen bedre beskyttet mod angreb. 

## <a name="how-feedback-loop-blocking-works"></a>Sådan fungerer blokering af feedbackløkker

Når en mistænkelig adfærd eller fil registreres, f.eks. [Microsoft Defender Antivirus](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-in-windows-10), sendes der oplysninger om den pågældende artefakt til flere klassificeringer. Programmet til hurtig beskyttelse undersøger og korrelerer oplysningerne med andre signaler for at nå frem til en beslutning om, hvorvidt en fil skal blokeres. Kontrol og klassificering af artefakter sker hurtigt. Det resulterer i hurtig blokering af bekræftet malware og driver beskyttelsen på tværs af hele økosystemet. 

Med hurtig beskyttelse på plads kan et angreb stoppes på en enhed, andre enheder i organisationen og enheder i andre organisationer, efterhånden som et angreb forsøger at udvide sidefoden.


## <a name="configuring-feedback-loop-blocking"></a>Konfiguration af blokering af feedbackløkker

Hvis din organisation bruger Defender til Slutpunkt, er blokering af feedback-loop aktiveret som standard. Men hurtig beskyttelse opstår gennem en kombination af Defender til slutpunkt-funktioner, maskinlæringsbeskyttelsesfunktioner og signaldeling på tværs af Microsofts sikkerhedstjenester. Sørg for, at følgende funktioner og egenskaber for Defender til slutpunkt er aktiveret og konfigureret:

- [Grundlinjer i Microsoft Defender til slutpunkter](/microsoft-365/security/defender-endpoint/configure-machines-security-baseline)

- [Enheder, der er onboardet til Microsoft Defender til Slutpunkt](/microsoft-365/security/defender-endpoint/onboard-configure)

- [Slutpunktsregistrering og -svar i bloktilstand](/microsoft-365/security/defender-endpoint/edr-in-block-mode)

- [Reduktion af angrebsoverfladen](/microsoft-365/security/defender-endpoint/attack-surface-reduction)

- [Næste generations beskyttelse](/windows/security/threat-protection/microsoft-defender-antivirus/configure-microsoft-defender-antivirus-features) (antivirus)

## <a name="related-articles"></a>Relaterede artikler

- [Blokering og inddæmmelse af funktionsmåder](behavioral-blocking-containment.md)

- [(Blog) Adfærdsblokering og -inddædning: Transformér optik til beskyttelse](https://www.microsoft.com/security/blog/2020/03/09/behavioral-blocking-and-containment-transforming-optics-into-protection/)

- [Nyttige Microsoft Defender til slutpunktsressourcer](/microsoft-365/security/defender-endpoint/helpful-resources)
