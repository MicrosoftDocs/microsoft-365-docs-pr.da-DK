---
title: Sammenlign sikkerhedsfunktioner i Microsoft 365 planer for små og mellemstore virksomheder
description: Forstå forskellene mellem Defender for Business og Defender for Endpoint. Hvis du ved, hvad der er inkluderet i hver plan, kan det hjælpe dig med at træffe en informeret beslutning for din virksomhed.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: reference
ms.date: 03/15/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- m365-initiative-defender-business
- m365-security-compliance
ms.openlocfilehash: d7651e9ec4ec3cfbf3fe8e853b6de1de9e50dae1
ms.sourcegitcommit: 1c5f9d17a8b095cd88b23f4874539adc3ae021de
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/08/2022
ms.locfileid: "64714675"
---
# <a name="compare-microsoft-defender-for-business-to-microsoft-365-business-premium"></a>Sammenlign Microsoft Defender til virksomheder med Microsoft 365 Business Premium

> [!IMPORTANT]
> Microsoft Defender til virksomheder udrulles til [Microsoft 365 Business Premium](../../business-premium/index.md) kunder fra den 1. marts 2022. Defender for Business som et separat abonnement fås som prøveversion og udrulles gradvist til kunder og [it-partnere, der tilmelder sig her](https://aka.ms/mdb-preview) for at anmode om det. Prøveversionen indeholder et [indledende sæt scenarier](mdb-tutorials.md#try-these-preview-scenarios), og vi tilføjer jævnligt funktioner.
> 
> Nogle oplysninger i denne artikel er relateret til forhåndsudgivne produkter/tjenester, der kan blive ændret væsentligt, før de udgives kommercielt. Microsoft giver ingen garantier, udtrykkelige eller stiltiende, for de oplysninger, der er angivet her. 

Microsoft tilbyder en lang række cloudløsninger og -tjenester, herunder flere forskellige planer for små og mellemstore virksomheder. [Microsoft 365 Business Premium](../../business/microsoft-365-business-overview.md) omfatter f.eks. funktioner til administration af sikkerhed og enheder sammen med produktivitetsfunktioner, f.eks. Office apps. Denne artikel er udviklet til at hjælpe med at tydeliggøre, hvilke sikkerhedsfunktioner, f.eks. enhedsbeskyttelse, der er inkluderet i Microsoft 365 Business Premium, Microsoft Defender til virksomheder og Microsoft Defender for Endpoint.

Microsoft Defender til virksomheder er tilgængelig som et separat tilbud eller som en del af Microsoft 365 Business Premium (fra og med 1. marts 2022).

>
> **Har du et øjeblik?**
> Tag vores <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">korte undersøgelse om Microsoft Defender til virksomheder</a>. Vi vil meget gerne høre fra dig!
>

**Brug denne artikel til at**:

- [Sammenlign Microsoft Defender til virksomheder (separat) med Microsoft 365 Business Premium](#compare-security-features-in-microsoft-defender-for-business-to-microsoft-365-business-premium)
- [Sammenlign Defender for Business (separat) med Microsoft Defender for Endpoint virksomhedstilbud](#compare-microsoft-defender-for-business-to-microsoft-defender-for-endpoint-plans-1-and-2)

**Du behøver ikke at have et Microsoft 365 abonnement for at købe og bruge Microsoft Defender til virksomheder.** Microsoft Defender til virksomheder er inkluderet i Microsoft 365 Business Premium, og det er tilgængelig som en separat sikkerhedsløsning til små og mellemstore virksomheder. Hvis du allerede har Microsoft 365 Business Basic eller Standard, kan du overveje at føje enten opgradering til Microsoft 365 Business Premium eller tilføje Microsoft Defender til virksomheder for at få flere trusselsbeskyttelsesfunktioner. 

## <a name="compare-security-features-in-microsoft-defender-for-business-to-microsoft-365-business-premium"></a>Sammenlign sikkerhedsfunktioner i Microsoft Defender til virksomheder med Microsoft 365 Business Premium

> [!NOTE]
> Denne artikel er beregnet til at give et overordnet overblik over de trusselsbeskyttelsesfunktioner, der er inkluderet i Microsoft Defender til virksomheder (som en separat plan) og Microsoft 365 Business Premium (hvilket omfatter Defender for Business). Denne artikel er ikke beregnet til at fungere som en tjenestebeskrivelse eller et licenskontraktdokument. Du kan finde flere oplysninger [under Microsoft 365 licensvejledning til overholdelse af sikkerheds- &](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)

**Fra og med den 1. marts 2022 begynder Defender for Business at udrulle som en del af Microsoft 365 Business Premium. Defender for Business som et separat tilbud fås stadig som prøveversion.**

I følgende tabel sammenlignes sikkerhedsfunktioner og -egenskaber i Defender for Business (separat) med Microsoft 365 Business Premium. 

 <br/><br/>

| Funktion/funktionalitet | [Microsoft Defender for Business](mdb-overview.md)<br/>(separat, i øjeblikket i prøveversion) | [Microsoft 365 Business Premium](../../business/microsoft-365-business-overview.md)<br/>(omfatter Defender for Business) |
|:---|:---|:---|
| Mailbeskyttelse | Ja <br/>- [Mailscanning med Microsoft Defender Antivirus](../defender-endpoint/configure-advanced-scan-types-microsoft-defender-antivirus.md) | Ja <br/>- [Exchange Online Protection](../office-365-security/exchange-online-protection-overview.md) <br/>- [Mailscanning med Microsoft Defender Antivirus](../defender-endpoint/configure-advanced-scan-types-microsoft-defender-antivirus.md) |
| Antispambeskyttelse | Ja <br/>- Til enheder | Ja <br/>- Til enheder<br/>- Til Microsoft 365 mailindhold, f.eks. meddelelser og vedhæftede filer |
| Beskyttelse modmalware | Ja<br/>- Til enheder | Ja <br/>- Til enheder<br/>- Til Microsoft 365 mailindhold, f.eks. meddelelser og vedhæftede filer |
| [Næste generations beskyttelse](../defender-endpoint/microsoft-defender-antivirus-in-windows-10.md) <br/> (beskyttelse mod antivirus og antimalware) | Ja<br/>- Microsoft Defender Antivirus er medtaget i Windows 10 og nyere  | Ja <br/>- Microsoft Defender Antivirus er medtaget i Windows 10 og nyere<br/>- Næste generations beskyttelsespolitikker for onboardede enheder |
| [Reduktion af angrebsoverfladen](../defender-endpoint/overview-attack-surface-reduction.md) <br/>(ASR-regler i Windows 10 eller nyere og firewallbeskyttelse) | Ja  | Ja  |
| [Slutpunktsregistrering og -svar](../defender-endpoint/overview-endpoint-detection-response.md) <br/>(handlingsbaseret registrering og manuelle svarhandlinger) | Ja | Ja |
| [Automatiseret undersøgelse og svar](../defender-endpoint/automated-investigations.md) | Ja | Ja |
| [Håndtering af trusler og sikkerhedsrisici](../defender-endpoint/tvm-dashboard-insights.md) | Ja | Ja |
| Centraliseret administration og rapportering  | Ja  | Ja  |
| [Api'er](../defender-endpoint/apis-intro.md) <br/>(til integration med brugerdefinerede apps eller rapporteringsløsninger)  | Ja | Ja |


## <a name="compare-microsoft-defender-for-business-to-microsoft-defender-for-endpoint-plans-1-and-2"></a>Sammenlign Microsoft Defender til virksomheder med Microsoft Defender for Endpoint plan 1 og 2

Defender for Business giver små og mellemstore virksomheder professionelle funktioner i Defender for Endpoint. 

I følgende tabel sammenlignes sikkerhedsfunktioner og -egenskaber i Defender for Business med Microsoft Defender for Endpoint Plan 1 og 2. <br/><br/>

| Funktion/funktionalitet | [Defender for Business](mdb-overview.md)<br/>(separat, i øjeblikket i prøveversion) | [Defender for Endpoint Plan 1](../defender-endpoint/defender-endpoint-plan-1.md) | [Defender for Endpoint Plan 2](../defender-endpoint/microsoft-defender-endpoint.md) |
|:---|:---|:---|:---|
| [Centraliseret administration](../defender-endpoint/manage-atp-post-migration.md) <sup>[[1](#fn1)]</sup> | Ja | Ja | Ja |
| [Forenklet klientkonfiguration](mdb-simplified-configuration.md) | Ja | Nej | Nej |
| [Håndtering af trusler og sikkerhedsrisici](../defender-endpoint/next-gen-threat-and-vuln-mgt.md) | Ja | Nej | Ja |
| [Reduktion af angrebsoverflade](../defender-endpoint/overview-attack-surface-reduction.md) | Ja | Ja | Ja |
| [Næste generations beskyttelse](../defender-endpoint/next-generation-protection.md) | Ja | Ja | Ja |
| [Slutpunktsregistrering og -svar](../defender-endpoint/overview-endpoint-detection-response.md) | Ja <sup>[[2](#fn2)]</sup> | Nej | Ja |
| [Automatiseret undersøgelse og svar](../defender-endpoint/automated-investigations.md) | Ja <sup>[[2](#fn2)]</sup> | Nej | Ja |
| [Trusselsjagt](../defender-endpoint/advanced-hunting-overview.md) og seks måneders dataopbevaring | Nej | Nej | Ja |
| [Trusselsanalyse](../defender-endpoint/threat-analytics.md) | Ja <sup>[[2](#fn2)]</sup> | Nej | Ja |
| [Understøttelse på tværs af platforme](../defender-endpoint/minimum-requirements.md) <br/>(Windows, macOS, iOS og Android OS) | Ja <sup>[[3](#fn3)]</sup> | Ja | Ja |
| [Microsoft Threat Experts](../defender-endpoint/microsoft-threat-experts.md) | Nej | Nej | Ja |
| Partner-API'er | Ja | Ja | Ja |
| [integration af Microsoft 365 fyrtårn](../../lighthouse/m365-lighthouse-overview.md) <br/>(Til visning af sikkerhedshændelser på tværs af kundelejere) | Ja | Nej | Nej |

(<a id="fn1">1</a>) Onboard og administrer enheder på Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)) eller med et andet værktøj, f.eks. Microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)).

(<a id="fn2">2</a>) Disse funktioner er optimeret til små og mellemstore virksomheder.

(<a id="fn3">3</a>) I løbet af prøveversionsprogrammet understøttes Windows klientenheder på Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)).

## <a name="next-steps"></a>Næste trin

- [Se kravene til Microsoft Defender til virksomheder](mdb-requirements.md)
- [Hent Microsoft Defender til virksomheder](get-defender-business.md)
- [Få mere at vide om, hvordan du konfigurerer Microsoft Defender til virksomheder](mdb-setup-configuration.md) 
