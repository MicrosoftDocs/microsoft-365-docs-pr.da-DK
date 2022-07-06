---
title: Brug netværksupload til at importere PST-filer
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: 'For administratorer: Få mere at vide om, hvordan du bruger netværksupload til masseimport af flere PST-filer til brugerpostkasser i Microsoft 365.'
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 0b24dc0ddc69c9af7516ee844af3899ff92fe4c4
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66626023"
---
# <a name="use-network-upload-to-import-your-organizations-pst-files-to-microsoft-365"></a>Brug netværksoverførsel til at importere din organisations PST-filer til Microsoft 365

> [!NOTE]
> Denne artikel er til administratorer. Forsøger du at importere PST-filer til din egen postkasse? Se [Importér mail, kontakter og kalender fra en Outlook.pst-fil](https://go.microsoft.com/fwlink/p/?LinkID=785075)
  
Her er de trinvise instruktioner, der kræves for at bruge netværksupload til masseimport af flere PST-filer til Microsoft 365-postkasser. Hvis du vil have mere at vide om, hvordan du bruger netværksoverførsel til masseimport af PST-filer til Microsoft 365-postkasser, skal du se [Ofte stillede spørgsmål om brug af netværksupload til at importere PST-filer](./faqimporting-pst-files-to-office-365.yml#using-network-upload-to-import-pst-files).
  
[Trin 1: Kopiér SAS URL-adressen, og download AzCopy](#step-1-copy-the-sas-url-and-download-azcopy)

[Trin 2: Overfør dine PST-filer til Microsoft 365](#step-2-upload-your-pst-files-to-microsoft-365)

[(Valgfrit) Trin 3: Få vist en liste over de PST-filer, der er overført](#optional-step-3-view-a-list-of-the-pst-files-uploaded-to-microsoft-365)

[Trin 4: Opret PST-importtilknytningsfilen](#step-4-create-the-pst-import-mapping-file)

[Trin 5: Opret et PST-importjob](#step-5-create-a-pst-import-job)

[Trin 6: Filtrer data, og start PST-importjobbet](#step-6-filter-data-and-start-the-pst-import-job)

Du skal kun udføre trin 1 én gang for at importere PST-filer til Microsoft 365-postkasser. Når du har udført disse trin, skal du følge trin 2 til og med trin 6, hver gang du vil uploade og importere et bundt PST-filer.

## <a name="before-you-import-pst-files"></a>Før du importerer PST-filer
  
- Du skal have tildelt rollen Importér eksport af postkasse i Exchange Online for at oprette importjob i Microsoft Purview-compliance-portal og importere PST-filer til brugerpostkasser. Denne rolle er som standard ikke tildelt nogen rollegruppe i Exchange Online. Du kan føje rollen Importér eksport af postkasse til rollegruppen Organisationsadministration. Du kan også oprette en rollegruppe, tildele rollen Importér eksport af postkasse og derefter tilføje dig selv som medlem. Du kan få flere oplysninger i afsnittene "Føj en rolle til en rollegruppe" eller "Opret en rollegruppe" i [Administrer rollegrupper](/Exchange/permissions-exo/role-groups).

    Ud over rollen Importér eksport af postkasse skal du også tildeles rollen Mailmodtagere i Exchange Online. Denne rolle er som standard tildelt rollegrupperne Organisationsadministration og Modtageradministration i Exchange Online.

    > [!TIP]
    > Overvej at oprette en ny rollegruppe i Exchange Online, der er specifikt beregnet til import af PST-filer. Hvis du vil have det minimumsniveau af rettigheder, der kræves for at importere PST-filer, skal du tildele rollerne Importér eksport af postkasse og Postmodtagere til den nye rollegruppe og derefter tilføje medlemmer.
  
- Den eneste understøttede metode til import af PST-filer til Microsoft 365 er at bruge værktøjet AzCopy, som beskrevet i denne artikel. Du kan ikke bruge Azure Storage Explorer til at uploade PST-filer direkte til Azure Storage-området.

- Store PST-filer kan påvirke ydeevnen af PST-importprocessen. Derfor anbefaler vi, at hver PST-fil, du uploader til Azure Storage-placeringen i Trin 2, ikke må være større end 20 GB.

- Denne procedure omfatter kopiering og lagring af en kopi af en URL-adresse, der indeholder en adgangsnøgle. Disse oplysninger bruges i trin 2 til at uploade dine PST-filer og i trin 3, hvis du vil have vist en liste over de PST-filer, der er uploadet til Microsoft 365. Sørg for at tage forholdsregler for at beskytte denne URL-adresse, som du ville beskytte adgangskoder eller andre sikkerhedsrelaterede oplysninger. Du kan f.eks. gemme det i et microsoft Word-dokument, der er beskyttet med adgangskode, eller på et krypteret USB-drev. Se afsnittet [Flere oplysninger](#more-information) for at få et eksempel på denne kombinerede URL-adresse og nøgle.

- Du kan importere PST-filer til en inaktiv postkasse i Microsoft 365. Det gør du ved at angive GUID'et for den inaktive postkasse i parameteren  `Mailbox` i PST-importtilknytningsfilen. Du kan finde flere oplysninger under Trin 4 under fanen **Instruktioner** i denne artikel.

- I en Hybrid Exchange-udrulning kan du importere PST-filer til en skybaseret arkivpostkasse for en bruger, hvis primære postkasse er i det lokale miljø. Det gør du ved at gøre følgende i tilknytningsfilen til PST-import:

  - Angiv mailadressen for brugerens lokale postkasse i parameteren  `Mailbox` .

  - Angiv **TRUE-værdien** i parameteren  `IsArchive` .

    Se [Trin 4](#step-4-create-the-pst-import-mapping-file) for at få flere oplysninger.

- Når PST-filer er importeret, aktiveres indstillingen for opbevaring af venteposition for postkassen i en ubestemt varighed. Det betyder, at den opbevaringspolitik, der er tildelt postkassen, ikke behandles, før du slår opbevarings ventepositionen fra eller angiver en dato for at slå ventepositionen fra. Hvorfor gør vi det? Hvis meddelelser, der er importeret til en postkasse, er gamle, kan de blive slettet permanent (slettet), fordi deres opbevaringsperiode er udløbet på baggrund af de opbevaringsindstillinger, der er konfigureret for postkassen. Hvis postkassen placeres i opbevaringsposition, kan ejeren af postkassen administrere disse nyligt importerede meddelelser eller give dig tid til at ændre opbevaringsindstillingerne for postkassen. Se afsnittet [Flere oplysninger](#more-information) i denne artikel for at få forslag til administration af opbevarings venteposition.

- Som standard er den maksimale meddelelsesstørrelse, der kan modtages af en Microsoft 365-postkasse, 35 MB. Det skyldes, at standardværdien for egenskaben  *MaxReceiveSize*  for en postkasse er angivet til 35 MB. Grænsen for den maksimale størrelse på meddelelser i Microsoft 365 er dog 150 MB. Så hvis du importerer en PST-fil, der indeholder et element, der er større end 35 MB, ændrer microsoft 365-importtjenesten automatisk værdien af egenskaben  *MaxReceiveSize*  i destinationspostkassen til 150 MB. Dette gør det muligt at importere meddelelser op til 150 MB til brugerpostkasser.

    > [!TIP]
    > Hvis du vil identificere meddelelsens modtagelsesstørrelse for en postkasse, kan du køre denne kommando i Exchange Online PowerShell: `Get-Mailbox <user mailbox> | FL MaxReceiveSize`.

- Du kan få en overordnet oversigt over PST-importprocessen i afsnittet [Sådan fungerer importprocessen](#how-the-import-process-works) i denne artikel.

## <a name="step-1-copy-the-sas-url-and-download-azcopy"></a>Trin 1: Kopiér SAS URL-adressen, og download AzCopy

Det første trin er at downloade AzCopy-værktøjet, som er det værktøj, du kører i trin 2 for at uploade PST-filer til Microsoft 365. Du kopierer også SAS-URL-adressen for din organisation. Denne URL-adresse er en kombination af netværks-URL-adressen til Azure Storage-placeringen i Microsoft-cloudmiljøet for din organisation og en SAS-nøgle (Shared Access Signature). Denne nøgle giver dig de nødvendige tilladelser til at uploade PST-filer til en Azure Storage-placering. Sørg for at tage forholdsregler for at beskytte SAS URL-adressen. Det er unikt for din organisation og bruges i trin 2.

> [!IMPORTANT]
> Hvis du vil importere PST-filer ved hjælp af metoden til netværksupload og kommandosyntaksen, der er beskrevet i denne artikel, skal du bruge den version af AzCopy, der kan hentes i trin 6b i følgende procedure. Du kan også downloade den samme version af AzCopy [herfra](https://aka.ms/downloadazcopylatest). Brug af en anden version af AzCopy understøttes ikke.
  
1. Gå til , <https://compliance.microsoft.com> og log på med legitimationsoplysningerne for en administratorkonto i din organisation.

2. Klik på **Import** af **datalivscyklusstyring** \> i ruden til venstre på overholdelsesportalen.

    > [!NOTE]
    > Du skal have tildelt de nødvendige tilladelser for at få adgang til siden **Import** på overholdelsesportalen. Se afsnittet **Før du begynder for at få** flere oplysninger. 

3. Klik på ![Tilføj ikon under fanen **Importér**.](../media/ITPro-EAC-AddIcon.gif) **Nyt importjob**.

    Guiden Importér job vises.

4. Skriv et navn til PST-importjobbet, og klik derefter på **Næste**. Brug små bogstaver, tal, bindestreger og understregningstegn. Du kan ikke bruge store bogstaver eller medtage mellemrum i navnet.

5. På siden **Vil du overføre eller sende data? skal du** klikke på **Overfør dine data** og derefter klikke på **Næste**.

    ![Klik på Overfør dine data for at oprette et importjob til netværksupload.](../media/e59f9dc3-ccde-44ff-ac38-c4e39d76ae85.png)
  
6. Gør følgende to ting på siden **Importér data** :

    ![Kopiér SAS URL-adressen, og download AzCopy-værktøjet på siden Importér data.](../media/74411014-ec4b-4e25-9065-404c934cce17.png)
  
    1. I trin 2 skal du klikke på **Vis SAS URL-adresse til netværksupload**. Når SAS URL-adressen vises, skal du klikke på **Kopiér til Udklipsholder** og derefter indsætte den og gemme den i en fil, så du kan få adgang til den senere.

    2. I trin 3 skal du klikke på **Download Azure AzCopy** for at downloade AzCopy-værktøjet til din lokale computer. Denne version af AzCopy er blot en eksekverbar fil, så der er ikke noget at installere.

   > [!NOTE]
   > Du kan lade **siden Importér data** være åben (hvis du skal kopiere SAS-URL-adressen igen) eller klikke på **Annuller** for at lukke den.

## <a name="step-2-upload-your-pst-files-to-microsoft-365"></a>Trin 2: Overfør dine PST-filer til Microsoft 365

Nu er du klar til at bruge AzCopy-værktøjet til at uploade PST-filer til Microsoft 365. Dette værktøj uploader og gemmer PST-filer på en Microsoft-leveret Azure Storage-placering i Microsoft-cloudmiljøet. Som tidligere forklaret, er den Azure Storage-placering, du uploader dine PST-filer til, placeret i det samme regionale Microsoft-datacenter, hvor din organisation er placeret. Pst-filerne skal være placeret på et filshare eller en filserver i din organisation eller på en Azure Storage-placering, der administreres af din organisation, for at fuldføre dette trin. PST-lagringsplaceringen kaldes kildeplaceringen i denne procedure. Hver gang du kører azcopy-værktøjet, kan du angive en anden kildeplacering.

> [!NOTE]
> Som tidligere nævnt må hver PST-fil, du uploader til Azure Storage-placeringen, ikke være større end 20 GB. PST-filer, der er større end 20 GB, kan påvirke ydeevnen af den PST-importproces, du starter i trin 6. Hver PST-fil skal også have et entydigt navn.

1. Åbn en kommandoprompt på din lokale computer.

2. Gå til den mappe, hvor du downloadede azcopy.exe-filen i trin 1.

3. Kør følgende kommando for at overføre PST-filerne til Microsoft 365.

    ```powershell
    azcopy.exe copy "<Source location of PST files>" "<SAS URL>"
    ```

    > [!IMPORTANT]
    > Du kan angive en mappe eller en Azure Storage-placering som kildeplacering i den forrige kommando. Du kan ikke angive en individuel PST-fil. Alle PST-filer på kildeplaceringen overføres.

    I følgende tabel beskrives de azcopy.exe felter og deres påkrævede værdier. De oplysninger, du fik i det forrige trin, bruges i værdierne for disse felter.

    | Feltet | Beskrivelse |
    |:-----|:-----|
    | Kilde |Det første felt angiver den kildemappe i din organisation, der indeholder de PST-filer, der uploades til Microsoft 365. Du kan også angive en Azure Storage-placering som kildeplacering for de PST-filer, der skal uploades. <br/> Sørg for at omgive værdien af dette felt med dobbelte anførselstegn (" ").  <br/> <br/>**Eksempler**: <br/>`"\\FILESERVER01\PSTs"` <br/> Eller  <br/>`"https://storageaccountid.blob.core.windows.net/PSTs?sp=racwdl&st=2021-09-21T07:25:53Z&se=2021-09-21T15:25:53Z&sv=2020-08-04&sr=c&sig=xxxxxx"`|  
    | Destination |Angiver den SAS-URL-adresse, du fik i trin 1.  <br/> Sørg for at omgive værdien af denne parameter med dobbelte anførselstegn (" ").<br/><br/>**Bemærk:** Hvis du bruger SAS URL-adressen i et script eller en batchfil, skal du holde øje med visse tegn, der skal escapes. Du skal f.eks. skifte `%` til `%%` og ændre `&` til `^&`.<br/><br/>**Tip!** (Valgfrit) Du kan angive en undermappe på Azure Storage-placeringen, hvor PST-filerne skal uploades til. Det gør du ved at tilføje en undermappeplacering (efter "dataindtagelse") i SAS URL-adressen. I det første eksempel angives der ikke en undermappe. Det betyder, at PST-filerne uploades til roden (kaldet *data om indtagelse*) for Azure Storage-placeringen. I det andet eksempel uploades PST-filerne til en undermappe (kaldet  *PSTFiles*) i roden af Azure Storage-placeringen.  <br/><br/>**Eksempler**: <br/> `"https://3c3e5952a2764023ad14984.blob.core.windows.net/ingestiondata?sv=2012-02-12&amp;se=9999-12-31T23%3A59%3A59Z&amp;sr=c&amp;si=IngestionSasForAzCopy201601121920498117&amp;sig=Vt5S4hVzlzMcBkuH8bH711atBffdrOS72TlV1mNdORg%3D"` <br/> Eller  <br/>  `"https://3c3e5952a2764023ad14984.blob.core.windows.net/ingestiondata/PSTFiles?sv=2012-02-12&amp;se=9999-12-31T23%3A59%3A59Z&amp;sr=c&amp;si=IngestionSasForAzCopy201601121920498117&amp;sig=Vt5S4hVzlzMcBkuH8bH711atBffdrOS72TlV1mNdORg%3D"` <br/> |
    | `--recursive` |Dette valgfri flag angiver rekursiv tilstand, så værktøjet AzCopy kopierer PST-filer, der er placeret i undermapper i kildemappen, som er angivet i kildefeltet. Standardværdien for dette flag er `true`. <br/>**Bemærk:** Hvis du medtager dette flag, har PST-filer i undermapper et andet filnavn på Azure Storage-placeringen, når de er uploadet. Du skal angive det nøjagtige filnavn i den CSV-fil, du opretter i trin 4.|
    | `--s2s-preserve-access-tier` | Dette valgfrie flag er kun påkrævet, når kildeplaceringen er en generel v2 Azure Storage-placering, der understøtter adgangsniveauer. I forbindelse med PST-importscenariet er det ikke nødvendigt at bevare adgangsniveauet, når du kopierer PST-filer fra din Azure Storage-konto til den Azure Storage-placering, der leveres af Microsoft. I dette tilfælde kan du medtage dette flag og bruge værdien .`false` Du behøver ikke at bruge dette flag, når du kopierer PST-filer fra en klassisk Azure Storage-konto, som ikke understøtter adgangsniveauer.|
   |||

Du kan få flere oplysninger om kommandoen **azcopy.exe copy** under [azcopy copy (azcopy copy](/azure/storage/common/storage-ref-azcopy-copy)).

Her er eksempler på syntaksen for værktøjet AzCopy, der bruger faktiske værdier for hver parameter.

### <a name="example-1"></a>Eksempel 1

Dette er et eksempel på en kildemappe, der er placeret på filserveren eller på en lokal computer.

```powershell
azcopy.exe copy "\\FILESERVER1\PSTs" "https://3c3e5952a2764023ad14984.blob.core.windows.net/ingestiondata?sv=2012-02-12&amp;se=9999-12-31T23%3A59%3A59Z&amp;sr=c&amp;si=IngestionSasForAzCopy201601121920498117&amp;sig=Vt5S4hVzlzMcBkuH8bH711atBffdrOS72TlV1mNdORg%3D"
```

### <a name="example-2"></a>Eksempel 2

Dette er et eksempel på en kildemappe, der er placeret på en klassisk Azure Storage-konto med undermapper.

```powershell
azcopy.exe copy "https://storageaccountid.blob.core.windows.net/PSTs?sp=racwdl&st=2021-09-21T07:25:53Z&se=2021-09-21T15:25:53Z&sv=2020-08-04&sr=c&sig=xxxxxx" "https://3c3e5952a2764023ad14984.blob.core.windows.net/ingestiondata?sv=2012-02-12&amp;se=9999-12-31T23%3A59%3A59Z&amp;sr=c&amp;si=IngestionSasForAzCopy201601121920498117&amp;sig=Vt5S4hVzlzMcBkuH8bH711atBffdrOS72TlV1mNdORg%3D" --recursive
```

### <a name="example-3"></a>Eksempel 3

Dette er et eksempel på en kildemappe, der er placeret på en generel v2 Azure Storage-konto. Adgangsniveauer bevares ikke, når PST-filerne uploades.

```powershell
azcopy.exe copy "https://storageaccountid.blob.core.windows.net/PSTs?sp=racwdl&st=2021-09-21T07:25:53Z&se=2021-09-21T15:25:53Z&sv=2020-08-04&sr=c&sig=xxxxxx" "https://3c3e5952a2764023ad14984.blob.core.windows.net/ingestiondata?sv=2012-02-12&amp;se=9999-12-31T23%3A59%3A59Z&amp;sr=c&amp;si=IngestionSasForAzCopy201601121920498117&amp;sig=Vt5S4hVzlzMcBkuH8bH711atBffdrOS72TlV1mNdORg%3D" --s2s-preserve-access-tier=false
```

Når du har kørt kommandoen, vises der statusmeddelelser, der viser statussen for overførsel af PST-filerne. En endelig statusmeddelelse viser det samlede antal filer, der blev overført.

> [!TIP]
> Når du har kørt **kommandoenazcopy.exe copy** og kontrollere, at alle parametrene er korrekte, skal du gemme en kopi af kommandolinjesyntaksen i den samme (sikrede) fil, hvor du kopierede de oplysninger, du fik i trin 1. Derefter kan du kopiere og indsætte denne kommando i en kommandoprompt, hver gang du vil køre værktøjet AzCopy for at overføre PST-filer til Microsoft 365. Den eneste værdi, du skal ændre, er for kildefeltet. Dette afhænger af den kildemappe, hvor PST-filerne er placeret.

## <a name="optional-step-3-view-a-list-of-the-pst-files-uploaded-to-microsoft-365"></a>(Valgfrit) Trin 3: Få vist en liste over de PST-filer, der er uploadet til Microsoft 365

Som et valgfrit trin kan du installere og bruge Microsoft Azure Storage Explorer (som er et gratis værktøj med åben kildekode) til at få vist listen over de PST-filer, du har uploadet til Azure-blob. Der er to gode grunde til at gøre dette:
  
- Kontrollér, at PST-filer fra den delte mappe eller filserver i din organisation blev overført til Azure-blob.

- Kontrollér filnavnet (og stinavnet på undermappen, hvis du har inkluderet en) for hver PST-fil, der er overført til Azure-blob'en. Dette er nyttigt, når du opretter PST-tilknytningsfilen i næste trin, fordi du skal angive både mappestinavnet og filnavnet for hver PST-fil. Hvis du kontrollerer disse navne, kan det hjælpe med at reducere potentielle fejl i PST-tilknytningsfilen.

Det separate Azure Storage Explorer-program er generelt tilgængeligt. Du kan downloade den nyeste version ved hjælp af linket i følgende procedure.
  
> [!IMPORTANT]
> Du kan ikke bruge Azure Storage Explorer til at uploade eller redigere PST-filer. Den eneste understøttede metode til import af PST-filer er at bruge AzCopy. Du kan heller ikke slette PST-filer, som du har uploadet til Azure-blob. Hvis du forsøger at slette en PST-fil, får du vist en fejlmeddelelse om, at du ikke har de nødvendige tilladelser. Bemærk, at alle PST-filer automatisk slettes fra dit Azure-lagerområde. Hvis der ikke er nogen igangværende importjob, slettes alle PST-filer i objektbeholderen **ingestiondata** 30 dage efter, at det seneste importjob blev oprettet.
  
Sådan installerer du Azure Storage Explorer og opretter forbindelse til dit Azure Storage-område:
  
1. Download og installér [værktøjet Microsoft Azure Storage Explorer](https://go.microsoft.com/fwlink/p/?LinkId=544842).

2. Start Microsoft Azure Storage Explorer.

3. Klik på **Blob-objektbeholder** på siden **Vælg ressource** i dialogboksen **Opret forbindelse til Azure Storage**.
  
4. På siden **Vælg godkendelsesmetode** skal du vælge indstillingen **Delt adgangssignatur (SAS)** og derefter klikke på **Næste**.

5. På siden **Angiv forbindelsesoplysninger** skal du indsætte den SAS URL-adresse, du fik i trin 1, i feltet under **SAS URL-adresse til Blob-objektbeholder** og derefter klikke på **Næste**. Når du har indsat SAS URL-adressen, udfyldes feltet under **Vist navn** automatisk med **data om indtagelse**.

6. På siden **Oversigt** kan du gennemse forbindelsesoplysningerne og derefter klikke på **Opret forbindelse**.

    Databeholderen **for dataindtagelse** åbnes. Den indeholder de PST-filer, du overførte i trin 2. Dataobjektbeholderen til **dataindtagelse** er placeret under **Lagerkonti** \> **(vedhæftede objektbeholdere)** \> **Blob-objektbeholdere**. 
  
7. Når du er færdig med at bruge Microsoft Azure Storage Explorer, skal du højreklikke på **data om indtagelse** og derefter klikke på **Afbryd forbindelsen** for at afbryde forbindelsen til dit Azure Storage-område. Ellers får du vist en fejl, næste gang du forsøger at vedhæfte.
  
## <a name="step-4-create-the-pst-import-mapping-file"></a>Trin 4: Opret PST-importtilknytningsfilen

Når PST-filerne er blevet uploadet til Azure Storage-placeringen for din organisation, er det næste trin at oprette en kommasepareret værdifil (CSV), der angiver, hvilke brugerpostkasser PST-filerne importeres til. Du sender denne CSV-fil i næste trin, når du opretter et PST-importjob.
  
1. [Download en kopi af PST-importtilknytningsfilen](https://go.microsoft.com/fwlink/p/?LinkId=544717).

2. Åbn eller gem CSV-filen på din lokale computer. I følgende eksempel vises en fuldført PST-importtilknytningsfil (åbnet i Notesblok). Det er meget nemmere at bruge Microsoft Excel til at redigere CSV-filen.

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

    Den første række eller kolonneoverskrift i CSV-filen viser de parametre, der skal bruges af PST-importtjenesten til at importere PST-filerne til brugerpostkasser. Hvert parameternavn er adskilt af et komma. Hver række under overskriftsrækken repræsenterer parameterværdierne for import af en PST-fil til en bestemt postkasse. Du skal bruge en række for hver PST-fil, du vil importere til en brugerpostkasse. Du kan maksimalt have 500 rækker i CSV-tilknytningsfilen. Hvis du vil importere mere end 500 PST-filer, skal du oprette flere tilknytningsfiler og oprette flere importjob i trin 5.

    > [!NOTE]
    > Undlad at ændre noget i kolonneoverskriften, herunder SharePoint-parametrene. De ignoreres under PST-importprocessen. Sørg også for at erstatte pladsholderdataene i tilknytningsfilen med dine faktiske data.

3. Brug oplysningerne i følgende tabel til at udfylde CSV-filen med de påkrævede oplysninger.

    | Parameter | Beskrivelse | Eksempel |
    |:-----|:-----|:-----|
    | `Workload` <br/> |Angiver den tjeneste, som dataene skal importeres til. Hvis du vil importere PST-filer til brugerpostkasser, skal du bruge  `Exchange`.  <br/> | `Exchange` <br/> |
    | `FilePath` <br/> |Angiver mappeplaceringen på den Azure Storage-placering, du overførte PST-filerne til i trin 2.  <br/> Hvis du ikke inkluderede et valgfrit undermappenavn i SAS URL-adressen i  `/Dest:` parameteren i trin 2, skal du lade denne parameter være tom i CSV-filen. Hvis du har medtaget et undermappenavn, skal du angive det i denne parameter (se det andet eksempel). Der skelnes mellem store og små bogstaver i værdien for denne parameter.  <br/> Uanset hvad skal  *du ikke*  inkludere "data for indtagelse" i værdien for  `FilePath` parameteren.  <br/><br/> **Vigtigt:** Casen for filnavnet skal være den samme som den sag, du brugte, hvis du inkluderede et valgfrit undermappenavn i SAS URL-adressen i destinationsfeltet i trin 2. Hvis du f.eks. brugte  `PSTFiles` til navnet på undermappen i trin 2 og derefter bruger  `pstfiles` parameteren  `FilePath` i CSV-filen, mislykkes importen af PST-filen. Sørg for at bruge det samme tilfælde i begge tilfælde.  <br/> |(lad argumentet være tomt)  <br/> Eller  <br/>  `PSTFiles` <br/> |
    | `Name` <br/> |Angiver navnet på den PST-fil, der importeres til brugerpostkassen. Der skelnes mellem store og små bogstaver i værdien for denne parameter. Filnavnet på hver PST-fil i tilknytningsfilen for et importjob skal være entydigt. <br/> <br/>**Vigtigt:** Sagen for PST-filnavnet i CSV-filen skal være den samme som den PST-fil, der blev uploadet til Azure Storage-placeringen i trin 2. Hvis du f.eks. bruger  `annb.pst` parameteren i  `Name` CSV-filen, men navnet på den faktiske PST-fil er `AnnB.pst`, mislykkes importen af den pågældende PST-fil. Sørg for, at navnet på PST i CSV-filen bruger samme sag som den faktiske PST-fil.  <br/> | `annb.pst` <br/> |
    | `Mailbox` <br/> |Angiver mailadressen på den postkasse, som PST-filen importeres til. Du kan ikke angive en offentlig mappe, fordi PST-importtjenesten ikke understøtter import af PST-filer til offentlige mapper.  <br/> Hvis du vil importere en PST-fil til en inaktiv postkasse, skal du angive postkassens GUID for denne parameter. Hvis du vil hente dette GUID, skal du køre følgende PowerShell-kommando i Exchange Online:`Get-Mailbox <identity of inactive mailbox> -InactiveMailboxOnly | FL Guid` <br/> <br/>**Bemærk:** Nogle gange kan du have flere postkasser med den samme mailadresse, hvor den ene postkasse er en aktiv postkasse, og den anden postkasse er i tilstanden blød slettet (eller inaktiv). I disse situationer skal du angive postkassens GUID for entydigt at identificere den postkasse, PST-filen skal importeres til. Hvis du vil hente dette GUID til aktive postkasser, skal du køre følgende PowerShell-kommando:  `Get-Mailbox <identity of active mailbox> | FL Guid`. Kør denne kommando  `Get-Mailbox <identity of soft-deleted or inactive mailbox> -SoftDeletedMailbox | FL Guid`for at hente GUID'et for postkasser med blød sletning (eller inaktive).  <br/> | `annb@contoso.onmicrosoft.com` <br/> Eller  <br/>  `2d7a87fe-d6a2-40cc-8aff-1ebea80d4ae7` <br/> |
    | `IsArchive` <br/> | Angiver, om PST-filen skal importeres til brugerens arkivpostkasse. Der er to muligheder:  <br/><br/>**FALSK:** Importerer PST-filen til brugerens primære postkasse.  <br/> **SANDT:** Importerer PST-filen til brugerens arkivpostkasse. Dette forudsætter, at [brugerens arkivpostkasse er aktiveret](enable-archive-mailboxes.md). <br/><br/>Hvis du angiver denne parameter til  `TRUE` , og brugerens arkivpostkasse ikke er aktiveret, mislykkes importen for den pågældende bruger. Hvis en import mislykkes for én bruger (fordi vedkommendes arkiv ikke er aktiveret, og denne egenskab er angivet til  `TRUE`), påvirkes de andre brugere i importjobbet ikke.  <br/>  Hvis du lader denne parameter være tom, importeres PST-filen til brugerens primære postkasse.  <br/> <br/>**Bemærk:** Hvis du vil importere en PST-fil til en skybaseret arkivpostkasse for en bruger, hvis primære postkasse er i det lokale miljø, skal du blot angive  `TRUE` for denne parameter og angive mailadressen for brugerens lokale postkasse for  `Mailbox` parameteren.  <br/> | `FALSE` <br/> Eller  <br/>  `TRUE` <br/> |
    | `TargetRootFolder` <br/> | Angiver den postkassemappe, som PST-filen importeres til.  <br/> <br/> Hvis du lader denne parameter være tom, importeres PST-filen til en ny mappe med navnet **Importeret** på rodniveauet i postkassen (samme niveau som mappen Indbakke og de andre standardpostkassemapper).  <br/> <br/> Hvis du angiver  `/`, importeres mapperne og elementerne i PST-filen øverst i mappestrukturen i destinationspostkassen eller -arkivet. Hvis der findes en mappe i destinationspostkassen (f.eks. standardmapper, f.eks. Indbakke, Sendt post og Slettet post), flettes elementerne i den pågældende mappe i PST'en med den eksisterende mappe i målpostkassen. Hvis PST-filen f.eks. indeholder en indbakkemappe, importeres elementerne i den pågældende mappe til mappen Indbakke i målpostkassen. Der oprettes nye mapper, hvis de ikke findes i mappestrukturen for destinationspostkassen.  <br/><br/>  Hvis du angiver  `/<foldername>`, importeres elementer og mapper i PST-filen til en mappe med navnet  *\<foldername\>*  . Hvis du f.eks. bruger  `/ImportedPst`, importeres elementer til en mappe med navnet **ImportedPst**. Denne mappe placeres i brugerens postkasse på samme niveau som mappen Indbakke.  <br/><br/> **Tip:** Overvej at køre et par testbatch for at eksperimentere med denne parameter, så du kan bestemme den bedste mappeplacering til import af PST-filer.  <br/> |(lad argumentet være tomt)  <br/> Eller  <br/>  `/` <br/> Eller  <br/>  `/ImportedPst` <br/> |
    | `ContentCodePage` <br/> |Denne valgfri parameter angiver en numerisk værdi for den tegntabel, der skal bruges til import af PST-filer i ANSI-filformatet. Denne parameter bruges til at importere PST-filer fra kinesiske, japanske og koreanske (CJK) organisationer, fordi disse sprog typisk bruger et dobbeltbytetegnsæt (DBCS) til tegnkodning. Hvis denne parameter ikke bruges til at importere PST-filer til sprog, der bruger DBCS til postkassemappenavne, bliver mappenavnene ofte forvansket, når de er importeret.  <br/><br/> Du kan se en liste over understøttede værdier, der skal bruges til denne parameter, under [Tegntabel-id'er](/windows/win32/intl/code-page-identifiers).  <br/> <br/>**Bemærk:** Som tidligere angivet er dette en valgfri parameter, og du behøver ikke at inkludere den i CSV-filen. Du kan også inkludere den og lade værdien være tom for en eller flere rækker.  <br/> |(lad argumentet være tomt)  <br/> Eller  <br/>  `932` (som er tegntabel-id'et for ANSI/OEM Japansk)  <br/> |
    | `SPFileContainer` <br/> |Lad denne parameter være tom i forbindelse med PST-import.  <br/> |Ikke relevant  <br/> |
    | `SPManifestContainer` <br/> |Lad denne parameter være tom i forbindelse med PST-import.  <br/> |Ikke relevant  <br/> |
    | `SPSiteUrl` <br/> |Lad denne parameter være tom i forbindelse med PST-import.  <br/> |Ikke relevant  <br/> |

## <a name="step-5-create-a-pst-import-job"></a>Trin 5: Opret et PST-importjob

Det næste trin er at oprette PST-importjobbet i tjenesten Importér i Microsoft 365. Som tidligere forklaret skal du sende den PST-importtilknytningsfil, du oprettede i trin 4. Når du har oprettet jobbet, analyserer Microsoft 365 dataene i PST-filerne og giver dig derefter mulighed for at filtrere de data, der faktisk importeres til de postkasser, der er angivet i PST-importtilknytningsfilen (se [trin 6](#step-6-filter-data-and-start-the-pst-import-job)).
  
1. Gå til , <https://compliance.microsoft.com> og log på med legitimationsoplysningerne for en administratorkonto i din organisation.

2. I venstre rude på overholdelsesportalen skal du klikke på **Administration af datalivscyklus > Importér**.

3. Klik på ![Tilføj ikon under fanen **Importér**.](../media/ITPro-EAC-AddIcon.gif) **Nyt importjob**.

   > [!NOTE]
   > Du skal have tildelt de nødvendige tilladelser for at få adgang til siden **Importér** på overholdelsesportalen for at oprette et importjob. Se afsnittet **Før du importerer PST-filer** for at få flere oplysninger. 

4. Skriv et navn til PST-importjobbet, og klik derefter på **Næste**. Brug små bogstaver, tal, bindestreger og understregningstegn. Du kan ikke bruge store bogstaver eller medtage mellemrum i navnet.

5. På siden **Vil du overføre eller sende data? skal du** klikke på **Overfør dine data** og derefter klikke på **Næste**.
  
6. I trin 4 på siden **Importér data** skal du klikke på afkrydsningsfelterne **Jeg er færdig med at overføre mine filer** , og **jeg har adgang til tilknytningsfilen** og derefter klikke på **Næste**.

    ![Klik på de to afkrydsningsfelter i trin 4.](../media/9f2427e8-3af2-4e27-95e6-a9f08430d3d8.png)
  
7. På siden **Vælg tilknytningsfilen** skal du klikke på **Vælg tilknytningsfil** for at sende den CSV-tilknytningsfil, du oprettede i trin 4.

    ![Klik på Vælg tilknytningsfil for at sende den CSV-fil, du oprettede til importjobbet.](../media/d30b1d73-80bb-491e-a642-a21673d06889.png)
  
8. Når navnet på CSV-filen vises under **Tilknytning af filnavn**, skal du klikke på **Valider** for at kontrollere, om der er fejl i CSV-filen.

    ![Klik på Valider for at kontrollere, om der er fejl i CSV-filen.](../media/4680999d-5538-4059-b878-2736a5445037.png)
  
    CSV-filen skal valideres korrekt for at oprette et PST-importjob. Filnavnet ændres til grønt, når det er valideret. Hvis valideringen mislykkes, skal du klikke på linket **Vis log** . Der åbnes en valideringsfejlrapport med en fejlmeddelelse for hver række i filen, der mislykkedes.

   > [!NOTE]
   > Som tidligere forklaret kan en tilknytningsfil maksimalt have 500 rækker. Valideringen mislykkes, hvis tilknytningsfilen indeholder mere end 500 rækker. Hvis du vil importere mere end 500 PST-filer, skal du oprette flere tilknytningsfiler og flere importjob.

9. Når tilknytningsfilen er valideret, skal du læse dokumentet med vilkår og betingelser og derefter klikke på afkrydsningsfeltet.

10. Klik på **Gem** for at sende jobbet, og klik derefter på **Luk** , når jobbet er oprettet.

    Der vises en status-pop op-side med statussen **Analyse i gang** , og det nye importjob vises på listen på siden **Importér PST-filer** .

11. Klik på **opdateringsikonet**![.](../media/O365-MDM-Policy-RefreshIcon.gif) for at opdatere de statusoplysninger, der vises i kolonnen **Status** . Når analysen er fuldført, og dataene er klar til at blive importeret, ændres status til **Fuldført analyse**.

    Du kan klikke på importjobbet for at få vist status-pop op-siden, som indeholder mere detaljerede oplysninger om importjobbet, f.eks. status for hver PST-fil, der er angivet i tilknytningsfilen.

## <a name="step-6-filter-data-and-start-the-pst-import-job"></a>Trin 6: Filtrer data, og start PST-importjobbet

Når du har oprettet importjobbet i trin 5, analyserer Microsoft 365 dataene i PST-filerne (på en sikker og sikker måde) ved at identificere elementernes alder og de forskellige meddelelsestyper, der er inkluderet i PST-filerne. Når analysen er fuldført, og dataene er klar til import, har du mulighed for at importere alle dataene i PST-filerne, eller du kan trimme de data, der importeres, ved at angive filtre, der styrer, hvilke data der importeres.
  
1. Under fanen **Importér** i overholdelsesportalen skal du vælge de importjob, du oprettede i trin 5, og derefter klikke på **Importér til Microsoft 365**.
  
   Siden **Filtrer dine data** vises. Den indeholder dataindsigt som følge af den analyse, der er udført på PST-filerne af Microsoft 365, herunder oplysninger om dataenes alder. På dette tidspunkt har du mulighed for at filtrere de data, der importeres, eller importere alle dataene, som de er. 

    ![Du kan trimme dataene i PST-filerne eller importere dem alle.](../media/287fc030-99e9-417b-ace7-f64617ea5d4e.png)
  
2. Gør et af følgende:

   1. Hvis du vil trimme de data, du importerer, skal du klikke på **Ja. Jeg vil filtrere dem, før du importerer** dem.

      Du kan finde detaljerede trinvise instruktioner om filtrering af dataene i PST-filerne og derefter starte importjobbet under [Filtrer data, når du importerer PST-filer til Microsoft 365](filter-data-when-importing-pst-files.md).

      Eller

   2. Hvis du vil importere alle data i PST-filerne, skal du klikke på **Nej, jeg vil importere alt** og klikke på **Næste**.

3. Hvis du har valgt at importere alle dataene, skal du klikke på **Importér data** for at starte importjobbet. 

   Status for importjobbet vises på siden **Importér PST-filer** . Klik på ![ikonet Opdater.](../media/O365-MDM-Policy-RefreshIcon.gif) **Opdater** for at opdatere de statusoplysninger, der vises i kolonnen **Status** . Klik på importjobbet for at få vist status-pop op-siden, hvor der vises statusoplysninger om hver PST-fil, der importeres.

## <a name="more-information"></a>Flere oplysninger

- Hvorfor importere PST-filer til Microsoft 365?

  - Det er en god måde at importere din organisations arkiveringsmeddelelsesdata til Microsoft 365 på.

  - Dataene er tilgængelige for brugeren fra alle enheder, fordi de er gemt i cloudmiljøet.

  - Det hjælper med at imødekomme organisationens overholdelsesbehov ved at lade dig anvende Microsoft Purview-funktioner på dataene fra de PST-filer, du har importeret. Dette omfatter:

  - Aktivering af [arkivpostkasser](enable-archive-mailboxes.md) og [automatisk udvidelse af arkivering](enable-autoexpanding-archiving.md) for at give brugerne ekstra lagerplads i postkassen til at gemme de data, du har importeret.

  - Placering af postkasser i [procesventeposition](./create-a-litigation-hold.md) for at bevare de data, du har importeret.

  - Brug microsoft [eDiscovery-værktøjer](search-for-content.md) til at søge efter de data, du har importeret.

  - Brug af [politikker for opbevaring i Microsoft 365](retention.md) til at styre, hvor længe de data, du har importeret, bevares, og hvilken handling der skal udføres, når opbevaringsperioden udløber.

  - Søger i [overvågningsloggen](search-the-audit-log-in-security-and-compliance.md) efter postkasserelaterede hændelser, der påvirker de data, du har importeret.

  - Importerer data til [inaktive postkasser](inactive-mailboxes-in-office-365.md) for at arkivere data med henblik på overholdelse af angivne standarder. 

  - Brug af [politikker til forebyggelse af datatab](dlp-learn-about-dlp.md) for at forhindre, at følsomme data lækker uden for din organisation.

- Som tidligere forklaret aktiverer Microsoft 365-importtjenesten indstillingen for bevarelse af venteposition (i ubestemt varighed), når PST-filer importeres til en postkasse. Det betyder, at egenskaben  *RetentionHoldEnabled*  er angivet til  **Sand** , så den opbevaringspolitik, der er tildelt postkassen, ikke behandles. Dette giver ejeren af postkassen tid til at administrere de nyligt importerede meddelelser ved at forhindre, at en politik for sletning eller arkivering sletter eller arkiverer ældre meddelelser. Her er nogle trin, du kan udføre for at administrere denne opbevarings venteposition:

  - Efter et bestemt tidsrum kan du slå opbevaringsventetiden fra ved at køre kommandoen **Set-Mailbox -RetentionHoldEnabled $false** . Du kan finde instruktioner under [Placer en postkasse i opbevaringsventeposition](/exchange/security-and-compliance/messaging-records-management/mailbox-retention-hold).

  - Du kan konfigurere opbevarings ventepositionen, så den er slået fra på en dato i fremtiden. Det gør du ved at køre datokommandoen **Set-Mailbox -EndDateForRetentionHold**. Hvis du f.eks. antager, at dags dato er den 1. juni 2016, og du vil have bevarelseslagret slået fra om 30 dage, skal du køre følgende kommando:  **Set-Mailbox -EndDateForRetentionHold 7/1/2016**. I dette scenarie skal du lade egenskaben  **RetentionHoldEnabled**  være angivet til  *Sand*. Du kan få flere oplysninger under [Set-Mailbox](/powershell/module/exchange/set-mailbox).

  - Du kan ændre indstillingerne for den opbevaringspolitik, der er tildelt postkassen, så ældre elementer, der er importeret, ikke straks slettes eller flyttes til brugerens arkivpostkasse. Du kan f.eks. forlænge opbevaringsalderen for en politik for sletning eller arkivering, der er tildelt postkassen. I dette scenarie skal du deaktivere opbevaringsventepositionen på postkassen, når du har ændret indstillingerne for opbevaringspolitikken. Du kan få flere oplysninger under [Konfigurer en politik for arkiv og sletning for postkasser i din organisation](set-up-an-archive-and-deletion-policy-for-mailboxes.md).

### <a name="how-the-import-process-works"></a>Sådan fungerer importprocessen
  
Du kan bruge indstillingen til overførsel af netværk og tjenesten Microsoft 365 Import til masseimport af PST-filer til brugerpostkasser. Netværksupload betyder, at du uploader PST-filerne et midlertidigt lagerområde i Microsoft-cloudmiljøet. Derefter kopierer Microsoft 365-importtjenesten PST-filerne fra lagerområdet til destinationsbrugerpostkasserne.
  
Her er en illustration og beskrivelse af processen til netværksupload til import af PST-filer til postkasser i Microsoft 365.
  
![Arbejdsproces for processen til netværksupload til import af PST-filer til Microsoft 365.](../media/9e05a19e-1e7a-4f1f-82df-9118f51588c4.png)
  
1. **Download PST-importværktøjet og nøglen til en privat Azure Storage-placering:** Det første trin er at downloade kommandolinjeværktøjet AzCopy og en adgangsnøgle, der bruges til at uploade PST-filerne til en Azure Storage-placering i Microsoft-cloudmiljøet. Du henter disse fra siden **Importér** på overholdelsesportalen. Nøglen (kaldet en SAS-nøgle (Secure Access Signature) giver dig de nødvendige tilladelser til at uploade PST-filer til en privat og sikker Azure Storage-placering. Denne adgangsnøgle er unik for din organisation og hjælper med at forhindre uautoriseret adgang til dine PST-filer, når de er uploadet til Microsoft-cloudmiljøet. Import af PST-filer kræver ikke, at din organisation har et separat Azure-abonnement.

2. **Upload PST-filerne til Azure Storage-placeringen:** Det næste trin er at bruge værktøjet azcopy.exe (downloadet i trin 1) til at uploade og gemme dine PST-filer på en Azure Storage-placering, der er placeret i det samme regionale Microsoft-datacenter, hvor din organisation er placeret. Hvis du vil overføre dem, skal de PST-filer, du vil importere, være placeret i et filshare eller en filserver i din organisation.

    Der er et valgfrit trin, som du kan udføre for at få vist listen over PST-filer, når de er uploadet til Azure Storage-placeringen.

3. **Opret en PST-importtilknytningsfil:** Når PST-filerne er blevet uploadet til Azure Storage-placeringen, er næste trin at oprette en kommasepareret værdifil (CSV), der angiver, hvilke brugerpostkasser PST-filerne importeres til. Bemærk, at en PST-fil kan importeres til en brugers primære postkasse eller deres arkivpostkasse. Tjenesten Microsoft 365 Import bruger oplysningerne i CSV-filen til at importere PST-filerne.

4. **Opret et PST-importjob:** Det næste trin er at oprette et PST-importjob på siden **Importér PST-filer** på overholdelsesportalen og sende den PST-importtilknytningsfil, der blev oprettet i det forrige trin. Når du har oprettet importjobbet, analyserer Microsoft 365 dataene i PST-filerne og giver dig derefter mulighed for at angive filtre, der styrer, hvilke data der faktisk importeres til de postkasser, der er angivet i PST-importtilknytningsfilen.

5. **Filtrer de PST-data, der importeres til postkasser:** Når importjobbet er oprettet og startet, analyserer Microsoft 365 dataene i PST-filerne (sikkert og sikkert) ved at identificere elementernes alder og de forskellige meddelelsestyper, der er inkluderet i PST-filerne. Når analysen er fuldført, og dataene er klar til import, har du mulighed for at importere alle dataene i PST-filerne, eller du kan trimme de data, der importeres, ved at angive filtre, der styrer, hvilke data der importeres.

6. **Start PST-importjobbet:** Når importjobbet er startet, bruger Microsoft 365 oplysningerne i PST-importtilknytningsfilen til at importere PSTs-filerne fra Azure Storage-placeringen til brugerpostkasser. Statusoplysninger om importjobbet (herunder oplysninger om hver PST-fil, der importeres) vises på siden **Importér PST-filer** på overholdelsesportalen. Når importjobbet er afsluttet, angives status for jobbet til **Fuldført**.
