---
title: Brug netværksupload til at importere din organisations PST-filer
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MED150
- MET150
ms.assetid: 103f940c-0468-4e1a-b527-cc8ad13a5ea6
description: 'Administratorer: Lær, hvordan du bruger netværksupload til masseimport af flere PST-filer til brugerpostkasser i Microsoft 365.'
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: b189be60efb48af33d26ea459bbee77878d4a93c
ms.sourcegitcommit: 36a19d80fe3f053df0fec398a7ff2dfc777f9730
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/30/2021
ms.locfileid: "63589567"
---
# <a name="use-network-upload-to-import-your-organizations-pst-files-to-microsoft-365"></a>Brug netværksupload til at importere din organisations PST-filer Microsoft 365

> [!NOTE]
> Denne artikel gælder for administratorer. Forsøger du at importere PST-filer til din egen postkasse? Se [Importere mail, kontakter og kalender fra en Outlook .pst-fil](https://go.microsoft.com/fwlink/p/?LinkID=785075)
  
Her er de trinvise instruktioner, der kræves for at bruge netværksupload til masseimport af flere PST-filer Microsoft 365 postkasser. Hvis du har ofte stillede spørgsmål om brug af netværksupload til masseimport af PST-filer til Microsoft 365-postkasser, skal du se Ofte stillede spørgsmål om brug af netværksupload til [at importere PST-filer](./faqimporting-pst-files-to-office-365.yml#using-network-upload-to-import-pst-files).
  
[Trin 1: Kopiér SAS URL-adressen, og download AzCopy](#step-1-copy-the-sas-url-and-download-azcopy)

[Trin 2: Upload PST-filer til at Microsoft 365](#step-2-upload-your-pst-files-to-microsoft-365)

[(Valgfrit) Trin 3: Få vist en liste over de PST-filer, der er uploadet](#optional-step-3-view-a-list-of-the-pst-files-uploaded-to-microsoft-365)

[Trin 4: Opret tilknytningsfilen til PST-import](#step-4-create-the-pst-import-mapping-file)

[Trin 5: Opret et PST-importjob](#step-5-create-a-pst-import-job)

[Trin 6: Filtrer data, og start PST-importjobbet](#step-6-filter-data-and-start-the-pst-import-job)

Du skal kun udføre trin 1 én gang for at importere PST-filer Microsoft 365 postkasser. Når du har fulgt disse trin, skal du følge trin 2 til 6, hver gang du vil uploade og importere en batch af PST-filer.

## <a name="before-you-import-pst-files"></a>Før du importerer PST-filer
  
- Du skal have tildelt rollen Postkasse Import Eksport i Exchange Online for at oprette importjob i Microsoft 365 Overholdelsescenter og importere PST-filer til brugerpostkasser. Som standard er denne rolle ikke tildelt nogen rollegruppe i Exchange Online. Du kan føje rollen Postkasse Import Eksport til rollegruppen Organisationsadministration. Eller du kan oprette en rollegruppe, tildele rollen Postkasse Import Eksport og derefter tilføje dig selv som medlem. Du kan finde flere oplysninger i afsnittene "Føj en rolle til en rollegruppe" eller "Opret en rollegruppe" i [Administrer rollegrupper](/Exchange/permissions-exo/role-groups).

    Ud over rollen Postkasse Import Eksport skal du også have tildelt rollen Postmodtagere i Exchange Online. Som standard er denne rolle tildelt rollegrupperne Organisationsadministration og Modtageradministration i Exchange Online.

    > [!TIP]
    > Overvej at oprette en ny rollegruppe i Exchange Online, der specifikt er beregnet til import af PST-filer. For det mindste niveau af rettigheder, der kræves for at importere PST-filer, skal du tildele rollerne Postkasse Import Eksport og Postmodtagere til den nye rollegruppe og derefter tilføje medlemmer.
  
- Den eneste understøttede metode til at importere PST-Microsoft 365-filer er at bruge værktøjet AzCopy som beskrevet i denne artikel. Du kan ikke bruge Stifinder Azure Storage at uploade PST-filer direkte til Azure Storage område.

- Store PST-filer kan påvirke ydeevnen for PST-importprocessen. Vi anbefaler derfor, at hver enkelt PST-fil, du overfører til Azure Storage i trin 2, ikke må være større end 20 GB.

- Denne fremgangsmåde indebærer kopiering og lagring af en kopi af en URL-adresse, der indeholder en adgangsnøgle. Disse oplysninger bruges i trin 2 til at uploade dine PST-filer, og i trin 3, hvis du vil have vist en liste over PST-filer, der er uploadet til Microsoft 365. Sørg for at beskytte denne URL-adresse på samme måde, som hvis du beskytter adgangskoder eller andre sikkerhedsrelaterede oplysninger. Du kan f.eks. gemme den i et adgangskodebeskyttet dokument Microsoft Word eller på et krypteret USB-drev. Se afsnittet [Flere oplysninger for](#more-information) at få et eksempel på denne kombinerede URL-adresse og nøgle.

- Du kan importere PST-filer til en inaktiv postkasse i Microsoft 365. Det gør du ved at angive GUID'et for den inaktive postkasse i  `Mailbox` parameteren i PST-importtilknytningsfilen. Se Trin 4 på fanen Instruktioner **i** denne artikel for at få flere oplysninger.

- I en Exchange-hybridinstallation kan du importere PST-filer til en skybaseret arkivpostkasse for en bruger, hvis primære postkasse er lokal. Det gør du ved at gøre følgende i PST-importtilknytningsfilen:

  - Angiv mailadressen til brugerens lokale postkasse i  `Mailbox` parameteren.

  - Angiv værdien **SAND** i  `IsArchive` parameteren.

    Se [Trin 4 for at](#step-4-create-the-pst-import-mapping-file) få flere oplysninger.

- Når PST-filer er importeret, er indstillingen for opbevaring af postkassen aktiveret i ubestemt tid. Det betyder, at den opbevaringspolitik, der er tildelt til postkassen, ikke behandles, før du deaktiverer opbevaringspositionen eller angiver en dato for at deaktivere ventepositionen. Hvorfor gør vi dette? Hvis meddelelser, der importeres til en postkasse, er gamle, kan de blive slettet permanent (slettet), fordi deres opbevaringsperiode er udløbet baseret på de opbevaringsindstillinger, der er konfigureret for postkassen. Når du sætter postkassen i venteposition, får postkassens ejer tid til at administrere disse nyligt importerede meddelelser, eller der gives tid til at ændre opbevaringsindstillingerne for postkassen. Se afsnittet [Flere oplysninger i](#more-information) denne artikel for at få forslag til administration af opbevaringspositionen.

- Som standard er den maksimale meddelelsesstørrelse, der kan modtages af Microsoft 365 postkasse, 35 MB. Det skyldes, at standardværdien for  *egenskaben MaxReceiveSize*  for en postkasse er angivet til 35 MB. Men grænsen for den maksimale størrelse for modtagelse af meddelelser i Microsoft 365 er 150 MB. Så hvis du importerer en PST-fil, der indeholder et element, der er større end 35 MB, ændrer tjenesten Microsoft 365-import automatisk værdien af *egenskaben MaxReceiveSize* på målpostkassen til 150 MB. Dette giver mulighed for at importere meddelelser på op til 150 MB til brugerpostkasser.

    > [!TIP]
    > For at identificere meddelelsens modtagelsesstørrelse for en postkasse kan du køre denne kommando i Exchange Online PowerShell: `Get-Mailbox <user mailbox> | FL MaxReceiveSize`.

- Hvis du vil have en detaljeret oversigt over PST-importprocessen, skal du [se afsnittet Sådan fungerer importprocessen](#how-the-import-process-works) i denne artikel.

## <a name="step-1-copy-the-sas-url-and-download-azcopy"></a>Trin 1: Kopiér SAS URL-adressen, og download AzCopy

Det første trin er at downloade AzCopy-værktøjet, som er det værktøj, du kører i trin 2, til at uploade PST-filer til Microsoft 365. Du kopierer også SAS URL-adressen for din organisation. Denne URL-adresse er en kombination af netværkets URL-adresse til Azure Storage placering i Microsoft-skyen for din organisation og en SAS-nøgle (Shared Access Signature). Denne nøgle giver dig de nødvendige tilladelser til at uploade PST-filer til en Azure Storage placering. Sørg for at beskytte SAS URL-adressen. Det er entydigt for din organisation og vil blive brugt i trin 2.

> [!IMPORTANT]
> Hvis du vil importere PST-filer ved hjælp af metoden til netværksupload og kommandosyntaksen, som er dokumenteret i denne artikel, skal du bruge den version af AzCopy, der kan downloades i trin 6b, i følgende procedure. Du kan også downloade den samme version af AzCopy [her](https://aka.ms/downloadazcopylatest). Brug af en anden version af AzCopy understøttes ikke.
  
1. Gå til <https://compliance.microsoft.com> og log på med legitimationsoplysningerne til en administratorkonto i organisationen.

2. Klik på Importér Microsoft 365 Overholdelsescenter venstre  \> **rude.**

    > [!NOTE]
    > Du skal have tildelt de relevante tilladelser for at få adgang til **siden Import** i Microsoft 365 Overholdelsescenter. Du kan **finde flere oplysninger i** afsnittet Inden du går i gang. 

3. Klik på **Tilføj** ikon under ![fanen Importér.](../media/ITPro-EAC-AddIcon.gif) **Nyt importjob**.

    Guiden Importér job vises.

4. Skriv et navn til PST-importjobbet, og klik derefter på **Næste**. Brug små bogstaver, tal, bindestreger og understregningstegn. Du må ikke bruge store bogstaver eller medtage mellemrum i navnet.

5. På siden **Vil du overføre eller sende data? skal du klikke** på **Upload dine data og** derefter klikke på **Næste**.

    ![Klik Upload dine data for at oprette et netværksoverførselsimportjob.](../media/e59f9dc3-ccde-44ff-ac38-c4e39d76ae85.png)
  
6. Gør følgende to ting på siden **Importér** data:

    ![Kopiér SAS-URL-adressen, og download værktøjet AzCopy på siden Importér data.](../media/74411014-ec4b-4e25-9065-404c934cce17.png)
  
    1. I trin 2 skal du klikke **på Vis netværksoverførsel SAS URL**. Når SAS URL-adressen vises, skal du  klikke på Kopiér til Udklipsholder og derefter indsætte den og gemme den i en fil, så du kan få adgang til den senere.

    2. I trin 3 skal du **klikke på Download Azure AzCopy** for at hente værktøjet AzCopy til din lokale computer. Denne version af AzCopy er blot en eksekverbar fil, så der er intet at installere.

   > [!NOTE]
   > Du kan lade siden **Importér data** være åben (i tilfælde af at du skal kopiere SAS URL-adressen igen) eller klikke på **Annuller** for at lukke den.

## <a name="step-2-upload-your-pst-files-to-microsoft-365"></a>Trin 2: Upload PST-filer til at Microsoft 365

Nu er du klar til at bruge værktøjet AzCopy til at uploade PST-filer til Microsoft 365. Dette værktøj uploader og gemmer PST-filer på en Microsoft-leveret Azure Storage i Microsoft-skyen. Som beskrevet tidligere er den Azure Storage, du overfører dine PST-filer til, placeret i det samme regionale Microsoft-datacenter, hvor din organisation er placeret. For at fuldføre dette trin skal PST-filerne være placeret i et filshare eller filserver i din organisation eller på en Azure Storage placering, der administreres af din organisation. Pst.-lagerplaceringen kaldes kildeplaceringen i denne procedure. Hver gang du kører værktøjet AzCopy, kan du angive en anden kildeplacering.

> [!NOTE]
> Som tidligere nævnt må hver PST-fil, som du overfører Azure Storage placering, ikke være større end 20 GB. PST-filer, der er større end 20 GB, kan påvirke ydeevnen af PST-importprocessen, som du starter i trin 6. Desuden skal hver PST-fil have et entydigt navn.

1. Åbn en kommandoprompt på din lokale computer.

2. Gå til den mappe, hvor du hentede azcopy.exe i trin 1.

3. Kør følgende kommando for at uploade PST-filerne til Microsoft 365.

    ```powershell
    azcopy.exe copy "<Source location of PST files>" "<SAS URL>"
    ```

    > [!IMPORTANT]
    > Du kan angive en mappe eller Azure Storage placering som kildeplaceringen i den forrige kommando. Du kan ikke angive en individuel PST-fil. Alle PST-filer på kildeplaceringen uploades.

    I følgende tabel beskrives de azcopy.exe og de påkrævede værdier. De oplysninger, du fik i det forrige trin, bruges i værdierne for disse felter.

    | Felt | Beskrivelse |
    |:-----|:-----|
    | Kilde |Det første felt angiver den kildemappe i din organisation, der indeholder de PST-filer, der skal uploades Microsoft 365. Alternativt kan du angive en placering Azure Storage som kildeplaceringen for de PST-filer, der skal uploades. <br/> Sørg for at omgive værdien af dette felt med dobbelte anførselstegn (" ").  <br/> <br/>**Eksempler**: <br/>`"\\FILESERVER01\PSTs"` <br/> Eller  <br/>`"https://storageaccountid.blob.core.windows.net/PSTs?sp=racwdl&st=2021-09-21T07:25:53Z&se=2021-09-21T15:25:53Z&sv=2020-08-04&sr=c&sig=xxxxxx"`|  
    | Destination |Angiver DEN SAS URL-adresse, du fik i trin 1.  <br/> Sørg for at omgive værdien af denne parameter med dobbelte anførselstegn (" ").<br/><br/>**Bemærk!** Hvis du bruger SAS URL-adressen i en script- eller batchfil, skal du holde øje med bestemte tegn, der skal escapes. Du skal f.eks. ændre `%` til `%%` og ændre `&` til `^&`.<br/><br/>**Tip:** (Valgfrit) Du kan angive en undermappe på den placering, Azure Storage PST-filerne skal uploades til. Det gør du ved at tilføje en undermappeplacering (efter "ingestiondata") i SAS-URL-adressen. Det første eksempel angiver ikke en undermappe. Det betyder, at PST'er overføres til roden (kaldet *ingestiondata*) for Azure Storage placering. Det andet eksempel overfører PST-filerne til en undermappe (kaldet *PSTFiles*) i roden af Azure Storage placering.  <br/><br/>**Eksempler**: <br/> `"https://3c3e5952a2764023ad14984.blob.core.windows.net/ingestiondata?sv=2012-02-12&amp;se=9999-12-31T23%3A59%3A59Z&amp;sr=c&amp;si=IngestionSasForAzCopy201601121920498117&amp;sig=Vt5S4hVzlzMcBkuH8bH711atBffdrOS72TlV1mNdORg%3D"` <br/> Eller  <br/>  `"https://3c3e5952a2764023ad14984.blob.core.windows.net/ingestiondata/PSTFiles?sv=2012-02-12&amp;se=9999-12-31T23%3A59%3A59Z&amp;sr=c&amp;si=IngestionSasForAzCopy201601121920498117&amp;sig=Vt5S4hVzlzMcBkuH8bH711atBffdrOS72TlV1mNdORg%3D"` <br/> |
    | `--recursive` |Dette valgfrie flag angiver rekursiv tilstand, så værktøjet AzCopy kopierer PSTs-filer, der er placeret i undermapper i kildemappen, der er angivet af kildefeltet. Standardværdien for dette flag er `true`. <br/>**Bemærk!** Hvis du medtager dette flag, har PST-filer i undermapper et andet stinavn på placeringen Azure Storage når de er uploadet. Du skal angive det nøjagtige filnavn i CSV-filen, som du opretter i trin 4.|
    | `--s2s-preserve-access-tier` | Dette valgfrie flag er kun påkrævet, når kildeplaceringen er en overordnet v2-placering, Azure Storage der understøtter adgangsniveauer. I scenariet PST-import er det ikke nødvendigt at bevare adgangsniveau, når du kopierer PST-filer fra din Azure Storage-konto til den Microsoft-angivne Azure Storage placering. I dette tilfælde kan du medtage dette flag og bruge en værdi på `false`. Du behøver ikke at bruge dette flag, når du kopierer PST-filer fra en klassisk Azure Storage-konto, hvilket ikke understøtter adgangsniveauer.|
   |||

Du kan finde flere oplysninger **azcopy.exe kommandoen Kopiér** eller Kopiér under [azcopykopi](/azure/storage/common/storage-ref-azcopy-copy).

Her er eksempler på syntaksen for værktøjet AzCopy, der bruger faktiske værdier for hver parameter.

### <a name="example-1"></a>Eksempel 1

Dette er et eksempel på en kildemappe, der er placeret på filserveren eller den lokale computer.

```powershell
azcopy.exe copy "\\FILESERVER1\PSTs" "https://3c3e5952a2764023ad14984.blob.core.windows.net/ingestiondata?sv=2012-02-12&amp;se=9999-12-31T23%3A59%3A59Z&amp;sr=c&amp;si=IngestionSasForAzCopy201601121920498117&amp;sig=Vt5S4hVzlzMcBkuH8bH711atBffdrOS72TlV1mNdORg%3D"
```

### <a name="example-2"></a>Eksempel 2

Dette er et eksempel for en kildemappe, der er placeret i en klassisk Azure Storage-konto med undermapper.

```powershell
azcopy.exe copy "https://storageaccountid.blob.core.windows.net/PSTs?sp=racwdl&st=2021-09-21T07:25:53Z&se=2021-09-21T15:25:53Z&sv=2020-08-04&sr=c&sig=xxxxxx" "https://3c3e5952a2764023ad14984.blob.core.windows.net/ingestiondata?sv=2012-02-12&amp;se=9999-12-31T23%3A59%3A59Z&amp;sr=c&amp;si=IngestionSasForAzCopy201601121920498117&amp;sig=Vt5S4hVzlzMcBkuH8bH711atBffdrOS72TlV1mNdORg%3D" --recursive
```

### <a name="example-3"></a>Eksempel 3

Dette er et eksempel for en kildemappe, der er placeret i en overordnet V2-Azure Storage konto. Adgangsniveauer bevares ikke, når PST-filerne uploades.

```powershell
azcopy.exe copy "https://storageaccountid.blob.core.windows.net/PSTs?sp=racwdl&st=2021-09-21T07:25:53Z&se=2021-09-21T15:25:53Z&sv=2020-08-04&sr=c&sig=xxxxxx" "https://3c3e5952a2764023ad14984.blob.core.windows.net/ingestiondata?sv=2012-02-12&amp;se=9999-12-31T23%3A59%3A59Z&amp;sr=c&amp;si=IngestionSasForAzCopy201601121920498117&amp;sig=Vt5S4hVzlzMcBkuH8bH711atBffdrOS72TlV1mNdORg%3D" --s2s-preserve-access-tier=false
```

Når du har kørt kommandoen, vises der statusmeddelelser, der viser status for overførsel af PST-filerne. En endelig statusmeddelelse viser det samlede antal filer, der er blevet overført.

> [!TIP]
> Når du har kørt kommandoen **azcopy.exe-kopi** og kontrollere, at alle parametrene er korrekte, skal du gemme en kopi af syntaksen på kommandolinjen i den samme (sikrede) fil, hvor du kopierede de oplysninger, du fik i trin 1. Derefter kan du kopiere og indsætte denne kommando i en kommandoprompt, hver gang du vil køre AzCopy-værktøjet til at uploade PST-filer til Microsoft 365. Den eneste værdi, du muligvis skal ændre, er for kildefeltet. Dette afhænger af den kildemappe, hvor PST-filerne er placeret.

## <a name="optional-step-3-view-a-list-of-the-pst-files-uploaded-to-microsoft-365"></a>(Valgfrit) Trin 3: Få vist en liste over pst.-filer, der er uploadet Microsoft 365

Som et valgfrit trin kan du installere og bruge Microsoft Azure Storage Stifinder (som er et gratis, open source-værktøj) til at få vist listen over PST-filer, du har uploadet til Azure Blob. Der er to gode grunde til at gøre dette:
  
- Kontrollér, at PST-filer fra den delte mappe eller filserver i organisationen er blevet uploadet til Azure blob.

- Bekræft filnavnet (og stinavnet for undermappen, hvis du inkluderede et) for hver PST-fil, der er uploadet til Azure blob. Dette er nyttigt, når du opretter PST-tilknytningsfilen i næste trin, fordi du skal angive både mappestinavn og filnavn for hver PST-fil. Bekræftelse af disse navne kan være med til at reducere potentielle fejl i PST-tilknytningsfilen.

Det Azure Storage Explorer-enkeltstående program er generelt tilgængeligt. Du kan downloade den nyeste version ved hjælp af linket i følgende procedure.
  
> [!IMPORTANT]
> Du kan ikke bruge Stifinder Azure Storage at uploade eller redigere PST-filer. Den eneste understøttede metode til import af PST-filer er at bruge AzCopy. Du kan heller ikke slette PST-filer, du har uploadet til Azure Blob. Hvis du forsøger at slette en PST-fil, får du en fejl om, at du ikke har de nødvendige tilladelser. Bemærk, at alle PST-filer automatisk slettes fra dit Azure-lagringsområde. Hvis der ikke er nogen importjob i gang, slettes alle PST-filer i beholderen **til ingestiondata** 30 dage efter, det seneste importjob blev oprettet.
  
Sådan installerer du Azure Storage og opretter forbindelse til dit Azure Storage område:
  
1. Download og installér [værktøjet Microsoft Azure Storage Stifinder](https://go.microsoft.com/fwlink/p/?LinkId=544842).

2. Start Microsoft Azure Storage Stifinder.

3. På siden **Vælg ressource** i dialogboksen Forbind **for Azure Storage skal du** klikke på **Blob-beholder**.
  
4. På siden **Vælg godkendelsesmetode** skal du vælge **indstillingen SAS -signatur (Shared Access Signature),** og derefter skal du klikke på **Næste**.

5. På siden **Angiv forbindelsesoplysninger** skal du indsætte SAS URL-adressen, du fik i trin 1, i feltet under **Blob container SAS URL** og derefter klikke på **Næste**. Når du har indsættet SAS URL-adressen, **udfyldes feltet** under Vist navn automatisk **med ingestiondata**.

6. På siden **Oversigt** kan du gennemse forbindelsesoplysningerne og derefter klikke på **Forbind**.

    **Beholderen til ingestiondata** åbnes. Den indeholder de PST-filer, du har uploadet i trin 2. **Beholderen til ingestiondata** er placeret under **Storage (Vedhæftede** \> **beholdere)** \> **Blob-beholdere**. 
  
7. Når du er færdig med at bruge Microsoft Azure Storage Stifinder, skal du højreklikke **på ingestiondata** og derefter klikke på Fjern  for at afbryde forbindelsen Azure Storage området. Ellers vises der en fejl, næste gang du forsøger at vedhæfte.
  
## <a name="step-4-create-the-pst-import-mapping-file"></a>Trin 4: Opret tilknytningsfilen til PST-import

Når PST-filerne er blevet uploadet til Azure Storage-placeringen for organisationen, er næste trin at oprette en fil med kommaseparerede værdier (CSV), der angiver, hvilke brugerpostkasser PST-filerne importeres til. Du skal sende denne CSV-fil i næste trin, når du opretter et PST-importjob.
  
1. [Download en kopi af PST-importtilknytningsfilen](https://go.microsoft.com/fwlink/p/?LinkId=544717).

2. Åbn eller gem CSV-filen på din lokale computer. I følgende eksempel vises en fuldført PST-importtilknytningsfil (åbnet i Notesblok). Det er meget nemmere at bruge Microsoft Excel at redigere CSV-filen.

    ```console
    Workload,FilePath,Name,Mailbox,IsArchive,TargetRootFolder,ContentCodePage,SPFileContainer,SPManifestContainer,SPSiteUrl
    Exchange,,annb.pst,annb@contoso.onmicrosoft.com,FALSE,/,,,,
    Exchange,,annb_archive.pst,annb@contoso.onmicrosoft.com,TRUE,,,,,
    Exchange,,donh.pst,donh@contoso.onmicrosoft.com,FALSE,/,,,,
    Exchange,,donh_archive.pst,donh@contoso.onmicrosoft.com,TRUE,,,,,
    Exchange,PSTFiles,pilarp.pst,pilarp@contoso.onmicrosoft.com,FALSE,/,,,,
    Exchange,PSTFiles,pilarp_archive.pst,pilarp@contoso.onmicrosoft.com,TRUE,/ImportedPst,,,,
    Exchange,PSTFiles,tonyk.pst,tonyk@contoso.onmicrosoft.com,FALSE,,,,,
    Exchange,PSTFiles,tonyk_archive.pst,tonyk@contoso.onmicrosoft.com,TRUE,/ImportedPst,,,,
    Exchange,PSTFiles,zrinkam.pst,zrinkam@contoso.onmicrosoft.com,FALSE,,,,,
    Exchange,PSTFiles,zrinkam_archive.pst,zrinkam@contoso.onmicrosoft.com,TRUE,/ImportedPst,,,,
    ```

    Den første række (eller kolonneoverskriften) i CSV-filen viser de parametre, der skal bruges af PST-importtjenesten til at importere PST-filer til brugerpostkasser. Hvert parameternavn er adskilt af et komma. Hver række under kolonneoverskriften repræsenterer parameterværdierne for import af en PST-fil til en bestemt postkasse. Du skal bruge en række for hver PST-fil, du vil importere til en brugerpostkasse. Du kan maksimalt have 500 rækker i CSV-tilknytningsfilen. Hvis du vil importere mere end 500 PST-filer, skal du oprette flere tilknytningsfiler og oprette flere importjob i trin 5.

    > [!NOTE]
    > Du skal ikke ændre noget i kolonneoverskriften, herunder SharePoint parametrene, de ignoreres under PST-importprocessen. Sørg også for at erstatte pladsholderdataene i tilknytningsfilen med de faktiske data.

3. Brug oplysningerne i følgende tabel til at udfylde CSV-filen med de nødvendige oplysninger.

    | Parameter | Beskrivelse | Eksempel |
    |:-----|:-----|:-----|
    | `Workload` <br/> |Angiver den tjeneste, data importeres til. Hvis du vil importere PST-filer til brugerpostkasser, skal du bruge  `Exchange`.  <br/> | `Exchange` <br/> |
    | `FilePath` <br/> |Angiver mappeplaceringen på den placering Azure Storage du har uploadet PST-filerne til i trin 2.  <br/> Hvis du ikke medtager et valgfrit navn til undermappen i SAS URL-adressen  `/Dest:` i parameteren i trin 2, skal du lade denne parameter være tom i CSV-filen. Hvis du har medtaget navnet på en undermappe, skal du angive den i denne parameter (se det andet eksempel). Der er store og små bogstaver i værdien for denne parameter.  <br/> Uanset hvad  *, skal du ikke*  medtage "ingestiondata" i værdien for  `FilePath` parameteren.  <br/><br/> **Vigtigt!** Tilfældet med filnavnet skal være det samme som det tilfælde, du brugte, hvis du inkluderede et valgfrit navn til undermappen i SAS URL-adressen i destinationsfeltet i trin 2. Hvis du f.eks.  `PSTFiles` brugte navnet på undermappen i trin 2  `pstfiles`  `FilePath` og derefter bruger i parameteren i CSV-filen, mislykkes importen af PST-filen. Sørg for at bruge den samme sag i begge forekomster.  <br/> |(lad feltet være tomt)  <br/> Eller  <br/>  `PSTFiles` <br/> |
    | `Name` <br/> |Angiver navnet på den PST-fil, der importeres til brugerpostkassen. Der er store og små bogstaver i værdien for denne parameter. Filnavnet på hver PST-fil i tilknytningsfilen til et importjob skal være entydigt. <br/> <br/>**Vigtigt!** Tilfældet med PST-filnavnet i CSV-filen skal være det samme som den PST-fil, der blev uploadet til placeringen Azure Storage i trin 2. Hvis du f.eks  `annb.pst`  `Name` . bruger i parameteren i CSV-filen, men navnet på den faktiske PST-fil `AnnB.pst`er , så mislykkes importen for den pågældende PST-fil. Sørg for, at navnet på PST-filen i CSV-filen bruger det samme tilfælde som den faktiske PST-fil.  <br/> | `annb.pst` <br/> |
    | `Mailbox` <br/> |Angiver mailadressen på den postkasse, som PST-filen importeres til. Du kan ikke angive en offentlig mappe, fordi PST-importtjenesten ikke understøtter import af PST-filer til offentlige mapper.  <br/> Hvis du vil importere en PST-fil til en inaktiv postkasse, skal du angive postkasse-GUID'et for denne parameter. For at få dette GUID skal du køre følgende PowerShell-kommando i Exchange Online:`Get-Mailbox <identity of inactive mailbox> -InactiveMailboxOnly | FL Guid` <br/> <br/>**Bemærk!** Nogle gange kan du have flere postkasser med den samme mailadresse, hvor den ene postkasse er en aktiv postkasse, og den anden postkasse er i en blød-slettet (eller inaktiv) tilstand. I disse situationer skal du angive postkasse-GUID'et for entydigt at identificere postkassen, som PST-filen skal importeres til. For at få dette GUID til aktive postkasser skal du køre følgende PowerShell-kommando:  `Get-Mailbox <identity of active mailbox> | FL Guid`. Kør denne kommando for at hente GUID'et for blød-slettede (eller inaktive) postkasser  `Get-Mailbox <identity of soft-deleted or inactive mailbox> -SoftDeletedMailbox | FL Guid`.  <br/> | `annb@contoso.onmicrosoft.com` <br/> Eller  <br/>  `2d7a87fe-d6a2-40cc-8aff-1ebea80d4ae7` <br/> |
    | `IsArchive` <br/> | Angiver, om PST-filen skal importeres til brugerens arkivpostkasse. Der er to muligheder:  <br/><br/>**FALSK:** Importerer PST-filen til brugerens primære postkasse.  <br/> **SAND:** Importerer PST-filen til brugerens arkivpostkasse. Her antages det [, at brugerens arkivpostkasse er aktiveret](enable-archive-mailboxes.md). <br/><br/>Hvis du indstiller denne parameter til  `TRUE` , og brugerens arkivpostkasse ikke er aktiveret, så mislykkes importen for den pågældende bruger. Hvis en import mislykkes for én bruger (  `TRUE`fordi brugerens arkiv ikke er aktiveret, og denne egenskab er angivet til ), påvirkes de andre brugere i importjobbet ikke.  <br/>  Hvis du lader denne parameter være tom, importeres PST-filen til brugerens primære postkasse.  <br/> <br/>**Bemærk!** Hvis du vil importere en PST-fil til en skybaseret arkivpostkasse for en bruger, hvis primære postkasse er lokal,  `TRUE` skal du blot angive for denne parameter og angive mailadressen til brugerens lokale postkasse for  `Mailbox` parameteren.  <br/> | `FALSE` <br/> Eller  <br/>  `TRUE` <br/> |
    | `TargetRootFolder` <br/> | Angiver den postkassemappe, pst.-filen importeres til.  <br/> <br/> Hvis du lader denne parameter være tom, importeres PST-filen til en ny mappe med  navnet Importeret på postkassens rodniveau (det samme niveau som mappen Indbakke og de andre standardpostkassemapper).  <br/> <br/> Hvis du angiver  `/`, importeres mapperne og elementerne i PST-filen til toppen af mappestrukturen i målpostkassen eller -arkivet. Hvis der findes en mappe i målpostkassen (f.eks. standardmapper som Indbakke, Sendt post og Slettet post), flettes elementerne i den pågældende mappe i PST-filen ind i den eksisterende mappe i destinationspostkassen. Hvis PST-filen f.eks. indeholder en indbakkemappe, importeres elementer i den pågældende mappe til indbakkemappen i målpostkassen. Der oprettes nye mapper, hvis de ikke findes i mappestrukturen for destinationspostkassen.  <br/><br/>  Hvis du angiver  `/<foldername>`, importeres elementer og mapper i PST-filen til en mappe med navnet  *\<foldername\>*  . Hvis du f.eks. bruger  `/ImportedPst`, importeres elementer til en mappe med navnet **ImportedPst**. Denne mappe vil være placeret i brugerens postkasse på samme niveau som mappen Indbakke.  <br/><br/> **Tip!** Overvej at køre et par testbatchs for at eksperimentere med denne parameter, så du kan bestemme den bedste mappeplacering til at importere PST-filer til.  <br/> |(lad feltet være tomt)  <br/> Eller  <br/>  `/` <br/> Eller  <br/>  `/ImportedPst` <br/> |
    | `ContentCodePage` <br/> |Denne valgfri parameter angiver en numerisk værdi for den kodeside, der skal bruges til at importere PST-filer i ANSI-filformatet. Denne parameter bruges til at importere PST-filer fra kinesiske, japanske og koreanske (CJK) organisationer, fordi disse sprog typisk bruger dobbelt byte tegnsæt (DBCS) til tegnkodning. Hvis denne parameter ikke bruges til at importere PST-filer for sprog, der bruger DBCS til postkassemappenavne, er mappenavnene ofte forvanslede, når de er importeret.  <br/><br/> Du kan finde en liste over understøttede værdier, der skal bruges til denne parameter, under [Kodesideidentifikatorer](/windows/win32/intl/code-page-identifiers).  <br/> <br/>**Bemærk!** Som tidligere nævnt er dette en valgfri parameter, og du behøver ikke at medtage den i CSV-filen. Eller du kan medtage den og lade værdien være tom for en eller flere rækker.  <br/> |(lad feltet være tomt)  <br/> Eller  <br/>  `932` (som er kodesidens identifikator for JAPANSK ANSI/OEM)  <br/> |
    | `SPFileContainer` <br/> |I forbindelse med PST-import skal du lade denne parameter være tom.  <br/> |Ikke relevant  <br/> |
    | `SPManifestContainer` <br/> |I forbindelse med PST-import skal du lade denne parameter være tom.  <br/> |Ikke relevant  <br/> |
    | `SPSiteUrl` <br/> |I forbindelse med PST-import skal du lade denne parameter være tom.  <br/> |Ikke relevant  <br/> |

## <a name="step-5-create-a-pst-import-job"></a>Trin 5: Opret et PST-importjob

Næste trin er at oprette PST-importjobbet i importtjenesten i Microsoft 365. Som beskrevet tidligere indsender du den PST-importtilknytningsfil, du oprettede i trin 4. Når du har oprettet jobbet, analyserer Microsoft 365 dataene i PST-filerne og giver dig derefter mulighed for at filtrere de data, der faktisk importeres til de postkasser, der er angivet i PST-importtilknytningsfilen (se trin [6](#step-6-filter-data-and-start-the-pst-import-job)).
  
1. Gå til <https://compliance.microsoft.com> og log på med legitimationsoplysningerne til en administratorkonto i organisationen.

2. I venstre rude i Microsoft 365 Overholdelsescenter skal du klikke på **> Importér**.

3. Klik på **Tilføj** ikon under ![fanen Importér.](../media/ITPro-EAC-AddIcon.gif) **Nyt importjob**.

   > [!NOTE]
   > Du skal have tildelt de relevante tilladelser for at få adgang til **siden Import i** Microsoft 365 Overholdelsescenter for at oprette et importjob. Du kan **finde flere oplysninger i** afsnittet Inden du går i gang. 

4. Skriv et navn til PST-importjobbet, og klik derefter på **Næste**. Brug små bogstaver, tal, bindestreger og understregningstegn. Du må ikke bruge store bogstaver eller medtage mellemrum i navnet.

5. På siden **Vil du overføre eller sende data? skal du klikke** på **Upload dine data og** derefter klikke på **Næste**.
  
6. I trin 4 på siden **Importér data** skal du klikke på  afkrydsningsfelterne Jeg er færdig med at overføre mine  filer, og jeg har adgang til tilknytningsfilen og derefter klikke på **Næste**.

    ![Klik på de to afkrydsningsfelter i trin 4.](../media/9f2427e8-3af2-4e27-95e6-a9f08430d3d8.png)
  
7. På siden **Vælg tilknytningsfilen skal du** klikke  på Vælg tilknytningsfil for at sende den CSV-tilknytningsfil, du oprettede i trin 4.

    ![Klik på Vælg tilknytningsfil for at sende den CSV-fil, du har oprettet til importjobbet.](../media/d30b1d73-80bb-491e-a642-a21673d06889.png)
  
8. Når navnet på CSV-filen vises under Navnet på **tilknytningsfilen, skal** du klikke på **Valider** for at kontrollere CSV-filen for fejl.

    ![Klik på Valider for at kontrollere, om der er fejl i CSV-filen.](../media/4680999d-5538-4059-b878-2736a5445037.png)
  
    CSV-filen skal bekræftes for at kunne oprette et PST-importjob. Filnavnet ændres til grønt, når det er blevet valideret. Hvis valideringen mislykkes, skal du klikke **på linket Vis** log. Der åbnes en valideringsfejlrapport med en fejlmeddelelse for hver række i filen, der mislykkedes.

   > [!NOTE]
   > Som beskrevet tidligere kan en tilknytningsfil maksimalt have 500 rækker. Valideringen mislykkes, hvis tilknytningsfilen indeholder mere end 500 rækker. Hvis du vil importere mere end 500 PST-filer, skal du oprette flere tilknytningsfiler og flere importjob.

9. Når tilknytningsfilen er valideret, skal du læse dokumentet med vilkår og betingelser og derefter klikke i afkrydsningsfeltet.

10. Klik **på** Gem for at sende jobbet, og klik derefter **på** Luk, når jobbet er blevet oprettet.

    Der vises en pop op-side med statussen Analyse i  gang, og det nye importjob vises på listen på siden **Importér PST-filer**.

11. Klik **på ikonet** ![Opdater opdatering.](../media/O365-MDM-Policy-RefreshIcon.gif) for at opdatere de statusoplysninger, der vises i **kolonnen Status** . Når analysen er færdig, og dataene er klar til at blive importeret, ændres status til **Analyse fuldført**.

    Du kan klikke på importjobbet for at få vist pop op-siden med status pop op-filen, som indeholder mere detaljerede oplysninger om importjobbet, f.eks. status for hver PST-fil, der er angivet i tilknytningsfilen.

## <a name="step-6-filter-data-and-start-the-pst-import-job"></a>Trin 6: Filtrer data, og start PST-importjobbet

Når du har oprettet importjobbet i trin 5, analyserer Microsoft 365 dataene i PST-filerne (på en sikker måde) ved at identificere alderen på elementerne og de forskellige meddelelsestyper, der er inkluderet i PST-filerne. Når analysen er færdig, og dataene er klar til at blive importeret, har du mulighed for at importere alle de data, der er indeholdt i PST-filerne, eller du kan trimme de importerede data ved at angive filtre, der styrer, hvilke data der importeres.
  
1. På fanen **Importér** i feltet Microsoft 365 Overholdelsescenter du vælge de importjob, du oprettede i trin 5, og derefter klikke på **Importér til Microsoft 365**.
  
   Siden **Filtrer** dine data vises. Den indeholder dataindsigt, der er resultatet af den analyse, der er udført på PST-filer af Microsoft 365, herunder oplysninger om alderen på dataene. På dette tidspunkt har du mulighed for at filtrere de data, der importeres eller importerer alle dataene, som de er. 

    ![Du kan trimme dataene i PST-filerne eller importere dem alle.](../media/287fc030-99e9-417b-ace7-f64617ea5d4e.png)
  
2. Gør et af følgende:

   1. Hvis du vil trimme de data, du importerer, **skal du klikke på Ja, jeg vil filtrere dem, før du importerer**.

      Du kan finde detaljerede trinvise instruktioner om at filtrere dataene i PST-filerne og derefter starte importjobbet i Filtrer data, når du importerer [PST-filer til Microsoft 365](filter-data-when-importing-pst-files.md).

      Eller

   2. Hvis du vil importere alle data i PST-filerne, skal du **klikke på Nej, jeg vil importere alt og** klikke på **Næste**.

3. Hvis du vælger at importere alle dataene, skal du klikke på **Importér data** for at starte importjobbet. 

   Status for importjobbet vises på siden **Importér PST-filer** . Klik ![på ikonet Opdater.](../media/O365-MDM-Policy-RefreshIcon.gif) **Opdater** for at opdatere de statusoplysninger, der vises i **kolonnen Status** . Klik på importjobbet for at få vist siden med pop op-status, som viser statusoplysninger om hver PST-fil, der importeres.

## <a name="more-information"></a>Flere oplysninger

- Hvorfor importere PST-filer Microsoft 365?

  - Det er en god metode til at importere organisationens arkiveringsdata for at Microsoft 365.

  - Dataene er tilgængelige for brugeren fra alle enheder, fordi de er gemt i skyen.

  - Det hjælper med at imødekomme organisationens behov for overholdelse ved at lade Microsoft 365 overholdelsesfunktioner til data fra PST-filer, du har importeret. Dette omfatter:

  - Aktivering af [arkivpostkasser og](enable-archive-mailboxes.md) [automatisk udvidende arkivering](enable-autoexpanding-archiving.md) for at give brugerne yderligere lagerplads til postkasser til lagring af de data, du har importeret.

  - Placere postkasser i retslig [tilbageholdelse for](./create-a-litigation-hold.md) at bevare de data, du har importeret.

  - Brug Microsoft [eDiscovery-værktøjer til](search-for-content.md) at søge i de data, du har importeret.

  - Brug [Microsoft 365 opbevaringspolitikker](retention.md) til at styre, hvor længe de importerede data bevares, og hvilken handling der skal ske, når en opbevaringsperiode udløber.

  - Søgning i [overvågningsloggen](search-the-audit-log-in-security-and-compliance.md) efter postkasserelaterede hændelser, der påvirker de data, du har importeret.

  - Import af data til [inaktive postkasser for at](inactive-mailboxes-in-office-365.md) arkivere data af hensyn til overholdelse af regler og standarder. 

  - Brug [af politikker til forebyggelse af datatab](dlp-learn-about-dlp.md) til at forhindre, at følsomme data ulækager uden for organisationen.

- Som beskrevet tidligere aktiverer tjenesten Microsoft 365 Opbevaring (i ubegrænset tid), efter PST-filer importeres til en postkasse. Det betyder, *at egenskaben RetentionHoldEnabled* er angivet  til Sand, så den opbevaringspolitik, der er tildelt postkassen, ikke behandles. Dette giver postkasseejeren tid til at administrere de nyligt importerede meddelelser ved at forhindre sletnings- eller arkiveringspolitik i at slette eller arkivere ældre meddelelser. Her er nogle trin, du kan gøre for at administrere denne opbevaringsposition:

  - Efter et bestemt tidsrum kan du deaktivere opbevaringspositionen ved at køre **kommandoen Set-Mailbox -RetentionHoldEnabled $false** opbevaring. Du kan finde en vejledning under [Placere en postkasse i venteposition](/exchange/security-and-compliance/messaging-records-management/mailbox-retention-hold).

  - Du kan konfigurere opbevaringspositionen, så den er slået fra på en eller anden dato i fremtiden. Det gør du ved at køre **kommandoen Set-Mailbox -EndDateForRetentionHold *date*** . Hvis f.eks. dags dato er 1. juni 2016, og du vil deaktivere opbevaringspositionen om 30 dage, skal du køre følgende kommando:  **Set-Mailbox -EndDateForRetentionHold 01-07-2016**. I dette scenarie skal egenskaben  **OpbevaringsholdEnabled**  være angivet til  *Sand*. Du kan få mere at vide [under Set-Mailbox](/powershell/module/exchange/set-mailbox).

  - Du kan ændre indstillingerne for den opbevaringspolitik, der er tildelt til postkassen, så ældre elementer, der er blevet importeret, ikke straks slettes eller flyttes til brugerens arkivpostkasse. Eksempelvis kan du forlænge opbevaringsalderen for en sletning eller arkiveringspolitik, der er tildelt postkassen. I dette scenarie skal du deaktivere opbevaringspositionen på postkassen, når du har ændret indstillingerne for opbevaringspolitikken. Få mere at vide under [Konfigurer en arkiverings- og sletningspolitik for postkasser i organisationen](set-up-an-archive-and-deletion-policy-for-mailboxes.md).

### <a name="how-the-import-process-works"></a>Sådan fungerer importprocessen
  
Du kan bruge indstillingen netværksupload og tjenesten Microsoft 365 import til masseimport af PST-filer til brugerpostkasser. Netværksupload betyder, at du overfører PST-filerne til et midlertidigt lagringsområde i Microsoft-skyen. Derefter kopierer Microsoft 365-importtjenesten PST-filerne fra lagringsområdet til målbrugerpostkasserne.
  
Her er en illustration og beskrivelse af netværksuploadprocessen til import af PST-filer til postkasser i Microsoft 365.
  
![Arbejdsproces for netværksuploadprocessen til import af PST-filer Microsoft 365.](../media/9e05a19e-1e7a-4f1f-82df-9118f51588c4.png)
  
1. **Download PST-importværktøjet** og -nøglen til privat Azure Storage-placering: Det første trin er at downloade kommandolinjeværktøjet AzCopy og en adgangsnøgle, der bruges til at uploade PST-filerne til en Azure Storage-placering i Microsoft-skyen. Du får disse fra **siden Import** i Microsoft 365 Overholdelsescenter. Nøglen (kaldet EN SIKKER adgangssignatur (SAS) giver dig de nødvendige tilladelser til at uploade PST-filer til en privat og sikker placering Azure Storage placering. Denne adgangsnøgle er unik for din organisation og hjælper med at forhindre uautoriseret adgang til dine PST-filer, når de er uploadet til Microsoft Cloud. Import af PST-filer kræver ikke, at din organisation har et separat Azure-abonnement. 

2. **Upload PST-filerne til Azure Storage-placeringen:** Næste trin er at bruge værktøjet azcopy.exe (downloadet i trin 1) til at uploade og gemme dine PST-filer på en placering i Azure Storage, som er placeret i det samme regionale Microsoft-datacenter, hvor din organisation er placeret. Hvis du vil overføre dem, skal de PST-filer, du vil importere, være placeret i et filshare eller en filserver i organisationen.

    Der er et valgfrit trin, du kan udføre for at få vist listen over PST-filer, når de er uploadet til Azure Storage placering.

3. **Opret en PST-importtilknytningsfil:** Når PST-filerne er blevet uploadet til placeringen i Azure Storage, er næste trin at oprette en kommasepareret fil (CSV), der angiver, hvilke brugerpostkasser PST-filerne skal importeres til. Bemærk, at en PST-fil kan importeres til en brugers primære postkasse eller dennes arkivpostkasse. Tjenesten Microsoft 365 importerer bruger oplysningerne i CSV-filen til at importere PST-filerne.

4. **Opret et PST-importjob:** Næste trin er at oprette et PST-importjob på siden **Importér PST-filer** i Microsoft 365 Overholdelsescenter og sende den PST-importtilknytningsfil, der blev oprettet i det forrige trin. Når du har oprettet importjobbet, analyserer Microsoft 365 dataene i PST-filerne og giver dig derefter mulighed for at angive filtre, der styrer, hvilke data der faktisk importeres til de postkasser, der er angivet i PST-importtilknytningsfilen. 

5. **Filtrer de PST-data, der importeres til postkasser:** Når importjobbet er oprettet og startet, analyserer Microsoft 365 dataene i PST-filerne (sikkert og sikkert) ved at identificere alderen på elementerne og de forskellige meddelelsestyper, der er inkluderet i PST-filerne. Når analysen er færdig, og dataene er klar til at blive importeret, har du mulighed for at importere alle de data, der er indeholdt i PST-filerne, eller du kan trimme de importerede data ved at angive filtre, der styrer, hvilke data der importeres.

6. **Start PST-importjobbet:** Når importjobbet er startet, bruger Microsoft 365 oplysningerne i PST-importtilknytningsfilen til at importere PST-filerne fra den Azure Storage placering til brugerpostkasserne. Statusoplysninger om importjobbet (herunder oplysninger om hver PST-fil, der importeres) vises på siden **Importér PST-filer** i Microsoft 365 Overholdelsescenter. Når importjobbet er afsluttet, angives jobstatus til **Fuldført**.
