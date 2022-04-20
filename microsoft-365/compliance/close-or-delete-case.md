---
title: Luk eller slet en sag
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Få mere at vide om, hvad der sker, når en undersøgelse eller en sag, der understøttes af en Microsoft Purview eDiscovery (Premium), lukkes eller slettes.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 45bf34450b430d7d33316fe0e6c6a21d12be2937
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/20/2022
ms.locfileid: "64993244"
---
# <a name="close-or-delete-an-ediscovery-premium-case"></a>Luk eller slet en eDiscovery-sag (Premium)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Når den juridiske sag eller undersøgelse, der understøttes af en Microsoft Purview eDiscovery (Premium)-sag, er fuldført, kan du lukke eller slette en sag. Du kan også genåbne en lukket sag.

## <a name="close-a-case"></a>Luk en sag

Her er, hvad der sker, når du lukker en eDiscovery-sag (Premium):

- Hvis sagen indeholder indholdsplaceringer, der er i venteposition, deaktiveres disse ventepositioner. Når ventepositionen er slået fra, anvendes der en 30-dages udvidet periode (kaldet *forsinkelsesventetid*) på indholdsplaceringer, der var i venteposition. Dette hjælper med at forhindre, at indhold slettes med det samme, og giver administratorer mulighed for at søge efter eller gendanne indhold, der slettes permanent, når forsinkelsesperioden udløber. Du kan finde flere oplysninger under [Fjernelse af indholdsplaceringer fra eDiscovery-venteposition](create-ediscovery-holds.md#removing-content-locations-from-an-ediscovery-hold).

- Hvis du lukker en sag, deaktiveres de ventepositioner, der er knyttet til den pågældende sag, kun. Hvis andre ventepositioner er placeret på en indholdsplacering (f.eks. en retslig venteposition, Microsoft Purview eDiscovery (Standard)-venteposition eller en venteposition fra en anden eDiscovery (Premium)-sag, bevares disse ventepositioner.

- Sagen er stadig angivet på eDiscovery-siden på Microsoft Purview-overholdelsesportalen. Detaljer, ventepositioner, søgninger og medlemmer af en lukket sag bevares.

- Du kan redigere en sag, når den er lukket. Du kan f.eks. tilføje eller fjerne medlemmer, oprette søgninger, eksportere søgeresultater og forberede søgeresultater til analyse i eDiscovery (Premium). Den primære forskel mellem aktive og lukkede sager er, at ventepositioner er slået fra, når en sag lukkes.

Sådan lukker du en sag:

1. Vælg den sag, du vil lukke, på siden **eDiscovery (Premium).**

2. Klik på **Vælg** under **Sagsoplysninger** under fanen **Indstillinger**.

   ![Få adgang til siden med sagsoplysninger i en eDiscovery(Premium)-sag.](..\media\AeDSelectCaseInformation.png) 

3. Nederst på pop op-vinduet **Sagsoplysninger** skal du klikke på **Handlinger** og derefter klikke på **Luk sag**.

   Det kan tage op til 60 minutter, før lukningsprocessen er fuldført.

## <a name="reopen-a-closed-case"></a>Åbn en lukket sag igen

Når du åbner en eDiscovery-sag (Premium) igen, genindføres eventuelle ventepositioner, der var på plads, da sagen blev lukket, ikke automatisk. Når sagen er genåbnet, skal du gå til fanen **Ventepositioner** og slå de forrige ventepositioner til. Hvis du vil slå en venteposition til, skal du vælge den for at få vist pop op-siden og derefter angive **Status** til **Til**.

Sådan genåbner du en lukket sag:

1. Vælg den sag, du vil genåbne, på siden **eDiscovery (Premium).**

2. Klik på **Vælg** under **Sagsoplysninger** under fanen **Indstillinger**.

3. Klik på **Handlinger** nederst på siden **Sagsoplysninger**, og klik derefter på **Genåbn sag**.

   Det kan tage op til 60 minutter, før genåbningsprocessen er fuldført.

## <a name="delete-a-case"></a>Slet en sag

Du kan slette både aktive og lukkede eDiscovery-sager (Premium). Når du sletter en sag, slettes alle komponenter, der er knyttet til sagen, f.eks. listen over tilsynsførende, kommunikation, søgninger, korrektursæt og eksportjob. Sagen fjernes fra listen over sager på siden **eDiscovery (Premium)** på Microsoft Purview-overholdelsesportalen. Du kan ikke gendanne eller genåbne en slettet sag.

> [!NOTE]
> I scenarier med dataspild kan du kun fjerne elementer i et korrektursæt ved at slette eDiscovery-sagen (Premium). Andre "søg og fjern" metoder fjerner ikke elementer fra et korrektursæt.

Før du kan slette en sag (uanset om den er aktiv eller lukket), skal du først slette *alle* ventepositioner, der er knyttet til sagen. Det omfatter sletning af ventepositioner med statussen **Fra**.

Sådan sletter du ventepositioner, der er knyttet til en sag:

1. Gå til fanen **Ventepositioner** i eDiscovery (Premium)-sagen, som du vil slette.

2. Klik på den venteposition, du vil slette.

3. Klik på **Slet venteposition** på pop op-siden.

Sådan sletter du en sag:

1. Vælg den sag, du vil slette, på siden **eDiscovery (Premium).**

2. Klik på **Vælg** under **Sagsoplysninger** under fanen **Indstillinger**.

3. Nederst på pop op-vinduet **Sagsoplysninger** skal du klikke på **Handlinger** og derefter klikke på **Slet sag**.

