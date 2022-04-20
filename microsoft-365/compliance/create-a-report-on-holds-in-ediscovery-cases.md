---
title: Brug et script til at oprette en rapport over eDiscovery-ventepositioner
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
description: Få mere at vide om, hvordan du opretter en rapport, der indeholder oplysninger om alle ventepositioner, der er knyttet til eDiscovery-sager.
ms.openlocfilehash: 98cdad3d125fbeab9afd9d7d99b572e5f0bf7386
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/20/2022
ms.locfileid: "64993200"
---
# <a name="use-a-script-to-create-a-report-on-holds-in-ediscovery-cases"></a>Brug et script til at oprette en rapport om ventepositioner i eDiscovery-sager

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Scriptet i denne artikel gør det muligt for eDiscovery-administratorer og eDiscovery-ledere at generere en rapport, der indeholder oplysninger om alle ventepositioner, der er knyttet til core- og eDiscovery-sager (Premium) i Microsoft Purview-overholdelsesportalen. Rapporten indeholder oplysninger som f.eks. navnet på den sag, som en venteposition er knyttet til, de indholdsplaceringer, der er sat i venteposition, og om ventepositionen er forespørgselsbaseret. Hvis der er sager, der ikke har nogen ventepositioner, opretter scriptet en ekstra rapport med en liste over sager uden venteposition.

Se afsnittet [Flere oplysninger](#more-information) for at få en detaljeret beskrivelse af de oplysninger, der er inkluderet i rapporten.

## <a name="admin-requirements-and-script-information"></a>Administratorkrav og scriptoplysninger

- Hvis du vil generere en rapport over alle eDiscovery-sager i din organisation, skal du være eDiscovery-administrator i din organisation. Hvis du er eDiscovery Manager, indeholder rapporten kun oplysninger om de sager, du har adgang til. Du kan finde flere oplysninger om eDiscovery-tilladelser under [Tildel eDiscovery-tilladelser](assign-ediscovery-permissions.md).

- Scriptet i denne artikel har minimal fejlhåndtering. Det primære formål er hurtigt at oprette en rapport om de ventepositioner, der er knyttet til eDiscovery-sager i din organisation.

- De eksempelscripts, der er angivet i dette emne, understøttes ikke i microsofts standardsupportprogram eller -tjeneste. Eksempelscripts leveres SOM IS uden nogen form for garanti. Microsoft fraskriver sig yderligere alle stiltiende garantier, herunder, uden begrænsning, eventuelle stiltiende garantier for salgbarhed eller egnethed til et bestemt formål. Hele risikoen som følge af brugen eller ydeevnen af eksempelscripts og dokumentationen forbliver hos dig. Under ingen omstændigheder må Microsoft, microsofts ophavsmænd eller andre, der er involveret i oprettelse, produktion eller levering af scripts, være ansvarlige for eventuelle skader overhovedet (herunder, uden begrænsning, skader for tab af forretningsoverskud, forretningsafbrydelser, tab af forretningsoplysninger eller andre økonomiske tab), der opstår som følge af brugen af eller manglende evne til at bruge eksempelscripts eller dokumentation,  selv om Microsoft er blevet underrettet om muligheden for sådanne skader.

## <a name="step-1-connect-to-security--compliance-center-powershell"></a>Trin 1: Opret forbindelse til Security & Compliance Center PowerShell

Det første trin er at oprette forbindelse til Security & Compliance Center PowerShell for din organisation. Du kan finde en trinvis vejledning under [Opret forbindelse til Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell).

## <a name="step-2-run-the-script-to-report-on-holds-associated-with-ediscovery-cases"></a>Trin 2: Kør scriptet for at rapportere om ventepositioner, der er knyttet til eDiscovery-sager

Når du har oprettet forbindelse til Security & Compliance Center PowerShell, er det næste trin at oprette og køre scriptet, der indsamler oplysninger om eDiscovery-sager i din organisation.

1. Gem følgende tekst i en Windows PowerShell-scriptfil ved hjælp af et filnavnssuffiks af .ps1. f.eks. CaseHoldsReport.ps1.

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
   write-host "Gathering a list of eDiscovery (Standard) cases and holds..."
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
   write-host "Gathering a list of eDiscovery (Premium) cases and holds..."
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

2. I Den Windows PowerShell-session, der blev åbnet i trin 1, skal du gå til den mappe, hvor du gemte scriptet.

3. Kør scriptet. f.eks.:

   ```powershell
   .\CaseHoldsReport.ps1
   ```

   Scriptet beder om en destinationsmappe, som rapporten skal gemmes i.

4. Skriv det fulde stinavn på den mappe, rapporten skal gemmes i, og tryk derefter på **Enter**.

   > [!TIP]
   > Hvis du vil gemme rapporten i den samme mappe, som scriptet er placeret i, skal du skrive et punktum ("."), når du bliver bedt om at angive en destinationsmappe. Hvis du vil gemme rapporten i en undermappe i den mappe, hvor scriptet er placeret, skal du blot skrive navnet på undermappen.

   Scriptet begynder at indsamle oplysninger om alle eDiscovery-sager i din organisation. Undlad at få adgang til rapportfilen, mens scriptet kører. Når scriptet er fuldført, vises der en bekræftelsesmeddelelse i Windows PowerShell-sessionen. Når denne meddelelse vises, kan du få adgang til rapporten i den mappe, du angav i trin 4. Filnavnet på rapporten er `CaseHoldsReport<DateTimeStamp>.csv`.

   Derudover opretter scriptet også en rapport med en liste over sager, der ikke har nogen ventepositioner. Filnavnet på denne rapport er `CaseswithNoHolds<DateTimeStamp>.csv`.

   Her er et eksempel på kørsel af CaseHoldsReport.ps1 script.

   ![Outputtet efter kørsel af CaseHoldsReport.ps1 script.](../media/7d312ed5-505e-4ec5-8f06-3571e3524a1a.png)

## <a name="more-information"></a>Flere oplysninger

Sagen indeholder en rapport, der oprettes, når du kører scriptet i denne artikel, indeholder følgende oplysninger om hver venteposition. Som tidligere forklaret skal du være eDiscovery-administrator for at returnere oplysninger om alle ventepositioner i din organisation. Du kan finde flere oplysninger om ventepositioner i [eDiscovery-sager](./get-started-core-ediscovery.md).

- Navnet på ventepositionen og navnet på den eDiscovery-sag, som ventepositionen er knyttet til.

- Angiver, om ventepositionen er knyttet til en Core- eller eDiscovery-sag (Premium).

- Hvorvidt eDiscovery-sagen er aktiv eller lukket.

- Angiver, om ventepositionen er aktiveret eller deaktiveret.

- Medlemmerne af eDiscovery-sagen, som ventepositionen er knyttet til. Sagsmedlemmer kan få vist eller administrere en sag, afhængigt af de eDiscovery-tilladelser, de er blevet tildelt.

- Det klokkeslæt og den dato, hvor sagen blev oprettet.

- Hvis en sag lukkes, den person, der lukkede den, og tidspunktet og datoen for den blev lukket.

- De Exchange postkasser og SharePoint websteder, der er i venteposition.

- Hvis ventepositionen er forespørgselsbaseret, er forespørgselssyntaksen.

- Det klokkeslæt og den dato, hvor ventepositionen blev oprettet, og den person, der oprettede den.

- Det klokkeslæt og den dato, hvor ventepositionen sidst blev ændret, og den person, der ændrede den.
