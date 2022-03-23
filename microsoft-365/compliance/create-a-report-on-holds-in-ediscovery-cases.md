---
title: Brug et script til at oprette en rapport over ventende eDiscovery-ventende
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 9/11/2017
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
ms.assetid: cca08d26-6fbf-4b2c-b102-b226e4cd7381
ms.custom:
- seo-marvel-apr2020
description: Få mere at vide om, hvordan du opretter en rapport, der indeholder oplysninger om alle de ventende elementer, der er knyttet til eDiscovery-sager.
ms.openlocfilehash: 568d4fa351879d271004d0f0749881f3de4b4a49
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63587692"
---
# <a name="use-a-script-to-create-a-report-on-holds-in-ediscovery-cases"></a>Brug et script til at oprette en rapport om ventende mails i eDiscovery-sager

Scriptet i denne artikel giver eDiscovery-administratorer og eDiscovery-ledere mulighed for at generere en rapport, der indeholder oplysninger om alle ventende elementer, der er knyttet til Core- og Advanced eDiscovery-sager i Microsoft 365 Overholdelsescenter. Rapporten indeholder oplysninger som f.eks. navnet på den sag, en venteposition er knyttet til, de indholdsplaceringer, der er sat i venteposition, og om ventepositionen er forespørgselsbaseret. Hvis der er tilfælde, der ikke har nogen ventende funktioner, opretter scriptet en ekstra rapport med en liste over sager uden ventende funktioner.

Se afsnittet [Flere oplysninger](#more-information) for at få en detaljeret beskrivelse af oplysningerne i rapporten.

## <a name="admin-requirements-and-script-information"></a>Administratorkrav og scriptoplysninger

- For at generere en rapport om alle eDiscovery-sager i din organisation skal du være eDiscovery-administrator i din organisation. Hvis du er eDiscovery-leder, indeholder rapporten kun oplysninger om de sager, du kan få adgang til. Du kan finde flere oplysninger om eDiscovery-tilladelser [under Tildel eDiscovery-tilladelser](assign-ediscovery-permissions.md).

- Scriptet i denne artikel har minimal fejlhåndtering. Det primære formål er hurtigt at oprette en rapport om de ventende, der er knyttet til eDiscovery-sager i din organisation.

- De eksempelscripts, der er angivet i dette emne, understøttes ikke i nogen Microsoft-standardsupportprogram eller -tjeneste. Eksempelscriptene leveres som de er, uden garantier af nogen art. Microsoft fraskriver sig yderligere alle stiltiende garantier, herunder, men ikke begrænset til stiltiende garantier for salgbarhed eller egnethed til bestemte formål. Den samlede risiko ved anvendelse eller ydeevne af eksempelscripts og dokumentation forbliver hos dig. I intet tilfælde kan Microsoft, dets forfattere eller andre involverede i oprettelse, produktion eller levering af scripts holdes ansvarlige for erstatning (herunder, men ikke begrænset til, erstatning for tabt forretningsfortjenester, driftstab, tabt erhvervsinformation eller andre økonomiske tab) som følge af brug af eller manglende mulighed for at bruge eksempelscripts eller dokumentation,  også selvom Microsoft er blevet underrettet om risikoen for sådanne skader.

## <a name="step-1-connect-to-security--compliance-center-powershell"></a>Trin 1: Forbind til Security & Compliance Center PowerShell

Det første trin er at oprette forbindelse til Security & Compliance Center PowerShell for organisationen. Du kan finde en trinvis vejledning under [Forbind Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell).

## <a name="step-2-run-the-script-to-report-on-holds-associated-with-ediscovery-cases"></a>Trin 2: Kør scriptet for at rapportere om ventende ventende mails, der er knyttet til eDiscovery-sager

Når du har oprettet forbindelse til Security & Compliance Center PowerShell, er næste trin at oprette og køre det script, der indsamler oplysninger om eDiscovery-sager i din organisation.

1. Gem følgende tekst i en Windows PowerShell scriptfil ved hjælp af et filnavnsuffiks af .ps1, f.eks. CaseHoldsReport.ps1.

   ```powershell
   #script begin
   " "
   write-host "***********************************************"
   write-host "   Security & Compliance Center   " -foregroundColor yellow -backgroundcolor darkgreen
   write-host "        eDiscovery cases - Holds report         " -foregroundColor yellow -backgroundcolor darkgreen
   write-host "***********************************************"
   " "
   #prompt users to specify a path to store the output files
   $time=get-date
   $Path = Read-Host 'Enter a folder path to save the report to a .csv file (filename is created automatically)'
   $outputpath=$Path+'\'+'CaseHoldsReport'+' '+$time.day+'-'+$time.month+'-'+$time.year+' '+$time.hour+'.'+$time.minute+'.csv'
   $noholdsfilepath=$Path+'\'+'CaseswithNoHolds'+' '+$time.day+'-'+$time.month+'-'+$time.year+' '+$time.hour+'.'+$time.minute+'.csv'
   #add case details to the csv file
   function add-tocasereport{
   Param([string]$casename,
   [String]$casetype,
   [String]$casestatus,
   [datetime]$casecreatedtime,
   [string]$casemembers,
   [datetime]$caseClosedDateTime,
   [string]$caseclosedby,
   [string]$holdname,
   [String]$Holdenabled,
   [string]$holdcreatedby,
   [string]$holdlastmodifiedby,
   [string]$ExchangeLocation,
   [string]$sharePointlocation,
   [string]$ContentMatchQuery,
   [datetime]$holdcreatedtime,
   [datetime]$holdchangedtime
   )
   $addRow = New-Object PSObject
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Case name" -Value $casename
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Case type" -Value $casetype
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Case status" -Value $casestatus
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Case members" -Value $casemembers
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Case created time" -Value $casecreatedtime
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Case closed time" -Value $caseClosedDateTime
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Case closed by" -Value $caseclosedby
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Hold name" -Value $holdname
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Hold enabled" -Value $Holdenabled
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Hold created by" -Value $holdcreatedby
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Hold last changed by" -Value $holdlastmodifiedby
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Exchange locations" -Value  $ExchangeLocation
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "SharePoint locations" -Value $sharePointlocation
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Hold query" -Value $ContentMatchQuery
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Hold created time (UTC)" -Value $holdcreatedtime
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Hold changed time (UTC)" -Value $holdchangedtime
   $allholdreport = $addRow | Select-Object "Case name","Case type","Case status","Hold name","Hold enabled","Case members", "Case created time","Case closed time","Case closed by","Exchange locations","SharePoint locations","Hold query","Hold created by","Hold created time (UTC)","Hold last changed by","Hold changed time (UTC)"
   $allholdreport | export-csv -path $outputPath -notypeinfo -append -Encoding ascii
   }
   #get information on the cases and pass values to the case report function
   " "
   write-host "Gathering a list of Core eDiscovery cases and holds..."
   " "
   $edc =Get-ComplianceCase -ErrorAction SilentlyContinue
   foreach($cc in $edc)
   {
   write-host "Working on case :" $cc.name
   if($cc.status -eq 'Closed')
   {
   $cmembers = ((Get-ComplianceCaseMember -Case $cc.name).windowsLiveID)-join ';'
   add-tocasereport -casename $cc.name -casetype $cc.casetype -casestatus $cc.Status -caseclosedby $cc.closedby -caseClosedDateTime $cc.ClosedDateTime -casemembers $cmembers
   }
   else{
   $cmembers = ((Get-ComplianceCaseMember -Case $cc.name).windowsLiveID)-join ';'
   $policies = Get-CaseHoldPolicy -Case $cc.Name | %{ Get-CaseHoldPolicy $_.Name -Case $_.CaseId -DistributionDetail}
   if ($policies -ne $NULL)
   {
   foreach ($policy in $policies)
   {
   $rule=Get-CaseHoldRule -Policy $policy.name
   add-tocasereport -casename $cc.name -casetype $cc.casetype -casemembers $cmembers -casestatus $cc.Status -casecreatedtime $cc.CreatedDateTime -holdname $policy.name -holdenabled $policy.enabled -holdcreatedby $policy.CreatedBy -holdlastmodifiedby $policy.LastModifiedBy -ExchangeLocation (($policy.exchangelocation.name)-join ';') -SharePointLocation (($policy.sharePointlocation.name)-join ';') -ContentMatchQuery $rule.ContentMatchQuery -holdcreatedtime $policy.WhenCreatedUTC -holdchangedtime $policy.WhenChangedUTC
   }
   }
   else{
   write-host "No hold policies found in case:" $cc.name -foregroundColor 'Yellow'
   " "
   [string]$cc.name | out-file -filepath $noholdsfilepath -append
   }
   }
   }
   #get information on the cases and pass values to the case report function
   " "
   write-host "Gathering a list of Advanced eDiscovery cases and holds..."
   " "
   $edc =Get-ComplianceCase -CaseType Advanced -ErrorAction SilentlyContinue
   foreach($cc in $edc)
   {
   write-host "Working on case :" $cc.name
   if($cc.status -eq 'Closed')
   {
   $cmembers = ((Get-ComplianceCaseMember -Case $cc.name).windowsLiveID)-join ';'
   add-tocasereport -casename $cc.name -casestatus -casetype $cc.casetype $cc.Status -caseclosedby $cc.closedby -caseClosedDateTime $cc.ClosedDateTime -casemembers $cmembers
   }
   else{
   $cmembers = ((Get-ComplianceCaseMember -Case $cc.name).windowsLiveID)-join ';'
   $policies = Get-CaseHoldPolicy -Case $cc.Name | %{ Get-CaseHoldPolicy $_.Name -Case $_.CaseId -DistributionDetail}
   if ($policies -ne $NULL)
   {
   foreach ($policy in $policies)
   {
   $rule=Get-CaseHoldRule -Policy $policy.name
   add-tocasereport -casename $cc.name -casetype $cc.casetype -casemembers $cmembers -casestatus $cc.Status -casecreatedtime $cc.CreatedDateTime -holdname $policy.name -holdenabled $policy.enabled -holdcreatedby $policy.CreatedBy -holdlastmodifiedby $policy.LastModifiedBy -ExchangeLocation (($policy.exchangelocation.name)-join ';') -SharePointLocation (($policy.sharePointlocation.name)-join ';') -ContentMatchQuery $rule.ContentMatchQuery -holdcreatedtime $policy.WhenCreatedUTC -holdchangedtime $policy.WhenChangedUTC
   }
   }
   else{
   write-host "No hold policies found in case:" $cc.name -foregroundColor 'Yellow'
   " "
   [string]$cc.name | out-file -filepath $noholdsfilepath -append
   }
   }
   }

   " "
   Write-host "Script complete! Report files saved to this folder: '$Path'"
   " "
   #script end
   ```

2. I den Windows PowerShell session, der blev åbnet i trin 1, skal du gå til den mappe, hvor du gemte scriptet.

3. Kør scriptet. for eksempel:

   ```powershell
   .\CaseHoldsReport.ps1
   ```

   Scriptet beder om en destinationsmappe at gemme rapporten i.

4. Skriv det fulde stinavn på mappen, som rapporten skal gemmes i, og tryk derefter på **Enter**.

   > [!TIP]
   > Hvis du vil gemme rapporten i den samme mappe, som scriptet er placeret i, skal du skrive et punktum ("."), når du bliver bedt om en destinationsmappe. Hvis du vil gemme rapporten i en undermappe i den mappe, hvor scriptet er placeret, skal du blot skrive navnet på undermappen.

   Scriptet begynder at indsamle oplysninger om alle eDiscovery-sager i din organisation. Få ikke adgang til rapportfilen, mens scriptet kører. Når scriptet er fuldført, vises der en bekræftelsesmeddelelse i Windows PowerShell session. Når denne meddelelse vises, kan du få adgang til rapporten i den mappe, du angav i trin 4. Rapportens filnavn er `CaseHoldsReport<DateTimeStamp>.csv`.

   Desuden opretter scriptet også en rapport med en liste over sager, der ikke har nogen ventende funktioner. Filnavnet for denne rapport er `CaseswithNoHolds<DateTimeStamp>.csv`.

   Her er et eksempel på at køre CaseHoldsReport.ps1 script.

   ![Outputtet efter at have kørt CaseHoldsReport.ps1 script.](../media/7d312ed5-505e-4ec5-8f06-3571e3524a1a.png)

## <a name="more-information"></a>Flere oplysninger

Sagen indeholder en rapport, der oprettes, når du kører scriptet i denne artikel, indeholder følgende oplysninger om hver venteposition. Som beskrevet tidligere skal du være eDiscovery-administrator for at returnere oplysninger om alle ventende oplysninger i organisationen. Du kan finde flere oplysninger om ventende sager i [eDiscovery-sager](./get-started-core-ediscovery.md).

- Navnet på ventepositionen og navnet på eDiscovery-sagen, som ventepositionen er knyttet til.

- Uanset om ventepositionen er knyttet til en core eller Advanced eDiscovery sag.

- Hvorvidt eDiscovery-sagen er aktiv eller lukket.

- Hvorvidt ventepositionen er aktiveret eller deaktiveret.

- Medlemmerne af eDiscovery-sagen, som ventepositionen er knyttet til. Sagsmedlemmer kan få vist eller administrere en sag afhængigt af de eDiscovery-tilladelser, de har fået tildelt.

- Det klokkeslæt og den dato, hvor sagen blev oprettet.

- Hvis en sag er lukket, kan den person, der lukkede den, samt klokkeslæt og dato, den blev lukket.

- Den Exchange postkasser og SharePoint websteder, der er i venteposition.

- Hvis ventepositionen er forespørgselsbaseret, er forespørgselssyntaksen.

- Det klokkeslæt og den dato, hvor ventepositionen blev oprettet, samt den person, der oprettede den.

- Det klokkeslæt og den dato, hvor ventepositionen sidst blev ændret, og den person, der har ændret den.
