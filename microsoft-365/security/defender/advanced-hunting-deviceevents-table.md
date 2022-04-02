---
title: DeviceEvents-tabel i det avancerede jagtskema
description: Få mere at vide om antivirus, firewall og andre begivenhedstyper i tabellen diverse enhedsbegivenheder (DeviceEvents) i det avancerede jagtskema
keywords: avanceret jagt, trusselssøgning, cybertrusler på jagt, Microsoft 365 Defender, microsoft 365, m365, søg, forespørgsel, telemetri, skemareference, kusto, tabel, kolonne, datatype, sikkerhedshændelser, antivirus, firewall, exploit guard, DeviceEvents
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
ms.openlocfilehash: 54eef2d828f9a236ae457769c8c4ff9ba429dac9
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/15/2021
ms.locfileid: "63603071"
---
# <a name="deviceevents"></a>DeviceEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**
- Microsoft 365 Defender
- Microsoft Defender til Slutpunkt

De diverse enhedsbegivenheder `DeviceEvents` eller tabellen i det avancerede [](advanced-hunting-overview.md) jagtskema indeholder oplysninger om forskellige hændelsestyper, herunder hændelser, der udløses af sikkerhedskontrolelementer, f.eks. Windows Defender Antivirus og udnyttelse af beskyttelse. Brug denne reference til at oprette forespørgsler, der returnerer oplysninger fra denne tabel.

>[!TIP]
> Du kan finde detaljerede oplysninger om de hændelsestyper (`ActionType` værdier), der understøttes af en tabel, ved at bruge den indbyggede skemareference, der er tilgængelig i Defender for Cloud.

Du kan finde oplysninger om andre tabeller i det avancerede jagtskema i [den avancerede jagtreference](advanced-hunting-schema-tables.md).


| Kolonnenavn | Datatype | Beskrivelse |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Dato og klokkeslæt for, hvornår begivenheden blev optaget |
| `DeviceId` | `string` | Entydigt id for computeren i tjenesten |
| `DeviceName` | `string` | Fuldt kvalificeret domænenavn på computeren |
| `ActionType` | `string` | Aktivitetstype, der udløste hændelsen. Se [skemareferencen i portalen for at](advanced-hunting-schema-tables.md?#get-schema-information-in-the-security-center) få mere at vide |
| `FileName` | `string` | Navnet på den fil, som den optagede handling blev anvendt på |
| `FolderPath` | `string` | Mappe, der indeholder den fil, som den optagede handling blev anvendt på |
| `SHA1` | `string` | SHA-1 i den fil, som den optagede handling blev anvendt på |
| `SHA256` | `string` | SHA-256 af den fil, som den optagede handling blev anvendt på. Dette felt udfyldes normalt ikke – brug kolonnen SHA1, når den er tilgængelig. |
| `MD5` | `string` | MD5-hash for den fil, som den optagede handling blev anvendt på |
| `FileSize` | `long` | Filens størrelse i byte |
| `AccountDomain` | `string` | Kontoens domæne |
| `AccountName` | `string` | Brugernavn på kontoen |
| `AccountSid` | `string` | Kontoens sikkerheds-id (SID) |
| `RemoteUrl` | `string` | URL-adressen eller det fulde domænenavn, der blev knyttet til |
| `RemoteDeviceName` | `string` | Navnet på den computer, der udførte en fjernhandling på den pågældende computer. Afhængigt af den hændelse, der rapporteres, kan dette navn være et fuldt kvalificeret domænenavn, et NetABAS-navn eller et værtsnavn uden domæneoplysninger |
| `ProcessId` | `int` | Proces-id (PID) for den netop oprettede proces |
| `ProcessCommandLine` | `string` | Kommandolinje, der bruges til at oprette den nye proces |
| `ProcessCreationTime` | `datetime` | Dato og klokkeslæt for oprettelse af processen |
| `ProcessTokenElevation` | `string` | Tokentype, der angiver tilstedeværelse eller fravær af brugeradgangskontrol (UAC)-rettighedsover udvidelse anvendt på den nyoprettede proces |
| `LogonId` | `string` | Id for en logonsession. Dette id er entydigt på den samme maskine, kun mellem genstart |
| `RegistryKey` | `string` | Registreringsdatabasenøgle, som den optagede handling blev anvendt på |
| `RegistryValueName` | `string` | Navnet på den registreringsdatabaseværdi, som den registrerede handling blev anvendt på |
| `RegistryValueData` | `string` | Data for den registreringsdatabaseværdi, som den registrerede handling blev anvendt på |
| `RemoteIP` | `string` | IP-adresse, der blev knyttet til |
| `RemotePort` | `int` | TCP-port på den eksterne enhed, der blev forbundet til |
| `LocalIP` | `string` | IP-adresse tildelt den lokale computer, der bruges under kommunikation |
| `LocalPort` | `int` | TCP-port på den lokale computer, der bruges under kommunikation |
| `FileOriginUrl` | `string` | URL-adressen, hvor filen blev downloadet fra |
| `FileOriginIP` | `string` | IP-adresse, hvor filen blev downloadet fra |
| `InitiatingProcessSHA1` | `string` | SHA-1 af den proces (billedfil), der startede hændelsen |
| `InitiatingProcessSHA256` | `string` | SHA-256 af den proces (billedfil), der startede hændelsen. Dette felt udfyldes normalt ikke – brug kolonnen SHA1, når den er tilgængelig. |
| `InitiatingProcessMD5` | `string` | MD5-hash for den proces (billedfil), der startede hændelsen |
| `InitiatingProcessFileName` | `string` | Navnet på den proces, der startede hændelsen |
| `InitiatingProcessFileSize` | `long` | Størrelsen på den fil, der kørte den proces, der er ansvarlig for begivenheden |
| `InitiatingProcessFolderPath` | `string` | Mappe, der indeholder den proces (billedfil), som startede hændelsen |
| `InitiatingProcessId` | `int` | Proces-id (PID) for den proces, der startede hændelsen |
| `InitiatingProcessCommandLine` | `string` | Kommandolinje, der bruges til at køre den proces, der startede hændelsen |
| `InitiatingProcessCreationTime` | `datetime` | Dato og klokkeslæt for den proces, der startede hændelsen blev startet |
| `InitiatingProcessAccountDomain` | `string` | Domæne for den konto, der kørte processen, der er ansvarlig for begivenheden |
| `InitiatingProcessAccountName` | `string` | Brugernavnet på den konto, der kørte den proces, der er ansvarlig for begivenheden |
| `InitiatingProcessAccountSid` | `string` | Security Identifier (SID) for den konto, der kørte den proces, der er ansvarlig for hændelsen |
| `InitiatingProcessAccountUpn` | `string` | Brugerens hovednavn (UPN) for den konto, der kørte processen med ansvar for begivenheden |
| `InitiatingProcessAccountObjectId` | `string` | Azure AD-objekt-id'et for den brugerkonto, der kørte den proces, der er ansvarlig for begivenheden |
| `InitiatingProcessVersionInfoCompanyName` | `string` | Firmanavn fra versionsoplysningerne for den proces (billedfil), der er ansvarlig for begivenheden |
| `InitiatingProcessVersionInfoProductName` | `string` | Produktnavn fra versionsoplysningerne for den proces (billedfil), der er ansvarlig for begivenheden |
| `InitiatingProcessVersionInfoProductVersion` | `string` | Produktversion fra versionsoplysningerne for den proces (billedfil), der er ansvarlig for begivenheden |
|` InitiatingProcessVersionInfoInternalFileName` | `string` | Internt filnavn fra versionsoplysningerne for den proces (billedfil), der er ansvarlig for begivenheden |
| `InitiatingProcessVersionInfoOriginalFileName` | `string` | Oprindeligt filnavn fra versionsoplysningerne for den proces (billedfil), der er ansvarlig for begivenheden |
| `InitiatingProcessVersionInfoFileDescription` | `string` | Beskrivelse fra versionsoplysningerne for den proces (billedfil), der er ansvarlig for begivenheden |
| `InitiatingProcessParentId` | `int` | Proces-id (PID) for den overordnede proces, der identificerede den proces, der er ansvarlig for begivenheden |
| `InitiatingProcessParentFileName` | `string` | Navnet på den overordnede proces, hvor den proces, der er ansvarlig for begivenheden, blev vist |
| `InitiatingProcessParentCreationTime` | `datetime` | Dato og klokkeslæt, hvor den overordnede for den proces, der er ansvarlig for begivenheden, blev startet |
| `InitiatingProcessLogonId` | `string` | Id for en logonsession for den proces, der startede hændelsen. Dette id er entydigt på den samme maskine, kun mellem genstart |
| `ReportId` | `long` | Hændelses-id baseret på en gentagende tæller. For at identificere entydige hændelser skal denne kolonne bruges sammen med kolonnerne DeviceName og Timestamp |
| `AppGuardContainerId` | `string` | Id for den virtualiserede beholder, der bruges af Application Guard til at isolere browseraktivitet |
| `AdditionalFields` | `string` | Yderligere oplysninger om hændelsen i JSON-matrixformat |

## <a name="related-topics"></a>Relaterede emner
- [Avanceret jagtoversigt](advanced-hunting-overview.md)
- [Lær forespørgselssproget](advanced-hunting-query-language.md)
- [Brug delte forespørgsler](advanced-hunting-shared-queries.md)
- [Lede på tværs af enheder, mails, apps og identiteter](advanced-hunting-query-emails-devices.md)
- [Forstå skemaet](advanced-hunting-schema-tables.md)
- [Anvend bedste fremgangsmåder for forespørgsler](advanced-hunting-best-practices.md)
