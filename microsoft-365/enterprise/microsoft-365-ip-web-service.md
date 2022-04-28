---
title: Office 365 IP-adresse og URL-webtjeneste
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 8/6/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- m365initiative-coredeploy
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
ms.reviewer: pandrew
search.appverid:
- MET150
- MOE150
- BCS160
description: Få mere at vide om, hvordan du bruger Office 365 IP-adresse og URL-webtjeneste til at hjælpe dig med bedre at identificere og differentiere Office 365 netværkstrafik.
ms.openlocfilehash: b13377c6230c869231b7cecda8375f663cbcd33b
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65100627"
---
# <a name="office-365-ip-address-and-url-web-service"></a>Office 365 IP-adresse og URL-webtjeneste

Webtjenesten Office 365 IP-adresse og URL-adresse hjælper dig med bedre at identificere og differentiere Office 365 netværkstrafik, hvilket gør det nemmere for dig at evaluere, konfigurere og holde dig ajour med ændringer. Denne REST-baserede webtjeneste erstatter de tidligere XML-filer, der kan downloades, og som blev udfaset den 2. oktober 2018.

Som kunde eller leverandør af netværksperimeterenheder kan du oprette i forhold til webtjenesten for Office 365 IP-adresse og FQDN-poster. Du kan få adgang til dataene direkte i en webbrowser ved hjælp af disse URL-adresser:

- Du kan finde den nyeste version af Office 365 URL-adresser og IP-adresseområder ved at bruge [https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).
- Hvis du vil se dataene på siden Office 365 URL-adresser og IP-adresseområder for firewalls og proxyservere, skal du bruge [https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).
- Hvis du vil hente alle de seneste ændringer siden juli 2018, da webtjenesten først var tilgængelig, skal du bruge [https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).

Som kunde kan du bruge denne webtjeneste til at:

- Opdater dine PowerShell-scripts for at hente Office 365 slutpunktsdata og ændre formateringen af dine netværksenheder.
- Brug disse oplysninger til at opdatere PAC-filer, der er installeret på klientcomputere.

Som leverandør af netværksperimeterenheder kan du bruge denne webtjeneste til at:

- Opret og test enhedssoftware for at downloade listen til automatiseret konfiguration.
- Kontrollér, om der er den aktuelle version.
- Hent de aktuelle ændringer.

> [!NOTE]
> Hvis du bruger Azure ExpressRoute til at oprette forbindelse til Office 365, skal du gennemse [Azure ExpressRoute for at få Office 365](azure-expressroute.md) for at blive fortrolig med de Office 365 tjenester, der understøttes via Azure ExpressRoute. Gennemse også artiklen [Office 365 URL-adresser og IP-adresseintervaller](urls-and-ip-address-ranges.md) for at forstå, hvilke netværksanmodninger for Office 365 programmer der kræver internetforbindelse. Dette hjælper med at konfigurere perimetersikkerhedsenhederne bedre.

Du kan finde flere oplysninger under:

- [Blogindlæg om annoncering i Office 365 Tech Community Forum](https://techcommunity.microsoft.com/t5/Office-365-Blog/Announcing-Office-365-endpoint-categories-and-Office-365-IP/ba-p/177638)
- [Office 365 Tech Community Forum for spørgsmål om brug af webtjenester](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)

## <a name="common-parameters"></a>Almindelige parametre

Disse parametre er fælles på tværs af alle webtjenestemetoderne:

- **format=\<JSON \| CSV\>** – Som standard er det returnerede dataformat JSON. Brug denne valgfri parameter til at returnere dataene i CSV-format (kommaseparerede værdier).
- **ClientRequestId=\<guid\>** – Et påkrævet GUID, som du genererer for klienttilknytningen. Opret et entydigt GUID for hver computer, der kalder webtjenesten (de scripts, der er inkluderet på denne side, genererer et GUID for dig). Brug ikke guid'erne, der vises i følgende eksempler, da de kan blive blokeret af webtjenesten i fremtiden. GUID-formatet er _xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxx_, hvor x repræsenterer et hexadecimaltal.

  Hvis du vil oprette et GUID, kan du bruge kommandoen [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) PowerShell eller bruge en onlinetjeneste, f.eks. [Generator af online-GUID](https://www.guidgenerator.com/).

## <a name="version-web-method"></a>Webmetode for version

Microsoft opdaterer posterne Office 365 IP-adresse og FQDN i begyndelsen af hver måned. Out-of-band-opdateringer udgives nogle gange på grund af supporthændelser, sikkerhedsopdateringer eller andre driftsmæssige krav.

Dataene for hver publicerede forekomst tildeles et versionsnummer, og webmetoden version giver dig mulighed for at kontrollere, om der er den nyeste version af hver Office 365 tjenesteforekomst. Vi anbefaler, at du kontrollerer versionen ikke mere end én gang i timen.

Parametrene for webmetoden til versionen er:

- **AllVersions=\<true \| false\>** – Den version, der returneres, er som standard den nyeste. Medtag denne valgfri parameter for at anmode om alle publicerede versioner, siden webtjenesten blev udgivet første gang.
- **Format=\<JSON \| CSV \| RSS\>** – Ud over formaterne JSON og CSV understøtter webmetoden også RSS. Du kan bruge denne valgfri parameter sammen med parameteren _AllVersions=true_ til at anmode om et RSS-feed, der kan bruges sammen med Outlook eller andre RSS-læsere.
- **Forekomst=\<Worldwide \| China \| USGovDoD \| USGovGCCHigh\>** – Denne valgfri parameter angiver den forekomst, versionen skal returneres for. Hvis den udelades, returneres alle forekomster. Gyldige forekomster er: Worldwide, China, USGovDoD, USGovGCCHigh.

Webmetoden til versionen er ikke begrænset og returnerer aldrig 429 HTTP-svarkoder. Svaret på webmetoden for versionen omfatter en cachekontrolheader, der anbefaler cachelagring af dataene i 1 time. Resultatet fra webmetoden version kan være en enkelt post eller en matrix af poster. Elementerne i hver post er:

- instance – Det korte navn på Office 365 tjenesteforekomst.
- latest – den nyeste version for slutpunkter for den angivne forekomst.
- versioner – en liste over alle tidligere versioner for den angivne forekomst. Dette element medtages kun, hvis parameteren _AllVersions_ er sand.

### <a name="version-web-method-examples"></a>Eksempler på webmetode til version

Eksempel 1- anmodnings-URI: <https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7>

Denne URI returnerer den nyeste version af hver Office 365 tjenesteforekomst. Eksempelresultat:

```json
[
 {
  "instance": "Worldwide",
  "latest": "2018063000"
 },
 {
  "instance": "USGovDoD",
  "latest": "2018063000"
 },
 {
  "instance": "USGovGCCHigh",
  "latest": "2018063000"
 },
 {
  "instance": "China",
  "latest": "2018063000"
 }
]
```

> [!IMPORTANT]
> GUID'et for parameteren ClientRequestID i disse URI'er er kun et eksempel. Hvis du vil prøve webtjeneste-URI'erne, skal du generere dit eget GUID. De GUID'er, der vises i disse eksempler, kan blive blokeret af webtjenesten i fremtiden.

Eksempel 2- anmodnings-URI: <https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7>

Denne URI returnerer den nyeste version af den angivne Office 365 tjenesteforekomst. Eksempelresultat:

```json
{
 "instance": "Worldwide",
 "latest": "2018063000"
}
```

Eksempel 3- anmodnings-URI: <https://endpoints.office.com/version/Worldwide?Format=CSV&ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7>

Denne URI viser output i CSV-format. Eksempelresultat:

```csv
instance,latest
Worldwide,2018063000
```

Eksempel 4- anmodnings-URI: <https://endpoints.office.com/version/Worldwide?AllVersions=true&ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7>

Denne URI viser alle tidligere versioner, der er publiceret for Office 365 verdensomspændende tjenesteforekomst. Eksempelresultat:

```json
{
  "instance": "Worldwide",
  "latest": "2018063000",
  "versions": [
    "2018063000",
    "2018062000"
  ]
}
```

Eksempel 5 RSS-feed-URI: <https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS>

Denne URI viser et RSS-feed for de publicerede versioner, der indeholder links til listen over ændringer for hver version. Eksempelresultat:

```xml
<?xml version="1.0" encoding="ISO-8859-1"?>
<rss version="2.0" xmlns:a10="https://www.w3.org/2005/Atom">
<channel>
<link>https://aka.ms/o365ip</link>
<description/>
<language>en-us</language>
<lastBuildDate>Thu, 02 Aug 2018 00:00:00 Z</lastBuildDate>
<item>
<guid isPermaLink="false">2018080200</guid>
<link>https://endpoints.office.com/changes/Worldwide/2018080200?singleVersion&clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7</link> <description>Version 2018080200 includes 2 changes. IPs: 2 added and 0 removed.</description>
<pubDate>Thu, 02 Aug 2018 00:00:00 Z</pubDate>
</item>
```

## <a name="endpoints-web-method"></a>Webmetode for slutpunkter

Webmetoden slutpunkter returnerer alle poster for IP-adresseintervaller og URL-adresser, der udgør Office 365-tjenesten. De nyeste data fra webmetoden for slutpunkter skal altid bruges til konfiguration af netværksenheder. Microsoft giver forhåndsmeddelelse 30 dage før publicering af nye tilføjelser for at give dig tid til at opdatere adgangskontrollister og proxyserver bypass-lister. Det anbefales, at du kun kalder webmetoden for slutpunkter igen, når webmetoden for versionen angiver, at der er en ny version af dataene tilgængelig.

Parametrene for slutpunktets webmetode er:

- **Tjenesteområder=\<Common \| Exchange \| SharePoint \| Skype\>** –En kommasepareret liste over tjenesteområder. De gyldige elementer er _Fælles_, _Exchange_, _SharePoint_ og _Skype_. Da _Elementer i Common_ Service-området er en forudsætning for alle andre tjenesteområder, inkluderer webtjenesten dem altid. Hvis du ikke medtager denne parameter, returneres alle tjenesteområder.
- **TenantName=\<tenant_name\>** – Dit Office 365 lejernavn. Webtjenesten tager det angivne navn og indsætter det i dele af URL-adresser, der indeholder lejernavnet. Hvis du ikke angiver et lejernavn, har disse dele af URL-adresser jokertegnet (\*).
- **NoIPv6=\<true \| false\>** – Angiv værdien til _sand_ for at udelade IPv6-adresser fra outputtet, hvis du ikke bruger IPv6 i netværket.
- **Forekomst=\<Worldwide \| China \| USGovDoD \| USGovGCCHigh\>** –Denne obligatoriske parameter angiver den forekomst, som slutpunkterne skal returneres fra. Gyldige forekomster er: _Worldwide_, _China_, _USGovDoD_ og _USGovGCCHigh_.

Hvis du kalder webmetoden for slutpunkter for mange gange fra den samme klient-IP-adresse, modtager du muligvis HTTP-svarkoden _429 (for mange anmodninger)_. Hvis du får vist denne svarkode, skal du vente 1 time, før du gentager din anmodning, eller generere et nyt GUID for anmodningen. Generelt bedste praksis er det kun at kalde webmetoden for slutpunkter, når webmetoden for versionen angiver, at der er en ny version tilgængelig.

Resultatet fra webmetoden slutpunkter er en matrix af poster, hvor hver post repræsenterer et bestemt slutpunktsæt. Elementerne for hver post er:

- id – Det uforanderlige id-nummer for slutpunktssættet.
- serviceArea – Det tjenesteområde, som dette er en del af: _Fælles_, _Exchange_, _SharePoint_ eller _Skype_.
- URL-adresser – URL-adresser for slutpunktssættet. En JSON-matrix af DNS-poster. Udeladt, hvis den er tom.
- tcpPorts – TCP-porte for slutpunktssættet. Alle portelementer formateres som en kommasepareret liste over porte eller portområder adskilt af et tankestregtegn (-). Porte gælder for alle IP-adresser og alle URL-adresser i slutpunktet, der er angivet for en given kategori. Udeladt, hvis den er tom.
- udpPorts – UDP-porte for IP-adresseintervaller i dette slutpunktssæt. Udeladt, hvis den er tom.
- ips – de IP-adresseområder, der er knyttet til dette slutpunkt, som er knyttet til de angivne TCP- eller UDP-porte. En JSON-matrix af IP-adresseområder. Udeladt, hvis den er tom.
- category – forbindelseskategorien for slutpunktssættet. Gyldige værdier er _Optimer_, _Tillad_ og _Standard_. Hvis du søger i outputtet for slutpunkterne for webmetoden efter kategorien for en bestemt IP-adresse eller URL-adresse, er det muligt, at din forespørgsel returnerer flere kategorier. I så fald skal du følge anbefalingen for den højeste prioritetskategori. Hvis slutpunktet f.eks. vises i både _Optimer_ og _Tillad_, skal du følge kravene til _Optimer_. Kræves.
- expressRoute – _Sand_ , hvis dette slutpunktssæt dirigeres over ExpressRoute, _Falsk_ , hvis ikke.
- required – _Sand_, hvis dette slutpunktssæt skal have forbindelse, for at Office 365 understøttes. _Falsk_ , hvis dette slutpunktsæt er valgfrit.
- noter – I forbindelse med valgfrie slutpunkter beskriver denne tekst Office 365 funktionalitet, der ikke er tilgængelig, hvis der ikke kan opnås adgang til IP-adresser eller URL-adresser i dette slutpunktsæt på netværkslaget. Udeladt, hvis den er tom.

### <a name="endpoints-web-method-examples"></a>Eksempler på slutpunktswebmetode

Eksempel 1- anmodnings-URI: <https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7>

Denne URI henter alle slutpunkter for Office 365 verdensomspændende forekomst for alle arbejdsbelastninger. Eksempelresultat, der viser et udsnit af outputtet:

```json
[
 {
  "id": 1,
  "serviceArea": "Exchange",
  "serviceAreaDisplayName": "Exchange Online",
  "urls":
   [
    "*.protection.outlook.com"
   ],
  "ips":
   [
    "2a01:111:f403::/48", "23.103.132.0/22", "23.103.136.0/21", "23.103.198.0/23", "23.103.212.0/22", "40.92.0.0/14", "40.107.0.0/17", "40.107.128.0/18", "52.100.0.0/14", "213.199.154.0/24", "213.199.180.128/26", "94.245.120.64/26", "207.46.163.0/24", "65.55.88.0/24", "216.32.180.0/23", "23.103.144.0/20", "65.55.169.0/24", "207.46.100.0/24", "2a01:111:f400:7c00::/54", "157.56.110.0/23", "23.103.200.0/22", "104.47.0.0/17", "2a01:111:f400:fc00::/54", "157.55.234.0/24", "157.56.112.0/24", "52.238.78.88/32"
   ],
  "tcpPorts": "443",
  "expressRoute": true,
  "category": "Allow"
 },
 {
  "id": 2,
  "serviceArea": "Exchange",
  "serviceAreaDisplayName": "Exchange Online",
  "urls":
   [
    "*.mail.protection.outlook.com"
   ],
```

Det fulde output af anmodningen i dette eksempel ville indeholde andre slutpunktssæt.

Eksempel 2- anmodnings-URI: [https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp; ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

I dette eksempel hentes slutpunkter for Office 365 Verdensomspændende forekomst kun for Exchange Online og afhængigheder.

Outputtet, f.eks. 2, svarer til eksempel 1, bortset fra at resultaterne ikke indeholder slutpunkter for SharePoint Online eller Skype for Business Online.

## <a name="changes-web-method"></a>Ændrer webmetode

Webmetoden ændringer returnerer de seneste opdateringer, der er blevet publiceret, typisk den forrige måneds ændringer af IP-adresseintervaller og URL-adresser.

De vigtigste ændringer af data for slutpunkter er nye URL-adresser og IP-adresser. Hvis du ikke føjer en IP-adresse til en liste over firewalladgangskontrol eller en URL-adresse til en tilsidesættelsesliste for proxyserveren, kan det medføre afbrydelse af Office 365 brugere bag denne netværksenhed. Uanset driftskravene publiceres nye slutpunkter til webtjenesten 30 dage før den dato, hvor slutpunkterne klargøres til brug for at give dig tid til at opdatere adgangskontrollister og lister over tilsidesættelse af proxyserver.

Den påkrævede parameter for webmetoden for ændringer er:

- **Version=\<YYYYMMDDNN>** – Påkrævet URL-ruteparameter. Denne værdi er den version, du har implementeret i øjeblikket. Webtjenesten returnerer ændringerne siden denne version. Formatet er _YYYYYMMDDNN_, hvor _NN_ er et naturligt tal forøget, hvis der kræves flere versioner for at blive publiceret på en enkelt dag, hvor _00_ repræsenterer den første opdatering for en given dag. Webtjenesten kræver, at _versionsparameteren_ indeholder nøjagtigt 10 cifre.

Webmetoden for ændringer er begrænset på samme måde som slutpunktets webmetode. Hvis du modtager en 429 HTTP-svarkode, skal du vente 1 time, før du gentager din anmodning eller genererer et nyt GUID for anmodningen.

Resultatet af webmetoden ændringer er en matrix af poster, hvor hver post repræsenterer en ændring i en bestemt version af slutpunkterne. Elementerne for hver post er:

- id – Det uforanderlige id for ændringsposten.
- endpointSetId – Id'et for den post for slutpunktssættet, der ændres.
- disposition – Beskriver, hvad ændringen gjorde med posten for slutpunktssættet. Værdier _ændres_, _tilføjes_ eller _fjernes_.
- effekt – Ikke alle ændringer er lige vigtige for alle miljøer. I dette element beskrives den forventede indvirkning på et perimetermiljø for virksomhedsnetværket som følge af denne ændring. Dette element er kun inkluderet i ændringsposter for version **2018112800** og nyere. Mulighederne for indvirkningen er: – AddedIp – En IP-adresse blev føjet til Office 365 og vil snart være live på tjenesten. Dette repræsenterer en ændring, du skal foretage på en firewall eller en anden lag 3-netværksperimeterenhed. Hvis du ikke tilføjer dette, før vi begynder at bruge det, kan du opleve en afbrydelse.
  – AddedUrl – En URL-adresse blev føjet til Office 365 og vil snart være live på tjenesten. Dette repræsenterer en ændring, du skal foretage på en proxyserver eller URL-fortolker netværksperimeterenhed. Hvis du ikke tilføjer denne URL-adresse, før vi begynder at bruge den, kan du opleve et udfald.
  – AddedIpAndUrl – Både en IP-adresse og en URL-adresse blev tilføjet. Dette repræsenterer en ændring, du skal foretage på enten en firewall layer 3-enhed eller en proxyserver eller EN URL-fortolkningsenhed. Hvis du ikke tilføjer dette IP/URL-par, før vi begynder at bruge det, kan du opleve en afbrydelse.
  – RemovedIpOrUrl – Mindst én IP-adresse eller URL-adresse blev fjernet fra Office 365. Fjern netværksslutpunkterne fra perimeterenhederne, men du har ingen deadline for at gøre dette.
  – ChangedIsExpressRoute – Supportattributten ExpressRoute blev ændret. Hvis du bruger ExpressRoute, skal du muligvis udføre handlinger, afhængigt af din konfiguration.
  – MovedIpOrUrl – Vi har flyttet en IP-adresse eller URL-adresse mellem dette slutpunktssæt og et andet. Generelt kræves der ingen handling.
  – RemovedDuplicateIpOrUrl – Vi har fjernet en duplikeret IP-adresse eller URL-adresse, men den er stadig publiceret til Office 365. Generelt kræves der ingen handling.
  – OtherNonPriorityChanges – Vi har ændret noget mindre kritisk end alle de andre indstillinger, f.eks. indholdet af et notefelt.
- version – Versionen af det publicerede slutpunktssæt, hvor ændringen blev introduceret. Versionsnumre har formatet _YYYYYMMDDNN_, hvor _NN_ er et naturligt tal, der forøges, hvis der kræves flere versioner for at blive publiceret på en enkelt dag.
- previous – En understruktur, der beskriver tidligere værdier for ændrede elementer i slutpunktssættet. Dette medtages ikke for nyligt tilføjede slutpunktssæt. Omfatter  _ExpressRoute_, _serviceArea_, _category_, _required_, _tcpPorts_, _udpPorts_ og _notes_.
- current – En understruktur, der beskriver opdaterede værdier for ændringer af elementer i slutpunktssættet. Omfatter _ExpressRoute_, _serviceArea_, _category_, _required_, _tcpPorts_, _udpPorts_ og _notes_.
- add – En understruktur med detaljer om elementer, der skal føjes til samlinger af slutpunktssæt. Udelades, hvis der ikke er nogen tilføjelser.
  – effectiveDate – Definerer dataene, når tilføjelserne er live i tjenesten.
  – ips – elementer, der skal føjes til _ips-matrixen_ .
  – URL-adresser– Elementer, der skal føjes til matrixen _URL-adresser_ .
- remove – En understruktur med detaljer om elementer, der skal fjernes fra slutpunktssættet. Udelades, hvis der ikke er nogen fjernelser.
  – ips – elementer, der skal fjernes fra _ips-matrixen_ .
  – URL-adresser– Elementer, der skal fjernes fra matrixen _URL-adresser_ .

### <a name="changes-web-method-examples"></a>Ændrer eksempler på webmetode

Eksempel 1- anmodnings-URI: <https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7>

Dette anmoder om alle tidligere ændringer af Office 365 verdensomspændende tjenesteforekomst. Eksempelresultat:

```json
[
 {
  "id": 424,
  "endpointSetId": 32,
  "disposition": "Change",
  "version": "2018062700",
  "remove":
   {
    "urls":
     [
      "*.api.skype.com", "skypegraph.skype.com"
     ]
   }
 },
 {
  "id": 426,
  "endpointSetId": 31,
  "disposition": "Change",
  "version": "2018062700",
  "add":
   {
    "effectiveDate": "20180609",
    "ips":
     [
      "51.140.203.190/32"
     ]
   },
  "remove":
   {
    "ips":
     [
```

Eksempel 2- anmodnings-URI: <https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7>

Dette anmoder om ændringer siden den angivne version til Office 365 verdensomspændende forekomst. I dette tilfælde er den angivne version den nyeste. Eksempelresultat:

```json
[
  {
    "id":3,
    "endpointSetId":33,
    "changeDescription":"Removing old IP prefixes",
    "disposition":"Change",
    "version":"2018031301",
    "remove":{
      "ips":["65.55.127.0/24","66.119.157.192/26","66.119.158.0/25",
      "111.221.76.128/25","111.221.77.0/26","207.46.5.0/24"]
    }
  },
  {
    "id":4,
    "endpointSetId":45,
    "changeDescription":"Removing old IP prefixes",
    "disposition":"Change",
    "version":"2018031301",
    "remove":{
      "ips":["13.78.93.8/32","40.113.87.220/32","40.114.149.220/32",
      "40.117.100.83/32","40.118.214.164/32","104.208.31.113/32"]
    }
  }
]
```

## <a name="example-powershell-script"></a>Eksempel på PowerShell-script

Du kan køre dette PowerShell-script for at se, om der er handlinger, du skal udføre for at få opdaterede data. Du kan køre dette script som en planlagt opgave for at kontrollere, om der er en versionsopdatering. Hvis du vil undgå for stor belastning på webtjenesten, skal du prøve ikke at køre scriptet mere end én gang i timen.

Scriptet gør følgende:

- Kontrollerer versionsnummeret for de aktuelle Office 365 verdensomspændende forekomstslutpunkter ved at kalde REST API'en for webtjenesten.
- Kontrollerer, om der er en aktuel version af filen på _$Env:TEMP\O365_endpoints_latestversion.txt_. Stien til den globale variabel **$Env:TEMP** er normalt _C:\Users\\<username\>\AppData\Local\Temp_.
- Hvis det er første gang, scriptet køres, returnerer scriptet den aktuelle version og alle aktuelle IP-adresser og URL-adresser, skriver slutpunktsversionen til filen _$Env:TEMP\O365_endpoints_latestversion.txt_ og slutpunkterne dataoutput til filen _$Env:TEMP\O365_endpoints_data.txt_. Du kan ændre stien til og/eller navnet på outputfilen ved at redigere disse linjer:

    ``` powershell
    $versionpath = $Env:TEMP + "\O365_endpoints_latestversion.txt"
    $datapath = $Env:TEMP + "\O365_endpoints_data.txt"
    ```

- Hvis den seneste version af webtjenesten er identisk med versionen i _denO365_endpoints_latestversion.txt_ fil, afsluttes scriptet ved hver efterfølgende udførelse af scriptet uden at foretage ændringer.
- Når den nyeste version af webtjenesten er nyere end versionen i _O365_endpoints_latestversion.txt-filen_ , returnerer scriptet slutpunkterne og filtrene for kategorislutpunkterne **Tillad** og **Optimer** , opdaterer versionen i _filenO365_endpoints_latestversion.txt_ og skriver de opdaterede data til _O365_endpoints_data.txt-filen_ .

Scriptet genererer et entydigt _ClientRequestId_ for den computer, det udføres på, og genbruger dette id på tværs af flere kald. Dette id gemmes i _filenO365_endpoints_latestversion.txt_ .

### <a name="to-run-the-powershell-script"></a>Sådan kører du PowerShell-scriptet

1. Kopiér scriptet, og gem det på den lokale harddisk eller i den lokale scriptplacering som _Get-O365WebServiceUpdates.ps1_.
1. Udfør scriptet i din foretrukne scripteditor, f.eks. PowerShell ISE eller VS Code, eller fra en PowerShell-konsol ved hjælp af følgende kommando:

    ``` powershell
   powershell.exe -file <path>\Get-O365WebServiceUpdates.ps1
    ```

    Der er ingen parametre at overføre til scriptet.

```powershell
<# Get-O365WebServiceUpdates.ps1
From https://aka.ms/ipurlws
v1.1 8/6/2019

DESCRIPTION
This script calls the REST API of the Office 365 IP and URL Web Service (Worldwide instance)
and checks to see if there has been a new update since the version stored in an existing
$Env:TEMP\O365_endpoints_latestversion.txt file in your user directory's temp folder
(usually C:\Users\<username>\AppData\Local\Temp).
If the file doesn't exist, or the latest version is newer than the current version in the
file, the script returns IPs and/or URLs that have been changed, added or removed in the latest
update and writes the new version and data to the output file $Env:TEMP\O365_endpoints_data.txt.

USAGE
Run as a scheduled task every 60 minutes.

PARAMETERS
n/a

PREREQUISITES
PS script execution policy: Bypass
PowerShell 3.0 or later
Does not require elevation
#>

#Requires -Version 3.0

# web service root URL
$ws = "https://endpoints.office.com"
# path where output files will be stored
$versionpath = $Env:TEMP + "\O365_endpoints_latestversion.txt"
$datapath = $Env:TEMP + "\O365_endpoints_data.txt"

# fetch client ID and version if version file exists; otherwise create new file and client ID
if (Test-Path $versionpath) {
    $content = Get-Content $versionpath
    $clientRequestId = $content[0]
    $lastVersion = $content[1]
    Write-Output ("Version file exists! Current version: " + $lastVersion)
}
else {
    Write-Output ("First run! Creating version file at " + $versionpath + ".")
    $clientRequestId = [GUID]::NewGuid().Guid
    $lastVersion = "0000000000"
    @($clientRequestId, $lastVersion) | Out-File $versionpath
}

# call version method to check the latest version, and pull new data if version number is different
$version = Invoke-RestMethod -Uri ($ws + "/version/Worldwide?clientRequestId=" + $clientRequestId)
if ($version.latest -gt $lastVersion) {
    Write-Host "New version of Office 365 worldwide commercial service instance endpoints detected"
    # write the new version number to the version file
    @($clientRequestId, $version.latest) | Out-File $versionpath
    # invoke endpoints method to get the new data
    $endpointSets = Invoke-RestMethod -Uri ($ws + "/endpoints/Worldwide?clientRequestId=" + $clientRequestId)
    # filter results for Allow and Optimize endpoints, and transform these into custom objects with port and category
    # URL results
    $flatUrls = $endpointSets | ForEach-Object {
        $endpointSet = $_
        $urls = $(if ($endpointSet.urls.Count -gt 0) { $endpointSet.urls } else { @() })
        $urlCustomObjects = @()
        if ($endpointSet.category -in ("Allow", "Optimize")) {
            $urlCustomObjects = $urls | ForEach-Object {
                [PSCustomObject]@{
                    category = $endpointSet.category;
                    url      = $_;
                    tcpPorts = $endpointSet.tcpPorts;
                    udpPorts = $endpointSet.udpPorts;
                }
            }
        }
        $urlCustomObjects
    }
    # IPv4 results
    $flatIp4s = $endpointSets | ForEach-Object {
        $endpointSet = $_
        $ips = $(if ($endpointSet.ips.Count -gt 0) { $endpointSet.ips } else { @() })
        # IPv4 strings contain dots
        $ip4s = $ips | Where-Object { $_ -like '*.*' }
        $ip4CustomObjects = @()
        if ($endpointSet.category -in ("Allow", "Optimize")) {
            $ip4CustomObjects = $ip4s | ForEach-Object {
                [PSCustomObject]@{
                    category = $endpointSet.category;
                    ip = $_;
                    tcpPorts = $endpointSet.tcpPorts;
                    udpPorts = $endpointSet.udpPorts;
                }
            }
        }
        $ip4CustomObjects
    }
    # IPv6 results
    $flatIp6s = $endpointSets | ForEach-Object {
        $endpointSet = $_
        $ips = $(if ($endpointSet.ips.Count -gt 0) { $endpointSet.ips } else { @() })
        # IPv6 strings contain colons
        $ip6s = $ips | Where-Object { $_ -like '*:*' }
        $ip6CustomObjects = @()
        if ($endpointSet.category -in ("Optimize")) {
            $ip6CustomObjects = $ip6s | ForEach-Object {
                [PSCustomObject]@{
                    category = $endpointSet.category;
                    ip = $_;
                    tcpPorts = $endpointSet.tcpPorts;
                    udpPorts = $endpointSet.udpPorts;
                }
            }
        }
        $ip6CustomObjects
    }

    # write output to screen
    Write-Output ("Client Request ID: " + $clientRequestId)
    Write-Output ("Last Version: " + $lastVersion)
    Write-Output ("New Version: " + $version.latest)
    Write-Output ""
    Write-Output "IPv4 Firewall IP Address Ranges"
    ($flatIp4s.ip | Sort-Object -Unique) -join "," | Out-String
    Write-Output "IPv6 Firewall IP Address Ranges"
    ($flatIp6s.ip | Sort-Object -Unique) -join "," | Out-String
    Write-Output "URLs for Proxy Server"
    ($flatUrls.url | Sort-Object -Unique) -join "," | Out-String
    Write-Output ("IP and URL data written to " + $datapath)

    # write output to data file
    Write-Output "Office 365 IP and UL Web Service data" | Out-File $datapath
    Write-Output "Worldwide instance" | Out-File $datapath -Append
    Write-Output "" | Out-File $datapath -Append
    Write-Output ("Version: " + $version.latest) | Out-File $datapath -Append
    Write-Output "" | Out-File $datapath -Append
    Write-Output "IPv4 Firewall IP Address Ranges" | Out-File $datapath -Append
    ($flatIp4s.ip | Sort-Object -Unique) -join "," | Out-File $datapath -Append
    Write-Output "" | Out-File $datapath -Append
    Write-Output "IPv6 Firewall IP Address Ranges" | Out-File $datapath -Append
    ($flatIp6s.ip | Sort-Object -Unique) -join "," | Out-File $datapath -Append
    Write-Output "" | Out-File $datapath -Append
    Write-Output "URLs for Proxy Server" | Out-File $datapath -Append
    ($flatUrls.url | Sort-Object -Unique) -join "," | Out-File $datapath -Append
}
else {
    Write-Host "Office 365 worldwide commercial service instance endpoints are up-to-date."
}
```

## <a name="example-python-script"></a>Eksempel på Python-script

Her er et Python-script, der testes med Python 3.6.3 på Windows 10, som du kan køre for at se, om der er handlinger, du skal udføre for opdaterede data. Dette script kontrollerer versionsnummeret for Office 365 verdensomspændende forekomstslutpunkter. Når der er en ændring, downloades slutpunkterne og filtrene for kategorislutpunkterne _Tillad_ og _Optimer_ . Den bruger også et entydigt ClientRequestId på tværs af flere kald og gemmer den nyeste version, der blev fundet i en midlertidig fil. Kald dette script én gang i timen for at kontrollere, om der er en versionsopdatering.

```python
import json
import tempfile
from pathlib import Path
import urllib.request
import uuid
# helper to call the webservice and parse the response
def webApiGet(methodName, instanceName, clientRequestId):
    ws = "https://endpoints.office.com"
    requestPath = ws + '/' + methodName + '/' + instanceName + '?clientRequestId=' + clientRequestId
    request = urllib.request.Request(requestPath)
    with urllib.request.urlopen(request) as response:
        return json.loads(response.read().decode())
# path where client ID and latest version number will be stored
datapath = Path(tempfile.gettempdir() + '/endpoints_clientid_latestversion.txt')
# fetch client ID and version if data exists; otherwise create new file
if datapath.exists():
    with open(datapath, 'r') as fin:
        clientRequestId = fin.readline().strip()
        latestVersion = fin.readline().strip()
else:
    clientRequestId = str(uuid.uuid4())
    latestVersion = '0000000000'
    with open(datapath, 'w') as fout:
        fout.write(clientRequestId + '\n' + latestVersion)
# call version method to check the latest version, and pull new data if version number is different
version = webApiGet('version', 'Worldwide', clientRequestId)
if version['latest'] > latestVersion:
    print('New version of Office 365 worldwide commercial service instance endpoints detected')
    # write the new version number to the data file
    with open(datapath, 'w') as fout:
        fout.write(clientRequestId + '\n' + version['latest'])
    # invoke endpoints method to get the new data
    endpointSets = webApiGet('endpoints', 'Worldwide', clientRequestId)
    # filter results for Allow and Optimize endpoints, and transform these into tuples with port and category
    flatUrls = []
    for endpointSet in endpointSets:
        if endpointSet['category'] in ('Optimize', 'Allow'):
            category = endpointSet['category']
            urls = endpointSet['urls'] if 'urls' in endpointSet else []
            tcpPorts = endpointSet['tcpPorts'] if 'tcpPorts' in endpointSet else ''
            udpPorts = endpointSet['udpPorts'] if 'udpPorts' in endpointSet else ''
            flatUrls.extend([(category, url, tcpPorts, udpPorts) for url in urls])
    flatIps = []
    for endpointSet in endpointSets:
        if endpointSet['category'] in ('Optimize', 'Allow'):
            ips = endpointSet['ips'] if 'ips' in endpointSet else []
            category = endpointSet['category']
            # IPv4 strings have dots while IPv6 strings have colons
            ip4s = [ip for ip in ips if '.' in ip]
            tcpPorts = endpointSet['tcpPorts'] if 'tcpPorts' in endpointSet else ''
            udpPorts = endpointSet['udpPorts'] if 'udpPorts' in endpointSet else ''
            flatIps.extend([(category, ip, tcpPorts, udpPorts) for ip in ip4s])
    print('IPv4 Firewall IP Address Ranges')
    print(','.join(sorted(set([ip for (category, ip, tcpPorts, udpPorts) in flatIps]))))
    print('URLs for Proxy Server')
    print(','.join(sorted(set([url for (category, url, tcpPorts, udpPorts) in flatUrls]))))

    # TODO send mail (e.g. with smtplib/email modules) with new endpoints data
else:
    print('Office 365 worldwide commercial service instance endpoints are up-to-date')
```

## <a name="web-service-interface-versioning"></a>Versionsstyring af webtjenestegrænseflade

Opdateringer af parametrene eller resultaterne for disse webtjenestemetoder kan være påkrævet i fremtiden. Når versionen af disse webtjenester er offentligt tilgængelig, vil Microsoft gøre en rimelig indsats for at give forhåndsmeddelelse om væsentlige opdateringer til webtjenesten. Når Microsoft mener, at en opdatering kræver ændringer af klienter, der bruger webtjenesten, holder Microsoft den tidligere version (én version tilbage) af webtjenesten tilgængelig i mindst 12 måneder efter udgivelsen af den nye version. Kunder, der ikke opgraderer på dette tidspunkt, kan muligvis ikke få adgang til webtjenesten og dens metoder. Kunderne skal sikre, at klienter i webtjenesten fortsætter med at arbejde uden fejl, hvis der foretages følgende ændringer af grænsefladesignaturen for webtjenesten:

- Tilføjelse af en ny valgfri parameter til en eksisterende webmetode, der ikke skal leveres af ældre klienter, og som ikke påvirker det resultat, som en ældre klient modtager.
- Tilføjelse af en ny navngiven attribut i et af svar-REST-elementerne eller andre kolonner til svar-CSV.
- Tilføjelse af en ny webmetode med et nyt navn, der ikke kaldes af ældre klienter.

## <a name="update-notifications"></a>Opdateringsmeddelelser

Du kan bruge et par forskellige metoder til at få mailmeddelelser, når ændringer af IP-adresserne og URL-adresserne publiceres til webtjenesten.

- Hvis du vil bruge en Power Automate løsning, skal du se [Brug Power Automate til at modtage en mail for ændringer af Office 365 IP-adresser og URL-adresser](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/m-p/240651).
- Hvis du vil udrulle en Azure Logic App ved hjælp af en ARM-skabelon, [skal du se Office 365 Update Notification (v1.1)](https://aka.ms/ipurlws-updates-template).
- Hvis du vil skrive dit eget meddelelsesscript ved hjælp af PowerShell, skal du se [Send-MailMessage](/powershell/module/microsoft.powershell.utility/send-mailmessage).

## <a name="exporting-a-proxy-pac-file"></a>Eksport af en proxy-PAC-fil

[Get-PacFile er et PowerShell-script](https://www.powershellgallery.com/packages/Get-PacFile), der læser de nyeste netværksslutpunkter fra Office 365 IP-adresse og URL-webtjeneste og opretter et eksempel på en PAC-fil. Du kan få oplysninger om brug af Get-PacFile under [Brug en PAC-fil til direkte routing af vigtig Office 365 trafik](managing-office-365-endpoints.md#use-a-pac-file-for-direct-routing-of-vital-office-365-traffic).

## <a name="related-topics"></a>Relaterede emner
  
[Office 365-URL-adresser og IP-adresseintervaller](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)

[Administrere Office 365-slutpunkter](managing-office-365-endpoints.md)
  
[Ofte stillede spørgsmål om Office 365 slutpunkter](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)

[principper for Office 365 netværksforbindelser](microsoft-365-network-connectivity-principles.md)

[Office 365 netværk og justering af ydeevne](network-planning-and-performance.md)

[Vurdering af Office 365 netværksforbindelse](assessing-network-connectivity.md)
  
[Mediekvalitet og ydeevne for netværksforbindelsen i Skype for Business Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Optimering af netværket til Skype for Business Online](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)

[Office 365 justering af ydeevnen ved hjælp af grundlinjer og ydeevnehistorik](performance-tuning-using-baselines-and-history.md)
  
[Plan for fejlfinding af ydeevnen for Office 365](performance-troubleshooting-plan.md)
