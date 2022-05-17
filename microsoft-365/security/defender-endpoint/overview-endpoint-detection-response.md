---
title: Oversigt over slutpunktsregistrering og -svar funktioner
ms.reviewer: ''
description: Få mere at vide om slutpunktsregistrering og -svar funktioner i Microsoft Defender for Endpoint
keywords: Microsoft Defender for Endpoint, slutpunktsregistrering og -svar, svar, opdagelse, cybersikkerhed, beskyttelse
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
ms.openlocfilehash: 78f05c9e366d2f8b4d5b4d7697961f0d702581f8
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/17/2022
ms.locfileid: "65438520"
---
# <a name="overview-of-endpoint-detection-and-response"></a>Oversigt over slutpunktsregistrering og -svar

**Gælder for:**
- [Microsoft Defender for Endpoint plan 1 og 2](defender-endpoint-plan-1-2.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Defender for Endpoint slutpunktsregistrering og -svar funktioner giver avancerede angrebsregistreringer, der er næsten i realtid og kan handles på. Sikkerhedsanalytikere kan prioritere beskeder effektivt, få indsigt i det fulde omfang af et brud og reagere på trusler.

Når der registreres en trussel, oprettes der beskeder i systemet, som en analytiker skal undersøge. Beskeder med de samme angrebsteknikker eller tilskrevet den samme person med ondsindede hensigter samles i en enhed, der kaldes en _hændelse_. Sammenlægning af beskeder på denne måde gør det nemt for analytikere samlet at undersøge og reagere på trusler.

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
