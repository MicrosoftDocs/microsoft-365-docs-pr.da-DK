---
title: Administrer udstedelse af medarbejdere i Advanced eDiscovery
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
description: Du kan tilføje medarbejdere, der udsteder medarbejdere for hele organisationen Advanced eDiscovery så de kan føjes til enhver form for kommunikation, som er under kontrol, i alle tilfælde i din organisation.
ms.openlocfilehash: 21c5a3db9cb0cfefb26bc75537f298c7e8a5c09a
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63704795"
---
# <a name="manage-issuing-officers-in-advanced-ediscovery"></a>Administrer udstedelse af medarbejdere i Advanced eDiscovery

Når du eller andre opretter en meddelelse om venteposition eller anden type kommunikation, der sendes til en bruger, som i det tilfælde er vagtansvarlig, skal du angive en udstederofficer. Meddelelsen sendes til vagtchefen på vegne af den angivne udstederofficer. Eksempelvis kan en advokat i din organisation være ansvarlig for at oprette og sende meddelelser om ventepositioner for at varsle i en sag. I dette scenarie kan advokatsekretæren angive en advokat i organisationen som udsteder officer. Who kan angives som udsteder? Der findes to typer brugere, der kan vælges som udsendelsesofficer til kommunikation af en medarbejderofficer:

- Alle medlemmer af det specifikke tilfælde, som kommunikationen sendes på vegne af.

- Alle brugere, der føjes til en liste over udstedere for hele organisationen. Brugere fra denne liste kan føjes en udstederofficer til alle tilfælde i organisationen.

Denne artikel forklarer, hvordan du føjer og fjerner brugere til listen over medarbejdere, der udsteder medarbejdere på tværs af organisationen.

## <a name="before-you-add-an-issuing-officer"></a>Før du tilføjer en udstederofficer

- Du skal være eDiscovery-administrator i din organisation for at tilføje eller fjerne udstedelse af medarbejdere. Få mere at vide under [Tildel eDiscovery-tilladelser i Microsoft 365 Overholdelsescenter](assign-ediscovery-permissions.md)  

- Den bruger, der tilføjes som udsteder, skal have en aktiv postkasse i Microsoft 365 organisation.

- Din organisation kan maksimalt have 15 udstedelsesmedarbejdere. Medlemmer af en sag, der kan angives som udsteder, tælles ikke med i denne grænse. Denne grænse gælder kun for antallet af brugere, der kan føjes til siden **Udstederofficer** i Advanced eDiscovery.

## <a name="add-an-issuing-officer"></a>Tilføj en udstederofficer

1. I Microsoft 365 Overholdelsescenter skal du gå til [Advanced eDiscovery](https://go.microsoft.com/fwlink/p/?linkid=2173764) og derefter klikke på **Advanced eDiscovery indstillinger**.

   ![Vælg Advanced eDiscovery indstillinger](..\media\HistoricalVersions1.png)

2. På siden **Indstillinger** skal du vælge fanen **Udstedelse af medarbejdere** for at få vist **siden Administrer udstedelsesmedarbejdere**.

   ![Indstillingsside for udstedelse af ledere.](..\media\AeDIssuingOfficers1.png)

3. Klik **på Tilføj** , og søg derefter efter og tilføj en eller flere brugere til listen over udstedende medarbejdere.

Når du har tilføjet brugere som medarbejdere ved udstedelse af medarbejdere, kan du eller andre brugere angive disse brugere som udsendelsesmedarbejder for kommunikation for alle tilfælde i organisationen. Du kan finde flere oplysninger om oprettelse af kommunikation for relevante personer [under Opret en meddelelse om retslig venteposition](create-hold-notification.md).

## <a name="remove-an-issuing-officer"></a>Fjern en udstederofficer

1. I Microsoft 365 Overholdelsescenter skal du gå til [Advanced eDiscovery](https://go.microsoft.com/fwlink/p/?linkid=2173764) og derefter klikke på **Advanced eDiscovery indstillinger**.

2. På siden **Indstillinger** skal du vælge **fanen Udsteder medarbejdere**.

3. Vælg en eller flere brugere på listen over kontaktpersoner, der udstedes, og klik derefter på **Slet**.

Når du sletter brugere fra listen over udstedende medarbejdere, kan disse brugere ikke længere angives som udstederofficer i nye kommunikationsformer, der er under kontrol, medmindre brugeren er medlem af den specifikke sag, kommunikationen udstedes fra. Fjernelse af en udsteder vil heller ikke påvirke al kommunikation, der blev sendt, før brugeren blev fjernet som udsteder.
