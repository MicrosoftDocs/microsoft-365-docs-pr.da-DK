---
title: Ydeevneanalyse til Microsoft Defender Antivirus
description: Beskriver fremgangsmåden til at finjustere ydeevnen for Microsoft Defender Antivirus.
keywords: finjuster, ydeevne, microsoft defender for slutpunkt, defender antivirus
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 91dd3dc8563e7bd443362c47190139101a5ede61
ms.sourcegitcommit: 4c207a9bdbb6c8ba372ae37907ccefca031a49f8
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/09/2022
ms.locfileid: "63598485"
---
# <a name="performance-analyzer-for-microsoft-defender-antivirus"></a>Ydeevneanalyse til Microsoft Defender Antivirus

**Gælder for**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

**Hvad er Microsoft Defender Antivirus ydeevneanalyse?**

I nogle tilfælde kan det være nødvendigt at finjustere ydeevnen for Microsoft Defender Antivirus når den scanner bestemte filer og mapper. Ydeevneanalyse er et kommandolinjeværktøj i PowerShell, der hjælper med at afgøre, hvilke filer, filtypenavne og processer, der kan forårsage problemer med ydeevnen på individuelle slutpunkter. Disse oplysninger kan bruges til bedre at vurdere problemer med ydeevnen og anvende afhjælpningshandlinger.

Nogle af de muligheder, du kan analysere, omfatter:

- Vigtigste filer, der påvirker scanningstiden
- Vigtigste processer, der påvirker scanningstiden
- Vigtigste filtypenavne, der påvirker scanningstiden
- Kombinationer – f.eks. de vigtigste filer pr. filtype, de øverste scanninger pr. fil, de øverste scanninger pr. fil pr. proces

## <a name="running-performance-analyzer"></a>Kørsel af ydeevneanalyse

Processen på højt niveau for kørsel af ydeevneanalyse omfatter følgende trin:

1. Kør ydeevneanalyse for at indsamle en optagelse af Microsoft Defender Antivirus hændelser på slutpunktet.

   > [!NOTE]
   > Ydeevnen for Microsoft Defender Antivirus hændelser af typen **Microsoft-Antimalware-Engine** optages via ydeevneanalysen.

2. Analysér scanningsresultaterne ved hjælp af forskellige optagelsesrapporter.

## <a name="using-performance-analyzer"></a>Brug af ydeevneanalyse

Hvis du vil starte optagelse af systemhændelser, skal du åbne PowerShell i administrativ tilstand og udføre følgende trin:

1. Kør følgende kommando for at starte optagelsen:

   `New-MpPerformanceRecording -RecordTo <recording.etl>`
 
    hvor `-RecordTo` parameter angiver den fulde stiplacering, hvor sporingsfilen gemmes. Du kan finde flere oplysninger om cmdlet [Microsoft Defender Antivirus cmdlet'er](/powershell/module/defender).

2. Hvis der er processer eller tjenester, der mener at påvirke ydeevnen, skal du genskabe situationen ved at udføre de relevante opgaver.

3. Tryk **på Enter** for at stoppe og gemme optagelsen eller **på Ctrl+C** for at annullere optagelsen.

4. Analysér resultaterne ved hjælp af ydeevneanalyseparametret `Get-MpPerformanceReport`. Ved udførelse af kommandoen får `Get-MpPerformanceReport -Path <recording.etl> -TopFiles 3 -TopScansPerFile 10`brugeren f.eks. en liste over top-ti scanninger for de tre øverste filer, der påvirker ydeevnen. 

Du kan finde flere oplysninger om kommandolinjeparametre og -indstillinger i [New-MpPerformanceRecording](#new-mpperformancerecording) og [Get-MpPerformanceReport](#get-mpperformancereport).

> [!NOTE]
> Hvis du får fejlen "Optagelsen kan ikke startes, fordi Windows Performance Recorder allerede optager", når du kører en optagelse, skal du køre følgende kommando for at stoppe den eksisterende sporing med den nye kommando: **wpr -cancel -instancename MSFT_MpPerformanceRecording**

### <a name="performance-tuning-data-and-information"></a>Data og oplysninger til justering af ydeevnen

Baseret på forespørgslen vil brugeren kunne få vist data for scanningsantal, varighed (total/min/gennemsnit/max/median), sti, proces og årsag til scanningen. Billedet nedenfor viser eksempeloutput for en simpel forespørgsel om de øverste 10 filer til scanningspåvirkning. 

:::image type="content" source="images/example-output.png" alt-text="Eksempeloutput for en grundlæggende TopFiles-forespørgsel":::

### <a name="additional-functionality-exporting-and-converting-to-csv-and-json"></a>Yderligere funktionalitet: eksport og konvertering til CSV og JSON

Resultaterne af ydeevneanalyse kan også eksporteres og konverteres til en CSV- eller JSON-fil.
Eksempler, der beskriver processen med at "eksportere" og "konvertere" gennem eksempelkoder, kan du se nedenfor.

#### <a name="for-csv"></a>For CSV

- **Sådan eksporterer du**: `(Get-MpPerformanceReport -Path:.\Repro-Install.etl -Topscans:1000). TopScans | Export-CSV -Path:.\Repro-Install-Scans.csv -Encoding:UTF8 -NoTypeInformation`

- **Sådan konverterer du**: `(Get-MpPerformanceReport -Path:.\Repro-Install.etl -Topscans:100). TopScans | ConvertTo-Csv -NoTypeInformation`

#### <a name="for-json"></a>Til JSON

- **Sådan konverterer du**: `(Get-MpPerformanceReport -Path:.\Repro-Install.etl -Topscans:1000). TopScans | ConvertTo-Json -Depth:1`

### <a name="requirements"></a>Krav
Microsoft Defender Antivirus har følgende forudsætninger:

- Understøttede Windows versioner: Windows 10, Windows 11 og Windows Server 2016 og nyere
- Platformversion: 4.18.2108.7+
- PowerShell-version: PowerShell version 5.1, PowerShell ISE, Remote PowerShell (4.18.2201.10+), PowerShell 7.x (4.18.2201.10+)

## <a name="powershell-reference"></a>PowerShell-reference
Der er to nye PowerShell-cmdlet'er, der bruges til at finjustere ydeevnen Microsoft Defender Antivirus: 

- [New-MpPerformanceRecording](#new-mpperformancerecording)
- [Get-MpPerformanceReport](#get-mpperformancereport)


### <a name="new-mpperformancerecording"></a>New-MpPerformanceRecording

I det følgende afsnit beskrives referencen til den nye PowerShell-cmdlet New-MpPerformanceRecording. Denne cmdlet indsamler en optagelse af ydeevne Microsoft Defender Antivirus scanninger.

#### <a name="syntax-new-mpperformancerecording"></a>Syntaks: New-MpPerformanceRecording

```powershell
New-MpPerformanceRecording -RecordTo <String >
```

#### <a name="description-new-mpperformancerecording"></a>Beskrivelse: New-MpPerformanceRecording
Cmdlet'en `New-MpPerformanceRecording` indsamler en ydeevneoptagelse af Microsoft Defender Antivirus scanninger. Disse optagelseer af ydeevne indeholder Microsoft-Antimalware-Engine- og NT-kerneproceshændelser og kan analyseres efter indsamling ved hjælp af cmdlet'en [Get-MpPerformanceReport](#get-mpperformancereport) .

Denne `New-MpPerformanceRecording` cmdlet giver indsigt i problematiske filer, der kan medføre en forringelse af ydeevnen for Microsoft Defender Antivirus. Dette værktøj leveres "som det er og er" og har ikke til formål at give forslag til udeladelse. Udeladelse kan reducere beskyttelsesniveauet på dine slutpunkter. Eventuelle undtagelser skal defineres med forsigtighed.

Du kan finde flere oplysninger om ydeevneanalyse i [Dokumenter til ydeevneanalyse](/windows-hardware/test/wpt/windows-performance-analyzer) .

> [!IMPORTANT]
> Denne cmdlet kræver administratorrettigheder.

**Understøttede os-versioner**

Windows version 10 og nyere.

> [!NOTE]
> Denne funktion er tilgængelig fra og med platform version 4.18.2108.X og nyere.

#### <a name="examples-new-mpperformancerecording"></a>Eksempler: New-MpPerformanceRecording

##### <a name="example-1-collect-a-performance-recording-and-save-it"></a>Eksempel 1: Indsaml en optagelse af ydeevnen, og gem den

```powershell
New-MpPerformanceRecording -RecordTo:.\Defender-scans.etl
```

Ovenstående kommando indsamler en optagelse af ydeevnen og gemmer den på den angivne sti: **.\Defender-scans.etl**.

##### <a name="example-2-collect-a-performance-recording-for-remote-powershell-session"></a>Eksempel 2: Indsaml en optagelse af ydeevnen for Remote PowerShell-session

```powershell
$s = New-PSSession -ComputerName Server02 -Credential Domain01\User01
New-MpPerformanceRecording -RecordTo C:\LocalPathOnServer02\trace.etl -Session $s
```

Ovenstående kommando indsamler en optagelse af ydeevnen på Server02 (som angivet af argument $s for parametersession) og gemmer den på den angivne sti: **C:\LocalPathOnServer02\trace.etl** på Server02.

#### <a name="parameters-new-mpperformancerecording"></a>Parametre: New-MpPerformanceRecording

##### <a name="-recordto"></a>-RecordTo
Angiver den placering, hvor du vil gemme optagelsen af Microsoft Defender Antimalware-ydeevnen.

```yaml
Type: String
Position: Named
Default value: None
Accept pipeline input: False 
Accept wildcard characters: False
```

##### <a name="-session"></a>-Session 
Angiver det PSSession-objekt, hvori der skal oprettes og gemmes Microsoft Defender Antivirus af ydeevnen. Når du bruger denne parameter, refererer RecordTo-parameteren til den lokale sti på fjerncomputeren. Tilgængelig med Defender-platform version 4.18.2201.10.

```yaml
Type: PSSession[]
Position: 0
Default value: None
Accept pipeline input: False 
Accept wildcard characters: False
```

### <a name="get-mpperformancereport"></a>Get-MpPerformanceReport

I det følgende afsnit beskrives Get-MpPerformanceReport PowerShell-cmdlet'en. Analyserer og rapporterer om Microsoft Defender Antivirus (MDAV) ydeevneoptagelse.

#### <a name="syntax-get-mpperformancereport"></a>Syntaks: Get-MpPerformanceReport

```powershell
Get-MpPerformanceReport    [-Path] <String>
[-TopScans <Int32>]
[-TopFiles  <Int32>
    [-TopScansPerFile <Int32>]
    [-TopProcessesPerFile  <Int32>  
        [-TopScansPerProcessPerFile <Int32>]
    ]
] 
[-TopExtensions  <Int32>
    [-TopScansPerExtension <Int32>]
    [-TopProcessesPerExtension <Int32>
        [-TopScansPerProcessPerExtension <Int32>]
        ]
    [-TopFilesPerExtension  <Int32>
        [-TopScansPerFilePerExtension <Int32>]
        ]
    ] 
]
[-TopProcesses  <Int32>
    [-TopScansPerProcess <Int32>]
    [-TopExtensionsPerProcess <Int32>
        [-TopScansPerExtensionPerProcess <Int32>]
    ]
]
[-TopFilesPerProcess  <Int32>
    [-TopScansPerFilePerProcess <Int32>]
]
[-MinDuration <String>]
```

#### <a name="description-get-mpperformancereport"></a>Beskrivelse: Get-MpPerformanceReport
Cmdlet'en `Get-MpPerformanceReport` analyserer en tidligere indsamlet [Microsoft Defender Antivirus-ydeevneoptagelse (New-MpPerformanceRecording](#new-mpperformancerecording)) og rapporterer de filstier, filtypenavne og processer, der har den største effekt på Microsoft Defender Antivirus-scanninger.

Ydeevneanalyse giver indsigt i problematiske filer, der kan medføre en forringelse af ydeevnen for Microsoft Defender Antivirus. Dette værktøj leveres "SOM det er og er" og har ikke til formål at give forslag til udeladelse. Udeladelse kan reducere beskyttelsesniveauet på dine slutpunkter. Eventuelle undtagelser skal defineres med forsigtighed.

Du kan finde flere oplysninger om ydeevneanalyse i [Dokumenter til ydeevneanalyse](/windows-hardware/test/wpt/windows-performance-analyzer) .

**Understøttede os-versioner**

Windows version 10 og nyere.

> [!NOTE]
> Denne funktion er tilgængelig fra og med platform version 4.18.2108.X og nyere.

#### <a name="examples-get-mpperformancereport"></a>Eksempler: Get-MpPerformanceReport

##### <a name="example-1-single-query"></a>Eksempel 1: Enkelt forespørgsel 

```powershell
Get-MpPerformanceReport -Path:.\Defender-scans.etl -TopScans:20
```

##### <a name="example-2-multiple-queries"></a>Eksempel 2: Flere forespørgsler 

```powershell
Get-MpPerformanceReport -Path:.\Defender-scans.etl -TopFiles:10 -TopExtensions:10 -TopProcesses:10 -TopScans:10
```

##### <a name="example-3-nested-queries"></a>Eksempel 3: Indlejrede forespørgsler 

```powershell
Get-MpPerformanceReport -Path:.\Defender-scans.etl -TopProcesses:10 -TopExtensionsPerProcess:3 -TopScansPerExtensionPerProcess:3
```

##### <a name="example-4-using--minduration-parameter"></a>Eksempel 4: Brug af parameteren -MinDuration

```powershell
Get-MpPerformanceReport -Path:.\Defender-scans.etl -TopScans:100 -MinDuration:100ms
```

#### <a name="parameters-get-mpperformancereport"></a>Parametre: Get-MpPerformanceReport

##### <a name="-minduration"></a>-MinDuration
Angiver minimumvarigheden af scanningen eller den samlede scanningsvarighed for filer, udvidelser og processer, der er inkluderet i rapporten; accepterer værdier som  **0,1234567sec**, **0,1234 ms**, **0.1us** eller en gyldig TimeSpan.

```yaml
Type: String
Position: Named
Default value: None
Accept pipeline input: False 
Accept wildcard characters: False
```

##### <a name="-path"></a>-Sti
Angiver stien/stierne til en eller flere placeringer.

```yaml
Type: String
Position: 0
Default value: None
Accept pipeline input: True
Accept wildcard characters: False
```

### <a name="-topextensions"></a>-TopExtensions 
Angiver, hvor mange udvidelser der skal have output i toppen, sorteret efter "Varighed".

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <a name="-topextensionsperprocess"></a>-TopExtensionsPerProcess 
Angiver, hvor mange filtypenavne der skal vises for hver proces øverst, sorteret efter "Varighed".

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <a name="-topfiles"></a>-TopFiles
Anmoder om en rapport med topfiler og angiver, hvor mange øverste filer, der skal vises, sorteret efter "Varighed".


```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <a name="-topfilesperextension"></a>-TopFilesPerExtension 
Angiver, hvor mange af de øverste filer, der skal vises for hver udvidelse øverst, sorteret efter "Varighed".


```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <a name="-topfilesperprocess"></a>-TopFilesPerProcess
Angiver, hvor mange filer der skal vises øverst for hver proces øverst, sorteret efter "Varighed".

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <a name="-topprocesses"></a>-TopProcesses
Anmoder om en rapport over topprocesser og angiver, hvor mange af de øverste processer, der skal vises, sorteret efter "Varighed".

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <a name="-topprocessesperextension"></a>-TopProcessesPerExtension 
Angiver, hvor mange topprocesser der skal arbejdes med for hver topudvidelse, sorteret efter "Varighed".


```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```


### <a name="-topprocessesperfile"></a>-TopProcessesPerFile
Angiver, hvor mange topprocesser der skal vises for hver øverste fil, sorteret efter "Varighed".


```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <a name="-topscans"></a>-TopScans
Anmoder om en rapport med topscanninger og angiver, hvor mange scanninger der skal vises, sorteret efter "Varighed".


```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```


### <a name="-topscansperextension"></a>-TopScansPerExtension
Angiver, hvor mange scanninger der skal vises for hver topudvidelse, sorteret efter "Varighed".


```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```


### <a name="-topscansperextensionperprocess"></a>-TopScansPerExtensionPerProcess 
Angiver, hvor mange scanninger der skal vises for hver topudvidelse for hver proces øverst, sorteret efter "Varighed".


```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```


### <a name="-topscansperfile"></a>-TopScansPerFile
Angiver, hvor mange scanninger der skal vises for hver øverste fil, sorteret efter "Varighed".


```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <a name="-topscansperfileperextension"></a>-TopScansPerFilePerExtension 
Angiver, hvor mange scanninger der skal vises for hver topfil for hvert filtypenavn, sorteret efter "Varighed".


```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```


### <a name="-topscansperfileperprocess"></a>-TopScansPerFilePerProcess 
Angiver, hvor mange scanninger der er bedst for outputtet for hver af de øverste filer for hver proces øverst, sorteret efter "Varighed".


```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```


### <a name="-topscansperprocess"></a>-TopScansPerProcess 
Angiver, hvor mange scanninger der skal vises for hver topproces i rapporten Top processes, sorteret efter "Varighed".


```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <a name="-topscansperprocessperextension"></a>-TopScansPerProcessPerExtension
Angiver, hvor mange scanninger der er bedst for outputtet for hver proces øverst, sorteret efter "Varighed".


```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <a name="-topscansperprocessperfile"></a>-TopScansPerProcessPerFile
Angiver, hvor mange scanninger der er bedst for outputtet for hver proces øverst, sorteret efter "Varighed".


```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```
