---
title: Tabellen EmailUrlInfo i det avancerede jagtskema
description: Få mere at vide om URL-adresse eller linkoplysninger i tabellen EmailUrlInfo i det avancerede jagtskema
keywords: avanceret jagt, trusselsjagt, cybertrusselsjagt, Microsoft 365 Defender, microsoft 365, m365, søgning, forespørgsel, telemetri, skemareference, kusto, tabel, kolonne, datatype, beskrivelse, EmailUrlInfo, netværksmeddelelses-id, url, link
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
ms.openlocfilehash: 9453a5a7ddb48ff09ca217aa23c5e557d57d00e5
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/29/2022
ms.locfileid: "65130949"
---
# <a name="emailurlinfo"></a>EmailUrlInfo

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender
- Microsoft Defender for Office 365

Tabellen `EmailUrlInfo` i det [avancerede jagtskema](advanced-hunting-overview.md) indeholder oplysninger om URL-adresser i mails og vedhæftede filer, der behandles af Microsoft Defender for Office 365. Brug denne reference til at oprette forespørgsler, der returnerer oplysninger fra denne tabel. 

Du kan finde oplysninger om andre tabeller i det avancerede jagtskema [i referencen til avanceret jagt](advanced-hunting-schema-tables.md).

| Kolonnenavn | Datatype | Beskrivelse |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Dato og klokkeslæt for registrering af hændelsen |
| `NetworkMessageId` | `string` | Entydigt id for mailen, der genereres af Microsoft 365 |
| `Url` | `string` | Fuldstændig URL-adresse i mailens emne, brødtekst eller vedhæftede fil |
| `UrlDomain` | `string` | URL-adressens domænenavn eller værtsnavn |
| `ReportId` | `long` | Hændelses-id baseret på en gentaget tæller. Hvis du vil identificere entydige hændelser, skal denne kolonne bruges sammen med kolonnerne DeviceName og Timestamp |

## <a name="related-topics"></a>Relaterede emner
- [Oversigt over avanceret jagt](advanced-hunting-overview.md)
- [Få mere at vide om forespørgselssproget](advanced-hunting-query-language.md)
- [Brug delte forespørgsler](advanced-hunting-shared-queries.md)
- [Lede på tværs af enheder, mails, apps og identiteter](advanced-hunting-query-emails-devices.md)
- [Forstå skemaet](advanced-hunting-schema-tables.md)
- [Anvend bedste praksis for forespørgsler](advanced-hunting-best-practices.md)
