---
title: Oversigt over integration af Microsoft Defender til skyapps
ms.reviewer: ''
description: Microsoft Defender for Endpoint integreres med Defender for Cloud Apps ved at videresende alle netværksaktiviteter i skyen.
keywords: sky, app, netværk, synlighed, brug
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
ms.date: 10/18/2018
ms.technology: mde
ms.openlocfilehash: d3cf5259aeb070175d5d2a4a95154974c6cd4d56
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63592742"
---
# <a name="microsoft-defender-for-cloud-apps-in-defender-for-endpoint-overview"></a>Oversigt over Microsoft Defender til skyapps i Defender til slutpunkt

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

[!include[Prerelease information](../../includes/prerelease.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Microsoft Defender til skyapps er en omfattende løsning, der giver indblik i skyapps og -tjenester ved at give dig mulighed for at styre og begrænse adgangen til skyapps, samtidig med at du gennemtvinger overholdelseskrav til data, der er gemt i skyen. Du kan få mere at vide [under Defender til skyapps](/cloud-app-security/what-is-cloud-app-security).

> [!NOTE]
> Denne funktion er tilgængelig med en E5-licens [til Enterprise Mobility + Security](https://www.microsoft.com/cloud-platform/enterprise-mobility-security) på enheder, der Windows 10 version 1809 eller nyere eller Windows 11.

## <a name="microsoft-defender-for-endpoint-and-defender-for-cloud-apps-integration"></a>Integration af Microsoft Defender for Endpoint og Defender til skyapps

Defender til opdagelse af skyapps afhænger af, at skytrafiklogfiler videresendes til den fra virksomhedens firewall og proxyservere. Microsoft Defender til slutpunkt integreres med Defender for Cloud Apps ved at indsamle og videresende alle netværksaktiviteter i skyen, hvilket giver uovertrufne synlighed i brugen af skyapps. Overvågningsfunktionaliteten er indbygget i enheden, hvilket giver fuld dækning af netværksaktivitet.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4r4yQ]

Integrationen indeholder følgende væsentlige forbedringer af den eksisterende opdagelse af Defender til skyapps:

- Tilgængelig overalt – Da netværksaktiviteten indsamles direkte fra slutpunktet, er den tilgængelig overalt, hvor enheden er til eller fra virksomhedens netværk, da den ikke længere afhænger af trafik, der dirigeres gennem virksomhedens firewall eller proxyservere.

- Fungerer uden videre, kræver ingen konfiguration – Videresendelse af skytrafiklogfiler til Defender til skyapps kræver firewall og proxyserverkonfiguration. Med integration af Defender for Endpoint og Defender for Cloud Apps er der ingen konfiguration påkrævet. Du skal bare slå det til Microsoft 365 Defender indstillingerne, og så er du klar.

- Enhedskontekst – Skytrafiklogfiler mangler enhedskontekst. Defender for slutpunktsnetværksaktiviteter rapporteres med enhedskonteksten (hvilken enhed, der fik adgang til skyappen), så du kan forstå præcis, hvor (enhed) netværksaktiviteten fandt sted, ud over hvem (bruger) der udførte den.

Du kan finde flere oplysninger om opdagelse i skyen [under Arbejde med apps, der opdages](/cloud-app-security/discovered-apps).

## <a name="related-topic"></a>Relateret emne

- [Konfigurer integration af Microsoft Defender til skyapps](microsoft-cloud-app-security-config.md)
