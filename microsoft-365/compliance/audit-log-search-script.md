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
description: Brug et PowerShell-script, der kører Search-UnifiedAuditLog cmdlet'en i Exchange Online til at søge i overvågningsloggen. Dette script er optimeret til at returnere et stort sæt overvågningsposter, hver gang du kører det. Scriptet eksporterer disse poster til en CSV-fil, som du kan få vist eller transformere ved hjælp af Power-forespørgsel Excel.
ms.openlocfilehash: 60f78f5a5eebeaa90f01b4b251d917f178c06ae9
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/13/2021
ms.locfileid: "63592581"
---
# <a name="use-a-powershell-script-to-search-the-audit-log"></a>Brug et PowerShell-script til at søge i overvågningsloggen

Sikkerhed, overholdelse af regler og standarder og overvågning er blevet en topprioritet for it-administratorer i nutidens verden. Microsoft 365 har flere indbyggede funktioner, der kan hjælpe organisationer med at administrere sikkerhed, overholdelse og overvågning. Samlet overvågningslogføring kan især hjælpe dig med at undersøge sikkerhedshændelser og problemer med overholdelse af regler og standarder. Du kan hente overvågningslogfiler ved hjælp af følgende metoder:

- [Den Office 365 Management Activity API](/office/office-365-management-api/office-365-management-activity-api-reference)

- [Søgeværktøjet til overvågningslogfiler](search-the-audit-log-in-security-and-compliance.md) i Microsoft 365 Overholdelsescenter

- [Search-UnifiedAuditLog-cmdlet'en](/powershell/module/exchange/search-unifiedauditlog) i Exchange Online PowerShell

Hvis du har brug for at hente overvågningslogfiler med jævne mellemrum, bør du overveje en løsning, der bruger Office 365 Management Activity API, da det kan give store organisationer mulighed for skalerbarhed og ydeevne til at hente millioner af overvågningsposter løbende. At bruge søgeværktøjet til overvågningslogfiler i Microsoft 365 Overholdelsescenter er en god måde til hurtigt at finde overvågningsposter for bestemte handlinger, der forekommer i kortere tidsinterval. Hvis du bruger længere tidsintervaller i overvågningsloggens søgeværktøj, især for store organisationer, kan det returnere for mange poster til, at det er nemt at administrere eller eksportere.

Når der er situationer, hvor du er nødt til manuelt at hente overvågningsdata for en bestemt undersøgelse eller hændelse, især for længere datointervaller i større organisationer, kan det være den bedste mulighed at bruge **Search-UnifiedAuditLog-cmdlet'en** . Denne artikel indeholder et PowerShell-script, der bruger den cmdlet, der kan hente 50.000 overvågningsposter (hver gang du kører cmdlet'en), og derefter eksportere dem til en CSV-fil, som du kan formatere ved hjælp af Power-forespørgsel i Excel som en hjælp til din gennemgang. Når du bruger scriptet i denne artikel, minimeres risikoen for, at store overvågningslogsøgninger får time out i tjenesten.

## <a name="before-you-run-the-script"></a>Før du kører scriptet

- Overvågningslogføring skal være aktiveret, for at organisationen kan bruge scriptet til at returnere overvågningsposter. Overvågningslogføring er som standard slået til for Microsoft 365 og Office 365 virksomheder. Hvis du vil bekræfte, at søgning i overvågningsloggen er aktiveret for din organisation, kan du køre følgende kommando i Exchange Online PowerShell:

  ```powershell
  Get-AdminAuditLogConfig | FL UnifiedAuditLogIngestionEnabled
  ```

  Værdien af egenskaben `True` **UnifiedAuditLogIngestionEnabled** angiver, at søgning i overvågningsloggen er aktiveret.

- Du skal være tildelt rollen View-Only overvågningslogfiler eller overvågningslogfiler i en Exchange Online at køre scriptet. Disse roller tildeles som standard rollegrupperne Styring af overholdelse og Organisationsadministration på siden Tilladelser <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">i Exchange Administration</a>. Du kan finde flere oplysninger i afsnittet "Krav til søgning i overvågningsloggen" i [Søg i overvågningsloggen i overholdelsescenteret](search-the-audit-log-in-security-and-compliance.md#before-you-search-the-audit-log).

- Det kan tage lang tid, før scriptet er færdigt. Hvor lang tid det tager at køre, afhænger af datointervallet og størrelsen på det interval, du konfigurerer scriptet til at hente overvågningsposter for. Større datointervaller og mindre intervaller medfører lang kørselstid. Se tabellen i trin 2 for at få mere at vide om datointervaller og -intervaller.

- Eksempelscriptet, der er angivet i denne artikel, understøttes ikke i nogen Microsoft-standardsupportprogram eller -tjeneste. Eksempelscriptet leveres som det er, uden garantier af nogen art. Microsoft fraskriver sig yderligere alle stiltiende garantier, herunder, men ikke begrænset til stiltiende garantier for salgbarhed eller egnethed til bestemte formål. Den samlede risiko ved anvendelse eller ydeevne af eksempelscriptet og dokumentationen forbliver hos dig. I intet tilfælde kan Microsoft, dets forfattere eller andre involverede i oprettelse, produktion eller levering af scriptet holdes ansvarlige for erstatning (herunder, men ikke begrænset til, erstatning for tabt forretningsfortjenester, driftstab, tabt erhvervsinformation eller andre økonomiske tab) som følge af brug af eller manglende mulighed for at bruge eksempelscriptet eller dokumentationen,  også selvom Microsoft er blevet underrettet om risikoen for sådanne skader.

## <a name="step-1-connect-to-exchange-online-powershell"></a>Trin 1: Forbind til Exchange Online PowerShell

Det første trin er at oprette forbindelse til Exchange Online PowerShell. Du kan oprette forbindelse ved hjælp af moderne godkendelse eller med multifaktorgodkendelse. Du kan finde en trinvis vejledning under Forbind [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

## <a name="step-2-modify-and-run-the-script-to-retrieve-audit-records"></a>Trin 2: Rediger og kør scriptet for at hente overvågningsposter

Når du har oprettet forbindelse til Exchange Online PowerShell, er næste trin at oprette, redigere og køre scriptet for at hente overvågningsdataene. De første syv linjer i overvågningsloggens søgescript indeholder følgende variabler, som du kan ændre for at konfigurere søgningen. Se tabellen i trin 2 for at få en beskrivelse af disse variabler.

1. Gem følgende tekst i et Windows PowerShell ved hjælp af et filnavnsuffiks af .ps1. For eksempel SearchAuditLog.ps1.

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

2. Rediger de variabler, der er angivet i følgende tabel, for at konfigurere søgekriterierne. Scriptet indeholder eksempelværdier for disse variabler, men du skal ændre dem (medmindre andet er angivet) så de opfylder dine specifikke krav.

   <br>

   ****

   |Variabel|Eksempelværdi|Beskrivelse|
   |---|---|---|
   |`$logFile`|"d:\temp\AuditSearchLog.txt"|Angiver navnet og placeringen af logfilen, der indeholder oplysninger om status for søgning i overvågningsloggen, der udføres af scriptet. Scriptet skriver UTC-tidsstempler til logfilen.|
   |`$outputFile`|"d:\temp\AuditRecords.csv"|Angiver navnet og placeringen af csv-filen, der indeholder de overvågningsposter, der returneres af scriptet.|
   |`[DateTime]$start` og `[DateTime]$end`|[DateTime]::UtcNow.AddDays(-1) <br/>[DateTime]::UtcNow|Angiver datointervallet for søgning i overvågningsloggen. Scriptet returnerer poster for overvågningsaktiviteter, der er opstået inden for det angivne datointerval. Hvis du f.eks. vil returnere aktiviteter, der er udført i januar 2021, `"2021-01-01"` `"2021-01-31"` kan du bruge en startdato og en slutdato (husk at omgive værdierne i dobbelte anførselstegn) Eksempelværdien i scriptet returnerer poster for aktiviteter, der er udført inden for de seneste 24 timer. Hvis du ikke medtager et tidsstempel i værdien, er standardtidsstemplet 12:00 (midnat) på den angivne dato.|
   |`$record`|"AzureActiveDirectory"|Angiver posttypen for de overvågningsaktiviteter (også kaldet handlinger *), der* skal søges efter. Denne egenskab angiver den tjeneste eller funktion, som en aktivitet blev udløst i. Du kan finde en liste over de posttyper, du kan bruge til denne variabel, [under Posttypen Overvågningslog](/office/office-365-management-api/office-365-management-activity-api-schema#auditlogrecordtype). Du kan bruge navnet på posttypen eller enUM-værdi. <br/><br/>**Tip!** Hvis du vil returnere overvågningsposter for alle posttyper, skal du bruge værdien `$null` (uden dobbelte anførselstegn).|
   |`$resultSize`|5000|Angiver antallet af returnerede resultater, hver gang cmdlet'en **Search-UnifiedAuditLog** kaldes af scriptet (kaldes *et resultatsæt*). Værdien 5.000 er den maksimale værdi, der understøttes af cmdlet'en. Lad denne værdi være, som den er.|
   |`$intervalMinutes`|60|For at hjælpe med at overkomme grænsen på 5.000 returnerede poster tager denne variabel det dataområde, du har angivet, og opdeler det i mindre tidsintervaller. Nu er hvert interval, ikke hele datointervallet, underlagt kommandoens 5000 postoutputbegrænsning. Standardværdien for 5000 poster pr. 60-minutters interval inden for datointervallet skal være tilstrækkelig for de fleste organisationer. Men hvis scriptet returnerer en fejl, hvor der står , `maximum results limitation reached`skal du reducere tidsintervallet (f.eks. til 30 minutter eller endda 15 minutter) og køre scriptet igen.|
   ||||

   De fleste af de variabler, der er angivet i den forrige tabel, svarer til parametrene for **Search-UnifiedAuditLog-cmdlet'en** . Du kan finde flere oplysninger om disse parametre [under Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog).

3. Åbn scriptet på din lokale computer Windows PowerShell og gå til den mappe, hvor du gemte det ændrede script.

4. Kør scriptet i Exchange Online PowerShell, f.eks.:

   ```powershell
   .\SearchAuditLog.ps1
   ```

Scriptet viser statusmeddelelser, mens det kører. Når scriptet er færdigt med at køre, oprettes `$logFile` `$outputFile` logfilen og CSV-filen, der indeholder overvågningsposterne, og gemmes i de mapper, der er defineret af variablerne og defineret.

> [!IMPORTANT]
> Der er en grænse på 50.000 for det maksimale antal overvågningsposter, der returneres, hver gang du kører cmdlet'en i scriptet. Hvis du kører dette script, og det returnerer 50.000 resultater, er det sandsynligt, at overvågningsposter for aktiviteter, der fandt sted inden for datointervallet, ikke blev medtaget. Hvis dette sker, anbefaler vi, at du opdeler datointervallet i mindre varigheder og derefter kører scriptet igen for hvert datointerval. Hvis et datointerval på 90 dage f.eks. returnerer 50.000 resultater, kan du køre scriptet igen to gange, én gang for de første 45 dage i datointervallet og derefter igen i de næste 45 dage.

## <a name="step-3-format-and-view-the-audit-records"></a>Trin 3: Formatere og få vist overvågningsposterne

Når du har kørt scriptet og eksporteret overvågningsposterne til en CSV-fil, kan det være en god ide at formatere CSV-filen for at gøre det nemmere at gennemse og analysere overvågningsposterne. En måde at gøre dette på er ved at bruge transformeringsfunktionen JSON i Power Query i Excel til at opdele hver egenskab i JSON-objektet i kolonnen **AuditData** i sin egen kolonne. Du kan finde en trinvis vejledning under "Trin 2: Formatere den eksporterede overvågningslog ved hjælp af Power-forespørgselseditoren" i Eksportér, konfigurere og få vist [overvågningslogposter](export-view-audit-log-records.md#step-2-format-the-exported-audit-log-using-the-power-query-editor).
