---
title: Brug et PowerShell-script til at søge i overvågningsloggen
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
description: Brug et PowerShell-script, der kører Search-UnifiedAuditLog-cmdlet'en i Exchange Online til at søge i overvågningsloggen. Dette script er optimeret til at returnere et stort sæt overvågningsposter, hver gang du kører det. Scriptet eksporterer disse poster til en CSV-fil, som du kan få vist eller transformere ved hjælp af Power Query i Excel.
ms.openlocfilehash: fc7f2e8626fd5b510dca08504d91dd0faadd78b6
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64943837"
---
# <a name="use-a-powershell-script-to-search-the-audit-log"></a>Brug et PowerShell-script til at søge i overvågningsloggen

Sikkerhed, overholdelse af angivne standarder og overvågning er blevet en topprioritet for it-administratorer i dagens verden. Microsoft 365 har flere indbyggede funktioner, der kan hjælpe organisationer med at administrere sikkerhed, overholdelse af angivne standarder og overvågning. Unified Audit Logging kan især hjælpe dig med at undersøge sikkerhedshændelser og problemer med overholdelse af angivne standarder. Du kan hente overvågningslogge ved hjælp af følgende metoder:

- [API'en til administration af Office 365](/office/office-365-management-api/office-365-management-activity-api-reference)

- [Søgeværktøjet til overvågningslog](search-the-audit-log-in-security-and-compliance.md) på Microsoft Purview-overholdelsesportalen

- Cmdlet'en [Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog) i Exchange Online PowerShell

Hvis du har brug for at hente overvågningslogge regelmæssigt, bør du overveje en løsning, der bruger API'en Office 365 Management Activity, da den kan give store organisationer skalerbarhed og ydeevne til løbende at hente millioner af overvågningsposter. Brug af søgeværktøjet til overvågningslog i overholdelsesportalen er en god måde hurtigt at finde overvågningsposter for bestemte handlinger, der forekommer inden for et kortere tidsinterval. Hvis du bruger længere tidsintervaller i søgeværktøjet til overvågningslog, især for store organisationer, kan det returnere for mange poster til nemt at administrere eller eksportere.

Når der er situationer, hvor du skal hente overvågningsdata manuelt for en bestemt undersøgelse eller hændelse, især i forbindelse med længere datointervaller i større organisationer, kan det være den bedste løsning at bruge cmdlet'en **Search-UnifiedAuditLog** . Denne artikel indeholder et PowerShell-script, der bruger den cmdlet, der kan hente 50.000 overvågningsposter (hver gang du kører cmdlet'en) og derefter eksportere dem til en CSV-fil, som du kan formatere ved hjælp af Power Query i Excel som en hjælp til din gennemgang. Brug af scriptet i denne artikel minimerer også risikoen for, at store søgninger i overvågningsloggen får timeout i tjenesten.

## <a name="before-you-run-the-script"></a>Før du kører scriptet

- Overvågningslogføring skal være aktiveret, for at din organisation kan bruge scriptet til at returnere overvågningsposter. Overvågningslogføring er som standard slået til for Microsoft 365 og Office 365 virksomhedsorganisationer. Hvis du vil kontrollere, at søgning i overvågningslog er slået til for din organisation, kan du køre følgende kommando i Exchange Online PowerShell:

  ```powershell
  Get-AdminAuditLogConfig | FL UnifiedAuditLogIngestionEnabled
  ```

  Værdien for `True` egenskaben **UnifiedAuditLogIngestionEnabled** angiver, at søgning i overvågningslog er slået til.

- Du skal have tildelt rollen View-Only Overvågningslogge eller Overvågningslogfiler i Exchange Online for at kunne køre scriptet korrekt. Disse roller tildeles som standard til rollegrupperne Administration af overholdelse og Organisationsadministration på siden Tilladelser i <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange Administration</a>. Du kan finde flere oplysninger i afsnittet "Krav til søgning i overvågningsloggen" i [Søg i overvågningsloggen i Overholdelsescenter](search-the-audit-log-in-security-and-compliance.md#before-you-search-the-audit-log).

- Det kan tage lang tid, før scriptet er fuldført. Hvor lang tid det tager at køre, afhænger af datointervallet og størrelsen af det interval, du konfigurerer scriptet til at hente overvågningsposter for. Større datointervaller og mindre intervaller vil resultere i en lang kørselstid. Se tabellen i trin 2 for at få flere oplysninger om datointervallet og intervallerne.

- Eksempelscriptet, der er angivet i denne artikel, understøttes ikke i microsofts standardsupportprogram eller -tjeneste. Eksempelscriptet leveres SOM IS uden nogen form for garanti. Microsoft fraskriver sig yderligere alle stiltiende garantier, herunder, uden begrænsning, eventuelle stiltiende garantier for salgbarhed eller egnethed til et bestemt formål. Hele risikoen som følge af brugen eller ydeevnen af eksempelscriptet og dokumentationen forbliver hos dig. Under ingen omstændigheder må Microsoft, microsofts forfattere eller andre, der er involveret i oprettelse, produktion eller levering af scriptet, være ansvarlige for eventuelle skader overhovedet (herunder, uden begrænsning, skader for tab af forretningsoverskud, forretningsafbrydelser, tab af forretningsoplysninger eller andre økonomiske tab), der opstår som følge af brugen af eller manglende evne til at bruge eksempelscriptet eller dokumentationen,  selv om Microsoft er blevet underrettet om muligheden for sådanne skader.

## <a name="step-1-connect-to-exchange-online-powershell"></a>Trin 1: Forbind at Exchange Online PowerShell

Det første trin er at oprette forbindelse til Exchange Online PowerShell. Du kan oprette forbindelse ved hjælp af moderne godkendelse eller med multifaktorgodkendelse (MFA). Du kan finde en trinvis vejledning under [Forbind til at Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

## <a name="step-2-modify-and-run-the-script-to-retrieve-audit-records"></a>Trin 2: Rediger og kør scriptet for at hente overvågningsposter

Når du har oprettet forbindelse til Exchange Online PowerShell, er næste trin at oprette, redigere og køre scriptet for at hente overvågningsdataene. De første syv linjer i søgescriptet til overvågningsloggen indeholder følgende variabler, som du kan ændre for at konfigurere din søgning. Se tabellen i trin 2 for at få en beskrivelse af disse variabler.

1. Gem følgende tekst i et Windows PowerShell script ved hjælp af et filnavnssuffiks af .ps1. F.eks. SearchAuditLog.ps1.

   ```powershell
   #Modify the values for the following variables to configure the audit log search.
   $logFile = "d:\AuditLogSearch\AuditLogSearchLog.txt"
   $outputFile = "d:\AuditLogSearch\AuditLogRecords.csv"
   [DateTime]$start = [DateTime]::UtcNow.AddDays(-1)
   [DateTime]$end = [DateTime]::UtcNow
   $record = "AzureActiveDirectory"
   $resultSize = 5000
   $intervalMinutes = 60
   
   #Start script
   [DateTime]$currentStart = $start
   [DateTime]$currentEnd = $start
   
   Function Write-LogFile ([String]$Message)
   {
       $final = [DateTime]::Now.ToUniversalTime().ToString("s") + ":" + $Message
       $final | Out-File $logFile -Append
   }
   
   Write-LogFile "BEGIN: Retrieving audit records between $($start) and $($end), RecordType=$record, PageSize=$resultSize."
   Write-Host "Retrieving audit records for the date range between $($start) and $($end), RecordType=$record, ResultsSize=$resultSize"
   
   $totalCount = 0
   while ($true)
   {
       $currentEnd = $currentStart.AddMinutes($intervalMinutes)
       if ($currentEnd -gt $end)
       {
           $currentEnd = $end
       }
   
       if ($currentStart -eq $currentEnd)
       {
           break
       }
   
       $sessionID = [Guid]::NewGuid().ToString() + "_" +  "ExtractLogs" + (Get-Date).ToString("yyyyMMddHHmmssfff")
       Write-LogFile "INFO: Retrieving audit records for activities performed between $($currentStart) and $($currentEnd)"
       Write-Host "Retrieving audit records for activities performed between $($currentStart) and $($currentEnd)"
       $currentCount = 0
   
       $sw = [Diagnostics.StopWatch]::StartNew()
       do
       {
           $results = Search-UnifiedAuditLog -StartDate $currentStart -EndDate $currentEnd -RecordType $record -SessionId $sessionID -SessionCommand ReturnLargeSet -ResultSize $resultSize
   
           if (($results | Measure-Object).Count -ne 0)
           {
               $results | export-csv -Path $outputFile -Append -NoTypeInformation
   
               $currentTotal = $results[0].ResultCount
               $totalCount += $results.Count
               $currentCount += $results.Count
               Write-LogFile "INFO: Retrieved $($currentCount) audit records out of the total $($currentTotal)"
   
               if ($currentTotal -eq $results[$results.Count - 1].ResultIndex)
               {
                   $message = "INFO: Successfully retrieved $($currentTotal) audit records for the current time range. Moving on!"
                   Write-LogFile $message
                   Write-Host "Successfully retrieved $($currentTotal) audit records for the current time range. Moving on to the next interval." -foregroundColor Yellow
                   ""
                   break
               }
           }
       }
       while (($results | Measure-Object).Count -ne 0)
   
       $currentStart = $currentEnd
   }
   
   Write-LogFile "END: Retrieving audit records between $($start) and $($end), RecordType=$record, PageSize=$resultSize, total count: $totalCount."
   Write-Host "Script complete! Finished retrieving audit records for the date range between $($start) and $($end). Total count: $totalCount" -foregroundColor Green
   ```

2. Rediger de variabler, der er angivet i følgende tabel, for at konfigurere søgekriterierne. Scriptet indeholder eksempelværdier for disse variabler, men du skal ændre dem (medmindre andet er angivet) for at opfylde dine specifikke krav.

   <br>

   ****

   |Variabel|Eksempelværdi|Beskrivelse|
   |---|---|---|
   |`$logFile`|"d:\temp\AuditSearchLog.txt"|Angiver navnet på og placeringen af den logfil, der indeholder oplysninger om status for den overvågningslogsøgning, der udføres af scriptet. Scriptet skriver UTC-tidsstempler til logfilen.|
   |`$outputFile`|"d:\temp\AuditRecords.csv"|Angiver navnet på og placeringen af den CSV-fil, der indeholder de overvågningsposter, der returneres af scriptet.|
   |`[DateTime]$start` Og `[DateTime]$end`|[DateTime]::UtcNow.AddDays(-1) <br/>[DateTime]::UtcNow|Angiver datointervallet for søgning i overvågningsloggen. Scriptet returnerer poster for overvågningsaktiviteter, der fandt sted inden for det angivne datointerval. Hvis du f.eks. vil returnere aktiviteter, der udføres i januar 2021, kan du bruge en startdato `"2021-01-01"` og en slutdato `"2021-01-31"` for (sørg for at omgive værdierne i dobbelte anførselstegn) Eksempelværdien i scriptet returnerer poster for aktiviteter, der er udført i de forrige 24 timer. Hvis du ikke medtager et tidsstempel i værdien, er standardtidsstemplet 12:00 (midnat) på den angivne dato.|
   |`$record`|"AzureActiveDirectory"|Angiver posttypen for de overvågningsaktiviteter (også kaldet *handlinger*), der skal søges efter. Denne egenskab angiver den tjeneste eller funktion, som en aktivitet blev udløst i. Du kan se en liste over posttyper, som du kan bruge til denne variabel, under [Overvågningslogposttype](/office/office-365-management-api/office-365-management-activity-api-schema#auditlogrecordtype). Du kan bruge navnet på posttypen eller ENUM-værdien. <br/><br/>**Tip:** Hvis du vil returnere overvågningsposter for alle posttyper, skal du bruge værdien `$null` (uden dobbelte anførselstegnsmærker).|
   |`$resultSize`|5000|Angiver antallet af resultater, der returneres, hver gang **Search-UnifiedAuditLog-cmdlet'en** kaldes af scriptet (kaldes et *resultatsæt*). Værdien af 5.000 er den maksimale værdi, der understøttes af cmdlet'en. Lad denne værdi være, som den er.|
   |`$intervalMinutes`|60|For at hjælpe med at overvinde grænsen på 5000 returnerede poster tager denne variabel det dataområde, du har angivet, og opdeler det i mindre tidsintervaller. Nu er hvert interval, ikke hele datointervallet, underlagt kommandoens grænse på 5000 postoutput. Standardværdien på 5000 poster pr. 60-minutters interval inden for datointervallet bør være tilstrækkelig for de fleste organisationer. Men hvis scriptet returnerer en fejl med teksten , `maximum results limitation reached`skal du reducere tidsintervallet (f.eks. til 30 minutter eller endda 15 minutter) og køre scriptet igen.|
   ||||

   De fleste af de variabler, der er angivet i den forrige tabel, svarer til parametre for cmdlet'en **Search-UnifiedAuditLog** . Du kan finde flere oplysninger om disse parametre under [Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog).

3. Åbn Windows PowerShell på din lokale computer, og gå til den mappe, hvor du gemte det ændrede script.

4. Kør scriptet i Exchange Online PowerShell, f.eks.:

   ```powershell
   .\SearchAuditLog.ps1
   ```

Scriptet viser statusmeddelelser, mens det kører. Når scriptet er færdigt, oprettes logfilen og den CSV-fil, der indeholder overvågningsposterne, og de gemmes i de mapper, der er defineret af variablerne `$logFile` og `$outputFile` .

> [!IMPORTANT]
> Der er en grænse på 50.000 for det maksimale antal overvågningsposter, der returneres, hver gang du kører cmdlet'en i scriptet. Hvis du kører dette script, og det returnerer 50.000 resultater, er det sandsynligt, at overvågningsposter for aktiviteter, der fandt sted inden for datointervallet, ikke blev medtaget. Hvis det sker, anbefaler vi, at du opdeler datointervallet i mindre varigheder og derefter kører scriptet igen for hvert datointerval. Hvis et datointerval på f.eks. 90 dage returnerer 50.000 resultater, kan du køre scriptet to gange, én gang for de første 45 dage i datointervallet og derefter igen for de næste 45 dage.

## <a name="step-3-format-and-view-the-audit-records"></a>Trin 3: Formatér og få vist overvågningsposterne

Når du har kørt scriptet og eksporteret overvågningsposterne til en CSV-fil, kan du formatere CSV-filen for at gøre det nemmere at gennemse og analysere overvågningsposterne. En måde at gøre dette på er ved at Power Query JSON-transformeringsfunktion i Excel at opdele hver egenskab i JSON-objektet i kolonnen **AuditData** i sin egen kolonne. Du kan finde en trinvis vejledning under "Trin 2: Formatér den eksporterede overvågningslog ved hjælp af Power Query-editor" i [Eksportér, konfigurer og få vist overvågningslogposter](export-view-audit-log-records.md#step-2-format-the-exported-audit-log-using-the-power-query-editor).
