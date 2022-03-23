---
title: Lukke eller slette en sag
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
description: Få mere at vide om, hvad der sker, når en undersøgelse eller en juridisk sag, der Advanced eDiscovery en sag, lukkes eller slettes.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 88e0892bec3f220d9c405f3886c37fa89ad2c647
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63587277"
---
# <a name="close-or-delete-an-advanced-ediscovery-case"></a>Lukke eller slette en Advanced eDiscovery store og små bogstaver

Når den juridiske sag eller undersøgelse, der understøttes af en Advanced eDiscovery sag, er afsluttet, kan du lukke eller slette en sag. Du kan også genåbne en lukket sag.

## <a name="close-a-case"></a>Luk en sag

Her er, hvad der sker, når du lukker en Advanced eDiscovery sag:

- Hvis sagen indeholder indholdsplaceringer, der er i venteposition, deaktiveres disse ventepositioner. Når ventepositionen er deaktiveret, anvendes en udvidet periode på 30 dage (kaldet *forsinkelse) på* indholdsplaceringer, der var i venteposition. Dette er med til at forhindre, at indhold slettes med det samme, og giver administratorer mulighed for at søge efter eller gendanne indhold, der slettes permanent, når perioden for forsinkelse udløber. Få mere at vide under [Fjern indholdsplaceringer fra en eDiscovery-venteposition](create-ediscovery-holds.md#removing-content-locations-from-an-ediscovery-hold).

- Når du lukker en sag, deaktiveres kun de ventende, der er knyttet til den pågældende sag. Hvis andre ventepositioner er på en indholdsplacering (f.eks. retslig venteposition, core eDiscovery-venteposition eller venteposition fra en anden Advanced eDiscovery-sag), bevares disse ventepositioner stadig.

- Sagen er stadig anført på eDiscovery-siden i Microsoft 365 Overholdelsescenter. Detaljer, vente hold, søgninger og medlemmer af en lukket sag bevares.

- Du kan redigere en sag, efter den er lukket. Du kan f.eks. tilføje eller fjerne medlemmer, oprette søgninger, eksportere søgeresultater og forberede søgeresultaterne til analyse i Advanced eDiscovery. Den primære forskel mellem aktive og lukkede sager er, at ventende sager er deaktiveret, når en sag lukkes.

Sådan lukker du en sag:

1. På siden **Advanced eDiscovery** skal du markere den sag, du vil lukke.

2. På fanen **Indstillinger** under Oplysninger om **sag skal** du klikke på **Vælg**.

   ![Få adgang til pop op-siden med sagsoplysninger i en Advanced eDiscovery sag.](..\media\AeDSelectCaseInformation.png) 

3. Nederst på pop **op-siden Med** sagsoplysninger skal du klikke på **Handlinger** og derefter klikke på **Luk sag**.

   Det kan tage op til 60 minutter, før afslutningsprocessen er fuldført.

## <a name="reopen-a-closed-case"></a>Genåbne en lukket sag

Når du genåbner Advanced eDiscovery,, genaktiveres eventuelle ventende anbringelsesrum, der var på plads, da sagen blev lukket, ikke automatisk. Når sagen er genåbnet, skal du gå til fanen Vente **hold og** aktivere de forrige ventende indstillinger. Hvis du vil aktivere en venteposition, skal du markere den for at få vist pop op-siden og derefter indstille **Status** til **Til**.

Sådan genåbner du en lukket sag:

1. På siden **Advanced eDiscovery** skal du vælge den sag, du vil genåbne.

2. På fanen **Indstillinger** under Oplysninger om **sag skal** du klikke på **Vælg**.

3. Nederst på pop **op-siden Med sagsoplysninger** skal du klikke på **Handlinger og** derefter klikke på Åbn **store og små bogstaver igen**.

   Det kan tage op til 60 minutter, før genåbningsprocessen er fuldført.

## <a name="delete-a-case"></a>Slet en sag

Du kan slette både aktive og lukkede Advanced eDiscovery sager. Når du sletter en sag, slettes alle komponenter, der er knyttet til sagen, f.eks. listen over kontrolmedarbejdere, kommunikation, søgninger, korrektursæt og eksportjob. Sagen fjernes fra listen over sager på siden **Advanced eDiscovery** i Microsoft 365 Overholdelsescenter. Du kan ikke genoprette eller genåbne en slettet sag.

> [!NOTE]
> I scenarier med dataudløb er den eneste måde at fjerne elementer i et korrektursæt at slette Advanced eDiscovery tilfælde. Andre "søge- og tømningsmetoder" fjerner ikke elementer fra et korrektursæt.

Før du kan slette en sag (uanset om den er aktiv eller lukket), skal du først slette alle *ventende filer* , der er knyttet til sagen. Det omfatter sletning af ventende filer med statussen **Fra**.

Sådan sletter du ventende filer, der er knyttet til en sag:

1. Gå til **fanen** Vente hold i Advanced eDiscovery, du vil slette.

2. Klik på den venteposition, du vil slette.

3. Klik på Slet hold på pop **op-siden**.

Sådan sletter du en sag:

1. På siden **Advanced eDiscovery** skal du markere den sag, du vil slette.

2. På fanen **Indstillinger** under Oplysninger om **sag skal** du klikke på **Vælg**.

3. Nederst på pop **op-siden Med sagsoplysninger** skal du klikke på **Handlinger og** derefter klikke på **Slet store og små bogstaver**.

