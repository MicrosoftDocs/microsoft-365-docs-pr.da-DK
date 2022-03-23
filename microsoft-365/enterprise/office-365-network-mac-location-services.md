---
title: Microsoft 365 til placeringstjenester for netværksforbindelse
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 12/06/2021
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: admindeeplinkMAC
description: Microsoft 365 til placeringstjenester for netværksforbindelse
ms.openlocfilehash: 6150102471b03fbc83be09b503a6969ca6615a87
ms.sourcegitcommit: 388279e10a160b85b345a8ad760f6816dda4e2ad
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/07/2021
ms.locfileid: "63590585"
---
# <a name="microsoft-365-network-connectivity-location-services"></a>Microsoft 365 til placeringstjenester for netværksforbindelse

I <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a> nu **Network Insights performance recommendations**, som er målepunkter for live performance, der indsamles fra din Microsoft 365 lejer. Disse målepunkter kan kun ses af administrative brugere i din lejer. Organisationsnetværksforbindelsen er designet pr. kontorplacering via en netværks udgangspunktplacering til internettet. Microsoft 365 klientforbindelse bruger denne rute og derefter på tværs af internettet til Microsoft-front doorservere. At identificere kontorplaceringer er nøglen til at kunne vise disse netværksindsigt.

## <a name="location-in-network-measurements"></a>Placering i netværksmål

En organisations administrator kan vælge placering, som skal medtages i de netværksmål, der bruges af denne funktion. Dette muliggør automatisk registrering af den by, hvor hvert kontor er placeret. Placeringsoplysninger er ikke nøjagtige og er slørede til 300m og kategoriseres efter by. På det tidspunkt, hvor placeringen registreres på Windows enhed, viser enheden et **Placeringsikon** i brug i proceslinjen. Administratorer kan give brugerne besked om udseendet af dette ikon. Med denne behandling behandles placeringen som organisationens kontorplacering og ikke placeringen af en person eller en enhed. Netværksindsigt kan vises i disse opdagede byer for kontorplaceringer. Hvis du vil have større nøjagtighed i anbefalingerne, kan du angive bestemte adresser for kontorplacering. Netværksindsigt samles til disse placeringer i stedet. Office placeringer kan ikke aggregeres mere end 300 meter.

## <a name="location-in-the-microsoft-365-admin-center"></a>Placering i Microsoft 365 Administration Center

I Microsoft 365 Administration <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">bruges</a> Bing til at vise, hvor organisationens kontorplaceringer er. Kontrolelementerne viser også netværkets perimetertopologi for en valgt kontorplacering. Når en administrator tilføjer specifikke adresseoplysninger for kontorplaceringer, bruges Bing Kort også til at foreslå adresser for at gøre det nemmere at dataindtastning.

## <a name="terms-of-use"></a>Vilkår for anvendelse

Alt indhold leveret via Bing Kort, herunder geokoder, kan kun bruges i det produkt, hvorfra indholdet er leveret. Kundens brug af funktionen Microsoft 365 Administration-placeringstjenester, der leveres af Bing Kort, er underlagt _de vilkår_ for anvendelse af <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Bing Kort End-User</a><https://go.microsoft.com/?linkid=9710837>, der er tilgængelige på og Microsofts erklæring om beskyttelse af [personlige oplysninger](https://go.microsoft.com/fwlink/?LinkID=248686).

Denne funktion, som leveres Bing Kort, understøttes også af **TomTom**. Du kan finde flere oplysninger om TomToms produkter og tjenester på [https://www.tomtom.com/legal](https://www.tomtom.com/legal).

## <a name="related-topics"></a>Relaterede emner

[Netværksforbindelse i Microsoft 365 Administration Center](office-365-network-mac-perf-overview.md)

[Microsoft 365 indsigt i netværksydeevne](office-365-network-mac-perf-insights.md)

[Microsoft 365 netværksvurdering](office-365-network-mac-perf-score.md)

[Microsoft 365 forbindelsestest i Microsoft 365 Administration](office-365-network-mac-perf-onboarding-tool.md)
