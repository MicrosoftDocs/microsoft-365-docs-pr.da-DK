---
title: DeviceNetworkEvents-tabel i det avancerede jagtskema
description: Få mere at vide om netværksforbindelseshændelser, du kan forespørge på fra DeviceNetworkEvents-tabellen i det avancerede jagtskema
keywords: avanceret jagt, trusselssøgning, cybertrusler på jagt, Microsoft 365 Defender, microsoft 365, m365, søgning, forespørgsel, telemetri, skemareference, kusto, tabel, kolonne, datatype, devicenetworkevents, NetworkCommunicationEvents, netværksforbindelse, ekstern ip, lokal ip
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
ms.openlocfilehash: 6e791efaf418b57716b1f53541292b37805898f4
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/15/2021
ms.locfileid: "63591810"
---
# <a name="devicenetworkevents"></a>DeviceNetworkEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender
- Microsoft Defender til Slutpunkt



Tabellen `DeviceNetworkEvents` i det avancerede [skema indeholder](advanced-hunting-overview.md) oplysninger om netværksforbindelser og relaterede begivenheder. Brug denne reference til at oprette forespørgsler, der returnerer oplysninger fra denne tabel.

>[!TIP]
> Du kan finde detaljerede oplysninger om de hændelsestyper (`ActionType` værdier), der understøttes af en tabel, ved at bruge den indbyggede skemareference, der er tilgængelig i Defender for Cloud.

Du kan finde oplysninger om andre tabeller i det avancerede jagtskema i [den avancerede jagtreference](advanced-hunting-schema-tables.md).

| Kolonnenavn | Datatype | Beskrivelse |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Dato og klokkeslæt for, hvornår begivenheden blev optaget |
| `DeviceId` | `string` | Entydigt id for computeren i tjenesten |
| `DeviceName` | `string` | Fuldt kvalificeret domænenavn på computeren |
| `ActionType` | `string` | Aktivitetstype, der udløste hændelsen. Se [skemareferencen i portalen for at](advanced-hunting-schema-tables.md?#get-schema-information-in-the-security-center) få mere at vide |
| `RemoteIP` | `string` | IP-adresse, der blev knyttet til |
| `RemotePort` | `int` | TCP-port på den eksterne enhed, der blev forbundet til |
| `RemoteUrl` | `string` | URL-adressen eller det fulde domænenavn, der blev knyttet til |
| `LocalIP` | `string` | IP-adresse tildelt den lokale computer, der bruges under kommunikation |
| `LocalPort` | `int` | TCP-port på den lokale computer, der bruges under kommunikation |
| `Protocol` | `string` | Protokol, der bruges under kommunikation |
| `LocalIPType` | `string` | Type af IP-adresse, f.eks. Offentlig, Privat, Reserveret, Loopback, Teredo, FourToSixMapping og Udsendelse |
| `RemoteIPType` | `string` | Type af IP-adresse, f.eks. Offentlig, Privat, Reserveret, Loopback, Teredo, FourToSixMapping og Udsendelse |
| `InitiatingProcessSHA1` | `string` | SHA-1 af den proces (billedfil), der startede hændelsen |
| `InitiatingProcessSHA256` | `string` | SHA-256 af den proces (billedfil), der startede hændelsen. Dette felt udfyldes normalt ikke – brug kolonnen SHA1, når den er tilgængelig. |
| `InitiatingProcessMD5` | `string` | MD5-hash for den proces (billedfil), der startede hændelsen |
| `InitiatingProcessFileName` | `string` | Navnet på den proces, der startede hændelsen |
| `InitiatingProcessFileSize` | `long` | Størrelsen på den fil, der kørte den proces, der er ansvarlig for begivenheden |
| `InitiatingProcessVersionInfoCompanyName` | `string` | Firmanavn fra versionsoplysningerne for den proces (billedfil), der er ansvarlig for begivenheden |
| `InitiatingProcessVersionInfoProductName` | `string` | Produktnavn fra versionsoplysningerne for den proces (billedfil), der er ansvarlig for begivenheden |
| `InitiatingProcessVersionInfoProductVersion` | `string` | Produktversion fra versionsoplysningerne for den proces (billedfil), der er ansvarlig for begivenheden |
| `InitiatingProcessVersionInfoInternalFileName` | `string` | Internt filnavn fra versionsoplysningerne for den proces (billedfil), der er ansvarlig for begivenheden |
| `InitiatingProcessVersionInfoOriginalFileName` | `string` | Oprindeligt filnavn fra versionsoplysningerne for den proces (billedfil), der er ansvarlig for begivenheden |
| `InitiatingProcessVersionInfoFileDescription` | `string` | Beskrivelse fra versionsoplysningerne for den proces (billedfil), der er ansvarlig for begivenheden |
| `InitiatingProcessId` | `int` | Proces-id (PID) for den proces, der startede hændelsen |
| `InitiatingProcessCommandLine` | `string` | Kommandolinje, der bruges til at køre den proces, der startede hændelsen |
| `InitiatingProcessCreationTime` | `datetime` | Dato og klokkeslæt for den proces, der startede hændelsen blev startet |
| `InitiatingProcessFolderPath` | `string` | Mappe, der indeholder den proces (billedfil), som startede hændelsen |
| `InitiatingProcessParentFileName` | `string` | Navnet på den overordnede proces, hvor den proces, der er ansvarlig for begivenheden, blev vist |
| `InitiatingProcessParentId` | `int` | Proces-id (PID) for den overordnede proces, der identificerede den proces, der er ansvarlig for begivenheden |
| `InitiatingProcessParentCreationTime` | `datetime` | Dato og klokkeslæt, hvor den overordnede for den proces, der er ansvarlig for begivenheden, blev startet |
| `InitiatingProcessAccountDomain` | `string` | Domæne for den konto, der kørte processen, der er ansvarlig for begivenheden |
| `InitiatingProcessAccountName` | `string` | Brugernavnet på den konto, der kørte den proces, der er ansvarlig for begivenheden |
| `InitiatingProcessAccountSid` | `string` | Security Identifier (SID) for den konto, der kørte den proces, der er ansvarlig for hændelsen |
| `InitiatingProcessAccountUpn` | `string` | Brugerens hovednavn (UPN) for den konto, der kørte processen med ansvar for begivenheden |
| `InitiatingProcessAccountObjectId` | `string` | Azure AD-objekt-id'et for den brugerkonto, der kørte den proces, der er ansvarlig for begivenheden |
| `InitiatingProcessIntegrityLevel` | `string` | Integritetsniveauet for den proces, der startede hændelsen. Windows tildeler integritetsniveauer til processer, der er baseret på bestemte egenskaber, f.eks. hvis de blev startet fra en internetoverførsel. Disse integritetsniveauer påvirker tilladelser til ressourcer |
| `InitiatingProcessTokenElevation` | `string` | Tokentype, der angiver tilstedeværelse eller fravær af UAC-rettighedskontering anvendt på den proces, der startede hændelsen |
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
