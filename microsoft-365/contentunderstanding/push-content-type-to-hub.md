---
title: Skubbe indholdstyper til en hub
description: Få mere at vide om, hvordan du skubber indholdstyper til en hub
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.custom: admindeeplinkSPO
ms.localizationpriority: high
ms.openlocfilehash: 4a7a84023f3155c2b6f1405a3da5d8c5776d0047
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63591685"
---
# <a name="push-content-types-to-a-hub"></a>Skubbe indholdstyper til en hub

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4GyeV]  

</br>


Hvis du vil gøre vigtige indholdstyper mere ensartet tilgængelige for SharePoint biblioteker og lister, kan du skubbe dem til de hubs, du vælger. Når du skubber indholdstyper, føjes de automatisk til nye lister og biblioteker, der er oprettet på de websteder, der er knyttet til hubben, og til nye websteder, der føjes til hubben. Denne funktion kræver en [SharePoint Syntex](index.md) licens.

For at denne funktion kan fungere, skal de indholdstyper, der skubbes, allerede være publiceret.

Sådan skubber du indholdstyper til hubs

1. I SharePoint Administration skal du udvide **Indholdstjenester** og derefter vælge <a href="https://go.microsoft.com/fwlink/?linkid=2185074" target="_blank">**galleriet Indholdstype**</a>.
2. Vælg den indholdstype, du vil skubbe til hubs.
3. **Vælg Rediger** på kommandolinjen.
4. Vælg **Vælg hubwebsteder**.
5. Vælg de hubwebsteder, du vil bruge, og vælg derefter **OK**.
6. Vælg **Gem**.

Når du skubber en indholdstype til en eksisterende hub & dens eksisterende tilknyttede websteder for første gang, kan der gå op til en time, fra hubben eller tilknyttede websteder er besøgt, før indstillingerne opdateres på webstedet. Nye tilknytninger til hubben kræver ikke denne ventetid, og indstillingerne afspejles om et par minutter.

Når indstillingerne er opdateret, vil indholdstypen med disse indstillinger være tilgængelig på et websted, der er tilknyttet hubben, efter et par minutter. Standardbiblioteksvisningen ændres til en af disse automatisk oprettede visninger. Hvis der er flere indholdstyper, der er rykket til det samme bibliotek, så er den nyeste (baseret på rækkefølgen af handlingen for at skubbe disse indholdstyper til den hub, dette bibliotek tilhører) det, der vil blive angivet som standardvisningen.  Derefter vil alle nye lister eller biblioteker, der oprettes, automatisk blive føjet til indholdstypen inden for et par minutter efter oprettelse. En tilføjet indholdstype føjes kun til et dokumentbibliotek, hvis den stammer direkte eller indirekte fra dokumentindholdstypen, og en indholdstype kun føjes til en liste, hvis den ikke stammer direkte eller indirekte fra dokumentindholdstypen.

## <a name="see-also"></a>Se også
