---
title: Kontekstafhængige fil- og mappeudeladelser
description: Beskriver funktionen kontekstafhængige fil- og mappeudeladelser for Windows Defender Antivirus. Denne funktion giver dig mulighed for at være mere specifik, når du definerer, i hvilken kontekst Windows Defender Antivirus ikke skal scanne en fil eller mappe, ved at anvende begrænsninger
keywords: Microsoft Defender Antivirus, proces, udeladelse, filer, scanninger
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: jweston-1
ms.author: v-jweston
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: a2dfcd6372398f92ba401a109302ef541de88565
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/29/2022
ms.locfileid: "66493964"
---
# <a name="contextual-file-and-folder-exclusions"></a>Kontekstafhængige fil- og mappeudeladelser

I denne artikel/sektion beskrives funktionen kontekstafhængige fil- og mappeudeladelser for Windows Defender Antivirus. Denne funktion giver dig mulighed for at være mere specifik, når du definerer, i hvilken kontekst Windows Defender Antivirus ikke skal scanne en fil eller mappe, ved at anvende begrænsninger.

## <a name="overview"></a>Oversigt

Udeladelser er primært beregnet til at afhjælpe indvirkninger på ydeevnen. De kommer med en bøde på reduceret beskyttelsesværdi. Disse begrænsninger giver dig mulighed for at begrænse denne reduktion af beskyttelse ved at angive omstændigheder, som udelukkelsen skal gælde under. Kontekstafhængige udeladelser er ikke egnede til at håndtere falske positiver på en pålidelig måde. Hvis du støder på en falsk positiv værdi, kan du indsende filer til analyse via [Microsoft 365 Defender-portalen](https://security.microsoft.com/) (påkrævet abonnement) eller via [Microsoft Sikkerhedsviden](https://www.microsoft.com/wdsi/filesubmission) websted. I forbindelse med en midlertidig undertrykkelsesmetode kan du overveje at oprette en brugerdefineret _tilladelsesindikator_ .

Der er fire begrænsninger, du kan anvende for at begrænse anvendelsen af en udelukkelse:

- **Begrænsning af fil-/mappestitype**. Du kan begrænse udeladelser til kun at gælde, hvis målet er en fil eller en mappe, ved at gøre hensigten specifik. Hvis destinationen er en fil, men udeladelse er angivet til at være en mappe, anvendes den ikke. Omvendt gælder udeladelse, hvis destinationen er en mappe, men udeladelse er angivet til at være en fil.
- **Begrænsning af scanningstype**. Giver dig mulighed for at definere den påkrævede scanningstype for at anvende en udeladelse. Du vil f.eks. kun udelukke en bestemt mappe fra Komplette scanninger, men ikke fra en "ressource"-scanning (målrettet scanning).
- **Begrænsning af scanningsudløsertype**. Du kan bruge denne begrænsning til at angive, at udeladelse kun skal gælde, når scanningen blev startet af en bestemt hændelse:
  - efter behov
  - ved adgang
  - eller stammer fra adfærdsovervågning
- **Procesbegrænsning**. Giver dig mulighed for at definere, at en udeladelse kun skal gælde, når en fil eller mappe tilgås af en bestemt proces.

## <a name="configuring-restrictions"></a>Konfiguration af begrænsninger

Begrænsninger anvendes typisk ved at føje begrænsningstypen til fil- eller mappeudeladelsesstien.  

| Begrænsning | Typename | Værdi |
|:---|:---|:---|
| Fil/mappe  | PathType  | Fil <br> Mappe |
| Scanningstype | ScanType | Hurtig <br> Fuld |
| Scanningsudløser | ScanTrigger | Ondemand <br> OnAccess <br> BM |
| Proces | Proces | "<image_path>" |

### <a name="requirements"></a>Krav

Denne funktion kræver Windows Defender Antivirus:

- Platform: **4.18.2205.7** eller nyere
- Motor: **1.1.19300.2** eller nyere

### <a name="syntax"></a>Syntaks

Som udgangspunkt kan du allerede have undtagelser på plads, som du ønsker at gøre mere specifik. Hvis du vil oprette udeladelsesstrengen, skal du først definere stien til den fil eller mappe, der skal udelades, og derefter tilføje typenavnet og den tilknyttede værdi, som vist i følgende eksempel.

`<PATH>\:{TypeName:value,TypeName:value}`

Vær opmærksom på, at der _skelnes_ mellem store og små bogstaver i alle **typer** og **værdier** .

### <a name="examples"></a>Eksempler

Følgende streng udelukker kun "c:\documents\design.doc", hvis det er en fil og kun i scanninger efter adgang:

`c:\documents\design.doc\:{PathType:file,ScanTrigger:OnAccess}`

Følgende streng udelukker kun "c:\documents\design.doc", hvis den er scannet (ved adgang), fordi en proces har fået adgang til den med billednavnet "winword.exe":

`c:\documents\design.doc\:{Process:”winword.exe”}`

Stien til procesbilledet kan indeholde jokertegn som i følgende eksempel:

`c:\documents\design.doc\:{Process:”C:\Program Files*\Microsoft Office\root\Office??\winword.exe”}`

### <a name="filefolder-restriction"></a>Fil-/mappebegrænsning

Du kan begrænse udeladelser til kun at gælde, hvis målet er en fil eller en mappe ved at gøre hensigten specifik. Hvis destinationen er en fil, men udeladelse er angivet som en mappe, gælder udeladelse ikke. Omvendt gælder udeladelse, hvis destinationen er en mappe, men udeladelse er angivet til at være en fil.

#### <a name="filefolder-exclusions-default-behavior"></a>Standardfunktionsmåde for udeladelser i filer/mapper

Hvis du ikke angiver andre indstillinger, udelades filen/mappen fra alle typer scanninger, _og_ udeladelsen gælder, uanset om destinationen er en fil eller en mappe. Du kan finde flere oplysninger om tilpasning af undtagelser, så de kun gælder for en bestemt scanningstype, under [Begrænsning af scanningstype](#scan-type-restriction).

#### <a name="folders"></a>Mapper

Hvis du vil sikre, at en udeladelse kun gælder, hvis destinationen er en mappe, kan du ikke bruge begrænsningen **PathType:folder** . Eksempel:

`C:\documents\:{PathType:folder}`

#### <a name="files"></a>Filer

Hvis du vil sikre dig, at en udeladelse kun gælder, hvis destinationen er en fil, ikke en mappe, kan du bruge begrænsningen PathType: file.

Eksempel:

`C:\documents\database.mdb\:{PathType:file}`

### <a name="scan-type-restriction"></a>Begrænsning af scanningstype

Udeladelser gælder som standard for alle scanningstyper:  

- **ressource**: en enkelt fil eller mappe scannes på en målrettet måde (f.eks. højreklik, Scan)
- **hurtig**: almindelige startplaceringer, der anvendes af malware, hukommelse og visse registreringsdatabasenøgler
- **full**: indeholder placeringer til hurtig scanning og komplet filsystem (alle filer og mapper)

For at afhjælpe problemer med ydeevnen kan du udelade en mappe eller et sæt filer fra at blive scannet af en bestemt scanningstype. Du kan også definere den påkrævede scanningstype for at anvende en udeladelse.  

Hvis du kun vil udelukke en mappe fra at blive scannet under en fuld scanning, skal du angive en begrænsningstype sammen med udeladelse af filer eller mapper som i følgende eksempel:

`C:\documents\:{ScanType:full}`

Hvis du kun vil udelukke en mappe fra at blive scannet under en hurtig scanning, skal du angive en begrænsningstype sammen med udeladelse af filen eller mappen:

`C:\program.exe\:{ScanType:quick}`

Hvis du vil sikre dig, at denne udeladelse kun gælder for en bestemt fil og ikke en mappe (c:\foo.exe kan være en mappe), skal du også anvende PathType-begrænsningen:

`C:\program.exe\:{ScanType:quick,PathType:file}`

### <a name="scan-trigger-restriction"></a>Begrænsning af scanningsudløser

Som standard gælder grundlæggende undtagelser for alle scanningsudløsere. ScanTrigger-begrænsning giver dig mulighed for at angive, at udeladelse kun skal gælde, når scanningen blev startet af en bestemt hændelse. efter behov (herunder hurtig, fuld og målrettet scanning), om adgang eller stammer fra adfærdsovervågning (herunder hukommelsesscanninger).

- **OnDemand**: En scanning blev udløst af en kommando- eller administratorhandling. Husk, at planlagte hurtig- og fuldscanninger også falder ind under denne kategori.
- **OnAccess**: En fil eller mappe åbnes/skrives/læses/ændres (typisk som beskyttelse i realtid)
- **BM**: En funktionsudløser medfører, at den adfærdsmæssige overvågning scanner en bestemt fil

Hvis du kun vil udelukke en fil eller mappe og dens indhold fra at blive scannet, når filen scannes, når der er adgang til den, skal du definere en begrænsning for scanningsudløseren, f.eks. følgende eksempel:

`c:\documents\:{ScanTrigger:OnAccess}`

### <a name="process-restriction"></a>Procesbegrænsning

Denne begrænsning giver dig mulighed for at definere, at en udeladelse kun skal gælde, når en fil eller mappe tilgås af en bestemt proces. Et almindeligt scenarie er, når du vil undgå at udelade processen, da undgåelse ville medføre, at Defender Antivirus ignorerer andre handlinger fra den pågældende proces.

> [!NOTE]  
>
> Hvis du bruger en stor mængde begrænsninger for procesudeladelse på en maskine, kan det påvirke ydeevnen negativt.  
> Da du har begrænset udeladelse til en eller flere processer, kan andre aktive processer (f.eks. indeksering, sikkerhedskopiering og opdateringer) desuden stadig udløse filscanninger.

Hvis du kun vil udelade en fil eller mappe, når en bestemt proces tilgås, skal du oprette en normal udeladelse af filer eller mapper og tilføje processen for at begrænse udeladelse til:  

`c:\documents\design.doc\:{Process:”winword.exe”, Process:”msaccess.exe”}`

### <a name="how-to-configure"></a>Sådan konfigurerer du

Når du har konstrueret de ønskede kontekstafhængige udeladelser, kan du bruge dit eksisterende administrationsværktøj til at konfigurere fil- og mappeudeladelser ved hjælp af den streng, du har oprettet.

Se: [Konfigurer og valider udeladelser for Microsoft Defender Antivirus-scanninger](configure-exclusions-microsoft-defender-antivirus.md)
