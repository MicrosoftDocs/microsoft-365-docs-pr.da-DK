---
title: Tabellen DeviceLogonEvents i det avancerede jagtskema
description: Få mere at vide om godkendelses- eller logonhændelser i tabellen DeviceLogonEvents i det avancerede jagtskema
keywords: avanceret jagt, trusselsjagt, cybertrusselsjagt, Microsoft 365 Defender, microsoft 365, m365, søgning, forespørgsel, telemetri, skemareference, kusto, tabel, kolonne, datatype, beskrivelse, logonevents, DeviceLogonEvents, godkendelse, logon, log på
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
ms.openlocfilehash: 516b74eb8d1e62194718e0ad3234b3269e07fb83
ms.sourcegitcommit: dd7e5b67ff4ae4e7f74490e437c1795933c74cc7
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/08/2022
ms.locfileid: "64731367"
---
# <a name="devicelogonevents"></a>DeviceLogonEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender
- Microsoft Defender for Endpoint



Tabellen `DeviceLogonEvents` i det [avancerede jagtskema](advanced-hunting-overview.md) indeholder oplysninger om brugerlogon og andre godkendelseshændelser på enheder. Brug denne reference til at oprette forespørgsler, der returnerer oplysninger fra denne tabel.

>[!TIP]
> Du kan finde detaljerede oplysninger om de hændelsestyper (`ActionType` værdier), der understøttes af en tabel, ved at bruge den indbyggede skemareference, der er tilgængelig i Defender for Cloud.

Du kan finde oplysninger om andre tabeller i det avancerede jagtskema [i referencen til avanceret jagt](advanced-hunting-schema-tables.md).

| Kolonnenavn | Datatype | Beskrivelse |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Dato og klokkeslæt for registrering af hændelsen |
| `DeviceId` | `string` | Entydigt id for computeren i tjenesten |
| `DeviceName` | `string` | Fuldt kvalificeret domænenavn (FQDN) på computeren |
| `ActionType` | `string` |Aktivitetstype, der udløste hændelsen |
| `LogonType` | `string` | Type af logonsession, specifikt:<br><br> - **Interaktiv** – Brugeren interagerer fysisk med computeren ved hjælp af det lokale tastatur og den lokale skærm<br><br> - **RDP-logon (Remote Interactive)** – Brugeren interagerer med computeren eksternt ved hjælp af Fjernskrivebord, Terminal Services, Fjernsupport eller andre RDP-klienter<br><br> - **Netværk** – Sessionen startes, når computeren tilgås ved hjælp af PsExec, eller når der opnås adgang til delte ressourcer på computeren, f.eks. printere og delte mapper<br><br> - **Batch** – Session startet af planlagte opgaver<br><br> - **Service** – Session startet af tjenester, når de starter<br> |
| `AccountDomain` | `string` | Kontoens domæne |
| `AccountName` | `string` | Brugernavnet på kontoen |
| `AccountSid` | `string` | Sikkerheds-id (SID) for kontoen |
| `Protocol` | `string` | Protokol, der bruges under kommunikationen |
| `FailureReason` | `string` | Oplysninger, der forklarer, hvorfor den registrerede handling mislykkedes |
| `IsLocalAdmin` | `boolean` | Boolesk indikator for, om brugeren er en lokal administrator på computeren |
| `LogonId` | `string` | Id for en logonsession. Dette id er kun entydigt på den samme computer mellem genstart |
| `RemoteDeviceName` | `string` | Navnet på den computer, der udførte en fjernhandling på den pågældende computer. Afhængigt af den hændelse, der rapporteres, kan dette navn være et fuldt kvalificeret domænenavn (FQDN), et NetBIOS-navn eller et værtsnavn uden domæneoplysninger |
| `RemoteIP` | `string` | IP-adresse, der blev oprettet forbindelse til |
| `RemoteIPType` | `string` | IP-adressetype, f.eks. offentlig, privat, reserveret, tilbagekobling, Teredo, FourToSixMapping og broadcast |
| `RemotePort` | `int` | TCP-port på den eksterne enhed, der blev tilsluttet |
| `InitiatingProcessAccountDomain` | `string` | Domænet for den konto, der kørte processen, som er ansvarlig for hændelsen |
| `InitiatingProcessAccountName` | `string` | Brugernavnet på den konto, der kørte den proces, der er ansvarlig for hændelsen |
| `InitiatingProcessAccountSid` | `string` | Sikkerheds-id (SID) for den konto, der kørte processen, der er ansvarlig for hændelsen |
| `InitiatingProcessAccountUpn` | `string` | Brugerens hovednavn (UPN) for den konto, der kørte den proces, der er ansvarlig for hændelsen |
| ` InitiatingProcessAccountObjectId` | `string` | Azure AD-objekt-id for den brugerkonto, der kørte processen, der er ansvarlig for hændelsen |
| `InitiatingProcessIntegrityLevel` | `string` | Integritetsniveau for den proces, der startede hændelsen. Windows tildeler integritetsniveauer til processer baseret på visse egenskaber, f.eks. hvis de blev startet fra en download på internettet. Disse integritetsniveauer påvirker tilladelser til ressourcer |
| `InitiatingProcessTokenElevation` | `string` | Tokentype, der angiver tilstedeværelsen eller fraværet af udvidede rettigheder for Bruger Access Control (UAC) for den proces, der startede hændelsen |
| `InitiatingProcessSHA1` | `string` | SHA-1 for den proces (billedfil), der startede hændelsen |
| `InitiatingProcessSHA256` | `string` | SHA-256 for den proces (billedfil), der startede hændelsen. Dette felt udfyldes normalt ikke. Brug kolonnen SHA1, når det er tilgængeligt |
| `InitiatingProcessMD5` | `string` | MD5-hash for den proces (billedfil), der startede hændelsen |
| `InitiatingProcessFileName` | `string` | Navnet på den proces, der startede hændelsen |
| `InitiatingProcessFileSize` | `long` | Størrelsen på den fil, der kørte den proces, der er ansvarlig for hændelsen |
| `InitiatingProcessVersionInfoCompanyName` | `string` | Firmanavn fra versionsoplysningerne for processen (billedfilen), der er ansvarlig for hændelsen |
| `InitiatingProcessVersionInfoProductName` | `string` | Produktnavn fra versionsoplysningerne for processen (billedfilen), der er ansvarlig for hændelsen |
| `InitiatingProcessVersionInfoProductVersion` | `string` | Produktversion fra versionsoplysningerne for processen (billedfilen), der er ansvarlig for hændelsen |
| `InitiatingProcessVersionInfoInternalFileName` | `string` | Internt filnavn fra versionsoplysningerne for processen (billedfilen), der er ansvarlig for hændelsen |
| `InitiatingProcessVersionInfoOriginalFileName` | `string` | Oprindeligt filnavn fra versionsoplysningerne for processen (billedfilen), der er ansvarlig for hændelsen |
| `InitiatingProcessVersionInfoFileDescription` | `string` | Beskrivelse fra versionsoplysningerne for den proces (billedfil), der er ansvarlig for hændelsen |
| `InitiatingProcessId` | `int` | Proces-id (PID) for den proces, der startede hændelsen |
| `InitiatingProcessCommandLine` | `string` | Kommandolinje, der bruges til at køre den proces, der startede hændelsen |
| `InitiatingProcessCreationTime` | `datetime` | Dato og klokkeslæt for, hvornår den proces, der startede hændelsen, blev startet |
| `InitiatingProcessFolderPath` | `string` | Mappe, der indeholder den proces (billedfil), der startede hændelsen |
| `InitiatingProcessParentId` | `int` | Proces-id (PID) for den overordnede proces, der forgrenede processen, der er ansvarlig for hændelsen |
| `InitiatingProcessParentFileName` | `string` | Navnet på den overordnede proces, der forgrenede processen, der er ansvarlig for hændelsen |
| `InitiatingProcessParentCreationTime` | `datetime` | Dato og klokkeslæt for, hvornår den overordnede for den proces, der er ansvarlig for hændelsen, blev startet |
| `ReportId` | `long` | Hændelses-id baseret på en gentaget tæller. Hvis du vil identificere entydige hændelser, skal denne kolonne bruges sammen med kolonnerne DeviceName og Timestamp |
| `AppGuardContainerId` | `string` | Identifikator for den virtualiserede objektbeholder, der bruges af Application Guard til at isolere browseraktivitet |
| `AdditionalFields` | `string` | Yderligere oplysninger om hændelsen i JSON-matrixformat |

>[!NOTE]
>Samlingen af DeviceLogonEvents understøttes ikke på Windows 7- eller Windows Server 2008R2-enheder, der er onboardet til Defender for Endpoint. Vi anbefaler, at du opgraderer til et nyere operativsystem for at få optimal synlighed i brugerlogonaktiviteten.

## <a name="related-topics"></a>Relaterede emner
- [Oversigt over avanceret jagt](advanced-hunting-overview.md)
- [Få mere at vide om forespørgselssproget](advanced-hunting-query-language.md)
- [Brug delte forespørgsler](advanced-hunting-shared-queries.md)
- [Lede på tværs af enheder, mails, apps og identiteter](advanced-hunting-query-emails-devices.md)
- [Forstå skemaet](advanced-hunting-schema-tables.md)
- [Anvend bedste praksis for forespørgsler](advanced-hunting-best-practices.md)
