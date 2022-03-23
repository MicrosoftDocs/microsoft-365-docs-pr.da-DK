---
title: Undersøg Microsoft Defender for slutpunktsdomæner
description: Brug undersøgelsesmulighederne til at se, om enheder og servere har kommunikeret med skadelige domæner.
keywords: undersøg domæne, domæne, skadeligt domæne, Microsoft Defender til slutpunkt, advarsel, URL
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: article
ms.date: 04/24/2018
ms.technology: mde
ms.openlocfilehash: bc309c3215524b20ff93c6f1f9c16248fdfffac1
ms.sourcegitcommit: dfa9f28a5a5055a9530ec82c7f594808bf28d0dc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/29/2021
ms.locfileid: "63591864"
---
# <a name="investigate-a-domain-associated-with-a-microsoft-defender-for-endpoint-alert"></a>Undersøg et domæne, der er knyttet til en besked om Microsoft Defender for Endpoint

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigatedomain-abovefoldlink)

Undersøg et domæne for at se, om enheder og servere i virksomhedens netværk har kommunikeret med et kendt ondsindet domæne.

Du kan undersøge et domæne ved hjælp af søgefunktionen eller ved at klikke på et domænelink fra **tidslinjen på enheden**.

Du kan se oplysninger fra følgende afsnit i visningen URL-adresse:

- URL-oplysninger, Kontakter, Navneservere
- Beskeder, der er relateret til denne URL-adresse 
- URL-adresse i organisationen
- Seneste observerede enheder med URL-adresse

## <a name="url-worldwide"></a>URL-adresse over hele verden

Afsnittet **URL Worldwide** indeholder URL-adressen, et link til yderligere oplysninger på Whois, antallet af relaterede åbne hændelser og antallet af aktive beskeder.

## <a name="incident"></a>Hændelse

**Hændelseskortet** viser et liggende søjlediagram over alle aktive beskeder i hændelser i løbet af de seneste 180 dage.

## <a name="prevalence"></a>Eller eller

Det **gyldigt** kort viser oplysninger om url-adressens placering i organisationen over en bestemt tidsperiode.

Selvom standardperioden er de seneste 30 dage, kan du tilpasse området ved at vælge pilen, der peger nedad, i hjørnet af kortet. Det korteste tilgængelige interval er til rådighed i løbet af den seneste dag, mens det længste interval er over de seneste 6 måneder.

## <a name="alerts"></a>Beskeder

Fanen **Vigtige beskeder** indeholder en liste over beskeder, der er knyttet til URL-adressen. Den tabel, der vises her, er en filtreret version af de beskeder, der vises på skærmen Beskedkø, som kun viser vigtige beskeder, der er knyttet til domænet, deres alvorsgrad, status, den tilknyttede hændelse, klassificering, undersøgelsestilstand og meget mere.

Fanen Beskeder kan justeres, så der vises flere eller færre oplysninger, ved at vælge  Tilpas kolonner i handlingsmenuen over kolonneoverskrifterne. Antallet af viste elementer kan også justeres ved at vælge **elementer pr. side** i samme menu.

## <a name="observed-in-organization"></a>Observeret i organisation

Fanen **Observeret i organisation giver** en kronologisk visning af de hændelser og tilknyttede beskeder, der er blevet observeret på URL-adressen. Denne fane indeholder en tidslinje og en tabel, der kan tilpasses med oplysninger om begivenheden, f.eks. klokkeslæt, enhed og en kort beskrivelse af, hvad der skete. 

Du kan få vist begivenheder fra forskellige tidsperioder ved at angive datoerne i tekstfelterne over tabeloverskrifterne. Du kan også tilpasse tidsintervallet ved at vælge forskellige områder af tidslinjen.

**Undersøg et domæne:**

1. Vælg  **URL-adresse i rullemenuen** Søgelinje.
2. Angiv URL-adressen i **feltet** Søg.
3. Klik på søgeikonet, eller tryk på **Enter**. Oplysninger om URL-adressen vises. Bemærk! Søgeresultaterne returneres kun for URL-adresser, der er observeret i kommunikation fra enheder i organisationen.
4. Brug søgefiltrene til at definere søgekriterierne. Du kan også bruge søgefeltet til tidslinjen til at filtrere de viste resultater for alle enheder i organisationen, der har observeret kommunikation med URL-adressen, den fil, der er knyttet til kommunikationen, og den senest observerede dato.
5. Når du klikker på et af enhedsnavnene, kommer du til den pågældende enheds visning, hvor du kan fortsætte med at undersøge rapporterede beskeder, funktionsmåder og hændelser.

## <a name="related-topics"></a>Relaterede emner
- [Få vist og organiser køen for Microsoft Defender for Endpoint Alerts](alerts-queue.md)
- [Administrer Microsoft Defender for Endpoint-beskeder](manage-alerts.md)
- [Undersøg Microsoft Defender for at få slutpunktsbeskeder](investigate-alerts.md)
- [Undersøg en fil, der er knyttet til en besked om Microsoft Defender for Endpoint](investigate-files.md)
- [Undersøg enhederne på listen Microsoft Defender for Slutpunktsenheder](investigate-machines.md)
- [Undersøg en IP-adresse, der er knyttet til en besked om Microsoft Defender for Endpoint](investigate-ip.md)
- [Undersøg en brugerkonto i Microsoft Defender til slutpunkt](investigate-user.md)
