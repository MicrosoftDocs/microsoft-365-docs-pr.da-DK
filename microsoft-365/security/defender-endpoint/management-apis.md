---
title: Oversigt over administration og API'er
ms.reviewer: ''
description: Få mere at vide om administrationsværktøjer og API-kategorier Microsoft Defender for Endpoint
keywords: onboarding, api, siem, rbac, access, portal, integration, undersøgelse, svar, enheder, enhed, brugerkontekst, programkontekst, streaming
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
ms.topic: conceptual
MS.technology: mde
ms.custom: api
ms.openlocfilehash: cc73531540222791eb39eeca74570f34ff78a1b7
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64469773"
---
# <a name="overview-of-management-and-apis"></a>Oversigt over administration og API'er

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-mgt-apis-abovefoldlink)


Defender til Slutpunkt understøtter en lang række indstillinger for at sikre, at kunderne nemt kan indføre platformen.

Anerkendelse af, at kundemiljøer og strukturer kan variere, blev Defender til Slutpunkt oprettet med fleksibilitet og detaljeret kontrol, så den passer til forskellige kundekrav.

## <a name="endpoint-onboarding-and-portal-access"></a>Onboarding af slutpunkter og portaladgang

Onboarding af enheder er fuldt integreret i Microsoft Endpoint Manager og Microsoft Intune til klientenheder og Microsoft Defender til serverenheder, hvilket giver en komplet komplet oplevelse af konfiguration, installation og overvågning. Derudover understøtter Microsoft Defender for Endpoint til Gruppepolitik og andre tredjepartsværktøjer, der bruges til administration af enheder.

Defender til Slutpunkt giver fuld kontrol over, hvad brugere med adgang til portalen kan se og gøre via fleksibiliteten i rollebaseret adgangskontrol (RBAC). RBAC-modellen understøtter alle varianter af sikkerhedsteamsstruktur:

- Globalt distribuerede organisationer og sikkerhedsteams
- Niveaued model security operations teams
- Fuldstændigt adskilte divisioner med enkelte centraliseret globale sikkerhedsteams

## <a name="available-apis"></a>Tilgængelige API'er

Løsningen Microsoft Defender for Endpoint bygget oven på en integrationsklar platform.

Defender til Slutpunkt fremviser mange af sine data og handlinger via et sæt programmatiske API'er. Disse API'er gør det muligt at automatisere arbejdsprocesser og udvikle baseret på Defender for Endpoint-funktioner.

:::image type="content" source="images/mdatp-apis.png" alt-text="Den tilgængelige API og integration i Microsoft Defender for Endpoint" lightbox="images/mdatp-apis.png":::

API'erne Defender til Slutpunkt kan grupperes i tre:

- Microsoft Defender for Endpoint API'er
- Rå datastreaming-API
- SIEM-integration

## <a name="microsoft-defender-for-endpoint-apis"></a>Microsoft Defender for Endpoint API'er

Defender til Slutpunkt tilbyder en lagdelt API-model, der eksponerer data og egenskaber i en struktureret, klar og brugervenlig model, der vises via en standard Azure AD-baseret godkendelses- og godkendelsesmodel, der giver adgang i kontekst for brugere eller SaaS-programmer. API-modellen er udviklet til at vise enheder og egenskaber i en ensartet form.

Watch this video for a quick overview of Defender for Endpoint's API'er.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4d73M]

**Undersøgelses-API'en** viser den omfattende værdi af Defender til slutpunkt – exposing beregnede eller "profilerede" enheder (f.eks. enhed, bruger og fil) og diskrete hændelser (f.eks. oprettelse af processer og filoprettelse), som typisk beskriver en funktionsmåde relateret til en enhed, hvilket giver adgang til data via undersøgelsesgrænseflader, der giver en forespørgselsbaseret adgang til data. Du kan finde flere oplysninger under [Understøttede API'er](exposed-apis-list.md).

**Svar-API'en** giver mulighed for at udføre handlinger i tjenesten og på enheder, gøre det muligt for kunder at modtage indikatorer, administrere indstillinger, beskedstatus samt udføre svarhandlinger på enheder ved hjælp af et program såsom isolere enheder fra netværket, sætte filer i karantæne og andre.

## <a name="raw-data-streaming-api"></a>Rå datastreaming-API

Defender for Endpoint raw data streaming API giver kunderne mulighed for at sende begivenheder og beskeder i realtid fra deres forekomster, når de opstår i en enkelt datastrøm, hvilket giver en mekanisme til lav latenstid og høj overførselshastighed.

Oplysninger om en Defender for Endpoint-begivenhed sendes direkte til Azure-lagerplads med henblik på langsigtet dataopbevaring eller til Azure Event Hubs til brug for visualiseringstjenester eller yderligere databehandlingsmotorer.

Du kan finde flere oplysninger i [Raw-datastreaming-API](raw-data-export.md).

Den nye Microsoft 365 Defender Streaming API omfatter mail- og beskedhændelser ud over enhedshændelser.
Du kan finde flere oplysninger [Microsoft 365 Defender Streaming API](../defender/streaming-api.md).

## <a name="siem-api"></a>SIEM API

Når du aktiverer integration af sikkerhedsoplysninger og begivenhedsstyring (SIEM), kan du trække registreringer fra Microsoft 365 Defender ved hjælp af din SIEM-løsning eller ved at oprette direkte forbindelse til registreringerne REST API. Dette aktiverer sektionen med oplysninger om adgang til SIEM-forbindelsen med forudindstillede værdier, og der oprettes et program under Azure Active Directory (Azure AD). 

## <a name="related-topics"></a>Relaterede emner

- [Få adgang til Microsoft Defender for Endpoint API'er](apis-intro.md)
- [Understøttede API'er](exposed-apis-list.md)
- [Tekniske partnermuligheder](partner-integration.md)
