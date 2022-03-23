---
title: Webbeskyttelse
description: Få mere at vide om webbeskyttelse i Microsoft Defender til slutpunkt, og hvordan du kan beskytte din organisation
keywords: webbeskyttelse, beskyttelse mod webtrusler, webbrowsing, sikkerhed, phishing, malware, udnyttelse, websteder, netværksbeskyttelse, Microsoft Edge, Internet Explorer, Chrome, Firefox, webbrowser, ondsindede websteder
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
ms.openlocfilehash: d21fdd481ade59ca869d5cfe086e537c0c431228
ms.sourcegitcommit: dd6514ae173f1c821d4ec25298145df6cb232e2e
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/19/2022
ms.locfileid: "63591190"
---
# <a name="web-protection"></a>Webbeskyttelse

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-main-abovefoldlink&rtc=1)


## <a name="about-web-protection"></a>Om webbeskyttelse

Webbeskyttelse i Microsoft Defender til slutpunkt er en funktion, der består af webtrusselsbeskyttelse, [filtrering af webindhold](web-content-filtering.md) og [brugerdefinerede indikatorer](manage-indicators.md).[](web-threat-protection.md) Med webbeskyttelse kan du beskytte dine enheder mod webtrusler og hjælpe dig med at regulere uønsket indhold. Du kan finde Web protection-rapporter i Microsoft 365 Defender portal ved at gå til **Rapporter > Web Protection**.

:::image type="content" alt-text="Billede af alle webbeskyttelseskort." source="images/web-protection.png" lightbox="images/web-protection.png":::

### <a name="web-threat-protection"></a>Webtrusselsbeskyttelse

De kort, der udgør webtrusselsbeskyttelse, er **webtrusler over tid og** **webtrusleroversigt**.

Webtrusselsbeskyttelse omfatter:

- Omfattende indsigt i webtrusler, der påvirker din organisation.
- Undersøgelsesfunktioner over webrelateret trusselsaktivitet via beskeder og omfattende profiler for URL-adresser og de enheder, der får adgang til disse URL-adresser.
- Et komplet sæt sikkerhedsfunktioner, der sporer generelle adgangstendenser til ondsindede og uønskede websteder.

Du kan finde flere oplysninger under [Beskyttelse mod webtrusler](web-threat-protection.md).

### <a name="custom-indicators"></a>Brugerdefinerede indikatorer

Brugerdefinerede indikatorregistreringer opsummeres også i organisationens webtrusler under **Webtrusselsregistreringer over** tid og **Web-trusselsoversigt**.

Brugerdefineret indikator omfatter:

- Mulighed for at oprette IP- og URL-baserede indikatorer for kompromis for at beskytte din organisation mod trusler.
- Undersøgelsesfunktioner over aktiviteter relateret til dine brugerdefinerede IP/URL-profiler og de enheder, der får adgang til disse URL-adresser.
- Muligheden for at oprette politikkerne Tillad, Bloker og Advar for IP'er og URL-adresser.

Få mere at vide under [Opret indikatorer for IP'er og URL-adresser/domæner](indicator-ip-domain.md)

### <a name="web-content-filtering"></a>Filtrering af webindhold

Filtrering af webindhold omfatter **webaktivitet efter kategori**, oversigt **over filtrering af webindhold og** **webaktivitetsoversigt**.

Filtrering af webindhold omfatter:

- Brugere er forhindret i at få adgang til websteder i blokerede kategorier, uanset om de søger lokalt eller væk.
- Du kan nemt installere forskellige politikker for forskellige sæt af brugere ved hjælp af de enhedsgrupper, der er defineret i rollebaserede adgangskontrolindstillinger [for Microsoft Defender til Slutpunkt](/microsoft-365/security/defender-endpoint/rbac).
- Du kan få adgang til webrapporter på samme centrale placering med synlighed over faktiske blokke og webforbrug.

Du kan finde flere oplysninger under [Filtrering af webindhold](web-content-filtering.md).

## <a name="order-of-precedence"></a>Rangorden

Webbeskyttelse består af følgende komponenter, der er angivet i rangordenen. Hver af disse komponenter gennemtvinges af SmartScreen-klienten Microsoft Edge og af Network Protection-klienten i alle andre browsere og processer.

- Brugerdefinerede indikatorer (IP/URL, politikker for Microsoft Defender til skyapps)
  - Tillad
  - Advar
  - Bloker

- Webtrusler (malware, phish)
  - SmartScreen Intel, herunder Exchange Online Protection (EOP)
  - Eskaleringer

- WCF (Web Content Filtering)

> [!NOTE]
> Microsoft Defender til skyapps genererer i øjeblikket kun indikatorer for blokerede URL-adresser.

Rækkefølgen relaterer til rækkefølgen af handlinger, som en URL- eller IP-adresse evalueres efter. Hvis du f.eks. har en politik for filtrering af webindhold, kan du oprette undtagelser via brugerdefinerede IP/URL-indikatorer. Brugerdefinerede indikatorer for forlig (IoC) er højere i rangordenen end WCF-blokke.

På samme måde kan man under en konflikt mellem indikatorer altid tilsidesætte blokke (tilsidesætte logik). Det betyder, at en tilladelsesindikator vinder over enhver blokindikator, der findes.

Tabellen nedenfor opsummerer nogle almindelige konfigurationer, der ville præsentere konflikter inden for webbeskyttelsesstakken. Den identificerer også de resulterende bestemmelser baseret på ovenstående rangfølge.

<br>

****

|Politik for brugerdefineret indikator|Webtrusselspolitik|WCF-politik|Politik for Defender til skyapps|Resultat|
|---|---|---|---|---|
|Tillad|Bloker|Bloker|Bloker|Tillad (tilsidesættelse af webbeskyttelse)|
|Tillad|Tillad|Bloker|Bloker|Tillad (WCF-undtagelse)|
|Advar|Bloker|Bloker|Bloker|Advar (tilsidesæt)|
|

Interne IP-adresser understøttes ikke af brugerdefinerede indikatorer. For en advarselspolitik, når den tilsidesættes af slutbrugeren, vil blokeringen af webstedet som standard ikke være blokeret i 24 timer for den pågældende bruger. Denne tidsramme kan ændres af administratoren og overføres ned af SmartScreen-skytjenesten. Muligheden for at springe en advarsel over kan også deaktiveres i Microsoft Edge brug af CSP til webtrusselsblokke (malware/phishing). Du kan finde flere oplysninger [Microsoft Edge SmartScreen Indstillinger](/DeployEdge/microsoft-edge-policies#smartscreen-settings-policies).

## <a name="protect-browsers"></a>Beskyt browsere

I alle webbeskyttelsesscenarier kan SmartScreen og netværksbeskyttelse bruges sammen for at sikre beskyttelse på tværs af både første- og tredjepartsbrowsere og -processer. SmartScreen er indbygget direkte Microsoft Edge, mens Netværksbeskyttelse overvåger trafik i tredjepartsbrowsere og -processer. Nedenstående diagram illustrerer dette koncept. Dette diagram over de to klienter, der arbejder sammen om at tilbyde flere browser-/app-dækninger, gælder nøjagtigt for alle funktioner i Web Protection (indikatorer, webtrusler, indholdsfiltrering).

:::image type="content" alt-text="Brug af SmartScreen og netværksbeskyttelse sammen." source="../../media/web-protection-protect-browsers.png" lightbox="../../media/web-protection-protect-browsers.png":::

## <a name="troubleshoot-endpoint-blocks"></a>Fejlfinding af slutpunktsblokke

Svar fra SmartScreen-skyen standardiseres. Værktøjer som f.eks. Fiddler kan bruges til at undersøge svaret fra skytjenesten, hvilket hjælper med at bestemme blokkens kilde.

Når SmartScreen-skytjenesten reagerer med et tillad, blokere eller advare svar, videresendes en svarkategori og serverkontekst tilbage til klienten. I Microsoft Edge er svarkategorien det, der bruges til at bestemme den relevante blokeringsside, der skal vises (skadelig, phishing, organisationspolitik).

Tabellen nedenfor viser svarene og deres korrelerede funktioner.

<br>

****

|ResponseCategory|Funktion, der er ansvarlig for blokken|
|---|---|
|CustomPolicy|WCF|
|CustomBlockList|Brugerdefinerede indikatorer|
|CasbPolicy|Defender til skyapps|
|Ondsindet|Webtrusler|
|Phishing|Webtrusler|
|||

## <a name="advanced-hunting-for-web-protection"></a>Avanceret jagt på webbeskyttelse

Kusto-forespørgsler i avanceret jagt kan bruges til at opsummere webbeskyttelsesblokke i din organisation i op til 30 dage. I disse forespørgsler bruges oplysningerne ovenfor til at skelne mellem de forskellige kilder til blokke og opsummere dem på en brugervenlig måde. Forespørgslen nedenfor viser f.eks. alle WCF-blokke, der stammer Microsoft Edge.

```kusto
DeviceEvents
| where ActionType == "SmartScreenUrlWarning"
| extend ParsedFields=parse_json(AdditionalFields)
| project DeviceName, ActionType, Timestamp, RemoteUrl, InitiatingProcessFileName, Experience=tostring(ParsedFields.Experience)
| where Experience == "CustomBlockList"
```

På samme måde kan du bruge forespørgslen nedenfor til at få vist alle WCF-blokke, der stammer fra Netværksbeskyttelse (f.eks. en WCF-blok i en tredjepartsbrowser). Bemærk, at ActionType er blevet opdateret, og "Oplevelse" er blevet ændret til "Svarkategori".

```kusto
DeviceEvents
| where ActionType == "ExploitGuardNetworkProtectionBlocked"
| extend ParsedFields=parse_json(AdditionalFields)
| project DeviceName, ActionType, Timestamp, RemoteUrl, InitiatingProcessFileName, ResponseCategory=tostring(ParsedFields.ResponseCategory)
| where ResponseCategory == "CustomPolicy"
```

Hvis du vil have vist listeblokke, der skyldes andre funktioner (f.eks. Brugerdefinerede indikatorer), skal du se tabellen ovenfor med en disposition for hver funktion og deres respektive svarkategori. Disse forespørgsler kan også ændres til at søge efter telemetri, der er relateret til bestemte maskiner i organisationen. Bemærk, at ActionType, der vises i hver forespørgsel ovenfor, kun viser de forbindelser, der blev blokeret af en webbeskyttelsesfunktion, og ikke al netværkstrafik.

## <a name="user-experience"></a>Brugeroplevelse

Hvis en bruger besøger en webside, der udgør en risiko for malware, phishing eller andre webtrusler, udløser Microsoft Edge en blokeringsside, hvor der står: "Dette websted er blevet rapporteret som usikkert" sammen med oplysninger om truslerne.

> [!div class="mx-imgBorder"]
> ![Side blokeret af Microsoft Edge.](../../media/web-protection-malicious-block.png)

Hvis blokeret af WCF eller en brugerdefineret indikator, vises en blokside i Microsoft Edge, der fortæller brugeren, at webstedet er blokeret af deres organisation.

> [!div class="mx-imgBorder"]
> ![Side blokeret af din organisation.](../../media/web-protection-indicator-blockpage.png)

Under alle omstændigheder vises der ingen blokeringssider i tredjepartsbrowsere, og brugeren får vist siden "Sikker forbindelse mislykkedes" sammen med en toastbesked. Afhængigt af den politik, der er ansvarlig for blokeringen, får en bruger vist en anden meddelelse i toastbeskeden. Filtrering af webindhold viser f.eks. meddelelsen "Dette indhold er blokeret".

> [!div class="mx-imgBorder"]
> ![Side blokeret af WCF.](../../media/web-protection-np-block.png)

## <a name="report-false-positives"></a>Rapportér falske positive

Hvis du vil rapportere en falsk positiv for websteder, der af SmartScreen anses for at være skadelige, skal du bruge det link, der vises på blokeringssiden i Microsoft Edge (som vist ovenfor).

For WCF kan du bestride kategorien for et domæne. Gå til fanen **Domæner i** WCF-rapporterne, og klik derefter **på Rapportaccuracy**. Der åbnes en pop op-pop op-pop-op-pop-op. Angiv prioriteten af hændelsen, og angiv nogle yderligere detaljer, f.eks. den foreslåede kategori. Du kan få mere at vide om, hvordan du aktiverer WCF, og hvordan du vælger kategorier for tvister, under [Filtrering af webindhold](web-content-filtering.md).

Du kan finde flere oplysninger om, hvordan du sender falske positive/negativer, i Adressere falske [positive/negativer i Microsoft Defender til slutpunkt](defender-endpoint-false-positives-negatives.md).

## <a name="related-information"></a>Relaterede oplysninger

<br>

****

|Emne|Beskrivelse|
|---|---|
|[Webtrusselsbeskyttelse](web-threat-protection.md) | Stop adgangen til phishingwebsteder, malwarevektorer, udnyttelseswebsteder, upålidelige websteder eller websteder med dårligt ry og websteder, som du har blokeret.|
|[Filtrering af webindhold](web-content-filtering.md) | Spore og regulere adgangen til websteder baseret på deres indholdskategorier.|
|
