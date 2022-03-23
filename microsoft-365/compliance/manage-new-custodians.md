---
title: Administrer yt brug af y-Advanced eDiscovery en sag
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
description: Få mere at vide om, hvordan du får vist detaljer, redigerer og masseredigeringer af listen over Advanced eDiscovery en sag.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 794677c8675f044bafb1c9a441e6c2bbee3e1c86
ms.sourcegitcommit: b19e54b3888a0b07d08dbd23172daec303c7c95b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/23/2021
ms.locfileid: "63587909"
---
# <a name="manage-custodians-in-an-advanced-ediscovery-case"></a>Administrer yt brug af y-Advanced eDiscovery en sag

Siden **Med y-personer** **under** fanen Datakilder i en Advanced eDiscovery en liste over alle behandlere, der er blevet føjet til sagen. Når du har føjet førere til en sag, indsamles oplysninger om hver af de kyndige automatisk fra Azure Active Directory og kan vises Advanced eDiscovery.

## <a name="view-custodian-details"></a>Få vist oplysninger om, hvor meget du er på arbejde

Hvis du vil have vist oplysninger om enian, der skal vises, skal du klikke på den, der er øver, på listen under **fanen Yplikator** . Der vises en pop op-side med følgende oplysninger om den, der skal vises.

![Oplysninger om ydsniske oplysninger.](../media/CustodianDetails.PNG)

- Kontaktoplysninger

  - **Titel**. Den andens stilling.
  
  - **Brugerens hovednavn**. Brugerens hovednavn(UPN) for den AdeleV@contoso.onmicrosoft.com.
  
  - **Placering**. Kontorplaceringen i assistentens forretningssted.
  
  - **Chef**. Den, der er ansvarlig for det, er den, der er ansvarlig for det. Den udpegede leder modtager alle meddelelser om eskalering til denne leder.
  
  - **Afdeling**. Navnet på den afdeling, hvor det er den, der er inforberedt.

- Sagsoplysninger

  - **Status**. Status for den, der skal kontrolleres i sagen. En status som **Aktiv angiver** , at deltageren er en del af sagen. Hvis der frigives en kontakt fra en sag, ændres status til **Frigivet**.
  
  - **Hold nede**. Angiver, om han eller hun er blevet sat i venteposition.

- Dataplaceringer og oplysninger om venteposition

  ![Det sted, hvor dataene opbevares, og oplysninger, der skal opbevares.](../media/CustodianHoldDetails.PNG)

  - **Opbevaringsplaceringer**. Viser antallet og typen af datakilder (postkasser, websteder og Teams), der er knyttet til din leder og er en del af sagen.

    - Hver dataplacering viser dens ventepositionsstatus. Mulige værdier for ventepositionsstatus: **I venteposition**, **Ikke i venteposition** og **I gang**.

    - Hvis du ikke kan se en ventepositionsstatus for en datakilde, skal du kontrollere status for den venteposition, der er angivet på fanen **Venteposition** for sagen. Den registrerede person identificerer de bestemte datakilder, der er i venteposition.

## <a name="edit-a-custodian"></a>Redigere en, der er tilsned

Som din sag skrider frem, vil du måske opdage, at der kan være yderligere datakilder, som er relevante for en bestemt person, der skal være relevante for sagen. I andre scenarier kan det være en ide at fjerne bestemte datakilder, der er blevet gennemgået og betragtes som ikke relevante.

Sådan opdaterer du de datakilder, der er knyttet til en leder:

1. Gå til **eDiscovery > Advanced eDiscovery** og åbn sagen.
  
2. Klik på **fanen Datakilder** .
  
3. Vælg en kontaktpersoneret på listen, og klik derefter på **Rediger** på pop op-siden.

    ![Redigere datakilder.](../media/EditCustodianDataSource.PNG)
  
4. Sådan tilføjes eller fjernes den primære postkasse og OneDrive konto, der skal være til hjælp for den pågældende bruger:

    - Udvid den overordnede for at få vist de primære dataplaceringer, der tidligere er knyttet til den person, der skal arbejde med dataene.

    - Klik **på** Rediger ud **for** **Postkasse eller OneDrive** for at tilføje postkassen eller placeringen for OneDrive postkassen.

    - Vælg **Ryd** ud for  Postkasse **eller OneDrive** for at fjerne postkassen eller postkassens OneDrive-konto fra at blive knyttet som en dataplacering for denne bruger.

5. Hvis du vil tilføje eller fjerne andre postkasser, websteder, Teams- eller Yammer-grupper til en bestemt person, der skal være til  hjælp, skal du klikke på Rediger ud for tjenesten for at tilføje en dataplacering.

   - **Exchange**: Bruges til at knytte andre postkasser til assistenten. Skriv navnet eller aliasset (mindst tre tegn) på brugerpostkasser eller distributionsgrupper i søgefeltet. Vælg de postkasser, der skal tildeles til postkassen, og klik derefter på **Tilføj**.

   - **SharePoint**: Bruges til at knytte SharePoint til medarbejderen. Vælg et websted på listen, eller søg efter et websted ved at skrive en URL-adresse i søgefeltet. Vælg de websteder, der skal tildeles til din vismand, og klik derefter på **Tilføj**.

   - **Teams**: Bruges til at tildele Microsoft Teams, som den, der er din medarbejder, aktuelt er medlem af. Vælg de teams, der skal tildeles til din teamleder, og klik derefter på **Tilføj**. Når du har tilføjet et team, identificerer og finder systemet automatisk den SharePoint websteds- og gruppepostkasse, der er knyttet til teamet, og tildeler dem til vedkommende, der er tilknyttet teamet.

   - **Yammer**: Bruges til at tildele de Yammer grupper, som den, der er medlem af, aktuelt er medlem af. Vælg de grupper, der skal tildeles til den, der skal tilknyttes, og klik derefter **på Tilføj**. Når du har tilføjet et team, identificerer og finder systemet automatisk den SharePoint websteds- og gruppepostkasse, der er knyttet til den pågældende gruppe, og tildeler dem til vedkommende, der er tilknyttet teamet.

   > [!NOTE]
   > Du kan bruge placeringsvælgerne Exchange og **SharePoint** til at knytte postkasser eller websteder i organisationen, herunder teams eller Yammer-grupper, som en assistent ikke er medlem af, til en medarbejder. For at gøre dette skal du tilføje både den postkasse og det websted, der er knyttet til hvert team eller Yammer gruppe.

6. Når du har redigeret dataplaceringerne for den person, der er til hjælp, skal du klikke på **Næste** for at **gå til siden med indstillinger for Venteposition** .  

7. På siden **med indstillinger for Venteposition** skal du opdatere indstillingerne for venteposition for den, der skal anvendes.

## <a name="reindex-custodian-data"></a>Inddæd data, der skal være behandler, igen

I de fleste eDiscovery-arbejdsprocesser til juridiske undersøgelser, søges der i et undersæt af en person, der er leder, efter at den person, der skal have foretaget undersøgelsen, er blevet føjet til en juridisk sag. På grund af meget store filstørrelser eller beskadigelse af data kan nogle af elementerne i de datakilder, der er knyttet til en bruger, være delvist indekseret. Ved hjælp [af den](indexing-custodian-data.md) avancerede indekseringsfunktion i Advanced eDiscovery kan de mest delvist indekserede elementer automatisk afhjælpes ved at indeksere disse elementer efter behov igen.

Når en hjælper føjes til en sag, bliver dataene, der er knyttet til den person, der er tilknyttet den, automatisk indekseret (via den avancerede indekseringsproces). Det betyder, at du kan lade dataene være lokale i stedet for at skulle downloade og afhjælpe dem og derefter søge i dem offline). Men under livscyklussen for en juridisk sag kan nye datakilder være knyttet til en person, der er tilknyttet en person. I dette tilfælde kan du genindstille den registreredes data ved at køre den avancerede indekseringsproces igen for at afhjælpe eventuelle delvist indekserede elementer og opdatere indekset for den person, der er til opbevaring.

Sådan udløses indekseringsprocessen til at håndtere delvist indekserede elementer:

1. Gå til **eDiscovery > Advanced eDiscovery** og åbn sagen.

2. Klik på **fanen** Kilder.

3. På siden **YP'er** skal du vælge en øvermand, hvis data skal indekseres igen.

4. Klik på Opdater indeks på pop **op-siden**.

   Der vises en dialogboks, hvor der står, at indeksjobbet er blevet oprettet.

Det er en lang proces at genindsende oplysninger om den person, der skal arbejde med dataene. det tilsvarende job, der oprettes, hedder **Genindeksering af data, der er relevante for den relevante person**. Du kan holde styr på status på **fanen Jobs** eller under fanen **Y'er** ved at overvåge status i **kolonnen Status for indeksering af job** .

Du kan finde flere oplysninger under:

- [Arbejd med behandlingsfejl](processing-data-for-case.md)

- [Administrer job](managing-jobs-ediscovery20.md)

## <a name="release-a-custodian-from-a-case"></a>Frigive en øvermand fra en sag

Der frigives en inficere i situationer, hvor en sag lukkes, den, der skal beskyttes, er ikke længere forpligtet til at bevare indhold i en sag, eller når den ansvarlige for sagen anses for ikke længere at være relevant for sagen. 

Hvis du frigiver en vagtleder, efter at en meddelelse om venteposition er blevet offentliggjort, sendes der en meddelelse til vagtlederen. Desuden fjernes eventuelle ventende funktioner i datakilder, der er knyttet til den person, der har været tilknyttet. Hvis vagten var sat i venteposition *, hvor* der ikke blev udstedt meddelelser om retslig venteposition, sendes der ikke en meddelelse om retslig venteposition, men eventuelle ventepositioner, der er knyttet til den pågældende person, fjernes.

Sådan frigiver du en chef:

1. Gå til **eDiscovery > Advanced eDiscovery** og åbn sagen.

2. Klik på **fanen** Kilder.

3. På siden **YP'er** skal du derefter vælge den person, der skal være den, der bliver frigjort fra sagen.

4. På pop op-siden skal du klikke på **Frigiv, der skal have hjælp.**

   Der vises en advarselsside, der forklarer, at hvis der er sat en venteposition på en datakilde, der er knyttet til det, der er tilknyttet det, der er tilknyttet den, fjernes ventepositionen, og at alle andre ventepositioner, der er knyttet til en anden Advanced eDiscovery-sag, stadig vil være gældende. Dette omfatter andre typer opbevarings- og opbevaringsfunktioner (f.eks. en Microsoft 365 opbevaringspolitik).

5. Klik **på Ja** for at bekræfte, at du vil frigive den pågældende. 

    Status for denne bruger på fanen **Y'er er** angivet til Frigivet, og **status for Venteposition** på pop op-siden ændres til **Falsk**.

> [!NOTE]
> En advokat kan være involveret i flere retstilfælde samtidigt. Når der frigives en besked fra en bestemt sag, påvirkes vente hold og meddelelser på tværs af andre sager ikke.
