---
title: Undersøg hændelser i Microsoft Defender for Endpoint
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
ms.openlocfilehash: d66dde2c3f346449c7ecd03a7ef577e39cf98991
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64468793"
---
# <a name="investigate-incidents-in-microsoft-defender-for-endpoint"></a>Undersøg hændelser i Microsoft Defender for Endpoint

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


Undersøg hændelser, der påvirker dit netværk, forstå, hvad de betyder, og sammenlæg beviser for at løse dem.

Når du undersøger en hændelse, får du vist følgende:

- Oplysninger om hændelse
- Hændelseskommentarer og -handlinger
- Faner (beskeder, enheder, undersøgelser, beviser, graf)

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4qLUV]

## <a name="analyze-incident-details"></a>Analysér oplysninger om hændelse

Klik på en hændelse for at få vist **ruden Hændelse**. Vælg **Åbn hændelsesside** for at få vist oplysninger om hændelsen og relaterede oplysninger (beskeder, enheder, undersøgelser, beviser, graf).

:::image type="content" source="images/atp-incident-details.png" alt-text="Oplysninger om en hændelse" lightbox="images/atp-incident-details.png":::

### <a name="alerts"></a>Beskeder

Du kan undersøge beskederne og se, hvordan de blev kædet sammen i en hændelse. Beskeder grupperes i hændelser ud fra følgende årsager:

- Automatiseret undersøgelse – Den automatiserede undersøgelse udløste den tilknyttede besked, mens den oprindelige besked blev undersøges
- Filegenskaber – De filer, der er knyttet til beskeden, har de samme egenskaber
- Manuel tilknytning – En bruger sammenkædede beskederne manuelt
- Proxytid – Beskederne blev udløst på den samme enhed inden for en bestemt tidsramme
- Samme fil – De filer, der er knyttet til beskeden, er nøjagtig de samme
- Samme URL-adresse – Den URL-adresse, der udløste beskeden, er præcis den samme

:::image type="content" source="images/atp-incidents-alerts-reason.png" alt-text="Fanen Vigtige beskeder med siden med oplysninger om hændelser, der viser årsagen til, at beskederne blev sammenkædet i den pågældende hændelse" lightbox="images/atp-incidents-alerts-reason.png":::

Du kan også administrere en besked og få vist metadata for beskeder sammen med andre oplysninger. Få mere at vide under [Undersøg beskeder](investigate-alerts.md).

### <a name="devices"></a>Enheder

Du kan også undersøge de enheder, der er en del af eller relateret til en bestemt hændelse. Få mere at vide under [Undersøg enheder](investigate-machines.md).

:::image type="content" source="images/atp-incident-device-tab.png" alt-text="Fanen Enheder på siden med oplysninger om hændelser" lightbox="images/atp-incident-device-tab.png":::

### <a name="investigations"></a>Undersøgelser

Vælg **Undersøgelser for** at se alle de automatiske undersøgelser, der startes af systemet som reaktion på beskeder om hændelser.

:::image type="content" source="images/atp-incident-investigations-tab.png" alt-text="Fanen Undersøgelser på siden med oplysninger om hændelser" lightbox="images/atp-incident-investigations-tab.png":::

## <a name="going-through-the-evidence"></a>Gennemgå beviserne

Microsoft Defender for Endpoint automatisk alle hændelsers understøttede hændelser og mistænkelige enheder i beskederne, så du får besked om autorespons og oplysninger om vigtige filer, processer, tjenester og meget mere.

Hver af de analyserede enheder markeres som inficeret, afhjælpet eller mistænkelig.

:::image type="content" source="images/atp-incident-evidence-tab.png" alt-text="Fanen Beviser på siden med oplysninger om hændelsen" lightbox="images/atp-incident-evidence-tab.png":::

## <a name="visualizing-associated-cybersecurity-threats"></a>Visualisere tilknyttede trusler mod cybersikkerhed

Microsoft Defender for Endpoint samler trusselsoplysningerne til en hændelse, så du kan se mønstre og korrelationer, der kommer fra forskellige datapunkter. Du kan få vist en sådan korrelation via grafen over hændelser.

### <a name="incident-graph"></a>Graf over hændelser

The **Graph** fortæller historien om cybersecurity-angrebene. For eksempel viser den dig, hvad der var indgangspunktet, hvilken indikator for forlig eller aktivitet, der blev observeret på hvilken enhed. osv.

:::image type="content" source="images/atp-incident-graph-tab.png" alt-text="Graf over hændelser" lightbox="images/atp-incident-graph-tab.png":::

Du kan klikke på cirklerne i hændelsesdiagrammet for at få vist detaljerne for de skadelige filer, tilknyttede filregistreringer, hvor mange forekomster der har været i hele verden, uanset om det er blevet observeret i din organisation, hvis det er sådan, hvor mange forekomster.

:::image type="content" source="images/atp-incident-graph-details.png" alt-text="Siden med oplysninger om hændelsen" lightbox="images/atp-incident-graph-details.png":::

## <a name="related-topics"></a>Relaterede emner

- [Kø over hændelser](/microsoft-365/security/defender-endpoint/view-incidents-queue)
- [Undersøg hændelser i Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/investigate-incidents)
- [Administrer Microsoft Defender for Endpoint hændelser](/microsoft-365/security/defender-endpoint/manage-incidents)
