---
title: Retningslinjer for testpakke
description: Gennemse retningslinjerne for testpakken
search.appverid: MET150
author: mansipatel-usl
ms.author: mapatel
manager: rshastri
audience: Software-Vendor
ms.topic: how-to
ms.date: 02/04/2022
ms.service: virtual-desktop
ms.localizationpriority: medium
ms.collection: TestBase-M365
ms.custom: ''
ms.reviewer: mapatel
f1.keywords: NOCSH
ms.openlocfilehash: 0b5e69a245b21f4f6985eb54ca865b602059cba8
ms.sourcegitcommit: 954c8af658adb270fe843991e048c6a30e86e77c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/06/2022
ms.locfileid: "63606613"
---
# <a name="test-package-guidelines"></a>Retningslinjer for testpakke

## <a name="1-script-referencing"></a>1. Reference til script

Når du uploader .zip fil til portalen, udpakker vi alt indholdet af den pågældende fil i en rodmappe. Du behøver ikke at skrive nogen kode for at udføre denne indledende udpakkede handling. Du kan også referere til enhver fil på .zip ved hjælp af stien i forhold til den uploadede zip-fil.

I eksemplet nedenfor viser vi, hvordan du kan referere til dine binære/scripts fra inputfeltet på fanen Opgaver. Teksten med blå skal indtastes i feltet **Scriptsti uden** **anførselstegnene.**

Det er vigtigt, at du er opmærksom på indholdet i din zip-fil, før du uploader den. Når du komprimerer en mappe, opretter din lokale computer ofte en hovedmappe under zip-filen. I dette tilfælde vises referencen med **fed skrift nedenfor** :

**Contoso_App_Folder.zip**:

```console
├── Contoso_App_Folder

│   ├── file1.exe

│   ├── ScriptX.ps1

│   ├── folder1

│      ├── file3.exe

│      ├── script.ps1
```

- ScriptX.ps1 - **"Contoso_App_Folder/ScriptX.ps1"**
- Script.ps1 - **"Contoso_App_Folder/folder1/script.ps1"**

Andre gange kan din zip-fil have dine filer eller indhold nedenunder (f.eks. ingen mappe på andet niveau):

**Zip_file_uploaded.zip**:

```console
├── file1.exe

├── ScriptX.ps1

├── folder1

│   ├── file3.exe

│   ├── script.ps1
```

- ScriptX.ps1 - **"ScriptX.ps1"**
- Script.ps1 - **"folder1/script.ps1"**

## <a name="2-script-execution"></a>2. Script-udførelse

**Out of Box-test:** Programpakken skal indeholde mindst tre PowerShell-scripts. Disse scripts udføres uden opsyn ved installation, start og lukning af programmet og dets afhængigheder. Hvert script skal håndtere kontrol af sine egne forudsætninger, validere dets egen succes og rydde op efter sig selv (hvis det er nødvendigt).

**Funktionstest:** Programpakken skal indeholde mindst ét PowerShell-script. Hvis der leveres mere end ét script, køres scripts i overførselssekvens, og en fejl i et bestemt script stopper efterfølgende scripts i at blive udført.

### <a name="script-requirements"></a>Scriptkrav

- PowerShell Version 5.1+
- Uovervåget udførelse
- Fejlreturkode
- Valider succes
- Logføring til scriptspecifik logmappe

Hvert script skal køre uden opsyn (ingen brugerprompter) for at kunne køre i testpipelinen.

> [!NOTE]
> Scripts bør returnere "0" ved vellykket fuldførelse og en fejlkode, der ikke er nul, hvis der opstår en fejl under udførelse.

Hvert script skal validere, om det kørte korrekt. Eksempelvis skal installationsscriptet kontrollere, om der findes bestemte binære og/eller registreringsdatabasenøgler på systemet, når den binære installationsprogram er færdig med at udføre. Denne kontrol hjælper med at sikre en rimelig grad af tillid til, at installationen blev gennemført.

Validering er nødvendig for at kunne diagnosticere, hvor der opstår fejl under en testkørsel. Hvis scriptet f.eks. ikke kan installere programmet uden at kunne starte det.

> [!IMPORTANT]
> **Undgå følgende:** Scripts bør ikke genstarte computeren, hvis det er nødvendigt at genstarte. Angiv dette under overførslen af dine scripts.

## <a name="3-log-collection"></a>3. Logsamling

Hvert script bør få tilgivet alle logfiler, det genererer, i en mappe med navnet `logs`. Alle mapper i den mappe, der `logs` er navngivet, kopieres og præsenteres til download på `Test Results` siden.

Installationsscriptet (som kan være placeret i mappen **App/scripts/Install** ) kan f.eks. skrive sine logfiler til: **logs/install.log**, så den endelige logfil er på: **Apps/scripts/install/logs/install.log**

Systemet vil hente filen sammen `install.log` med andre filer i andre `logs` mapper og samle den til download.

## <a name="4-application-binaries"></a>4. Program binære

Alle binære og afhængigheder skal medtages i den enkelte zip-fil.

Disse binære bør omfatte alt, hvad der er nødvendigt for installation af programmet (f.eks. programinstallationsprogrammet). Hvis programmet er afhængig af nogen frameworks, f.eks. .NET Core/Standard eller .NET Framework, skal disse frameworks medtages i filen og refereres korrekt til de angivne scripts.

> [!NOTE]
> Den uploadede zip-fil må ikke have nogen mellemrum eller specialtegn i navnet

## <a name="5-applicationtest-rules"></a>5. Program-/testregler

For at dine programmer/tests kan køre korrekt under Test Base-infrastrukturen, skal de overholde de regler, der er beskrevet i [Program/Test-regler ](rules.md). 

## <a name="next-steps"></a>Næste trin

Gå videre til den næste artikel for at få vist **nogle ofte stillede spørgsmål**
> [!div class="nextstepaction"]
> [Næste trin](faq.md)
