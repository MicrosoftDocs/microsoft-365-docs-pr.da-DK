---
title: Effektivitetsanalyse til Microsoft Defender Antivirus
description: Beskriver proceduren til justering af ydeevnen for Microsoft Defender Antivirus.
keywords: tune, performance, microsoft defender for endpoint, defender antivirus
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
ms.openlocfilehash: 558358cca679d9600f9a95c13c4fac6147764b75
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/10/2022
ms.locfileid: "66013348"
---
# <a name="performance-analyzer-for-microsoft-defender-antivirus"></a>Effektivitetsanalyse til Microsoft Defender Antivirus

**Gælder for**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Antivirus

**Platforme**
- Windows

## <a name="what-is-microsoft-defender-antivirus-performance-analyzer"></a>Hvad er Microsoft Defender Antivirus effektivitetsanalyse?

I nogle tilfælde skal du muligvis tilpasse ydeevnen for Microsoft Defender Antivirus, når den scanner bestemte filer og mapper. Effektivitetsanalyse er et PowerShell-kommandolinjeværktøj, der hjælper med at bestemme, hvilke filer, filtypenavne og processer der kan medføre problemer med ydeevnen på individuelle slutpunkter. Disse oplysninger kan bruges til bedre at vurdere problemer med ydeevnen og anvende afhjælpningshandlinger.

Nogle af de indstillinger, der skal analyseres, omfatter:

- De mest populære filer, der påvirker scanningstiden
- De vigtigste processer, der påvirker scanningstiden
- De mest populære filtypenavne, der påvirker scanningstiden
- Kombinationer – f.eks. topfiler pr. filtypenavn, topscanninger pr. fil, topscanninger pr. fil pr. proces

## <a name="running-performance-analyzer"></a>Kørsel af Effektivitetsanalyse

Processen på højt niveau for kørsel af effektivitetsanalyse omfatter følgende trin:

1. Kør Effektivitetsanalyse for at indsamle en ydelsesoptagelse af Microsoft Defender Antivirus hændelser på slutpunktet.

   > [!NOTE]
   > Ydeevnen for Microsoft Defender Antivirus hændelser af typen **Microsoft-Antimalware-Engine** registreres via effektivitetsanalysen.

2. Analysér scanningsresultaterne ved hjælp af forskellige optagelsesrapporter.

## <a name="using-performance-analyzer"></a>Brug af Effektivitetsanalyse

Hvis du vil starte optagelsen af systemhændelser, skal du åbne PowerShell i administrativ tilstand og udføre følgende trin:

1. Kør følgende kommando for at starte optagelsen:

   `New-MpPerformanceRecording -RecordTo <recording.etl>`

    hvor `-RecordTo` parameteren angiver den fulde stiplacering, hvor sporingsfilen gemmes. Du kan få flere cmdlet-oplysninger [under Microsoft Defender Antivirus cmdlet'er](/powershell/module/defender).

2. Hvis processer eller tjenester menes at påvirke ydeevnen, skal du genskabe situationen ved at udføre de relevante opgaver.

3. Tryk på **ENTER** for at stoppe og gemme optagelsen, eller tryk på **Ctrl+C** for at annullere optagelsen.

4. Analysér resultaterne ved hjælp af parameteren for effektivitetsanalysen `Get-MpPerformanceReport`. Ved udførelse af kommandoen `Get-MpPerformanceReport -Path <recording.etl> -TopFiles 3 -TopScansPerFile 10`får brugeren f.eks. vist en liste over top-10-scanninger for de øverste 3 filer, der påvirker ydeevnen.

Du kan få flere oplysninger om kommandolinjeparametre og -indstillinger i [New-MpPerformanceRecording](#new-mpperformancerecording) and [Get-MpPerformanceReport](#get-mpperformancereport).

> [!NOTE]
> Hvis du får vist fejlmeddelelsen "Der kan ikke startes en optagelse af ydeevnen, fordi Windows Performance Recorder allerede optager" under kørsel af en optagelse, skal du køre følgende kommando for at stoppe den eksisterende sporing med den nye kommando: **wpr -cancel -instancename MSFT_MpPerformanceRecording**

## <a name="performance-tuning-data-and-information"></a>Justering af ydeevnedata og -oplysninger

Baseret på forespørgslen kan brugeren få vist data for antal scanninger, varighed (total/min/average/max/median), sti, proces og årsag til scanning. Billedet nedenfor viser eksempeloutputtet for en enkel forespørgsel af de 10 øverste filer med henblik på scanningseffekt.

:::image type="content" source="images/example-output.png" alt-text="Eksempel på output for en grundlæggende TopFiles-forespørgsel" lightbox="images/example-output.png":::

## <a name="additional-functionality-exporting-and-converting-to-csv-and-json"></a>Yderligere funktionalitet: eksport og konvertering til CSV og JSON

Resultaterne af effektivitetsanalysen kan også eksporteres og konverteres til en CSV- eller JSON-fil.
Du kan finde eksempler, der beskriver processen med at "eksportere" og "konvertere" via eksempelkoder, nedenfor.

### <a name="for-csv"></a>Til CSV

- **Sådan eksporterer du**: `(Get-MpPerformanceReport -Path:.\Repro-Install.etl -Topscans:1000). TopScans | Export-CSV -Path:.\Repro-Install-Scans.csv -Encoding:UTF8 -NoTypeInformation`

- **Sådan konverterer du**: `(Get-MpPerformanceReport -Path:.\Repro-Install.etl -Topscans:100). TopScans | ConvertTo-Csv -NoTypeInformation`

### <a name="for-json"></a>For JSON

- **Sådan konverterer du**: `(Get-MpPerformanceReport -Path:.\Repro-Install.etl -Topscans:1000). TopScans | ConvertTo-Json -Depth:1`

Hvis du vil sikre, at maskinlæsbart output til eksport med andre databehandlingssystemer, anbefales det at bruge parameteren -Raw for Get-MpPerformanceReport. Se nedenfor for at få flere oplysninger

## <a name="requirements"></a>Krav

Microsoft Defender Antivirus effektivitetsanalyse har følgende forudsætninger:

- Understøttede Windows versioner: Windows 10, Windows 11 og Windows Server 2016 og nyere
- Platformversion: 4.18.2108.7+
- PowerShell-version: PowerShell Version 5.1, PowerShell ISE, remote PowerShell (4.18.2201.10+), PowerShell 7.x (4.18.2201.10+)

## <a name="powershell-reference"></a>PowerShell-reference

Der er to nye PowerShell-cmdlet'er, der bruges til at justere ydeevnen for Microsoft Defender Antivirus:

- [Ny-MpPerformanceRecording](#new-mpperformancerecording)
- [Get-MpPerformanceReport](#get-mpperformancereport)

### <a name="new-mpperformancerecording"></a>New-MpPerformanceRecording

I følgende afsnit beskrives referencen til den nye PowerShell-cmdlet New-MpPerformanceRecording. Denne cmdlet indsamler en ydeevneoptagelse af Microsoft Defender Antivirus scanninger.

#### <a name="syntax-new-mpperformancerecording"></a>Syntaks: New-MpPerformanceRecording

```powershell
New-MpPerformanceRecording -RecordTo <String >
```

#### <a name="description-new-mpperformancerecording"></a>Beskrivelse: New-MpPerformanceRecording

Cmdlet'en `New-MpPerformanceRecording` indsamler en ydeevneoptagelse af Microsoft Defender Antivirus scanninger. Disse ydelsesoptagelser indeholder kerneproceshændelser i Microsoft-Antimalware og NT og kan analyseres efter samling ved hjælp af Cmdlet'en [Get-MpPerformanceReport](#get-mpperformancereport) .

Denne `New-MpPerformanceRecording` cmdlet giver indsigt i problematiske filer, der kan medføre en forringelse af ydeevnen af Microsoft Defender Antivirus. Dette værktøj leveres "SOM ER OG FOREFINDES" og er ikke beregnet til at komme med forslag til undtagelser. Udeladelser kan reducere beskyttelsesniveauet på dine slutpunkter. Eventuelle udeladelser skal defineres med forsigtighed.

Du kan få flere oplysninger om effektivitetsanalysen [i dokumenter om Effektivitetsanalyse](/windows-hardware/test/wpt/windows-performance-analyzer).

> [!IMPORTANT]
> Denne cmdlet kræver administratorrettigheder med administratorrettigheder.

**Understøttede operativsystemversioner**:

Windows version 10 og nyere.

> [!NOTE]
> Denne funktion er tilgængelig fra og med platformversion 4.18.2108.X og nyere.

#### <a name="examples-new-mpperformancerecording"></a>Eksempler: New-MpPerformanceRecording

##### <a name="example-1-collect-a-performance-recording-and-save-it"></a>Eksempel 1: Indsaml en optagelse af ydeevnen, og gem den

```powershell
New-MpPerformanceRecording -RecordTo:.\Defender-scans.etl
```

Ovenstående kommando indsamler en optagelse af ydeevnen og gemmer den på den angivne sti: **.\Defender-scans.etl**.

##### <a name="example-2-collect-a-performance-recording-for-remote-powershell-session"></a>Eksempel 2: Indsaml en ydelsesoptagelse for en ekstern PowerShell-session

```powershell
$s = New-PSSession -ComputerName Server02 -Credential Domain01\User01
New-MpPerformanceRecording -RecordTo C:\LocalPathOnServer02\trace.etl -Session $s
```

Ovenstående kommando indsamler en optagelse af ydeevnen på Server02 (som angivet af argument $s af parametersessionen) og gemmer den i den angivne sti: **C:\LocalPathOnServer02\trace.etl** på Server02.

##### <a name="example-3-collect-a-performance-recording-in-non-interactive-mode"></a>Eksempel 3: Indsaml en optagelse af ydeevnen i ikke-interaktiv tilstand

```powershell
New-MpPerformanceRecording -RecordTo:.\Defender-scans.etl -Seconds 60
```

Ovenstående kommando indsamler en optagelse af ydeevnen i den varighed i sekunder, der er angivet af parameteren -Seconds. Dette anbefales til brugere, der udfører batchsamlinger, som ikke kræver nogen interaktion eller prompt.

#### <a name="parameters-new-mpperformancerecording"></a>Parametre: New-MpPerformanceRecording

##### <a name="-recordto"></a>-Optag til

Angiver den placering, hvor ydeevnen for Microsoft Defender Antimalware skal gemmes.

```yaml
Type: String
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-session"></a>-Session

Angiver det PSSession-objekt, hvor den Microsoft Defender Antivirus ydelsesoptagelse skal oprettes og gemmes. Når du bruger denne parameter, henviser parameteren RecordTo til den lokale sti på fjerncomputeren. Tilgængelig med Defender platform version 4.18.2201.10.

```yaml
Type: PSSession[]
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-seconds"></a>-Sekunder

Angiver varigheden af ydelsesoptagelsen i sekunder. Dette anbefales til brugere, der udfører batchsamlinger, som ikke kræver nogen interaktion eller prompt.

```yaml
Type: Int32
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### <a name="get-mpperformancereport"></a>Get-MpPerformanceReport

I følgende afsnit beskrives Get-MpPerformanceReport PowerShell-cmdlet'en. Analyserer og rapporterer om Microsoft Defender Antivirus (MDAV)-ydelsesoptagelse.

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
[-Raw]
```

#### <a name="description-get-mpperformancereport"></a>Beskrivelse: Get-MpPerformanceReport

Cmdlet'en `Get-MpPerformanceReport` analyserer en tidligere indsamlet Microsoft Defender Antivirus ydelsesoptagelse ([New-MpPerformanceRecording](#new-mpperformancerecording)) og rapporterer de filstier, filtypenavne og processer, der forårsager den største indvirkning på Microsoft Defender Antivirus scanninger.

Effektivitetsanalyse giver indsigt i problematiske filer, der kan medføre en forringelse af ydeevnen for Microsoft Defender Antivirus. Dette værktøj leveres som "AS IS" og er ikke beregnet til at komme med forslag til undtagelser. Udeladelser kan reducere beskyttelsesniveauet på dine slutpunkter. Eventuelle udeladelser skal defineres med forsigtighed.

Du kan få flere oplysninger om effektivitetsanalysen [i dokumenter om Effektivitetsanalyse](/windows-hardware/test/wpt/windows-performance-analyzer).

**Understøttede operativsystemversioner**:

Windows version 10 og nyere.

> [!NOTE]
> Denne funktion er tilgængelig fra og med platformversion 4.18.2108.X og nyere.

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

##### <a name="example-5-using--raw-parameter"></a>Eksempel 5: Brug af parameteren -Raw

```powershell
Get-MpPerformanceReport -Path:.\Defender-scans.etl -TopFiles:10 -TopExtensions:10 -TopProcesses:10 -TopScans:10 -Raw | ConvertTo-Json
```

Brug af -Raw i ovenstående kommando angiver, at outputtet skal være maskinlæsbart og let kan konverteres til serialiseringsformater, f.eks. JSON

#### <a name="parameters-get-mpperformancereport"></a>Parametre: Get-MpPerformanceReport

##### <a name="-minduration"></a>-MinDuration

Angiver minimumvarigheden af eventuelle scannings- eller samlede scanningsvarigheder for filer, udvidelser og processer, der er inkluderet i rapporten. accepterer værdier som  **f.eks. 0.1234567sec**, **0.1234 ms**, **0.1us** eller en gyldig TimeSpan.

```yaml
Type: String
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-path"></a>-Sti

Angiver stien eller stierne til en eller flere placeringer.

```yaml
Type: String
Position: 0
Default value: None
Accept pipeline input: True
Accept wildcard characters: False
```

##### <a name="-raw"></a>-Rå

Angiver, at outputtet af ydelsesoptagelsen skal være maskinlæsbart og let kan konverteres til serialiseringsformater, f.eks. JSON (f.eks. via kommandoen Konvertér til JSON). Dette anbefales til brugere, der er interesseret i batchbehandling med andre databehandlingssystemer.

```yaml
Type: <SwitchParameter>
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-topextensions"></a>-Topudvidelser

Angiver, hvor mange topudvidelser der skal udskrives, sorteret efter "Varighed".

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-topextensionsperprocess"></a>-TopExtensionsPerProcess

Angiver, hvor mange topudvidelser der skal udskrives for hver topproces sorteret efter "Varighed".

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-topfiles"></a>-TopFiler

Anmoder om en rapport med topfiler og angiver, hvor mange topfiler der skal udskrives, sorteret efter "Varighed".

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-topfilesperextension"></a>-TopFilesPerExtension

Angiver, hvor mange topfiler der skal udskrives for hver topudvidelse sorteret efter "Varighed".

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-topfilesperprocess"></a>-TopFilesPerProcess

Angiver, hvor mange topfiler der skal udskrives for hver topproces sorteret efter "Varighed".

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-topprocesses"></a>-Topprocesser

Anmoder om en rapport med topprocesser og angiver, hvor mange af de øverste processer der skal udskrives, sorteret efter "Varighed".

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-topprocessesperextension"></a>-TopProcessesPerExtension

Angiver, hvor mange topprocesser der skal udskrives for hver topudvidelse sorteret efter "Varighed".

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-topprocessesperfile"></a>-TopProcessesPerFile

Angiver, hvor mange topprocesser der skal udskrives for hver topfil sorteret efter "Varighed".

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-topscans"></a>-TopScans

Anmoder om en rapport med en topscanning og angiver, hvor mange topscanninger der skal udskrives, sorteret efter "Varighed".

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-topscansperextension"></a>-TopScansPerExtension

Angiver, hvor mange topscanninger der skal udskrives for hver topudvidelse sorteret efter "Varighed".

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-topscansperextensionperprocess"></a>-TopScansPerExtensionPerProcess

Angiver, hvor mange topscanninger der skal udskrives for hver topudvidelse for hver topproces sorteret efter "Varighed".

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-topscansperfile"></a>-TopScansPerFile

Angiver, hvor mange topscanninger der skal udskrives for hver topfil sorteret efter "Varighed".

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-topscansperfileperextension"></a>-TopScansPerFilePerExtension

Angiver, hvor mange topscanninger der skal udskrives for hver topfil for hvert øverste filtypenavn sorteret efter "Varighed".

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-topscansperfileperprocess"></a>-TopScansPerFilePerProcess

Angiver, hvor mange topscanninger der søges efter output for hver topfil for hver topproces sorteret efter "Varighed".

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-topscansperprocess"></a>-TopScansPerProcess

Angiver, hvor mange topscanninger der skal udskrives for hver topproces i rapporten Topprocesser sorteret efter "Varighed".

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-topscansperprocessperextension"></a>-TopScansPerProcessPerExtension

Angiver, hvor mange topscanninger der søges efter output for hver topproces for hver topudvidelse sorteret efter "Varighed".

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-topscansperprocessperfile"></a>-TopScansPerProcessPerFile

Angiver, hvor mange topscanninger der søges efter output for hver topproces for hver topfil sorteret efter "Varighed".

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

## <a name="additional-resources"></a>Yderligere ressourcer

Hvis du leder efter Antivirus-relaterede oplysninger til andre platforme, kan du se:

- [Angiv indstillinger for Microsoft Defender for Endpoint på macOS-](mac-preferences.md)
- [Microsoft Defender for Endpoint på Mac](microsoft-defender-endpoint-mac.md)
- [Politikindstillinger for macOS Antivirus for Microsoft Defender Antivirus for Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
- [Angiv indstillinger for Microsoft Defender for Endpoint på Linux](linux-preferences.md)
- [Microsoft Defender for Endpoint på Linux](microsoft-defender-endpoint-linux.md)
- [Konfigurer Defender for Endpoint på Android-funktioner](android-configure.md)-  [Konfigurer Microsoft Defender for Endpoint på iOS-funktioner](ios-configure-features.md)
