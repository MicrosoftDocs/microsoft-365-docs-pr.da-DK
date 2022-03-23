---
title: Beskyt din organisation mod webtrusler
description: Få mere at vide om webbeskyttelse i Microsoft Defender til Slutpunkt, og hvordan du kan beskytte din organisation.
keywords: webbeskyttelse, beskyttelse mod webtrusler, webbrowsing, sikkerhed, phishing, malware, udnyttelse, websteder, netværksbeskyttelse, Edge, Internet Explorer, Chrome, Firefox, webbrowser
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 398fdb8bbfb5bba59fce83e24e7d6cdd496e90bd
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2021
ms.locfileid: "63591812"
---
# <a name="protect-your-organization-against-web-threats"></a>Beskyt din organisation mod webtrusler

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-main-abovefoldlink&rtc=1)

Webtrusselsbeskyttelse er en [del af webbeskyttelse](web-protection-overview.md) i Defender til slutpunkt. Den bruger [netværksbeskyttelse til](network-protection.md) at beskytte dine enheder mod webtrusler. Ved at integrere med Microsoft Edge og populære tredjepartsbrowsere som Chrome og Firefox stopper webtrusler uden en webproxy og kan beskytte enheder, mens de er væk eller i det lokale miljø. Webtrusselsbeskyttelse stopper adgangen til phishingwebsteder, malwarevektorer, udnyttelseswebsteder, upålidelige websteder eller websteder med dårligt ry samt websteder, du har blokeret i din [brugerdefinerede liste over indikatorer](manage-indicators.md).

> [!NOTE]
> Det kan tage op til en time, før enheder modtager nye brugerdefinerede indikatorer.

## <a name="prerequisites"></a>Forudsætninger

Webbeskyttelse bruger netværksbeskyttelse til at sikre webbrowsing Microsoft Edge webbrowsere og tredjepartswebbrowsere.

Sådan aktiverer du netværksbeskyttelse på dine enheder:

- Rediger sikkerheds grundlinjen Defender for Endpoint under **Web & Network Protection** for at aktivere netværksbeskyttelse, før du udruller eller geninstallerer den. [Få mere at vide om at gennemse og tildele sikkerhedslinjen Defender for Endpoint](configure-machines-security-baseline.md#review-and-assign-the-microsoft-defender-for-endpoint-security-baseline)
- Slå netværksbeskyttelse til ved hjælp af intune-enhedskonfiguration, SCCM, Gruppepolitik eller din MDM-løsning. [Læs mere om aktivering af netværksbeskyttelse](enable-network-protection.md)

> [!NOTE]
> Hvis du angiver netværksbeskyttelse til **Kun overvågning**, er blokering ikke tilgængelig. Du vil også kunne registrere og logge forsøg på at få adgang til skadelige og uønskede websteder udelukkende Microsoft Edge websteder.

## <a name="configure-web-threat-protection"></a>Konfigurere beskyttelse mod webtrusler

Følgende procedure beskriver, hvordan du konfigurerer beskyttelse mod webtrusler ved hjælp Microsoft Endpoint Manager Administration.

1. Gå til Microsoft Endpoint Manager Administration ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)), og log på.
 
2. Vælg **Endpoint security** \> **Attack surface reduction**, og vælg **derefter + Opret politik**.

3. Vælg en platform, **f.eks. Windows 10 senere**, vælg **Webbeskyttelsesprofil**, og vælg derefter **Opret**. 

4. Angiv et **navn og** en beskrivelse under fanen Grundlæggende, og vælg derefter **Næste**.

5. På fanen **Konfigurationsindstillinger** skal du **udvide Webbeskyttelse**, angive dine indstillinger og derefter vælge **Næste**.

   - Angiv **Aktivér netværksbeskyttelse til** **Aktiveret** , så webbeskyttelse er slået til. Alternativt kan du angive netværksbeskyttelse til **overvågningstilstand for** at se, hvordan det fungerer i dit miljø. I overvågningstilstand forhindrer netværksbeskyttelse ikke brugere i at besøge websteder eller domæner, men den sporer registreringer som hændelser. 
   - Hvis du vil beskytte brugere mod phishingsvindel og skadelig software, skal **du slå Kræv SmartScreen Den ældre version af Microsoft Edge** til **Ja**.
   - Hvis du vil forhindre brugere i at ignorere advarsler om potentielt skadelige websteder, skal du angive **Bloker ondsindet adgang til webstedet** til **Ja**.
   - Hvis du vil forhindre brugere i at ignorere advarslerne og hente ikke-bekræftede filer, skal du angive **Bloker ikke-bekræftet filoverførsel** tl **Ja**. 

6. På fanen **Omfangsmærker** skal du, hvis din organisation bruger omfangsmærker, **vælge + Vælg områdemærker** og derefter vælge **Næste**. Hvis du ikke bruger områdemærker, skal du **vælge Næste**. Du kan få mere at vide om omfangsmærker [under Brug rollebaseret adgangskontrol (RBAC) og omfangsmærker for distribueret IT](/mem/intune/fundamentals/scope-tags).

7. På fanen **Opgaver skal** du angive de brugere og enheder, der skal modtage webbeskyttelsespolitikken, og derefter vælge **Næste**.

8. På fanen **Gennemse + Opret** skal du gennemgå dine politikindstillinger og derefter vælge **Opret**.

## <a name="related-topics"></a>Relaterede emner

- [Oversigt over webbeskyttelse](web-protection-overview.md)
- [Webtrusselsbeskyttelse](web-threat-protection.md)
- [Overvåge websikkerhed](web-protection-monitoring.md)
- [Svar på webtrusler](web-protection-response.md)
- [Netværksbeskyttelse](network-protection.md)
