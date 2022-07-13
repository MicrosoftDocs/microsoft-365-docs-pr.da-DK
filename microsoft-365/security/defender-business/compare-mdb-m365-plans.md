---
title: Sammenlign sikkerhedsfunktioner i Microsoft 365-planer for små og mellemstore virksomheder
description: Hvordan er Defender for Business sammenlignet med Defender for Endpoint og Microsoft 365 Business Premium? Se, hvad der er inkluderet i de enkelte planer, så du kan træffe en mere informeret beslutning for din virksomhed.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: reference
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- m365-initiative-defender-business
- m365-security-compliance
ms.openlocfilehash: 9c3c4cf2914e268abeabc199e72ef28dac81a0f1
ms.sourcegitcommit: fa90763559239c4c46c5e848939126763879d8e4
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/13/2022
ms.locfileid: "66771990"
---
# <a name="compare-security-features-in-microsoft-365-plans-for-small-and-medium-sized-businesses"></a>Sammenlign sikkerhedsfunktioner i Microsoft 365-planer for små og mellemstore virksomheder

Microsoft tilbyder en lang række cloudløsninger og -tjenester, herunder planer for små og mellemstore virksomheder. [Microsoft 365 Business Premium](../../business/microsoft-365-business-overview.md) omfatter f.eks. funktioner til administration af sikkerhed og enhed sammen med produktivitetsfunktioner som f.eks. Office-apps. I denne artikel beskrives sikkerhedsfunktionerne i Microsoft 365 Business Premium, Microsoft Defender til virksomheder og [Microsoft Defender for Endpoint](../defender-endpoint/microsoft-defender-endpoint.md).


**Brug denne artikel til at**:

- [Sammenlign Defender for Business (separat) med Microsoft 365 Business Premium](#compare-security-features-in-microsoft-defender-for-business-to-microsoft-365-business-premium).
- [Sammenlign Defender for Business (separat) med Defender for Endpoint Enterprise-tilbud](#compare-microsoft-defender-for-business-to-microsoft-defender-for-endpoint-plans-1-and-2).

> [!TIP]
> Defender for Business fås som en separat sikkerhedsløsning til små og mellemstore virksomheder. Den er også inkluderet i Microsoft 365 Business Premium. Hvis du allerede har Microsoft 365 Business Basic eller Standard, kan du overveje enten at opgradere til Microsoft 365 Business Premium eller føje Defender for Business til dit abonnement for at få flere trusselsbeskyttelsesfunktioner til dine enheder.

## <a name="compare-security-features-in-microsoft-defender-for-business-to-microsoft-365-business-premium"></a>Sammenlign sikkerhedsfunktioner i Microsoft Defender til virksomheder med Microsoft 365 Business Premium

> [!NOTE]
> Denne artikel indeholder en overordnet oversigt over de trusselsbeskyttelsesfunktioner, der er inkluderet i Microsoft Defender til virksomheder (som en separat plan) og Microsoft 365 Business Premium (som omfatter Defender for Business). Det er ikke meningen, at det skal være en tjenestebeskrivelse eller et licenskontraktdokument. Du kan finde flere detaljerede oplysninger i [Microsoft 365-licensvejledning til sikkerhed & overholdelse af angivne standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

Defender for Business er også tilgængelig som et separat abonnement og er også inkluderet i Microsoft 365 Business Premium. I følgende tabel sammenlignes sikkerhedsfunktioner og -egenskaber i Defender for Business (separat) med Microsoft 365 Business Premium.

|Funktion/funktion|[Microsoft Defender for Business](mdb-overview.md)<br/>(separat)|[Microsoft 365 Business Premium](../../business/microsoft-365-business-overview.md)<br/>(omfatter Defender for Business)|
|---|---|---|
|Mailbeskyttelse|Ja <br/>[Mailscanning med Microsoft Defender Antivirus](../defender-endpoint/configure-advanced-scan-types-microsoft-defender-antivirus.md)|Ja <ul><li>[Exchange Online Protection](../office-365-security/exchange-online-protection-overview.md)</li><li>[Mailscanning med Microsoft Defender Antivirus](../defender-endpoint/configure-advanced-scan-types-microsoft-defender-antivirus.md)</li></ul>|
|Antispambeskyttelse|Ja<br/>Til enheder|Ja <ul><li>Til enheder</li><li>For Microsoft 365-mailindhold, f.eks. meddelelser og vedhæftede filer</li></ul>|
|Beskyttelse modmalware|Ja<br/>Til enheder|Ja<ul><li>Til enheder</li><li>For Microsoft 365-mailindhold, f.eks. meddelelser og vedhæftede filer</li></ul>|
|[Næste generations beskyttelse](../defender-endpoint/microsoft-defender-antivirus-in-windows-10.md) <br/> (beskyttelse mod antivirus og antimalware)|Ja<br/>Microsoft Defender Antivirus er inkluderet i Windows 10 og nyere|Ja <ul><li>Microsoft Defender Antivirus er inkluderet i Windows 10 og nyere</li><li>Næste generations beskyttelsespolitikker for onboardede enheder</li></ul>|
|[Reduktion af angrebsoverfladen](../defender-endpoint/overview-attack-surface-reduction.md) <br/>(ASR-regler i Windows 10 eller nyere og firewallbeskyttelse)|Ja|Ja|
|[Slutpunktsregistrering og -svar](../defender-endpoint/overview-endpoint-detection-response.md) <br/>(handlingsbaseret registrering og manuelle svarhandlinger)|Ja|Ja|
|[Automatiseret undersøgelse og svar](../defender-endpoint/automated-investigations.md)|Ja|Ja|
|[Håndtering af trusler og sikkerhedsrisici](../defender-endpoint/tvm-dashboard-insights.md)|Ja|Ja|
|Centraliseret administration og rapportering|Ja|Ja|
|[Api'er](../defender-endpoint/apis-intro.md) <br/>(til integration med brugerdefinerede apps eller rapporteringsløsninger)|Ja|Ja|

## <a name="compare-microsoft-defender-for-business-to-microsoft-defender-for-endpoint-plans-1-and-2"></a>Sammenlign Microsoft Defender til virksomheder med Microsoft Defender for Endpoint plan 1 og 2

Defender for Business giver små og mellemstore virksomheder de professionelle funktioner i Defender for Endpoint. I følgende tabel sammenlignes sikkerhedsfunktioner og -egenskaber i Defender for Business med virksomhedstilbud, Microsoft Defender for Endpoint Plan 1 og 2.

|Funktion/funktion|[Defender for Business](mdb-overview.md)<br/>(separat)|[Defender for Endpoint Plan 1](../defender-endpoint/defender-endpoint-plan-1.md)<br/>(til virksomhedskunder) |[Defender for Endpoint Plan 2](../defender-endpoint/microsoft-defender-endpoint.md)<br/>(til virksomhedskunder) |
|---|---|---|---|
|[Centraliseret administration](../defender-endpoint/manage-atp-post-migration.md) |Ja <sup>[[1](#fn1)]</sup>|Ja|Ja|
|[Forenklet klientkonfiguration](mdb-simplified-configuration.md)|Ja|Nej|Nej|
|[Håndtering af trusler og sikkerhedsrisici](../defender-endpoint/next-gen-threat-and-vuln-mgt.md)|Ja|Nej|Ja|
|[Reduktion af angrebsoverflade](../defender-endpoint/overview-attack-surface-reduction.md)|Ja|Ja|Ja|
|[Næste generations beskyttelse](../defender-endpoint/next-generation-protection.md)|Ja|Ja|Ja|
|[Slutpunktsregistrering og -svar](../defender-endpoint/overview-endpoint-detection-response.md)|Ja <sup>[[2](#fn2)]</sup>|Nej|Ja|
|[Automatiseret undersøgelse og svar](../defender-endpoint/automated-investigations.md)|Ja <sup>[[3](#fn3)]</sup>|Nej|Ja|
|[Trusselsjagt](../defender-endpoint/advanced-hunting-overview.md) og seks måneders dataopbevaring |Nej <sup>[[4](#fn4)]</sup>|Nej|Ja|
|[Trusselsanalyse](../defender-endpoint/threat-analytics.md)|Ja <sup>[[5](#fn5)]</sup>|Nej|Ja|
|[Understøttelse på tværs af platforme](../defender-endpoint/minimum-requirements.md) <br/>(Windows, Mac, iOS og Android OS)|Ja <sup>[[6](#fn6)]</sup>|Ja|Ja|
|[Microsoft Threat Experts](../defender-endpoint/microsoft-threat-experts.md)|Nej|Nej|Ja|
|Partner-API'er|Ja|Ja|Ja|
|[Integration af Microsoft 365 Lighthouse](../../lighthouse/m365-lighthouse-overview.md) <br/>(Til visning af sikkerhedshændelser på tværs af kundelejere)|Ja |Ja <sup>[[7](#fn7)]</sup>|Ja <sup>[[7](#fn7)]</sup>|

(<a id="fn1">1</a>) Onboarde og administrer enheder på Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)) eller ved hjælp af Microsoft Intune, der administreres i Microsoft Endpoint Manager Administration ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)).

(<a id="fn2">2</a>) EDR-funktioner (Endpoint Detection and Response) i Defender for Business omfatter funktionsmådebaseret registrering og følgende manuelle svarhandlinger: 
- Kør antivirusscanning
- Isoler enhed
- Stop og sæt en fil i karantæne
- Tilføj en indikator for at blokere eller tillade en fil

(<a id="fn3">3</a>) I Defender for Business er automatiseret undersøgelse og svar som standard slået til i hele lejeren. Hvis du slår automatiseret undersøgelse og svar fra, påvirker det beskyttelse i realtid. Se [Gennemse indstillinger for avancerede funktioner](mdb-configure-security-settings.md#review-settings-for-advanced-features).  

(<a id="fn4">4</a>) Der er ingen tidslinjevisning i Defender for Business.

(<a id="fn5">5</a>) I Defender for Business er trusselsanalyser optimeret til små og mellemstore virksomheder.

(<a id="fn6">6</a>) Se [Onboard enheder til Microsoft Defender til virksomheder](mdb-onboard-devices.md).

(<a id="fn7">7</a>) Muligheden for at få vist hændelser på tværs af lejere ved hjælp af Defender for Endpoint er ny!

## <a name="next-steps"></a>Næste trin

- [Se kravene til Microsoft Defender til virksomheder](mdb-requirements.md)
- [Hent Microsoft Defender til virksomheder](get-defender-business.md)
- [Få mere at vide om, hvordan du konfigurerer Microsoft Defender til virksomheder](mdb-setup-configuration.md)
