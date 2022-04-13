---
title: Konfigurer søgning efter Microsoft 365 Multi-Geo
ms.reviewer: adwood
ms.author: tlarsen
author: tklarsen
manager: arnek
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: seo-marvel-mar2020
ms.collection: Strat_SP_gtc
ms.localizationpriority: medium
f1.keywords:
- NOCSH
description: Få mere at vide om, hvordan du konfigurerer søgning i et multi-geo-miljø. Det er kun nogle klienter, f.eks. OneDrive, der kan returnere resultater i et multi-geo-miljø.
ms.openlocfilehash: a6f152a3f226befa8bc060dadd0eed1c0952523c
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/13/2022
ms.locfileid: "64824920"
---
# <a name="configure-search-for-microsoft-365-multi-geo"></a>Konfigurer søgning efter Microsoft 365 Multi-Geo

I et multi-geo-miljø har hver geo-placering sit eget søgeindeks og søgecenter. Når en bruger søger, sendes forespørgslen til alle indeksene, og de returnerede resultater flettes.

En bruger på én geografisk placering kan f.eks. søge efter indhold, der er gemt på en anden geografisk placering, eller efter indhold på et SharePoint websted, der er begrænset til en anden geografisk placering. Hvis brugeren har adgang til dette indhold, viser søgningen resultatet.

## <a name="which-search-clients-work-in-a-multi-geo-environment"></a>Hvilke søgeklienter arbejder i et multi-geo-miljø?

Disse klienter kan returnere resultater fra alle geografiske placeringer:

- OneDrive
- Delve
- Startsiden for SharePoint
- Søgecentret
- Brugerdefinerede søgeprogrammer, der bruger api'en SharePoint Search

### <a name="onedrive"></a>OneDrive

Så snart multi-geo-miljøet er konfigureret, får brugere, der søger i OneDrive resultater fra alle geografiske placeringer.

### <a name="delve"></a>Delve

Så snart multi-geo-miljøet er konfigureret, får brugere, der søger i Delve resultater fra alle geografiske placeringer.

Det Delve feed og profilkortet viser kun eksempler på filer, der er gemt på den centrale placering. For filer, der er gemt på satellitplaceringer, vises ikonet for filtypen i stedet.

### <a name="the-sharepoint-home-page"></a>Startsiden for SharePoint

Så snart multi-geo-miljøet er blevet konfigureret, kan brugerne se nyheder, seneste og fulgte websteder fra flere geografiske placeringer på deres SharePoint hjemmeside. Hvis de bruger søgefeltet på SharePoint startside, får de flettede resultater fra flere geografiske placeringer.

### <a name="the-search-center"></a>Søgecentret

Når multi-geo-miljøet er konfigureret, viser hvert søgecenter fortsat kun resultater fra deres egen geoplacering. Administratorer skal [ændre indstillingerne for hvert søgecenter](#_Set_up_a_1) for at få resultater fra alle geografiske placeringer. Derefter får brugere, der søger i søgecentret, resultater fra alle geografiske placeringer.

### <a name="custom-search-applications"></a>Brugerdefinerede søgeprogrammer

Som sædvanlig interagerer brugerdefinerede søgeprogrammer med søgeindekserne ved hjælp af de eksisterende REST API'er til søgning SharePoint. Hvis du vil hente resultater fra alle eller nogle geografiske placeringer, skal programmet [kalde API'en og inkludere de nye Multi-Geo-forespørgselsparametre](#_Get_custom_search) i anmodningen. Dette udløser en fan ud af forespørgslen til alle geografiske placeringer.

## <a name="whats-different-about-search-in-a-multi-geo-environment"></a>Hvad er anderledes ved søgning i et multi-geo-miljø?

Nogle søgefunktioner, du måske kender, fungerer anderledes i et multi-geo-miljø.

<table>
<thead>
<tr class="header">
<th align="left">Funktion</th>
<th align="left">Sådan fungerer det</th>
<th align="left">Løsning</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Fremhævede resultater</td>
<td align="left">Du kan oprette forespørgselsregler med fremhævede resultater på forskellige niveauer: for hele lejeren, for en gruppe af websteder eller for et websted. I et multi-geo-miljø skal du definere hævede resultater på lejerniveau for at hæve resultaterne til søgecentrene på alle geografiske placeringer. Hvis du kun vil hæve resultater i søgecentret, der er på den geografiske placering af gruppen af websteder eller på webstedet, skal du definere de fremhævede resultater på gruppe af websteder eller på webstedsniveau. Disse resultater hæves ikke på andre geografiske placeringer.</td>
<td align="left">Hvis du ikke har brug for forskellige fremhævede resultater pr. geografisk placering, f.eks. forskellige regler for rejser, anbefaler vi, at du definerer hævede resultater på lejerniveau.</td>
</tr>
<tr class="even">
<td align="left">Søg efter afgrænsninger</td>
<td align="left">Søgning returnerer afgrænsninger fra alle en lejers geografiske placeringer og aggregerer dem derefter. Sammenlægningen er den bedste indsats, hvilket betyder, at antallet af afgrænsninger muligvis ikke er 100 % nøjagtigt. I de fleste søgebaserede scenarier er denne nøjagtighed tilstrækkelig.
</td>
<td align="left">I forbindelse med søgebaserede programmer, der afhænger af fuldførelse af afgrænsningsfunktionen, skal du forespørge hver geoplacering uafhængigt af hinanden.</td>
</tr>
<tr class="odd">
<td align="left"></td>
<td align="left">Multi-geo-søgning understøtter ikke dynamisk bucketing for numeriske afgrænsninger.</td>
<td align="left">Brug <a href="/sharepoint/dev/general-development/query-refinement-in-sharepoint">parameteren "Discretize"</a> til numeriske afgrænsninger.</td>
</tr>
<tr class="even">
<td align="left">Dokument-id'er</td>
<td align="left">Hvis du udvikler et søgedrevet program, der afhænger af dokument-id'er, skal du bemærke, at dokument-id'er i et multi-geo-miljø ikke er unikke på tværs af geografiske placeringer, de er unikke pr. geografisk placering.</td>
<td align="left">Vi har tilføjet en kolonne, der identificerer den geografiske placering. Brug denne kolonne til at opnå entydighed. Denne kolonne hedder "GeoLocationSource".</td>
</tr>
<tr class="odd">
<td align="left">Antal resultater</td>
<td align="left">På siden med søgeresultater vises kombinerede resultater fra de geografiske placeringer, men det er ikke muligt at side ud over 500 resultater.</td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left">Hybridsøgning</td>
<td align="left">I et hybridt SharePoint miljø med <a href="/sharepoint/hybrid/learn-about-cloud-hybrid-search-for-sharepoint">hybridsøgning i cloudmiljøet</a> føjes indhold i det lokale miljø til det Microsoft 365 indeks for den centrale placering.</td>
<td align="left"></td>
</tr>
</tbody>
</table>

## <a name="whats-not-supported-for-search-in-a-multi-geo-environment"></a>Hvad understøttes ikke til søgning i et multi-geo-miljø?

Nogle af de søgefunktioner, du kender, understøttes ikke i et multi-geo-miljø.

<table>
<thead>
<tr class="header">
<th align="left">Søgefunktion</th>
<th align="left">Bemærk</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Godkendelse kun for apps</td>
<td align="left">Godkendelse kun til apps (privilegeret adgang fra tjenester) understøttes ikke i søgning i flere geografiske områder.</td>
</tr>
<tr class="even">
<td align="left">Gæsterne</td>
<td align="left">Gæster får kun resultater fra den geografiske placering, de søger fra.</td>
</tr>
</tbody>
</table>

## <a name="how-does-search-work-in-a-multi-geo-environment"></a>Hvordan fungerer søgning i et multi-geo-miljø?

Alle søgeklienter bruger de eksisterende SharePoint REST API'er til søgning til at interagere med søgeindekserne.

![Diagram, der viser, hvordan SharePoint REST API'er til søgning interagerer med søgeindekserne.](../media/configure-search-for-multi-geo-image1-1.png)

1. En søgeklient kalder REST-slutpunktet for søgning med forespørgselsegenskaben EnableMultiGeoSearch= true.
2. Forespørgslen sendes til alle geografiske placeringer i lejeren.
3. Søgeresultater fra hver geografisk placering flettes og rangeres.
4. Klienten får samlede søgeresultater.

<span id="_Set_up_a" class="anchor"><span id="_Ref501388384" class="anchor"></span></span>Bemærk, at vi ikke fletter søgeresultaterne, før vi har modtaget resultater fra alle geografiske placeringer. Det betyder, at multi-geo-søgninger har yderligere ventetid sammenlignet med søgninger i et miljø med kun én geografisk placering.

<span id="_Set_up_a_1" class="anchor"><span id="_Ref505252370" class="anchor"></span></span>
## <a name="get-a-search-center-to-show-results-from-all-geo-locations"></a>Få et søgecenter for at få vist resultater fra alle geografiske placeringer

Hvert søgecenter har flere lodrette lodrette elementer, og du skal konfigurere hvert lodrette enkeltvist.

1. Sørg for, at du udfører disse trin med en konto, der har tilladelse til at redigere siden med søgeresultater og webdelen Søgeresultat.

2. Naviger til siden med søgeresultater (se [listen over](https://support.office.com/article/174d36e0-2f85-461a-ad9a-8b3f434a4213) sider med søgeresultater)

3. Vælg den lodrette for at konfigurere, klik **på Indstillinger** tandhjulsikon i øverste højre hjørne, og klik derefter på **Rediger side**. Siden med søgeresultater åbnes i redigeringstilstand.

   ![Rediger sidevalg i Indstillinger.](../media/configure-search-for-multi-geo-image2.png)

4. I webdelen Søgeresultater skal du flytte markøren til øverste højre hjørne af webdelen, klikke på pilen og derefter klikke på **Rediger webdel** i menuen. Værktøjsruden Søgeresultater åbnes under båndet øverst til højre på siden.

   ![Rediger valg af webdel.](../media/configure-search-for-multi-geo-image3.png)

5. Vælg **Vis Multi-Geo-resultater** under **Indstillinger for resultatkontrol** i sektionen **Indstillinger** i værktøjsruden Webdel for at få vist webdelen Søgeresultater for at få vist resultater fra alle geografiske placeringer.

6. Klik på **OK** for at gemme ændringen og lukke værktøjsruden for webdelen.

7. Kontrollér dine ændringer af webdelen Søgeresultater ved at klikke på **Tjek ind** under fanen Side i hovedmenuen.

8. Publicer ændringerne ved hjælp af det link, der er angivet i noten øverst på siden.

<span id="_Get_custom_search" class="anchor"><span id="_Ref501388387" class="anchor"></span></span>
## <a name="get-custom-search-applications-to-show-results-from-all-or-some-geo-locations"></a>Hent brugerdefinerede søgeprogrammer for at få vist resultater fra alle eller nogle geografiske placeringer

Brugerdefinerede søgeprogrammer henter resultater fra alle eller nogle geografiske placeringer ved at angive forespørgselsparametre med anmodningen til REST API'en til SharePoint Search. Afhængigt af forespørgselsparametrene er forespørgslen udtjekning til alle geografiske placeringer eller til nogle geografiske placeringer. Hvis du f.eks. kun har brug for at forespørge på et undersæt af geografiske placeringer for at finde relevante oplysninger, kan du styre blæseren ud til disse. Hvis anmodningen lykkes, returnerer REST API'en til SharePoint search svardata.

### <a name="requirement"></a>Krav

For hver geografisk placering skal du sikre, at alle brugere i organisationen har fået tildelt tilladelsesniveauet **Læs** for rodwebstedet (f.eks. contosoAPAC.sharepoint.com/ og contosoEU.sharepoint.com/). [Få mere at vide om tilladelser](https://support.office.com/article/understanding-permission-levels-in-sharepoint-87ecbb0e-6550-491a-8826-c075e4859848).

### <a name="query-parameters"></a>Forespørgselsparametre

EnableMultiGeoSearch – Dette er en boolesk værdi, der angiver, om forespørgslen skal udtrækkes til indekserne for andre geoplaceringer i multi-geo-lejeren. Indstil den til **sand** for at fremhæve forespørgslen. **false** til ikke at udtjekke forespørgslen. Hvis du ikke inkluderer denne parameter, er standardværdien **falsk**, medmindre du foretager et REST API-kald mod et websted, der bruger skabelonen Enterprise Search Center, i dette tilfælde er standardværdien **sand**. Hvis du bruger parameteren i et miljø, der ikke er multi-geo, ignoreres parameteren.

ClientType – Dette er en streng. Angiv et entydigt klientnavn for hvert søgeprogram. Hvis du ikke inkluderer denne parameter, sendes forespørgslen ikke til andre geografiske placeringer.

MultiGeoSearchConfiguration – Dette er en valgfri liste over, hvilke geografiske placeringer i multi-geo-lejeren der skal aktiveres i forespørgslen, når **EnableMultiGeoSearch** er **sand**. Hvis du ikke inkluderer denne parameter eller lader den være tom, er forespørgslen fannederet til alle geografiske placeringer. For hver geografisk placering skal du angive følgende elementer i JSON-format:

<table>
<thead>
<tr class="header">
<th align="left">Element</th>
<th align="left">Beskrivelse</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">DataLocation</td>
<td align="left">Den geografiske placering, f.eks. NAM.</td>
</tr>
<tr class="even">
<td align="left">Slutpunkt</td>
<td align="left">Det slutpunkt, der skal oprettes forbindelse til, f.eks. https://contoso.sharepoint.com</td>
</tr>
<tr class="odd">
<td align="left">Kilde-id</td>
<td align="left">GUID for resultatkilden, f.eks. B81EAB55-3140-4312-B0F4-9459D1B4FFEE.</td>
</tr>
</tbody>
</table>

Hvis du udelader DataLocation eller EndPoint, eller hvis en DataLocation er duplikeret, mislykkes anmodningen. [Du kan få oplysninger om slutpunktet for en lejers geografiske placeringer ved hjælp af Microsoft Graph](/sharepoint/dev/solution-guidance/multigeo-discovery).

### <a name="response-data"></a>Svardata

MultiGeoSearchStatus – Dette er en egenskab, som SharePoint Search API returnerer som svar på en anmodning. Værdien af egenskaben er en streng og giver følgende oplysninger om de resultater, som SharePoint Search API returnerer:

<table>
<thead>
<tr class="header">
<th align="left">Værdi</th>
<th align="left">Beskrivelse</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Fuld</td>
<td align="left">Komplette resultater fra <strong>alle</strong> geografiske placeringer.</td>
</tr>
<tr class="even">
<td align="left">Delvis</td>
<td align="left">Delvise resultater fra en eller flere geografiske placeringer. Resultaterne er ufuldstændige på grund af en forbigående fejl.</td>
</tr>
</tbody>
</table>

### <a name="query-using-the-rest-service"></a>Forespørgsel ved hjælp af REST-tjenesten

Med en GET-anmodning angiver du forespørgselsparametrene i URL-adressen. Med en POST-anmodning overfører du forespørgselsparametrene i brødteksten i JSON-formatet (JavaScript Object Notation).

#### <a name="request-headers"></a>Anmodningsheadere

<table>
<thead>
<tr class="header">
<th align="left">Navn</th>
<th align="left">Værdi</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Indholdstype</td>
<td align="left">application/json;odata=verbose</td>
</tr>
</tbody>
</table>

#### <a name="sample-get-request-thats-fanned-out-to-all-geo-locations"></a>Eksempel på GET-anmodning, der er fremhævet til **alle** geografiske placeringer

```http
https:// \<tenant\>/\_api/search/query?querytext='sharepoint'&Properties='EnableMultiGeoSearch:true'&ClientType='my\_client\_id'
```

#### <a name="sample-get-request-to-fan-out-to-some-geo-locations"></a>Eksempel på GET-anmodning om at gå ud til **nogle** geografiske placeringer

```http
https:// \<tenant\>/\_api/search/query?querytext='site'&ClientType='my_client_id'&Properties='EnableMultiGeoSearch:true, MultiGeoSearchConfiguration:[{DataLocation\\:"NAM"\\,Endpoint\\:"https\\://contosoNAM.sharepoint.com"\\,SourceId\\:"B81EAB55-3140-4312-B0F4-9459D1B4FFEE"}\\,{DataLocation\\:"CAN"\\,Endpoint\\:"https\\://contosoCAN.sharepoint-df.com"}]'
```

> [!NOTE]
> Kommaer og kolon på listen over geografiske placeringer for egenskaben MultiGeoSearchConfiguration har foranstillet **omvendt skråstreg** . Dette skyldes, at GET-anmodninger bruger kolon til at adskille egenskaber og kommaer til separate argumenter for egenskaber. Uden omvendt skråstreg som et escape-tegn fortolkes egenskaben MultiGeoSearchConfiguration forkert.

#### <a name="sample-post-request-thats-fanned-out-to-all-geo-locations"></a>Eksempel på EN POST-anmodning, der er udtjekning til **alle** geografiske placeringer

```http
    {
    "request": {
            "__metadata": {
            "type": "Microsoft.Office.Server.Search.REST.SearchRequest"
        },
        "Querytext": "sharepoint",
        "Properties": {
            "results": [
                {
                    "Name": "EnableMultiGeoSearch",
                    "Value": {
                        "QueryPropertyValueTypeIndex": 3,
                        "BoolVal": true
                    }
                }
            ]
        },
        "ClientType": "my_client_id"
        }
    }
```

#### <a name="sample-post-request-thats-fanned-out-to-some-geo-locations"></a>Eksempel på EN POST-anmodning, der er udtjekning til **nogle** geografiske placeringer

```http
    {
        "request": {
            "Querytext": "SharePoint",
            "ClientType": "my_client_id",
            "Properties": {
                "results": [
                    {
                        "Name": "EnableMultiGeoSearch",
                        "Value": {
                            "QueryPropertyValueTypeIndex": 3,
                            "BoolVal": true
                        }
                    },
                    {
                        "Name": "MultiGeoSearchConfiguration",
                        "Value": {
                        "StrVal": "[{\"DataLocation\":\"NAM\",\"Endpoint\":\"https://contoso.sharepoint.com\",\"SourceId\":\"B81EAB55-3140-4312-B0F4-9459D1B4FFEE\"},{\"DataLocation\":\"CAN\",\"Endpoint\":\"https://contosoCAN.sharepoint.com\"}]",
                            "QueryPropertyValueTypeIndex": 1
                        }
                    }
                ]
            }
        }
    }
```

### <a name="query-using-csom"></a>Forespørgsel ved hjælp af CSOM

Her er et eksempel på en CSOM-forespørgsel, der er fannederet til **alle** geografiske placeringer:

```CSOM
var keywordQuery = new KeywordQuery(ctx);
keywordQuery.QueryText = query.SearchQueryText;
keywordQuery.ClientType = <enter a string here>;
keywordQuery.Properties["EnableMultiGeoSearch"] = true;
```
