---
title: Tabellen UrlClickEvents i det avancerede jagtskema
description: Få mere at vide om, hvordan du jagter phishingkampagner og mistænkelige klik ved hjælp af tabellen UrlClickEvents i det avancerede jagtskema.
keywords: avanceret jagt, trusselsjagt, cybertrusselsjagt, Microsoft 365 Defender, microsoft 365, m365, søgning, forespørgsel, telemetri, skemareference, kusto, tabel, kolonne, datatype, beskrivelse, UrlClickEvents, SafeLinks, phishing, malware, ondsindede klik, outlook, teams, mail, Office365
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
ms.openlocfilehash: bb7ee0397c79cc64c6f7396b6c3ca9450c8306f2
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/29/2022
ms.locfileid: "65130240"
---
# <a name="urlclickevents"></a>UrlClickEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender
- Microsoft Defender for Office 365


Tabellen `UrlClickEvents` i det avancerede jagtskema indeholder oplysninger om [klik på Pengeskab links](../office-365-security/safe-links.md) fra mails, Microsoft Teams og Office 365 apps i understøttede skrivebords-, mobil- og webapps. 

> [!IMPORTANT]
> Nogle oplysninger er relateret til et forhåndsudgivet produkt, som kan blive ændret væsentligt, før det udgives kommercielt. Microsoft giver ingen garantier, udtrykkelige eller stiltiende, med hensyn til de oplysninger, der er angivet her.

Du kan finde oplysninger om andre tabeller i det avancerede jagtskema [i referencen til avanceret jagt](advanced-hunting-schema-tables.md).

| Kolonnenavn | Datatype | Beskrivelse |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Den dato og det klokkeslæt, hvor brugeren klikkede på linket |
| `Url` | `string` | Den fulde URL-adresse, som brugeren har klikket på |
| `ActionType` | `string` | Angiver, om kliket blev tilladt eller blokeret af Pengeskab Links eller blokeret på grund af en lejerpolitik, f.eks. fra listen Over blokerede lejere|
| `AccountUpn` | `string` | Brugerens hovednavn på den konto, der klikkede på linket|
| `Workload` | `string` | Det program, som brugeren klikkede på linket fra, hvor værdierne er Mail, Office og Teams|
| `NetworkMessageId` | `string` | Det entydige id for den mail, der indeholder det klikkede link, genereret af Microsoft 365|
| `IPAddress` | `string` | Offentlig IP-adresse på den enhed, som brugeren har klikket på linket fra|
| `ThreatTypes` | `string` | Dom på tidspunktet for klik, der fortæller, om URL-adressen førte til malware, phish eller andre trusler|
| `DetectionMethods` | `string` | Registreringsteknologi, der blev brugt til at identificere truslen på tidspunktet for klik|
| `IsClickedThrough` | `bool` | Angiver, om brugeren kunne klikke sig igennem til den oprindelige URL-adresse eller ikke var tilladt|
| `UrlChain` | `string` | I forbindelse med scenarier, der involverer omdirigering, indeholder den URL-adresser, der findes i omdirigeringskæden|
| `ReportId` | `string` | Dette er det entydige id for en klikhændelse. Bemærk, at rapport-id'et ville have samme værdi i forbindelse med klikfrekvenssscenarier, og at det derfor skal bruges til at korrelere en klikhændelse.|

Du kan prøve denne eksempelforespørgsel, der bruger tabellen `UrlClickEvents` til at returnere en liste over links, hvor en bruger fik tilladelse til at fortsætte: 

```kusto
// Search for malicious links where user was allowed to proceed through
UrlClickEvents
| where ActionType == "ClickAllowed" or IsClickedThrough !="0"
| where ThreatTypes has "Phish"
| summarize by ReportId, IsClickedThrough, AccountUpn, NetworkMessageId, ThreatTypes, Timestamp
```

## <a name="related-topics"></a>Relaterede emner

- [Proaktiv jagt på trusler](advanced-hunting-overview.md)
- [Pengeskab Links i Microsoft Defender for Office 365](../office-365-security/safe-links.md)
- [Udfør handlinger på avancerede resultater af jagtforespørgslen](advanced-hunting-take-action.md)