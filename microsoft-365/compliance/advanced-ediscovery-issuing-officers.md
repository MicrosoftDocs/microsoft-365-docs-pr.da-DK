---
title: Administrer udstedende medarbejdere i eDiscovery (Premium)
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Du kan tilføje udstedende medarbejdere for hele organisationen i eDiscovery (Premium), så de under alle omstændigheder kan føjes til enhver form for kommunikation i din organisation.
ms.openlocfilehash: 0a3383f9f725a7d5afacd1cab504eefc97b91fd3
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66627685"
---
# <a name="manage-issuing-officers-in-ediscovery-premium"></a>Administrer udstedende medarbejdere i eDiscovery (Premium)

Når du eller andre opretter en meddelelse om venteposition eller en anden type kommunikation, der sendes til en bruger, der er tilsynsførende i tilfælde af, skal du angive en udstedende officer. Meddelelsen sendes til den tilsynsførende på vegne af den angivne udstedende officer. En paralegal i din organisation kan f.eks. være ansvarlig for at oprette og sende meddelelser om venteposition til tilsynsførende i en sag. I dette scenarie kan advokatfuldmægtigen angive en advokat i organisationen som den udstedende officer. Hvem kan angives som udstedende officer? Der er to typer brugere, der kan vælges som udstedende officer til en tilsynsførende kommunikation:

- Ethvert medlem af den specifikke sag, som meddelelsen sendes på vegne af.

- Alle brugere, der føjes til en liste over udstedende medarbejdere i hele organisationen. Brugere fra denne liste kan under alle omstændigheder føjes en udstedende officer til din organisation.

I denne artikel forklares det, hvordan du tilføjer og fjerner brugere på listen over udstedende medarbejdere i hele organisationen.

## <a name="before-you-add-an-issuing-officer"></a>Før du tilføjer en udstedende

- Du skal være eDiscovery-administrator i din organisation for at tilføje eller fjerne udstedende medarbejdere. Du kan finde flere oplysninger under [Tildel eDiscovery-tilladelser i Microsoft Purview-compliance-portal](assign-ediscovery-permissions.md)  

- Den bruger, der tilføjes som udstedende officer, skal have en aktiv postkasse i din Microsoft 365-organisation.

- Din organisation kan maksimalt have 15 udstedende medarbejdere. Medlemmer af en sag, der kan angives som udstedende officer, tælles ikke med i denne grænse. Denne grænse gælder kun for det antal brugere, der kan føjes til siden **Udstedende medarbejdere** i eDiscovery (Premium).

## <a name="add-an-issuing-officer"></a>Tilføj en udstedende officer

1. Gå til [eDiscovery (Premium)](https://go.microsoft.com/fwlink/p/?linkid=2173764) på overholdelsesportalen, og klik derefter på **indstillinger for eDiscovery (Premium**).

   ![Vælg indstillinger for eDiscovery (Premium)](..\media\HistoricalVersions1.png)

2. På siden **Indstillinger** skal du vælge fanen **Udstedende medarbejdere** for at få vist siden **Administrer udstedende medarbejdere** .

   ![Siden Med indstillinger for udstedende officerer.](..\media\AeDIssuingOfficers1.png)

3. Klik på **Tilføj** , og søg derefter efter og føj en eller flere brugere til listen over udstedende medarbejdere.

Når du har tilføjet brugere som udstedende officerer, kan du eller andre brugere under alle omstændigheder i organisationen angive disse brugere som udstedende tilsynsførende for kommunikation. Du kan få flere oplysninger om oprettelse af tilsynsførende kommunikation under [Opret en meddelelse om juridisk venteposition](create-hold-notification.md).

## <a name="remove-an-issuing-officer"></a>Fjern en udstedende

1. Gå til [eDiscovery (Premium)](https://go.microsoft.com/fwlink/p/?linkid=2173764) på overholdelsesportalen, og klik derefter på **indstillinger for eDiscovery (Premium**).

2. På siden **Indstillinger** skal du vælge fanen **Udstedende officerer** .

3. Vælg en eller flere brugere på listen over udstedende medarbejdere, og klik derefter på **Slet**.

Når du har slettet brugere fra listen over udstedende myndigheder, kan disse brugere ikke længere angives som udstedende officer i ny kommunikation med tilsynsførende, medmindre brugeren er medlem af det specifikke tilfælde, som meddelelsen sendes fra. Hvis du fjerner en udstedende officer, påvirker det heller ikke meddelelser, der blev sendt, før brugeren blev fjernet som udstedende officer.
