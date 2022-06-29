---
title: Integrer dine SIEM-værktøjer med Microsoft 365 Defender
description: Få mere at vide om, hvordan du bruger REST API og konfigurerer understøttede værktøjer til administration af sikkerhedsoplysninger og hændelser til at modtage og hente registreringer.
keywords: konfigurer siem, værktøjer til administration af sikkerhedsoplysninger og hændelser, splunk, arcsight, brugerdefinerede indikatorer, rest api, beskeddefinitioner, indikatorer for kompromis
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
ms.openlocfilehash: 3e2772fd458c60e48f78c0d4b816cdac8ca25940
ms.sourcegitcommit: c6f1486617b39565bfd8f662ee6ad65a9cefd3e3
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/29/2022
ms.locfileid: "66530301"
---
# <a name="integrate-your-siem-tools-with-microsoft-365-defender"></a>Integrer dine SIEM-værktøjer med Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

## <a name="pull-microsoft-365-defender-incidents-and-streaming-event-data-using-security-information-and-events-management-siem-tools"></a>Træk Microsoft 365 Defender hændelser og streaming af hændelsesdata ved hjælp af SIEM-værktøjer (security information and events management)

> [!NOTE]
>
> - [Microsoft 365 Defender Hændelser](incident-queue.md) består af samlinger af korrelerede beskeder og deres beviser.
> - [Microsoft 365 Defender Streaming-API](streaming-api.md) streamer hændelsesdata fra Microsoft 365 Defender til hændelseshubber eller Azure Storage-konti.

Microsoft 365 Defender understøtter SIEM-værktøjer (Security Information Information and Event Management) til hentning af oplysninger fra din virksomhedslejer i Azure Active Directory (AAD) ved hjælp af OAuth 2.0-godkendelsesprotokollen for et registreret AAD-program, der repræsenterer den specifikke SIEM-løsning eller connector, der er installeret i dit miljø. 

Du kan finde flere oplysninger under:

- [licens til Microsoft 365 Defender API'er og vilkår for anvendelse](api-terms.md)
- [Få adgang til de Microsoft 365 Defender API'er](api-access.md)
- [Hello World eksempel](api-hello-world.md)
- [Få adgang med programkontekst](api-create-app-web.md)

Der er to primære modeller til at overføre sikkerhedsoplysninger: 

1.  Indtagelse af Microsoft 365 Defender hændelser og deres indeholdte beskeder fra en REST API i Azure. 

2.  Indtagelse af streaminghændelsesdata enten via Azure Event Hubs eller Azure Storage-konti. 

Microsoft 365 Defender understøtter i øjeblikket følgende SIEM-løsningsintegrationer: 

- [Indtagelse af hændelser fra HÆNDELSERNE REST API](#ingesting-incidents-from-the-incidents-rest-api)
- [Indtagelse af streaminghændelsesdata via Event Hub](#ingesting-streaming-event-data-via-event-hubs)

## <a name="ingesting-incidents-from-the-incidents-rest-api"></a>Indtagelse af hændelser fra HÆNDELSERNE REST API

### <a name="incident-schema"></a>Hændelsesskema
Du kan få flere oplysninger om Microsoft 365 Defender hændelsesegenskaber, herunder indeholdte metadata for besked- og bevisenheder, under [Skematilknytning](../defender/api-list-incidents.md#schema-mapping).

### <a name="splunk"></a>Splunk

Brug af det nye fuldt understøttede Splunk-tilføjelsesprogram til Microsoft Security, der understøtter:

- Indtagelse af hændelser, der indeholder beskeder fra følgende produkter, som er knyttet til Splunks CIM (Common Information Model):

  - Microsoft 365 Defender
  - Microsoft Defender for Endpoint
  - Microsoft Defender for Identity og Azure Active Directory Identity Protection
  - Microsoft Defender for Cloud Apps

- Indtagelse af defender for endpoint-beskeder (fra Azure-slutpunktet for Defender for Endpoint) og opdatering af disse beskeder

- Understøttelse af opdatering af Microsoft 365 Defender hændelser og/eller Microsoft Defender for Endpoint beskeder, og de respektive dashboards er blevet flyttet til Microsoft 365 App for Splunk. 

Du kan få flere oplysninger om:

- Tilføjelsesprogrammet Splunk til Microsoft Security finder du i [Microsoft Security-tilføjelsesprogrammet på Splunkbase](https://splunkbase.splunk.com/app/6207/#/overview)

- Microsoft 365-appen til Splunk, se [Microsoft 365-appen på Splunkbase](https://splunkbase.splunk.com/app/3786/)

### <a name="micro-focus-arcsight"></a>Micro Focus ArcSight

Den nye SmartConnector til Microsoft 365 Defender indfødningshændelser i ArcSight og knytter disse til CEF (Common Event Framework).

Du kan få flere oplysninger om den nye ArcSight SmartConnector til Microsoft 365 Defender i [ArcSight-produktdokumentationen](https://community.microfocus.com/cyberres/productdocs/w/connector-documentation/39246/smartconnector-for-microsoft-365-defender).

SmartConnector erstatter den tidligere FlexConnector for Microsoft Defender for Endpoint, der er blevet udfaset.
  

## <a name="ingesting-streaming-event-data-via-event-hubs"></a>Indtagelse af streaminghændelsesdata via Event Hubs

Først skal du streame hændelser fra din AAD-lejer til din Event Hubs eller Azure Storage-konto. Du kan få flere oplysninger under [Streaming-API](../defender/streaming-api.md).

Du kan få flere oplysninger om de hændelsestyper, der understøttes af Streaming-API'en, under [Understøttede streaminghændelsestyper](../defender/supported-event-types.md).

### <a name="splunk"></a>Splunk

Brug Splunk-tilføjelsesprogrammet til Microsoft Cloud Services til at indtage hændelser fra Azure Event Hubs.  

Du kan få flere oplysninger om tilføjelsesprogrammet Splunk til Microsoft Cloud Services i [Tilføjelsesprogrammet Microsoft Cloud Services på Splunkbase](https://splunkbase.splunk.com/app/3110/).
  

### <a name="ibm-qradar"></a>IBM QRadar
>Brug den nye IBM QRadar Microsoft 365 Defender Device Support Module (DSM), der kalder [Microsoft 365 Defender Streaming API](streaming-api.md), der gør det muligt at indtage streaminghændelsesdata fra Microsoft 365 Defender produkter via Event Hubs eller Azure Storage-konto. Du kan få flere oplysninger om understøttede hændelsestyper under [Understøttede hændelsestyper](supported-event-types.md).
