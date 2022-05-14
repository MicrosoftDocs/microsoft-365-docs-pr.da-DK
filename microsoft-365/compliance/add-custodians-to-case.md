---
title: Føj tilsynsførende til en eDiscovery-sag (Premium)
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
description: Få mere at vide om, hvordan du bruger det indbyggede værktøj til administration af tilsynsførende i Microsoft Purview eDiscovery (Premium) til at koordinere dine arbejdsprocesser og identificere relevante datakilder i en sag.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 59caac668972968ae3eada2d52d4a5fff8abeae0
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/14/2022
ms.locfileid: "65416106"
---
# <a name="add-custodians-to-an-ediscovery-premium-case"></a>Føj tilsynsførende til en eDiscovery-sag (Premium)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Brug det indbyggede værktøj til administration af tilsynsførende i Microsoft Purview eDiscovery (Premium) til at koordinere dine arbejdsprocesser omkring administration af tilsynsførende og identificere relevante, frihedsberøvende datakilder, der er knyttet til en sag. Når du tilføjer en tilsynsførende, kan systemet automatisk identificere og placere en venteposition på deres Exchange postkasse og OneDrive for Business konto. Under undersøgelsens registreringsproces kan du også identificere andre datakilder (f.eks. postkasser, websteder eller Teams), som en tilsynsførende har tilgået eller bidraget til. I denne situation kan du bruge værktøjet til administration af tilsynsførende til at knytte disse datakilder til en bestemt tilsynsførende. Når du har føjet tilsynsførende til en sag og knyttet andre datakilder til dem, kan du hurtigt bevare data og søge i dataene om varetægtsfængsling.

Du kan tilføje og administrere tilsynsførende i eDiscovery-sager (Premium) i fire trin:

1. Identificer vogterne.

2. Vælg dataplaceringer for tilsynsførende.

3. Konfigurer indstillinger for venteposition.

4. Gennemse vogterne, og fuldfør processen.

## <a name="make-sure-you-have-the-necessary-permissions"></a>Sørg for, at du har de nødvendige tilladelser

Hvis du vil føje tilsynsførende til en sag, skal du være medlem af rollegruppen eDiscovery Manager. Dette giver dig de nødvendige tilladelser til at føje tilsynsførende til en sag og placere en venteposition på datakilderne for frihedsberøvelse. Du kan finde flere oplysninger under [Tildel eDiscovery-tilladelser](get-started-with-advanced-ediscovery.md#step-2-assign-ediscovery-permissions).

## <a name="step-1-identify-custodians"></a>Trin 1: Identificer tilsynsførende

1. Gå til , [https://compliance.microsoft.com](https://compliance.microsoft.com) og log på med en brugerkonto, der er tildelt de relevante eDiscovery-tilladelser.

2. Vælg **eDiscoveryeDiscovery** >  **(Premium)** i navigationsruden til venstre i Microsoft Purview-compliance-portal, og vælg fanen [**Sager**](https://go.microsoft.com/fwlink/p/?linkid=2173764).

3. Vælg den sag, du vil føje tilsynsførende til.

4. Vælg fanen **Datakilder**, og vælg derefter **Tilføj** **datakildeTilføj** >  nye tilsynsførende.

5. Føj en eller flere brugere i din organisation som vogtere til sagen ved at skrive den første del af en persons navn eller alias. Når du har fundet den korrekte person, skal du vælge vedkommendes navn for at føje vedkommende til listen.

## <a name="step-2-choose-custodian-data-locations"></a>Trin 2: Vælg dataplaceringer for tilsynsførende

Når du har valgt tilsynsførende, forsøger systemet automatisk at identificere og bekræfte disse brugere og deres datakilder. Når du har føjet tilsynsførende til listen, inkluderer værktøjet automatisk den primære postkasse og OneDrive konto for hver tilsynsførende. Du kan vælge ikke at inkludere disse datakilder, når du føjer tilsynsførende til sagen.

Ud over en tilsynsførendes postkasse og OneDrive konto kan du også knytte andre dataplaceringer til en tilsynsførende, f.eks. SharePoint websted eller et Microsoft Team, som vogteren er medlem af. Dette giver dig mulighed for at bevare, indsamle, analysere og gennemse indhold i andre datakilder, der er knyttet til vogterne af sagen.

Sådan fravælger du den primære postkasse og OneDrive konto til en tilsynsførende:

1. Udvid tilsynsførende for at få vist de primære dataplaceringer, der automatisk er knyttet til hver enkelt tilsynsførende.

2. Vælg **Ryd** ud for **Postkasse** eller **OneDrive** for at fjerne en tilsynsførendes postkasse eller OneDrive konto fra at blive tilknyttet som en dataplacering for denne tilsynsførende.

   ![Konfigurer placeringer, der skal knyttes til en tilsynsførende.](../media/ConfigureCustodianLocations.png)

Sådan knytter du andre postkasser, websteder, Teams eller Yammer grupper til en bestemt tilsynsførende:

1. Udvid en tilsynsførende for at få vist følgende tjenester for at knytte dataplaceringer til tilsynsførende. Klik på **Rediger** ud for en tjeneste for at tilføje en dataplacering.

   - **Exchange**: Bruges til at knytte andre postkasser til tilsynsførende. Skriv navnet eller aliasset (mindst tre tegn) for brugerpostkasser eller distributionsgrupper i søgefeltet. Vælg de postkasser, der skal tildeles til tilsynsførende, og klik derefter på **Tilføj**.

   - **SharePoint**: Bruges til at knytte SharePoint websteder til vogteren. Vælg et websted på listen, eller søg efter et websted ved at skrive en URL-adresse i søgefeltet. Vælg de websteder, der skal tildeles til tilsynsførende, og klik derefter på **Tilføj**.

   - **Teams**: Bruges til at tildele det Microsoft Teams, som vogteren i øjeblikket er medlem af. Vælg de teams, der skal tildeles til tilsynsførende, og klik derefter på **Tilføj**. Når du har tilføjet et team, identificerer og finder systemet automatisk det SharePoint websted og gruppepostkasse, der er knyttet til teamet, og tildeler dem til tilsynsførende.

   - **Yammer**: Bruges til at tildele de Yammer grupper, som vogteren i øjeblikket er medlem af. Vælg de grupper, der skal tildeles til tilsynsførende, og klik derefter på **Tilføj**. Når du har tilføjet et team, identificerer og finder systemet automatisk det SharePoint websted og gruppepostkasse, der er knyttet til gruppen, og tildeler dem til tilsynsførende.

   > [!NOTE]
   > Du kan bruge **Exchange** og **SharePoint** placeringsvælgere til at knytte en postkasse eller et websted i din organisation til en tilsynsførende. , Dette omfatter tilknytning af postkassen og webstedet for en Microsoft-gruppe eller Yammer gruppe, som en tilsynsførende ikke er medlem af. Det gør du ved at tilføje både den postkasse og det websted, der er knyttet til hvert team eller Yammer gruppe.

2. Du kan få vist det samlede antal postkasser, websteder, Teams og Yammer grupper, der er tildelt hver tilsynsførende, ved at udvide hver tilsynsførende i tabellen. Når du har færdiggjort de tildelte dataplaceringer for hver tilsynsførende, vedligeholdes og bruges disse tilknytninger under indsamlings-, behandlings- og gennemsynsfaserne i arbejdsprocessen for eDiscovery (Premium).

3. Når du har tilføjet tilsynsførende og konfigureret deres dataplaceringer, skal du klikke på **Næste** for at gå til siden **Indstillinger for venteposition** .  

## <a name="step-3-configure-hold-settings"></a>Trin 3: Konfigurer indstillinger for venteposition

 Når du har færdiggjort vogterne og deres dataplaceringer, kan du placere nogle eller alle tilsynsførende i venteposition. Når du sætter en tilsynsførende i venteposition, bevares alt indhold på alle indholdsplaceringer, der er knyttet til vogteren, indtil du fjerner ventepositionen eller frigiver vogteren fra ventepositionen. I nogle tilfælde kan det være en god idé at føje tilsynsførende til en sag uden at sætte dem i venteposition.

Sådan placerer du tilsynsførende og datakilder i venteposition:

1. På siden **Indstillinger for venteposition** kan du anvende en venteposition på individuelle tilsynsførende ved at markere afkrydsningsfeltet under kolonnen **Venteposition** .

   Du kan også placere alle tilsynsførende i venteposition ved at markere afkrydsningsfeltet **Hold** i venteposition øverst i kolonnen.

2. Kontrollér valgene for frihedsberøvelse, og klik derefter på **Næste**.

   > [!NOTE]
   > Hvis du ikke tilbageholder en tilsynsførende, føjes tilsynsførende og deres tilknyttede datakilder til sagen, men indholdet i disse datakilder bevares ikke af den venteposition, der er knyttet til sagen.

## <a name="step-4-review-the-custodians-and-complete-the-process"></a>Trin 4: Gennemse vogterne, og fuldfør processen

Før du rent faktisk føjer vogterne til sagen, kan du gennemse listen over tilsynsførende, de dataplaceringer, der er tildelt dem, og indstillinger for venteposition.

1. Bekræft og gennemse alle antallet af datakilder og indstillingen for venteposition, der er knyttet til hver tilsynsførende i tabellen. Hvis det er nødvendigt, skal du gå tilbage til siderne Med indstillinger for **Identificer tilsynsførende** eller **Venteposition** for at foretage ændringer.

2. Klik på **Send** for at føje tilsynsførende og deres dataplaceringer til sagen og anvende alle indstillinger for frihedsberøvelse.

   De nye tilsynsførende føjes til sagen og vises på fanen **Datakilder** .

   [![Tilsynsførende, der er angivet under fanen Datakilder.](../media/DataSourcesTab.png) ](../media/DataSourcesTab.png#lightbox)
