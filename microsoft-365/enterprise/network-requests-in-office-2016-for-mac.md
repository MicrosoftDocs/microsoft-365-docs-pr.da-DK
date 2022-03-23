---
title: Netværksanmodninger i Office til Mac
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/9/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Adm_O365_Setup
- seo-marvel-apr2020
search.appverid: MOM160
ms.assetid: afdae969-4046-44b9-9adb-f1bab216414b
description: I denne artikel beskrives, hvilke slutpunkter og webadresser, Office til Mac forsøger at nå, samt hvilke tjenester der er til rådighed.
ms.openlocfilehash: 37071b0aaf9e6f172d99a10cb4a1506f1627ef03
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63590348"
---
# <a name="network-requests-in-office-for-mac"></a>Netværksanmodninger i Office til Mac

Office til Mac-programmer giver en indbygget appoplevelse på macOS-platformen. Hver app er udviklet til at fungere i en række forskellige scenarier, herunder tilstande, hvor der ikke er netværksadgang tilgængelig. Når en computer er tilsluttet et netværk, opretter programmerne automatisk forbindelse til en række webbaserede tjenester for at give forbedret funktionalitet. Følgende oplysninger beskriver, hvilke slutpunkter og webadresser programmerne forsøger at nå, samt hvilke tjenester der er til rådighed. Disse oplysninger er nyttige ved fejlfinding af problemer med netværkskonfiguration og konfiguration af politikker for netværksproxyservere. Oplysningerne i denne artikel skal supplere artiklen Office 365 [webadresser](urls-and-ip-address-ranges.md) og adresseintervaller, som indeholder slutpunkter for computere, der kører Microsoft Windows. Medmindre andet er angivet, gælder oplysningerne i denne artikel også for Office 2019 til Mac og Office 2016 til Mac, der fås som et engangskøb fra en forhandler eller via en volumenlicensaftale. 

  
Det meste af denne artikel er tabeller, der beskriver netværkswebadresser, typer og beskrivelse af tjenester eller funktioner, der leveres af det pågældende slutpunkt. Hver af de Office apps kan variere i sin brug af tjenester og slutpunkter. Følgende apps er defineret i tabellerne nedenfor:
  
- W: Word
- P: PowerPoint
- X: Excel
- O: Outlook
- N: OneNote
   
URL-typen er defineret som følger:
  
- ST: Statisk – URL-adressen er hard-coded i klientprogrammet.
    
- SS: Semi-Static – URL-adressen er kodet som en del af en webside eller omdirigering.
    
- CS: Konfigurationstjeneste – URL-adressen returneres som en del Office Konfigurationstjeneste.

    
## <a name="office-for-mac-default-configuration"></a>Office til Mac standardkonfiguration

 **Installation og opdateringer**
  
Følgende netværksslutpunkter bruges til at downloade Office til Mac fra Microsoft Content Delivery Network (CDN).
  
|**URL-adresse**|**Type**|**Beskrivelse**|
|:-----|:-----|:-----|
|```https://go.microsoft.com/fwlink/```  <br/> |ST  <br/> |Microsoft 365 installationsportalens videresendelseslinktjeneste til de seneste installationspakker.  <br/> |
|```https://officecdn-microsoft-com.akamaized.net/```  <br/> |SS  <br/> |Placering af installationspakker på Content Delivery Network.  <br/> |
|```https://officecdn.microsoft.com/```  <br/> |SS  <br/> |Placering af installationspakker på Content Delivery Network.  <br/> |
|```https://officeci-mauservice.azurewebsites.net/```  <br/> |ST  <br/> |Administrationskontrolslutpunkt for Microsoft Automatiske opdateringer  <br/> |
   
 **Første start af app**
  
Følgende netværksslutpunkter kontaktes ved den første start af en Office-app. Disse slutpunkter giver øget Office funktionalitet for brugere, og URL-adresserne kontaktes uanset licenstype (herunder volumenlicensinstallationer).
  
|**URL-adresse**|**Apps**|**Type**|**Beskrivelse**|
|:-----|:-----|:-----|:-----|
|```https://config.edge.skype.com/```  <br/> |WXPON  <br/> |ST  <br/> |'Flighting'-konfiguration – giver mulighed for lysning og eksperimenteren med funktioner.  <br/> |
|```https://ocos-office365-s2s.msedge.net/```  <br/> |WXPON  <br/> |ST  <br/> |'Flighting'-netværkskonfigurationstest  <br/> |
|```https://client-office365-tas.msedge.net/```  <br/> |WXPON  <br/> |ST  <br/> |'Flighting'-netværkskonfigurationstest  <br/> |
|```https://officeclient.microsoft.com/```  <br/> |WXPON  <br/> |ST  <br/> |Office konfigurationstjeneste – hovedliste over tjenesteslutpunkter.  <br/> |
|```https://nexusrules.officeapps.live.com/```  <br/> |WXPON  <br/> |ST  <br/> |Office regeltelemetrioverførsel – informerer klienten om, hvilke data og hændelser der skal overføres til telemetritjenesten.  <br/> |
|```https://mobile.pipe.aria.microsoft.com/```  <br/> |N  <br/> |CS  <br/> |OneNote-telemetritjeneste  <br/> |
|```https://nexus.officeapps.live.com/```  <br/> |WXPON  <br/> |ST  <br/> |Office telemetri Upload Reporting - "Heartbeart" og fejlhændelser, der forekommer på klienten, uploades til telemetritjenesten.  <br/> |
|```https://templateservice.office.com/```  <br/> |WXP  <br/> |CS  <br/> |Office skabelontjeneste – giver brugerne onlinedokumentskabeloner.  <br/> |
|```https://omextemplates.content.office.net/```  <br/> |WXP  <br/> |CS  <br/> |Office over skabeloner – Storage af PNG-skabelonbilleder.  <br/> |
|```https://store.office.com/```  <br/> |WXP  <br/> |CS  <br/> |Store konfiguration til Office apps.  <br/> |
|```https://odc.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |Office dokumentintegrationstjenester (liste over tjenester og slutpunkter) og Home Realm Discovery.  <br/> |
|```https://cdn.odc.officeapps.live.com/```  <br/> |WXPON  <br/> |CS  <br/> |Ressourcer til Home Realm Discovery v2 (15.40 og nyere)  <br/> |
|```https://officecdn.microsoft.com/```  <br/> |WXPON  <br/> |ST  <br/> |Manifester for Microsoft Automatiske opdateringer – kontrollerer, om der er tilgængelige opdateringer  <br/> |
|```https://ajax.aspnetcdn.com/```  <br/> |WXPO  <br/> |SS  <br/> |Microsoft Ajax JavaScript-bibliotek  <br/> |
|```https://wikipedia.firstpartyapps.oaspapps.com/```  <br/> |W  <br/> |SS  <br/> |Wikipedia-app til Office konfiguration og ressourcer.  <br/> |
|```https://excelbingmap.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |SS  <br/> |Bing Kort-app til Office konfiguration og ressourcer.  <br/> |
|```https://peoplegraph.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |SS  <br/> |Personer Graph app til Office konfiguration og ressourcer.  <br/> |
|```https://www.onenote.com/```  <br/> |N  <br/> |ST  <br/> |Nyt indhold til OneNote.  <br/> |
|```https://site-cdn.onenote.net/```  <br/> |N  <br/> |ST  <br/> |Nyt indhold til OneNote.  <br/> |
|```https://site-cdn.onenote.net/```  <br/> |N  <br/> |SS  <br/> |Nyheder i billeder til OneNote.  <br/> |
|```https://acompli.helpshift.com/```  <br/> |O  <br/> |ST  <br/> |Supporttjeneste i appen.  <br/> |
|```https://prod-global-autodetect.acompli.net/```  <br/> |O  <br/> |ST  <br/> |Tjeneste til registrering af mailkonto.  <br/> |
|```https://autodiscover-s.outlook.com/```  <br/> |WXPO  <br/> |ST  <br/> |Outlook AutoDiscovery  <br/> |
|```https://outlook.office365.com/```  <br/> |WXPO  <br/> |ST  <br/> |Outlook slutpunkt for Microsoft 365 tjeneste.  <br/> |
|```https://r1.res.office365.com/```  <br/> |O  <br/> |ST  <br/> |Ikoner for Outlook-tilføjelsesprogrammet.  <br/> |
   
> [!NOTE]
> Tjenesten Office fungerer som en tjeneste til automatisk registrering for alle Microsoft Office klienter, ikke kun for Mac. De slutpunkter, der returneres i svaret er semi-statiske, da ændringer er meget sjældne, men stadig mulige. 
  
 **Log på**
  
Følgende netværksslutpunkter kontaktes, når du logger på skybaseret lager. Forskellige tjenester kan blive kontaktet afhængigt af din kontotype. Eksempel:
  
- **MSA: Microsoft-konto** – bruges typisk til forbruger- og detailscenarier 
    
- **OrgID: Organisationskonto** – bruges typisk til kommercielle scenarier 
    
|**URL-adresse**|**Apps**|**Type**|**Beskrivelse**|
|:-----|:-----|:-----|:-----|
|```https://login.windows.net/```  <br/> |WXPON  <br/> |ST  <br/> |Windows godkendelsestjeneste  <br/> |
|```https://login.microsoftonline.com/```  <br/> |WXPON  <br/> |ST  <br/> |Microsoft 365-logontjeneste (OrgID)  <br/> |
|```https://login.live.com/```  <br/> |WXPON  <br/> |ST  <br/> |Logontjeneste til Microsoft-konto (MSA)  <br/> |
|```https://auth.gfx.ms/```  <br/> |WXPON  <br/> |CS  <br/> |Microsoft Account Login Service Helper (MSA)  <br/> |
|```https://secure.aadcdn.microsoftonline-p.com/```  <br/> |WXPON  <br/> |SS  <br/> |Microsoft 365 Login Branding (OrgID)  <br/> |
|```https://ocws.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |Dokument- og Storage søger  <br/> |
|```https://roaming.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |Tjeneste for senest anvendte dokumenter (MRU )  <br/> |
   
> [!NOTE]
> For abonnementsbaserede licenser og detaillicenser aktiveres produktet, når du logger på, og det giver adgang til skyressourcer som f.eks. OneDrive. Ved installationer med volumenlicens bliver brugerne stadig bedt om at logge på (som standard), men det er kun påkrævet for at få adgang til skyressourcer, da produktet allerede er aktiveret. 
  
 **Produktaktivering**
  
Følgende netværksslutpunkter gælder for aktiveringer med Microsoft 365-abonnement og detaillicens. Specifikt gælder dette IKKE for installationer med volumenlicens.
  
|**URL-adresse**|**Apps**|**Type**|**Beskrivelse**|
|:-----|:-----|:-----|:-----|
|```https://ols.officeapps.live.com/```  <br/> |WXPON  <br/> |CS  <br/> |Office-licenstjeneste  <br/> |
   
 **Nyt indhold**
  
Følgende netværksslutpunkter gælder kun for Microsoft 365 abonnement.
  
|**URL-adresse**|**Apps**|**Type**|**Beskrivelse**|
|:-----|:-----|:-----|:-----|
|```https://contentstorage.osi.office.net/```  <br/> |WXPO  <br/> |SS  <br/> |Nyheder i JSON-sideindhold.  <br/> |
   
 **Researcher**
  
Følgende netværksslutpunkter gælder kun for Microsoft 365 abonnement.
  
|**URL-adresse**|**Apps**|**Type**|**Beskrivelse**|
|:-----|:-----|:-----|:-----|
|```https://entity.osi.office.net/```  <br/> |W  <br/> |CS  <br/> |Researcher-webtjeneste  <br/> |
|```https://cdn.entity.osi.office.net/```  <br/> |W  <br/> |CS  <br/> |Statisk indhold i Researcher  <br/> |
|```https://www.bing.com/```  <br/> |W  <br/> |CS  <br/> |Researcher-indholdsudbyder  <br/> |
   
 **Smart opslag**
  
Følgende netværksslutpunkter gælder både for aktiveringer med Microsoft 365-abonnement og detail-/volumenlicens.
  
|**URL-adresse**|**Apps**|**Type**|**Beskrivelse**|
|:-----|:-----|:-----|:-----|
|```https://uci.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |Insights webtjeneste  <br/> |
|```https://ajax.googleapis.com/```  <br/> |WXPN  <br/> |CS  <br/> |JQuery-bibliotek  <br/> |
|```https://cdnjs.cloudflare.com/```  <br/> |WXPN  <br/> |CS  <br/> |Understøttelse af JavaScript-bibliotek  <br/> |
|```https://www.bing.com/```  <br/> |WXPN  <br/> |CS  <br/> |Insights indholdsudbyder  <br/> |
|```https://tse1.mm.bing.net/```  <br/> |WXPN  <br/> |CS  <br/> |Insights indholdsudbyder  <br/> |
   
 **PowerPoint Designer**
  
Følgende netværksslutpunkter gælder kun for Microsoft 365 abonnement.
  
|**URL-adresse**|**Apps**|**Type**|**Beskrivelse**|
|:-----|:-----|:-----|:-----|
|```https://pptsgs.officeapps.live.com/```  <br/> |P  <br/> |CS  <br/> |PowerPoint Designer-webtjeneste  <br/> |
   
 **PowerPoint Hurtigstarter**
  
Følgende netværksslutpunkter gælder kun for Microsoft 365 abonnement.
  
|**URL-adresse**|**Apps**|**Type**|**Beskrivelse**|
|:-----|:-----|:-----|:-----|
|```https://pptcts.officeapps.live.com/```  <br/> |P  <br/> |CS  <br/> |PowerPoint Hurtigstarter-webtjeneste  <br/> |
   
 **Send en glad/glad**
  
Følgende netværksslutpunkter gælder både for aktiveringer med Microsoft 365-abonnement og detail-/volumenlicens.
  
|**URL-adresse**|**Apps**|**Type**|**Beskrivelse**|
|:-----|:-----|:-----|:-----|
|```https://sas.office.microsoft.com/```  <br/> |WXPON  <br/> |CS  <br/> |Send en smiley-tjeneste  <br/> |
   
 **Kontakt support**
  
Følgende netværksslutpunkter gælder både for aktiveringer med Microsoft 365-abonnement og detail-/volumenlicens.
  
|**URL-adresse**|**Apps**|**Type**|**Beskrivelse**|
|:-----|:-----|:-----|:-----|
|```https://powerlift-frontdesk.acompli.net/```  <br/> |O  <br/> |CS  <br/> |Kontakt support  <br/> |
|```https://acompli.helpshift.com/```  <br/> |O  <br/> |CS  <br/> |Supporttjeneste i appen  <br/> |
   
 **Gem som PDF**
  
Følgende netværksslutpunkter gælder både for aktiveringer med Microsoft 365-abonnement og detail-/volumenlicens.
  
|**URL-adresse**|**Apps**|**Type**|**Beskrivelse**|
|:-----|:-----|:-----|:-----|
|```https://wordcs.officeapps.live.com/```  <br/> |W  <br/> |CS  <br/> |Tjeneste til konvertering af Word-dokument (PDF)  <br/> |
   
 **Office apps (også kaldet tilføjelsesprogrammer)**
  
Følgende netværksslutpunkter gælder for aktiveringer med både Microsoft 365-abonnement og detail-/volumenlicens, når Office der er tillid til tilføjelsesapps.
  
|**URL-adresse**|**Apps**|**Type**|**Beskrivelse**|
|:-----|:-----|:-----|:-----|
|```https://store.office.com/```  <br/> |WXPO  <br/> |CS  <br/> |Office-app butikskonfiguration  <br/> |
|```https://wikipedia.firstpartyapps.oaspapps.com/```  <br/> |W  <br/> |SS  <br/> |Wikipedia-appressourcer  <br/> |
|```https://excelbingmap.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |SS  <br/> |Bing-kortappressourcer  <br/> |
|```https://peoplegraph.firstpartyapps.oaspapps.com```  <br/> |X  <br/> |SS  <br/> |Personer, Graph-appressourcer  <br/> |
|```https://o15.officeredir.microsoft.com/```  <br/> |WPX  <br/> |SS  <br/> |Office omdirigeringstjeneste  <br/> |
|```https://appsforoffice.microsoft.com/```  <br/> |WXP  <br/> |SS  <br/> |Office JavaScript-biblioteker  <br/> |
|```https://telemetry.firstpartyapps.oaspapps.com/```  <br/> |WX  <br/> |SS  <br/> |Telemetri- og rapporteringstjeneste til Office apps  <br/> |
|```https://ajax.microsoft.com/```  <br/> |W  <br/> |SS  <br/> |Microsoft Ajax JavaScript-bibliotek  <br/> |
|```https://ajax.aspnetcdn.com/```  <br/> |X  <br/> |SS  <br/> |Microsoft Ajax JavaScript-bibliotek  <br/> |
|```https://c.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |Office JavaScript-biblioteker  <br/> |
|```https://c1.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |Supportressourcer  <br/> |
|```https://cs.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |Supportressourcer  <br/> |
|```https://c.bing.com/```  <br/> |WPXO  <br/> |SS  <br/> |Supportressourcer  <br/> |
|```https://*.cdn.optimizely.com/```  <br/> |WPXO  <br/> |SS  <br/> |JavaScript-bibliotek  <br/> |
|```https://errors.client.optimizely.com/```  <br/> |WPX  <br/> |SS  <br/> |Fejlrapportering  <br/> |
|```https://*-contentstorage.osi.office.net/```  <br/> |WPXO  <br/> |SS  <br/> |Skrifttyperessourcer  <br/> |
|```https://nexus.ensighten.com/```  <br/> |WPXO  <br/> |SS  <br/> |Telemetritjeneste  <br/> |
|```https://browser.pipe.aria.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |Telemetrirapportering  <br/> |
|```https://*.vo.msecnd.net/```  <br/> |WPXO  <br/> |SS  <br/> |Microsoft Store aktivbibliotek  <br/> |
|```https://*.wikipedia.org/```  <br/> |W  <br/> |SS  <br/> |Wikipedia-sideressourcer  <br/> |
|```https://upload.wikimedia.org/```  <br/> |W  <br/> |SS  <br/> |Wikipedia-medieressourcer  <br/> |
|```https://wikipedia.firstpartyappssandbox.oappseperate.com/```  <br/> |W  <br/> |SS  <br/> |Wikipedia-sandkasseramme  <br/> |
|```https://*.virtualearth.net/```  <br/> |X  <br/> |SS  <br/> |Kortskabeloner  <br/> |
   
 **Sikre links**
  
Følgende netværksslutpunkt gælder kun for alle Office til Microsoft 365-abonnement.
  
|**URL-adresse**|**Type**|**Beskrivelse**|
|:-----|:-----|:-----|
|```https://*.oscs.protection.outlook.com/```  <br/> |CS  <br/> |Microsoft Pengeskab Link Service  <br/> |
   
 **Rapportering om nedbrud**
  
Følgende netværksslutpunkt gælder for alle Office til både Microsoft 365-abonnements- og detail-/volumenlicensaktivering. Når en proces uventet går ned, genereres der en rapport, som sendes til Watson-tjenesten.
  
|**URL-adresse**|**Type**|**Beskrivelse**|
|:-----|:-----|:-----|
|```https://watson.microsoft.com/```  <br/> |ST  <br/> |Tjenesten Microsoft Fejlrapportering  <br/> |
|```https://officeci.azurewebsites.net/```  <br/> |ST  <br/> |Office fælles Insights tjeneste  <br/> |
   
## <a name="options-for-reducing-network-requests-and-traffic"></a>Indstillinger til at reducere netværksanmodninger og -trafik

Standardkonfigurationen af Office til Mac giver den bedste brugeroplevelse, både med hensyn til funktionalitet og med at holde computeren opdateret. I visse situationer kan det være en fordel at forhindre programmer i at kontakte netværksslutpunkter. Dette afsnit beskriver muligheder for at gøre dette.
  
 ### <a name="disabling-cloud-sign-in-and-office-add-ins"></a>Deaktivere skybaserede Sign-In og Office Add-Ins
  
Kunder med volumenlicens kan have strenge politikker vedrørende lagring af dokumenter i skybaseret lagerplads. Den følgende programbaserede indstilling kan indstilles til at deaktivere MSA-/OrgID-logon og adgang til Office-tilføjelsesprogram.
  
- ```defaults write com.microsoft.Word UseOnlineContent -integer 0```

- ```defaults write com.microsoft.Excel UseOnlineContent -integer 0```

- ```defaults write com.microsoft.Powerpoint UseOnlineContent -integer 0```

Hvis brugerne forsøger at få adgang til Sign-In, får de vist en fejlmeddelelse om, at der ikke er en netværksforbindelse. Da denne indstilling også blokerer online produktaktivering, bør den kun bruges til installationer med volumenlicens. Specifikt forhindrer brug af denne indstilling Office programmer i at få adgang til følgende slutpunkter:
  
- ```https://odc.officeapps.live.com```
    
- ```https://*.firstpartyapps.oaspapps.com```
    
- Alle slutpunkter, der er angivet i afsnittet "Log på" ovenfor.
    
- Alle slutpunkter, der er angivet i sektionen "Smart opslag" ovenfor.
    
- Alle slutpunkter, der er angivet i afsnittet "Produktaktivering" ovenfor.
    
- Alle slutpunkter, der er angivet i afsnittet Office (også kaldet tilføjelsesprogrammer)" ovenfor.
    
Hvis du vil genoprette fuld funktionalitet for brugeren, skal du enten angive indstillingen til "2" eller fjerne den.
  
> [!NOTE]
> Denne indstilling kræver Office til Mac build 15.25 [160726] eller nyere. 
  
### <a name="telemetry"></a>Telemetri 
  
Office til Mac sender telemetrioplysninger tilbage til Microsoft med jævne mellemrum. Data uploades til 'Nexus'-slutpunktet. Telemetridata hjælper det tekniske team med at vurdere tilstand og eventuelle uventede funktionsmåder for hver Office-app. Der findes to kategorier af telemetri:
  
- **Heartbeat** indeholder oplysninger om version og licens. Disse data sendes straks efter start af appen. 
    
- **Brug** indeholder oplysninger om, hvordan apps bruges, samt ikke-alvorlige fejl. Disse data sendes hvert 60. minut. 
    
Microsoft tager beskyttelsen af dine personlige oplysninger meget alvorligt. Du kan læse om Microsofts politik for dataindsamling på [https://privacy.microsoft.com](https://privacy.microsoft.com). Hvis du vil forhindre programmer i at sende telemetridata om "Brug", kan indstillingen **SendAltTelemetriEnabled** justeres. Indstillingen er programbaseret og kan angives via macOS-konfigurationsprofiler eller manuelt fra Terminal: 
  
```defaults write com.microsoft.Word SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Excel SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Powerpoint SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Outlook SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.onenote.mac SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.autoupdate2 SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Office365ServiceV2 SendAllTelemetryEnabled -bool FALSE```

Heartbeat-telemetri sendes altid og kan ikke deaktiveres.
  
### <a name="crash-reporting"></a>Rapportering om nedbrud
  
Når der opstår en alvorlig programfejl, afsluttes programmet uventet, og der uploades en rapport om nedbruddet til 'Watson'-tjenesten. Nedbrudsrapporten består af en kaldstak, som er listen over trin, som programmet behandler i tiden op til nedbruddet. Disse trin hjælper det tekniske team med at identificere netop den funktion, der mislykkedes og hvorfor.
  
I nogle tilfælde får indholdet af et dokument programmet til at gå ned. Hvis appen identificerer dokumentet som årsag, bliver brugeren spurgt, om det er i orden også at sende dokumentet sammen med kaldstakken. Brugerne kan foretage et informeret valg til dette spørgsmål. It-administratorer kan have strenge krav vedrørende overførsel af dokumenter og kan på vegne af brugeren træffe beslutningen om aldrig at sende dokumenter. Følgende indstilling kan angives for at forhindre dokumenter i at blive sendt og for at undertrykke prompten til brugeren:
  
```defaults write com.microsoft.errorreporting IsAttachFilesEnabled -bool FALSE```

> [!NOTE]
> Hvis **SendAltTelemetriEnabled er indstillet** til **FALSK**, deaktiveres al rapportering om nedbrud for den pågældende proces. Hvis du vil aktivere rapportering om nedbrud uden at sende forbrugsdatatelemetri, kan følgende indstilling angives: ```defaults write com.microsoft.errorreporting IsMerpEnabled -bool TRUE``` 
  
### <a name="updates"></a>Opdateringer
  
Microsoft udgiver Office til Mac opdateringer med jævne mellemrum (typisk en gang om måneden). Vi anbefaler på det kraftigste, at brugere og it-administratorer holder deres computere opdateret for at sikre, at de nyeste sikkerhedsopdateringer er installeret. I tilfælde hvor it-administratorer ønsker at følge og administrere opdateringer på en computer tæt, kan følgende indstilling angives for at forhindre Automatiske opdateringer i automatisk at registrere og tilbyde produktopdateringer:
  
```defaults write com.microsoft.autoupdate2 HowToCheck -string 'Manual'```

### <a name="blocking-requests-with-a-firewallproxy"></a>Blokering af anmodninger med en firewall/proxy
  
Hvis din organisation blokerer anmodninger til URL-adresser via en firewall eller proxyserver, skal du sørge for at konfigurere de URL-adresser, der er angivet i dokumentet, som enten tilladte eller blokere, der er angivet med et 40X-svar (f.eks. 403 eller 404). Et 40X-svar gør det muligt for Office-programmerne på problemfrit at acceptere den manglende adgang til ressourcen, og det giver en hurtigere brugeroplevelse end blot at opgive forbindelsen, hvilket igen får klienten til at forsøge igen.
  
Hvis din proxyserver kræver godkendelse, returneres et 407-svar til klienten. Du får den bedste oplevelse ved at sikre, at du bruger Office til Mac builds 15.27 eller nyere, da de indeholder specifikke rettelser til at arbejde med NTLM- og Kerberos-servere.
  
  
## <a name="see-also"></a>Se også

[Office 365-URL-adresser og IP-adresseintervaller](urls-and-ip-address-ranges.md)

