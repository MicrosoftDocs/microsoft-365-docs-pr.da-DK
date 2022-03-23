---
title: Importere flere eksterne kontakter til Exchange Online
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 6/29/2018
audience: End User
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
- MOP150
ms.assetid: bed936bc-0969-4a6d-a7a5-66305c14e958
ms.custom: admindeeplinkEXCHANGE
description: Få mere at vide om, hvordan administratorer Exchange Online PowerShell og en CSV-fil til at importere flere eksterne kontakter til den globale adresseliste.
ms.openlocfilehash: fbb2d9bb93d9275e662872d945254d6bf27deb92
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/13/2021
ms.locfileid: "63589514"
---
# <a name="bulk-import-external-contacts-to-exchange-online"></a>Importere flere eksterne kontakter til Exchange Online

**Denne artikel gælder for administratorer. Forsøger du at importere kontakter til din egen postkasse? Se [Importere kontakter til Outlook](https://support.office.com/article/bb796340-b58a-46c1-90c7-b549b8f3c5f8)**
   
Har din virksomhed masser af eksisterende forretningskontakter, som du vil medtage i det delte adressekartotek (også kaldet den globale adresseliste) i Exchange Online? Vil du tilføje eksterne kontakter som medlemmer af distributionsgrupper, ligesom du kan med brugere i din virksomhed? Hvis det er ja, kan du bruge Exchange Online PowerShell og en CSV-fil (med kommaseparerede værdier) til at importere flere eksterne kontakter Exchange Online. Det er en tretrinsproces:
  
[Trin 1: Opret en CSV-fil, der indeholder oplysninger om de eksterne kontakter](#step-1-create-a-csv-file-that-contains-information-about-the-external-contacts)

[Trin 2: Opret de eksterne kontakter med PowerShell](#step-2-create-the-external-contacts-with-powershell) 

[Trin 3: Føje oplysninger til egenskaberne for de eksterne kontakter](#step-3-add-information-to-the-properties-of-the-external-contacts)

Når du har fuldført disse trin for at importere kontakter, kan du udføre disse yderligere opgaver:
  
- [Tilføje flere eksterne kontakter](#add-more-external-contacts)
  
- [Skjule eksterne kontakter fra det delte adressekartotek](#hide-external-contacts-from-the-shared-address-book)
  
## <a name="step-1-create-a-csv-file-that-contains-information-about-the-external-contacts"></a>Trin 1: Opret en CSV-fil, der indeholder oplysninger om de eksterne kontakter

Det første trin er at oprette en CSV-fil, der indeholder oplysninger om hver ekstern kontakt, du vil importere til Exchange Online. 
  
1. Kopiér følgende tekst til en tekstfil i Notesblok, og gem den på skrivebordet som en CSV-fil ved hjælp af et filnavnsuffiks af .csv; for eksempel ExternalContacts.csv.
    
    > [!TIP]
    > Hvis dit sprog indeholder specialtegn (f.eks. **å**, **ä** og **ö** på svensk), gemmes CSV-filen med UTF-8-kodning eller en anden Unicode-kodning, når du gemmer filen i Notesblok. 
  
    ```text
    ExternalEmailAddress,Name,FirstName,LastName,StreetAddress,City,StateorProvince,PostalCode,Phone,MobilePhone,Pager,HomePhone,Company,Title,OtherTelephone,Department,CountryOrRegion,Fax,Initials,Notes,Office,Manager
    danp@fabrikam.com,Dan Park,Dan,Park,1234 23rd Ave,Golden,CO,80215,206-111-1234,303-900-1234,555-1212,123-456-7890,Fabrikam,Shipping clerk,555-5555,Shipping,US,123-4567,R.,Good worker,31/1663,Dan Park
    pilar@contoso.com,Pilar Pinilla,Pilar,Pinilla,1234 Main St.,Seattle,WA,98017,206-555-0100,206-555-0101,206-555-0102,206-555-1234,Contoso,HR Manager,206-555-0104,Executive,US,206-555-0105,P.,Technical decision maker,31/1000,Dan Park
    ```

    Den første række (eller kolonneoverskriften) i CSV-filen viser egenskaberne for kontakter, der kan bruges, når du importerer dem til Exchange Online. Hvert egenskabsnavn er adskilt af et komma. Hver række under kolonneoverskriften repræsenterer egenskabsværdierne for import af en enkelt ekstern kontakt. 
    
    > [!NOTE]
    > Denne tekst indeholder eksempeldata, som du kan slette. Men du må ikke slette eller ændre den første række (overskrift). Den indeholder alle egenskaberne for de eksterne kontakter. 
  
2. Åbn CSV-filen i Microsoft Excel for at redigere CSV-filen, fordi det er meget nemmere at bruge Excel til at redigere CSV-filen.
    
3. Opret en række for hver kontakt, du vil importere til Exchange Online. Udfyld så mange af cellerne som muligt. Disse oplysninger vises i det delte adressekartotek for hver kontakt. 
    
    > [!IMPORTANT]
    >  Følgende egenskaber (som er de første fire elementer i kolonneoverskriften) er nødvendige for at oprette en ekstern kontakt og skal være udfyldt i CSV-filen: **EksternEmailAdresse**, **Navn**, **Fornavn**, **Efternavn**. PowerShell-kommandoen, som du kører i trin 2, bruger værdierne for disse egenskaber til at oprette kontakterne. 

## <a name="step-2-create-the-external-contacts-with-powershell"></a>Trin 2: Opret de eksterne kontakter med PowerShell

Næste trin er at bruge den CSV-fil, du oprettede i trin 1, og PowerShell til at importere flere eksterne kontakter, der er angivet i CSV-filen, til at Exchange Online. 
  
1.  Forbind PowerShell til din Exchange Online organisation. Du kan finde en trinvis vejledning under Forbind [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Sørg for at bruge brugernavnet og adgangskoden til din globale administratorkonto, når du opretter forbindelse til Exchange Online PowerShell. 
    
2. Når du forbinder PowerShell til Exchange Online, skal du gå til den skrivebordsmappe, hvor du gemte CSV-filen i trin 1, f.eks`C:\Users\Administrator\desktop`. .
    
3. Kør følgende kommando for at oprette de eksterne kontakter:

    ```powershell
    Import-Csv .\ExternalContacts.csv|%{New-MailContact -Name $_.Name -DisplayName $_.Name -ExternalEmailAddress $_.ExternalEmailAddress -FirstName $_.FirstName -LastName $_.LastName}
    ```

    Det kan tage et stykke tid at oprette de nye kontakter, afhængigt af hvor mange du vil importere. Når kommandoen er færdig med at køre, viser PowerShell en liste over de nye kontakter, der blev oprettet. 
    
4. Hvis du vil have vist de nye eksterne kontakter, skal Exchange Administration (EAC) og derefter klikke **på Modtagere kontakter** \> <a href="https://go.microsoft.com/fwlink/?linkid=2182970" target="_blank">**.**</a> 
    
    > [!TIP]
    > Du kan finde en vejledning til at oprette forbindelse til [EAC Exchange Administration i Exchange Online](/exchange/exchange-admin-center). 
  
5. Hvis det er nødvendigt, **skal du** klikke på Opdater for at opdatere listen og se de eksterne kontakter, der blev importeret. 
    
    De importerede kontakter vises i det delte adressekartotek i Outlook og Outlook på internettet.
    
    > [!NOTE]
    > Du kan også få vist kontakterne i Microsoft 365 Administration ved at gå til **Brugeres** \> **kontakter**. 

## <a name="step-3-add-information-to-the-properties-of-the-external-contacts"></a>Trin 3: Føje oplysninger til egenskaberne for de eksterne kontakter

Når du kører kommandoen i trin 2, oprettes de eksterne kontakter, men de indeholder ikke nogen af de kontakt- eller organisationsoplysninger, som er oplysningerne fra de fleste af cellerne i CSV-filen. Dette skyldes, at når du opretter nye eksterne kontakter, udfyldes kun de påkrævede egenskaber. Du skal ikke bekymre dig, hvis du ikke har udfyldt alle oplysningerne i CSV-filen. Hvis den ikke er der, tilføjes den ikke.
  
1.  Forbind PowerShell til din Exchange Online organisation. Du kan finde en trinvis vejledning under Forbind [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).
    
2. Gå til den skrivebordsmappe, hvor du gemte CSV-filen i trin 1. f.eks. `C:\Users\Administrator\desktop`.
    
3. Kør følgende to kommandoer for at tilføje de andre egenskaber fra CSV-filen til de eksterne kontakter, du oprettede i trin 2.
    
    ```powershell
    $Contacts = Import-CSV .\ExternalContacts.csv
  
    ```

    ```powershell
    $contacts | ForEach {Set-Contact $_.Name -StreetAddress $_.StreetAddress -City $_.City -StateorProvince $_.StateorProvince -PostalCode $_.PostalCode -Phone $_.Phone -MobilePhone $_.MobilePhone -Pager $_.Pager -HomePhone $_.HomePhone -Company $_.Company -Title $_.Title -OtherTelephone $_.OtherTelephone -Department $_.Department -Fax $_.Fax -Initials $_.Initials -Notes  $_.Notes -Office $_.Office -Manager $_.Manager}
    ```

    > [!NOTE]
    > _Parameteret Manager_ kan være problematisk. Hvis cellen er tom i CSV-filen, får du en fejl, og ingen af egenskabsoplysningerne føjes til kontakten. Hvis du ikke behøver at angive en leder, skal du blot slette fra  ` -Manager $_.Manager ` den forrige PowerShell-kommando. 
  
    Det kan tage et stykke tid at opdatere kontakterne, afhængigt af hvor mange du importerede i trin 1. 
    
4. Sådan kontrollerer du, at egenskaberne blev føjet til kontakterne: 
    
1. I <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange Administration skal</a> du gå til **Kontakter for** \> **modtagere**.
    
2. Klik på en kontakt, og klik derefter **på rediger** ![ikonet Rediger.](../media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif) for at få vist kontaktens egenskaber. 
    
Det var det! Brugerne kan se kontakterne og de yderligere oplysninger i adressekartoteket Outlook og Outlook på internettet.
  
## <a name="add-more-external-contacts"></a>Tilføje flere eksterne kontakter

Du kan gentage trin 1 til 3 for at tilføje nye eksterne kontakter Exchange Online. Du eller brugerne i virksomheden kan bare tilføje en ny række i CSV-filen til den nye kontakt. Derefter kan du køre PowerShell-kommandoerne fra trin 2 og trin 3 for at oprette og føje oplysninger til de nye kontakter.
  
> [!NOTE]
> Når du kører kommandoen til at oprette nye kontakter, får du muligvis en fejl, der siger, at de kontakter, der blev oprettet tidligere, allerede findes. Men alle nye kontakter, der føjes til CSV-filen, oprettes. 
  
## <a name="hide-external-contacts-from-the-shared-address-book"></a>Skjule eksterne kontakter fra det delte adressekartotek>

Nogle virksomheder kan kun bruge eksterne kontakter, så de kan tilføjes som medlemmer af distributionsgrupper. I dette scenarie vil de måske skjule eksterne kontakter fra det delte adressekartotek. Sådan gør du:
  
1.  Forbind PowerShell til din Exchange Online organisation. Du kan finde en trinvis vejledning under Forbind [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).
    
2. Kør følgende kommando for at skjule en enkelt ekstern kontakt.
    
    ```powershell
    Set-MailContact <external contact> -HiddenFromAddressListsEnabled $true 
    ```

    Hvis du f.eks. vil skjule Pilar Pinilla fra det delte adressekartotek, skal du køre denne kommando:

    ```powershell
    Set-MailContact "Pilar Pinilla" -HiddenFromAddressListsEnabled $true
    ```

3. Kør denne kommando for at skjule alle eksterne kontakter fra det delte adressekartotek:

    ```powershell
    Get-Contact -ResultSize unlimited -Filter {(RecipientTypeDetails -eq 'MailContact')} | Set-MailContact -HiddenFromAddressListsEnabled $true  
    ```

Når du har skjult dem, vises eksterne kontakter ikke i det delte adressekartotek, men du kan stadig tilføje dem som medlemmer af en distributionsgruppe.