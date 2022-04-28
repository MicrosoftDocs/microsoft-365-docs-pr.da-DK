---
title: Administrer tilsynsførende i en eDiscovery-sag (Premium)
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
description: Få mere at vide om, hvordan du får vist detaljer, redigerer og masserediger listen over tilsynsførende i en eDiscovery-sag (Premium).
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 6ea05e2f0b19c23b236f7b64eb3a425fdb29cc39
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65077938"
---
# <a name="manage-custodians-in-an-ediscovery-premium-case"></a>Administrer tilsynsførende i en eDiscovery-sag (Premium)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Siden **Tilsynsførende** under fanen **Datakilder** i en Microsoft Purview eDiscovery-sag (Premium) indeholder en liste over alle tilsynsførende, der er føjet til sagen. Når du har føjet tilsynsførende til en sag, indsamles oplysninger om hver enkelt tilsynsførende automatisk fra Azure Active Directory og kan ses i eDiscovery (Premium).

## <a name="view-custodian-details"></a>Vis oplysninger om tilsynsførende

Hvis du vil have vist oplysninger om en tilsynsførende, skal du klikke på tilsynsførende på listen under fanen **Tilsynsførende** . Der vises en pop op-side, som indeholder følgende oplysninger om vogteren.

![Oplysninger om tilsynsførende.](../media/CustodianDetails.PNG)

- Kontaktoplysninger

  - **Titel**. Forældremyndighedens stilling.
  
  - **Brugerens hovednavn**. Brugerens hovednavn (UPN) for tilsynsførende, f.eks. AdeleV@contoso.onmicrosoft.com.
  
  - **Placering**. Kontor i fængselsinspektørens forretningssted.
  
  - **Leder**. Forældremyndighedens chef. Den udpegede leder modtager enhver eskaleringskommunikation for denne tilsynsførende.
  
  - **Afdeling**. Navnet på den afdeling, hvor vogteren arbejder.

- Sagsoplysninger

  - **Status**. Forældremyndighedens status i sagen. Statussen **Aktiv** angiver, at frihedsberøveren er en del af sagen. Hvis en varetægtsfængsling frigives fra en sag, ændres statussen til **Frigivet**.
  
  - **Vent**. Angiver, om varens varetægtsfængsling er sat i venteposition.

- Dataplaceringer og oplysninger om venteposition

  ![Dataplaceringer og oplysninger om bevarelse af data i varetægtsfængsling.](../media/CustodianHoldDetails.PNG)

  - **Varetægtsfængslede steder**. Viser antallet og typen af datakilder (postkasser, websteder og Teams), der er knyttet til tilsynsførende og er en del af sagen.

    - Hver dataplacering viser status for venteposition. Mulige værdier for status for venteposition: **I venteposition**, **Ikke i venteposition** og **Igangværende**.

    - Hvis du ikke kan se en ventepositionsstatus for en datakilde, skal du kontrollere statussen for den frihedsberøvende venteposition, der er angivet under fanen **Venteposition** for sagen. Forældremyndigheden identificerer de specifikke datakilder, der er i venteposition.

## <a name="edit-a-custodian"></a>Rediger en tilsynsførende

Efterhånden som din sag skrider frem, kan du opdage, at der kan være yderligere datakilder, der er relevante for en bestemt tilsynsførende og sagen. I andre scenarier kan det være en god idé at fjerne visse datakilder, der er blevet gennemset og anses for ikke at være relevante.

Sådan opdaterer du de datakilder, der er knyttet til en tilsynsførende:

1. Gå til **eDiscovery > eDiscovery (Premium),** og åbn sagen.
  
2. Klik på fanen **Datakilder** .
  
3. Vælg en tilsynsførende på listen, og klik derefter på **Rediger** på pop op-siden.

    ![Rediger datakilder.](../media/EditCustodianDataSource.PNG)
  
4. Sådan tilføjer eller fjerner du den primære postkasse og OneDrive konto til den tilsynsførende:

    - Udvid tilsynsførende for at få vist de primære dataplaceringer, der tidligere er knyttet til tilsynsførende.

    - Klik på **Rediger** ud for **Postkasse** eller **OneDrive** for at tilføje den tilsynsførendes postkasse eller OneDrive placering.

    - Vælg **Ryd** ud for **Postkasse** eller **OneDrive** for at fjerne den tilsynsførendes postkasse eller OneDrive konto fra at blive tilknyttet som en dataplacering for denne tilsynsførende.

5. Hvis du vil tilføje eller fjerne andre postkasser, websteder, Teams eller Yammer grupper til en bestemt tilsynsførende, skal du klikke på **Rediger** ud for tjenesten for at tilføje en dataplacering.

   - **Exchange**: Bruges til at knytte andre postkasser til tilsynsførende. Skriv navnet eller aliasset (mindst tre tegn) for brugerpostkasser eller distributionsgrupper i søgefeltet. Vælg de postkasser, der skal tildeles til tilsynsførende, og klik derefter på **Tilføj**.

   - **SharePoint**: Bruges til at knytte SharePoint websteder til vogteren. Vælg et websted på listen, eller søg efter et websted ved at skrive en URL-adresse i søgefeltet. Vælg de websteder, der skal tildeles til tilsynsførende, og klik derefter på **Tilføj**.

   - **Teams**: Bruges til at tildele det Microsoft Teams, som vogteren i øjeblikket er medlem af. Vælg de teams, der skal tildeles til tilsynsførende, og klik derefter på **Tilføj**. Når du har tilføjet et team, identificerer og finder systemet automatisk det SharePoint websted og gruppepostkasse, der er knyttet til teamet, og tildeler dem til tilsynsførende.

   - **Yammer**: Bruges til at tildele de Yammer grupper, som vogteren i øjeblikket er medlem af. Vælg de grupper, der skal tildeles til tilsynsførende, og klik derefter på **Tilføj**. Når du har tilføjet et team, identificerer og finder systemet automatisk det SharePoint websted og gruppepostkasse, der er knyttet til gruppen, og tildeler dem til tilsynsførende.

   > [!NOTE]
   > Du kan bruge **Exchange** og **SharePoint** placeringsvælgere til at knytte alle postkasser eller websteder i din organisation, herunder teams eller Yammer grupper, som en tilsynsførende ikke er medlem af, til en tilsynsførende. Det gør du ved at tilføje både den postkasse og det websted, der er knyttet til hvert team eller Yammer gruppe.

6. Når du har redigeret dataplaceringerne for tilsynsførende, skal du klikke på **Næste** for at gå til siden **Indstillinger for venteposition** .  

7. Opdater indstillinger **for** bevarelse for vogteren på siden Indstillinger for venteposition.

## <a name="reindex-custodian-data"></a>Gendæd data om tilsynsførende

I de fleste eDiscovery-arbejdsprocesser til juridiske undersøgelser søges der i et undersæt af en tilsynsførendes data, når tilsynsførende er føjet til en juridisk sag. På grund af meget store filstørrelser eller mulig beskadigelse af data kan nogle elementer i de datakilder, der er knyttet til en tilsynsførende, blive delvist indekseret. Ved hjælp af den [avancerede indekseringsfunktion](indexing-custodian-data.md) i eDiscovery (Premium) kan de fleste delvist indekserede elementer afhjælpes automatisk ved at omindeksere disse elementer efter behov.

Når en tilsynsførende føjes til en sag, genindekseres de data, der er placeret i de datakilder, der er knyttet til vogteren, automatisk (af den avancerede indekseringsproces). Det betyder, at du kan lade dataene være på stedet i stedet for at skulle downloade og afhjælpe dem og derefter søge i dem offline). Men i løbet af livscyklussen for en juridisk sag kan nye datakilder være knyttet til en tilsynsførende. I dette tilfælde kan du omindeksere tilsynsførendes data ved at køre den avancerede indekseringsproces igen for at afhjælpe eventuelle delvist indekserede elementer og opdatere indekset for tilsynsførendes data.

Sådan udløser du den omindekseringsproces, der skal håndtere delvist indekserede elementer:

1. Gå til **eDiscovery > eDiscovery (Premium),** og åbn sagen.

2. Klik på fanen **Kilder** .

3. På siden **Tilsynsførende** skal du vælge en tilsynsførende, hvis data skal indekseres igen.

4. Klik på **Opdater indeks** på pop op-siden.

   Der vises en dialogboks, hvor der står, at indeksjobbet er blevet oprettet.

Omdexering af data fra tilsynsførende er en langvarig proces. det tilsvarende job, der er oprettet, kaldes **Genindeksering af tilsynsførende data**. Du kan spore statussen under fanen **Job** eller under fanen **Tilsynsførende** ved at overvåge statussen i kolonnen **Status for indeksering af job** .

Du kan finde flere oplysninger under:

- [Arbejd med behandlingsfejl](processing-data-for-case.md)

- [Administrer job](managing-jobs-ediscovery20.md)

## <a name="release-a-custodian-from-a-case"></a>Frigiv en varetægtsfængsling fra en sag

En varetægtsfængsling frigives i situationer, hvor en sag er afsluttet, hvor varetægtsfængslet ikke længere er forpligtet til at bevare indholdet i en sag, eller når forældremyndigheden anses for ikke længere at være relevant for sagen. 

Hvis du frigiver en varetægtsfængslet efter en meddelelse om frihedsberøvelse blev offentliggjort, vil en meddelelse blive sendt til varetægtsfængslet. Derudover fjernes alle ventepositioner, der er placeret på datakilder, som var knyttet til vogteren. Hvis tilsynsførende blev sat i *stille venteposition*, hvor de ikke blev udstedt nogen meddelelser om juridisk venteposition, sendes der ikke en meddelelse om frigivelse, men alle ventepositioner, der er placeret på datakilder, der var knyttet til den pågældende tilsynsførende, fjernes.

Sådan frigiver du en tilsynsførende:

1. Gå til **eDiscovery > eDiscovery (Premium),** og åbn sagen.

2. Klik på fanen **Kilder** .

3. På siden **Tilsynsførende** , og vælg derefter den tilsynsførende, der frigives fra sagen.

4. Klik på **Frigiv tilsynsførende** på pop op-siden.

   Der vises en advarselsside, der forklarer, at hvis en venteposition er placeret på en datakilde, der er knyttet til vogteren, fjernes ventepositionen, og at alle andre ventepositioner, der er knyttet til en anden eDiscovery-sag (Premium), stadig gælder. Det omfatter andre typer opbevarings- og opbevaringsfunktioner (f.eks. en politik for Microsoft 365 opbevaring).

5. Klik på **Ja** for at bekræfte, at du vil frigive tilsynsførende. 

    Status for denne bruger under fanen **Tilsynsførende** er angivet til **Frigivet** , og status for **venteposition** på pop op-siden ændres til **Falsk**.

> [!NOTE]
> En varetægtsfængsling kan være involveret samtidig i flere retssager. Når en tilsynsførende frigives fra en bestemt sag, påvirkes ventepositionerne og meddelelserne på tværs af andre sager ikke.
