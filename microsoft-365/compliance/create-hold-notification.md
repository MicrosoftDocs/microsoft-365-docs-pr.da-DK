---
title: Opret en meddelelse om retslig venteposition
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
description: Brug kommunikationsværktøjet i en Advanced eDiscovery til at sende, indsamle og spore meddelelser om retslig venteposition.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 5c0bda35ffe2547e1c30b4bbf0a6c7d0d0563b7b
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63588910"
---
# <a name="create-a-legal-hold-notice"></a>Opret en meddelelse om retslig venteposition

Ved Advanced eDiscovery at hjælpe med at kommunikere, kan organisationer administrere deres arbejdsgang omkring kommunikation med medarbejdere. Via kommunikationsværktøjet kan juridiske teams systematisk sende, indsamle og spore meddelelser om retslig venteposition. Den fleksible oprettelsesproces gør det også muligt for teams at tilpasse arbejdsprocessen for meddelelser om venteposition og indholdet i meddelelserne, der sendes til hjælpere.

![Kommunikationsside.](../media/CommunicationPage.PNG)

I artiklen beskrives trinnene i arbejdsprocessen til besked om venteposition.

## <a name="step-1-specify-communication-details"></a>Trin 1: Angiv kommunikationsdetaljer

Det første trin er at angive de relevante oplysninger for meddelelser om retslig venteposition eller anden kommunikation, der er egnet til retslig opbevaring.

![Siden Name Communication.](../media/NameCommunication.PNG)

1. I Microsoft 365 Overholdelsescenter skal du gå **til eDiscovery > Avanceret** for at få vist listen over sager i din organisation.

2. Vælg en sag, klik på **fanen Kommunikation** , og klik derefter på **Ny kommunikation**.

3. På siden **Navn skal** du angive følgende kommunikationsindstillinger.

    - **Navn**: Dette er navnet på kommunikationen.

    - **Udsteder officer**: På rullelisten vises brugere i organisationen, der kan vælges som udstederofficer for kommunikationen. Hver meddelelse, der sendes til vagtchefer, sendes på vegne af den valgte udstederofficer. Listen over brugere i rullemenuen består af medlemmerne af sagen og den organisation, der udsteder medarbejdere. Disse udstedende medarbejdere tilføjes af en eDiscovery-administrator og er tilgængelige i alle Advanced eDiscovery i din organisation. Få mere at vide under [Administrer udstedelse af medarbejdere](advanced-ediscovery-issuing-officers.md).

    - **Vælg kommunikationsskabelon**: Rullelisten viser skabelonerne fra biblioteket Kommunikation på siden Advanced eDiscovery kommunikationsindstillinger. Hvis du vælger en skabelon, vises den på **Definer portalindhold** som et udgangspunkt for teksten i den meddelelse, du opretter. Hvis du ikke vælger en skabelon, er du nødt til selv at oprette meddelelsen fra bunden. Hvis du vil have mere at vide om kommunikationsskabeloner, skal [du se Administrere relevante kommunikationsskabeloner](advanced-ediscovery-communications-library.md).

4. Klik på **Næste**.

## <a name="step-2-define-the-portal-content"></a>Trin 2: Definer portalindholdet

Derefter kan du oprette og tilføje indholdet af ventepositionsmeddelelsen. På siden **Definer portalindhold** i guiden **Opret kommunikation** skal du angive indholdet af meddelelsen om venteposition. Dette indhold føjes automatisk til meddelelser om udstedelse, genudstedelse, påmindelse og eskalering. Desuden vises dette indhold hos den overvågende brugers overholdelsesportal. Hvis du har valgt en skabelon fra kommunikationsbiblioteket, vises den og giver et udgangspunkt for den meddelelse, du opretter.

![Siden Portalindhold.](../media/PortalContent.PNG)

Sådan opretter du portalindholdet:

1. Skriv (eller klip og indsæt fra et andet dokument) din meddelelse om venteposition i tekstfeltet til portalens indhold. Hvis du har valgt en kommunikationsskabelon på den forrige side i guiden, vises skabelonen. Du kan redigere skabelonens indhold efter behov.

2. Indsæt flettevariabler i din meddelelse for at tilpasse meddelelsen og dele portalen til overholdelse af regler og standarder for overholdelse af regler og standarder.

3. Klik på **Næste**.

  > [!TIP]
  > Hvis du vil have mere at vide om, hvordan du kan tilpasse indholdet og formatet af portalindholdet, skal [du se Brug af Kommunikationseditor](using-communications-editor.md).

## <a name="step-3-set-the-required-notifications"></a>Trin 3: Indstil de nødvendige meddelelser

Når du har defineret indholdet af meddelelsen om venteposition, kan du konfigurere arbejdsgangene omkring afsendelse og administration af meddelelsesprocessen. Meddelelser er mails, der sendes til at underrette og følge op med  vejledningen. Alle hjælpere, der føjes til meddelelsen, modtager den samme meddelelse.

For at konfigurere og sende en meddelelse om venteposition skal du inkludere meddelelser om udstedelse, genudstedelse og udgivelse.

### <a name="issuance-notification"></a>Meddelelse om udstedelse

Når kommunikationen er oprettet, **startes Udstedelsesmeddelelsen** af den angivne udstedelsesmedarbejder. Udsendelsesmeddelelsen er den første meddelelse, der sendes til den, der skal underrettes, for at informere vedkommende om sine bevaringsforpligtelser.

Sådan oprettes en meddelelse om udstedelse:

1. I feltet **Udstedelse skal** du klikke på **Rediger**.

2. Hvis det er nødvendigt, kan du føje yderligere sagsmedlemmer eller medarbejdere **til felterne Cc** **og Bcc** . Hvis du vil føje flere brugere til disse felter, skal du adskille mailadresserne med et semikolon.

3. Angiv **Emne** for meddelelsen (påkrævet).

4. Angiv det indhold eller de yderligere instruktioner, du vil give til den, der skal vises (påkrævet). Det portalindhold, du definerede i trin 2, føjes til slutningen af udstedelsesmeddelelsen.

5. Klik på **Gem**.

### <a name="re-issuance-notification"></a>Re-Issuance meddelelse

I løbet af sagens forløb kan det være nødvendigt at give besked om, at der skal bevares yderligere eller færre data, end det tidligere blev beskrevet. Når du har opdateret portalens indhold, sendes der en meddelelse om genanholdelse, og du får besked om ændringer af deres bevaringsforpligtelser.

Sådan oprettes en meddelelse om genudgivelse:

1. Klik **på Rediger i** feltet **Gensue**.

2. Hvis det er nødvendigt, kan du føje yderligere sagsmedlemmer eller medarbejdere **til felterne Cc** **og Bcc** . Hvis du vil føje flere brugere til disse felter, skal du adskille mailadresserne med et semikolon.

3. Angiv **Emne** for meddelelsen (påkrævet).

4. Angiv det indhold eller de yderligere instruktioner, du vil give til den, der skal vises (påkrævet). Det portalindhold, du definerede i trin 2, føjes til slutningen af genmeddelelsen.

5. Klik på **Gem**.

> [!NOTE]
> Hvis portalindholdet ændres (på siden **Definer portalindhold** i guiden Rediger  kommunikation), sendes der automatisk en meddelelse om genudstedelse til alle medarbejdere, der er tildelt meddelelsen. Når meddelelsen er sendt, bliver hjælpere blive bedt om at bekræfte deres meddelelse om venteposition igen. Hvis du har konfigureret påmindelses- eller eskaleringsarbejdsprocesser, starter disse også igen. Du kan finde flere oplysninger om, hvilke andre hændelser i sagsstyring, der udløser kommunikation, [under Hændelser, der udløser meddelelser](#events-that-trigger-notifications).

### <a name="release-notification"></a>Meddelelse om udgivelse

Når en sag er løst, eller hvis en øvermand ikke længere er underlagt opbevaring af indhold, kan du frigive den, der skal have hjælp, fra en sag. Hvis vagten tidligere blev udstedt en meddelelse om venteposition, kan meddelelse om frigivelse bruges til at give besked om, at han eller hun er blevet frigjort fra sin forpligtelse.

Sådan opretter du en udgivelsesmeddelelse:

1. Klik på **Rediger** i feltet **Udgivelse**.

2. Hvis det er nødvendigt, kan du føje yderligere sagsmedlemmer eller medarbejdere **til felterne Cc** **og Bcc** . Hvis du vil føje flere brugere til disse felter, skal du adskille mailadresserne med et semikolon.

3. Angiv **Emne** for meddelelsen (påkrævet).

4. Angiv det indhold eller de yderligere instruktioner, du vil give til den, der skal vises (påkrævet).

5. Klik **på Gem** , og gå til næste trin.

## <a name="optional-step-4-set-the-optional-notifications"></a>(Valgfrit) Trin 4: Indstil de valgfrie meddelelser

Du kan også forenkle arbejdsprocessen til at følge op med svarer ikke-planlæggere ved at oprette og planlægge automatiserede påmindelses- og eskaleringsmeddelelser.

![Siden Påmindelse/eskalering.](../media/ReminderEscalations.PNG)

### <a name="reminders"></a>Påmindelser

Når du har sendt en meddelelse om venteposition, kan du følge op med svarer for at holde op med at reagere på dem ved at definere en påmindelsesarbejdsproces.

Sådan planlægger du påmindelser:

1. Klik på **Rediger** i feltet **Påmindelse**.

2. Aktivér **arbejdsprocessen** Påmindelse ved at slå **status til** /fra-knappen (påkrævet).

3. Angiv Et **Påmindelsesinterval (i dage)** (påkrævet). Dette er antallet af dage, der skal ventes, før du sender de første påmindelsesmeddelelser og opfølgende påmindelser. Hvis du f.eks. angiver påmindelsesintervallet til syv dage, sendes den første påmindelse syv dage efter, at meddelelsen om venteposition oprindeligt blev udstedt. Alle efterfølgende påmindelser sendes også hver syv dage.

4. Angiv Antallet **af påmindelser** (påkrævet). Dette felt angiver, hvor mange påmindelser der skal sendes til ledende brugere, der ikke svarer. Hvis du f.eks. angiver antallet af påmindelser til 3, så modtager en modtager maksimalt tre påmindelser. Når en vagter anerkender meddelelsen om venteposition, sendes der ikke længere påmindelser til den pågældende bruger.

5. Angiv **Emne** for meddelelsen (påkrævet).

6. Angiv det indhold eller de yderligere instruktioner, du vil give til den, der skal vises (påkrævet). Det portalindhold, du definerede i trin 2, føjes til slutningen af påmindelsesmeddelelsen.

7. Klik **på Gem** , og gå til næste trin.

### <a name="escalations"></a>Eskaleringer

I nogle situationer kan det være nødvendigt med yderligere måder at følge op med manglende respons på. Hvis en værge ikke anerkender en meddelelse om venteposition efter at have modtaget det angivne antal påmindelser, kan det juridiske team angive en arbejdsproces for automatisk at sende en eskaleringsmeddelelse til den person, der er ansvarlig for meddelelsen, og dennes leder.

Sådan planlægger du eskaleringer:

1. Klik på **Rediger i** feltet **Eskalering**.

2. Aktivér **eskaleringsarbejdsprocessen** ved at slå **status til** /fra-knappen til.

3. Angiv **eskaleringsintervallet (i dage)** (påkrævet).

4. Angiv Antallet **af eskaleringer** (påkrævet). Dette felt angiver, hvor mange eskaleringer der skal sendes for ikke at reagere på brugere, der ikke reagerer. Hvis du f.eks. angiver antallet af eskaleringer til 3, sendes der en eskaleringsmeddelelse til vagtchefen og deres leder maksimalt tre gange. Når en vagter anerkender meddelelsen om venteposition, sendes eskaleringerne ikke længere.

5. Angiv **Emne** for meddelelsen (påkrævet).

6. Angiv det indhold eller de yderligere instruktioner, du vil give til den, der skal vises (påkrævet). Det portalindhold, du definerede i trin 2, føjes til slutningen af eskaleringsmeddelelsen.

7. Klik **på Gem** , og gå til næste trin.

## <a name="step-5-assign-custodians-to-receive-notifications"></a>Trin 5: Tildel personer, der skal modtage meddelelser, til at modtage meddelelser

Når du har færdiggjort indholdet til meddelelser, skal du vælge de y-y-væsker, du vil sende meddelelser til.

![Vælg Y-1-1-side.](../media/SelectCustodians.PNG)

Sådan tilføjer du y-førere:

1. Tildel kontrolere til kommunikationen ved at klikke på afkrydsningsfeltet ud for deres navn.

    Når kommunikationen er oprettet, anvendes meddelelsesarbejdsprocessen automatisk på de valgte hjælpere.

2. Klik **på Næste** for at gennemgå kommunikationsindstillingerne og detaljerne.

> [!NOTE]
> Du kan kun tilføje brugere, der skal være førere, som er blevet føjet til sagen, og ikke har fået tilsendt endnu en meddelelse i sagen.

## <a name="step-6-review-settings"></a>Trin 6: Gennemse indstillinger

Når du har gennemset indstillingerne og **klikket på Send** for at fuldføre kommunikationen, starter systemet automatisk kommunikationsarbejdsprocessen ved at sende udsendelsesmeddelelsen.

## <a name="events-that-trigger-notifications"></a>Hændelser, der udløser meddelelser

I følgende tabel beskrives hændelser i processen for sagsstyring, der udløser, hvornår de forskellige typer meddelelser sendes til y-4-4-42016-

|Kommunikationstype|Udløser |
|:---------|:---------|
|Udstedelsesmeddelelse|Den første oprettelse af meddelelsen. Du kan også sende en meddelelse om venteposition manuelt igen. |
|Meddelelser om genangivelse|Opdatering af portalindholdet på siden **Definer portalindhold** i **guiden** Rediger kommunikation.|
|Meddelelser om frigivelse|Den anden, der skal arbejde på sagen, frigives fra sagen.|
|Påmindelser|Det interval og antal påmindelser, der er konfigureret for påmindelsen.|
|Eskaleringer|Det interval og antal påmindelser, der er konfigureret for eskalering.|
|||
