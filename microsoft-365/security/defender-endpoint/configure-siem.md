---
title: Integrer dine SIEM-værktøjer med Microsoft Defender for Endpoint
description: Få mere at vide om, hvordan du henter hændelser og beskeder og integrerer SIEM-værktøjer.
keywords: konfigurer siem, værktøjer til administration af sikkerhedsoplysninger og hændelser, splunk, arcsight, brugerdefinerede indikatorer, rest api, beskeddefinitioner, indikatorer for kompromis
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
ms.openlocfilehash: d679ac0d01a7e922e49b72b574a43e6f684179f9
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/06/2022
ms.locfileid: "64664496"
---
# <a name="integrate-your-siem-tools-with-microsoft-defender-for-endpoint"></a>Integrer dine SIEM-værktøjer med Microsoft Defender for Endpoint

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


## <a name="ingest-alerts-using-security-information-and-events-management-siem-tools"></a>Indfødning af beskeder ved hjælp af SIEM-værktøjer (Security Information And Events Management)

> [!NOTE]
>
> [Microsoft Defender for Endpoint Besked](alerts.md) består af en eller flere mistænkelige eller skadelige hændelser, der opstod på enheden, og deres relaterede oplysninger. API'en Microsoft Defender for Endpoint besked er den seneste API til beskedforbrug og indeholder en detaljeret liste over relaterede beviser for hver besked. Du kan få flere oplysninger under [Metoder og egenskaber for beskeder](alerts.md) og [Listebeskeder](get-alerts.md).

Microsoft Defender for Endpoint understøtter SIEM-værktøjer (security information and event management), der henter oplysninger fra din virksomhedslejer i Azure Active Directory (AAD) ved hjælp af OAuth 2.0-godkendelsesprotokollen for en registreret AAD  program, der repræsenterer den specifikke SIEM-løsning eller -connector, der er installeret i dit miljø.

Du kan finde flere oplysninger under:

- [licens til Microsoft Defender for Endpoint API'er og vilkår for anvendelse](api-terms-of-use.md) 
- [Få adgang til Microsoft Defender for Endpoint API'er](apis-intro.md)
- [Hello World eksempel (beskriver, hvordan du registrerer et program i Azure Active Directory)](api-hello-world.md)
- [Få adgang med programkontekst](exposed-apis-create-app-webapp.md)


Microsoft Defender for Endpoint understøtter i øjeblikket følgende SIEM-løsningsintegrationer: 

- [Indtagelse af hændelser og beskeder fra Microsoft 365 Defender og Microsoft Defender for Endpoint hændelser og beskeder REST API'er](#ingesting-incidents-and-alerts-from-the-microsoft-365-defender-and-microsoft-defender-for-endpoint-incidents-and-alerts-rest-apis)
- [Indtagelse af Microsoft Defender for Endpoint hændelser fra streaming-API'en for Microsoft 365 Defender-hændelse](#ingesting-microsoft-defender-for-endpoint-events-from-the-microsoft-365-defender-event-streaming-api)

## <a name="ingesting-incidents-and-alerts-from-the-microsoft-365-defender-and-microsoft-defender-for-endpoint-incidents-and-alerts-rest-apis"></a>Indtagelse af hændelser og beskeder fra Microsoft 365 Defender og Microsoft Defender for Endpoint hændelser og beskeder REST API'er

### <a name="ingesting-incidents-from-the-microsoft-365-defender-incidents-rest-api"></a>Indtagelse af hændelser fra REST API'en for Microsoft 365 Defender hændelser

Du kan få flere oplysninger om API'en for Microsoft 365 Defender hændelser under [metoder og egenskaber for hændelser](../defender/api-incident.md).

### <a name="ingesting-alerts-from-the-microsoft-defender-for-endpoint-alerts-rest-api"></a>Indtagelse af beskeder fra REST API'en for Microsoft Defender for Endpoint-beskeder

Du kan få flere oplysninger om API'en for Microsoft Defender for Endpoint beskeder under [metoder og egenskaber for beskeder](alerts.md).

## <a name="siem-tool-integration-with-microsoft-defender-for-endpoint"></a>Integration af SIEM-værktøj med Microsoft Defender for Endpoint

### <a name="splunk"></a>Splunk

Brug af tilføjelsesprogrammet Microsoft 365 Defender for Splunk, der understøtter:

- Indtagelse af Microsoft Defender for Endpoint beskeder
- Opdatering af beskeder i Microsoft Defender for Endpoint inde fra Splunk

Du kan få flere oplysninger om tilføjelsesprogrammet Microsoft 365 Defender for Splunk i [splunkbase](https://splunkbase.splunk.com/app/4959/).

### <a name="micro-focus-arcsight"></a>Micro Focus ArcSight

Den nye SmartConnector til Microsoft 365 Defender indfødningshændelser, der indeholder beskeder fra alle Microsoft 365 Defender produkter - herunder fra Microsoft Defender for Endpoint - til ArcSight og knytter disse til CEF (Common Event Framework).

Du kan få flere oplysninger om den nye ArcSight SmartConnector til Microsoft 365 Defender i dokumentationen til [ArcSight-produkt](https://www.microfocus.com/documentation/arcsight/arcsight-smartconnectors/microsoft-365-defender/index.html).

SmartConnector erstatter den tidligere FlexConnector for Microsoft 365 Defender.

### <a name="ibm-qradar"></a>IBM QRadar

>[!NOTE]
>IBM QRadar-integration med Microsoft 365 Defender, som omfatter Microsoft Defender for Endpoint, understøttes nu af det nye DSM (Microsoft 365 Defender Device Support Module), der kalder [ Microsoft 365 Defender Streaming-API](../defender/streaming-api.md), der gør det muligt at indtage streaminghændelsesdata fra Microsoft 365 Defender produkter, herunder Microsoft Defender for Endpoint. Du kan få flere oplysninger om den nye QRadar-Microsoft 365 Defender DSM i [IBM QRadar-produktdokumentationen](https://www.ibm.com/docs/en/dsm?topic=microsoft-365-defender), og du kan få flere oplysninger om streaming-API-understøttede [hændelsestyper under Understøttede hændelsestyper](../defender/supported-event-types.md).

Nye kunder onboardes ikke længere ved hjælp af det tidligere QRadar Microsoft Defender ATP Device Support Module (DSM), og eksisterende kunder opfordres til at anvende den nye Microsoft 365 Defender DSM som deres eneste integrationspunkt med alle Microsoft 365 Defender produkter.

## <a name="ingesting-microsoft-defender-for-endpoint-events-from-the-microsoft-365-defender-event-streaming-api"></a>Indtagelse af Microsoft Defender for Endpoint hændelser fra streaming-API'en for Microsoft 365 Defender-hændelse

Microsoft 365 Defender streaming af hændelsesdata omfatter beskeder og andre hændelser fra Microsoft Defender for Endpoint og andre Microsoft Defender-produkter. Disse hændelser kan streames til en Azure Storage konto eller til Azure Event Hubs. Integrationsmodellen via hændelseshubber understøttes i øjeblikket af Splunk og IBM QRadar.

Du kan finde flere oplysninger under [Microsoft 365 Defender SIEM-integration](../defender/configure-siem-defender.md).
