---
title: Tabellen EmailPostDeliveryEvents i det avancerede jagtskema
description: Få mere at vide om handlinger efter levering, der er Microsoft 365 mails i tabellen EmailPostDeliveryEvents i det avancerede jagtskema
keywords: avanceret jagt, trusselssøgning, cybertrusler på jagt, Microsoft 365 Defender, microsoft 365, m365, søg, forespørgsel, telemetri, skemareference, kusto, tabel, kolonne, datatype, beskrivelse, MailPostDeliveryEvents, netværksmeddelelses-id, afsender, modtager, vedhæftet fil-id, navn på vedhæftet fil, malwarekonstruation, phishingkontur, antal vedhæftede filer, antal links, URL-antal
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
ms.openlocfilehash: 59d611ae89aeedf386cd0dcad5939a9510f0820e
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/15/2021
ms.locfileid: "63591304"
---
# <a name="emailpostdeliveryevents"></a>EmailPostDeliveryEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender

Tabellen `EmailPostDeliveryEvents` i det avancerede [søgeskema](advanced-hunting-overview.md) indeholder oplysninger om handlinger efter levering, der er foretaget på mails, der behandles af Microsoft 365. Brug denne reference til at oprette forespørgsler, der returnerer oplysninger fra denne tabel.

>[!TIP]
> Du kan finde detaljerede oplysninger om de hændelsestyper (`ActionType` værdier), der understøttes af en tabel, ved at bruge den indbyggede skemareference, der er tilgængelig i Defender for Cloud.

Hvis du vil have mere at vide om individuelle mails, kan du også [`EmailEvents`](advanced-hunting-emailevents-table.md)bruge , [`EmailAttachmentInfo`](advanced-hunting-emailattachmentinfo-table.md)og tabellerne [`EmailUrlInfo`](advanced-hunting-emailurlinfo-table.md) . Du kan finde oplysninger om andre tabeller i det avancerede jagtskema i [den avancerede jagtreference](advanced-hunting-schema-tables.md).

> [!IMPORTANT]
> Nogle oplysninger relaterer til foreløbige produkter, som kan ændres væsentligt, før det frigives kommercielt. Microsoft påser ingen garantier, udtrykkelige eller underforståede, med hensyn til de oplysninger, du har angivet her.

| Kolonnenavn | Datatype | Beskrivelse |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Dato og klokkeslæt for, hvornår begivenheden blev optaget |
| `NetworkMessageId` | `string` | Entydigt id for den mail, der genereres af Microsoft 365 |
| `InternetMessageId` | `string` | Offentligt id for den mail, der er angivet af det afsendende mailsystem |
| `Action` | `string` | Handling, der er foretaget på enheden |
| `ActionType` | `string` | Aktivitetstype, der udløste begivenheden: Manuel afhjælpning, Phish ZAP, Malware ZAP |
| `ActionTrigger` | `string` | Angiver, om en handling blev udløst af en administrator (manuelt eller via godkendelse af en afventende automatiseret handling) eller ved en særlig mekanisme, f.eks. en ZAP eller dynamisk levering |
| `ActionResult` | `string` | Resultat af handlingen |
| `RecipientEmailAddress` | `string` | Mailadressen på modtageren eller modtagerens mailadresse efter udvidelse af distributionslisten |
| `DeliveryLocation` | `string` | Placering, hvor mailen blev leveret: Indbakke/mappe, Lokal/Ekstern, Uønsket, Karantæne, Mislykket, Tabt, Slettede elementer |
| `ReportId` | `long` | Hændelses-id baseret på en gentagende tæller. Denne kolonne skal bruges sammen med kolonnerne DeviceName og Timetamp til at identificere entydige hændelser. |
| `ThreatTypes` | `string` | Konklusion fra mailfiltreringsstakken for, om mailen indeholder malware, phishing eller andre trusler |
| `DetectionMethods` | `string` | Metoder til at detektere malware, phishing eller andre trusler, der findes i mailen |

## <a name="supported-event-types"></a>Understøttede hændelsestyper
Denne tabel registrerer hændelser med `ActionType` følgende værdier:

- **Manuel afhjælpning –** En administrator har handlet manuelt på en mail, efter den blev leveret til brugerpostkassen. Dette omfatter handlinger, der er foretaget manuelt [via Threat Explorer](../office-365-security/threat-explorer.md) eller [godkendelser af automatiserede handlinger til undersøgelse og svar (AIR](m365d-autoir-actions.md)).
- **Phish ZAP** – [Automatisk tømning i nul timer (ZAP) fandt](../office-365-security/zero-hour-auto-purge.md) sted på en phishing-mail efter levering.
- **Malware ZAP** – Automatisk tømning hver time (ZAP) tog skridtet mod en mail, der blev fundet med malware efter levering.

## <a name="related-topics"></a>Relaterede emner
- [Avanceret jagtoversigt](advanced-hunting-overview.md)
- [Lær forespørgselssproget](advanced-hunting-query-language.md)
- [Brug delte forespørgsler](advanced-hunting-shared-queries.md)
- [Lede på tværs af enheder, mails, apps og identiteter](advanced-hunting-query-emails-devices.md)
- [Forstå skemaet](advanced-hunting-schema-tables.md)
- [Anvend bedste fremgangsmåder for forespørgsler](advanced-hunting-best-practices.md)
