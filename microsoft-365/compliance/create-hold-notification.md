---
title: Opret en meddelelse om juridisk venteposition
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
description: Brug kommunikationsværktøjet i en eDiscovery-sag (Premium) til at sende, indsamle og spore meddelelser om juridiske ventepositioner.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 21090274f385d6a3354852134764a1f53a311f10
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65094984"
---
# <a name="create-a-legal-hold-notice"></a>Opret en meddelelse om juridisk venteposition

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Ved hjælp af eDiscovery-kommunikation (Premium) kan organisationer administrere deres arbejdsproces omkring kommunikation med tilsynsførende. Gennem kommunikationsværktøjet kan juridiske teams systematisk sende, indsamle og spore meddelelser om juridiske ventepositioner. Den fleksible oprettelsesproces giver også teams mulighed for at tilpasse arbejdsprocessen for meddelelse om venteposition og indholdet i de meddelelser, der sendes til tilsynsførende.

![Kommunikationsside.](../media/CommunicationPage.PNG)

I artiklen beskrives trinnene i arbejdsprocessen for meddelelse om venteposition.

## <a name="step-1-specify-communication-details"></a>Trin 1: Angiv kommunikationsdetaljer

Det første trin er at angive de relevante oplysninger om meddelelser om juridiske ventepositioner eller andre oplysninger om varetægtsfængsling.

![Siden Navnkommunikation.](../media/NameCommunication.PNG)

1. På Microsoft Purview-overholdelsesportalen skal du gå til **eDiscovery > Avanceret** for at få vist listen over sager i din organisation.

2. Vælg en sag, klik på fanen **Kommunikation** , og klik derefter på **Ny kommunikation**.

3. På siden **Navngiv kommunikation** skal du angive følgende kommunikationsindstillinger.

    - **Navn**: Dette er navnet på kommunikationen.

    - **Udstedende officer**: På rullelisten vises de brugere i organisationen, der kan vælges som udstedende officer for kommunikationen. Hver kommunikation, der sendes til tilsynsførende, sendes på vegne af den valgte udstedende officer. Listen over brugere på rullelisten består af sagsmedlemmer og udstedende myndigheder i hele organisationen. Disse udstedende medarbejdere tilføjes af en eDiscovery-administrator og er tilgængelige i alle eDiscovery-sager (Premium) i din organisation. Du kan få flere oplysninger under [Administrer udstedende medarbejdere](advanced-ediscovery-issuing-officers.md).

    - **Vælg kommunikationsskabelon**: På rullelisten vises skabelonerne fra kommunikationsbiblioteket på siden med indstillinger for eDiscovery (Premium). Hvis du vælger en skabelon, vises den i **Definer portalindhold** som udgangspunkt for teksten i den meddelelse, du opretter. Hvis du ikke vælger en skabelon, skal du selv oprette meddelelsen fra bunden. Du kan få flere oplysninger om kommunikationsskabeloner under [Administrer skabeloner til tilsynsførende kommunikation](advanced-ediscovery-communications-library.md).

4. Klik på **Næste**.

## <a name="step-2-define-the-portal-content"></a>Trin 2: Definer portalindholdet

Derefter kan du oprette og tilføje indholdet af meddelelsen om venteposition. Angiv indholdet af ventepositionsmeddelelsen på siden **Definer portalindhold** i guiden **Opret kommunikation** . Dette indhold føjes automatisk til meddelelser om udstedelse, genudstedelse, påmindelse og eskalering. Derudover vises dette indhold på vogterens overholdelsesportal. Hvis du har valgt en skabelon fra biblioteket Kommunikation, vises den og giver et startpunkt for den meddelelse, du opretter.

![Portalindholdsside.](../media/PortalContent.PNG)

Sådan opretter du portalindholdet:

1. Skriv (eller klip og indsæt fra et andet dokument) meddelelsen om venteposition i tekstfeltet til portalindholdet. Hvis du har valgt en kommunikationsskabelon på den forrige guideside, vises skabelonen. Du kan redigere skabelonindholdet efter behov.

2. Indsæt fletvariabler i din meddelelse for at tilpasse meddelelsen og dele portalen til overholdelse af regler og standarder.

3. Klik på **Næste**.

  > [!TIP]
  > Hvis du vil vide mere om, hvordan du tilpasser indholdet og formatet af portalindholdet, skal du se [Brug kommunikationseditoren](using-communications-editor.md).

## <a name="step-3-set-the-required-notifications"></a>Trin 3: Angiv de påkrævede meddelelser

Når du har defineret indholdet af meddelelsen om venteposition, kan du konfigurere arbejdsprocesserne omkring afsendelse og administration af meddelelsesprocessen. Meddelelser er mails, der sendes for at give tilsynsførende besked og følge op på dem. Alle tilsynsførende, der føjes til kommunikationen, modtager den samme meddelelse.

Hvis du vil konfigurere og sende en meddelelse om venteposition, skal du inkludere meddelelser om udstedelse, genudgivelse og udgivelse.

### <a name="issuance-notification"></a>Meddelelse om udstedelse

Når kommunikationen er oprettet, **startes udstedelsesmeddelelsen** af den angivne udstedende officer. Udstedelsesmeddelelsen er den første meddelelse, der sendes til vogteren for at informere dem om deres bevarelsesforpligtelser.

Sådan opretter du en meddelelse om udstedelse:

1. Klik på **Rediger** i feltet **Udstedelse**.

2. Hvis det er nødvendigt, kan du føje flere sagsmedlemmer eller personale til felterne **Cc** og **Bcc** . Hvis du vil føje flere brugere til disse felter, skal du adskille mailadresser med semikolon.

3. Angiv **emnet** for meddelelsen (påkrævet).

4. Angiv det indhold eller yderligere instruktioner, du vil give til vogteren (påkrævet). Det portalindhold, du definerede i trin 2, føjes til slutningen af udstedelsesmeddelelsen.

5. Klik på **Gem**.

### <a name="re-issuance-notification"></a>Re-Issuance meddelelse

Efterhånden som sagen skrider frem, kan tilsynsførende blive bedt om at bevare yderligere eller færre data, end de tidligere blev bedt om. Når du har opdateret portalindholdet, sendes meddelelse om genudgivelse, og vogtere underrettes om eventuelle ændringer af deres bevarelsesforpligtelser.

Sådan opretter du en meddelelse om genudgivelse:

1. Klik på **Rediger** i feltet **Genudgang**.

2. Hvis det er nødvendigt, kan du føje flere sagsmedlemmer eller personale til felterne **Cc** og **Bcc** . Hvis du vil føje flere brugere til disse felter, skal du adskille mailadresser med semikolon.

3. Angiv **emnet** for meddelelsen (påkrævet).

4. Angiv det indhold eller yderligere instruktioner, du vil give til vogteren (påkrævet). Det portalindhold, du definerede i trin 2, føjes til slutningen af meddelelsen om genudgivelse.

5. Klik på **Gem**.

> [!NOTE]
> Hvis portalindholdet ændres (på siden **Definer portalindhold** i guiden **Rediger kommunikation** ), sendes udstedelsesmeddelelsen automatisk til alle tilsynsførende, der er tildelt meddelelsen. Når meddelelsen er sendt, bliver tilsynsførende bedt om at bekræfte deres meddelelse om venteposition igen. Hvis du har konfigureret arbejdsprocesser for påmindelse eller eskalering, startes disse også igen. Du kan få flere oplysninger om, hvilke andre hændelser for sagsstyring der udløser kommunikation, under [Hændelser, der udløser meddelelser](#events-that-trigger-notifications).

### <a name="release-notification"></a>Meddelelse om udgivelse

Når en sag er løst, eller hvis en tilsynsførende ikke længere er underlagt bevarelse af indhold, kan du frigive den tilsynsførende fra en sag. Hvis frihedsberøveren tidligere har fået en meddelelse om frigivelse, kan den bruges til at advare vogtere om, at de er blevet frigivet fra deres forpligtelse.

Sådan opretter du en udgivelsesmeddelelse:

1. Klik på **Rediger** i feltet **Udgivelse**.

2. Hvis det er nødvendigt, kan du føje flere sagsmedlemmer eller personale til felterne **Cc** og **Bcc** . Hvis du vil føje flere brugere til disse felter, skal du adskille mailadresser med semikolon.

3. Angiv **emnet** for meddelelsen (påkrævet).

4. Angiv det indhold eller yderligere instruktioner, du vil give til vogteren (påkrævet).

5. Klik på **Gem** , og gå til næste trin.

## <a name="optional-step-4-set-the-optional-notifications"></a>(Valgfrit) Trin 4: Angiv de valgfrie meddelelser

Du kan også forenkle arbejdsprocessen for opfølgning med tilsynsførende, der ikke svarer, ved at oprette og planlægge automatiserede påmindelses- og eskaleringsmeddelelser.

![Påmindelse/eskaleringsside.](../media/ReminderEscalations.PNG)

### <a name="reminders"></a>Påmindelser

Når du har sendt en meddelelse om venteposition, kan du følge op med tilsynsførende, der ikke svarer, ved at definere en arbejdsproces for påmindelse.

Sådan planlægger du påmindelser:

1. Klik på **Rediger** i feltet **Påmindelse**.

2. Aktivér arbejdsprocessen **Påmindelse** ved at aktivere til/ **fra-knappen Status** (påkrævet).

3. Angiv **påmindelsesintervallet (i dage)** (påkrævet). Dette er det antal dage, der skal ventes, før du sender de første påmindelser og meddelelser om opfølgningspåmindelser. Hvis du f.eks. angiver påmindelsesintervallet til syv dage, sendes den første påmindelse syv dage efter, at meddelelsen om venteposition oprindeligt blev udstedt. Alle efterfølgende påmindelser sendes også hver syvende dag.

4. Angiv **antallet af påmindelser** (påkrævet). Dette felt angiver, hvor mange påmindelser der skal sendes til tilsynsførende, der ikke svarer. Hvis du f.eks. angiver antallet af påmindelser til 3, modtager en tilsynsførende maksimalt tre påmindelser. Når en tilsynsførende har bekræftet meddelelsen om venteposition, sendes der ikke længere påmindelser til den pågældende bruger.

5. Angiv **emnet** for meddelelsen (påkrævet).

6. Angiv det indhold eller yderligere instruktioner, du vil give til vogteren (påkrævet). Det portalindhold, du definerede i trin 2, føjes til slutningen af påmindelsesmeddelelsen.

7. Klik på **Gem** , og gå til næste trin.

### <a name="escalations"></a>Eskaleringer

I nogle situationer har du muligvis brug for yderligere måder at følge op på med tilsynsførende, der ikke svarer. Hvis en tilsynsførende ikke anerkender en meddelelse om venteposition efter at have modtaget det angivne antal påmindelser, kan det juridiske team angive en arbejdsproces for automatisk at sende en eskaleringsmeddelelse til tilsynsførende og deres leder.

Sådan planlægges eskaleringer:

1. Klik på **Rediger** i feltet **Eskalering**.

2. Aktivér arbejdsprocessen **Eskalering** ved at aktivere til/fra-knappen **Status** .

3. Angiv **eskaleringsintervallet (i dage)** (påkrævet).

4. Angiv **antallet af eskaleringer** (påkrævet). Dette felt angiver, hvor mange eskaleringer der skal sendes til tilsynsførende, der ikke svarer. Hvis du f.eks. angiver antallet af eskaleringer til 3, sendes der en eskaleringsmeddelelse til tilsynsførende og deres leder maksimalt tre gange. Når en tilsynsførende har bekræftet meddelelsen om venteposition, sendes der ikke længere eskaleringer.

5. Angiv **emnet** for meddelelsen (påkrævet).

6. Angiv det indhold eller yderligere instruktioner, du vil give til vogteren (påkrævet). Det portalindhold, du definerede i trin 2, føjes til slutningen af eskaleringsmeddelelsen.

7. Klik på **Gem** , og gå til næste trin.

## <a name="step-5-assign-custodians-to-receive-notifications"></a>Trin 5: Tildel vogtere til at modtage meddelelser

Når du har færdiggjort indholdet til meddelelser, skal du vælge de tilsynsførende, som du vil sende meddelelser til.

![Vælg siden Tilsynsførende.](../media/SelectCustodians.PNG)

Sådan tilføjer du tilsynsførende:

1. Tildel tilsynsførende til kommunikationen ved at klikke på afkrydsningsfeltet ud for deres navn.

    Når kommunikationen er oprettet, anvendes meddelelsesarbejdsprocessen automatisk for de valgte tilsynsførende.

2. Klik på **Næste** for at gennemse kommunikationsindstillinger og -detaljer.

> [!NOTE]
> Du kan kun tilføje tilsynsførende, der er blevet føjet til sagen, og som ikke er blevet sendt en anden meddelelse i sagen.

## <a name="step-6-review-settings"></a>Trin 6: Gennemse indstillinger

Når du har gennemset indstillingerne og klikket på **Send** for at fuldføre kommunikationen, starter systemet automatisk kommunikationsarbejdsprocessen ved at sende meddelelse om udstedelse.

## <a name="events-that-trigger-notifications"></a>Hændelser, der udløser meddelelser

I følgende tabel beskrives hændelser i sagshåndteringsprocessen, der udløses, når de forskellige typer meddelelser sendes til tilsynsførende.

|Kommunikationstype|Udløse |
|:---------|:---------|
|Meddelelser om udstedelse|Den indledende oprettelse af meddelelsen. Du kan også sende en meddelelse om venteposition manuelt. |
|Meddelelser om udstedelse|Opdaterer portalindholdet på siden **Definer portalindhold** i guiden **Rediger kommunikation** .|
|Udgivelsesmeddelelser|Varetægtsfængslet er løsladt fra sagen.|
|Påmindelser|Intervallet og antallet af påmindelser, der er konfigureret for påmindelsen.|
|Eskaleringer|Intervallet og antallet af påmindelser, der er konfigureret for eskaleringen.|
|||
