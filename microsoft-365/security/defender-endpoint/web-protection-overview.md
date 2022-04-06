---
title: Webbeskyttelse
description: Få mere at vide om webbeskyttelse i Microsoft Defender for Endpoint, og hvordan den kan beskytte din organisation
keywords: webbeskyttelse, webtrusselsbeskyttelse, webbrowsing, sikkerhed, phishing, malware, udnyttelse, websteder, netværksbeskyttelse, Edge, Internet Explorer, Chrome, Firefox, webbrowser, skadelige websteder
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 4184948316e683a59b45b9397aaea74260e290ee
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/06/2022
ms.locfileid: "64664166"
---
# <a name="web-protection"></a>Webbeskyttelse

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Vil du opleve Microsoft Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-main-abovefoldlink&rtc=1)


## <a name="about-web-protection"></a>Om webbeskyttelse

Webbeskyttelse i Microsoft Defender for Endpoint består af [webtrusselbeskyttelse](web-threat-protection.md), [filtrering af webindhold](web-content-filtering.md) og [brugerdefinerede indikatorer](manage-indicators.md). Med webbeskyttelse kan du beskytte dine enheder mod webtrusler og hjælpe dig med at regulere uønsket indhold. Du kan finde webbeskyttelsesrapporter på Microsoft 365 Defender-portalen ved at gå til **Rapporter > Webbeskyttelse**.

:::image type="content" source="images/web-protection.png" alt-text="Webbeskyttelseskortene" lightbox="images/web-protection.png":::

### <a name="web-threat-protection"></a>Beskyttelse mod webtrusler

De kort, der udgør webtrusselbeskyttelse, er **webtrusselsregistreringer over tid** og **webtrusseloversigt**.

Beskyttelse af webtrusler omfatter:

- Omfattende synlighed af webtrusler, der påvirker din organisation.
- Undersøgelsesfunktioner via webrelateret trusselsaktivitet via beskeder og omfattende profiler af URL-adresser og de enheder, der har adgang til disse URL-adresser.
- Et komplet sæt sikkerhedsfunktioner, der sporer generelle adgangstendenser til skadelige og uønskede websteder.

Du kan få flere oplysninger under [Beskyttelse mod webtrusler](web-threat-protection.md).

### <a name="custom-indicators"></a>Brugerdefinerede indikatorer

Brugerdefinerede indikatorregistreringer opsummeres også i dine organisationers webtrusselrapporter under **webtrusselsregistreringer over tid** og **oversigt over webtrusler**.

Brugerdefineret indikator indeholder:

- Mulighed for at oprette IP- og URL-baserede indikatorer for kompromis for at beskytte din organisation mod trusler.
- Undersøgelsesfunktioner i forbindelse med aktiviteter, der er relateret til dine brugerdefinerede IP/URL-profiler og de enheder, der har adgang til disse URL-adresser.
- Muligheden for at oprette politikker for Tillad, Bloker og Advar for IP-adresser og URL-adresser.

Du kan få flere oplysninger under [Opret indikatorer for IP-adresser og URL-adresser/domæner](indicator-ip-domain.md)

### <a name="web-content-filtering"></a>Filtrering af webindhold

Filtrering af webindhold omfatter **webaktivitet efter kategori**, **oversigt over filtrering af webindhold** og **webaktivitetsoversigt**.

Filtrering af webindhold omfatter:

- Brugerne forhindres i at få adgang til websteder i blokerede kategorier, uanset om de søger i det lokale miljø eller væk fra dem.
- Du kan nemt udrulle forskellige politikker til forskellige brugersæt ved hjælp af de enhedsgrupper, der er defineret i [Microsoft Defender for Endpoint rollebaserede indstillinger for adgangskontrol](/microsoft-365/security/defender-endpoint/rbac).
- Du kan få adgang til webrapporter på den samme centrale placering med synlighed over faktiske blokke og webforbrug.

Du kan få flere oplysninger under [Filtrering af webindhold](web-content-filtering.md).

## <a name="order-of-precedence"></a>Rangorden

Webbeskyttelse består af følgende komponenter, der er angivet i prioriteret rækkefølge. Hver af disse komponenter gennemtvinges af SmartScreen-klienten i Microsoft Edge og af Network Protection-klienten i alle andre browsere og processer.

- Brugerdefinerede indikatorer (IP/URL, Microsoft Defender for Cloud Apps politikker)
  - Tillade
  - Advare
  - Bloker

- Webtrusler (malware, phish)
  - SmartScreen Intel, herunder Exchange Online Protection (EOP)
  - Eskaleringer

- WCF (Web Content Filtering)

> [!NOTE]
> Microsoft Defender for Cloud Apps genererer i øjeblikket kun indikatorer for blokerede URL-adresser.

Rækkefølgen er relateret til den rækkefølge af handlinger, som en URL-adresse eller IP-adresse evalueres efter. Hvis du f.eks. har en politik til filtrering af webindhold, kan du oprette udeladelser via brugerdefinerede IP/URL-indikatorer. Brugerdefinerede indikatorer for kompromis (IoC) har højere prioritetsrækkefølge end WCF-blokke.

På samme måde kan tillad under en konflikt mellem indikatorer altid have forrang over blokke (tilsidesættelseslogik). Det betyder, at en tilladelsesindikator vinder over en hvilken som helst blokindikator, der findes.

I nedenstående tabel opsummeres nogle almindelige konfigurationer, der ville give konflikter i webbeskyttelsesstakken. Den identificerer også de resulterende beslutninger baseret på den rangplacering, der er angivet ovenfor.

<br>

****

|Brugerdefineret indikatorpolitik|Webtrusselpolitik|WCF-politik|Politik for Defender for Cloud Apps|Resultat|
|---|---|---|---|---|
|Tillade|Bloker|Bloker|Bloker|Tillad (tilsidesættelse af webbeskyttelse)|
|Tillade|Tillade|Bloker|Bloker|Tillad (WCF-undtagelse)|
|Advare|Bloker|Bloker|Bloker|Advar (tilsidesæt)|
|

Interne IP-adresser understøttes ikke af brugerdefinerede indikatorer. Hvis en advarselspolitik tilsidesættes af slutbrugeren, fjernes blokeringen af webstedet som standard i 24 timer for den pågældende bruger. Denne tidsramme kan ændres af administratoren og overføres af SmartScreen-cloudtjenesten. Muligheden for at omgå en advarsel kan også deaktiveres i Microsoft Edge ved hjælp af CSP til webtrusselblokke (malware/phishing). Du kan få flere oplysninger [under Microsoft Edge SmartScreen-Indstillinger](/DeployEdge/microsoft-edge-policies#smartscreen-settings-policies).

## <a name="protect-browsers"></a>Beskyt browsere

I alle webbeskyttelsesscenarier kan SmartScreen og Network Protection bruges sammen for at sikre beskyttelse på tværs af både første- og tredjepartsbrowsere og -processer. SmartScreen er indbygget direkte i Microsoft Edge, mens Network Protection overvåger trafik i tredjepartsbrowsere og -processer. Nedenstående diagram illustrerer dette koncept. Dette diagram over de to klienter, der arbejder sammen om at levere flere browser-/app-dækninger, er nøjagtigt for alle funktioner i Web Protection (indikatorer, webtrusler, indholdsfiltrering).

:::image type="content" source="../../media/web-protection-protect-browsers.png" alt-text="Brugen af smartScreen og Network Protection sammen" lightbox="../../media/web-protection-protect-browsers.png":::

## <a name="troubleshoot-endpoint-blocks"></a>Foretag fejlfinding af slutpunktblokke

Svar fra SmartScreen-clouden standardiseres. Værktøjer som Fiddler kan bruges til at inspicere svaret fra cloudtjenesten, hvilket hjælper med at bestemme kilden til blokken.

Når SmartScreen-cloudtjenesten svarer med et tillad, bloker eller advar-svar, videresendes en svarkategori og serverkontekst til klienten. I Microsoft Edge er svarkategorien den, der bruges til at bestemme den relevante blokside, der skal vises (ondsindet, phishing, organisationspolitik).

I nedenstående tabel vises svarene og deres korrelerede funktioner.

<br>

****

|Svarkategori|Funktion, der er ansvarlig for blokken|
|---|---|
|Brugerdefineret politik|WCF|
|CustomBlockList|Brugerdefinerede indikatorer|
|CasbPolicy|Defender for Cloud Apps|
|Skadelig|Webtrusler|
|Phishing|Webtrusler|
|||

## <a name="advanced-hunting-for-web-protection"></a>Avanceret søgning efter webbeskyttelse

Kusto-forespørgsler i avanceret jagt kan bruges til at opsummere webbeskyttelsesblokke i din organisation i op til 30 dage. Disse forespørgsler bruger de oplysninger, der er angivet ovenfor, til at skelne mellem de forskellige kilder til blokke og opsummere dem på en brugervenlig måde. Forespørgslen nedenfor viser f.eks. alle WCF-blokke, der stammer fra Microsoft Edge.

```kusto
DeviceEvents
| where ActionType == "SmartScreenUrlWarning"
| extend ParsedFields=parse_json(AdditionalFields)
| project DeviceName, ActionType, Timestamp, RemoteUrl, InitiatingProcessFileName, Experience=tostring(ParsedFields.Experience)
| where Experience == "CustomBlockList"
```

På samme måde kan du bruge forespørgslen nedenfor til at få vist alle WCF-blokke, der stammer fra Network Protection (f.eks. en WCF-blok i en tredjepartsbrowser). Bemærk, at ActionType er blevet opdateret, og 'Experience' er blevet ændret til 'ResponseCategory'.

```kusto
DeviceEvents
| where ActionType == "ExploitGuardNetworkProtectionBlocked"
| extend ParsedFields=parse_json(AdditionalFields)
| project DeviceName, ActionType, Timestamp, RemoteUrl, InitiatingProcessFileName, ResponseCategory=tostring(ParsedFields.ResponseCategory)
| where ResponseCategory == "CustomPolicy"
```

Hvis du vil have vist blokke, der skyldes andre funktioner (f.eks. brugerdefinerede indikatorer), skal du se tabellen ovenfor, der beskriver hver funktion og deres respektive svarkategori. Disse forespørgsler kan også ændres for at søge efter telemetri, der er relateret til bestemte maskiner i din organisation. Bemærk, at den ActionType, der vises i hver forespørgsel ovenfor, kun viser de forbindelser, der blev blokeret af en webbeskyttelsesfunktion, og ikke al netværkstrafik.

## <a name="user-experience"></a>Brugeroplevelse

Hvis en bruger besøger en webside, der udgør en risiko for malware, phishing eller andre webtrusler, udløser Microsoft Edge en blokside, der læser 'Dette websted er blevet rapporteret som usikkert' sammen med oplysninger relateret til truslen.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/web-protection-malicious-block.png" alt-text="Siden er blokeret af Microsoft Edge" lightbox="../../media/web-protection-malicious-block.png":::

Hvis den er blokeret af WCF eller en brugerdefineret indikator, vises der en blokside i Microsoft Edge, der fortæller brugeren, at webstedet er blokeret af vedkommendes organisation.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/web-protection-indicator-blockpage.png" alt-text="Den side, der er blokeret af din organisation" lightbox="../../media/web-protection-indicator-blockpage.png":::

Under alle omstændigheder vises der ingen bloksider i tredjepartsbrowsere, og brugeren får vist siden "Sikker forbindelse mislykkedes" sammen med en toastmeddelelse. Afhængigt af den politik, der er ansvarlig for blokken, får en bruger vist en anden meddelelse i toastmeddelelsen. Filtrering af webindhold viser f.eks. meddelelsen "Dette indhold er blokeret".

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/web-protection-np-block.png" alt-text="Siden er blokeret af WCF" lightbox="../../media/web-protection-np-block.png":::

## <a name="report-false-positives"></a>Rapportér falske positiver

Hvis du vil rapportere et falsk positivt for websteder, der er blevet betragtet som farlige af SmartScreen, skal du bruge det link, der vises på bloksiden i Microsoft Edge (som vist ovenfor).

For WCF kan du bestride kategorien for et domæne. Gå til fanen **Domæner** i WCF-rapporterne, og klik derefter på **Fejl i rapport**. Der åbnes et pop op-vindue. Angiv prioriteten for hændelsen, og angiv nogle yderligere oplysninger, f.eks. den foreslåede kategori. Du kan få flere oplysninger om, hvordan du slår WCF til, og hvordan du bestrider kategorier, under [Filtrering af webindhold](web-content-filtering.md).

Du kan finde flere oplysninger om, hvordan du indsender falske positiver/negativer, [i Adresse falske positive/negative i Microsoft Defender for Endpoint](defender-endpoint-false-positives-negatives.md).

## <a name="related-information"></a>Relaterede oplysninger

<br>

****

|Emne|Beskrivelse|
|---|---|
|[Beskyttelse mod webtrusler](web-threat-protection.md) | Stop adgangen til phishing-websteder, malwarevektorer, udnyttelseswebsteder, websteder, der ikke er tillid til, eller websteder med lavt omdømme og websteder, som du har blokeret.|
|[Filtrering af webindhold](web-content-filtering.md) | Spor og regulerer adgangen til websteder baseret på deres indholdskategorier.|
|
