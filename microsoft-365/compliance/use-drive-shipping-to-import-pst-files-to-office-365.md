---
title: Brug drevforsendelse til at importere PST-filer
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
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 40829b57-793c-4d41-b171-e9270129173d
ms.custom: seo-marvel-apr2020
description: Administratoren kan få mere at vide om, hvordan du masseimporterer PST-filer til Microsoft 365 postkasser ved at kopiere PST-filer til en harddisk og derefter sende dem til Microsoft.
ms.openlocfilehash: 4f3c38c203b98fd4448657edfac6ee9b72a515be
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65095438"
---
# <a name="use-drive-shipping-to-import-your-organizations-pst-files"></a>Brug drevforsendelse til at importere din organisations PST-filer

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

**Denne artikel er til administratorer. Forsøger du at importere PST-filer til din egen postkasse? Se [Importér mail, kontakter og kalender fra en .pst-fil Outlook](https://go.microsoft.com/fwlink/p/?LinkID=785075)**
   
Brug Office 365 importtjenesten, og kør forsendelse til masseimport af PST-filer til brugerpostkasser. Forsendelse af drev betyder, at du kopierer PST-filerne til en harddisk og derefter fysisk sender drevet til Microsoft. Når Microsoft modtager din harddisk, kopierer datacenterafdelingen dataene fra harddisken til et lagerområde i Microsoft-cloudmiljøet. Derefter har du mulighed for at trimme de PST-data, der importeres til destinationspostkasserne, ved at angive filtre, der styrer, hvilke data der importeres. Når du har startet importjobbet, importerer importtjenesten PST-dataene fra lagerområdet til brugerpostkasser. Brug af drevforsendelse til at importere PST-filer til brugerpostkasser er en måde at overføre organisationens mail til Office 365 på.
  
Her er de trin, der kræves for at bruge drevforsendelse til at importere PST-filer til Microsoft 365 postkasser:
  
[Trin 1: Download pst-importværktøjet](#step-1-download-the-pst-import-tool)

[Trin 2: Kopiér PST-filerne til harddisken](#step-2-copy-the-pst-files-to-the-hard-drive)

[Trin 3: Opret PST-importtilknytningsfilen](#step-3-create-the-pst-import-mapping-file)

[Trin 4: Opret et PST-importjob i Office 365](#step-4-create-a-pst-import-job-in-office-365)

[Trin 5: Send harddisken til Microsoft](#step-5-ship-the-hard-drive-to-microsoft)

[Trin 6: Filtrer data, og start PST-importjobbet](#step-6-filter-data-and-start-the-pst-import-job)
  
> [!IMPORTANT]
> Du skal udføre trin 1 én gang for at downloade importværktøjet. Når du har udført disse trin, skal du følge trin 2 til og med trin 6, hver gang du vil sende en harddisk til Microsoft. 
  
Hvis du vil have mere at vide om, hvordan du bruger drevforsendelse til at importere PST-filer til Office 365, skal du se [Ofte stillede spørgsmål om brug af drevforsendelse til at importere PST-filer](./faqimporting-pst-files-to-office-365.yml#using-drive-shipping-to-import-pst-files). 
  
## <a name="before-you-import-pst-files"></a>Før du importerer PST-filer

- Du skal have tildelt rollen Importér eksport af postkasse i Exchange Online for at oprette importjob på Microsoft Purview-overholdelsesportalen og importere PST-filer til brugerpostkasser. Denne rolle er som standard ikke tildelt nogen rollegruppe i Exchange Online. Du kan føje rollen Importér eksport af postkasse til rollegruppen Organisationsadministration. Du kan også oprette en rollegruppe, tildele rollen Importér eksport af postkasse og derefter tilføje dig selv som medlem. Du kan få flere oplysninger i afsnittene "Føj en rolle til en rollegruppe" eller "Opret en rollegruppe" i [Administrer rollegrupper](/Exchange/permissions-exo/role-groups).

    Ud over rollen Importér eksport af postkasse skal du også tildeles rollen Mailmodtagere i Exchange Online. Denne rolle er som standard tildelt rollegrupperne Organisationsadministration og Modtageradministration i Exchange Online.

    > [!TIP]
    > Overvej at oprette en ny rollegruppe i Exchange Online, der er specifikt beregnet til import af PST-filer til Office 365. Hvis du vil have det minimumsniveau af rettigheder, der kræves for at importere PST-filer, skal du tildele rollerne Importér eksport af postkasse og Postmodtagere til den nye rollegruppe og derefter tilføje medlemmer.
  
- Du skal gemme de PST-filer, du vil kopiere til en harddisk, på en filserver eller en delt mappe i din organisation. I trin 2 skal du køre værktøjet Azure Import Export (WAImportExport.exe), der kopierer de PST-filer, der er gemt på denne filserver eller delte mappe, til harddisken.

- Store PST-filer kan påvirke ydeevnen af PST-importprocessen. Derfor anbefaler vi, at hver PST-fil, du kopierer til harddisken i Trin 2, ikke må være større end 20 GB.

- Kun 2,5"sSD-diske (solid state-drev) eller 2,5" eller 3,5" SATA II/III-interne harddiske understøttes til brug sammen med Office 365 importtjenesten. Du kan bruge harddiske op til 10 TB. I forbindelse med importjob behandles kun den første datamængde på harddisken. Dataenheden skal være formateret med NTFS. Når du kopierer data til en harddisk, kan du vedhæfte dem direkte ved hjælp af en 2,5 tommer SSD- eller 2,5- eller 3,5-tommer SATA II/III-connector, eller du kan vedhæfte dem eksternt ved hjælp af en ekstern 2,5"SSD- eller 2,5-tommers eller 3,5-tommer SATA II/III USB-adapter.
    
    > [!IMPORTANT]
    > Eksterne harddiske, der følger med en indbygget USB-adapter, understøttes ikke af tjenesten Office 365 Import. Disken i kabinettet på en ekstern harddisk kan ikke bruges. Undlad at sende eksterne harddiske. 
  
- Den harddisk, du kopierer PST-filerne til, skal krypteres med BitLocker. Det WAImportExport.exe værktøj, du kører i trin 2, hjælper dig med at konfigurere BitLocker. Den genererer også en BitLocker-krypteringsnøgle, som Microsofts datacenterpersonale bruger til at få adgang til drevet for at uploade PST-filerne til det Azure Storage område i Microsoft-cloudmiljøet.
    
- Drevforsendelse er tilgængelig via en Microsoft Enterprise Agreement (EA). Drevforsendelse er ikke tilgængelig via en MPSA (Microsoft Products and Services Agreement).
    
- Prisen for at importere PST-filer til Microsoft 365-postkasser ved hjælp af drevforsendelse er 2 USD pr. GB data. Hvis du f.eks. leverer en harddisk, der indeholder 1.000 GB (1 TB) PST-filer, er prisen USD 2.000 USD. Du kan samarbejde med en partner om at betale importgebyret. Du kan finde oplysninger om, hvordan du finder en partner, under [Find din Microsoft-partner eller -forhandler](../admin/manage/find-your-partner-or-reseller.md).
    
- Du eller din organisation skal have en konto hos FedEx eller DHL.
    
  - Organisationer i USA, Brasilien og Europa skal have FedEx-konti.
    
  - Organisationer i Østasien, Det sydøstlige Asien, Japan, Republikken Korea og Australien skal have DHL-konti.
    
    Microsoft bruger (og opkræver) denne konto til at returnere harddisken til dig.
    
- Den harddisk, du sender til Microsoft, kan krydse internationale grænser. I dette tilfælde er du ansvarlig for at sikre, at harddisken og de data, den indeholder, importeres og/eller eksporteres i overensstemmelse med gældende lovgivning. Før du sender en harddisk, skal du kontakte dine rådgivere for at bekræfte, at dit drev og dine data lovligt kan sendes til det identificerede Microsoft-datacenter. Dette hjælper med at sikre, at det når Microsoft i tide.
    
- Denne procedure omfatter kopiering og lagring af en BitLocker-krypteringsnøgle. Sørg for at tage forholdsregler for at beskytte disse nøgler, som du ville beskytte adgangskoder eller andre sikkerhedsrelaterede oplysninger. Du kan f.eks. gemme dem i et Microsoft Word dokument, der er beskyttet med adgangskode, eller gemme dem på et krypteret USB-drev. Se afsnittet [Flere oplysninger](#more-information) for at få et eksempel på disse nøgler. 
    
- Når PST-filer er importeret til en Microsoft 365 postkasse, aktiveres indstillingen for opbevaring af venteposition for postkassen i en ubestemt varighed. Det betyder, at den opbevaringspolitik, der er tildelt postkassen, ikke behandles, før du slår opbevarings ventepositionen fra eller angiver en dato for at slå ventepositionen fra. Hvorfor gør vi det? Hvis meddelelser, der er importeret til en postkasse, er gamle, kan de blive slettet permanent (slettet), fordi deres opbevaringsperiode er udløbet på baggrund af de opbevaringsindstillinger, der er konfigureret for postkassen. Hvis postkassen placeres i opbevaringsposition, kan ejeren af postkassen administrere disse nyligt importerede meddelelser eller give dig tid til at ændre opbevaringsindstillingerne for postkassen. Se afsnittet [Flere oplysninger](#more-information) for at få forslag til administration af opbevarings venteposition. 
    
- Den maksimale meddelelsesstørrelse, der kan modtages af en Microsoft 365 postkasse, er som standard 35 MB. Det skyldes, at standardværdien for egenskaben  *MaxReceiveSize*  for en postkasse er angivet til 35 MB. Grænsen for den maksimale størrelse på meddelelser i Microsoft 365 er dog 150 MB. Så hvis du importerer en PST-fil, der indeholder et element, der er større end 35 MB, Office 365 importtjenesten, ændrer vi automatisk værdien af egenskaben *MaxReceiveSize* i målpostkassen til 150 MB. Dette gør det muligt at importere meddelelser op til 150 MB til brugerpostkasser. 
    
    > [!TIP]
    > Hvis du vil identificere meddelelsens modtagelsesstørrelse for en postkasse, kan du køre denne kommando i Exchange Online PowerShell: `Get-Mailbox <user mailbox> | FL MaxReceiveSize`. 
  
- Du kan importere PST-filer til en inaktiv postkasse i Office 365. Det gør du ved at angive GUID'et for den inaktive postkasse i parameteren  `Mailbox` i PST-importtilknytningsfilen. Se [Trin 3: Opret PST-importtilknytningsfilen](#step-3-create-the-pst-import-mapping-file) for at få flere oplysninger. 
    
- I en Exchange hybridinstallation kan du importere PST-filer til en skybaseret arkivpostkasse for en bruger, hvis primære postkasse er i det lokale miljø. Det gør du ved at gøre følgende i tilknytningsfilen til PST-import:
    
  - Angiv mailadressen for brugerens lokale postkasse i parameteren  `Mailbox` . 
    
  - Angiv **TRUE-værdien** i parameteren  `IsArchive` . 
    
    Se [Trin 3: Opret PST-importtilknytningsfilen](#step-3-create-the-pst-import-mapping-file) for at få flere oplysninger. 

## <a name="step-1-download-the-pst-import-tool"></a>Trin 1: Download pst-importværktøjet

Det første trin er at downloade værktøjet, og at du bruger trin 2 til at kopiere PST-filer til harddisken.
  
> [!IMPORTANT]
> Du skal bruge Azure Import/Export værktøjsversion 1 (WAimportExportV1) til at importere PST-filer ved hjælp af drevforsendelsesmetoden. Version 2 af Azure Import/Export-værktøjet understøttes ikke, og hvis du bruger det, vil det resultere i, at harddisken forberedes forkert til importjobbet. Sørg for at downloade Azure Import/Export-værktøjet fra Microsoft Purview-overholdelsesportalen ved at følge procedurerne i dette trin. 
  
1. Gå til , <https://compliance.microsoft.com> og log på med legitimationsoplysningerne for en administratorkonto i din organisation.

2. Klik på **Import** af **datalivscyklusstyring** \> i venstre navigationsrude i overholdelsesportalen.
    
    > [!NOTE]
    > Som tidligere angivet skal du have tildelt de relevante tilladelser for at få adgang til siden **Import** på overholdelsesportalen.
  
3. Klik på ![Tilføj ikon under fanen **Importér**.](../media/ITPro-EAC-AddIcon.gif) **Nyt importjob**.
    
4. Skriv et navn til PST-importjobbet i guiden til import af job, og klik derefter på **Næste**. Brug små bogstaver, tal, bindestreger og understregningstegn. Du kan ikke bruge store bogstaver eller medtage mellemrum i navnet.
    
5. På siden **Vælg importjobtype** skal du klikke på **Send harddiske til en af vores fysiske placeringer** og derefter klikke på **Næste**.
    
    ![Klik på Send harddiske til en af vores fysiske placeringer for at oprette et drev til import af forsendelse.](../media/1584fdc5-cd4c-4e47-932e-db6c8e07f5f8.png)
  
6. Gør følgende på siden **Importér data** :     
    
    **Download Azure Import/Export-værktøjet** for at downloade og installere Værktøjet Azure Import/Export (version 1).
    
    - Klik på **Gem** \> **som** i pop op-vinduet for at gemme den WaImportExportV1.zip fil i en mappe på din lokale computer.
    
    - Udpak den WaImportExportV1.zip fil.
    
7. Klik på **Annuller** for at lukke guiden.
    
    Du kommer tilbage til siden **Importér** på overholdelsesportalen, når du opretter importjobbet i trin 4.

## <a name="step-2-copy-the-pst-files-to-the-hard-drive"></a>Trin 2: Kopiér PST-filerne til harddisken

Det næste trin er at bruge værktøjet WAImportExport.exe til at kopiere PST-filer til harddisken. Dette værktøj krypterer harddisken med BitLocker, kopierer psts til harddisken og opretter en journalfil, der gemmer oplysninger om kopieringsprocessen. Hvis du vil fuldføre dette trin, skal PST-filerne være placeret på et filshare eller på en filserver i din organisation. Dette kaldes kildemappen i følgende procedure.

 Som tidligere nævnt må hver PST-fil, du kopierer til harddisken, ikke være større end 20 GB. PST-filer, der er større end 20 GB, kan påvirke ydeevnen af den PST-importproces, du starter i trin 6.
  
> [!IMPORTANT]
> Når du har kørt WAImportExport.exe værktøj første gang for en harddisk, skal du hver gang bruge en anden syntaks. Denne syntaks forklares i trin 4 i denne procedure for at kopiere PST-filer til harddisken.
  
1. Åbn en kommandoprompt på din lokale computer.
    
    > [!TIP]
    > Hvis du kører kommandoprompten som administrator (ved at vælge "Kør som administrator", når du åbner den), vises der fejlmeddelelser i kommandopromptvinduet. Dette kan hjælpe dig med at foretage fejlfinding af problemer med at køre værktøjet WAImportExport.exe.
  
2. Gå til den mappe, hvor du installerede værktøjet WAImportExport.exe i trin 1.
3. Kør følgende kommando, første gang du bruger WAImportExport.exe til at kopiere PST-filer til en harddisk.

    ```powershell
    WAImportExport.exe PrepImport /j:<Name of journal file> /t:<Drive letter> /id:<Name of session> /srcdir:<Location of PST files> /dstdir:<PST file path> /blobtype:BlockBlob /encrypt /logdir:<Log file location>
    ```

    I følgende tabel beskrives parametrene og deres påkrævede værdier.
    
    |**Parameter**|**Beskrivelse**|**Eksempel**|
    |:-----|:-----|:-----|
    | `/j:` <br/> |Angiver navnet på journalfilen. Denne fil gemmes i den samme mappe, hvor værktøjet WAImportExport.exe er placeret. Hver harddisk, du sender til Microsoft, skal have én journalfil. Hver gang du kører WAImportTool.exe for at kopiere PST-filer til en harddisk, føjes der oplysninger til journalfilen for det pågældende drev.  <br/> Microsofts datacenterpersonale bruger oplysningerne i journalfilen til at knytte harddisken til det importjob, du opretter i trin 4, og til at uploade PST-filerne til området Azure Storage i Microsoft-cloudmiljøet.  <br/> | `/j:PSTHDD1.jrn` <br/> |
    | `/t:` <br/> |Angiver drevbogstavet for harddisken, når den er tilsluttet den lokale computer.  <br/> | `/t:h` <br/> |
    | `/id:` <br/> |Angiver navnet på kopisessionen. En session defineres som hver gang, du kører værktøjet WAImportExport.exe til at kopiere filer til harddisken. PST-filerne kopieres til en mappe med navnet med det sessionsnavn, der er angivet i denne parameter.  <br/> | `/id:driveship1` <br/> |
    | `/srcdir:` <br/> |Angiver den kildemappe i organisationen, der indeholder de PST-filer, der kopieres under sessionen. Sørg for at omgive værdien af denne parameter med dobbelte anførselstegn (" ").  <br/> | `/srcdir:"\\FILESERVER01\PSTs"` <br/> |
    | `/dstdir:` <br/> |Angiver destinationsmappen i det Azure Storage område i Microsoft-cloudmiljøet, hvor psts uploades. Du skal bruge værdien  `ingestiondata/`. Sørg for at omgive værdien af denne parameter med dobbelte anførselstegn (" ").  <br/> Du kan også føje en ekstra filsti til værdien af denne parameter. Du kan f.eks. bruge filstien til kildemappen på harddisken (konverteret til et URL-format), som er angivet i parameteren  `/srcdir:` . Ændres f.eks  `\\FILESERVER01\PSTs` . til  `FILESERVER01/PSTs`. I dette tilfælde skal du stadig inkludere  `ingestiondata` i filstien. Så i dette eksempel ville værdien for parameteren  `/dstdir:` være  `"ingestiondata/FILESERVER01/PSTs"`.  <br/> En af grundene til at tilføje den ekstra filsti er, hvis du har PSTs-filer med det samme filnavn.  <br/> > [!NOTE]> Hvis du inkluderer det valgfri stinavn, indeholder navneområdet for en PST-fil, når den er uploadet til Azure Storage-området, stinavnet og navnet på PST-filen, `FILESERVER01/PSTs/annb.pst`f.eks. . Hvis du ikke inkluderer et stinavn, er navneområdet kun PST-filnavnet. for eksempel  `annb.pst`.           | `/dstdir:"ingestiondata/"` <br/> Eller  <br/>  `/dstdir:"ingestiondata/FILESERVER01/PSTs"` <br/> |
    | `/blobtype:` <br/> |Angiver den type blobs i området Azure Storage, PST-filerne skal importeres til. Brug værdien **BlockBlob** til import af PST-filer. Denne parameter er påkrævet.   <br/> | `/blobtype:BlockBlob` <br/> |
    | `/encrypt` <br/> |Denne knap aktiverer BitLocker for harddisken. Denne parameter kræves, første gang du kører værktøjet WAImportExport.exe.  <br/> BitLocker-krypteringsnøglen kopieres til journalfilen og den logfil, der oprettes, hvis du bruger parameteren  `/logfile:` . Som tidligere forklaret gemmes journalfilen i den samme mappe, hvor værktøjet WAImportExport.exe er placeret.  <br/> | `/encrypt` <br/> |
    | `/logdir:` <br/> |Denne valgfri parameter angiver en mappe, som logfiler skal gemmes i. Hvis den ikke er angivet, gemmes logfilerne i den samme mappe, hvor værktøjet WAImportExport.exe er placeret. Sørg for at omgive værdien af denne parameter med dobbelte anførselstegn (" ").  <br/> | `/logdir:"c:\users\admin\desktop\PstImportLogs"` <br/> |
   
    Her er et eksempel på syntaksen for værktøjet WAImportExport.exe, der bruger faktiske værdier for hver parameter:
    
    ```powershell
    WAImportExport.exe PrepImport /j:PSTHDD1.jrn /t:f /id:driveship1 /srcdir:"\\FILESERVER01\PSTs" /dstdir:"ingestiondata/" blobtype:BlockBlob /encrypt /logdir:"c:\users\admin\desktop\PstImportLogs"
    ```

    Når du har kørt kommandoen, vises der statusmeddelelser, der viser status for kopiering af PST-filerne til harddisken. En endelig statusmeddelelse viser det samlede antal filer, der blev kopieret.
    
4. Kør denne kommando, hver gang du efterfølgende kører værktøjet WAImportExport.ext for at kopiere PST-filer til den samme harddisk.

    ```powershell
    WAImportExport.exe PrepImport /j:<Name of journal file> /id:<Name of new session> /srcdir:<Location of PST files> /dstdir:<PST file path> /blobtype:BlockBlob 
    ```

    Her er et eksempel på syntaksen for kørsel af efterfølgende sessioner for at kopiere PST-filer til den samme harddisk.

    ```powershell
    WAImportExport.exe PrepImport /j:PSTHDD1.jrn /id:driveship2 /srcdir:"\\FILESERVER01\PSTs\SecondBatch" /dstdir:"ingestiondata/" /blobtype:BlockBlob
    ```

## <a name="step-3-create-the-pst-import-mapping-file"></a>Trin 3: Opret PST-importtilknytningsfilen

Når Microsofts datacenterpersonale har uploadet PST-filerne fra harddisken til området Azure Storage, bruger importtjenesten oplysningerne i PST-importtilknytningsfilen, som er en kommasepareret værdifil (CSV), som angiver, hvilke brugerpostkasser PST-filerne importeres til. Du skal sende denne CSV-fil i næste trin, når du opretter et PST-importjob.
  
1. [Download en kopi af PST-importtilknytningsfilen](https://go.microsoft.com/fwlink/p/?LinkId=544717).
    
2. Åbn eller gem CSV-filen på din lokale computer. I følgende eksempel vises en fuldført PST-importtilknytningsfil (åbnet i Notesblok). Det er meget nemmere at bruge Microsoft Excel til at redigere CSV-filen.

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

    Den første række eller kolonneoverskrift i CSV-filen viser de parametre, der skal bruges af PST-importtjenesten til at importere PST-filerne til brugerpostkasser. Hvert parameternavn er adskilt af et komma. Hver række under overskriftsrækken repræsenterer parameterværdierne for import af en PST-fil til en bestemt postkasse. Du skal bruge en række for hver PST-fil, der blev kopieret til harddisken. Sørg for at erstatte pladsholderdataene i tilknytningsfilen med dine faktiske data.

    > [!NOTE]
    > Undlad at ændre noget i overskriftsrækken, herunder parametrene for SharePoint. De ignoreres under PST-importprocessen. 
  
3. Brug oplysningerne i følgende tabel til at udfylde CSV-filen med de påkrævede oplysninger.
    
    |**Parameter**|**Beskrivelse**|**Eksempel**|
    |:-----|:-----|:-----|
    | `Workload` <br/> |Angiver den tjeneste, som dataene skal importeres til. Hvis du vil importere PST-filer til brugerpostkasser, skal du bruge  `Exchange`.  <br/> | `Exchange` <br/> |
    | `FilePath` <br/> | Angiver mappeplaceringen i det Azure Storage område, som PST-filer kopieres til, når harddisken leveres til Microsoft.  <br/>  Det, du tilføjer i denne kolonne i CSV-filen, afhænger af, hvad du angav i for parameteren  `/dstdir:` i det forrige trin. Hvis du har undermapper på kildeplaceringen, skal værdien i `FilePath` parameteren indeholde den relative sti til undermappen, f.eks. /folder1/user1/.  <br/>  Hvis du har brugt  `/dstdir:"ingestiondata/"`, skal du lade denne parameter være tom i CSV-filen.  <br/>  Hvis du har medtaget et valgfrit stinavn for værdien af  `/dstdir:` parameteren (f.eks.  `/dstdir:"ingestiondata/FILESERVER01/PSTs"`, skal du bruge dette stinavn (ikke inklusive "ingestiondata") for denne parameter i CSV-filen. Der skelnes mellem store og små bogstaver i værdien for denne parameter.  <br/>  Uanset hvad skal  *du ikke*  inkludere "data for indtagelse" i værdien for  `FilePath` parameteren. Lad denne parameter være tom, eller angiv kun det valgfri stinavn.  <br/> > [!IMPORTANT]> Hvis der er tale om filnavnet, skal det være det samme, som du angav i  `/dstdir:` parameteren i det forrige trin. Hvis du f.eks. brugte  `"ingestiondata/FILESERVER01/PSTs"` til navnet på undermappen i det forrige trin, men derefter brugte  `fileserver01/psts` den  `FilePath` i parameteren i CSV-filen, mislykkes importen af PST-filen. Sørg for at bruge det samme tilfælde i begge tilfælde.           |(lad argumentet være tomt)  <br/> Eller  <br/>  `FILESERVER01/PSTs` <br/> |
    | `Name` <br/> |Angiver navnet på den PST-fil, der importeres til brugerpostkassen. Der skelnes mellem store og små bogstaver i værdien for denne parameter.  <br/> > [!IMPORTANT]> Sagen for PST-filnavnet i CSV-filen skal være den samme som den PST-fil, der blev uploadet til den Azure Storage placering i Trin 2. Hvis du f.eks. bruger  `annb.pst` parameteren i  `Name` CSV-filen, men navnet på den faktiske PST-fil er  `AnnB.pst`, mislykkes importen af den pågældende PST-fil. Sørg for, at navnet på PST i CSV-filen bruger samme sag som den faktiske PST-fil.           | `annb.pst` <br/> |
    | `Mailbox` <br/> |Angiver mailadressen på den postkasse, som PST-filen importeres til. Du kan ikke angive en offentlig mappe, fordi PST-importtjenesten ikke understøtter import af PST-filer til offentlige mapper.  <br/> Hvis du vil importere en PST-fil til en inaktiv postkasse, skal du angive postkassens GUID for denne parameter. Hvis du vil hente dette GUID, skal du køre følgende PowerShell-kommando i Exchange Online:`Get-Mailbox <identity of inactive mailbox> -InactiveMailboxOnly | FL Guid` <br/> > [!NOTE]> Nogle gange kan du have flere postkasser med den samme mailadresse, hvor den ene postkasse er en aktiv postkasse, og den anden postkasse er i tilstanden blød slettet (eller inaktiv). I disse situationer skal du angive postkassens GUID for entydigt at identificere den postkasse, PST-filen skal importeres til. Hvis du vil hente dette GUID til aktive postkasser, skal du køre følgende PowerShell-kommando:  `Get-Mailbox <identity of active mailbox> | FL Guid`. Hvis du vil hente GUID'et for postkasser med blød sletning (eller inaktive), skal du køre denne kommando:  `Get-Mailbox <identity of soft-deleted or inactive mailbox> -SoftDeletedMailbox | FL Guid`.           | `annb@contoso.onmicrosoft.com` <br/> Eller  <br/>  `2d7a87fe-d6a2-40cc-8aff-1ebea80d4ae7` <br/> |
    | `IsArchive` <br/> | Angiver, om PST-filen skal importeres til brugerens arkivpostkasse. Der er to muligheder:  <br/> **FALSK** Importerer PST-filen til brugerens primære postkasse.  <br/> **SANDT** Importerer PST-filen til brugerens arkivpostkasse. Dette forudsætter, at [brugerens arkivpostkasse er aktiveret](enable-archive-mailboxes.md). Hvis du angiver denne parameter til  `TRUE` , og brugerens arkivpostkasse ikke er aktiveret, mislykkes importen for den pågældende bruger. Hvis en import mislykkes for én bruger (fordi vedkommendes arkiv ikke er aktiveret, og denne egenskab er angivet til  `TRUE`), påvirkes de andre brugere i importjobbet ikke.  <br/>  Hvis du lader denne parameter være tom, importeres PST-filen til brugerens primære postkasse.  <br/> **Bemærk:** Hvis du vil importere en PST-fil til en skybaseret arkivpostkasse for en bruger, hvis primære postkasse er i det lokale miljø, skal du blot angive  `TRUE` for denne parameter og angive mailadressen for brugerens lokale postkasse for  `Mailbox` parameteren.  <br/> | `FALSE` <br/> Eller  <br/>  `TRUE` <br/> |
    | `TargetRootFolder` <br/> | Angiver den postkassemappe, som PST-filen importeres til.  <br/>  Hvis du lader denne parameter være tom, importeres PST til en ny mappe med navnet **Importeret** , der er placeret på rodniveauet i postkassen (samme niveau som mappen Indbakke og de andre standardpostkassemapper).  <br/>  Hvis du angiver  `/`, importeres elementerne i PST-filen direkte i brugerens indbakkemappe.  <br/>  Hvis du angiver  `/<foldername>`, importeres elementer i PST-filen til en mappe med navnet  *\<foldername\>*. Hvis du f.eks. bruger  `/ImportedPst`, importeres elementer til en mappe med navnet **ImportedPst**. Denne mappe placeres i brugerens postkasse på samme niveau som mappen Indbakke.  <br/> |(lad argumentet være tomt)  <br/> Eller  <br/>  `/` <br/> Eller  <br/>  `/ImportedPst` <br/> |
    | `ContentCodePage` <br/> |Denne valgfri parameter angiver en numerisk værdi for den tegntabel, der skal bruges til import af PST-filer i ANSI-filformatet. Denne parameter bruges til at importere PST-filer fra kinesiske, japanske og koreanske (CJK) organisationer, fordi disse sprog typisk bruger et dobbeltbytetegnsæt (DBCS) til tegnkodning. Hvis denne parameter ikke bruges til at importere PST-filer til sprog, der bruger DBCS til postkassemappenavne, bliver mappenavnene ofte forvansket, når de er importeret.  <br/> Du kan se en liste over understøttede værdier, der skal bruges til denne parameter, under [Tegntabel-id'er](/windows/win32/intl/code-page-identifiers).  <br/> > [!NOTE]> Som tidligere angivet er dette en valgfri parameter, og du behøver ikke at inkludere den i CSV-filen. Du kan også inkludere den og lade værdien være tom for en eller flere rækker.           |(lad argumentet være tomt)  <br/> Eller  <br/>  `932` (som er tegntabel-id'et for ANSI/OEM Japansk)  <br/> |
    | `SPFileContainer` <br/> |Lad denne parameter være tom i forbindelse med PST-import.  <br/> |Ikke relevant  <br/> |
    | `SPManifestContainer` <br/> |Lad denne parameter være tom i forbindelse med PST-import.  <br/> |Ikke relevant  <br/> |
    | `SPSiteUrl` <br/> |Lad denne parameter være tom i forbindelse med PST-import.  <br/> |Ikke relevant  <br/> |

## <a name="step-4-create-a-pst-import-job-in-office-365"></a>Trin 4: Opret et PST-importjob i Office 365

Det næste trin er at oprette PST-importjobbet i tjenesten Importér i Office 365. Som tidligere forklaret skal du sende den PST-importtilknytningsfil, du oprettede i trin 3. Når du har oprettet jobbet, bruger importtjenesten oplysningerne i tilknytningsfilen til at importere PST-filerne til den angivne brugerpostkasse, når PST-filerne er kopieret fra harddisken til området Azure Storage, og du opretter og starter importjobbet.
  
1. Gå til , <https://compliance.microsoft.com> og log på med legitimationsoplysningerne for en administratorkonto i din organisation.

2. Klik på **Import** af **datalivscyklusstyring** \> i venstre navigationsrude i overholdelsesportalen.

3. Klik på ![Tilføj ikon under fanen **Importér**.](../media/ITPro-EAC-AddIcon.gif) **Nyt importjob**.

    > [!NOTE]
    > Som tidligere angivet skal du have tildelt de relevante tilladelser for at få adgang til siden **Import** på overholdelsesportalen.
  
4. Skriv et navn til PST-importjobbet, og klik derefter på **Næste**. Brug små bogstaver, tal, bindestreger og understregningstegn. Du kan ikke bruge store bogstaver eller medtage mellemrum i navnet.

5. På siden **Vælg importjobtype** skal du klikke på **Send harddiske til en af vores fysiske placeringer** og derefter klikke på **Næste**.
  
6. I trin 6 skal du klikke på afkrydsningsfelterne **Jeg har forberedt mine harddiske og har adgang til de nødvendige drevjournalfiler** , og **jeg har adgang til tilknytningsfilen** og derefter klikke på **Næste**.

    ![Klik på de to afkrydsningsfelter i trin 6.](../media/fad43078-ea68-4acd-b2ed-75a800183262.png)
  
7. På siden **Vælg drevfil** skal du klikke på **Vælg drevfil** og derefter gå til den samme mappe, hvor værktøjet WAImportExport.exe er placeret. Den journalfil, der blev oprettet i trin 2, blev kopieret til denne mappe.

    ![Klik på Vælg drevfil for at sende den journalfil, der blev oprettet, da du kørte værktøjet WAImportExport.exe.](../media/1ea35c04-bd88-4d7e-b7d9-dc390149d94f.png)
  
8. Vælg journalfilen. f.eks. `PSTHDD1.jrn`.

    > [!TIP]
    > Da du kørte værktøjet WAImportExport.exe i trin 2, blev navnet på journalfilen angivet af  `/j:` parameteren.
  
9. Når navnet på drevfilen vises under **Drevfilnavn**, skal du klikke på **Valider** for at kontrollere, om der er fejl i drevfilen.

    ![Klik på Valider for at validere den valgte drevfil.](../media/4b707f5a-152a-4e74-b9f5-449c88d1fec4.png)
  
    Drevfilen skal valideres for at oprette et PST-importjob. Filnavnet ændres til grønt, når det er valideret. Hvis valideringen mislykkes, skal du klikke på linket **Vis log** . Der åbnes en valideringsfejlrapport med en fejlmeddelelse med oplysninger om, hvorfor filen mislykkedes. 

    > [!NOTE]
    > Du skal tilføje og validere en journalfil for hver harddisk, du sender til Microsoft. 
  
10. Når du har tilføjet og valideret en journalfil for hver harddisk, du sender til Microsoft, skal du klikke på **Næste**.
    
11. Klik på ![Tilføj ikon.](../media/ITPro-EAC-AddIcon.gif) **Vælg tilknytningsfil** for at sende den PST-importtilknytningsfil, du oprettede i trin 3. 

    ![Klik på Vælg tilknytningsfil for at sende den CSV-fil, du oprettede til importjobbet.](../media/d30b1d73-80bb-491e-a642-a21673d06889.png)
  
12. Når navnet på CSV-filen vises under **Tilknytning af filnavn**, skal du klikke på **Valider** for at kontrollere, om der er fejl i CSV-filen. 

    ![Klik på Valider for at kontrollere, om der er fejl i CSV-filen.](../media/4680999d-5538-4059-b878-2736a5445037.png)
  
    CSV-filen skal valideres korrekt for at oprette et PST-importjob. Filnavnet ændres til grønt, når det er valideret. Hvis valideringen mislykkes, skal du klikke på linket **Vis log** . Der åbnes en valideringsfejlrapport med en fejlmeddelelse for hver række i filen, der mislykkedes. 

13. Når PST-tilknytningsfilen er valideret, skal du klikke på **Næste**.

14. Skriv dine kontaktoplysninger i de relevante felter på siden **Angiv kontaktoplysninger** . 

    Adressen for den Microsoft-placering, du sender dine harddiske til, vises. Denne adresse genereres automatisk på baggrund af placeringen af dit Microsoft-datacenter. Kopiér denne adresse til en fil, eller tag et skærmbillede.

15. Læs dokumentet med vilkår og betingelser, klik på afkrydsningsfeltet, og klik derefter på **Gem** for at sende importjobbet. 

    Når importjobbet er oprettet, vises der en statusside, der forklarer de næste trin i forsendelsesprocessen.

16. Klik på ![ikonet Opdater under fanen **Importér**.](../media/O365-MDM-Policy-RefreshIcon.gif) **Opdater** for at få vist det nye drev for afsendelsesimportjob på listen over importjob. Status angives til **Venter på sporingsnummer**. Du kan også klikke på importjobbet for at få vist statusvinduet, som indeholder mere detaljerede oplysninger om importjobbet.

## <a name="step-5-ship-the-hard-drive-to-microsoft"></a>Trin 5: Send harddisken til Microsoft

Næste trin er at sende harddisken til Microsoft og derefter angive sporingsnummeret for forsendelses- og returforsendelsesoplysningerne for drevforsendelsesjobbet. Når drevet er modtaget af Microsoft, tager det mellem 7 og 10 arbejdsdage for datacenterpersonalet at uploade dine PST-filer til Azure Storage område for din organisation.
  
> [!NOTE]
> Hvis du ikke angiver sporingsnummeret og returvareleveranceoplysningerne inden for 14 dage efter oprettelsen af importjobbet, udløber importjobbet. Hvis det sker, skal du oprette et nyt drev for afsendelsesimportjob (se [Trin 4: Opret et PST-importjob i Office 365](#step-4-create-a-pst-import-job-in-office-365)) og sende drevfilen og PST-importtilknytningsfilen igen.
  
### <a name="ship-the-hard-drive"></a>Send harddisken

Vær opmærksom på følgende ting, når du sender harddiske til Microsoft:
  
- Send ikke SATA-til-USB-adapteren. Du behøver kun at sende harddisken.

- Pak harddisken korrekt. brug f.eks. en antistatisk pose eller bobleombrydning.

- Brug en leveringsudbyder efter eget valg til at sende harddisken til Microsoft.

- Send harddisken til adressen for den Microsoft-placering, der blev vist, da du oprettede importjobbet i trin 4. Sørg for at medtage "Office 365 Import Service" i leveringsadressen.

- Når du har leveret harddisken, skal du skrive navnet på leveringsfirmaet og sporingsnummeret ned. Du skal angive disse i næste trin.
    
### <a name="enter-the-tracking-number-and-other-shipping-information"></a>Angiv sporingsnummeret og andre forsendelsesoplysninger

Når du har leveret harddisken til Microsoft, skal du fuldføre følgende procedure på siden Importér tjeneste.
  
1. Gå til , <https://compliance.microsoft.com> og log på med legitimationsoplysningerne for en administratorkonto i din organisation.

2. Klik på **DatalivscyklusstyringImportér** >  i venstre navigationsrude i overholdelsesportalen.

3. Klik på jobbet for den drevleverance, du vil angive sporingsnummeret for, under fanen **Importér** .

4. På status-pop op-siden skal du klikke på **Angiv sporingsnummer**.

5. Angiv følgende forsendelsesoplysninger:

   1. **Leveringsudbyder** Skriv navnet på den leveringsudbyder, du brugte til at sende harddisken til Microsoft. 

   2. **Sporingsnummer** Skriv sporingsnummeret for harddiskleverancen. 

   3. **Kontonummer for returudbyder** Skriv din organisations kontonummer for den operatør, der er angivet under **Return carrier**. Microsoft bruger (og opkræver) denne konto til at sende din harddisk tilbage til dig. Organisationer i USA og Europa skal have en konto hos FedEx. Organisationer i Asien og resten af verden, skal have en konto hos DHL.

6. Klik på **Gem** for at gemme disse oplysninger til importjobbet. 

    Klik på ![ikonet Opdater under fanen **Importér**.](../media/O365-MDM-Policy-RefreshIcon.gif) **Opdater** for at opdatere oplysningerne for dit drev til import af forsendelse. Bemærk, at status nu er angivet til **Drev under overførsel**.

## <a name="step-6-filter-data-and-start-the-pst-import-job"></a>Trin 6: Filtrer data, og start PST-importjobbet

Når din harddisk er modtaget af Microsoft, ændres status for importjobbet på siden **Importér PST-filer** til **Modtagne drev**. Datacenterpersonalet bruger oplysningerne i journalfilen til at uploade dine PST-filer til det Azure Storage område for din organisation. På dette tidspunkt ændres status til **Import i gang**. Som tidligere nævnt tager det mellem 7 og 10 arbejdsdage efter modtagelse af din harddisk at uploade PST-filerne.
  
Når PST-filer er uploadet til Azure, ændres status til **Igangværende analyse**. Dette angiver, at Microsoft 365 analyserer dataene i PST-filerne (på en sikker og sikker måde) for at identificere elementernes alder og de forskellige meddelelsestyper, der er inkluderet i PST-filerne. Når analysen er fuldført, og dataene er klar til at blive importeret, ændres status for importjobbet til **Fuldført analyse**. På dette tidspunkt har du mulighed for at importere alle dataene i PST-filerne, eller du kan trimme de data, der importeres, ved at angive filtre, der styrer, hvilke data der importeres.
  
1. Gå til , <https://compliance.microsoft.com> og log på med legitimationsoplysningerne for en administratorkonto i din organisation.

2. Klik på Administration \> af **datalivscyklus** **Import****i venstre navigationsrude i overholdelsesportalen.

3. Under fanen **Importér** skal du vælge det importjob, du oprettede i trin 4, og klikke på **Importér for at Office 365**.
  
    Der vises en fly out-side med oplysninger om PST-filerne og andre oplysninger om importjobbet.

4. Klik på **Importér for at Office 365**.

5. Siden **Filtrer dine data** vises. Den indeholder dataindsigt som følge af den analyse, der er udført på PST-filerne af Office 365, herunder oplysninger om dataenes alder. På dette tidspunkt har du mulighed for at filtrere de data, der importeres, eller importere alle dataene, som de er. 

    ![Du kan trimme dataene i PST-filerne eller importere dem alle.](../media/287fc030-99e9-417b-ace7-f64617ea5d4e.png)
  
6. Gør et af følgende:

   1. Hvis du vil trimme de data, du importerer, skal du klikke på **Ja. Jeg vil filtrere dem, før du importerer** dem.

      Du kan finde detaljerede trinvise instruktioner om filtrering af dataene i PST-filerne og derefter starte importjobbet under [Filtrer data, når du importerer PST-filer til Office 365](filter-data-when-importing-pst-files.md).

      Eller

   1. Hvis du vil importere alle data i PST-filerne, skal du klikke på **Nej, jeg vil importere alt** og klikke på **Næste**.

7. Hvis du har valgt at importere alle dataene, skal du klikke på **Importér data** for at starte importjobbet. 

    Status for importjobbet vises på siden **Importér PST-filer** . Klik på ![ikonet Opdater.](../media/O365-MDM-Policy-RefreshIcon.gif) **Opdater** for at opdatere de statusoplysninger, der vises i kolonnen **Status** . Klik på importjobbet for at få vist status-pop op-siden, hvor der vises statusoplysninger om hver PST-fil, der importeres. Når importen er fuldført, og PST-filer er importeret til brugerpostkasser, ændres status til **Fuldført**.

## <a name="view-a-list-of-the-pst-files-uploaded-to-microsoft-365"></a>Vis en liste over de PST-filer, der er overført til Microsoft 365

Du kan installere og bruge Microsoft Azure Storage Explorer (som er et gratis værktøj med åben kildekode) til at få vist listen over de PST-filer, vi er uploadet (af Microsofts datacenterpersonale) til Azure Storage område for din organisation. Det kan du gøre for at bekræfte, at PST-filer fra de harddiske, du sendte til Microsoft, blev overført til området Azure Storage.
  
> [!IMPORTANT]
> Du kan ikke bruge Azure Storage Explorer til at uploade eller redigere PST-filer. Den eneste understøttede metode til import af PST-filer til Microsoft 365 er at bruge AzCopy. Du kan heller ikke slette PST-filer, som du har uploadet til Azure-blob. Hvis du forsøger at slette en PST-fil, får du vist en fejlmeddelelse om, at du ikke har de nødvendige tilladelser. Alle PST-filer slettes automatisk fra dit Azure Storage område. Hvis der ikke er nogen igangværende importjob, slettes alle PST-filer i objektbeholderen ** ingestiondata ** 30 dage efter, at det seneste importjob blev oprettet.
  
Udfør følgende trin for at hente URL-adressen til den delte adgangssignatur (SAS) for din organisation. Denne URL-adresse er en kombination af netværks-URL-adressen for den Azure Storage placering i Microsoft-cloudmiljøet for din organisation og en SAS-nøgle. Denne nøgle giver dig de nødvendige tilladelser til at få adgang til organisationens Azure Storage placering.

Sådan installerer du Azure Storage Explorer og opretter forbindelse til dit Azure Storage område:

1. Gå til , <https://compliance.microsoft.com> og log på med legitimationsoplysningerne for en administratorkonto i din organisation.

2. I venstre rude på overholdelsesportalen skal du klikke på Administration  >  af **datalivscyklusImportér**.

3. Klik på ![Tilføj ikon under fanen **Importér**.](../media/ITPro-EAC-AddIcon.gif) **Nyt importjob**.

4. Skriv et navn til PST-importjobbet i guiden til import af job, og klik derefter på **Næste**. Brug små bogstaver, tal, bindestreger og understregningstegn. Du kan ikke bruge store bogstaver eller medtage mellemrum i navnet.

5. Klik på **Upload dine data** på siden **Vælg importjobtype**, og klik derefter på **Næste**.

6. I trin 2 skal du klikke på **Vis SAS URL-adresse til netværksupload**.

7. Når URL-adressen vises, skal du kopiere den og gemme den i en fil. Sørg for at kopiere hele URL-adressen.

    > [!IMPORTANT]
    > Sørg for at tage forholdsregler for at beskytte SAS URL-adressen. Dette kan bruges af alle til at få adgang til Azure-lagerområdet for din organisation.
  
8. Klik på **Annuller** for at lukke guiden importjob.

9. Download og installér [værktøjet Microsoft Azure Storage Explorer](https://go.microsoft.com/fwlink/p/?LinkId=544842).

10. Start Microsoft Azure Storage Explorer, højreklik **Storage Konti** i venstre rude, og klik derefter på **Forbind for at Azure Storage**.

    ![Højreklik på Storage Konti, og klik derefter på Forbind for at Azure Storage.](../media/75b80cc3-c336-4f96-ad32-54ac9b96a7af.png)
  
11. Klik på **Brug en SAS-URI (delt adgangssignatur) eller en forbindelsesstreng,** og klik på **Næste**.

12. Klik på **Brug en SAS URI**, indsæt den SAS-URL-adresse, du fik i trin 1, i feltet under **URI**, og klik derefter på **Næste**.

13. På siden **Forbindelsesoversigt** kan du gennemse forbindelsesoplysningerne og derefter klikke på **Forbind**.

    Databeholderen **for dataindtagelse** åbnes. Den indeholder PST-filerne fra harddisken. Dataobjektbeholderen **til dataindtagelse** er placeret under **Blob-objektbeholdere** **til Storage konti** \> **(SAS-Attached Services).** \>

    ![Azure Storage Explorer viser en liste over de PST-filer, du har overført.](../media/12376fed-13a5-4a09-8fe6-e819e011b334.png)
  
14. Når du er færdig med at bruge Microsoft Azure Storage Explorer, skal du højreklikke på **data om indtagelse** og derefter klikke på **Fjern forbindelse** for at afbryde forbindelsen til dit Azure Storage område. Ellers får du vist en fejl, næste gang du forsøger at vedhæfte. 

    ![Højreklik på indtagelse, og klik på Afbryd forbindelsen for at afbryde forbindelsen til Azure Storage område.](../media/1e8e5e95-4215-4ce4-a13d-ab5f826a0510.png)

## <a name="troubleshooting-tips"></a>Fejlfindingstip

- **Hvad sker der, hvis importjobbet mislykkes på grund af fejl i CSV-tilknytningsfilen til PST-import?** Hvis et importjob mislykkes på grund af fejl i tilknytningsfilen, behøver du ikke at sende harddisken til Microsoft igen for at oprette et importjob. Det skyldes, at PST-filerne fra den harddisk, du har sendt til forsendelsesimportjobbet for drevet, allerede er blevet uploadet til Azure Storage område for din organisation. I dette tilfælde skal du kun rette fejlene i PST Import CSV-tilknytningsfilen og derefter oprette et nyt importjob til netværksupload og sende den reviderede CSV-tilknytningsfil. Hvis du vil oprette og starte et nyt job til import af netværksoverførsler, skal du se [Trin 5: Opret et PST-importjob i Microsoft 365](use-network-upload-to-import-pst-files.md#step-5-create-a-pst-import-job) og [trin 6: Filtrer data, og start jobbet PST-import](use-network-upload-to-import-pst-files.md#step-6-filter-data-and-start-the-pst-import-job) i emnet "Brug netværksupload til at importere PST-filer til Office 365". 
    
    > [!NOTE]
    > Hvis du vil foretage fejlfinding af PST Import CSV-tilknytningsfilen, skal du bruge værktøjet [Azure Storage Explorer](#view-a-list-of-the-pst-files-uploaded-to-microsoft-365) til at få vist mappestrukturen i objektbeholderen **ingestiondata** for PST-filerne fra din harddisk, der blev uploadet til Azure Storage-området. Tilknytning af filfejl skyldes typisk en forkert værdi i FilePath-parameteren. Denne parameter angiver placeringen af en PST-fil i Azure Storage-området. Se beskrivelsen af parameteren FilePath i tabellen i [trin 3](#step-3-create-the-pst-import-mapping-file). Som tidligere forklaret blev placeringen af PST-filer i Azure-lagerområdet angivet af  `/dstdir:` parameteren, da du kørte værktøjet WAImportExport.exe i [trin 2](#step-2-copy-the-pst-files-to-the-hard-drive). 
  
## <a name="more-information"></a>Flere oplysninger

- Drive shipping er en effektiv måde at importere store mængder af arkiveringsmeddelelsesdata på for at Microsoft 365 at drage fordel af de funktioner til overholdelse af angivne standarder, der er tilgængelige for din organisation. Når arkiveringsdata er importeret til brugerpostkasser, kan du:

  - Aktivér [arkivpostkasser](enable-archive-mailboxes.md) og [automatisk udvidelse af arkivering](enable-autoexpanding-archiving.md) for at give brugerne mere postkasselagerplads til dataene. 

  - Placer postkasser i [procesventeposition](./create-a-litigation-hold.md) for at bevare dataene. 

  - Brug Microsoft [eDiscovery-værktøjer](search-for-content.md) til at søge i dataene. 

  - Anvend [Microsoft 365 opbevaringspolitikker](retention.md) for at styre, hvor længe dataene bevares, og hvilken handling der skal udføres, når opbevaringsperioden udløber. 

  - Søg i [overvågningsloggen](search-the-audit-log-in-security-and-compliance.md) efter hændelser, der er relateret til disse data. 

  - Importér data til [inaktive postkasser](inactive-mailboxes-in-office-365.md) for at arkivere data med henblik på overholdelse af angivne standarder. 

  - Beskyt din organisation mod [tab af følsomme](dlp-learn-about-dlp.md) oplysninger. 

- Her er et eksempel på nøglen til sikker lagerkonto og en BitLocker-krypteringsnøgle. Dette eksempel indeholder også syntaksen for den WAImportExport.exe kommando, du kører for at kopiere PST-filer til en harddisk. Sørg for at tage forholdsregler for at beskytte disse, ligesom du ville beskytte adgangskoder eller andre sikkerhedsrelaterede oplysninger.

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

- Som tidligere forklaret aktiverer tjenesten Office 365 Import indstillingen for bevarelse af venteposition (på ubestemt tid), når PST-filer importeres til en postkasse. Det betyder, at egenskaben  *RentionHoldEnabled*  er angivet til  `True` , så den opbevaringspolitik, der er tildelt postkassen, ikke behandles. Dette giver ejeren af postkassen tid til at administrere de nyligt importerede meddelelser ved at forhindre, at en politik for sletning eller arkivering sletter eller arkiverer ældre meddelelser. Her er nogle trin, du kan udføre for at administrere denne opbevarings venteposition: 

  - Efter et bestemt tidsrum kan du slå opbevaringsventetiden fra ved at køre kommandoen  `Set-Mailbox -RetentionHoldEnabled $false` . Du kan finde instruktioner under [Placer en postkasse i opbevaringsventeposition](/exchange/security-and-compliance/messaging-records-management/mailbox-retention-hold).

  - Du kan konfigurere opbevarings ventepositionen, så den er slået fra på en dato i fremtiden. Det gør du ved at køre kommandoen  `Set-Mailbox -EndDateForRetentionHold <date>` . Hvis du f.eks. antager, at dags dato er den 1. juni 2016, og du vil have bevarelsespositionen slået fra om 30 dage, skal du køre følgende kommando:  `Set-Mailbox -EndDateForRetentionHold 7/1/2016`. I dette scenarie skal du lade egenskaben  *RentionHoldEnabled*  være angivet til  *Sand*. Du kan få flere oplysninger under [Set-Mailbox](/powershell/module/exchange/set-mailbox).

  - Du kan ændre indstillingerne for den opbevaringspolitik, der er tildelt postkassen, så ældre elementer, der er importeret, ikke straks slettes eller flyttes til brugerens arkivpostkasse. Du kan f.eks. forlænge opbevaringsalderen for en politik for sletning eller arkivering, der er tildelt postkassen. I dette scenarie skal du deaktivere opbevaringsventepositionen på postkassen, når du har ændret indstillingerne for opbevaringspolitikken. Du kan få flere oplysninger under [Konfigurer en politik for arkiv og sletning for postkasser i din organisation](set-up-an-archive-and-deletion-policy-for-mailboxes.md).
