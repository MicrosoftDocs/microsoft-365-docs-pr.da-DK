---
title: Integrer dine SIEM-værktøjer med Microsoft Defender for Endpoint
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
ms.openlocfilehash: ed88048b506ecfcddb8394667e7d800927fc1d83
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/04/2022
ms.locfileid: "64634905"
---
# <a name="integrate-your-siem-tools-with-microsoft-defender-for-endpoint"></a>Integrer dine SIEM-værktøjer med Microsoft Defender for Endpoint

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


## <a name="ingest-alerts-using-security-information-and-events-management-siem-tools"></a>Beskeder omngest ved hjælp af sikkerhedsoplysninger og værktøjer til administration af begivenheder (SIEM)

> [!NOTE]
>
> [Microsoft Defender for Endpoint besked består](alerts.md) af en eller flere mistænkelige eller skadelige hændelser, der er opstået på enheden, og deres relaterede oplysninger. Besked-Microsoft Defender for Endpoint er den seneste API til forbrug af beskeder og indeholder en detaljeret liste over relaterede beviser for hver besked. Få mere at vide under [Beskedmetoder og -egenskaber](alerts.md) [og Vis beskeder](get-alerts.md).

Microsoft Defender for Endpoint understøtter værktøjer til sikkerhedsoplysninger og begivenhedsstyring (SIEM) til at modtage oplysninger fra din virksomhedslejer i Azure Active Directory (AAD) ved hjælp af OAuth 2.0-godkendelsesprotokol til en registreret AAD  program, der repræsenterer den specifikke SIEM-løsning eller forbindelse, der er installeret i dit miljø.

Du kan finde flere oplysninger under:

- [Microsoft Defender for Endpoint API-licens og vilkår for anvendelse](api-terms-of-use.md) 
- [Få adgang til Microsoft Defender for Endpoint API'er](apis-intro.md)
- [Hello World (beskriver, hvordan du registrerer et program i Azure Active Directory)](api-hello-world.md)
- [Få adgang med programkontekst](exposed-apis-create-app-webapp.md)


Microsoft Defender for Endpoint understøtter i øjeblikket følgende INTEGRATIONER AF SIEM-løsninger: 

- [Indtrængende hændelser og beskeder fra Microsoft 365 Defender og Microsoft Defender for Endpoint hændelser og vigtige REST-API'er](#ingesting-incidents-and-alerts-from-the-microsoft-365-defender-and-microsoft-defender-for-endpoint-incidents-and-alerts-rest-apis)
- [Inngesting Microsoft Defender for Endpoint events from the Microsoft 365 Defender event streaming API](#ingesting-microsoft-defender-for-endpoint-events-from-the-microsoft-365-defender-event-streaming-api)

## <a name="ingesting-incidents-and-alerts-from-the-microsoft-365-defender-and-microsoft-defender-for-endpoint-incidents-and-alerts-rest-apis"></a>Indtrængende hændelser og beskeder fra Microsoft 365 Defender og Microsoft Defender for Endpoint hændelser og vigtige REST-API'er

### <a name="ingesting-incidents-from-the-microsoft-365-defender-incidents-rest-api"></a>Ingesting incidents from the Microsoft 365 Defender incidents REST API

Du kan finde flere Microsoft 365 Defender om hændelses-API'en i [Metoder og egenskaber for hændelser](../defender/api-incident.md).

### <a name="ingesting-alerts-from-the-microsoft-defender-for-endpoint-alerts-rest-api"></a>Modtage beskeder fra Microsoft Defender for Endpoint REST-API

Du kan finde flere oplysninger Microsoft Defender for Endpoint API'en til vigtige beskeder under [metoder og egenskaber for beskeder](alerts.md).

## <a name="siem-tool-integration-with-microsoft-defender-for-endpoint"></a>Integration af SIEM-værktøjet med Microsoft Defender for Endpoint

### <a name="splunk"></a>Splunk

Brug af Microsoft 365 Defender til Splunk, der understøtter:

- Microsoft Defender for Endpoint beskeder om indtrængning
- Opdatering af beskeder i Microsoft Defender for Endpoint fra Splunk

Du kan finde flere oplysninger Microsoft 365 Defender tilføjelsesprogrammet til Splunk under [splunkbase](https://splunkbase.splunk.com/app/4959/).

### <a name="micro-focus-arcsight"></a>Micro Focus ArcSight

Den nye SmartConnector til Microsoft 365 Defender indtrænger hændelser, der indeholder beskeder fra alle Microsoft 365 Defender-produkter – herunder fra Microsoft Defender for Endpoint – til ArcSight og tilknytter dem til Common Event Framework (CEF).

Du kan finde flere oplysninger om den nye ArcSight SmartConnector til Microsoft 365 Defender i [dokumentationen til ArcSight-produkt](https://www.microfocus.com/documentation/arcsight/arcsight-smartconnectors/microsoft-365-defender/index.html).

SmartConnector erstatter den tidligere FlexConnector til Microsoft 365 Defender.

### <a name="ibm-qradar"></a>IBM Q Ibmar

>[!NOTE]
>IBM Q Ibmar-integration med Microsoft 365 Defender, som omfatter Microsoft Defender for Endpoint, understøttes nu af det nye Microsoft 365 Defender-enhedssupportmodul (DSM), der kalder [ Microsoft 365 Defender Streaming API,](../defender/streaming-api.md) der gør det muligt at modtage data om streaminghændelser fra Microsoft 365 Defender-produkter, herunder Microsoft Defender for Endpoint. Du kan finde flere oplysninger om den nye QRigar Microsoft 365 Defender DSM under [IBM QKatalog-produktdokumentation](https://www.ibm.com/docs/en/dsm?topic=microsoft-365-defender), og du kan finde flere oplysninger om hændelsestyper, der understøttes af Streaming API, under Understøttede [hændelsestyper](../defender/supported-event-types.md).

Nye kunder er ikke længere onboardet ved hjælp af det forrige QDriverar Microsoft Defender ATP Device Support Module (DSM), og eksisterende kunder opfordres til at indføre den nye Microsoft 365 Defender DSM som deres enkelte integrationspunkt i alle Microsoft 365 Defender-produkter.

## <a name="ingesting-microsoft-defender-for-endpoint-events-from-the-microsoft-365-defender-event-streaming-api"></a>Inngesting Microsoft Defender for Endpoint events from the Microsoft 365 Defender event streaming API

Microsoft 365 Defender data om streaminghændelser omfatter beskeder og andre begivenheder fra Microsoft Defender for Endpoint og andre Microsoft Defender-produkter. Disse hændelser kan streames til en Azure Storage-konto eller til Azure Event Hubs. Integrationsmodellen via begivenhedshubs understøttes i øjeblikket af Splunk og IBM QHubar.

Du kan finde flere oplysninger [Microsoft 365 Defender integration med SIEM](../defender/configure-siem-defender.md).
