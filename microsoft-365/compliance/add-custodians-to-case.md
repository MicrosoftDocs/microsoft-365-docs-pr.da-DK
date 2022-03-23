---
title: Føje Advanced eDiscovery ere til Advanced eDiscovery sag
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
description: Få mere at vide om, hvordan du bruger det indbyggede værktøj til kontrol af Advanced eDiscovery at koordinere dine arbejdsprocesser og identificere relevante datakilder i en sag.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: b0a15610c84c9e1142cd1afa6ebf121f387ce807
ms.sourcegitcommit: 2e05865beeb2051fd9ece212a46179310b946a46
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/23/2021
ms.locfileid: "63587488"
---
# <a name="add-custodians-to-an-advanced-ediscovery-case"></a>Føje Advanced eDiscovery ere til Advanced eDiscovery sag

Brug det indbyggede værktøj til kontrol af forældreforberedende arbejde i Advanced eDiscovery til at koordinere dine arbejdsprocesser omkring administration af hjælpere og identificere relevante, koordinerede datakilder, der er knyttet til en sag. Når du tilføjer en revisor, kan systemet automatisk identificere og placere en venteposition på deres Exchange og OneDrive for Business konto. Under din undersøgelsesproces kan du også identificere andre datakilder (f.eks. postkasser, websteder eller Teams), som en person, der har fået adgang til eller bidraget til, har fået adgang til. I denne situation kan du bruge værktøjet til kontrol af, hvordan man tilknytter disse datakilder, en specifik assistent. Når du har føjet assistenter til en sag og knytter andre datakilder til dem, kan du hurtigt bevare data og søge efter dataene, der skal beskyttes.

Du kan tilføje og administrere  tilføjelser i Advanced eDiscovery tilfælde i fire trin:

1. Identificer de øverere, der skal øver sig.

2. Vælg sted, hvor der er adgang til dine data.

3. Konfigurer indstillinger for venteposition.

4. Gennemgå yteringsianerne, og fuldfør processen.

## <a name="make-sure-you-have-the-necessary-permissions"></a>Sørg for, at du har de nødvendige tilladelser

Hvis du vil føje projektledere til en sag, skal du være medlem af rollegruppen eDiscovery Manager. Dette giver dig de nødvendige tilladelser til at føje y-brugere til en sag og placere en venteposition på de vigtigste datakilder. Få mere at vide under [Tildel eDiscovery-tilladelser](get-started-with-advanced-ediscovery.md#step-2-assign-ediscovery-permissions).

## <a name="step-1-identify-custodians"></a>Trin 1: Identificer forældreforseende

1. Gå til [https://compliance.microsoft.com](https://compliance.microsoft.com) og log på med en brugerkonto, der har fået tildelt de relevante eDiscovery-tilladelser.

2. I venstre navigationsrude i Microsoft 365 Overholdelsescenter skal du **vælge eDiscovery** >  **Advanced eDiscovery** og vælge [**fanen**](https://go.microsoft.com/fwlink/p/?linkid=2173764) Sager.

3. Vælg den sag, du vil føje y-y-væsner til.

4. Vælg fanen **Datakilder**, og vælg derefter Tilføj **datakilderFængsere** >  **nye årsagen til dette**.

5. Tilføj en eller flere brugere i organisationen som brugere af sagen ved at skrive den første del af en persons navn eller alias. Når du har fundet den rigtige person, skal du vælge personens navn for at føje vedkommende til listen.

## <a name="step-2-choose-custodian-data-locations"></a>Trin 2: Vælg dataplaceringer, der skal være under vejledning

Når du har valgt brugere, der skal kontrolleres, forsøger systemet automatisk at identificere og bekræfte disse brugere og deres datakilder. Når du har føjet hjælpere til listen, medtager værktøjet automatisk den primære postkasse og den primære OneDrive-konto for hver af de personer, der er tilsvarer. Du kan vælge ikke at medtage disse datakilder, når du føjer ydsere til sagen.

Ud over en assistents postkasse og OneDrive-konto kan du også knytte andre dataplaceringer til en medarbejder, f.eks. SharePoint-websted, eller et Microsoft-team, som assistenten er medlem af. På denne måde kan du bevare, indsamle, analysere og gennemgå indhold i andre datakilder, der er knyttet til sagens brugere.

Sådan fravælger du den primære postkasse OneDrive konto til en bruger, der skal have en konto:

1. Udvid den vismand, der skal have adgang til, for at få vist de primære dataplaceringer, der automatisk er knyttet til hver modtager.

2. Vælg **Ryd** ud for  Postkasse **eller OneDrive** for at fjerne en postkasseejers eller OneDrive-konto fra at blive knyttet som en dataplacering for denne bruger.

   ![Konfigurer placeringer, der skal knyttes til en assistent.](../media/ConfigureCustodianLocations.png)

Sådan knyttes andre postkasser, websteder, Teams eller grupper Yammer til en bestemt assistent:

1. Udvid en assistent, der skal arbejde, for at få vist følgende tjenester for at knytte dataplaceringer til assistenten. Klik **på Rediger** ud for en tjeneste for at tilføje en dataplacering.

   - **Exchange**: Bruges til at knytte andre postkasser til assistenten. Skriv navnet eller aliasset (mindst tre tegn) på brugerpostkasser eller distributionsgrupper i søgefeltet. Vælg de postkasser, der skal tildeles til postkassen, og klik derefter på **Tilføj**.

   - **SharePoint**: Bruges til at knytte SharePoint til medarbejderen. Vælg et websted på listen, eller søg efter et websted ved at skrive en URL-adresse i søgefeltet. Vælg de websteder, der skal tildeles til din vismand, og klik derefter på **Tilføj**.

   - **Teams**: Bruges til at tildele Microsoft Teams, som den, der er din medarbejder, aktuelt er medlem af. Vælg de teams, der skal tildeles til din teamleder, og klik derefter på **Tilføj**. Når du har tilføjet et team, identificerer og finder systemet automatisk den SharePoint websteds- og gruppepostkasse, der er knyttet til teamet, og tildeler dem til vedkommende, der er tilknyttet teamet.

   - **Yammer**: Bruges til at tildele de Yammer grupper, som den, der er medlem af, aktuelt er medlem af. Vælg de grupper, der skal tildeles til den, der skal tilknyttes, og klik derefter **på Tilføj**. Når du har tilføjet et team, identificerer og finder systemet automatisk den SharePoint websteds- og gruppepostkasse, der er knyttet til den pågældende gruppe, og tildeler dem til vedkommende, der er tilknyttet teamet.

   > [!NOTE]
   > Du kan bruge **vælgerne Exchange** og **SharePoint** til at knytte postkasser eller websteder i organisationen til en medarbejder, der er tilknyttet. , Dette omfatter tilknytning af postkassen og webstedet for et Microsoft-team eller Yammer, som en medarbejdergruppe ikke er medlem af. For at gøre dette skal du tilføje både den postkasse og det websted, der er knyttet til hvert team eller Yammer gruppe.

2. Du kan få vist det samlede antal postkasser, websteder, Teams og Yammer grupper, der er tildelt til hver enkelt fremviser, ved at udvide hver enkelt hjælpelinje i tabellen. Når du har færdiggjort de tildelte dataplaceringer for hver seerleder, vedligeholdes og bruges disse tilknytninger under indsamling, behandling og gennemgang i Advanced eDiscovery arbejdsproces.

3. Når du har tilføjet tilpasningsianianer og konfigureret deres dataplaceringer, skal du klikke **på Næste** for at gå **til siden med indstillinger for** Venteposition.  

## <a name="step-3-configure-hold-settings"></a>Trin 3: Konfigurer indstillinger for venteposition

 Når du er færdig med at have ydseret deres ydsere og deres dataplaceringer, kan du placere nogle eller alle oritterne i venteposition. Når du anbringer en leder, der skal hjælpe, i venteposition, bevares alt indhold på alle indholdsplaceringer, der er knyttet til den, der skal håndteres, indtil du fjerner ventepositionen eller frigiver det pågældende indhold fra ventepositionen. I nogle tilfælde kan det være en god ide at føje  opstillinger til en sag uden at sætte dem i venteposition.

Sådan anbringer du esvarslende og datakilder i venteposition:

1. På siden **med indstillinger for** Venteposition kan du anvende venteposition for individuelle øverere ved at markere afkrydsningsfeltet under **kolonnen Venteposition** .

   Du kan også placere alle y-afkrydsningsfelter i venteposition ved at **markere** afkrydsningsfeltet Sæt i venteposition øverst i kolonnen.

2. Kontrollér markeringerne for kontrol af ventepositionen, og klik derefter på **Næste**.

   > [!NOTE]
   > Hvis du ikke anbringer en venteposition hos en, der er tilknyttet, føjes den, der er tilknyttet datakilden, til sagen, men indholdet i disse datakilder bevares ikke af det hold, der er knyttet til sagen.

## <a name="step-4-review-the-custodians-and-complete-the-process"></a>Trin 4: Gennemgå yteringerne og fuldfør processen

Før du rent faktisk føjer medarbejdere til sagen, kan du gennemgå listen over kontrolianer, de dataplaceringer, der er tildelt dem, og indstillingerne for venteposition.

1. Bekræft og gennemse alle datakildernes antal og indstillingen for venteposition, der er knyttet til hvervarsmand i tabellen. Hvis det er nødvendigt, kan du gå tilbage til **indstillingssiderne Identificer** og Hold for at foretage eventuelle ændringer.

2. Klik **på Send** for at føje opbevaringsere og deres dataplaceringer til sagen og anvende alle indstillinger for hold ved opbevaring.

   De nye øverere føjes til sagen og vises på **fanen** Datakilder.

   [![Y-y-1-1-2, der er angivet under fanen Datakilder.](../media/DataSourcesTab.png) ](../media/DataSourcesTab.png#lightbox)
