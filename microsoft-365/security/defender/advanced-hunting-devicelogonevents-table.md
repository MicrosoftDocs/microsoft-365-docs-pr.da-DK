---
title: DeviceLogonEvents-tabel i det avancerede jagtskema
description: Få mere at vide om godkendelses- eller logonhændelser i DeviceLogonEvents-tabellen i det avancerede jagtskema
keywords: avanceret jagt, trusselssøgning, cybertrusler på jagt, Microsoft 365 Defender, microsoft 365, m365, søg, forespørgsel, telemetri, skemareference, kusto, tabel, kolonne, datatype, beskrivelse, logonevents, DeviceLogonEvents, godkendelse, logon, log på
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
ms.openlocfilehash: dbafb4c967bca09195277aa4c79c95dd1dc87afb
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/15/2021
ms.locfileid: "63592040"
---
# <a name="devicelogonevents"></a>DeviceLogonEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender
- Microsoft Defender til Slutpunkt



Tabellen `DeviceLogonEvents` i det avancerede [skema indeholder](advanced-hunting-overview.md) oplysninger om brugerlogon og andre godkendelseshændelser på enheder. Brug denne reference til at oprette forespørgsler, der returnerer oplysninger fra denne tabel.

>[!TIP]
> Du kan finde detaljerede oplysninger om de hændelsestyper (`ActionType` værdier), der understøttes af en tabel, ved at bruge den indbyggede skemareference, der er tilgængelig i Defender for Cloud.

Du kan finde oplysninger om andre tabeller i det avancerede jagtskema i [den avancerede jagtreference](advanced-hunting-schema-tables.md).

| Kolonnenavn | Datatype | Beskrivelse |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Dato og klokkeslæt for, hvornår begivenheden blev optaget |
| `DeviceId` | `string` | Entydigt id for computeren i tjenesten |
| `DeviceName` | `string` | Fuldt kvalificeret domænenavn på computeren |
| `ActionType` | `string` |Aktivitetstype, der udløste begivenheden |
| `LogonType` | `string` | Logonsessionstype, mere specifikt:<br><br> - **Interaktiv** – Brugeren interagerer fysisk med maskinen ved hjælp af det lokale tastatur og den lokale skærm<br><br> - **Fjerninter interaktive logons (RDP)** – Brugeren interagerer med computeren eksternt ved hjælp af Fjernskrivebord, TerminalTjenester, Fjernsupport eller andre RDP-klienter<br><br> - **Netværk** – Session startet, når computeren åbnes ved hjælp af PsExec, eller når delte ressourcer på computeren, f.eks. printere og delte mapper, tilgås<br><br> - **Batch** – Session startet af planlagte opgaver<br><br> - **Tjeneste** – session startet af tjenester, når de starter<br> |
| `AccountDomain` | `string` | Kontoens domæne |
| `AccountName` | `string` | Brugernavn på kontoen |
| `AccountSid` | `string` | Kontoens sikkerheds-id (SID) |
| `Protocol` | `string` | Protokol, der bruges under kommunikation |
| `FailureReason` | `string` | Oplysninger, der forklarer, hvorfor den registrerede handling mislykkedes |
| `IsLocalAdmin` | `boolean` | Boolesk indikator for, om brugeren er en lokal administrator på computeren |
| `LogonId` | `string` | Id for en logonsession. Dette id er entydigt på den samme maskine, kun mellem genstart |
| `RemoteDeviceName` | `string` | Navnet på den computer, der udførte en fjernhandling på den pågældende computer. Afhængigt af den hændelse, der rapporteres, kan dette navn være et fuldt kvalificeret domænenavn, et NetABAS-navn eller et værtsnavn uden domæneoplysninger |
| `RemoteIP` | `string` | IP-adresse, der blev knyttet til |
| `RemoteIPType` | `string` | Type af IP-adresse, f.eks. Offentlig, Privat, Reserveret, Loopback, Teredo, FourToSixMapping og Udsendelse |
| `RemotePort` | `int` | TCP-port på den eksterne enhed, der blev forbundet til |
| `InitiatingProcessAccountDomain` | `string` | Domæne for den konto, der kørte processen, der er ansvarlig for begivenheden |
| `InitiatingProcessAccountName` | `string` | Brugernavnet på den konto, der kørte den proces, der er ansvarlig for begivenheden |
| `InitiatingProcessAccountSid` | `string` | Security Identifier (SID) for den konto, der kørte den proces, der er ansvarlig for hændelsen |
| `InitiatingProcessAccountUpn` | `string` | Brugerens hovednavn (UPN) for den konto, der kørte processen med ansvar for begivenheden |
| ` InitiatingProcessAccountObjectId` | `string` | Azure AD-objekt-id'et for den brugerkonto, der kørte den proces, der er ansvarlig for begivenheden |
| `InitiatingProcessIntegrityLevel` | `string` | Integritetsniveauet for den proces, der startede hændelsen. Windows tildeler integritetsniveauer til processer, der er baseret på bestemte egenskaber, f.eks. hvis de blev startet fra en internetoverførsel. Disse integritetsniveauer påvirker tilladelser til ressourcer |
| `InitiatingProcessTokenElevation` | `string` | Tokentype, der angiver tilstedeværelse eller fravær af UAC-rettighedskontering anvendt på den proces, der startede hændelsen |
| `InitiatingProcessSHA1` | `string` | SHA-1 af den proces (billedfil), der startede hændelsen |
| `InitiatingProcessSHA256` | `string` | SHA-256 af den proces (billedfil), der startede hændelsen. Dette felt udfyldes normalt ikke – brug kolonnen SHA1, når den er tilgængelig |
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
| `InitiatingProcessParentId` | `int` | Proces-id (PID) for den overordnede proces, der identificerede den proces, der er ansvarlig for begivenheden |
| `InitiatingProcessParentFileName` | `string` | Navnet på den overordnede proces, hvor den proces, der er ansvarlig for begivenheden, blev vist |
| `InitiatingProcessParentCreationTime` | `datetime` | Dato og klokkeslæt, hvor den overordnede for den proces, der er ansvarlig for begivenheden, blev startet |
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
