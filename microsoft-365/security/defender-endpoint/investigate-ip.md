---
title: Undersøg en IP-adresse, der er knyttet til en besked
description: Brug undersøgelsesmulighederne til at undersøge mulig kommunikation mellem enheder og eksterne IP-adresser.
keywords: undersøge, undersøge, IP-adresse, advarsel, Microsoft Defender til slutpunkt, ekstern IP
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: article
ms.date: 04/24/2018
ms.technology: mde
ms.openlocfilehash: b20a8d5f1f33ebe62fa1ec9a5e8c8e05dbddbc2b
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63593468"
---
# <a name="investigate-an-ip-address-associated-with-a-microsoft-defender-for-endpoint-alert"></a>Undersøg en IP-adresse, der er knyttet til en besked om Microsoft Defender for Endpoint

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

Undersøg den mulige kommunikation mellem dine enheder og IP-adresser (external internet protocol).

Når du identificerer alle enheder i organisationen, der kommunikeres med en mistænkelig eller kendt ondsindet IP-adresse, f.eks. kommando- og kontrolservere (C2), hjælper det med at bestemme det potentielle omfang af brud, tilknyttede filer og inficeret enheder.

Du kan finde oplysninger fra følgende afsnit i visningen IP-adresse:

- IP over hele verden
- Omvendte DNS-navne
- Beskeder, der er relateret til denne IP
- IP i organisationen
- Eller eller

## <a name="ip-worldwide-and-reverse-dns-names"></a>IP Worldwide og Reverse DNS names

Sektionen med oplysninger om IP-adressen viser attributter for IP-adressen, f.eks. dens ASN og dens Omvendte DNS-navne.

## <a name="alerts-related-to-this-ip"></a>Beskeder, der er relateret til denne IP

Afsnittet **Beskeder, der er relateret til denne IP-adresse** indeholder en liste over beskeder, der er knyttet til IP-adressen.

## <a name="ip-in-organization"></a>IP i organisationen

Afsnittet **IP i organisationen** indeholder oplysninger om, hvor mange IP-adresser i organisationen, der findes i organisationen.

## <a name="prevalence"></a>Eller eller

Afsnittet **Se se** , hvor mange enheder der har forbindelse til denne IP-adresse, og hvornår IP først og sidst blev set. Du kan filtrere resultaterne af denne sektion efter tidsperiode. standardperioden er 30 dage.

## <a name="most-recent-observed-devices-with-ip"></a>Seneste observerede enheder med IP

Afsnittet **Seneste observerede enheder med** IP giver en kronologisk visning af de hændelser og tilknyttede beskeder, der er blevet observeret på IP-adressen.

**Undersøg en ekstern IP:**

1. Vælg **IP** **i rullemenuen** Søgelinje.
2. Angiv IP-adressen i **feltet** Søg.
3. Klik på søgeikonet, eller tryk på **Enter**.

Oplysninger om IP-adressen vises, herunder: registreringsoplysninger (hvis de er tilgængelige), omvendte IP-adresser (f.eks. domæner), enheders enheder i organisationen, der kommunikerede med denne IP-adresse (i løbet af den tidsperiode, der kan vælges), og enhederne i organisationen, der er blevet observeret ved kommunikation med denne IP-adresse.

> [!NOTE]
> Søgeresultaterne returneres kun for IP-adresser, der er observeret i kommunikation med enheder i organisationen.

Brug søgefiltrene til at definere søgekriterierne. Du kan også bruge tidslinjesøgefeltet til at filtrere de viste resultater for alle enheder i organisationen, der har observeret kommunikation med IP-adressen, den fil, der er knyttet til kommunikationen, og den senest observerede dato.

Når du klikker på et af enhedsnavnene, kommer du til den pågældende enheds visning, hvor du kan fortsætte med at undersøge rapporterede beskeder, funktionsmåder og hændelser.

## <a name="related-topics"></a>Relaterede emner

- [Få vist og organiser køen for Microsoft Defender for Endpoint Alerts](alerts-queue.md)
- [Administrer Microsoft Defender for Endpoint-beskeder](manage-alerts.md)
- [Undersøg Microsoft Defender for at få slutpunktsbeskeder](investigate-alerts.md)
- [Undersøg en fil, der er knyttet til en besked om Microsoft Defender for Endpoint](investigate-files.md)
- [Undersøg enhederne på listen Microsoft Defender for Slutpunktsenheder](investigate-machines.md)
- [Undersøg et domæne, der er knyttet til en besked om Microsoft Defender for Endpoint](investigate-domain.md)
- [Undersøg en brugerkonto i Microsoft Defender til slutpunkt](investigate-user.md)
