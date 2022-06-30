---
title: Oversigt over slutpunktsregistrerings- og svarfunktioner
ms.reviewer: ''
description: Få mere at vide om funktionaliteten til registrering af slutpunkter og svar i Microsoft Defender for Endpoint
keywords: Microsoft Defender for Endpoint, registrering og svar på slutpunkter, svar, opdagelse, cybersikkerhed, beskyttelse
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
ms.technology: mde
ms.openlocfilehash: 757064e8867cda8676fd0cf20a662ff04d130e9c
ms.sourcegitcommit: bc35c7826e3403f259725ac72cca5bafd36aa56a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/30/2022
ms.locfileid: "66554505"
---
# <a name="overview-of-endpoint-detection-and-response"></a>Oversigt over registrering og svar af slutpunkter

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1 og 2](defender-endpoint-plan-1-2.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Funktionerne til registrering af slutpunkter og svar i Defender for Endpoint giver avancerede angrebsregistreringer, der er næsten i realtid og kan handles på. Sikkerhedsanalytikere kan prioritere beskeder effektivt, få indsigt i det fulde omfang af et brud og reagere på trusler.

Når der registreres en trussel, oprettes der beskeder i systemet, som en analytiker skal undersøge. Beskeder med de samme angrebsteknikker eller tilskrevet den samme person med ondsindede hensigter samles i en enhed, der kaldes en _hændelse_. Sammenlægning af beskeder på denne måde gør det nemt for analytikere samlet at undersøge og reagere på trusler.

> [!NOTE]
> Defender for Endpoint Detection er ikke beregnet til at være en overvågnings- eller logføringsløsning, der registrerer alle handlinger eller aktiviteter, der udføres på et bestemt slutpunkt. Vores sensor har en intern begrænsningsmekanisme, så den høje frekvens af gentagne identiske hændelser oversvømmer ikke loggene.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4o1j5]

> [!IMPORTANT]
> [Defender for Endpoint Plan 1](defender-endpoint-plan-1.md) og [Microsoft Defender til virksomheder](../defender-business/mdb-overview.md) kun indeholde følgende manuelle svarhandlinger:
> - Kør antivirusscanning
> - Isoler enhed
> - Stop og sæt en fil i karantæne
> - Tilføj en indikator for at blokere eller tillade en fil

Defender for Endpoint indsamler løbende adfærdsbestemt cybertelemetri inspireret af tankegangen "antag brud". Dette omfatter procesoplysninger, netværksaktiviteter, detaljeret optik i kerne- og hukommelsesstyring, brugerlogonaktiviteter, ændringer i registreringsdatabasen og filsystemet m.m. Oplysningerne gemmes i seks måneder, hvilket gør det muligt for en analytiker at rejse tilbage i tiden til starten af et angreb. Analytikeren kan derefter pivotere i forskellige visninger og nærme sig en undersøgelse via flere vektorer.

Svarfunktionerne giver dig mulighed for straks at afhjælpe trusler ved at reagere på de berørte enheder.

## <a name="related-topics"></a>Relaterede emner

- [Dashboard til sikkerhedshandlinger](security-operations-dashboard.md)
- [Kø over hændelser](view-incidents-queue.md)
- [Beskedkøer](alerts-queue.md)
- [Liste over enheder](machines-view-overview.md)
