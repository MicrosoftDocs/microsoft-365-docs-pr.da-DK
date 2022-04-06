---
title: Forstå afsnittet for analytikerrapporten i Trusselsanalyse.
ms.reviewer: ''
description: Hvordan rapportafsnittet i trusselsanalyserapporter indeholder oplysninger om trusler, afhjælpning, registreringer, avancerede forespørgselssøgninger og meget mere.
keywords: analytikerrapport, trusselsanalyse, registreringer, avancerede forespørgselsforespørgsler, afhjælpninger,
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 337f9a94b651adffc7360cb88b3d68c9c8167c0a
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64468099"
---
# <a name="the-analyst-report-in-threat-analytics"></a>Analytikerrapporten i trusselsanalyse

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du gerne Microsoft Defender for Endpoint? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Hver [trusselsanalyserapport](threat-analytics.md) indeholder dynamiske sektioner og en omfattende skriftlig sektion, der kaldes en _analytikerrapport_. For at få adgang til denne sektion skal du åbne rapporten om den registrerede trussel og vælge **fanen Analytikerrapport** .

:::image type="content" source="images/ta-analyst-report-small.png" alt-text="Afsnittet for analytikerrapporten i en trusselsanalyserapport" lightbox="images/ta-analyst-report-small.png":::

_Afsnittet Analytikerrapport i en trusselsanalyserapport_

## <a name="scan-the-analyst-report"></a>Scan analytikerrapporten

Hvert afsnit i analytikerrapporten er udviklet til at levere oplysninger, der kan handle på. Selvom rapporterne varierer, medtager de fleste rapporter sektionerne, der er beskrevet i følgende tabel.

<br>

****

|Rapportafsnit|Beskrivelse|
|---|---|
|Ledelsesresume|Oversigt over truslen, herunder hvornår den blev set første gang, dens motivation, væsentlige begivenheder, større mål og særskilte værktøjer og teknikker. Du kan bruge disse oplysninger til yderligere at vurdere, hvordan du prioriterer trussel i konteksten for din branche, geografiske placering og netværk.|
|Analyse|Tekniske oplysninger om truslerne, herunder oplysninger om et angreb, og hvordan hackere kan bruge en ny teknik eller angrebsoverflade|
|MITRE ATT&CK-teknikker, der er observeret|Sådan knyttes observerede teknikker [til MITRE ATT&CK-angrebsrammen](https://attack.mitre.org/)|
|[Afhjælpninger](#apply-additional-mitigations)|Anbefalinger, der kan stoppe eller hjælpe med at reducere effekten af truslen. Dette afsnit omfatter også afhjælpninger, der ikke registreres dynamisk som en del af rapporten om trusselsanalyse.|
|[Oplysninger om registrering](#understand-how-each-threat-can-be-detected)|Specifikke og generiske registreringer, der leveres af Microsoft-sikkerhedsløsninger, der kan surface-aktivitet eller komponenter, der er knyttet til truslen.|
|[Avanceret jagt](#find-subtle-threat-artifacts-using-advanced-hunting)|[Avancerede forespørgselsforespørgsler](advanced-hunting-overview.md) til proaktivt at identificere mulige trusselsaktivitet. De fleste forespørgsler leveres som supplement til registreringer, især med henblik på at finde potentielt skadelige komponenter eller funktionsmåder, der ikke dynamisk kan vurderes som skadelige.|
|Referencer|Microsoft- og tredjepartspublikationer, der refereres til af analytikere under oprettelsen af rapporten. Indhold af trusselsanalyse er baseret på data, der er valideret af Microsofts forsker. Oplysninger fra offentligt tilgængelige tredjepartskilder er tydeligt identificeret som sådanne.|
|Ændringslog|Det tidspunkt, hvor rapporten blev publiceret, og hvornår der blev foretaget væsentlige ændringer i rapporten.|
|

## <a name="apply-additional-mitigations"></a>Anvend yderligere afhjælpninger

Trusselsanalyse registrerer dynamisk [status for sikkerhedsopdateringer og sikre konfigurationer](threat-analytics.md#mitigations-review-list-of-mitigations-and-the-status-of-your-devices). Disse oplysninger er tilgængelige som diagrammer og tabeller på **fanen Afhjælpninger** .

Ud over disse registrerede afhjælpninger diskuterer analytikerrapporten også afhjælpninger, der ikke _overvåges_ dynamisk. Her er nogle eksempler på vigtige afhjælpninger, der ikke registreres dynamisk:

- Bloker mails med _.lnk-vedhæftede_ filer eller andre mistænkelige filtyper
- Randomisere lokale administratoradgangskoder
- Underdan slutbrugere om phishing-mail og andre trusselsvektorer
- Slå specifikke regler for [reduktion af angrebsoverfladen til](attack-surface-reduction.md)

Selvom du kan bruge fanen **Afhjælpninger** til at vurdere din sikkerhed mod en trussel, giver disse anbefalinger dig yderligere skridt i retning af at forbedre din sikkerhed. Læs omhyggeligt alle afhjælpningsvejledningen i analytikerrapporten, og anvend dem, når det er muligt.

## <a name="understand-how-each-threat-can-be-detected"></a>Forstå, hvordan hver enkelt trussel kan findes

Analytikerrapporten leverer også registreringerne fra Microsoft Defender Antivirus _og slutpunktsregistrering og -svar_ (Slutpunktsregistrering og -svar)-funktioner.

### <a name="antivirus-detections"></a>Antivirusregistreringer

Disse registreringer er tilgængelige på enheder med [Microsoft Defender Antivirus](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-in-windows-10) er slået til. Når disse registreringer sker på enheder, der er blevet onboardet til Microsoft Defender for Endpoint, udløser de også beskeder, der oplyser diagrammerne i rapporten.

> [!NOTE]
> Analytikerrapporten viser også **generiske** registreringer, der kan identificere en lang række trusler ud over komponenter eller funktionsmåder, der er specifikke for den registrerede trussel. Disse generiske registreringer afspejler ikke diagrammerne.

### <a name="endpoint-detection-and-response-edr-alerts"></a>Slutpunktsregistrering og svarbeskeder (Slutpunktsregistrering og -svar)

Slutpunktsregistrering og -svar hæves for enheder [onboardet til Microsoft Defender for Endpoint](onboard-configure.md). Disse beskeder er generelt afhængige af sikkerhedssignaler, der indsamles af Microsoft Defender for Endpoint-sensoren og andre slutpunktsfunktioner (f.eks. antivirus, netværksbeskyttelse, tæmmebeskyttelse), der fungerer som effektive signalkilder.

Ligesom listen over antivirusregistreringer er nogle af disse Slutpunktsregistrering og -svar designet til generisk at markere mistænkelig adfærd, der muligvis ikke er knyttet til den registrerede trussel. I sådanne tilfælde identificerer rapporten beskeden tydeligt som "generisk", og at den ikke påvirker nogen af diagrammerne i rapporten.

## <a name="find-subtle-threat-artifacts-using-advanced-hunting"></a>Find diskrete trussels-artefakter ved hjælp af avanceret jagt

Selvom registreringer giver dig mulighed for at identificere og stoppe den registrerede trussel automatisk, efterlader mange angrebsaktiviteter diskrete sporinger, der kræver yderligere inspektion. Nogle angrebsaktiviteter udviser adfærd, som også kan være normal, så dynamisk registrering af dem kan resultere i driftsstøj eller endda falske positive.

[Avanceret jagt](advanced-hunting-overview.md) giver en forespørgselsgrænseflade, der er baseret på Kusto-forespørgselssprog, der forenkler lokalisering af diskrete indikatorer for trusselsaktivitet. Det giver dig også mulighed for at få vist kontekstafhængige oplysninger og kontrollere, om symboler er forbundet med en trussel.

Avancerede forespørgselsforespørgsler i analytikerrapporter er blevet undersøgt af Microsoft-analytikere og er klar til at blive kørt i avanceret [forespørgselseditor](https://security.microsoft.com/advanced-hunting). Du kan også bruge forespørgslerne til at oprette [brugerdefinerede registreringsregler,](custom-detection-rules.md) der udløser beskeder om fremtidige matches.

## <a name="related-topics"></a>Relaterede emner

- [Oversigt over Trusselsanalyse](threat-analytics.md)
- [Find proaktivt trusler med avanceret jagt](advanced-hunting-overview.md)
- [Brugerdefinerede registreringsregler](custom-detection-rules.md)
