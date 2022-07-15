---
title: Funktionen FileProfile() i avanceret jagt efter Microsoft 365 Defender
description: Få mere at vide om, hvordan du bruger FileProfile() til at forbedre oplysninger om filer i dine avancerede resultater af jagtforespørgslen
keywords: avanceret jagt, trusselsjagt, cybertrusselsjagt, Microsoft 365 Defender, microsoft 365, m365, søgning, forespørgsel, telemetri, skemareference, kusto, FileProfile, filprofil, funktion, berigelse
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 3e530bd9c1e6af58c83a88fc16b5ac4f9aee60e0
ms.sourcegitcommit: a209c9f86a7b4340a426c4cfed2d36a388c71124
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/15/2022
ms.locfileid: "66797923"
---
# <a name="fileprofile"></a>FileProfile()

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender

Funktionen `FileProfile()` er en berigelsesfunktion i [avanceret jagt](advanced-hunting-overview.md) , der føjer følgende data til filer, der blev fundet af forespørgslen.

| Kolonne | Datatype | Beskrivelse |
|------------|---------------|-------------|
| `SHA1` | `string` | SHA-1 for den fil, som den registrerede handling blev anvendt på |
| `SHA256` | `string` | SHA-256 af den fil, som den registrerede handling blev anvendt på |
| `MD5` | `string` | MD5-hash for den fil, som den registrerede handling blev anvendt på |
| `FileSize` | `int` | Filens størrelse i byte |
| `GlobalPrevalence` | `int` | Antal forekomster af enheden, der er observeret af Microsoft globalt |
| `GlobalFirstSeen` | `datetime` | Dato og klokkeslæt for første gang, hvor enheden blev observeret globalt af Microsoft |
| `GlobalLastSeen` | `datetime` | Den dato og det klokkeslæt, hvor enheden sidst blev observeret af Microsoft globalt |
| `Signer` | `string` | Oplysninger om underskriveren af filen |
| `Issuer` | `string` | Oplysninger om det udstedende nøglecenter |
| `SignerHash` | `string` | Entydig hashværdi, der identificerer underskriveren |
| `IsCertificateValid` | `boolean` | Om det certifikat, der blev brugt til at signere filen, er gyldigt |
| `IsRootSignerMicrosoft` | `boolean` | Angiver, om underskriveren af rodcertifikatet er Microsoft, og om filen er indbygget i Windows OS |
| `SignatureState` | `string` | Tilstand for filsignatur: SignedValid – filen er signeret med en gyldig signatur, SignedInvalid - filen er signeret, men certifikatet er ugyldigt, Usigneret - filen er ikke signeret, Ukendt - oplysninger om filen kan ikke hentes
| `IsExecutable` | `boolean` | Om filen er en PE-fil (Portable Executable) |
| `ThreatName` | `string` | Registreringsnavn for malware eller andre trusler, der findes |
| `Publisher` | `string` | Navnet på den organisation, der publicerede filen |
| `SoftwareName` | `string` | Navnet på softwareproduktet |

## <a name="syntax"></a>Syntaks

```kusto
invoke FileProfile(x,y)
```

## <a name="arguments"></a>Argumenter

- **x** – den fil-id-kolonne, der skal bruges: `SHA1`, `SHA256`, `InitiatingProcessSHA1`eller `InitiatingProcessSHA256`; funktionen bruger `SHA1` , hvis den ikke er angivet
- **y** – begrænsning til antallet af poster, der skal beriges, 1-1000; funktionen bruger 100, hvis den ikke er angivet


>[!TIP]
> Berigelsesfunktioner viser kun supplerende oplysninger, når de er tilgængelige. Tilgængeligheden af oplysninger er forskellig og afhænger af mange faktorer. Sørg for at overveje dette, når du bruger FileProfile() i dine forespørgsler eller ved oprettelse af brugerdefinerede registreringer. Vi anbefaler, at du bruger funktionen FileProfile() med SHA1 for at opnå de bedste resultater.

## <a name="examples"></a>Eksempler

### <a name="project-only-the-sha1-column-and-enrich-it"></a>Projektér kun SHA1-kolonnen, og gør den bedre

```kusto
DeviceFileEvents
| where isnotempty(SHA1) and Timestamp > ago(1d)
| take 10
| project SHA1
| invoke FileProfile()
```

### <a name="enrich-the-first-500-records-and-list-low-prevalence-files"></a>Enrich de første 500 poster og liste filer med lav prævalens

```kusto
DeviceFileEvents
| where ActionType == "FileCreated" and Timestamp > ago(1d)
| project CreatedOn = Timestamp, FileName, FolderPath, SHA1
| invoke FileProfile("SHA1", 500) 
| where GlobalPrevalence < 15
```

## <a name="related-topics"></a>Relaterede emner
- [Oversigt over avanceret jagt](advanced-hunting-overview.md)
- [Få mere at vide om forespørgselssproget](advanced-hunting-query-language.md)
- [Forstå skemaet](advanced-hunting-schema-tables.md)
- [Få flere eksempler på forespørgsler](advanced-hunting-shared-queries.md)
