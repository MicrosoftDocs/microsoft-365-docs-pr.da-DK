---
title: Tabellen IdentityInfo i det avancerede søgeskema
description: Få mere at vide om brugerkontooplysninger i tabellen IdentityInfo i det avancerede jagtskema
keywords: avanceret jagt, trusselssøgning, cybertrusler på jagt, Microsoft 365 Defender, microsoft 365, m365, søgning, forespørgsel, telemetri, skemareference, kusto, tabel, kolonne, datatype, beskrivelse, AccountInfo, IdentityInfo, konto
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
ms.openlocfilehash: b09d1774ab35dbca9119deb98864d6c6f78051a9
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/15/2021
ms.locfileid: "63592893"
---
# <a name="identityinfo"></a>IdentityInfo

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender

Tabellen `IdentityInfo` i det avancerede [jagtskema](advanced-hunting-overview.md) indeholder oplysninger om brugerkonti, der er hentet fra forskellige tjenester, herunder Azure Active Directory. Brug denne reference til at oprette forespørgsler, der returnerer oplysninger fra denne tabel.

>[!NOTE]
>Denne tabel blev omdøbt fra `AccountInfo`. Under omdøbninger opdateres alle forespørgsler, der er gemt i portalen, automatisk. Kontrollér forespørgsler, du har gemt et andet sted.

Du kan finde oplysninger om andre tabeller i det avancerede jagtskema i [den avancerede jagtreference](advanced-hunting-schema-tables.md).

| Kolonnenavn | Datatype | Beskrivelse |
|-------------|-----------|-------------|
| `AccountObjectId` | `string` | Entydigt id for kontoen i Azure AD |
| `AccountUpn` | `string` | Brugerens hovednavn (UPN) for kontoen |
| `OnPremSid` | `string` | Det lokale sikkerheds-id (SID) for kontoen |
| `CloudSid` | `string` | Skysikkerheds-id for kontoen |
| `GivenName` | `string` | Det angivne navn eller fornavn for kontoens bruger |
| `Surname` | `string` | Efternavn, familienavn eller efternavn på kontoens bruger |
| `AccountDisplayName` | `string` | Navnet på den kontobruger, der vises i adressekartoteket. Typisk en kombination af et givet navn eller fornavn, et mellemnavn og efternavn. |
| `Department` | `string` | Navnet på den afdeling, som kontoens bruger tilhører |
| `JobTitle` | `string` | Kontoens stilling |
| `AccountName` | `string` | Brugernavn på kontoen |
| `AccountDomain` | `string` | Kontoens domæne |
| `EmailAddress` | `string` | SMTP-adressen for kontoen |
| `SipProxyAddress` | `string` | Voice over IP-adressen (VOIP) session initiation protocol (SIP) for kontoen |
| `City` | `string` | By, hvor kontobrugeren er placeret |
| `Country` | `string` | Land/område, hvor kontobrugeren er placeret |
| `IsAccountEnabled` | `boolean` | Angiver, om kontoen er aktiveret eller ej |

## <a name="related-topics"></a>Relaterede emner
- [Avanceret jagtoversigt](advanced-hunting-overview.md)
- [Lær forespørgselssproget](advanced-hunting-query-language.md)
- [Brug delte forespørgsler](advanced-hunting-shared-queries.md)
- [Lede på tværs af enheder, mails, apps og identiteter](advanced-hunting-query-emails-devices.md)
- [Forstå skemaet](advanced-hunting-schema-tables.md)
- [Anvend bedste fremgangsmåder for forespørgsler](advanced-hunting-best-practices.md)
