---
title: Microsoft Purview eDiscovery Graph-connectors
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: 07/15/2022
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.collection:
- m365-security-compliance
- m365solution-ediscovery
- m365initiative-compliance
- m365solution-overview
ms.localizationpriority: medium
search.appverid:
- SPO160
- MOE150
- MET150
description: Microsoft 365-kunder kan udføre eDiscovery-søgninger på indhold, der er indtaget til virksomhedssøgning.
ms.openlocfilehash: df6f948f60b74da6868f4f3877ee3a39e97c2a46
ms.sourcegitcommit: 180da7b39cfda7263a89bda0c3b93d9d6e55f3c2
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/19/2022
ms.locfileid: "66843785"
---
# <a name="use-graph-connectors-with-ediscovery-premium"></a>Brug Graph-connectors med eDiscovery (Premium)

Microsoft 365-kunder kan udføre eDiscovery-søgninger på indhold, der er indtaget til virksomhedssøgning. Dette hjælper organisationer med at forbedre deres overholdelse af angivne standarder i forhold til eksterne indholdskilder ved at bringe dem i overensstemmelse med Microsofts løsninger til overholdelse af angivne standarder.

Med Graph-connectors kan du gøre indhold fra eksterne datakilder tilgængeligt for Microsoft Purview eDiscovery Premium-løsning. Få mere at vide om oprettelse af Graph Connectors for din organisation her: [Oversigt over Microsoft Graph-connectors til Microsoft Search](/microsoftsearch/connectors-overview).

## <a name="add-graph-connector-as-a-data-source-within-a-case"></a>Tilføj Graph Connector som en datakilde i en sag

Når Graph Connectors er oprettet for en organisation, og eDiscovery er aktiveret, vil muligheden for at føje Graph Connector-datakilden til sagen være tilgængelig under ikke-Microsoft 365-placeringer. Det er kun de forbindelser, der er oprettet og aktiveret, der er tilgængelige for eDiscovery-styringen, så de kan medtages i en sag.

:::image type="content" source="../media/ediscovery-graph-new.png" alt-text="Du kan vælge Graph som en datakilde.":::

## <a name="collect-graph-connectors-content"></a>Indsaml indhold fra Graph Connectors

Ved tilføjelse af Graph Connectors-indhold som en datakilde er dette indhold derefter tilgængeligt til søgning og samling. I guiden til samling skal du vælge Graph Connector-indholdet som en datakilde, der ikke er frihedsberøvende. Brug betingelser som f.eks. datointerval, nøgleord og meget mere til at søge på tværs af det forbundne indhold for kun at indsamle det indhold, der er interessant. Når guiden er færdig, får du estimater for mængden af indhold, der indeholder resultater i forhold til dine søgekriterier, og overfører samlingen til korrektursættet.  

## <a name="review-content"></a>Gennemse indhold

Når eDiscovery-ledere har indsamlet til et anmeldelsessæt, kan de gennemse indhold fra Graph Connectors for at få mere at vide om indholdet og arbejde på at vurdere, om oplysningerne er kritiske og relevante for sagen.  

## <a name="export-content"></a>Eksportér indhold

Når det er valideret, at det indhold, der indsamles til gennemsyn, er det korrekte indhold, er dette indhold derefter tilgængeligt til eksport fra korrektursættet direkte. Vælg eksportindstillinger, og send eksportjobbet for det Connectors-indhold, der skal eksporteres fra korrektursættet.
