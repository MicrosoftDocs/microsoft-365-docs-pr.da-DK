---
title: Konfigurere søgning efter Microsoft 365 multi-geo
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
description: Få mere at vide om, hvordan du konfigurerer søgning i et multi-geo-miljø. Kun nogle klienter, f.eks. OneDrive, kan returnere resultater i et multi-geo-miljø.
ms.openlocfilehash: d6d6895c6dc393bb1f28dff60dea996bf80aad5a
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63590607"
---
# <a name="configure-search-for-microsoft-365-multi-geo"></a>Konfigurere søgning efter Microsoft 365 multi-geo

I et multi-geo-miljø har hver geoplacering sit eget søgeindeks og søgecenter. Når en bruger søger, er forespørgslen udtonet til alle indekserne, og de returnerede resultater flettes.

Eksempelvis kan en bruger på én geoplacering søge efter indhold, der er gemt på en anden geoplacering, eller efter indhold på et SharePoint-websted, der er begrænset til en anden geoplacering. Hvis brugeren har adgang til dette indhold, vises resultatet ved søgning.

## <a name="which-search-clients-work-in-a-multi-geo-environment"></a>Hvilke søgeklienter fungerer i et miljø med flere geografiske oplysninger?

Disse klienter kan returnere resultater fra alle geoplaceringer:

- OneDrive
- Delve
- SharePoint startside
- Søgecenter
- Brugerdefinerede søgeprogrammer, der bruger SharePoint Search API

### <a name="onedrive"></a>OneDrive

Så snart multi-geo-miljøet er konfigureret, får brugere, der søger i OneDrive resultater fra alle geoplaceringer.

### <a name="delve"></a>Delve

Så snart multi-geo-miljøet er konfigureret, får brugere, der søger i Delve resultater fra alle geoplaceringer.

Feeden Delve og profilkortet viser kun eksempler på filer, der er gemt på den centrale placering. For filer, der er gemt på satellitplaceringer, vises ikonet for filtypen i stedet.

### <a name="the-sharepoint-home-page"></a>SharePoint startside

Så snart multi-geo-miljøet er konfigureret, vil brugerne se nyheder, seneste og fulgte websteder fra flere geoplaceringer på deres SharePoint startside. Hvis de bruger søgefeltet på SharePoint, får de flettede resultater fra flere geografiske placeringer.

### <a name="the-search-center"></a>Søgecenter

Når multi-geo-miljøet er konfigureret, fortsætter hvert søgecenter med kun at vise resultater fra deres egen geoplacering. Administratorer skal [ændre indstillingerne for hvert søgecenter for at](#_Set_up_a_1) få resultater fra alle geoplaceringer. Efterfølgende får brugere, der søger i søgecenteret, resultater fra alle geoplaceringer.

### <a name="custom-search-applications"></a>Brugerdefinerede søgeprogrammer

Som normalt interagerer brugerdefinerede søgeprogrammer med søgeindekserne ved hjælp af de eksisterende SharePoint Search REST-API'er. For at få resultater fra alle eller nogle geoplaceringer skal programmet kalde API'en og medtage de nye [multi-geo-forespørgselsparametre](#_Get_custom_search) i anmodningen. Dette udløser en fan ud af forespørgslen til alle geoplaceringer.

## <a name="whats-different-about-search-in-a-multi-geo-environment"></a>Hvad er anderledes ved søgning i et miljø med flere geografiske områder?

Nogle søgefunktioner, som du muligvis kender, fungerer anderledes i et multi-geo-miljø.

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
<td align="left">Promoverede resultater</td>
<td align="left">Du kan oprette forespørgselsregler med promoverede resultater på forskellige niveauer: for hele lejeren, for en gruppe af websteder eller for et websted. I et multi-geo-miljø skal du definere promoverede resultater på lejerniveau for at promovere resultaterne til søgecentrene på alle geoplaceringer. Hvis du kun vil promovere resultater i søgecenteret, der er på geoplaceringen for gruppen af websteder eller webstedet, skal du definere de promoverede resultater på niveauet for gruppen af websteder eller webstedet. Disse resultater promoveres ikke på andre geoplaceringer.</td>
<td align="left">Hvis du ikke har brug for forskellige promoverede resultater pr. geoplacering, f.eks. forskellige regler for rejser, anbefaler vi, at du definerer promoverede resultater på lejerniveau.</td>
</tr>
<tr class="even">
<td align="left">Søge afgrænsning</td>
<td align="left">Søgningen returnerer afgrænsninger fra alle en lejers geografiske placeringer og aggregerer dem derefter. Sammenlægningen er den bedste indsats, hvilket betyder, at antallet af afgrænsninger muligvis ikke er 100 % nøjagtige. Denne nøjagtighed er tilstrækkelig for de fleste søgebaserede scenarier. 
</td>
<td align="left">For søgebaserede programmer, der afhænger af fuldhed af afgrænsning, skal du forespørge på hver geoplacering enkeltvis.</td>
</tr>
<tr class="odd">
<td align="left"></td>
<td align="left">Multi-geo søgning understøtter ikke dynamisk bucketing for numeriske afgrænsning.</td>
<td align="left">Brug <a href="/sharepoint/dev/general-development/query-refinement-in-sharepoint">parameteren "Diskret" for numeriske</a> afgrænsning.</td>
</tr>
<tr class="even">
<td align="left">Dokument-i-dokumenter</td>
<td align="left">Hvis du udvikler et søgebaseret program, der afhænger af dokument-id'er, skal du bemærke, at dokument-id'er i et multi-geo-miljø ikke er entydige på tværs af geoplaceringer, de er entydige pr. geoplacering.</td>
<td align="left">Vi har tilføjet en kolonne, der identificerer geoplaceringen. Brug denne kolonne til at opnå entydighed. Denne kolonne hedder "GeoLocationSource".</td>
</tr>
<tr class="odd">
<td align="left">Antal resultater</td>
<td align="left">Siden med søgeresultater viser kombinerede resultater fra geoplaceringerne, men det er ikke muligt at side mere end 500 resultater.</td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left">Hybridsøgning</td>
<td align="left">I et SharePoint-miljø med <a href="/sharepoint/hybrid/learn-about-cloud-hybrid-search-for-sharepoint">hybridsøgning</a> i skyen føjes lokalt indhold til Microsoft 365 på den centrale placering.</td>
<td align="left"></td>
</tr>
</tbody>
</table>

## <a name="whats-not-supported-for-search-in-a-multi-geo-environment"></a>Hvad understøttes ikke til søgning i et multi-geo-miljø?

Nogle af de søgefunktioner, du muligvis kender, understøttes ikke i et multi-geo-miljø.

<table>
<thead>
<tr class="header">
<th align="left">Søgefunktion</th>
<th align="left">Bemærk!</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Kun appgodkendelse</td>
<td align="left">Appgodkendelse (privilegeret adgang fra tjenester) understøttes ikke i søgning i flere geografiske områder.</td>
</tr>
<tr class="even">
<td align="left">Gæster</td>
<td align="left">Gæster får kun resultater fra den geoplacering, de søger fra.</td>
</tr>
</tbody>
</table>

## <a name="how-does-search-work-in-a-multi-geo-environment"></a>Hvordan fungerer søgning i et miljø med flere geografiske oplysninger?

Alle søgeklienterne bruger de eksisterende SharePoint SEARCH REST-API'er til at interagere med søgeindekserne.

![Diagram, der viser, SharePoint SØG REST-API'er interagerer med søgeindekserne.](../media/configure-search-for-multi-geo-image1-1.png)

1. En søgeklient kalder Søge-REST-slutpunktet med forespørgselsegenskaben EnableMultiGeoSearch= sand.
2. Forespørgslen sendes til alle geoplaceringer i lejeren.
3. Søgeresultater fra hver geoplacering flettes og rangeres.
4. Klienten får samlede søgeresultater.

<span id="_Set_up_a" class="anchor"><span id="_Ref501388384" class="anchor"></span></span>Bemærk, at vi ikke fletter søgeresultaterne, før vi har modtaget resultater fra alle geoplaceringer. Det betyder, at multi-geo-søgninger har yderligere ventetid sammenlignet med søgninger i et miljø med kun én geoplacering.

<span id="_Set_up_a_1" class="anchor"><span id="_Ref505252370" class="anchor"></span></span>
## <a name="get-a-search-center-to-show-results-from-all-geo-locations"></a>Få et søgecenter til at vise resultater fra alle geografiske placeringer

Hvert søgecenter har flere lodrette linjer, og du skal konfigurere hver lodret lodret.

1. Sørg for at udføre disse trin med en konto, der har tilladelse til at redigere siden med søgeresultater og webdelen Søgeresultat.

2. Gå til siden med søgeresultater (se [listen over](https://support.office.com/article/174d36e0-2f85-461a-ad9a-8b3f434a4213) søgeresultatsider)

3. Vælg den lodrette for at konfigurere, **klik Indstillinger** tandhjulsikonet i øverste højre hjørne, og klik derefter på **Rediger side**. Siden med søgeresultater åbnes i redigeringstilstand.

   ![Rediger sidemarkering Indstillinger.](../media/configure-search-for-multi-geo-image2.png)

4. Flyt markøren til øverste højre hjørne af webdelen i webdelen Søgeresultater, klik på pilen, og klik derefter på **Rediger** webdel i menuen. Værktøjsruden for webdelen Søgeresultater åbnes under båndet øverst til højre på siden.

   ![Rediger valg af webdel.](../media/configure-search-for-multi-geo-image3.png)

5. I værktøjsruden for webdelen i **sektionen Indstillinger** **under Indstillinger** for resultatkontrol skal du vælge Vis **multi-geo-resultater** for at få webdelen Søgeresultater for at vise resultater fra alle geoplaceringer.

6. Klik **på OK** for at gemme ændringen og lukke værktøjsruden Webdel.

7. Kontrollér dine ændringer af webdelen Søgeresultater ved at klikke **på Tjek** ind på fanen Side i hovedmenuen.

8. Publicer ændringerne ved hjælp af linket i noten øverst på siden.

<span id="_Get_custom_search" class="anchor"><span id="_Ref501388387" class="anchor"></span></span>
## <a name="get-custom-search-applications-to-show-results-from-all-or-some-geo-locations"></a>Få brugerdefinerede søgeprogrammer til at vise resultater fra alle eller nogle geografiske placeringer

Brugerdefinerede søgeprogrammer får resultater fra alle eller nogle geoplaceringer ved at angive forespørgselsparametre sammen med anmodningen SharePoint Søg REST-API. Afhængigt af forespørgselsparametrene er forespørgslen udtonet til alle geoplaceringer eller til nogle geoplaceringer. Hvis du f.eks. kun har brug for at forespørge på et undersæt af geoplaceringer for at finde relevante oplysninger, kan du styre fanerne udelukkende til disse. Hvis anmodningen lykkes, returnerer SharePoint REST-API svardata.

### <a name="requirement"></a>Krav

For hver geoplacering skal du sikre, at alle brugere i organisationen har fået tilladelsesniveauet Læse  til rodwebstedet (f.eks. contosoAPAC.sharepoint.com/ og contosoPAC.sharepoint.com/). [Få mere at vide om tilladelser](https://support.office.com/article/understanding-permission-levels-in-sharepoint-87ecbb0e-6550-491a-8826-c075e4859848).

### <a name="query-parameters"></a>Forespørgselsparametre

EnableMultiGeoSearch – Dette er en boolesk værdi, der angiver, om forespørgslen skal udlejes til indekserne for andre geoplaceringer for multi-geo-lejeren. Indstil den **til sand** for at udpnde forespørgslen. **falsk** for ikke at udb køre forespørgslen. Hvis du ikke medtager denne parameter, er standardværdien **falsk, undtagen** når du foretager et REST API-opkald mod et websted, der bruger Enterprise Search Center-skabelonen, i dette tilfælde er standardværdien **sand**. Hvis du bruger parameteren i et miljø, der ikke er multi-geo, ignoreres parameteren.

ClientType – Dette er en streng. Angiv et entydigt klientnavn for hvert søgeprogram. Hvis du ikke medtager denne parameter, er forespørgslen ikke fanet ud til andre geoplaceringer.

MultiGeoSearchConfiguration – Dette er en valgfri liste over hvilke geoplaceringer i multi-geo-lejeren, du kan bruge til at udleje forespørgslen, når **EnableMultiGeoSearch** **er sand**. Hvis du ikke medtager denne parameter eller lader den være tom, bliver forespørgslen sendt ud til alle geoplaceringer. For hver geoplacering skal du angive følgende elementer i JSON-format:

<table>
<thead>
<tr class="header">
<th align="left">Element</th>
<th align="left">Beskrivelse</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Dataplacering</td>
<td align="left">Geoplaceringen, f.eks. NAM.</td>
</tr>
<tr class="even">
<td align="left">EndPoint</td>
<td align="left">Slutpunktet, der skal oprettes forbindelse til, f.eks. https://contoso.sharepoint.com</td>
</tr>
<tr class="odd">
<td align="left">SourceId</td>
<td align="left">GUID for resultatkilden, f.eks. B81EAB55-3140-4312-B0F4-9459D1B4FFEE.</td>
</tr>
</tbody>
</table>

Hvis du udelader Dataplacering eller Slutpunkt, eller hvis en Dataplacering er duplikeret, mislykkes anmodningen. [Du kan få oplysninger om slutpunktet for en lejers geoplaceringer ved hjælp af Microsoft Graph](/sharepoint/dev/solution-guidance/multigeo-discovery).

### <a name="response-data"></a>Svardata

MultiGeoSearchStatus – Dette er en egenskab, som SharePoint Search API returnerer som svar på en anmodning. Værdien af egenskaben er en streng og giver følgende oplysninger om de resultater, som den SharePoint Search API returnerer:

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
<td align="left">Fulde resultater <strong>fra alle</strong> geoplaceringer.</td>
</tr>
<tr class="even">
<td align="left">Delvis</td>
<td align="left">Delvise resultater fra en eller flere geoplaceringer. Resultaterne er ufuldstændige på grund af en midlertidig fejl.</td>
</tr>
</tbody>
</table>

### <a name="query-using-the-rest-service"></a>Forespørgsel ved hjælp af REST-tjenesten

Med en GET-anmodning angiver du forespørgselsparametrene i URL-adressen. Med en POST-anmodning passerer du forespørgselsparametrene i brødteksten i JavaScript Object Notation-formatet (JSON).

#### <a name="request-headers"></a>Anmod om brevhoveder

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

#### <a name="sample-get-request-thats-fanned-out-to-all-geo-locations"></a>Eksempel på GET-anmodning, der er udtonet **til** alle geoplaceringer

```http
https:// \<tenant\>/\_api/search/query?querytext='sharepoint'&Properties='EnableMultiGeoSearch:true'&ClientType='my\_client\_id'
```

#### <a name="sample-get-request-to-fan-out-to-some-geo-locations"></a>Eksempel på GET-anmodning om at faner **ud til** nogle geoplaceringer

```http
https:// \<tenant\>/\_api/search/query?querytext='site'&ClientType='my_client_id'&Properties='EnableMultiGeoSearch:true, MultiGeoSearchConfiguration:[{DataLocation\\:"NAM"\\,Endpoint\\:"https\\://contosoNAM.sharepoint.com"\\,SourceId\\:"B81EAB55-3140-4312-B0F4-9459D1B4FFEE"}\\,{DataLocation\\:"CAN"\\,Endpoint\\:"https\\://contosoCAN.sharepoint-df.com"}]'
```

> [!NOTE]
> Kommaer og kolon på listen over geoplaceringer for egenskaben MultiGeoSearchConfiguration indledes med en **skråstreg** . Dette skyldes, at GET-anmodninger bruger kolon til at adskille egenskaber og kommaer til at adskille argumenter i egenskaber. Uden en skråstreg som escape-tegn fortolkes egenskaben MultiGeoSearchConfiguration forkert.

#### <a name="sample-post-request-thats-fanned-out-to-all-geo-locations"></a>Eksempel på EN POST-anmodning, der er blevet udvidet **til alle** geoplaceringer

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

#### <a name="sample-post-request-thats-fanned-out-to-some-geo-locations"></a>Eksempel på EN POST-anmodning, der er blevet udvidet **til** nogle geoplaceringer

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

Her er en CSOM-eksempelforespørgsel, der er faner **for alle** geoplaceringer:

```CSOM
var keywordQuery = new KeywordQuery(ctx);
keywordQuery.QueryText = query.SearchQueryText;
keywordQuery.ClientType = <enter a string here>;
keywordQuery.Properties["EnableMultiGeoSearch"] = true;
```
