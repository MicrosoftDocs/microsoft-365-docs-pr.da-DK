---
title: Tabellen IdentityQueryEvents i det avancerede jagtskema
description: Få mere at vide om hændelser i Active Directory-forespørgsel i tabellen IdentityQueryEvents i det avancerede jagtskema
keywords: avanceret jagt, trusselssøgning, cybertrusler på jagt, Microsoft 365 Defender, microsoft 365, m365, søgning, forespørgsel, telemetri, skemareference, kusto, tabel, kolonne, datatype, beskrivelse, IdentityQueryEvents, Azure AD, Active Directory, Microsoft Defender til identitet, identiteter, LDAP-forespørgsler
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
ms.openlocfilehash: 0b3c98b629d8984b984af3f3dba25a65ab7671e6
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/15/2021
ms.locfileid: "63591915"
---
# <a name="identityqueryevents"></a>IdentityQueryEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender

Tabellen `IdentityQueryEvents` i det avancerede [søgeskema](advanced-hunting-overview.md) indeholder oplysninger om forespørgsler, der udføres mod Active Directory-objekter, f.eks. brugere, grupper, enheder og domæner. Brug denne reference til at oprette forespørgsler, der returnerer oplysninger fra denne tabel.

>[!TIP]
> Du kan finde detaljerede oplysninger om de hændelsestyper (`ActionType` værdier), der understøttes af en tabel, ved at bruge den indbyggede skemareference, der er tilgængelig i Defender for Cloud.

Du kan finde oplysninger om andre tabeller i det avancerede jagtskema i [den avancerede jagtreference](advanced-hunting-schema-tables.md).

| Kolonnenavn | Datatype | Beskrivelse |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Dato og klokkeslæt for, hvornår begivenheden blev optaget |
| `ActionType` | `string` | Aktivitetstype, der udløste hændelsen. Se [skemareferencen i portalen for at](advanced-hunting-schema-tables.md?#get-schema-information-in-the-security-center) få mere at vide |
| `Application` | `string` | Program, der udførte den optagede handling |
| `QueryType` | `string` | Forespørgselstype, f.eks. QueryGroup, QueryUser eller EnumerateUsers |
| `QueryTarget` | `string` | Navn på bruger, gruppe, enhed, domæne eller en anden enhedstype, der forespørges |
| `Query` | `string` | Streng, der bruges til at køre forespørgslen |
| `Protocol` | `string` | Protokol, der bruges under kommunikation |
| `AccountName` | `string` | Brugernavn på kontoen |
| `AccountDomain` | `string` | Kontoens domæne |
| `AccountUpn` | `string` | Brugerens hovednavn (UPN) for kontoen |
| `AccountSid` | `string` | Kontoens sikkerheds-id (SID) |
| `AccountObjectId` | `string` | Entydigt id for kontoen i Azure AD |
| `AccountDisplayName` | `string` | Navnet på den kontobruger, der vises i adressekartoteket. Typisk en kombination af et givet navn eller fornavn, et mellemnavn og efternavn. |
| `DeviceName` | `string` | Fuldt kvalificeret domænenavn for slutpunktet |
| `IPAddress` | `string` | IP-adresse, der er tildelt slutpunktet og brugt under relateret netværkskommunikation |
| `Port` | `string` | TCP-port, der bruges under kommunikation |
| `DestinationDeviceName` | `string` | Navnet på den enhed, der kører det serverprogram, der behandler den optagede handling |
| `DestinationIPAddress` | `string` | IP-adressen på den enhed, der kører det serverprogram, der behandler den optagede handling |
| `DestinationPort` | `string` | Destinationsport for relateret netværkskommunikation |
| `TargetDeviceName` | `string` | Fuldt kvalificeret domænenavn for den enhed, som den optagede handling blev anvendt på |
| `TargetAccountUpn` | `string` | Brugerens hovednavn (UPN) for den konto, som den registrerede handling blev anvendt på |
| `TargetAccountDisplayName` | `string` | Visningsnavnet for den konto, som den registrerede handling blev anvendt på |
| `Location` | `string` | By, land eller anden geografisk placering, der er knyttet til begivenheden |
| `ReportId` | `long` | Entydigt id for hændelsen |
| `AdditionalFields` | `string` | Yderligere oplysninger om enheden eller hændelsen |

## <a name="related-topics"></a>Relaterede emner
- [Avanceret jagtoversigt](advanced-hunting-overview.md)
- [Lær forespørgselssproget](advanced-hunting-query-language.md)
- [Brug delte forespørgsler](advanced-hunting-shared-queries.md)
- [Lede på tværs af enheder, mails, apps og identiteter](advanced-hunting-query-emails-devices.md)
- [Forstå skemaet](advanced-hunting-schema-tables.md)
- [Anvend bedste fremgangsmåder for forespørgsler](advanced-hunting-best-practices.md)
