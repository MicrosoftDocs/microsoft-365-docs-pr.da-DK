---
title: Integrer dine SIEM-værktøjer med Microsoft 365 Defender
description: Få mere at vide om, hvordan du bruger REST API og konfigurerer understøttede værktøjer til administration af sikkerhedsoplysninger og begivenheder til at modtage og trække registreringer.
keywords: configure siem, security information and events management tools, splunk, arcsight, custom indicators, rest api, alert definitions, indicators of compromise
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
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 210705bd3392e4aeeadd815ed8c1840e772f6ad9
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/19/2021
ms.locfileid: "63593015"
---
# <a name="integrate-your-siem-tools-with-microsoft-365-defender"></a>Integrer dine SIEM-værktøjer med Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender til Slutpunkt](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

## <a name="pull-microsoft-365-defender-incidents-and-streaming-event-data-using-security-information-and-events-management-siem-tools"></a>Trække Microsoft 365 Defender hændelser og data om streaming af begivenheder ved hjælp af værktøjer til sikkerhedsoplysninger og administration af begivenheder (SIEM)

> [!NOTE]
>
> - [Microsoft 365 Defender hændelser](incident-queue.md) består af samlinger af korrelerede beskeder og deres beviser.
> - [Microsoft 365 Defender streamer hændelsesdata for Streaming API](streaming-api.md) fra Microsoft 365 Defender til begivenhedshubs eller Azure-lagerkonti.

Microsoft 365 Defender understøtter sikkerhedsoplysninger og værktøjer til begivenhedsstyring (SIEM), der sender oplysninger fra din virksomhedslejer i Azure Active Directory (AAD) ved hjælp af OAuth 2.0-godkendelsesprotokol til et registreret AAD-program, der repræsenterer den specifikke SIEM-løsning eller forbindelse, der er installeret i din miljø. 

Du kan finde flere oplysninger under:

- [Microsoft 365 Defender API'ers licens og vilkår for anvendelse](api-terms.md)
- [Få adgang til Microsoft 365 Defender API'er](api-access.md)
- [Eksempel på Hej verden](api-hello-world.md)
- [Få adgang med programkontekst](api-create-app-web.md)

Der findes to primære modeller til ingest security information: 

1.  Inngesting Microsoft 365 Defender hændelser og deres indeholdte beskeder fra en REST API i Azure. 

2.  Inngesting streaming event data either through Azure Event Hubs or Azure Storage Accounts. 

Microsoft 365 Defender understøtter i øjeblikket følgende INTEGRATIONER AF SIEM-løsninger: 

- [Modtage hændelser fra hændelserne REST API](#ingesting-incidents-from-the-incidents-rest-api)
- [Inngesting streaming event data via Event Hub](#ingesting-streaming-event-data-via-event-hubs)

## <a name="ingesting-incidents-from-the-incidents-rest-api"></a>Modtage hændelser fra hændelserne REST API

### <a name="incident-schema"></a>Hændelsesskema
Du kan finde flere oplysninger Microsoft 365 Defender om hændelsesegenskaber, herunder indeholdt metadata for beskeder og beviser, under [Skematilknytning](../defender/api-list-incidents.md#schema-mapping).

### <a name="splunk"></a>Splunk

Brug af Microsoft 365 Defender til Splunk, der understøtter:

- Ngesting incidents that contain alerts from the following products, which are mapped onto Splunk's Common Information Model (CIM):

  - Microsoft 365 Defender
  - Microsoft Defender til Slutpunkt
  - Microsoft Defender for Identity og Azure Active Directory Identity Protection
  - Microsoft Defender til skyapps

- Opdatering af hændelser i Microsoft 365 Defender inde fra Splunk

- Ingesting Defender for Endpoint alerts (from the Defender for Endpoint's Azure endpoint) og opdatering af disse beskeder

Du kan finde flere oplysninger Microsoft 365 Defender tilføjelsesprogrammet til Splunk under [splunkbase](https://splunkbase.splunk.com/app/4959/).

### <a name="micro-focus-arcsight"></a>Micro Focus ArcSight

Den nye SmartConnector til Microsoft 365 Defender hændelser i ArcSight og tilknytter dem til Common Event Framework (CEF).

Du kan finde flere oplysninger om den nye ArcSight SmartConnector til Microsoft 365 Defender i Dokumentation [til ArcSight-produkt](https://community.microfocus.com/cyberres/productdocs/w/connector-documentation/39246/smartconnector-for-microsoft-365-defender).

SmartConnector erstatter den tidligere FlexConnector til Microsoft Defender for slutpunktet.
  

## <a name="ingesting-streaming-event-data-via-event-hubs"></a>Inngesting streaming event data via Event Hubs

Først skal du streame begivenheder fra din AAD-lejer til dine begivenhedshubs eller din Azure Storage-konto. Du kan få mere at vide under [Streaming API](../defender/streaming-api.md).

Du kan finde flere oplysninger om de hændelsestyper, der understøttes af Streaming API, under [Understøttede typer af streaminghændelser](../defender/supported-event-types.md).

### <a name="splunk"></a>Splunk
Brug tilføjelsesprogrammet Splunk til Microsofts skytjenester til at få adgang til begivenheder fra Azure Event Hubs.  


Du kan finde flere oplysninger om Splunk-tilføjelsesprogrammet til Microsofts skytjenester under [splunkbase](https://splunkbase.splunk.com/app/3110/).
  

### <a name="ibm-qradar"></a>IBM Q Ibmar
>Brug den nye IBM QDriver Microsoft 365 Defender Device Support Module (DSM), der kalder [Microsoft 365 Defender Streaming API](streaming-api.md), der giver mulighed for indgående streaming af begivenhedsdata fra Microsoft 365 Defender-produkter. Du kan finde flere oplysninger om understøttede hændelsestyper under [Understøttede hændelsestyper](supported-event-types.md).
