---
title: Undersøgelse af delvist indekserede elementer i eDiscovery
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
ms.assetid: 4e8ff113-6361-41e2-915a-6338a7e2a1ed
ms.custom:
- seo-marvel-apr2020
description: Få mere at vide om, hvordan du administrerer delvist indekserede elementer (også kaldet indekserede elementer) Exchange, SharePoint og OneDrive for Business i organisationen.
ms.openlocfilehash: 308b99b8bcb8d11c53759700d43651e521987948
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63587477"
---
# <a name="investigating-partially-indexed-items-in-ediscovery"></a>Undersøgelse af delvist indekserede elementer i eDiscovery

En eDiscovery-søgning, som du kører fra Microsoft 365 Overholdelsescenter, medtager automatisk delvist indekserede elementer i de anslåede søgeresultater, når du kører en søgning. Delvist indekserede elementer er Exchange postkasseelementer og dokumenter på SharePoint og OneDrive for Business websteder, som af en eller anden grund ikke blev indekseret helt til søgning. De fleste mails og webstedsdokumenter indekseres, fordi de falder inden [for indekseringsgrænserne for mails](limits-for-content-search.md#indexing-limits-for-email-messages). Nogle elementer overskrider dog muligvis disse indekseringsgrænser og bliver delvist indekseret. Her er andre årsager til, at elementer ikke kan indekseres til søgning og returneres som delvist indekserede elementer, når du kører en eDiscovery-søgning:
  
- Mails har en vedhæftet fil, der ikke kan åbnes, f.eks. billedfiler. dette er den mest almindelige årsag til delvist indekserede mailelementer.

- For mange filer vedhæftet en mail.

- En fil, der er vedhæftet en mail, er for stor.

- Filtypen understøttes til indeksering, men der opstod en indekseringsfejl for en bestemt fil.

Selvom det varierer, har de fleste organisationers kunder mindre end 1 % indhold efter volumen og mindre end 12 % indhold efter størrelse, der er delvist indekseret. Årsagen til forskellen mellem lydstyrke og størrelse er, at større filer har en større sandsynlighed for at indeholde indhold, der ikke kan indekseres fuldstændigt.
  
## <a name="why-does-the-partially-indexed-item-count-change-for-a-search"></a>Hvorfor ændres det delvist indekserede elementantal for en søgning?

Når du har kørt en eDiscovery-søgning, vises det samlede antal og størrelsen af delvist indekserede elementer på de placeringer, der blev søgt på, i søgeresultatstatistikken, der vises i den detaljerede statistik for søgningen. Bemærk, at disse  *kaldes unindexed elementer*  i søgestatistikken. Her er nogle ting, der påvirker antallet af delvist indekserede elementer, der returneres i søgeresultaterne:
  
- Hvis et element er delvist indekseret og svarer til søgeforespørgslen, medtages det både i antallet (og størrelsen) af søgeresultatelementer og delvist indekserede elementer. Men når resultaterne af den samme søgning eksporteres, medtages elementet kun i sæt af søgeresultater. er det ikke medtaget som et delvist indekseret element.

- Delvist indekserede elementer, der er placeret i SharePoint- OneDrive-websteder, medtages  ikke i estimatet for delvist indekserede elementer, der vises i den detaljerede statistik for søgningen. Delvist indekserede elementer kan dog eksporteres, når du eksporterer resultaterne af en eDiscovery-søgning. Hvis du f.eks. kun søger efter websteder, vil det anslåede antal delvist indekserede elementer være nul.
  
## <a name="calculating-the-ratio-of-partially-indexed-items-in-your-organization"></a>Beregne forholdet mellem delvist indekserede elementer i organisationen

For at forstå din organisations eksponering for delvist indekserede elementer kan du køre en søgning efter alt indhold i alle postkasser (ved hjælp af en tom nøgleordsforespørgsel). I følgende eksempel er der 1.629.904 (146,46 GB) fuldt indekserede elementer og 10.025 (10,27 GB) delvist indekserede elementer.
  
![Eksempel på søgestatistik, der viser delvist indekserede elementer.](../media/PartiallyIndexedItemsTest.png)
  
Du kan bestemme procentdelen af delvist indekserede elementer ved at bruge følgende beregninger.
  
 **Sådan beregner du forholdet mellem delvist indekserede elementer i organisationen:**

`(Total number of partially indexed items/Total number of items) x 100`

`(10025/1629904) x 100 = 0.62%`

Ved at bruge søgeresultaterne fra det forrige eksempel bliver 0,62 % af alle postkasseelementer delvist indekseret.
  
 **Sådan beregner du procentdelen af størrelsen på delvist indekserede elementer i organisationen:**

`(Size of all partially indexed items/Size of all items) x 100`

`(10.27 GB/146.46 GB) x 100 = 7.0%`

Så i det forrige eksempel er 7 % af den samlede størrelse af postkasseelementer fra delvist indekserede elementer. Som tidligere nævnt har de fleste organisationer kunder mindre end 1 % indhold efter volumen og mindre end 12 % indhold efter størrelse, der er delvist indekseret.

## <a name="working-with-partially-indexed-items"></a>Arbejde med delvist indekserede elementer

Hvis du er nødt til at undersøge delvist indekserede elementer for at validere, at de ikke indeholder relevante oplysninger, kan du [](export-a-content-search-report.md) eksportere en rapport for indholdssøgning, der indeholder oplysninger om delvist indekserede elementer. Når du eksporterer en rapport over indholdssøgning, skal du sørge for at vælge en af eksportindstillingerne, der indeholder delvist indekserede elementer.
  
![Vælg den anden eller tredje mulighed for at eksportere delvist indekserede elementer.](../media/PartiallyIndexedItemsExportOptions.png)
  
Når du eksporterer eDiscovery-søgeresultater eller en søgerapport ved hjælp af en af disse indstillinger, indeholder eksporten en rapport med navnet Unindexed Items.csv. Denne rapport indeholder de fleste af de samme oplysninger som ResultsLog.csv fil; Men filen Unindexed Items.csv også to felter, der er relateret til delvist indekserede elementer: **Fejlmærker** og **Egenskaber for fejl**. Disse felter indeholder oplysninger om indeksfejlen for hvert delvist indekseret element. Hvis du bruger oplysningerne i disse to felter, kan det hjælpe dig med at afgøre, om indekseringsfejlen har en særlig indvirkning på din undersøgelse. 

> [!NOTE]
> Unindexed-Items.csv indeholder også felter med navnet **Fejltype** **og Fejlmeddelelse**. Dette er ældre felter, der indeholder oplysninger, der svarer til oplysningerne i felterne  Fejlmærker og **Fejlegenskaber,** men med mindre detaljerede oplysninger. Du kan roligt ignorere disse ældre felter.
  
## <a name="errors-related-to-partially-indexed-items"></a>Fejl relateret til delvist indekserede elementer

Fejlmærker består af to oplysninger, fejlen og filtypen. I dette fejl/filtype-par:

```text
 parseroutputsize_xls
```

 `parseroutputsize` er fejlen og er `xls` den filtype, fejlen opstod på. I tilfælde hvor filtypen ikke blev genkendt, eller filtypen ikke gælder for fejlen, `noformat` kan du se værdien i stedet for filtypen.
  
Følgende er en liste over indekseringsfejl og en beskrivelse af den mulige årsag til fejlen.
  
| Fejlmærke | Beskrivelse |
|:-----|:-----|
| `attachmentcount` <br/> |Der var for mange vedhæftede filer i en mail, og nogle af disse vedhæftede filer blev ikke behandlet.  <br/> |
| `attachmentdepth` <br/> |Indholds-henteren og dokument-parseren fandt for mange niveauer af vedhæftede filer indlejret i andre vedhæftede filer. Nogle af disse vedhæftede filer blev ikke behandlet.  <br/> |
| `attachmentrms` <br/> |En vedhæftet fil kunne ikke afkode, fordi den var RMS-beskyttet.  <br/> |
| `attachmentsize` <br/> |En fil, der er vedhæftet en mail, var for stor og kunne ikke behandles.  <br/> |
| `indexingtruncated` <br/> |Når du skriver den behandlet mail til indekset, var en af de indekserbare egenskaber for stor og blev afkortet. De afkortede egenskaber er angivet i feltet Fejlegenskaber.  <br/> |
| `invalidunicode` <br/> |En mail indeholdt tekst, der ikke kunne behandles som gyldig Unicode. Indekseringen for dette element kan være ufuldstændig.  <br/> |
| `parserencrypted` <br/> |Indholdet af vedhæftede filer eller mails er krypteret, Microsoft 365 du ikke kunne afkode indholdet.  <br/> |
| `parsererror` <br/> |Der opstod en ukendt fejl under fortolkning. Dette skyldes typisk en softwarefejl eller nedbrud af tjenesten.  <br/> |
| `parserinputsize` <br/> |En vedhæftet fil var for stor til, at parseren kunne håndtere den, og fortolkningen af den vedhæftede fil skete eller blev ikke fuldført.  <br/> |
| `parsermalformed` <br/> |En vedhæftet fil var forkert udformet og kunne ikke håndteres af parseren. Dette resultat kan skyldes gamle filformater, filer, der er oprettet af inkompatibel software, eller virus, der forestiller sig at være noget andet end det, der påstås.  <br/> |
| `parseroutputsize` <br/> |Outputtet fra fortolkningen af en vedhæftet fil var for stort og skulle afkortes.  <br/> |
| `parserunknowntype` <br/> |En vedhæftet fil havde en filtype, Microsoft 365 kunne finde.  <br/> |
| `parserunsupportedtype` <br/> |En vedhæftet fil havde en filtype, Office 365 kunne registrere, men fortolkning af den pågældende filtype understøttes ikke.  <br/> |
| `propertytoobig` <br/> |Værdien af en mailegenskab i Exchange Store var for stor til at kunne hentes, og meddelelsen kunne ikke behandles. Dette sker typisk kun for brødtekstegenskaben for en mail.  <br/> |
| `retrieverrms` <br/> |Indholdsstyring kunne ikke afkode en RMS-beskyttet meddelelse.  <br/> |
| `wordbreakertruncated` <br/> |Der blev identificeret for mange ord i dokumentet under indekseringen. Behandlingen af egenskaben standses, når grænsen er nået, og egenskaben afkortes.  <br/> |

Fejlfelter beskriver, hvilke felter der påvirkes af den behandlingsfejl, der er angivet i feltet Fejlmærker. Hvis du søger efter en egenskab  `subject`  `participants`, f.eks. eller , påvirker fejl i meddelelsens brødtekst ikke resultaterne af søgningen. Dette kan være nyttigt, når du beslutter, præcist hvilke delvist indekserede elementer, der skal undersøges yderligere.
  
## <a name="using-a-powershell-script-to-determine-your-organizations-exposure-to-partially-indexed-email-items"></a>Brug af et PowerShell-script til at bestemme din organisations eksponering for delvist indekserede mailelementer

Følgende trin viser dig, hvordan du kører et PowerShell-script, der søger efter alle elementer i alle Exchange-postkasser og derefter genererer en rapport om organisationens forhold mellem delvist indekserede mailelementer (efter antal og størrelse) og viser antallet af elementer (og deres filtype) for hver indeksfejl, der opstår. Brug beskrivelserne af fejlkoden i forrige afsnit til at identificere indekseringsfejlen.
  
1. Gem følgende tekst i en Windows PowerShell scriptfil ved hjælp af et filnavnsuffiks af .ps1, f.eks. `PartiallyIndexedItems.ps1`.

   ```powershell
     write-host "**************************************************"
     write-host "     Security & Compliance Center PowerShell      " -foregroundColor yellow -backgroundcolor darkgreen
     write-host "   eDiscovery Partially Indexed Item Statistics   " -foregroundColor yellow -backgroundcolor darkgreen
     write-host "**************************************************"
     " " 
     # Create a search with Error Tags Refinders enabled
     Remove-ComplianceSearch "RefinerTest" -Confirm:$false -ErrorAction 'SilentlyContinue'
     New-ComplianceSearch -Name "RefinerTest" -ContentMatchQuery "size>0" -RefinerNames ErrorTags -ExchangeLocation ALL
     Start-ComplianceSearch "RefinerTest"
     # Loop while search is in progress
     do{
         Write-host "Waiting for search to complete..."
         Start-Sleep -s 5
         $complianceSearch = Get-ComplianceSearch "RefinerTest"
     }while ($complianceSearch.Status -ne 'Completed')
     $refiners = $complianceSearch.Refiners | ConvertFrom-Json
     $errorTagProperties = $refiners.Entries | Get-Member -MemberType NoteProperty
     $partiallyIndexedRatio = $complianceSearch.UnindexedItems / $complianceSearch.Items
     $partiallyIndexedSizeRatio = $complianceSearch.UnindexedSize / $complianceSearch.Size
     " "
     "===== Partially indexed items ====="
     "         Total          Ratio"
     "Count    {0:N0}{1:P2}" -f $complianceSearch.Items.ToString("N0").PadRight(15, " "), $partiallyIndexedRatio
     "Size(GB) {0:N2}{1:P2}" -f ($complianceSearch.Size / 1GB).ToString("N2").PadRight(15, " "), $partiallyIndexedSizeRatio
     " "
     Write-Host ===== Reasons for partially indexed items =====
     foreach($errorTagProperty in $errorTagProperties)
     {
         $name = $refiners.Entries.($errorTagProperty.Name).Name
         $count = $refiners.Entries.($errorTagProperty.Name).TotalCount
         $frag = $name.Split("{_}")
         $errorTag = $frag[0]
         $fileType = $frag[1]
         if ($errorTag -ne $lastErrorTag)
         {
             $errorTag
         }
         "    " + $fileType + " => " + $count
         $lastErrorTag = $errorTag
     }
   ```

2. [Forbind til Security & Compliance Center PowerShell](/powershell/exchange/exchange-online-powershell).

3. I Security & Compliance Center PowerShell skal du gå til den mappe, hvor du gemte scriptet i trin 1, og derefter køre scriptet. for eksempel:

   ```powershell
   .\PartiallyIndexedItems.ps1
   ```

Her er et eksempel på det output, der returneres af scriptet.
  
![Eksempel på output fra script, der genererer en rapport om din organisations eksponering for delvist indekserede mailelementer.](../media/aeab5943-c15d-431a-bdb2-82f135abc2f3.png)

> [!NOTE]
> Bemærk følgende:
>  
> - Det samlede antal og størrelsen af mailelementer og organisationens forhold mellem delvist indekserede mailelementer (efter antal og størrelse).
> 
> - En liste med fejlmærker og de tilsvarende filtyper, hvor fejlen opstod.
  
## <a name="see-also"></a>Se også

[Delvist indekserede elementer i eDiscovery](partially-indexed-items-in-content-search.md)
