---
title: Tabellen EmailPostDeliveryEvents i det avancerede jagtskema
description: Få mere at vide om handlinger efter levering, der udføres på Microsoft 365 mails i tabellen EmailPostDeliveryEvents i det avancerede jagtskema
keywords: avanceret jagt, trusselsjagt, cybertrusselsjagt, Microsoft 365 Defender, microsoft 365, m365, søgning, forespørgsel, telemetri, skemareference, kusto, tabel, kolonne, datatype, beskrivelse, EmailPostDeliveryEvents, netværksmeddelelses-id, afsender, modtager, vedhæftet id, navn på vedhæftet fil, malware-dom, phishing-dom, antal vedhæftede filer, antal links, URL-adresse
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
ms.openlocfilehash: 876b240d73613637cc2f564ce6415873b645293c
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/29/2022
ms.locfileid: "65130577"
---
# <a name="emailpostdeliveryevents"></a>EmailPostDeliveryEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender
- Microsoft Defender for Office 365

Tabellen `EmailPostDeliveryEvents` i det [avancerede jagtskema](advanced-hunting-overview.md) indeholder oplysninger om handlinger efter levering, der udføres på mails, der behandles af Microsoft 365. Brug denne reference til at oprette forespørgsler, der returnerer oplysninger fra denne tabel.

>[!TIP]
> Du kan finde detaljerede oplysninger om de hændelsestyper (`ActionType` værdier), der understøttes af en tabel, ved at bruge den indbyggede skemareference, der er tilgængelig i Defender for Cloud.

Hvis du vil have flere oplysninger om individuelle mails, kan du også bruge tabellerne [`EmailEvents`](advanced-hunting-emailevents-table.md)[`EmailUrlInfo`](advanced-hunting-emailurlinfo-table.md) , [`EmailAttachmentInfo`](advanced-hunting-emailattachmentinfo-table.md)og . Du kan finde oplysninger om andre tabeller i det avancerede jagtskema [i referencen til avanceret jagt](advanced-hunting-schema-tables.md).

> [!IMPORTANT]
> Nogle oplysninger er relateret til et forhåndsudgivet produkt, som kan blive ændret væsentligt, før det udgives kommercielt. Microsoft giver ingen garantier, udtrykkelige eller stiltiende, med hensyn til de oplysninger, der er angivet her.

| Kolonnenavn | Datatype | Beskrivelse |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Dato og klokkeslæt for registrering af hændelsen |
| `NetworkMessageId` | `string` | Entydigt id for mailen, der genereres af Microsoft 365 |
| `InternetMessageId` | `string` | Offentlig identifikator for den mail, der er angivet af det sendende mailsystem |
| `Action` | `string` | Handling, der udføres på enheden |
| `ActionType` | `string` | Aktivitetstype, der udløste hændelsen: Manuel afhjælpning, Phish ZAP, Malware ZAP |
| `ActionTrigger` | `string` | Angiver, om en handling blev udløst af en administrator (manuelt eller via godkendelse af en ventende automatisk handling) eller af en særlig mekanisme, f.eks. en ZAP eller Dynamisk levering |
| `ActionResult` | `string` | Resultat af handlingen |
| `RecipientEmailAddress` | `string` | Mailadresse på modtageren eller mailadresse på modtageren efter udvidelse af distributionsliste |
| `DeliveryLocation` | `string` | Placering, hvor mailen blev leveret: Indbakke/Mappe, Lokalt/Eksternt, Uønsket, Karantæne, Mislykket, Mistet, Slettede elementer |
| `ReportId` | `long` | Hændelses-id baseret på en gentaget tæller. Hvis du vil identificere entydige hændelser, skal denne kolonne bruges sammen med kolonnerne DeviceName og Timestamp. |
| `ThreatTypes` | `string` | Dom fra mailfiltreringsstakken om, hvorvidt mailen indeholder malware, phishing eller andre trusler |
| `DetectionMethods` | `string` | Metoder, der bruges til at registrere malware, phishing eller andre trusler, der findes i mailen |

## <a name="supported-event-types"></a>Understøttede hændelsestyper
I denne tabel registreres hændelser med følgende `ActionType` værdier:

- **Manuel afhjælpning** – En administrator har manuelt udført en handling på en mail, efter at den blev leveret til brugerpostkassen. Dette omfatter handlinger, der udføres manuelt via [Threat Explorer](../office-365-security/threat-explorer.md) eller godkendelser af [air-handlinger (automated investigation and response).](m365d-autoir-actions.md)
- **Phish ZAP** – [ZAP (auto-purge) på nul timer](../office-365-security/zero-hour-auto-purge.md) tog handling på en phishing-mail efter levering.
- **Malware ZAP** - Nul-timers automatisk tømning (ZAP) tog handling på en mail fundet indeholder malware efter levering.

## <a name="related-topics"></a>Relaterede emner
- [Oversigt over avanceret jagt](advanced-hunting-overview.md)
- [Få mere at vide om forespørgselssproget](advanced-hunting-query-language.md)
- [Brug delte forespørgsler](advanced-hunting-shared-queries.md)
- [Lede på tværs af enheder, mails, apps og identiteter](advanced-hunting-query-emails-devices.md)
- [Forstå skemaet](advanced-hunting-schema-tables.md)
- [Anvend bedste praksis for forespørgsler](advanced-hunting-best-practices.md)
