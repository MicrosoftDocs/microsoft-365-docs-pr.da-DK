---
title: Gennemse krav og nøglekoncepter for Microsoft Defender til slutpunktsarkitektur
description: Det tekniske diagram for Microsoft Defender til slutpunkt i Microsoft 365 Defender hjælper dig med at forstå identiteten i Microsoft 365 før du opbygger dit prøvelaboratorium eller pilotmiljø.
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
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: b1381e7c2be2224818c72fb8e269ad65ffcacfc8
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/23/2022
ms.locfileid: "63755019"
---
# <a name="review-microsoft-defender-for-endpoint-architecture-requirements-and-key-concepts"></a>Gennemse krav og nøglekoncepter for Microsoft Defender til slutpunktsarkitektur

**Gælder for:** Microsoft 365 Defender

Denne artikel guider dig i gang med at konfigurere evalueringen af Microsoft Defender til slutpunktsmiljøet.

Du kan finde flere oplysninger om denne proces i [oversigtsartikel](eval-defender-endpoint-overview.md).

Før du aktiverer Microsoft Defender til slutpunkt, skal du sørge for, at du forstår arkitekturen og kan opfylde kravene.

## <a name="understand-the-architecture"></a>Forstå arkitekturen

Følgende diagram illustrerer Microsoft Defender til slutpunktsarkitektur og -integration. 

:::image type="content" source="../../media/defender/m365-defender-endpoint-architecture.png" alt-text="Trinnene til at føje Microsoft Defender for Office til Defender-evalueringsmiljøet" lightbox="../../media/defender/m365-defender-endpoint-architecture.png":::

I følgende tabel beskrives illustrationen.

Call-out | Beskrivelse
:---|:---|
1 | Enhederne er om bord via et af de understøttede administrationsværktøjer. 
2 | On-boarded devices provide and respond to Microsoft Defender for Endpoint signal data.
3 | Administrerede enheder er forbundet og/eller tilmeldt Azure Active Directory.
4 | Domænebaserede Windows-enheder synkroniseres med Azure Active Directory ved hjælp Azure Active Directory Forbind.
5 | Microsoft Defender til slutpunktsadvarsler, undersøgelser og svar administreres i Microsoft 365 Defender.

## <a name="understand-key-concepts"></a>Forstå nøglekoncepter

Følgende tabel identificerede nøglekoncepter, som er vigtige at forstå, når de skal evaluere, konfigurere og udrulle Microsoft Defender til slutpunkt: 

Koncept | Beskrivelse | Flere oplysninger
:---|:---|:---|
Administrationsportal | Microsoft 365 Defender til at overvåge og hjælpe med at besvare beskeder om potentielt avanceret vedvarende trusselsaktivitet eller databris. | [Oversigt over Microsoft Defender til Endpoint-portalen](/microsoft-365/security/defender-endpoint/portal-overview)
Reduktion af angrebsoverfladen | Hjælp med at reducere dine angrebsoverflader ved at minimere de steder, hvor din organisation er sårbar over for cybertrusler og angreb. | [Oversigt over reduktion af angrebsoverfladen](/microsoft-365/security/defender-endpoint/overview-attack-surface-reduction)
Registrering af slutpunkt og svar | Registrering af slutpunkter og svarfunktioner giver avancerede registreringer af angreb, der er næsten i realtid og kan handles på. | [Oversigt over slutpunktsregistrering og -svar egenskaber](/microsoft-365/security/defender-endpoint/overview-endpoint-detection-response)
Blokering og inddæmmelse af funktionsmåder | Funktionsmådeblokering og -spærring kan hjælpe med at identificere og stoppe trusler baseret på deres funktionsmåde og procestræer, selv når truslerne er begyndt at blive udført. | [Blokering og inddæmmelse af funktionsmåder](/microsoft-365/security/defender-endpoint/behavioral-blocking-containment)
Automatiseret undersøgelse og svar | Automatiseret undersøgelse anvender forskellige inspektionsalgoritmer, der er baseret på processer, der bruges af sikkerhedsanalytikere, og som er designet til at undersøge vigtige beskeder og tage øjeblikkelige skridt til at løse overtrædelser. | [Brug automatiserede undersøgelser til at undersøge og afhjælpe trusler](/microsoft-365/security/defender-endpoint/automated-investigations)
Avanceret jagt | Avanceret jagt er et forespørgselsbaseret værktøj til trusselssøgning, som gør det muligt at udforske op til 30 dages rå data, så du proaktivt kan undersøge hændelser i dit netværk for at finde trusselsindikatorer og -enheder. | [Oversigt over avanceret jagt](/microsoft-365/security/defender-endpoint/advanced-hunting-overview)
Threat Analytics | Trusselsanalyse er en række rapporter fra erfarne Microsoft-sikkerhedseksperter, der dækker de mest relevante trusler. | [Hold styr på og svar på nye trusler](/microsoft-365/security/defender-endpoint/threat-analytics)


Hvis du vil have mere at vide om de funktioner, der følger med Microsoft Defender til slutpunkt, skal [du se Hvad er Microsoft Defender til slutpunkt](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint).

## <a name="siem-integration"></a>SIEM-integration

Du kan integrere Microsoft Defender til slutpunkt med Microsoft Sentinel for mere omfattende analyse af sikkerhedshændelser på tværs af organisationen og opbygge strategibøger, så du kan få et effektivt og øjeblikkeligt svar. 

Microsoft Defender til slutpunkt kan også integreres i andre sikkerhedsoplysninger og event management-løsninger (SIEM). Få mere at vide under [Aktivér SIEM-integration i Microsoft Defender til slutpunkt](/microsoft-365/security/defender-endpoint/enable-siem-integration).


## <a name="next-steps"></a>Næste trin
[Aktivér evalueringen](eval-defender-endpoint-enable-eval.md)

Gå tilbage til oversigten for [Evaluer Microsoft Defender til slutpunkt](eval-defender-endpoint-overview.md)

Gå tilbage til oversigten for [Evaluer og Microsoft 365 Defender](eval-overview.md)
