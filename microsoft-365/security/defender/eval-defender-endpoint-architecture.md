---
title: Gennemse krav til Microsoft Defender for Endpoint arkitektur og vigtige begreber
description: Det tekniske diagram til Microsoft Defender for Endpoint i Microsoft 365 Defender hjælper dig med at forstå identiteten i Microsoft 365, før du bygger dit prøvelaboratorium eller pilotmiljø.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: v-jweston
author: jweston-1
ms.date: 07/09/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
- zerotrust-solution
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 5197acd8ceb3a2dea7c03b0ef076bca5dc9138dd
ms.sourcegitcommit: 61b22df76e0f81e5ef11c587b129287886151c79
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/12/2022
ms.locfileid: "66749127"
---
# <a name="review-microsoft-defender-for-endpoint-architecture-requirements-and-key-concepts"></a>Gennemse krav til Microsoft Defender for Endpoint arkitektur og vigtige begreber

**Gælder for:** Microsoft 365 Defender

I denne artikel får du en vejledning i, hvordan du konfigurerer evalueringen af Microsoft Defender for Endpoint miljø.

Du kan få flere oplysninger om denne proces i [oversigtsartiklen](eval-defender-endpoint-overview.md).

Før du aktiverer Microsoft Defender for Endpoint, skal du sørge for, at du forstår arkitekturen og kan opfylde kravene.

## <a name="understand-the-architecture"></a>Forstå arkitekturen

Følgende diagram illustrerer Microsoft Defender for Endpoint arkitektur og integrationer. 

:::image type="content" source="../../media/defender/m365-defender-endpoint-architecture.png" alt-text="Trinnene til tilføjelse af Microsoft Defender til Office i Defender-evalueringsmiljøet" lightbox="../../media/defender/m365-defender-endpoint-architecture.png":::

I følgende tabel beskrives illustrationen.

Opkald | Beskrivelse
:---|:---|
1 | Enheder er om bord via et af de understøttede administrationsværktøjer. 
2 | Enheder om bord leverer og reagerer på Microsoft Defender for Endpoint signaldata.
3 | Administrerede enheder er tilmeldt og/eller tilmeldt Azure Active Directory.
4 | Domænetilsluttede Windows-enheder synkroniseres til Azure Active Directory ved hjælp af Azure Active Directory Connect.
5 | Microsoft Defender for Endpoint beskeder, undersøgelser og svar administreres i Microsoft 365 Defender.

## <a name="understand-key-concepts"></a>Forstå vigtige begreber

I følgende tabel blev vigtige begreber identificeret, som er vigtige at forstå, når du evaluerer, konfigurerer og udruller Microsoft Defender for Endpoint: 

Koncept | Beskrivelse | Flere oplysninger
:---|:---|:---|
Administrationsportal | Microsoft 365 Defender portal til at overvåge og hjælpe med at besvare beskeder om potentielle vedvarende trusselsaktivitet eller databrud. | [oversigt over Microsoft Defender for Endpoint portal](/microsoft-365/security/defender-endpoint/portal-overview)
Reduktion af angrebsoverflade | Hjælp med at reducere dine angrebsoverflader ved at minimere de steder, hvor din organisation er sårbar over for cybertrusler og angreb. | [Oversigt over reduktion af angrebsoverflade](/microsoft-365/security/defender-endpoint/overview-attack-surface-reduction)
Registrering af slutpunkt og svar | Slutpunktsregistrerings- og svarfunktioner giver avancerede angrebsregistreringer, der er næsten i realtid og kan handles på. | [Oversigt over slutpunktsregistrerings- og svarfunktioner](/microsoft-365/security/defender-endpoint/overview-endpoint-detection-response)
Funktionsblokering og -opbevaring | Funktionalitet til adfærdsblokering og indkapsling kan hjælpe med at identificere og stoppe trusler baseret på deres adfærd og procestræer, selv når truslen er begyndt at blive udført. | [Blokering og opbevaring af funktionsmåder](/microsoft-365/security/defender-endpoint/behavioral-blocking-containment)
Automatiseret undersøgelse og svar | Ved automatiserede undersøgelser bruges forskellige inspektionsalgoritmer, der er baseret på processer, der bruges af sikkerhedsanalytikere, og som er designet til at undersøge beskeder og straks træffe foranstaltninger til at løse brud. | [Brug automatiserede undersøgelser til at undersøge og afhjælpe trusler](/microsoft-365/security/defender-endpoint/automated-investigations)
Avanceret jagt | Avanceret jagt er et forespørgselsbaseret værktøj til trusselsjagt, der giver dig mulighed for at udforske op til 30 dages rådata, så du proaktivt kan inspicere hændelser i dit netværk for at finde trusselsindikatorer og enheder. | [Oversigt over avanceret jagt](/microsoft-365/security/defender-endpoint/advanced-hunting-overview)
Threat Analytics | Threat Analytics er en række rapporter fra eksperteksperter fra Microsofts sikkerhedsforskere, der dækker de mest relevante trusler. | [Spor og reager på nye trusler](/microsoft-365/security/defender-endpoint/threat-analytics)


Du kan finde flere detaljerede oplysninger om de funktioner, der er inkluderet i Microsoft Defender for Endpoint, under [Hvad er Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint).

## <a name="siem-integration"></a>SIEM-integration

Du kan integrere Microsoft Defender for Endpoint med Microsoft Sentinel for mere omfattende at analysere sikkerhedshændelser på tværs af din organisation og bygge playbooks, så du kan reagere effektivt og øjeblikkeligt. 

Microsoft Defender for Endpoint kan også integreres i andre SIEM-løsninger (Security Information and Event Management). Du kan finde flere oplysninger under [Aktivér SIEM-integration i Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/enable-siem-integration).


## <a name="next-steps"></a>Næste trin
[Aktivér evalueringen](eval-defender-endpoint-enable-eval.md)

Vend tilbage til oversigten for [Evaluate Microsoft Defender for Endpoint](eval-defender-endpoint-overview.md)

Vend tilbage til oversigten for [Evaluate og pilot Microsoft 365 Defender](eval-overview.md)
