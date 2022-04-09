---
title: Forstå afsnittet om analytikerrapport i trusselsanalyse i Microsoft 365 Defender
ms.reviewer: ''
description: Få mere at vide om afsnittet med analytikerrapporten i hver rapport til trusselsanalyse. Forstå, hvordan den indeholder oplysninger om trusler, afhjælpninger, registreringer, avancerede jagtforespørgsler m.m.
keywords: analytikerrapport, trusselsanalyse, opdagelser, avancerede jagtforespørgsler, afhjælpninger,
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: microsoft-365-enterprise
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
ms.collection:
- M365-security-compliance
ms.topic: article
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 396be53e4c238a8de21082f025762a1a4243b57c
ms.sourcegitcommit: dd7e5b67ff4ae4e7f74490e437c1795933c74cc7
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/08/2022
ms.locfileid: "64731136"
---
# <a name="understand-the-analyst-report-in-threat-analytics-in-microsoft-365-defender"></a>Forstå analytikerrapporten i trusselsanalyse i Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**

- Microsoft 365 Defender

[!INCLUDE [Prerelease](../includes/prerelease.md)]

Hver [rapport til trusselsanalyse](threat-analytics.md) indeholder dynamiske afsnit og et omfattende skrevet afsnit kaldet _analytikerrapporten_. Hvis du vil have adgang til dette afsnit, skal du åbne rapporten om den sporede trussel og vælge fanen **Analytikerrapport** .

:::image type="content" source="../../media/threat-analytics/ta_analystreport_mtp.png" alt-text="Afsnittet med analytikerrapporten i en rapport til trusselsanalyse" lightbox="../../media/threat-analytics/ta_analystreport_mtp.png":::

_Sektionen Analytikerrapport i en rapport med trusselsanalyse_

## <a name="scan-the-analyst-report"></a>Scan analytikerrapporten

Hvert afsnit i analytikerrapporten er designet til at levere handlingsrettede oplysninger. Selvom rapporter varierer, indeholder de fleste rapporter de afsnit, der er beskrevet i følgende tabel.

| Rapportsektion | Beskrivelse |
|--|--|
| Resumé | Oversigt over truslen, herunder hvornår den først blev set, dens motivationer, bemærkelsesværdige begivenheder, store mål og forskellige værktøjer og teknikker. Du kan bruge disse oplysninger til yderligere at vurdere, hvordan du prioriterer truslen i forhold til din branche, din geografiske placering og dit netværk. |
| Analyse | Tekniske oplysninger om truslerne, herunder oplysninger om et angreb, og hvordan angribere kan bruge en ny teknik eller angrebsoverflade |
| MITRE ATT-&observerede CK-teknikker | Hvordan observerede teknikker knyttes til [MITRE ATT&CK-angrebsstrukturen](https://attack.mitre.org/) |
| [Afhjælpninger](#apply-additional-mitigations) | Anbefalinger, der kan stoppe eller hjælpe med at reducere truslens indvirkning. Dette afsnit indeholder også afhjælpninger, der ikke spores dynamisk som en del af rapporten til trusselsanalyse. |
| [Oplysninger om registrering](#understand-how-each-threat-can-be-detected) | Specifikke og generiske registreringer, der leveres af Microsofts sikkerhedsløsninger, som kan vise aktivitet eller komponenter, der er knyttet til truslen. |
| [Avanceret jagt](#find-subtle-threat-artifacts-using-advanced-hunting) | [Avancerede jagtforespørgsler](advanced-hunting-overview.md) for proaktivt at identificere mulig trusselsaktivitet. De fleste forespørgsler leveres for at supplere registreringer, især for at finde potentielt skadelige komponenter eller funktionsmåder, der ikke dynamisk kan vurderes som skadelige. |
| Referencer | Microsoft- og tredjepartspublikationer, som analytikere refererer til under oprettelsen af rapporten. Trusselsanalyseindhold er baseret på data, der er valideret af Microsoft-forskere. Oplysninger fra offentligt tilgængelige tredjepartskilder identificeres tydeligt som sådanne. |
| Ændringslog | Det tidspunkt, hvor rapporten blev publiceret, og hvor der blev foretaget betydelige ændringer af rapporten. |

## <a name="apply-additional-mitigations"></a>Anvend yderligere afhjælpninger

Trusselsanalyser sporer dynamisk [status for sikkerhedsopdateringer og sikre konfigurationer](threat-analytics.md#exposure-and-mitigations-review-list-of-mitigations-and-the-status-of-your-devices). Disse oplysninger er tilgængelige som diagrammer og tabeller under fanen **Eksponering & afhjælpninger** .

Ud over disse sporede afhjælpninger diskuterer analytikerrapporten også afhjælpninger, der _ikke_ overvåges dynamisk. Her er nogle eksempler på vigtige afhjælpninger, der ikke spores dynamisk:

- Bloker mails med _vedhæftede filer i .lnk_ eller andre mistænkelige filtyper
- Randomiser adgangskoder til lokale administratorer
- Oplær slutbrugere i phishing-mail og andre trusselsvektorer
- Aktivér specifikke [regler for reduktion af angrebsoverfladen](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction)

Selvom du kan bruge fanen **Eksponering & afhjælpninger** til at vurdere din sikkerhedsholdning mod en trussel, kan du med disse anbefalinger tage yderligere skridt til at forbedre din sikkerhedsholdning. Læs omhyggeligt alle afhjælpningsvejledningerne i analytikerrapporten, og anvend dem, når det er muligt.

## <a name="understand-how-each-threat-can-be-detected"></a>Forstå, hvordan hver trussel kan registreres

Analytikerrapporten indeholder også registreringer fra funktioner i Microsoft Defender Antivirus og _slutpunktsregistrering og -svar_ (Slutpunktsregistrering og -svar).

### <a name="antivirus-detections"></a>Antivirusregistreringer

Disse registreringer er tilgængelige på enheder, [hvor Microsoft Defender Antivirus](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-in-windows-10) er slået til. Når disse registreringer forekommer på enheder, der er blevet onboardet til Microsoft Defender for Endpoint, udløser de også beskeder, der lyser diagrammerne i rapporten.

>[!NOTE]
>Analytikerrapporten viser også **generiske registreringer** , der kan identificere en lang række trusler ud over komponenter eller funktionsmåder, der er specifikke for den sporede trussel. Disse generiske registreringer afspejles ikke i diagrammerne.

### <a name="endpoint-detection-and-response-edr-alerts"></a>Beskeder om registrering af slutpunkter og svar (Slutpunktsregistrering og -svar)

Slutpunktsregistrering og -svar beskeder sendes for [enheder, der er onboardet i Microsoft Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/onboard-configure). Disse beskeder er generelt afhængige af sikkerhedssignaler, der indsamles af Microsoft Defender for Endpoint-sensoren og andre slutpunktsfunktioner – f.eks. antivirus, netværksbeskyttelse, manipulationsbeskyttelse – der fungerer som effektive signalkilder.

På samme måde som listen over antivirusregistreringer er nogle Slutpunktsregistrering og -svar beskeder designet til at markere mistænkelig adfærd, der muligvis ikke er knyttet til den sporede trussel. I sådanne tilfælde identificerer rapporten klart beskeden som "generisk", og at den ikke påvirker nogen af diagrammerne i rapporten.

### <a name="email-related-detections-and-mitigations"></a>Mailrelaterede registreringer og afhjælpninger

Mailrelaterede registreringer og afhjælpninger fra Microsoft Defender for Office 365 er inkluderet i analytikerrapporter ud over de slutpunktsdata, der allerede er tilgængelige fra Microsoft Defender for Endpoint.

Oplysninger om forhindrede mailforsøg giver dig indsigt i, om din organisation var et mål for den trussel, der blev tacklet i analytikerrapporten, selvom angrebet er blevet effektivt blokeret, før det blev leveret eller leveret til mappen med uønsket mail.

## <a name="find-subtle-threat-artifacts-using-advanced-hunting"></a>Find subtile trusselsartefakter ved hjælp af avanceret jagt

Selvom registreringer giver dig mulighed for at identificere og stoppe den sporede trussel automatisk, efterlader mange angrebsaktiviteter diskrete sporinger, der kræver yderligere inspektion. Nogle angrebsaktiviteter udviser adfærd, der også kan være normale, så detektering af dem dynamisk kan resultere i driftsstøj eller endda falske positiver.

[Avanceret jagt](advanced-hunting-overview.md) giver en forespørgselsgrænseflade, der er baseret på Kusto Query Language, som forenkler lokalisering af diskrete indikatorer for trusselsaktivitet. Det giver dig også mulighed for at vise kontekstafhængige oplysninger og kontrollere, om indikatorer er forbundet til en trussel.

Avancerede jagtforespørgsler i analytikerrapporterne er blevet undersøgt af Microsoft-analytikere og er klar til at køre i [editoren til avanceret jagtforespørgsel](https://security.microsoft.com/advanced-hunting). Du kan også bruge forespørgslerne til at oprette [brugerdefinerede registreringsregler](custom-detection-rules.md) , der udløser beskeder om fremtidige matches.

>[!NOTE]
> Trusselsanalyse er også tilgængelig i [Microsoft Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/threat-analytics). Den har dog ikke dataintegrationen mellem Microsoft Defender for Office og Microsoft Defender for Endpoint.

## <a name="related-topics"></a>Relaterede emner

- [Oversigt over Trusselsanalyse](threat-analytics.md)
- [Find proaktivt trusler med avanceret jagt](advanced-hunting-overview.md)
- [Regler for brugerdefineret registrering](custom-detection-rules.md)
