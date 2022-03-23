---
title: Forstå afsnittet for analytikerrapporten i trusselsanalyse i Microsoft 365 Defender
ms.reviewer: ''
description: Få mere at vide om sektionen med analytikerrapporten for hver trusselsanalyserapport. Forstå, hvordan den giver oplysninger om trusler, afhjælpninger, registreringer, avancerede forespørgselsforespørgsler og meget mere.
keywords: analytikerrapport, trusselsanalyse, registreringer, avancerede forespørgselsforespørgsler, afhjælpninger,
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
ms.openlocfilehash: e29ccfc963c0bfc2e730744a131a5c9485c72e42
ms.sourcegitcommit: 2697938d2d4fec523b501c5e7b0b8ec8f34e59b0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/12/2022
ms.locfileid: "63591883"
---
# <a name="understand-the-analyst-report-in-threat-analytics-in-microsoft-365-defender"></a>Forstå analytikerrapporten i trusselsanalyse i Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**

- Microsoft 365 Defender

> Vil du gerne Microsoft 365 Defender? Du kan [evaluere det i et labmiljø](m365d-evaluation.md?ocid=cx-docs-MTPtriallab) eller [køre dit pilotprojekt i produktion](m365d-pilot.md?ocid=cx-evalpilot).
>

[!INCLUDE [Prerelease](../includes/prerelease.md)]

Hver [trusselsanalyserapport](threat-analytics.md) indeholder dynamiske sektioner og en omfattende skriftlig sektion, der kaldes en _analytikerrapport_. For at få adgang til denne sektion skal du åbne rapporten om den registrerede trussel og vælge **fanen Analytikerrapport** .

![Billede af afsnittet analytikerrapport for en rapport om trusselsanalyse.](../../media/threat-analytics/ta_analystreport_mtp.png)

_Afsnittet Analytikerrapport i en trusselsanalyserapport_

## <a name="scan-the-analyst-report"></a>Scan analytikerrapporten

Hvert afsnit i analytikerrapporten er udviklet til at levere oplysninger, der kan handle på. Selvom rapporterne varierer, medtager de fleste rapporter sektionerne, der er beskrevet i følgende tabel.

| Rapportafsnit | Beskrivelse |
|--|--|
| Ledelsesresume | Oversigt over truslen, herunder hvornår den blev set første gang, dens motivation, væsentlige begivenheder, større mål og særskilte værktøjer og teknikker. Du kan bruge disse oplysninger til yderligere at vurdere, hvordan du prioriterer trussel i konteksten for din branche, geografiske placering og netværk. |
| Analyse | Tekniske oplysninger om truslerne, herunder oplysninger om et angreb, og hvordan hackere kan bruge en ny teknik eller angrebsoverflade |
| MITRE ATT&CK-teknikker, der er observeret | Sådan knyttes observerede teknikker [til MITRE ATT&CK-angrebsrammen](https://attack.mitre.org/) |
| [Afhjælpninger](#apply-additional-mitigations) | Anbefalinger, der kan stoppe eller hjælpe med at reducere effekten af truslen. Dette afsnit omfatter også afhjælpninger, der ikke registreres dynamisk som en del af rapporten om trusselsanalyse. |
| [Oplysninger om registrering](#understand-how-each-threat-can-be-detected) | Specifikke og generiske registreringer, der leveres af Microsoft-sikkerhedsløsninger, der kan surface-aktivitet eller komponenter, der er knyttet til truslen. |
| [Avanceret jagt](#find-subtle-threat-artifacts-using-advanced-hunting) | [Avancerede forespørgselsforespørgsler](advanced-hunting-overview.md) til proaktivt at identificere mulige trusselsaktivitet. De fleste forespørgsler leveres som supplement til registreringer, især med henblik på at finde potentielt skadelige komponenter eller funktionsmåder, der ikke dynamisk kan vurderes som skadelige. |
| Referencer | Microsoft- og tredjepartspublikationer, der refereres til af analytikere under oprettelsen af rapporten. Indhold af trusselsanalyse er baseret på data, der er valideret af Microsofts forsker. Oplysninger fra offentligt tilgængelige tredjepartskilder er tydeligt identificeret som sådanne. |
| Ændringslog | Det tidspunkt, hvor rapporten blev publiceret, og hvornår der blev foretaget væsentlige ændringer i rapporten. |

## <a name="apply-additional-mitigations"></a>Anvend yderligere afhjælpninger

Trusselsanalyse registrerer dynamisk [status for sikkerhedsopdateringer og sikre konfigurationer](threat-analytics.md#exposure-and-mitigations-review-list-of-mitigations-and-the-status-of-your-devices). Disse oplysninger er tilgængelige i diagrammer og tabeller under fanen **& eksponeringsreducerende** risici.

Ud over disse registrerede afhjælpninger diskuterer analytikerrapporten også afhjælpninger, der ikke _overvåges_ dynamisk. Her er nogle eksempler på vigtige afhjælpninger, der ikke registreres dynamisk:

- Bloker mails med _.lnk-vedhæftede_ filer eller andre mistænkelige filtyper
- Randomisere lokale administratoradgangskoder
- Underdan slutbrugere om phishing-mail og andre trusselsvektorer
- Slå specifikke regler for [reduktion af angrebsoverfladen til](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction)

Selvom du kan bruge fanen  eksponering &-afhjælpninger til at vurdere din sikkerhedsposition over for en trussel, giver disse anbefalinger dig yderligere trin til at forbedre din sikkerhedsmæssige eftertryk. Læs omhyggeligt alle afhjælpningsvejledningen i analytikerrapporten, og anvend dem, når det er muligt.

## <a name="understand-how-each-threat-can-be-detected"></a>Forstå, hvordan hver enkelt trussel kan findes

Analytikerrapporten leverer også registreringerne fra Microsoft Defender Antivirus _og slutpunktsregistrering og -svar_ (Slutpunktsregistrering og -svar)-funktioner.

### <a name="antivirus-detections"></a>Antivirusregistreringer

Disse registreringer er tilgængelige på enheder med [Microsoft Defender Antivirus](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-in-windows-10) er slået til. Når disse registreringer sker på enheder, der er blevet onboardet til Microsoft Defender til slutpunkt, udløser de også beskeder, der oplyser diagrammerne i rapporten.

>[!NOTE]
>Analytikerrapporten viser også **generiske** registreringer, der kan identificere en lang række trusler ud over komponenter eller funktionsmåder, der er specifikke for den registrerede trussel. Disse generiske registreringer afspejler ikke diagrammerne.

### <a name="endpoint-detection-and-response-edr-alerts"></a>Slutpunktsregistrering og svarbeskeder (Slutpunktsregistrering og -svar)

Slutpunktsregistrering og -svar hæves for enheder[, der er onboardet til Microsoft Defender til slutpunkt](/windows/security/threat-protection/microsoft-defender-atp/onboard-configure). Disse beskeder er generelt afhængige af sikkerhedssignaler, der indsamles af Microsoft Defender for Endpoint-sensoren og andre slutpunktsfunktioner , f.eks. antivirus, netværksbeskyttelse, tæmmebeskyttelse – der fungerer som effektive signalkilder.

Ligesom listen over antivirusregistreringer er nogle af disse Slutpunktsregistrering og -svar designet til generisk at markere mistænkelig adfærd, der muligvis ikke er knyttet til den registrerede trussel. I sådanne tilfælde identificerer rapporten beskeden tydeligt som "generisk", og at den ikke påvirker nogen af diagrammerne i rapporten.

### <a name="email-related-detections-and-mitigations"></a>Mailrelaterede registreringer og afhjælpninger

Mailrelaterede registreringer og afhjælpninger fra Microsoft Defender for Office 365 findes i analytikerrapporter ud over de slutpunktsdata, der allerede er tilgængelige fra Microsoft Defender til Slutpunkt.

Forhindrede mailforsøg giver dig indsigt i, om din organisation var et mål for truslerne i analytikerrapporten, selvom angrebene effektivt er blevet blokeret før levering eller leveret til mappen med uønsket mail.

## <a name="find-subtle-threat-artifacts-using-advanced-hunting"></a>Find diskrete trussels-artefakter ved hjælp af avanceret jagt

Selvom registreringer giver dig mulighed for at identificere og stoppe den registrerede trussel automatisk, efterlader mange angrebsaktiviteter diskrete sporinger, der kræver yderligere inspektion. Nogle angrebsaktiviteter udviser adfærd, som også kan være normal, så dynamisk registrering af dem kan resultere i driftsstøj eller endda falske positive.

[Avanceret jagt](advanced-hunting-overview.md) giver en forespørgselsgrænseflade, der er baseret på Kusto-forespørgselssprog, der forenkler lokalisering af diskrete indikatorer for trusselsaktivitet. Det giver dig også mulighed for at få vist kontekstafhængige oplysninger og kontrollere, om symboler er forbundet med en trussel.

Avancerede forespørgselsforespørgsler i analytikerrapporter er blevet undersøgt af Microsoft-analytikere og er klar til at blive kørt i avanceret [forespørgselseditor](https://security.microsoft.com/advanced-hunting). Du kan også bruge forespørgslerne til at oprette [brugerdefinerede registreringsregler,](custom-detection-rules.md) der udløser beskeder om fremtidige matches.

>[!NOTE]
> Trusselsanalyse er også tilgængelig [i Microsoft Defender til slutpunkt](/windows/security/threat-protection/microsoft-defender-atp/threat-analytics). Den har dog ikke dataintegrationen mellem Microsoft Defender for Office og Microsoft Defender til Slutpunkt, som Microsoft 365 Defender Threat Analytics har.

## <a name="related-topics"></a>Relaterede emner

- [Oversigt over Trusselsanalyse](threat-analytics.md)
- [Find proaktivt trusler med avanceret jagt](advanced-hunting-overview.md)
- [Brugerdefinerede registreringsregler](custom-detection-rules.md)
