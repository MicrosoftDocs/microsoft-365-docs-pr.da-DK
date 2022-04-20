---
title: Undersøger delvist indekserede elementer i eDiscovery
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
description: Få mere at vide om, hvordan du administrerer delvist indekserede elementer (også kaldet ikke-indekserede elementer) fra Exchange, SharePoint og OneDrive for Business i din organisation.
ms.openlocfilehash: 0cab31f56576cac9cbe7b51ea2cdceb49aff6db9
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/20/2022
ms.locfileid: "64993112"
---
# <a name="investigating-partially-indexed-items-in-ediscovery"></a>Undersøger delvist indekserede elementer i eDiscovery

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

En eDiscovery-søgning, som du kører fra Microsoft Purview-overholdelsesportalen, inkluderer automatisk delvist indekserede elementer i de anslåede søgeresultater, når du kører en søgning. Delvist indekserede elementer er Exchange postkasseelementer og dokumenter på SharePoint og OneDrive for Business websteder, der af en eller anden grund ikke er fuldt indekseret til søgning. De fleste mails og webstedsdokumenter indekseres, fordi de falder inden [for indekseringsgrænserne for mails](limits-for-content-search.md#indexing-limits-for-email-messages). Nogle elementer kan dog overskride disse indekseringsgrænser og vil blive delvist indekseret. Her er andre årsager til, at elementer ikke kan indekseres til søgning og returneres som delvist indekserede elementer, når du kører en eDiscovery-søgning:
  
- Mails har en vedhæftet fil, der ikke kan åbnes, f.eks. billedfiler. dette er den mest almindelige årsag til delvist indekserede mailelementer.

- Der er knyttet for mange filer til en mail.

- En fil, der er knyttet til en mail, er for stor.

- Filtypen understøttes til indeksering, men der opstod en indekseringsfejl for en bestemt fil.

Selvom det varierer, har de fleste organisationers kunder mindre end 1 % indhold efter volumen og mindre end 12 % af indholdet efter størrelse, der er delvist indekseret. Årsagen til forskellen mellem diskenheden i forhold til størrelsen er, at større filer har en højere sandsynlighed for at indeholde indhold, der ikke kan indekseres fuldstændigt.
  
## <a name="why-does-the-partially-indexed-item-count-change-for-a-search"></a>Hvorfor ændres antallet af delvist indekserede elementer for en søgning?

Når du har kørt en eDiscovery-søgning, vises det samlede antal og den samlede størrelse af delvist indekserede elementer på de placeringer, der blev søgt på, i søgeresultatstatistikken, som vises i den detaljerede statistik for søgningen. Bemærk, at disse kaldes  *ikke-indekserede elementer*  i søgestatistikken. Her er et par ting, der påvirker antallet af delvist indekserede elementer, der returneres i søgeresultaterne:
  
- Hvis et element er delvist indekseret og stemmer overens med søgeforespørgslen, medtages det både i antallet (og størrelsen) af søgeresultatelementer og delvist indekserede elementer. Men når resultaterne af den samme søgning eksporteres, medtages elementet kun sammen med et sæt søgeresultater. det er ikke inkluderet som et delvist indekseret element.

- Delvist indekserede elementer, der er placeret på SharePoint og OneDrive websteder, *medtages ikke* i estimatet af delvist indekserede elementer, der vises i den detaljerede statistik for søgningen. Delvist indekserede elementer kan dog eksporteres, når du eksporterer resultaterne af en eDiscovery-søgning. Hvis du f.eks. kun søger på websteder, vil det anslåede antal delvist indekserede elementer være nul.
  
## <a name="calculating-the-ratio-of-partially-indexed-items-in-your-organization"></a>Beregning af forholdet mellem delvist indekserede elementer i din organisation

Hvis du vil forstå din organisations eksponering for delvist indekserede elementer, kan du køre en søgning efter alt indhold i alle postkasser (ved hjælp af en tom nøgleordsforespørgsel). I følgende eksempel er der 1.629.904 (146,46 GB) fuldt indekserede elementer og 10.025 (10.27 GB) delvist indekserede elementer.
  
![Eksempel på søgestatistik, der viser delvist indekserede elementer.](../media/PartiallyIndexedItemsTest.png)
  
Du kan bestemme procentdelen af delvist indekserede elementer ved hjælp af følgende beregninger.
  
 **Sådan beregner du forholdet mellem delvist indekserede elementer i din organisation:**

`(Total number of partially indexed items/Total number of items) x 100`

`(10025/1629904) x 100 = 0.62%`

Ved hjælp af søgeresultaterne fra det forrige eksempel indekseres 0,62 % af alle postkasseelementer delvist.
  
 **Sådan beregner du procentdelen af størrelsen af delvist indekserede elementer i din organisation:**

`(Size of all partially indexed items/Size of all items) x 100`

`(10.27 GB/146.46 GB) x 100 = 7.0%`

I det forrige eksempel er 7 % af den samlede størrelse af postkasseelementer fra delvist indekserede elementer. Som tidligere nævnt har de fleste organisationers kunder mindre end 1 % indhold efter volumen og mindre end 12 % af indholdet efter størrelse, der er delvist indekseret.

## <a name="working-with-partially-indexed-items"></a>Arbejde med delvist indekserede elementer

Hvis du har brug for at undersøge delvist indekserede elementer for at bekræfte, at de ikke indeholder relevante oplysninger, kan du [eksportere en indholdssøgningsrapport](export-a-content-search-report.md) , der indeholder oplysninger om delvist indekserede elementer. Når du eksporterer en indholdssøgningsrapport, skal du sørge for at vælge en af de eksportindstillinger, der indeholder delvist indekserede elementer.
  
![Vælg den anden eller tredje indstilling for at eksportere delvist indekserede elementer.](../media/PartiallyIndexedItemsExportOptions.png)
  
Når du eksporterer eDiscovery-søgeresultater eller en søgerapport ved hjælp af en af disse indstillinger, inkluderer eksporten en rapport med navnet Unindexed Items.csv. Denne rapport indeholder de fleste af de samme oplysninger som ResultsLog.csv-filen. Unindexed Items.csv-filen indeholder dog også to felter, der er relateret til delvist indekserede elementer: **Fejlkoder** og **fejlegenskaber**. Disse felter indeholder oplysninger om indekseringsfejlen for hvert delvist indekserede element. Hvis du bruger oplysningerne i disse to felter, kan det hjælpe dig med at afgøre, om indekseringsfejlen for en bestemt påvirker din undersøgelse eller ej. 

> [!NOTE]
> Unindexed Items.csv-filen indeholder også felter med navnet **Fejltype** og **Fejlmeddelelse**. Disse er ældre felter, der indeholder oplysninger, der ligner oplysningerne i felterne **Fejlkoder** og **Fejlegenskaber** , men med mindre detaljerede oplysninger. Du kan trygt ignorere disse ældre felter.
  
## <a name="errors-related-to-partially-indexed-items"></a>Fejl relateret til delvist indekserede elementer

Fejlkoder består af to oplysninger, fejlen og filtypen. I dette fejl-/filtypepar kan du f.eks.:

```text
 parseroutputsize_xls
```

 `parseroutputsize` er fejlen og `xls` er filtypen for den fil, som fejlen opstod på. I de tilfælde, hvor filtypen ikke blev genkendt, eller filtypen ikke blev anvendt på fejlen, får du vist værdien `noformat` i stedet for filtypen.
  
Følgende er en liste over indekseringsfejl og en beskrivelse af den mulige årsag til fejlen.
  
| Fejlkode | Beskrivelse |
|:-----|:-----|
| `attachmentcount` <br/> |En mail indeholdt for mange vedhæftede filer, og nogle af disse vedhæftede filer blev ikke behandlet.  <br/> |
| `attachmentdepth` <br/> |Indholdsudskifteren og dokumentparseren fandt for mange niveauer af vedhæftede filer indlejret i andre vedhæftede filer. Nogle af disse vedhæftede filer blev ikke behandlet.  <br/> |
| `attachmentrms` <br/> |En vedhæftet fil kunne ikke afkodes, fordi den var RMS-beskyttet.  <br/> |
| `attachmentsize` <br/> |En fil, der er knyttet til en mail, var for stor og kunne ikke behandles.  <br/> |
| `indexingtruncated` <br/> |Når du skriver den behandlede mail til indekset, var en af de egenskaber, der kan indekseres, for stor og afkortet. De afkortede egenskaber er angivet i feltet Fejlegenskaber.  <br/> |
| `invalidunicode` <br/> |En mail indeholdt tekst, der ikke kunne behandles som gyldig Unicode. Indekseringen af dette element er muligvis ufuldstændig.  <br/> |
| `parserencrypted` <br/> |Indholdet af den vedhæftede fil eller mail er krypteret, og Microsoft 365 kunne ikke afkode indholdet.  <br/> |
| `parsererror` <br/> |Der opstod en ukendt fejl under parsing. Dette skyldes typisk en softwarefejl eller et nedbrud af tjenesten.  <br/> |
| `parserinputsize` <br/> |En vedhæftet fil var for stor til, at fortolkeren kunne håndtere den, og fortolkning af den vedhæftede fil blev ikke udført eller blev ikke fuldført.  <br/> |
| `parsermalformed` <br/> |En vedhæftet fil er forkert udformet og kunne ikke håndteres af fortolkeren. Dette resultat kan skyldes gamle filformater, filer oprettet af inkompatibel software, eller virus foregiver at være noget andet end hævdede.  <br/> |
| `parseroutputsize` <br/> |Outputtet fra fortolkning af en vedhæftet fil var for stort og skulle afkortes.  <br/> |
| `parserunknowntype` <br/> |En vedhæftet fil havde en filtype, som Microsoft 365 ikke kunne registrere.  <br/> |
| `parserunsupportedtype` <br/> |En vedhæftet fil havde en filtype, som Office 365 kunne registrere, men fortolkning af denne filtype understøttes ikke.  <br/> |
| `propertytoobig` <br/> |Værdien af en mailegenskab i Exchange Store var for stor til at blive hentet, og meddelelsen kunne ikke behandles. Dette sker typisk kun for brødtekstegenskaben for en mail.  <br/> |
| `retrieverrms` <br/> |Indholdsud hentefunktionen kunne ikke afkode en RMS-beskyttet meddelelse.  <br/> |
| `wordbreakertruncated` <br/> |Der blev identificeret for mange ord i dokumentet under indekseringen. Behandlingen af egenskaben stoppede, da grænsen blev nået, og egenskaben afkortes.  <br/> |

Fejlfelter beskriver, hvilke felter der påvirkes af den behandlingsfejl, der er angivet i feltet Fejlkoder. Hvis du søger i en egenskab, f.eks  `subject` . eller  `participants`, påvirker fejl i meddelelsens brødtekst ikke søgeresultaterne. Dette kan være nyttigt, når du skal finde ud af, præcis hvilke delvist indekserede elementer du skal undersøge nærmere.
  
## <a name="using-a-powershell-script-to-determine-your-organizations-exposure-to-partially-indexed-email-items"></a>Brug af et PowerShell-script til at bestemme din organisations eksponering for delvist indekserede mailelementer

I følgende trin kan du se, hvordan du kører et PowerShell-script, der søger efter alle elementer i alle Exchange postkasser og derefter genererer en rapport om organisationens forhold mellem delvist indekserede mailelementer (efter antal og størrelse) og viser antallet af elementer (og deres filtype) for hver indekseringsfejl, der opstår. Brug beskrivelser af fejlkoder i det forrige afsnit til at identificere indekseringsfejlen.
  
1. Gem følgende tekst i en Windows PowerShell-scriptfil ved hjælp af et filnavnssuffiks af .ps1. f.eks. `PartiallyIndexedItems.ps1`.

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

2. [Opret forbindelse til Security & Compliance Center PowerShell](/powershell/exchange/exchange-online-powershell).

3. I Security & Compliance Center PowerShell skal du gå til den mappe, hvor du gemte scriptet i trin 1, og derefter køre scriptet. f.eks.:

   ```powershell
   .\PartiallyIndexedItems.ps1
   ```

Her er et eksempel på det output, der returneres af scriptet.
  
![Eksempel på output fra script, der genererer en rapport over din organisations eksponering for delvist indekserede mailelementer.](../media/aeab5943-c15d-431a-bdb2-82f135abc2f3.png)

> [!NOTE]
> Bemærk følgende:
>  
> - Det samlede antal og størrelsen på mailelementer og organisationens forhold mellem delvist indekserede mailelementer (efter antal og størrelse).
> 
> - En listefejlkoder og de tilsvarende filtyper, som fejlen opstod for.
  
## <a name="see-also"></a>Se også

[Delvist indekserede elementer i eDiscovery](partially-indexed-items-in-content-search.md)
