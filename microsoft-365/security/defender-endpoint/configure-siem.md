---
title: Integrer dine SIEM-værktøjer med Microsoft Defender til Slutpunkt
description: Få mere at vide om, hvordan du ingester hændelser og beskeder, og integrer SIEM-værktøjer.
keywords: configure siem, security information and events management tools, splunk, arcsight, custom indicators, rest api, alert definitions, indicators of compromise
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
ms.openlocfilehash: 4c0462bcfae77677fca05132aaf0895b897bf788
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/24/2022
ms.locfileid: "63593473"
---
# <a name="integrate-your-siem-tools-with-microsoft-defender-for-endpoint"></a>Integrer dine SIEM-værktøjer med Microsoft Defender til Slutpunkt

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


## <a name="ingest-alerts-using-security-information-and-events-management-siem-tools"></a>Beskeder omngest ved hjælp af sikkerhedsoplysninger og værktøjer til administration af begivenheder (SIEM)

> [!NOTE]
>
> [Microsoft Defender for Endpoint Alert er](alerts.md) sammensat fra en eller flere mistænkelige eller skadelige hændelser, der er opstået på enheden, og deres relaterede oplysninger. Microsoft Defender for Endpoint Alert API er den nyeste API til beskedforbrug og indeholder en detaljeret liste over relaterede beviser for hver besked. Få mere at vide under [Beskedmetoder og -egenskaber](alerts.md) [og Vis beskeder](get-alerts.md).

Microsoft Defender til Slutpunkt understøtter værktøjer til sikkerhedsoplysninger og begivenhedsstyring (SIEM), der sender oplysninger fra din virksomhedslejer i Azure Active Directory (AAD) ved hjælp af OAuth 2.0-godkendelsesprotokol til et registreret AAD-program, der repræsenterer den specifikke SIEM-løsning eller forbindelse, der er installeret i dit miljø.

Du kan finde flere oplysninger under:

- [Microsoft Defender for Endpoint API'ers licens og vilkår for anvendelse](api-terms-of-use.md) 
- [Få adgang til Microsoft Defender for Endpoint API'er](apis-intro.md)
- [Eksempel på Hej verden (beskriver, hvordan du registrerer et program Azure Active Directory)](api-hello-world.md)
- [Få adgang med programkontekst](exposed-apis-create-app-webapp.md)


Microsoft Defender til Slutpunkt understøtter i øjeblikket følgende integrationer af SIEM-løsninger: 

- [Indtrængende hændelser og beskeder fra Microsoft 365 Defender og Microsoft Defender for Endpoint-hændelser og -vigtige REST-API'er](#ingesting-incidents-and-alerts-from-the-microsoft-365-defender-and-microsoft-defender-for-endpoint-incidents-and-alerts-rest-apis)
- [Inngesting Microsoft Defender for Endpoint events from the Microsoft 365 Defender event streaming API](#ingesting-microsoft-defender-for-endpoint-events-from-the-microsoft-365-defender-event-streaming-api)

## <a name="ingesting-incidents-and-alerts-from-the-microsoft-365-defender-and-microsoft-defender-for-endpoint-incidents-and-alerts-rest-apis"></a>Indtrængende hændelser og beskeder fra Microsoft 365 Defender og Microsoft Defender for Endpoint-hændelser og -vigtige REST-API'er

### <a name="ingesting-incidents-from-the-microsoft-365-defender-incidents-rest-api"></a>Ingesting incidents from the Microsoft 365 Defender incidents REST API

Du kan finde flere Microsoft 365 Defender om hændelses-API'en i [Metoder og egenskaber for hændelser](../defender/api-incident.md).

### <a name="ingesting-alerts-from-the-microsoft-defender-for-endpoint-alerts-rest-api"></a>Modtage beskeder fra Microsoft Defender for Endpoint-påmindelser REST API

Du kan finde flere oplysninger om MICROSOFT Defender for Endpoint alerts API i [metoder og egenskaber for beskeder](alerts.md).

## <a name="siem-tool-integration-with-microsoft-defender-for-endpoint"></a>Integration af SIEM-værktøjet med Microsoft Defender til Slutpunkt

### <a name="splunk"></a>Splunk

Brug af Microsoft 365 Defender til Splunk, der understøtter:

- Ingesting Microsoft Defender for Endpoint alerts
- Opdatering af beskeder i Microsoft Defender til slutpunkt fra Splunk

Du kan finde flere oplysninger Microsoft 365 Defender tilføjelsesprogrammet til Splunk under [splunkbase](https://splunkbase.splunk.com/app/4959/).

### <a name="micro-focus-arcsight"></a>Micro Focus ArcSight

Den nye SmartConnector til Microsoft 365 Defender-hændelser, der indeholder beskeder fra alle Microsoft 365 Defender-produkter – herunder fra Microsoft Defender til slutpunkt – ind i ArcSight og tilknytter dem til Common Event Framework (CEF).

Du kan finde flere oplysninger om den nye ArcSight SmartConnector til Microsoft 365 Defender i [dokumentationen til ArcSight-produkt](https://community.microfocus.com/cyberres/productdocs/w/connector-documentation/39246/smartconnector-for-microsoft-365-defender).

SmartConnector erstatter den tidligere FlexConnector til Microsoft 365 Defender.

### <a name="ibm-qradar"></a>IBM Q Ibmar

>[!NOTE]
>IBM QArear-integration med Microsoft 365 Defender, som omfatter Microsoft Defender til slutpunkt, understøttes nu af det nye Microsoft 365 Defender Device Support Module (DSM), der kalder [Microsoft 365 Defender Streaming API](../defender/streaming-api.md), der giver mulighed for indgående data om streaminghændelser fra Microsoft 365 Defender produkter, herunder Microsoft Defender til slutpunkt. Du kan finde flere oplysninger om den nye QRigar Microsoft 365 Defender DSM under [IBM QKatalog-produktdokumentation](https://www.ibm.com/docs/en/dsm?topic=microsoft-365-defender), og du kan finde flere oplysninger om hændelsestyper, der understøttes af Streaming API, under Understøttede [hændelsestyper](../defender/supported-event-types.md).

Nye kunder er ikke længere onboardet ved hjælp af det forrige QDriverar Microsoft Defender ATP Device Support Module (DSM), og eksisterende kunder opfordres til at indføre den nye Microsoft 365 Defender DSM som deres enkelte integrationspunkt i alle Microsoft 365 Defender-produkter.

## <a name="ingesting-microsoft-defender-for-endpoint-events-from-the-microsoft-365-defender-event-streaming-api"></a>Inngesting Microsoft Defender for Endpoint events from the Microsoft 365 Defender event streaming API

Microsoft 365 Defender data om streaminghændelser omfatter beskeder og andre begivenheder fra Microsoft Defender til Slutpunkt og andre Microsoft Defender-produkter. Disse hændelser kan streames til en Azure Storage-konto eller til Azure Event Hubs. Integrationsmodellen via begivenhedshubs understøttes i øjeblikket af Splunk og IBM QHubar.

Du kan finde flere oplysninger [Microsoft 365 Defender integration med SIEM](../defender/configure-siem-defender.md).
