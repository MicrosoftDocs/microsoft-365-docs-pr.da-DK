---
title: Microsoft 365 Defender hændelser API'er og ressourcetypen hændelser
description: Få mere at vide om metoderne og egenskaberne for ressourcetypen Hændelser i Microsoft 365 Defender
keywords: hændelse, hændelser, api
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.custom: api
ms.openlocfilehash: a1a3f119e0aafe75b58df9c2330a950d5ab31ead
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/24/2022
ms.locfileid: "63593416"
---
# <a name="microsoft-365-defender-incidents-api-and-the-incidents-resource-type"></a>Microsoft 365 Defender hændelsers API og ressourcetypen hændelser

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!IMPORTANT]
> Nogle oplysninger relaterer til foreløbige produkter, som kan ændres væsentligt, før det frigives kommercielt. Microsoft påser ingen garantier, udtrykkelige eller underforståede, med hensyn til de oplysninger, du har angivet her.

En [hændelse](incidents-overview.md) er en samling relaterede beskeder, der beskriver et angreb. Begivenheder fra forskellige enheder i din organisation sammenlægges automatisk af Microsoft 365 Defender. Du kan bruge hændelses-API'en til automatisk at få adgang til din organisations hændelser og relaterede beskeder.

## <a name="quotas-and-resource-allocation"></a>Kvoter og ressourceallokering

Du kan anmode om op til 50 opkald i minuttet eller 1500 opkald pr. time. Hver metode har også sine egne kvoter. Du kan finde flere oplysninger om metodespecifikke kvoter i den pågældende artikel for den metode, du vil bruge.

En `429` HTTP-svarkode angiver, at du har nået en kvote, enten efter antal anmodninger, der er sendt, eller efter tildelt kørselstid. Svarteksten inkluderer tiden, indtil den kvote, du har nået, nulstilles.

## <a name="permissions"></a>Tilladelser

Hændelses-API'en kræver forskellige typer tilladelser for hver af dens metoder. Du kan finde flere oplysninger om nødvendige tilladelser i artiklen om de respektive metoder.

## <a name="methods"></a>Metoder

Metode | Returtype | Beskrivelse
-|-|-
[Liste over hændelser](api-list-incidents.md) | [Hændelsesliste](api-incident.md) | Få en liste over hændelser.
[Opdateringshændelse](api-update-incidents.md) | [Hændelse](api-incident.md) | Opdater en bestemt hændelse.
[Hent hændelse](api-get-incident.md) | [Hændelse](api-incident.md) | Få en enkelt hændelse.

## <a name="request-body-response-and-examples"></a>Anmodning om brødtekst, svar og eksempler

Se de respektive metodeartikler for at få mere at vide om, hvordan du opbygger en anmodning eller fortolker et svar, og for praktiske eksempler.

## <a name="common-properties"></a>Fælles egenskaber

Egenskab | Type | Beskrivelse
-|-|-
incidentId | lang | Hændelses-entydigt id.
redirectIncidentId | nullable long | Hændelses-id'et, som den aktuelle hændelse blev flettet til.
incidentName | streng | Navnet på hændelsen.
createdTime | DateTimeOffset | Dato og klokkeslæt (i UTC) hændelsen blev oprettet.
lastUpdateTime | DateTimeOffset | Dato og klokkeslæt (i UTC) hændelsen blev sidst opdateret.
assignedTo | streng | Ejeren af hændelsen.
alvorsgrad | Enum | Hændelsens alvorsgrad. De mulige værdier er: ```UnSpecified```, ```Informational```, ```Low```, ```Medium```og ```High```.
status | Enum | Angiver den aktuelle status for hændelsen. De mulige værdier er: ```Active```, ```InProgress```, ```Resolved```og ```Redirected```.
klassificering | Enum | Specifikation af hændelsen. De mulige værdier er: ```Unknown```, ```FalsePositive```, ```TruePositive```.
determination | Enum | Angiver bestemmelse af hændelsen. Mulige værdier er: ```NotAvailable```, , ```Apt``````Malware```, ```SecurityPersonnel```, ```SecurityTesting```, ```UnwantedSoftware```, ```Other```.
mærker | strengliste | Liste over hændelsesmærker.
kommentarer | Liste over hændelseskommentarer | Hændelseskommentarobjekt indeholder: kommentarstreng, createdBy-streng og createTime-datotid.
beskeder | Advarselsliste | Liste over relaterede beskeder. Se eksempler i [dokumentationen til List incidents](api-list-incidents.md) API.

## <a name="related-articles"></a>Relaterede artikler

- [Microsoft 365 Defender OVERSIGT over API'er](api-overview.md)
- [Oversigt over hændelser](incidents-overview.md)
- [Liste over hændelses-API'en](api-list-incidents.md)
- [Opdater hændelses-API](api-update-incidents.md)
