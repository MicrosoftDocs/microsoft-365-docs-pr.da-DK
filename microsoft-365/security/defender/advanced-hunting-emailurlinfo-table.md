---
title: Tabellen EmailUrlInfo i det avancerede jagtskema
description: Få mere at vide om URL-adresse eller linkoplysninger i tabellen EmailUrlInfo i det avancerede jagtskema
keywords: avanceret jagt, trusselssøgning, cybertrusel, Microsoft 365 Defender, microsoft 365, m365, søgning, forespørgsel, telemetri, skemareference, kusto, tabel, kolonne, datatype, beskrivelse, EmailUrlInfo, netværksmeddelelses-id, URL, link
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
ms.openlocfilehash: d0c9a8f1456aaeedbc8d296a1f738d0b2c57a156
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/15/2021
ms.locfileid: "63593547"
---
# <a name="emailurlinfo"></a>EmailUrlInfo

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender

Tabellen `EmailUrlInfo` i det avancerede [søgeskema](advanced-hunting-overview.md) indeholder oplysninger om URL-adresser på mails og vedhæftede filer, der behandles af Microsoft Defender Office 365. Brug denne reference til at oprette forespørgsler, der returnerer oplysninger fra denne tabel. 

Du kan finde oplysninger om andre tabeller i det avancerede jagtskema i [den avancerede jagtreference](advanced-hunting-schema-tables.md).

| Kolonnenavn | Datatype | Beskrivelse |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Dato og klokkeslæt for, hvornår begivenheden blev optaget |
| `NetworkMessageId` | `string` | Entydigt id for den mail, der genereres af Microsoft 365 |
| `Url` | `string` | Den fulde URL-adresse i mailens emne, brødtekst eller vedhæftede fil |
| `UrlDomain` | `string` | URL-adressens domænenavn eller værtsnavn |
| `ReportId` | `long` | Hændelses-id baseret på en gentagende tæller. For at identificere entydige hændelser skal denne kolonne bruges sammen med kolonnerne DeviceName og Timestamp |

## <a name="related-topics"></a>Relaterede emner
- [Avanceret jagtoversigt](advanced-hunting-overview.md)
- [Lær forespørgselssproget](advanced-hunting-query-language.md)
- [Brug delte forespørgsler](advanced-hunting-shared-queries.md)
- [Lede på tværs af enheder, mails, apps og identiteter](advanced-hunting-query-emails-devices.md)
- [Forstå skemaet](advanced-hunting-schema-tables.md)
- [Anvend bedste fremgangsmåder for forespørgsler](advanced-hunting-best-practices.md)
