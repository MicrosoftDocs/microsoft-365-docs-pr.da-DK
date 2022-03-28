---
title: Trin 2. Udfør en vurdering af parathed for SOC-integration ved hjælp af Zero Trust Framework
description: Grundlæggende om at udføre en vurdering af parathed for SOC-integration ved hjælp af Zero Trust Framework, når du integrerer Microsoft 365 Defender i dine sikkerhedshandlinger.
keywords: hændelser, beskeder, undersøge, korrelation, angreb, enheder, brugere, identiteter, identitet, postkasse, mail, 365, microsoft, m365, hændelsesrespons, cyberangreb, secops, sikkerhedshandlinger, soc
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-m365dsecops
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 1197edf14977c0232936531399d726f62ab70889
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63596848"
---
# <a name="step-2-perform-a-soc-integration-readiness-assessment-using-the-zero-trust-framework"></a>Trin 2. Udfør en vurdering af parathed for SOC-integration ved hjælp af Zero Trust Framework

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**
- Microsoft 365 Defender

Når de grundlæggende funktioner i SOC-teamet (Security Operations Center) er defineret, er næste trin for din organisation at forberede indføringen af Microsoft 365 Defender gennem en nultillids [tilgang](/security/zero-trust/). Anvendelse kan hjælpe dig med at fastlægge de nødvendige krav til implementering af Microsoft 365 Defender ved hjælp af moderne brancheførende fremgangsmåder, mens Microsoft 365 Defender vurdere egenskaberne for dit miljø.

Denne tilgang er baseret på et stærkt grundlag af beskyttelse og omfatter nøgleområder som identitet, slutpunkter (enheder), data, apps, infrastruktur og netværk. Readiness Assessment-teamet vil fastlægge de områder, hvor et basiskrav til aktivering af Microsoft 365 Defender endnu ikke er opfyldt og skal afhjælpes.

Følgende er nogle af de elementer, der skal afhjælpes, for at SOC kan optimere processerne i SOC fuldt ud:

- **Identitet:** Ældre lokale Active Directory-domæneservices (AD DS), ingen MFA-plan, ingen oversigt over privilegerede konti og andre.
- **Slutpunkter (enheder):** Stort antal ældre operativsystemer, begrænset lagerenhed og andre.
- **Data og apps:**  Manglende standarder for datastyring, ingen oversigt over brugerdefinerede apps, der ikke kan integreres.
- **Infrastruktur:** Stort antal ikke-tilladte SaaS-licenser, ingen containersikkerhed og andre.
- **Netværk:** Problemer med ydeevnen på grund af lav båndbredde, fladt netværk, trådløse sikkerhedsproblemer og andre.

Organisationer skal også følge den [Microsoft 365 Defender artikel](m365d-enable.md) for at registrere grundlinjesættet af konfigurationskrav. Disse trin vil bestemme afhjælpningsaktiviteter, soc-grupperne skal udføre for effektivt at udvikle use cases. 

Indføringsprocedurer og oprettelse af use case er beskrevet i trin 3 og 4.

## <a name="next-step"></a>Næste trin

[Trin 3. Planlæg Microsoft 365 Defender integration med dit SOC-katalog over tjenester](integrate-microsoft-365-defender-secops-services.md)
