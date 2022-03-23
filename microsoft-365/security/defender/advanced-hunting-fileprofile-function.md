---
title: Funktionen FileProfile() i avanceret jagt på Microsoft 365 Defender
description: Få mere at vide om, hvordan du bruger FileProfile() til at berige oplysninger om filer i dine avancerede resultater af en forespørgsel
keywords: avanceret jagt, trusselssøgning, cybertrusler på jagt, Microsoft 365 Defender, microsoft 365, m365, søgning, forespørgsel, telemetri, skemareference, kusto, FileProfile, filprofil, funktion, berigende
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
ms.openlocfilehash: 2cd8c91717af8390160bf45a625ae3a3044ee387
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/15/2021
ms.locfileid: "63591157"
---
# <a name="fileprofile"></a>FileProfile()

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender

Funktionen `FileProfile()` er en berigende funktion i [avanceret jagt,](advanced-hunting-overview.md) der føjer følgende data til filer, der findes af forespørgslen.

| Kolonne | Datatype | Beskrivelse |
|------------|---------------|-------------|
| `SHA1` | `string` | SHA-1 i den fil, som den optagede handling blev anvendt på |
| `SHA256` | `string` | SHA-256 af den fil, som den optagede handling blev anvendt på |
| `MD5` | `string` | MD5-hash for den fil, som den optagede handling blev anvendt på |
| `FileSize` | `int` | Filens størrelse i byte |
| `GlobalPrevalence` | `int` | Antal forekomster af enheden, der er observeret af Microsoft globalt |
| `GlobalFirstSeen` | `datetime` | Dato og klokkeslæt, hvor enheden første gang observeres af Microsoft globalt |
| `GlobalLastSeen` | `datetime` | Dato og klokkeslæt, hvor enheden sidst blev observeret af Microsoft globalt |
| `Signer` | `string` | Oplysninger om underskriveren af filen |
| `Issuer` | `string` | Oplysninger om det udstedende nøglecenter |
| `SignerHash` | `string` | Entydig hash-værdi, der identificerer underskriveren |
| `IsCertificateValid` | `boolean` | Om det certifikat, der bruges til at signere filen, er gyldigt |
| `IsRootSignerMicrosoft` | `boolean` | Angiver, om underskriveren af rodcertifikatet er Microsoft |
| `SignatureState` | `string` | Tilstanden for filsignaturen: SignedValid – filen er signeret med en gyldig signatur, SignedInvalid – filen er signeret, men certifikatet er ugyldigt, Usigneret – filen er ikke signeret, Ukendt – oplysninger om filen kan ikke hentes
| `IsExecutable` | `boolean` | Om filen er en bærbar eksekverbar fil (PE) |
| `ThreatName` | `string` | Registreringsnavn for malware eller andre trusler, der er fundet |
| `Publisher` | `string` | Navnet på den organisation, der har publiceret filen |
| `SoftwareName` | `string` | Navnet på softwareproduktet |

## <a name="syntax"></a>Syntaks

```kusto
invoke FileProfile(x,y)
```

## <a name="arguments"></a>Argumenter

- **x** – kolonnen fil-id, der skal bruges: `SHA1`, `SHA256`, `InitiatingProcessSHA1`eller `InitiatingProcessSHA256`; funktion bruger, `SHA1` hvis ikke-angivet
- **y** – begræns antallet af poster, der kan beriges, 1-1000; funktion bruger 100, hvis ikke-angivet


>[!TIP]
> Berigende funktioner viser kun supplerende oplysninger, når de er tilgængelige. Tilgængeligheden af oplysninger er varieret og afhænger af en masse faktorer. Sørg for at overveje dette, når du bruger FileProfile() i dine forespørgsler eller til at oprette brugerdefinerede registreringer. For at få de bedste resultater anbefaler vi, at du bruger funktionen FileProfile() med SHA1.

## <a name="examples"></a>Eksempler

### <a name="project-only-the-sha1-column-and-enrich-it"></a>Project kun SHA1-kolonnen og gør den bedre

```kusto
DeviceFileEvents
| where isnotempty(SHA1) and Timestamp > ago(1d)
| take 10
| project SHA1
| invoke FileProfile()
```

### <a name="enrich-the-first-500-records-and-list-low-prevalence-files"></a>Gør de første 500 poster bedre, og opliste svagtseende filer

```kusto
DeviceFileEvents
| where ActionType == "FileCreated" and Timestamp > ago(1d)
| project CreatedOn = Timestamp, FileName, FolderPath, SHA1
| invoke FileProfile("SHA1", 500) 
| where GlobalPrevalence < 15
```

## <a name="related-topics"></a>Relaterede emner
- [Avanceret jagtoversigt](advanced-hunting-overview.md)
- [Lær forespørgselssproget](advanced-hunting-query-language.md)
- [Forstå skemaet](advanced-hunting-schema-tables.md)
- [Få flere forespørgselsekse eksempler](advanced-hunting-shared-queries.md)
