---
title: Tabellen AlertEvidence i det avancerede jagtskema
description: Få mere at vide om de oplysninger, der er knyttet til beskeder i tabellen AlertEvidence i det avancerede jagtskema
keywords: avanceret jagt, trusselssøgning, cybertrusler på jagt, Microsoft 365 Defender, microsoft 365, m365, søg, forespørgsel, telemetri, skemareference, kusto, tabel, kolonne, datatype, beskrivelse, AlertInfo, alert,tities, bevis, fil, IP-adresse, enhed, computer, bruger, konto
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
ms.openlocfilehash: 9d7fc7e757b15c3682368cbd6c41b32c18724422
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/15/2021
ms.locfileid: "63591811"
---
# <a name="alertevidence"></a>AlertEvidence

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender

Tabellen `AlertEvidence` i det avancerede [](advanced-hunting-overview.md) jagtskema indeholder oplysninger om forskellige enheder – filer, IP-adresser, URL-adresser, brugere eller enheder – der er knyttet til beskeder fra Microsoft Defender til Slutpunkt, Microsoft Defender til Office 365, Microsoft Defender til skyapps og Microsoft Defender for Identity. Brug denne reference til at oprette forespørgsler, der returnerer oplysninger fra denne tabel.

Du kan finde oplysninger om andre tabeller i det avancerede jagtskema i [den avancerede jagtreference](advanced-hunting-schema-tables.md).

| Kolonnenavn | Datatype | Beskrivelse |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Dato og klokkeslæt for, hvornår begivenheden blev optaget |
| `AlertId` | `string` | Entydigt id for beskeden |
| `ServiceSource` | `string` | Produkt eller tjeneste, der gav beskedoplysningerne |
| `EntityType` | `string` | Objekttype, f.eks. en fil, en proces, en enhed eller en bruger |
| `EvidenceRole` | `string` | Hvordan enheden er involveret i en besked, der angiver, om den er påvirket eller blot er relateret |
| `EvidenceDirection` | `string` | Angiver, om enheden er kilden eller destinationen for en netværksforbindelse |
| `FileName` | `string` | Navnet på den fil, som den optagede handling blev anvendt på |
| `FolderPath` | `string` | Mappe, der indeholder den fil, som den optagede handling blev anvendt på |
| `SHA1` | `string` | SHA-1 i den fil, som den optagede handling blev anvendt på |
| `SHA256` | `string` | SHA-256 af den fil, som den optagede handling blev anvendt på. Dette felt udfyldes normalt ikke – brug kolonnen SHA1, når den er tilgængelig. |
| `FileSize` | `int` | Filens størrelse i byte |
| `ThreatFamily` | `string` | Malwarefamilie, som den mistænkelige eller skadelige fil eller proces er blevet klassificeret under |
| `RemoteIP` | `string` | IP-adresse, der blev knyttet til |
| `RemoteUrl` | `string` | URL-adressen eller det fulde domænenavn, der blev knyttet til |
| `AccountName` | `string` | Brugernavn på kontoen |
| `AccountDomain` | `string` | Kontoens domæne |
| `AccountSid` | `string` | Kontoens sikkerheds-id (SID) |
| `AccountObjectId` | `string` | Entydigt id for kontoen i Azure Active Directory |
| `AccountUpn` | `string` | Brugerens hovednavn (UPN) for kontoen |
| `DeviceId` | `string` | Entydigt id for enheden i tjenesten |
| `DeviceName` | `string` | Fuldt kvalificeret domænenavn på computeren |
| `LocalIP` | `string` | IP-adresse tildelt den lokale enhed, der bruges under kommunikation |
| `NetworkMessageId` | `string` | Entydigt id for den mail, der genereres af Office 365 |
| `EmailSubject` | `string` | Mailens emne |
| `ApplicationId` | `string` | Entydigt id for programmet |
| `Application` | `string` | Program, der udførte den optagede handling |
| `ProcessCommandLine` | `string` | Kommandolinje, der bruges til at oprette den nye proces |
| `AdditionalFields` | `string` | Yderligere oplysninger om hændelsen i JSON-matrixformat |
| `RegistryKey` |`string` | Registreringsdatabasenøgle, som den optagede handling blev anvendt på |
| `RegistryValueName` |`string` | Navnet på den registreringsdatabaseværdi, som den registrerede handling blev anvendt på |
| `RegistryValueData` |`string` | Data for den registreringsdatabaseværdi, som den registrerede handling blev anvendt på |

## <a name="related-topics"></a>Relaterede emner
- [Avanceret jagtoversigt](advanced-hunting-overview.md)
- [Lær forespørgselssproget](advanced-hunting-query-language.md)
- [Brug delte forespørgsler](advanced-hunting-shared-queries.md)
- [Lede på tværs af enheder, mails, apps og identiteter](advanced-hunting-query-emails-devices.md)
- [Forstå skemaet](advanced-hunting-schema-tables.md)
- [Anvend bedste fremgangsmåder for forespørgsler](advanced-hunting-best-practices.md)
