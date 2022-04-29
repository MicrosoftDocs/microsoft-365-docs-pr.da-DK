---
title: Tabellen EmailAttachmentInfo i det avancerede jagtskema
description: Få mere at vide om oplysninger om vedhæftede filer i mails i tabellen EmailAttachmentInfo i det avancerede jagtskema
keywords: avanceret jagt, trusselsjagt, cybertrusselsjagt, Microsoft 365 Defender, microsoft 365, m365, søgning, forespørgsel, telemetri, skemareference, kusto, tabel, kolonne, datatype, beskrivelse, EmailAttachmentInfo, netværksmeddelelses-id, afsender, modtager, vedhæftet id, vedhæftet fils navn, malware-dom
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
ms.openlocfilehash: b99daf9fa7597e44dc7ea20b517c2f7ed5aaa354
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/29/2022
ms.locfileid: "65130555"
---
# <a name="emailattachmentinfo"></a>EmailAttachmentInfo

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**

- Microsoft 365 Defender
- Microsoft Defender for Office 365

Tabellen `EmailAttachmentInfo` i det [avancerede jagtskema](advanced-hunting-overview.md) indeholder oplysninger om vedhæftede filer i mails, der behandles af Microsoft Defender for Office 365. Brug denne reference til at oprette forespørgsler, der returnerer oplysninger fra denne tabel.

Du kan finde oplysninger om andre tabeller i det avancerede jagtskema [i referencen til avanceret jagt](advanced-hunting-schema-tables.md).

> [!IMPORTANT]
> Nogle oplysninger er relateret til et forhåndsudgivet produkt, som kan blive ændret væsentligt, før det udgives kommercielt. Microsoft giver ingen garantier, udtrykkelige eller stiltiende, med hensyn til de oplysninger, der er angivet her.

| Kolonnenavn | Datatype | Beskrivelse |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Dato og klokkeslæt for registrering af hændelsen |
| `NetworkMessageId` | `string` | Entydigt id for mailen, der genereres af Microsoft 365 |
| `SenderFromAddress` | `string` | Afsendermailadresse i fra-headeren, som er synlig for mailmodtagere på deres mailklienter |
| `SenderDisplayName` | `string` | Navnet på den afsender, der vises i adressekartoteket, typisk en kombination af et givet eller fornavn, et mellemnavn og et efternavn eller efternavn |
| `SenderObjectId` | `string` | Entydigt id for afsenderens konto i Azure AD |
| `RecipientEmailAddress` | `string` | Mailadresse på modtageren eller mailadresse på modtageren efter udvidelse af distributionsliste |
| `RecipientObjectId` | `string` | Entydigt id for mailmodtageren i Azure AD |
| `FileName` | `string` | Navnet på den fil, som den registrerede handling blev anvendt på |
| `FileType` | `string` | Filtype |
| `SHA256` | `string` | SHA-256 for den fil, som den registrerede handling blev anvendt på. Dette felt udfyldes normalt ikke. Brug kolonnen SHA1, når det er tilgængeligt. |
| `ThreatTypes` | `string` | Dom fra mailfiltreringsstakken om, hvorvidt mailen indeholder malware, phishing eller andre trusler |
| `ThreatNames` | `string` | Registreringsnavn for malware eller andre trusler fundet |
| `DetectionMethods` | `string` | Metoder, der bruges til at registrere malware, phishing eller andre trusler, der findes i mailen |
| `ReportId` | `long` | Hændelses-id baseret på en gentaget tæller. Hvis du vil identificere entydige hændelser, skal denne kolonne bruges sammen med kolonnerne DeviceName og Timestamp. |
| `FileSize` | `string` | Filens størrelse i byte |

## <a name="related-topics"></a>Relaterede emner

- [Oversigt over avanceret jagt](advanced-hunting-overview.md)
- [Få mere at vide om forespørgselssproget](advanced-hunting-query-language.md)
- [Brug delte forespørgsler](advanced-hunting-shared-queries.md)
- [Lede på tværs af enheder, mails, apps og identiteter](advanced-hunting-query-emails-devices.md)
- [Forstå skemaet](advanced-hunting-schema-tables.md)
- [Anvend bedste praksis for forespørgsler](advanced-hunting-best-practices.md)
