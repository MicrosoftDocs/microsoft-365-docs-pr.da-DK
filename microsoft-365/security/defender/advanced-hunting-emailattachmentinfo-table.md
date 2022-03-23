---
title: Tabellen EmailAttachmentInfo i det avancerede jagtskema
description: Få mere at vide om oplysninger om vedhæftede filer i mail i tabellen EmailAttachmentInfo i det avancerede jagtskema
keywords: avanceret jagt, trusselssøgning, cybertrusler på jagt, Microsoft 365 Defender, microsoft 365, m365, søg, forespørgsel, telemetri, skemareference, kusto, tabel, kolonne, datatype, beskrivelse, EmailAttachmentInfo, netværksmeddelelses-id, afsender, modtager, vedhæftet id, navn på vedhæftet fil, malwarekontur
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
ms.openlocfilehash: ac3e7aeff6778709f68aa1da74446cf55a1a6c06
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/15/2021
ms.locfileid: "63593548"
---
# <a name="emailattachmentinfo"></a>EmailAttachmentInfo

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**

- Microsoft 365 Defender

Tabellen `EmailAttachmentInfo` i det avancerede [søgeskema](advanced-hunting-overview.md) indeholder oplysninger om vedhæftede filer i mails, der behandles af Microsoft Defender Office 365. Brug denne reference til at oprette forespørgsler, der returnerer oplysninger fra denne tabel.

Du kan finde oplysninger om andre tabeller i det avancerede jagtskema i [den avancerede jagtreference](advanced-hunting-schema-tables.md).

> [!IMPORTANT]
> Nogle oplysninger relaterer til foreløbige produkter, som kan ændres væsentligt, før det frigives kommercielt. Microsoft påser ingen garantier, udtrykkelige eller underforståede, med hensyn til de oplysninger, du har angivet her.

| Kolonnenavn | Datatype | Beskrivelse |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Dato og klokkeslæt for, hvornår begivenheden blev optaget |
| `NetworkMessageId` | `string` | Entydigt id for den mail, der genereres af Microsoft 365 |
| `SenderFromAddress` | `string` | Afsendermailadressen i overskriften FROM, som er synlig for mailmodtagere på deres mailklienter |
| `SenderDisplayName` | `string` | Navnet på afsenderen, der vises i adressekartoteket, typisk en kombination af et givet eller fornavn, en indledende mellemnavn og et efternavn eller efternavn |
| `SenderObjectId` | `string` | Entydigt id for afsenderens konto i Azure AD |
| `RecipientEmailAddress` | `string` | Mailadressen på modtageren eller modtagerens mailadresse efter udvidelse af distributionslisten |
| `RecipientObjectId` | `string` | Entydigt id for mailmodtageren i Azure AD |
| `FileName` | `string` | Navnet på den fil, som den optagede handling blev anvendt på |
| `FileType` | `string` | Filtypenavn |
| `SHA256` | `string` | SHA-256 af den fil, som den optagede handling blev anvendt på. Dette felt udfyldes normalt ikke – brug kolonnen SHA1, når den er tilgængelig. |
| `ThreatTypes` | `string` | Konklusion fra mailfiltreringsstakken for, om mailen indeholder malware, phishing eller andre trusler |
| `ThreatNames` | `string` | Registreringsnavn for malware eller andre trusler fundet |
| `DetectionMethods` | `string` | Metoder til at detektere malware, phishing eller andre trusler, der findes i mailen |
| `ReportId` | `long` | Hændelses-id baseret på en gentagende tæller. Denne kolonne skal bruges sammen med kolonnerne DeviceName og Timetamp til at identificere entydige hændelser. |
| `FileSize` | `string` | Filens størrelse i byte |

## <a name="related-topics"></a>Relaterede emner

- [Avanceret jagtoversigt](advanced-hunting-overview.md)
- [Lær forespørgselssproget](advanced-hunting-query-language.md)
- [Brug delte forespørgsler](advanced-hunting-shared-queries.md)
- [Lede på tværs af enheder, mails, apps og identiteter](advanced-hunting-query-emails-devices.md)
- [Forstå skemaet](advanced-hunting-schema-tables.md)
- [Anvend bedste fremgangsmåder for forespørgsler](advanced-hunting-best-practices.md)
