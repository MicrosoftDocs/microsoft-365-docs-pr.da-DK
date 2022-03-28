---
title: Undersøg hændelser i Microsoft Defender til slutpunkt
description: Se tilknyttede beskeder, administrer hændelsen, og se metadata for at hjælpe dig med at undersøge en hændelse
keywords: undersøge, hændelse, beskeder, metadata, risiko, registreringskilde, påvirkede enheder, mønstre, korrelation
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 2a297813fbde94499f2d239627be6c33c153e8b0
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/12/2022
ms.locfileid: "63597565"
---
# <a name="investigate-incidents-in-microsoft-defender-for-endpoint"></a>Undersøg hændelser i Microsoft Defender til slutpunkt

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


Undersøg hændelser, der påvirker dit netværk, forstå, hvad de betyder, og sammenlæg beviser for at løse dem.

Når du undersøger en hændelse, får du vist følgende:

- Oplysninger om hændelse
- Hændelseskommentarer og -handlinger
- Faner (beskeder, enheder, undersøgelser, beviser, graf)

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4qLUV]

## <a name="analyze-incident-details"></a>Analysér oplysninger om hændelse

Klik på en hændelse for at få vist **ruden Hændelse**. Vælg **Åbn hændelsesside** for at få vist oplysninger om hændelsen og relaterede oplysninger (beskeder, enheder, undersøgelser, beviser, graf).

![Billede af oplysninger om hændelsen1.](images/atp-incident-details.png)

### <a name="alerts"></a>Beskeder

Du kan undersøge beskederne og se, hvordan de blev kædet sammen i en hændelse. Beskeder grupperes i hændelser ud fra følgende årsager:

- Automatiseret undersøgelse – Den automatiserede undersøgelse udløste den tilknyttede besked, mens den oprindelige besked blev undersøges
- Filegenskaber – De filer, der er knyttet til beskeden, har de samme egenskaber
- Manuel tilknytning – En bruger sammenkædede beskederne manuelt
- Proxytid – Beskederne blev udløst på den samme enhed inden for en bestemt tidsramme
- Samme fil – De filer, der er knyttet til beskeden, er nøjagtig de samme
- Samme URL-adresse – Den URL-adresse, der udløste beskeden, er præcis den samme

![Billede af fanen beskeder med siden med oplysninger om hændelser, der viser årsagen til, at beskederne blev sammenkædet i den pågældende hændelse.](images/atp-incidents-alerts-reason.png)

Du kan også administrere en besked og få vist metadata for beskeder sammen med andre oplysninger. Få mere at vide under [Undersøg beskeder](investigate-alerts.md).

### <a name="devices"></a>Enheder

Du kan også undersøge de enheder, der er en del af eller relateret til en bestemt hændelse. Få mere at vide under [Undersøg enheder](investigate-machines.md).

![Billede af fanen enheder på siden med oplysninger om hændelser.](images/atp-incident-device-tab.png)

### <a name="investigations"></a>Undersøgelser

Vælg **Undersøgelser for** at se alle de automatiske undersøgelser, der startes af systemet som reaktion på beskeder om hændelser.

![Billede af fanen undersøgelser på siden med oplysninger om hændelser.](images/atp-incident-investigations-tab.png)

## <a name="going-through-the-evidence"></a>Gennemgå beviserne

Microsoft Defender til Slutpunkt undersøger automatisk alle hændelsers understøttede hændelser og mistænkelige enheder i beskederne, så du får besked om autorespons og oplysninger om vigtige filer, processer, tjenester og meget mere.

Hver af de analyserede enheder markeres som inficeret, afhjælpet eller mistænkelig.

![Billede af fanen bevis på siden med oplysninger om hændelser.](images/atp-incident-evidence-tab.png)

## <a name="visualizing-associated-cybersecurity-threats"></a>Visualisere tilknyttede trusler mod cybersikkerhed

Microsoft Defender til Slutpunkt samler trusselsoplysningerne i en hændelse, så du kan se mønstre og korrelationer, der kommer fra forskellige datapunkter. Du kan få vist en sådan korrelation via grafen over hændelser.

### <a name="incident-graph"></a>Graf over hændelser

The **Graph** fortæller historien om cybersecurity-angrebene. For eksempel viser den dig, hvad der var indgangspunktet, hvilken indikator for forlig eller aktivitet, der blev observeret på hvilken enhed. osv.

![Billede af grafen over hændelser.](images/atp-incident-graph-tab.png)

Du kan klikke på cirklerne i hændelsesdiagrammet for at få vist detaljerne for de skadelige filer, tilknyttede filregistreringer, hvor mange forekomster der har været i hele verden, uanset om det er blevet observeret i din organisation, hvis det er sådan, hvor mange forekomster.

![Billede af oplysninger om hændelsen.](images/atp-incident-graph-details.png)

## <a name="related-topics"></a>Relaterede emner

- [Kø over hændelser](/microsoft-365/security/defender-endpoint/view-incidents-queue)
- [Undersøg hændelser i Microsoft Defender til slutpunkt](/microsoft-365/security/defender-endpoint/investigate-incidents)
- [Administrer Microsoft Defender for Endpoint-hændelser](/microsoft-365/security/defender-endpoint/manage-incidents)
