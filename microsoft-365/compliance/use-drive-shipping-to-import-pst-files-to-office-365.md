---
title: Brug drevforsendelse til at importere din organisations PST-filer
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
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 40829b57-793c-4d41-b171-e9270129173d
ms.custom: seo-marvel-apr2020
description: Administratoren kan lære, hvordan pst.-filer importeres Microsoft 365 postkasser ved at kopiere PST-filer til en harddisk og derefter sende dem til Microsoft.
ms.openlocfilehash: 2b0e6e08d6c324914aaf2fdd9ce24b9b55ca2d95
ms.sourcegitcommit: 36a19d80fe3f053df0fec398a7ff2dfc777f9730
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/30/2021
ms.locfileid: "63589533"
---
# <a name="use-drive-shipping-to-import-your-organizations-pst-files"></a>Brug drevforsendelse til at importere din organisations PST-filer

**Denne artikel gælder for administratorer. Forsøger du at importere PST-filer til din egen postkasse? Se [Importere mail, kontakter og kalender fra en Outlook .pst-fil](https://go.microsoft.com/fwlink/p/?LinkID=785075)**
   
Brug tjenesten Office 365 og drevforsendelse til masseimport af PST-filer til brugerpostkasser. Drevforsendelse betyder, at du kopierer PST-filerne til en harddisk og derefter fysisk sender drevet til Microsoft. Når Microsoft modtager din harddisk, kopierer datacentermedarbejderen dataene fra harddisken til et lagringsområde i Microsoft-skyen. Derefter har du mulighed for at trimme pst.-data, der importeres til destinationspostkasser, ved at angive filtre, der styrer, hvilke data der importeres. Når du starter importjobbet, importerer importtjenesten PST-data fra lagringsområdet til brugerpostkasserne. Brug af drevforsendelse til at importere PST-filer til brugerpostkasser er en måde at overføre din organisations mails Office 365.
  
Her er de trin, der kræves for at bruge drevforsendelse til at importere PST-filer Microsoft 365 postkasser:
  
[Trin 1: Download PST-importværktøjet](#step-1-download-the-pst-import-tool)

[Trin 2: Kopiér PST-filerne til harddisken](#step-2-copy-the-pst-files-to-the-hard-drive)

[Trin 3: Opret tilknytningsfilen til PST-import](#step-3-create-the-pst-import-mapping-file)

[Trin 4: Opret et PST-importjob i Office 365](#step-4-create-a-pst-import-job-in-office-365)

[Trin 5: Send harddisken til Microsoft](#step-5-ship-the-hard-drive-to-microsoft)

[Trin 6: Filtrer data, og start PST-importjobbet](#step-6-filter-data-and-start-the-pst-import-job)
  
> [!IMPORTANT]
> Du skal udføre trin 1 én gang for at hente importværktøjet. Når du har udført disse trin, skal du følge trin 2 til 6, hver gang du vil sende en harddisk til Microsoft. 
  
For ofte stillede spørgsmål om brug af drevforsendelse til at importere PST-filer Office 365, se Ofte stillede spørgsmål om brug af [drevforsendelse til at importere PST-filer](./faqimporting-pst-files-to-office-365.yml#using-drive-shipping-to-import-pst-files). 
  
## <a name="before-you-import-pst-files"></a>Før du importerer PST-filer

- Du skal have tildelt rollen Postkasse Import Eksport i Exchange Online for at oprette importjob i Microsoft 365 Overholdelsescenter og importere PST-filer til brugerpostkasser. Som standard er denne rolle ikke tildelt nogen rollegruppe i Exchange Online. Du kan føje rollen Postkasse Import Eksport til rollegruppen Organisationsadministration. Eller du kan oprette en rollegruppe, tildele rollen Postkasse Import Eksport og derefter tilføje dig selv som medlem. Du kan finde flere oplysninger i afsnittene "Føj en rolle til en rollegruppe" eller "Opret en rollegruppe" i [Administrer rollegrupper](/Exchange/permissions-exo/role-groups).

    Ud over rollen Postkasse Import Eksport skal du også have tildelt rollen Postmodtagere i Exchange Online. Som standard er denne rolle tildelt rollegrupperne Organisationsadministration og Modtageradministration i Exchange Online.

    > [!TIP]
    > Overvej at oprette en ny rollegruppe Exchange Online, der specifikt er beregnet til import af PST-filer til Office 365. For det mindste niveau af rettigheder, der kræves for at importere PST-filer, skal du tildele rollerne Postkasse Import Eksport og Postmodtagere til den nye rollegruppe og derefter tilføje medlemmer.
  
- Du skal gemme de PST-filer, du vil kopiere, til en harddisk på en filserver eller en delt mappe i organisationen. I trin 2 kører du værktøjet Azure Import Export (WAImportExport.exe), der kopierer de PST-filer, der er gemt på denne filserver eller delte mappe, til harddisken.

- Store PST-filer kan påvirke ydeevnen for PST-importprocessen. Derfor anbefaler vi, at hver enkelt PST-fil, du kopierer til harddisken i trin 2, ikke må være større end 20 GB.

- Kun 2,5" solid state-drev (SSD'er) eller 2,5" eller 3,5" SATA II/III-interne harddiske er understøttet til brug sammen med Office 365-importtjenesten. Du kan bruge harddiske op til 10 TB. I forbindelse med importjob vil kun den første datamængde på harddisken blive behandlet. Datamængden skal være formateret med NTFS. Når du kopierer data til en harddisk, kan du tilslutte den direkte ved hjælp af en 2,5 tommer SSD- eller 2,5 tommer eller 3,5 tommer SATA II/III-forbindelse, eller du kan tilslutte den eksternt ved hjælp af en ekstern 2,5-tommer SSD eller 2,5 tommer eller 3,5 tommer SATA II/III USB-adapter.
    
    > [!IMPORTANT]
    > Eksterne harddiske, der indeholder en indbygget USB-adapter, understøttes ikke af Office 365 Import. Derudover kan disken i kassen på en ekstern harddisk ikke bruges. Send ikke eksterne harddiske. 
  
- Den harddisk, du kopierer PST-filerne til, skal være krypteret med BitLocker. Det WAImportExport.exe værktøj, du kører i trin 2, hjælper dig med at konfigurere BitLocker. Den genererer også en BitLocker-krypteringsnøgle, som microsofts datacentermedarbejder bruger til at få adgang til drevet for at overføre PST-filerne til Azure Storage-området i Microsoft-skyen.
    
- Drevforsendelse fås via en Microsoft Enterprise Agreement (EA). Drevforsendelse fås ikke gennem en Aftale om Microsoft-produkter og -tjenester (MPSA).
    
- Prisen for at importere PST-filer til Microsoft 365-postkasser ved hjælp af drevforsendelse er 2 USD pr. GB data. Hvis du f.eks. sender en harddisk, der indeholder 1.000 GB (1 TB) PST-filer, koster det 2.000 USD. Du kan arbejde sammen med en partner om at betale importgebyret. Hvis du vil have mere at vide om at finde en partner, [skal du se Find din Microsoft-partner eller -forhandler](../admin/manage/find-your-partner-or-reseller.md).
    
- Du eller din organisation skal have en konto hos FedEx eller DHL.
    
  - Organisationer i USA, Brasilien og Europa skal have FedEx-konti.
    
  - Organisationer i Østasien, Sydøstasien, Japan, Republikken Korea og Australien skal have DHL-konti.
    
    Microsoft bruger (og opkræver) denne konto for at returnere harddisken tilbage til dig.
    
- Harddisken, som du sender til Microsoft, kan krydse internationale grænser. I dette tilfælde er du ansvarlig for at sikre, at harddisken og de data, den indeholder, importeres og/eller eksporteres i overensstemmelse med gældende lovgivning. Før du sender en harddisk, skal du kontakte dine rådgivere for at bekræfte, at dit drev og data kan sendes til det identificerede Microsoft-datacenter på lovlig vis. Dette hjælper med at sikre, at den når rettidigt frem til Microsoft.
    
- Denne fremgangsmåde indebærer kopiering og lagring af en BitLocker-krypteringsnøgle. Sørg for at træffe forholdsregler for at beskytte disse nøgler, på samme måde som du beskytter adgangskoder eller andre sikkerhedsrelaterede oplysninger. Du kan f.eks. gemme dem i et adgangskodebeskyttet dokument Microsoft Word eller gemme dem på et krypteret USB-drev. Se afsnittet [Flere oplysninger](#more-information) for at få et eksempel på disse nøgler. 
    
- Når PST-filer importeres Microsoft 365 en postkasse, er indstillingen for opbevaring af postkassen aktiveret på ubestemt tid. Det betyder, at den opbevaringspolitik, der er tildelt til postkassen, ikke behandles, før du deaktiverer opbevaringspositionen eller angiver en dato for at deaktivere ventepositionen. Hvorfor gør vi dette? Hvis meddelelser, der importeres til en postkasse, er gamle, kan de blive slettet permanent (slettet), fordi deres opbevaringsperiode er udløbet baseret på de opbevaringsindstillinger, der er konfigureret for postkassen. Når du sætter postkassen i venteposition, får postkassens ejer tid til at administrere disse nyligt importerede meddelelser, eller der gives tid til at ændre opbevaringsindstillingerne for postkassen. Se afsnittet [Flere oplysninger for](#more-information) at få forslag til administration af opbevaringspositionen. 
    
- Som standard er den maksimale meddelelsesstørrelse, der kan modtages af Microsoft 365 postkasse, 35 MB. Det skyldes, at standardværdien for  *egenskaben MaxReceiveSize*  for en postkasse er angivet til 35 MB. Men grænsen for den maksimale størrelse for modtagelse af meddelelser i Microsoft 365 er 150 MB. Så hvis du importerer en PST-fil, der indeholder et element, der er større end 35 MB, ændrer tjenesten Office 365-import automatisk værdien af *egenskaben MaxReceiveSize* på målpostkassen til 150 MB. Dette giver mulighed for at importere meddelelser på op til 150 MB til brugerpostkasser. 
    
    > [!TIP]
    > For at identificere meddelelsens modtagelsesstørrelse for en postkasse kan du køre denne kommando i Exchange Online PowerShell: `Get-Mailbox <user mailbox> | FL MaxReceiveSize`. 
  
- Du kan importere PST-filer til en inaktiv postkasse i Office 365. Det gør du ved at angive GUID'et for den inaktive postkasse i  `Mailbox` parameteren i PST-importtilknytningsfilen. Se [Trin 3: Opret PST-importtilknytningsfilen](#step-3-create-the-pst-import-mapping-file) for at få flere oplysninger. 
    
- I en Exchange-hybridinstallation kan du importere PST-filer til en skybaseret arkivpostkasse for en bruger, hvis primære postkasse er lokal. Det gør du ved at gøre følgende i PST-importtilknytningsfilen:
    
  - Angiv mailadressen til brugerens lokale postkasse i  `Mailbox` parameteren. 
    
  - Angiv værdien **SAND** i  `IsArchive` parameteren. 
    
    Se [Trin 3: Opret PST-importtilknytningsfilen](#step-3-create-the-pst-import-mapping-file) for at få flere oplysninger. 

## <a name="step-1-download-the-pst-import-tool"></a>Trin 1: Download PST-importværktøjet

Det første trin er at downloade værktøjet, og at du bruger i trin 2 til at kopiere PST-filer til harddisken.
  
> [!IMPORTANT]
> Du skal bruge Azure Import/Export-værktøjet version 1 (WAimportExportV1) til at importere PST-filer ved hjælp af drevforsendelsesmetoden. Version 2 af Azure Import/Export-værktøjet understøttes ikke, og hvis du bruger det, forberedes harddisken til importjobbet forkert. Sørg for at downloade Azure Import/Export-værktøjet fra Microsoft 365 Overholdelsescenter ved at følge fremgangsmåden i dette trin. 
  
1. Gå til <https://compliance.microsoft.com> og log på med legitimationsoplysningerne til en administratorkonto i organisationen.

2. Klik på Microsoft 365 Overholdelsescenter **navigationsimport i venstre navigationsrude**\>.
    
    > [!NOTE]
    > Som tidligere nævnt skal du have tildelt de relevante tilladelser for at få adgang **til siden Import** i Microsoft 365 Overholdelsescenter. 
  
3. Klik på **Tilføj** ikon under ![fanen Importér.](../media/ITPro-EAC-AddIcon.gif) **Nyt importjob**.
    
4. Skriv et navn til PST-importjobbet i guiden Importér job, og klik derefter på **Næste**. Brug små bogstaver, tal, bindestreger og understregningstegn. Du må ikke bruge store bogstaver eller medtage mellemrum i navnet.
    
5. På siden **Vælg import af jobtype** skal du klikke **på Send harddiske til en af vores fysiske placeringer,** og klik derefter på **Næste**.
    
    ![Klik på Send harddiske til en af vores fysiske placeringer for at oprette et drevforsendelsesimportjob.](../media/1584fdc5-cd4c-4e47-932e-db6c8e07f5f8.png)
  
6. Gør **følgende på** siden Importér data:     
    
    **Download Azure Import/Export værktøjet til** at downloade og installere værktøjet Azure Import/Export (version 1).
    
    - I pop op-vinduet skal du klikke **på** \> **Gem Gem som** for at WaImportExportV1.zip filen i en mappe på din lokale computer. 
    
    - Udtræk WaImportExportV1.zip fil.
    
7. Klik **på Annuller** for at lukke guiden. 
    
    Du vender tilbage til **siden Importér** i Microsoft 365 Overholdelsescenter når du opretter importjobbet i trin 4. 

## <a name="step-2-copy-the-pst-files-to-the-hard-drive"></a>Trin 2: Kopiér PST-filerne til harddisken

Næste trin er at bruge værktøjet WAImportExport.exe kopiere PST-filer til harddisken. Dette værktøj krypterer harddisken med BitLocker, kopierer PST'erne til harddisken og opretter en journalfil, der gemmer oplysninger om kopiprocessen. For at fuldføre dette trin skal PST-filerne være placeret i et filshare eller en filserver i din organisation. Dette kaldes kildemappen i følgende procedure. 

 Som nævnt tidligere må hver PST-fil, du kopierer til harddisken, ikke være større end 20 GB. PST-filer, der er større end 20 GB, kan påvirke ydeevnen af PST-importprocessen, som du starter i trin 6.
  
> [!IMPORTANT]
> Når du kører værktøjet WAImportExport.exe for en harddisk, skal du bruge en anden syntaks hver gang derefter. Denne syntaks forklares i trin 4 i denne fremgangsmåde for at kopiere PST-filer til harddisken. 
  
1. Åbn en kommandoprompt på din lokale computer.
    
    > [!TIP]
    > Hvis du kører kommandoprompten som administrator (ved at vælge "Kør som administrator", når du åbner den), vises fejlmeddelelser i kommandopromptvinduet. Dette kan hjælpe dig med at foretage fejlfinding af problemer med at WAImportExport.exe værktøjet. 
  
2. Gå til den mappe, hvor du installerede WAImportExport.exe i trin 1.
    
3. Kør følgende kommando første gang, du bruger kommandoen WAImportExport.exe til at kopiere PST-filer til en harddisk.

    ```powershell
    WAImportExport.exe PrepImport /j:<Name of journal file> /t:<Drive letter> /id:<Name of session> /srcdir:<Location of PST files> /dstdir:<PST file path> /blobtype:BlockBlob /encrypt /logdir:<Log file location>
    ```

    I følgende tabel beskrives parametrene og de påkrævede værdier.
    
    |**Parameter**|**Beskrivelse**|**Eksempel**|
    |:-----|:-----|:-----|
    | `/j:` <br/> |Angiver navnet på journalfilen. Denne fil gemmes i den samme mappe, hvor WAImportExport.exe findes. Hver harddisk, du sender til Microsoft, skal have én journalfil. Hver gang du kører WAImportTool.exe at kopiere PST-filer til en harddisk, føjes oplysninger til journalfilen for det pågældende drev.  <br/> Microsoft-datacentermedarbejdere bruger oplysningerne i journalfilen til at knytte harddisken til det importjob, du opretter i trin 4, og til at overføre PST-filerne til Azure Storage-området i Microsoft-skyen.  <br/> | `/j:PSTHDD1.jrn` <br/> |
    | `/t:` <br/> |Angiver drevbogstavet på harddisken, når den er sluttet til din lokale computer.  <br/> | `/t:h` <br/> |
    | `/id:` <br/> |Angiver navnet på kopisessionen. En session defineres som, hver gang du kører WAImportExport.exe for at kopiere filer til harddisken. PST-filerne kopieres til en mappe med navnet på sessionen, som er angivet af denne parameter.  <br/> | `/id:driveship1` <br/> |
    | `/srcdir:` <br/> |Angiver den kildemappe i organisationen, der indeholder de PST-filer, der kopieres under sessionen. Sørg for at omgive værdien af denne parameter med dobbelte anførselstegn (" ").  <br/> | `/srcdir:"\\FILESERVER01\PSTs"` <br/> |
    | `/dstdir:` <br/> |Angiver destinationsmappen i Azure Storage i Microsoft-skyen, hvor PST'erne overføres. Du skal bruge værdien  `ingestiondata/`. Sørg for at omgive værdien af denne parameter med dobbelte anførselstegn (" ").  <br/> Du kan også føje en ekstra filsti til værdien af denne parameter. Du kan f.eks. bruge filstien fra kildemappen på harddisken (konverteret til ET URL-format), som er angivet i  `/srcdir:` parameteren. Ændres  `\\FILESERVER01\PSTs` f.eks. til  `FILESERVER01/PSTs`. I dette tilfælde skal du stadig medtage den  `ingestiondata` i filstien. Så i dette eksempel er værdien for  `/dstdir:` parameteren  `"ingestiondata/FILESERVER01/PSTs"`.  <br/> En grund til at tilføje den ekstra filsti er, hvis du har PST-filer med samme filnavn.  <br/> > [!NOTE]> Hvis du medtager det valgfrie stinavn, omfatter navneområdet for en PST-fil, når den er uploadet til området Azure Storage, stinavn og navnet på PST-filen, f.eks. `FILESERVER01/PSTs/annb.pst`. Hvis du ikke medtager et stinavn, er navneområdet kun PST-filnavnet. for eksempel  `annb.pst`.           | `/dstdir:"ingestiondata/"` <br/> Eller  <br/>  `/dstdir:"ingestiondata/FILESERVER01/PSTs"` <br/> |
    | `/blobtype:` <br/> |Angiver typen af blobs i Azure Storage at importere PST-filerne til. Til import af PST-filer skal du bruge **værdien BlockBlob**. Denne parameter er påkrævet.   <br/> | `/blobtype:BlockBlob` <br/> |
    | `/encrypt` <br/> |Denne kontakt aktiverer BitLocker til på harddisken. Denne parameter er påkrævet, første gang du kører WAImportExport.exe værktøjet.  <br/> BitLocker-krypteringsnøglen kopieres til journalfilen og den logfil, der oprettes, hvis du bruger  `/logfile:` parameteren. Som beskrevet tidligere gemmes journalfilen i den samme mappe, hvor WAImportExport.exe er placeret.  <br/> | `/encrypt` <br/> |
    | `/logdir:` <br/> |Denne valgfri parameter angiver en mappe at gemme logfiler i. Hvis det ikke er angivet, gemmes logfilerne i den samme mappe, hvor WAImportExport.exe er placeret. Sørg for at omgive værdien af denne parameter med dobbelte anførselstegn (" ").  <br/> | `/logdir:"c:\users\admin\desktop\PstImportLogs"` <br/> |
   
    Her er et eksempel på syntaksen for værktøjet WAImportExport.exe brug af faktiske værdier for hver parameter:
    
    ```powershell
    WAImportExport.exe PrepImport /j:PSTHDD1.jrn /t:f /id:driveship1 /srcdir:"\\FILESERVER01\PSTs" /dstdir:"ingestiondata/" blobtype:BlockBlob /encrypt /logdir:"c:\users\admin\desktop\PstImportLogs"
    ```

    Når du har kørt kommandoen, vises der statusmeddelelser, der viser status for kopiering af PST-filer til harddisken. En endelig statusmeddelelse viser det samlede antal filer, der blev kopieret.
    
4. Kør denne kommando, hver gang du efterfølgende kører værktøjet WAImportExport.ext for at kopiere PST-filer til den samme harddisk.

    ```powershell
    WAImportExport.exe PrepImport /j:<Name of journal file> /id:<Name of new session> /srcdir:<Location of PST files> /dstdir:<PST file path> /blobtype:BlockBlob 
    ```

    Her er et eksempel på syntaksen for efterfølgende sessioner med henblik på at kopiere PST-filer til den samme harddisk.

    ```powershell
    WAImportExport.exe PrepImport /j:PSTHDD1.jrn /id:driveship2 /srcdir:"\\FILESERVER01\PSTs\SecondBatch" /dstdir:"ingestiondata/" /blobtype:BlockBlob
    ```

## <a name="step-3-create-the-pst-import-mapping-file"></a>Trin 3: Opret tilknytningsfilen til PST-import

Når en medarbejder i Microsofts datacenter har uploadet PST-filerne fra harddisken til Azure Storage-området, bruger importtjenesten oplysningerne i PST-importtilknytningsfilen, som er en kommasepareret fil (CSV), der angiver, hvilke brugerpostkasser PST-filerne importeres til. Du skal sende denne CSV-fil i næste trin, når du opretter et PST-importjob.
  
1. [Download en kopi af PST-importtilknytningsfilen](https://go.microsoft.com/fwlink/p/?LinkId=544717).
    
2. Åbn eller gem CSV-filen på din lokale computer. I følgende eksempel vises en fuldført PST-importtilknytningsfil (åbnet i Notesblok). Det er meget nemmere at bruge Microsoft Excel at redigere CSV-filen.

    ```text
    Workload,FilePath,Name,Mailbox,IsArchive,TargetRootFolder,ContentCodePage,SPFileContainer,SPManifestContainer,SPSiteUrl
    Exchange,FILESERVER01/PSTs,annb.pst,annb@contoso.onmicrosoft.com,FALSE,/,,,,
    Exchange,FILESERVER01/PSTs,annb_archive.pst,annb@contoso.onmicrosoft.com,TRUE,/ImportedPst,,,,
    Exchange,FILESERVER01/PSTs,donh.pst,donh@contoso.onmicrosoft.com,FALSE,/,,,,
    Exchange,FILESERVER01/PSTs,donh_archive.pst,donh@contoso.onmicrosoft.com,TRUE,/ImportedPst,,,,
    Exchange,FILESERVER01/PSTs,pilarp.pst,pilarp@contoso.onmicrosoft.com,FALSE,/,,,,
    Exchange,FILESERVER01/PSTs,pilarp_archive.pst,pilarp@contoso.onmicrosoft.com,TRUE,/ImportedPst,,,,
    Exchange,,tonyk.pst,tonyk@contoso.onmicrosoft.com,FALSE,/,,,,
    Exchange,,tonyk_archive.pst,tonyk@contoso.onmicrosoft.com,TRUE,,,,,
    Exchange,,zrinkam.pst,zrinkam@contoso.onmicrosoft.com,FALSE,/,,,,
    Exchange,,zrinkam_archive.pst,zrinkam@contoso.onmicrosoft.com,TRUE,,,,,
    ```

    Den første række (eller kolonneoverskriften) i CSV-filen viser de parametre, der skal bruges af PST-importtjenesten til at importere PST-filer til brugerpostkasser. Hvert parameternavn er adskilt af et komma. Hver række under kolonneoverskriften repræsenterer parameterværdierne for import af en PST-fil til en bestemt postkasse. Du skal bruge en række for hver PST-fil, der blev kopieret til harddisken. Sørg for at erstatte pladsholderdataene i tilknytningsfilen med de faktiske data.

    > [!NOTE]
    > Du skal ikke ændre noget i kolonneoverskriften, herunder SharePoint parametrene, de ignoreres under PST-importprocessen. 
  
3. Brug oplysningerne i følgende tabel til at udfylde CSV-filen med de nødvendige oplysninger.
    
    |**Parameter**|**Beskrivelse**|**Eksempel**|
    |:-----|:-----|:-----|
    | `Workload` <br/> |Angiver den tjeneste, data importeres til. Hvis du vil importere PST-filer til brugerpostkasser, skal du bruge  `Exchange`.  <br/> | `Exchange` <br/> |
    | `FilePath` <br/> | Angiver mappeplaceringen i Azure Storage, som PST-filer kopieres til, når harddisken sendes til Microsoft.  <br/>  Hvad du tilføjer i denne kolonne i CSV-filen, afhænger af, hvad du har angivet for  `/dstdir:` parameteren i forrige trin. Hvis du har undermapper på kildeplaceringen, `FilePath` skal værdien i parameteren indeholde den relative sti til undermappen, f.eks. /folder1/user1/.  <br/>  Hvis du har brugt  `/dstdir:"ingestiondata/"`, skal du lade denne parameter være tom i CSV-filen.  <br/>  Hvis du har inkluderet et valgfrit stinavn for  `/dstdir:` værdien af parameteren (  `/dstdir:"ingestiondata/FILESERVER01/PSTs"`f.eks. , skal du bruge det pågældende stinavn (ikke inklusive "ingestiondata") for denne parameter i CSV-filen. Der er store og små bogstaver i værdien for denne parameter.  <br/>  Uanset hvad  *, skal du ikke*  medtage "ingestiondata" i værdien for  `FilePath` parameteren. Lad denne parameter være tom, eller angiv kun det valgfrie stinavn.  <br/> > [!IMPORTANT]> Tilfældet med filnavnet skal være det samme, som du angav i parameteren i  `/dstdir:` forrige trin. Hvis du f.eks  `"ingestiondata/FILESERVER01/PSTs"` . brugte navnet på undermappen i det forrige trin,  `fileserver01/psts`  `FilePath` men derefter brugte i parameteren i CSV-filen, vil importen til PST-filen mislykkes. Sørg for at bruge den samme sag i begge forekomster.           |(lad feltet være tomt)  <br/> Eller  <br/>  `FILESERVER01/PSTs` <br/> |
    | `Name` <br/> |Angiver navnet på den PST-fil, der importeres til brugerpostkassen. Der er store og små bogstaver i værdien for denne parameter.  <br/> > [!IMPORTANT]> Tilfældet med PST-filnavnet i CSV-filen skal være den samme som den PST-fil, der blev uploadet til den Azure Storage placering i trin 2. Hvis du f.eks  `annb.pst`  `Name` . bruger i parameteren i CSV-filen, men navnet på den faktiske PST-fil  `AnnB.pst`er , så mislykkes importen for den pågældende PST-fil. Sørg for, at navnet på PST-filen i CSV-filen bruger det samme tilfælde som den faktiske PST-fil.           | `annb.pst` <br/> |
    | `Mailbox` <br/> |Angiver mailadressen på den postkasse, som PST-filen importeres til. Du kan ikke angive en offentlig mappe, fordi PST-importtjenesten ikke understøtter import af PST-filer til offentlige mapper.  <br/> Hvis du vil importere en PST-fil til en inaktiv postkasse, skal du angive postkasse-GUID'et for denne parameter. For at få dette GUID skal du køre følgende PowerShell-kommando i Exchange Online:`Get-Mailbox <identity of inactive mailbox> -InactiveMailboxOnly | FL Guid` <br/> > [!NOTE]> Nogle gange kan du have flere postkasser med den samme mailadresse, hvor den ene postkasse er en aktiv postkasse, og den anden postkasse er i en blød-slettet (eller inaktiv) tilstand. I disse situationer skal du angive postkasse-GUID'et for entydigt at identificere postkassen, som PST-filen skal importeres til. For at få dette GUID til aktive postkasser skal du køre følgende PowerShell-kommando:  `Get-Mailbox <identity of active mailbox> | FL Guid`. For at få GUID'et til blød-slettede (eller inaktive) postkasser skal du køre denne kommando:  `Get-Mailbox <identity of soft-deleted or inactive mailbox> -SoftDeletedMailbox | FL Guid`.           | `annb@contoso.onmicrosoft.com` <br/> Eller  <br/>  `2d7a87fe-d6a2-40cc-8aff-1ebea80d4ae7` <br/> |
    | `IsArchive` <br/> | Angiver, om PST-filen skal importeres til brugerens arkivpostkasse. Der er to muligheder:  <br/> **FALSK** Importerer PST-filen til brugerens primære postkasse.  <br/> **SAND** Importerer PST-filen til brugerens arkivpostkasse. Her antages det [, at brugerens arkivpostkasse er aktiveret](enable-archive-mailboxes.md). Hvis du indstiller denne parameter til  `TRUE` , og brugerens arkivpostkasse ikke er aktiveret, så mislykkes importen for den pågældende bruger. Hvis en import mislykkes for én bruger (  `TRUE`fordi brugerens arkiv ikke er aktiveret, og denne egenskab er angivet til ), påvirkes de andre brugere i importjobbet ikke.  <br/>  Hvis du lader denne parameter være tom, importeres PST-filen til brugerens primære postkasse.  <br/> **Bemærk!** Hvis du vil importere en PST-fil til en skybaseret arkivpostkasse for en bruger, hvis primære postkasse er lokal,  `TRUE` skal du blot angive for denne parameter og angive mailadressen til brugerens lokale postkasse for  `Mailbox` parameteren.  <br/> | `FALSE` <br/> Eller  <br/>  `TRUE` <br/> |
    | `TargetRootFolder` <br/> | Angiver den postkassemappe, pst.-filen importeres til.  <br/>  Hvis du lader denne parameter være tom, importeres PST-filen til en ny mappe  med navnet Importeret, som er placeret på postkassens rodniveau (det samme niveau som mappen Indbakke og de andre standardpostkassemapper).  <br/>  Hvis du angiver  `/`, importeres elementer i PST-filen direkte til brugerens indbakkemappe.  <br/>  Hvis du angiver  `/<foldername>`, importeres elementer i PST-filen til en mappe med navnet  *\<foldername\>*. Hvis du f.eks. bruger  `/ImportedPst`, importeres elementer til en mappe med navnet **ImportedPst**. Denne mappe vil være placeret i brugerens postkasse på samme niveau som mappen Indbakke.  <br/> |(lad feltet være tomt)  <br/> Eller  <br/>  `/` <br/> Eller  <br/>  `/ImportedPst` <br/> |
    | `ContentCodePage` <br/> |Denne valgfri parameter angiver en numerisk værdi for den kodeside, der skal bruges til at importere PST-filer i ANSI-filformatet. Denne parameter bruges til at importere PST-filer fra kinesiske, japanske og koreanske (CJK) organisationer, fordi disse sprog typisk bruger dobbelt byte tegnsæt (DBCS) til tegnkodning. Hvis denne parameter ikke bruges til at importere PST-filer for sprog, der bruger DBCS til postkassemappenavne, er mappenavnene ofte forvanslede, når de er importeret.  <br/> Du kan finde en liste over understøttede værdier, der skal bruges til denne parameter, under [Kodesideidentifikatorer](/windows/win32/intl/code-page-identifiers).  <br/> > [!NOTE]> Som nævnt tidligere er dette en valgfri parameter, og du behøver ikke at medtage den i CSV-filen. Eller du kan medtage den og lade værdien være tom for en eller flere rækker.           |(lad feltet være tomt)  <br/> Eller  <br/>  `932` (som er kodesidens identifikator for JAPANSK ANSI/OEM)  <br/> |
    | `SPFileContainer` <br/> |I forbindelse med PST-import skal du lade denne parameter være tom.  <br/> |Ikke relevant  <br/> |
    | `SPManifestContainer` <br/> |I forbindelse med PST-import skal du lade denne parameter være tom.  <br/> |Ikke relevant  <br/> |
    | `SPSiteUrl` <br/> |I forbindelse med PST-import skal du lade denne parameter være tom.  <br/> |Ikke relevant  <br/> |

## <a name="step-4-create-a-pst-import-job-in-office-365"></a>Trin 4: Opret et PST-importjob i Office 365

Næste trin er at oprette PST-importjobbet i importtjenesten i Office 365. Som beskrevet tidligere indsender du den PST-importtilknytningsfil, du oprettede i trin 3. Når du har oprettet jobbet, bruger importtjenesten oplysningerne i tilknytningsfilen til at importere PST-filerne til den angivne brugerpostkasse, når PST-filerne er kopieret fra harddisken til Azure Storage-området, og du opretter og starter importjobbet.
  
1. Gå til <https://compliance.microsoft.com> og log på med legitimationsoplysningerne til en administratorkonto i organisationen.

2. Klik på Microsoft 365 Overholdelsescenter **navigationsimport i venstre navigationsrude**\>.

3. Klik på **Tilføj** ikon under ![fanen Importér.](../media/ITPro-EAC-AddIcon.gif) **Nyt importjob**.

    > [!NOTE]
    > Som tidligere nævnt skal du have tildelt de relevante tilladelser for at få adgang **til siden Import** i Microsoft 365 Overholdelsescenter.
  
4. Skriv et navn til PST-importjobbet, og klik derefter på **Næste**. Brug små bogstaver, tal, bindestreger og understregningstegn. Du må ikke bruge store bogstaver eller medtage mellemrum i navnet.

5. På siden **Vælg import af jobtype** skal du klikke **på Send harddiske til en af vores fysiske placeringer,** og klik derefter på **Næste**.
  
6. I trin 6 skal du klikke på  afkrydsningsfelterne Jeg har forberedt mine harddiske og har adgang til de nødvendige drevjournalfiler, og jeg har adgang til afkrydsningsfeltet for tilknytningsfilen og derefter klikke på **Næste**.

    ![Klik på de to afkrydsningsfelter i trin 6.](../media/fad43078-ea68-4acd-b2ed-75a800183262.png)
  
7. På siden **Vælg drevfil skal** du klikke på Vælg **drevfil** og derefter gå til den samme mappe, hvor WAImportExport.exe findes. Journalfilen, der blev oprettet i trin 2, blev kopieret til denne mappe.

    ![Klik på Vælg drevfil for at sende den journalfil, der blev oprettet, da du kørte WAImportExport.exe værktøj.](../media/1ea35c04-bd88-4d7e-b7d9-dc390149d94f.png)
  
8. Vælg journalfilen. f.eks. `PSTHDD1.jrn`.

    > [!TIP]
    > Da du kørte WAImportExport.exe i trin 2, blev navnet på journalfilen angivet af  `/j:` parameteren.
  
9. Når navnet på drevfilen vises under Drevfilnavn, **skal du klikke** på **Valider** for at kontrollere drevfilen for fejl.

    ![Klik på Valider for at validere den drevfil, du har valgt.](../media/4b707f5a-152a-4e74-b9f5-449c88d1fec4.png)
  
    Drevfilen skal bekræftes for at kunne oprette et PST-importjob. Filnavnet ændres til grønt, når det er blevet valideret. Hvis valideringen mislykkes, skal du klikke **på linket Vis** log. Der åbnes en valideringsfejlrapport med en fejlmeddelelse med oplysninger om, hvorfor filen mislykkedes. 

    > [!NOTE]
    > Du skal tilføje og validere en journalfil for hver harddisk, du sender til Microsoft. 
  
10. Når du har tilføjet og valideret en journalfil for hver harddisk, du sender til Microsoft, skal du klikke på **Næste**.
    
11. Klik ![på Tilføj ikon.](../media/ITPro-EAC-AddIcon.gif) **Vælg tilknytningsfil** for at sende den PST-importtilknytningsfil, du oprettede i trin 3. 

    ![Klik på Vælg tilknytningsfil for at sende den CSV-fil, du har oprettet til importjobbet.](../media/d30b1d73-80bb-491e-a642-a21673d06889.png)
  
12. Når navnet på CSV-filen vises under Navnet på **tilknytningsfilen, skal** du klikke på **Valider** for at kontrollere CSV-filen for fejl. 

    ![Klik på Valider for at kontrollere, om der er fejl i CSV-filen.](../media/4680999d-5538-4059-b878-2736a5445037.png)
  
    CSV-filen skal bekræftes for at kunne oprette et PST-importjob. Filnavnet ændres til grønt, når det er blevet valideret. Hvis valideringen mislykkes, skal du klikke **på linket Vis** log. Der åbnes en valideringsfejlrapport med en fejlmeddelelse for hver række i filen, der mislykkedes. 

13. Klik på Næste, når PST-tilknytningsfilen er blevet **valideret**.

14. På siden **Angiv kontaktoplysninger** skal du skrive dine kontaktoplysninger i de relevante felter. 

    Adressen på den Microsoft-placering, du sender dine harddiske til, vises. Denne adresse genereres automatisk baseret på din Microsoft-datacenterplacering. Kopiér denne adresse til en fil, eller tag et skærmbillede.

15. Læs dokumentet med vilkår og betingelser, klik på afkrydsningsfeltet, og klik derefter på **Gem for** at sende importjobbet. 

    Når importjobbet er oprettet, vises en statusside, der forklarer de næste trin i drevforsendelsesprocessen.

16. Klik på **Ikonet** Opdater under ![fanen Importér.](../media/O365-MDM-Policy-RefreshIcon.gif) **Opdater** for at få vist det nye drevforsendelsesimportjob på listen over importjob. Status er indstillet til **Venter på sporingsnummer**. Du kan også klikke på importjobbet for at få vist pop op-siden med statusoplysninger, som indeholder mere detaljerede oplysninger om importjobbet.

## <a name="step-5-ship-the-hard-drive-to-microsoft"></a>Trin 5: Send harddisken til Microsoft

Næste trin er at sende harddisken til Microsoft og derefter angive sporingsnummeret for forsendelses- og returforsendelsesoplysningerne for drevforsendelsesjobbet. Når drevet er modtaget af Microsoft, tager det mellem 7 og 10 arbejdsdage, før datacentermedarbejderen overfører dine PST-filer Azure Storage i organisationens område.
  
> [!NOTE]
> Hvis du ikke angiver sporingsnummer og returforsendelsesoplysninger inden for 14 dage efter oprettelse af importjobbet, er importjobbet udløbet. Hvis dette sker, skal du oprette et nyt importjob til drevforsendelse (se Trin [4: Opret et PST-importjob i Office 365](#step-4-create-a-pst-import-job-in-office-365)) og gensende drevfilen og PST-importtilknytningsfilen.
  
### <a name="ship-the-hard-drive"></a>Send harddisken

Husk følgende, når du sender harddiske til Microsoft:
  
- Send ikke SATA-til-USB-adapteren. skal du kun sende harddisken.

- Pak harddisken korrekt. Brug f.eks. en anti-statisk sæk eller bobleombrydning.

- Brug en leveringsudbyder efter eget valg til at sende harddisken til Microsoft.

- Send harddisken til adressen for den Microsoft-placering, der blev vist, da du oprettede importjobbet i trin 4. Sørg for at medtage "Office 365 Import service" i leveringsadressen.

- Når du har leveret harddisken, skal du skrive navnet på leveringsfirmaet og sporingsnummeret ned. Du skal angive disse i næste trin.
    
### <a name="enter-the-tracking-number-and-other-shipping-information"></a>Angiv sporingsnummer og andre leveringsoplysninger

Når du har sendt harddisken til Microsoft, skal du udføre følgende procedure på siden Importér tjeneste.
  
1. Gå til <https://compliance.microsoft.com> og log på med legitimationsoplysningerne til en administratorkonto i organisationen.

2. I venstre navigationsrude i navigationsruden Microsoft 365 Overholdelsescenter du klikke **på > Importér**.

3. På fanen **Importér** skal du klikke på jobbet for den drevforsendelse, du vil angive sporingsnummeret for.

4. Klik på Angiv registreringsnummer på siden med **pop op-sider med status**.

5. Angiv følgende leveringsoplysninger:

   1. **Leveringsudbyder** Skriv navnet på den leveringsudbyder, du brugte til at sende harddisken til Microsoft. 

   2. **Sporingsnummer** Skriv sporingsnummeret for harddiskforsendelsen. 

   3. **Kontonummer for returneringsudbyder** Skriv din organisations kontonummer for den udbyder, der er angivet under **Returudbyder**. Microsoft bruger (og opkræver) denne konto til at sende din harddisk tilbage til dig. Organisationer i USA og Europa skal have en konto med FedEx. Organisationer i Asien og resten af verden skal have en konto hos DHL.

6. Klik **på Gem** for at gemme disse oplysninger for importjobbet. 

    Klik på **Ikonet** Opdater under ![fanen Importér.](../media/O365-MDM-Policy-RefreshIcon.gif) **Opdater** for at opdatere oplysningerne for dit drevforsendelsesimportjob. Bemærk, at status nu er indstillet **til Drev under transport**.

## <a name="step-6-filter-data-and-start-the-pst-import-job"></a>Trin 6: Filtrer data, og start PST-importjobbet

Når Microsoft har modtaget din harddisk, ændres status for importjobbet på siden **Importér PST-filer** til **Drev modtaget**. Datacentermedarbejdere bruger oplysningerne i journalfilen til at uploade dine PST-filer til Azure Storage i organisationen. På dette tidspunkt ændres status til **Import er i gang**. Som tidligere nævnt tager det mellem 7 og 10 arbejdsdage, efter du har modtaget din harddisk, før du uploader PST-filerne.
  
Når PST-filer er uploadet til Azure, ændres status til **Igangværende analyse**. Dette angiver, at Microsoft 365 analyserer dataene i PST-filerne (på en sikker måde) for at identificere alderen på elementerne og de forskellige meddelelsestyper, der er inkluderet i PST-filerne. Når analysen er færdig, og dataene er klar til at blive importeret, ændres status for importjobbet til **Analyse fuldført**. På dette tidspunkt har du mulighed for at importere alle de data, der er indeholdt i PST-filerne, eller du kan trimme de data, der importeres, ved at angive filtre, der styrer, hvilke data der importeres.
  
1. Gå til <https://compliance.microsoft.com> og log på med legitimationsoplysningerne til en administratorkonto i organisationen.

2. Klik på Microsoft 365 Overholdelsescenter \> ***Import**** i venstre navigationsrude.

3. På fanen **Importér** skal du vælge det importjob, du oprettede i trin 4, og klikke **på Importér for Office 365**.
  
    En side med flyv ud vises med oplysninger om PST-filer og andre oplysninger om importjobbet.

4. Klik **på Importér for Office 365**.

5. Siden **Filtrer** dine data vises. Den indeholder dataindsigt, der er resultatet af den analyse, der er udført på PST-filer af Office 365, herunder oplysninger om alderen på dataene. På dette tidspunkt har du mulighed for at filtrere de data, der importeres eller importerer alle dataene, som de er. 

    ![Du kan trimme dataene i PST-filerne eller importere dem alle.](../media/287fc030-99e9-417b-ace7-f64617ea5d4e.png)
  
6. Gør et af følgende:

   1. Hvis du vil trimme de data, du importerer, **skal du klikke på Ja, jeg vil filtrere dem, før du importerer**.

      Hvis du vil have en detaljeret trinvis vejledning til at filtrere dataene i PST-filerne og derefter starte importjobbet, skal du se Filtrer data, når du importerer [PST-filer Office 365](filter-data-when-importing-pst-files.md).

      Eller

   1. Hvis du vil importere alle data i PST-filerne, skal du **klikke på Nej, jeg vil importere alt og** klikke på **Næste**.

7. Hvis du vælger at importere alle dataene, skal du klikke på **Importér data** for at starte importjobbet. 

    Status for importjobbet vises på siden **Importér PST-filer** . Klik ![på ikonet Opdater.](../media/O365-MDM-Policy-RefreshIcon.gif) **Opdater** for at opdatere de statusoplysninger, der vises i **kolonnen Status** . Klik på importjobbet for at få vist siden med pop op-status, som viser statusoplysninger om hver PST-fil, der importeres. Når importen er fuldført, og PST-filer er blevet importeret til brugerpostkasser, ændres status til **Fuldført**.

## <a name="view-a-list-of-the-pst-files-uploaded-to-microsoft-365"></a>Få vist en liste over pst.-filer, der er overført Microsoft 365

Du kan installere og bruge Microsoft Azure Storage Explorer (som er et gratis, open source-værktøj) til at få vist listen over de PST-filer, vi er blevet overført (af medarbejdere i Microsofts datacenter) til Azure Storage-området for organisationen. Det kan du gøre for at bekræfte, at PST-filer fra de harddiske, du har sendt til Microsoft, er blevet overført til Azure Storage filområdet.
  
> [!IMPORTANT]
> Du kan ikke bruge Stifinder Azure Storage at uploade eller redigere PST-filer. Den eneste understøttede metode til at importere PST-filer til Microsoft 365 er at bruge AzCopy. Du kan heller ikke slette PST-filer, du har uploadet til Azure Blob. Hvis du forsøger at slette en PST-fil, får du en fejl om, at du ikke har de nødvendige tilladelser. Alle PST-filer slettes automatisk fra dit Azure Storage område. Hvis der ikke er nogen importjob i gang, slettes alle PST-filer i beholderen ** ingestiondata ** 30 dage efter, det seneste importjob blev oprettet.
  
Udfør følgende trin for at få SAS-URL-adressen (Shared Access Signature) for organisationen. Denne URL-adresse er en kombination af netværkets URL-adresse til Azure Storage placering i Microsoft-skyen for din organisation og en SAS-nøgle. Denne nøgle giver dig de nødvendige tilladelser til at få adgang til din Azure Storage placering.

Sådan installerer du Azure Storage og opretter forbindelse til dit Azure Storage område:

1. Gå til <https://compliance.microsoft.com> og log på med legitimationsoplysningerne til en administratorkonto i organisationen.

2. I venstre rude i Microsoft 365 Overholdelsescenter skal du klikke på **> Importér**.

3. Klik på **Tilføj** ikon under ![fanen Importér.](../media/ITPro-EAC-AddIcon.gif) **Nyt importjob**.

4. Skriv et navn til PST-importjobbet i guiden Importér job, og klik derefter på **Næste**. Brug små bogstaver, tal, bindestreger og understregningstegn. Du må ikke bruge store bogstaver eller medtage mellemrum i navnet.

5. På siden **Vælg import af jobtype** skal du klikke **på Upload dine data** og derefter klikke på **Næste**.

6. I trin 2 skal du klikke **på Vis netværksoverførsel SAS URL**.

7. Når URL-adressen vises, skal du kopiere den og gemme den i en fil. Sørg for at kopiere hele URL-adressen.

    > [!IMPORTANT]
    > Sørg for at beskytte SAS URL-adressen. Dette kan bruges af alle til at få adgang til Azure-lagringsområdet i organisationen.
  
8. Klik **på Annuller** for at lukke guiden Importér job.

9. Download og installér [værktøjet Microsoft Azure Storage Stifinder](https://go.microsoft.com/fwlink/p/?LinkId=544842).

10. Start fanen Microsoft Azure Storage Stifinder, højreklik **på Storage konti** i venstre rude, og klik derefter på **Forbind at Azure Storage**.

    ![Højreklik på Konti Storage, og klik derefter på Forbind for at Azure Storage.](../media/75b80cc3-c336-4f96-ad32-54ac9b96a7af.png)
  
11. Klik **på Brug en SAS-URI (Shared Access Signature) eller forbindelsesstreng, og** klik på **Næste**.

12. Klik **på Brug en SAS URI**, indsæt DEN SAS URL-adresse, du fik i trin 1, i feltet under **URI**, og klik derefter på **Næste**.

13. På siden **Forbindelsesoversigt** kan du gennemse forbindelsesoplysningerne og derefter klikke på **Forbind**.

    **Beholderen til ingestiondata** åbnes. Den indeholder PST-filer fra din harddisk. **Beholderen til ingestiondata** er placeret under **Storage Accounts** \> **(SAS-Attached Services)** \> **Blob Containers**.

    ![Azure Storage viser en liste over de PST-filer, du har uploadet.](../media/12376fed-13a5-4a09-8fe6-e819e011b334.png)
  
14. Når du er færdig med at bruge Microsoft Azure Storage Stifinder, skal du højreklikke **på ingestiondata** og derefter klikke på Fjern  for at afbryde forbindelsen Azure Storage området. Ellers vises der en fejl, næste gang du forsøger at vedhæfte. 

    ![Højreklik på ingestion, og klik på Fjern for at afbryde forbindelsen Azure Storage forbindelse.](../media/1e8e5e95-4215-4ce4-a13d-ab5f826a0510.png)

## <a name="troubleshooting-tips"></a>Tip til fejlfinding

- **Hvad sker der, hvis importjobbet mislykkes på grund af fejl i PST-import-CSV-tilknytningsfilen?** Hvis et importjob mislykkes på grund af fejl i tilknytningsfilen, behøver du ikke at ombilde harddisken til Microsoft for at oprette et importjob. Det skyldes, at PST-filerne fra den harddisk, du har indsendt til importjobbet til drevforsendelse, allerede er blevet uploadet til området Azure Storage for organisationen. I dette tilfælde behøver du kun at rette fejlene i CSV-tilknytningsfilen til PST-import og derefter oprette et nyt "netværksupload"-importjob og sende den reviderede CSV-tilknytningsfil. Hvis du vil oprette og starte et nyt importjob til netværksupload, skal du se Trin [5: Opret et PST-importjob i Microsoft 365](use-network-upload-to-import-pst-files.md#step-5-create-a-pst-import-job) og Trin [6: Filtrer data, og start PST-importjobbet](use-network-upload-to-import-pst-files.md#step-6-filter-data-and-start-the-pst-import-job) i emnet "Brug netværksupload til at importere PST-filer til Office 365". 
    
    > [!NOTE]
    > For at hjælpe dig med at foretage fejlfinding af CSV-tilknytningsfilen til PST-import skal du bruge værktøjet [Azure Storage Explorer](#view-a-list-of-the-pst-files-uploaded-to-microsoft-365) til at få vist mappestrukturen **i beholderen til ingestiondata** for PST-filerne fra din harddisk, der er blevet overført til Azure-lagringsområdet. Fejl i tilknytningsfilen skyldes typisk en forkert værdi i parameteren FilePath. Denne parameter angiver placeringen af en PST-fil i Azure-lagringsområdet. Se beskrivelsen af FilePath-parameteren i tabellen i [trin 3](#step-3-create-the-pst-import-mapping-file). Som tidligere beskrevet blev placeringen af PST-filer i Azure-lagringsområdet  `/dstdir:` angivet af parameteren, da du kørte værktøjet WAImportExport.exe i [trin 2](#step-2-copy-the-pst-files-to-the-hard-drive). 
  
## <a name="more-information"></a>Flere oplysninger

- Drevforsendelse er en effektiv metode til at importere store mængder arkiveringsdata til Microsoft 365 at drage fordel af de overholdelsesfunktioner, der er tilgængelige for din organisation. Når arkiveringsdata importeres til brugerpostkasser, kan du:

  - [Aktivér arkivpostkasser](enable-archive-mailboxes.md) [og automatisk udvidende arkivering for](enable-autoexpanding-archiving.md) at give brugerne mere postkasselagerplads til dataene. 

  - Placer postkasser i [retslig tilbageholdelse](./create-a-litigation-hold.md) for at bevare dataene. 

  - Brug Microsoft [eDiscovery-værktøjer](search-for-content.md) til at søge i dataene. 

  - Anvend [Microsoft 365 opbevaringspolitikker for](retention.md) at styre, hvor længe dataene bevares, og hvilke handlinger der skal tages, når en opbevaringsperiode udløber. 

  - Søg i [overvågningsloggen](search-the-audit-log-in-security-and-compliance.md) efter hændelser, der er relateret til disse data. 

  - Importér data til [inaktive postkasser](inactive-mailboxes-in-office-365.md) for at arkivere data af hensyn til overholdelse af regler og standarder. 

  - Beskyt din organisation mod [datatab](dlp-learn-about-dlp.md) af følsomme oplysninger. 

- Her er et eksempel på nøglen til en sikker lagerkonto og en BitLocker-krypteringsnøgle. Dette eksempel indeholder også syntaksen for den WAImportExport.exe, du kører for at kopiere PST-filer til en harddisk. Sørg for at beskytte disse på samme måde, som du beskytter adgangskoder eller andre sikkerhedsrelaterede oplysninger.

    ```text
    Secure storage account key: 

    yaNIIs9Uy5g25Yoak+LlSHfqVBGOeNwjqtBEBGqRMoidq6/e5k/VPkjOXdDIXJHxHvNoNoFH5NcVUJXHwu9ZxQ==

    BitLocker encryption key:

    397386-221353-718905-535249-156728-127017-683716-083391

  COMMAND SYNTAX

  First time:

  WAImportExport.exe PrepImport /j:<Name of journal file> /t:<Drive letter> /id:<Name of session> /srcdir:<Location of PST files> /dstdir:<PST file path> /blobtype:BlockBlob /encrypt /logdir:<Log file location>

  Subsequent times:

  WAImportExport.exe PrepImport /j:<Name of journal file> /id:<Name of new session> /srcdir:<Location of PST files> /dstdir:<PST file path> /blobtype:BlockBlob 

  EXAMPLES

  First time:

  WAImportExport.exe PrepImport /j:PSTHDD1.jrn /t:f /id:driveship1 /srcdir:"\\FILESERVER1\PSTs" /dstdir:"ingestiondata/"
  /blobtype:BlockBlob /encrypt /logdir:"c:\users\admin\desktop\PstImportLogs"

  Subsequent times:

  WAImportExport.exe PrepImport /j:PSTHDD1.jrn /id:driveship2 /srcdir:"\\FILESERVER1\PSTs\SecondBatch" /dstdir:"ingestiondata/" /blobtype:BlockBlob
    ```

- Som beskrevet tidligere aktiverer tjenesten Office 365 opbevaringsposition (i ubegrænset tid), efter PST-filer importeres til en postkasse. Det betyder,  *at egenskaben RentionHoldEnabled*  `True` er indstillet til sådan, at den opbevaringspolitik, der er tildelt postkassen, ikke behandles. Dette giver postkasseejeren tid til at administrere de nyligt importerede meddelelser ved at forhindre sletnings- eller arkiveringspolitik i at slette eller arkivere ældre meddelelser. Her er nogle trin, du kan gøre for at administrere denne opbevaringsposition: 

  - Efter en bestemt tidsperiode kan du deaktivere opbevaringspositionen ved at køre  `Set-Mailbox -RetentionHoldEnabled $false` kommandoen. Du kan finde en vejledning under [Placere en postkasse i venteposition](/exchange/security-and-compliance/messaging-records-management/mailbox-retention-hold).

  - Du kan konfigurere opbevaringspositionen, så den er slået fra på en eller anden dato i fremtiden. Det gør du ved at køre  `Set-Mailbox -EndDateForRetentionHold <date>` kommandoen. Hvis f.eks. dags dato er 1. juni 2016, og du vil have opbevarings hold deaktiveret om 30 dage, skal du køre følgende kommando:  `Set-Mailbox -EndDateForRetentionHold 7/1/2016`. I dette scenarie skal du lade  *egenskaben RentionHoldEnabled*  være angivet til  *Sand*. Du kan få mere at vide [under Set-Mailbox](/powershell/module/exchange/set-mailbox).

  - Du kan ændre indstillingerne for den opbevaringspolitik, der er tildelt til postkassen, så ældre elementer, der er blevet importeret, ikke straks slettes eller flyttes til brugerens arkivpostkasse. Eksempelvis kan du forlænge opbevaringsalderen for en sletning eller arkiveringspolitik, der er tildelt postkassen. I dette scenarie skal du deaktivere opbevaringspositionen på postkassen, når du har ændret indstillingerne for opbevaringspolitikken. Få mere at vide under [Konfigurer en arkiverings- og sletningspolitik for postkasser i organisationen](set-up-an-archive-and-deletion-policy-for-mailboxes.md).
