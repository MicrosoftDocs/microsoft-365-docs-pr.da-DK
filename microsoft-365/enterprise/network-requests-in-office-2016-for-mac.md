---
title: Netværksanmodninger i Office til Mac
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: I denne artikel beskrives det, hvilke slutpunkter og URL-adresser Office til Mac programmer forsøger at oprette forbindelse til, og hvilke tjenester der leveres.
ms.openlocfilehash: 477225cf99ead3f5609c8082644293d4ac006603
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091121"
---
# <a name="network-requests-in-office-for-mac"></a>Netværksanmodninger i Office til Mac

Office til Mac programmer giver en indbygget appoplevelse på macOS-platformen. Hver app er designet til at fungere i en række forskellige scenarier, herunder tilstande, når der ikke er nogen tilgængelig netværksadgang. Når en computer har forbindelse til et netværk, opretter programmerne automatisk forbindelse til en række webbaserede tjenester for at levere forbedret funktionalitet. Følgende oplysninger beskriver, hvilke slutpunkter og URL-adresser programmerne forsøger at oprette forbindelse til, og hvilke tjenester der leveres. Disse oplysninger er nyttige, når du skal foretage fejlfinding af problemer med netværkskonfiguration og angive politikker for netværksproxyservere. Oplysningerne i denne artikel er beregnet til at supplere [artiklen Office 365 URL-adresse og adresseområder](urls-and-ip-address-ranges.md), som indeholder slutpunkter for computere, der kører Microsoft Windows. Medmindre det er angivet, gælder oplysningerne i denne artikel også for Office 2019 til Mac og Office 2016 til Mac, som er tilgængelige som et engangskøb fra en detailbutik eller via en volumenlicensaftale. 

  
De fleste af denne artikel indeholder tabeller med oplysninger om url-adresser, type og beskrivelse af tjenesten eller funktionen, der leveres af det pågældende slutpunkt. Hver af de Office apps kan variere i brugen af tjenesten og slutpunktet. Følgende apps er defineret i nedenstående tabeller:
  
- W: Word
- P: PowerPoint
- X: Excel
- O: Outlook
- N: OneNote
   
URL-typen er defineret på følgende måde:
  
- ST: Static – URL-adressen er hard-coded i klientprogrammet.
    
- SS: Semi-Static – URL-adressen er kodet som en del af en webside eller omdirigering.
    
- CS: Config Service – URL-adressen returneres som en del af Office Configuration Service.

    
## <a name="office-for-mac-default-configuration"></a>Office til Mac standardkonfiguration

 **Installation og opdateringer**
  
Følgende netværksslutpunkter bruges til at downloade Office til Mac installationsprogrammet fra Microsoft Content Delivery Network (CDN).
  
|**URL**|**Type**|**Beskrivelse**|
|:-----|:-----|:-----|
|```https://go.microsoft.com/fwlink/```  <br/> |ST  <br/> |Microsoft 365 tjeneste til videresendelse af links på installationsportalen til de nyeste installationspakker.  <br/> |
|```https://officecdn-microsoft-com.akamaized.net/```  <br/> |SS  <br/> |Placering af installationspakker på Content Delivery Network.  <br/> |
|```https://officecdn.microsoft.com/```  <br/> |SS  <br/> |Placering af installationspakker på Content Delivery Network.  <br/> |
|```https://officeci-mauservice.azurewebsites.net/```  <br/> |ST  <br/> |Slutpunkt for styringskontrol for Microsoft Automatiske opdateringer  <br/> |
   
 **Første appstart**
  
Følgende netværksslutpunkter kontaktes, første gang en Office-app startes. Disse slutpunkter indeholder forbedret Office funktionalitet for brugere, og URL-adresserne kontaktes, uanset licenstype (herunder installationer af volumenlicens).
  
|**URL**|**Apps**|**Type**|**Beskrivelse**|
|:-----|:-----|:-----|:-----|
|```https://config.edge.skype.com/```  <br/> |WXPON  <br/> |ST  <br/> |Konfiguration af "flighting" – giver mulighed for funktionslysning og eksperimentering.  <br/> |
|```https://ocos-office365-s2s.msedge.net/```  <br/> |WXPON  <br/> |ST  <br/> |'Flighting' Netværkskonfigurationstest  <br/> |
|```https://client-office365-tas.msedge.net/```  <br/> |WXPON  <br/> |ST  <br/> |'Flighting' Netværkskonfigurationstest  <br/> |
|```https://officeclient.microsoft.com/```  <br/> |WXPON  <br/> |ST  <br/> |Office Configuration Service – Masterliste over tjenesteslutpunkter.  <br/> |
|```https://nexusrules.officeapps.live.com/```  <br/> |WXPON  <br/> |ST  <br/> |Office Download af regler Telemetri – Informerer klienten om, hvilke data og hændelser der skal uploades til telemetritjenesten.  <br/> |
|```https://mobile.pipe.aria.microsoft.com/```  <br/> |N  <br/> |CS  <br/> |OneNote telemetritjeneste  <br/> |
|```https://nexus.officeapps.live.com/```  <br/> |WXPON  <br/> |ST  <br/> |Office Telemetri Upload Rapportering – "Heartbeart", og fejlhændelser, der opstår på klienten, uploades til telemetritjenesten.  <br/> |
|```https://templateservice.office.com/```  <br/> |WXP  <br/> |CS  <br/> |Office Skabelontjeneste – Giver brugerne mulighed for at bruge onlinedokumentskabeloner.  <br/> |
|```https://omextemplates.content.office.net/```  <br/> |WXP  <br/> |CS  <br/> |Office downloads af skabeloner – Storage af PNG-skabelonbilleder.  <br/> |
|```https://store.office.com/```  <br/> |WXP  <br/> |CS  <br/> |Store konfiguration af Office apps.  <br/> |
|```https://odc.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |Office Katalog over dokumentintegrationstjenester (liste over tjenester og slutpunkter) og Registrering af hjemmerige.  <br/> |
|```https://cdn.odc.officeapps.live.com/```  <br/> |WXPON  <br/> |CS  <br/> |Ressourcer til registrering af hjemmeressourcer v2 (15.40 og nyere)  <br/> |
|```https://officecdn.microsoft.com/```  <br/> |WXPON  <br/> |ST  <br/> |Microsoft AutoUpdate-manifester – kontrollerer, om der er opdateringer tilgængelige  <br/> |
|```https://ajax.aspnetcdn.com/```  <br/> |WXPO  <br/> |SS  <br/> |Microsoft Ajax JavaScript-bibliotek  <br/> |
|```https://wikipedia.firstpartyapps.oaspapps.com/```  <br/> |W  <br/> |SS  <br/> |Wikipedia-app til Office konfiguration og ressourcer.  <br/> |
|```https://excelbingmap.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |SS  <br/> |Bing Tilknyt app for Office konfiguration og ressourcer.  <br/> |
|```https://peoplegraph.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |SS  <br/> |Folk Graph app til Office konfiguration og ressourcer.  <br/> |
|```https://www.onenote.com/```  <br/> |N  <br/> |ST  <br/> |Nyheder i OneNote.  <br/> |
|```https://site-cdn.onenote.net/```  <br/> |N  <br/> |ST  <br/> |Nyt indhold til OneNote.  <br/> |
|```https://site-cdn.onenote.net/```  <br/> |N  <br/> |SS  <br/> |Nyheder i billeder til OneNote.  <br/> |
|```https://acompli.helpshift.com/```  <br/> |O  <br/> |ST  <br/> |Supporttjeneste i appen.  <br/> |
|```https://prod-global-autodetect.acompli.net/```  <br/> |O  <br/> |ST  <br/> |Tjenesten Til registrering af mailkonto.  <br/> |
|```https://autodiscover-s.outlook.com/```  <br/> |WXPO  <br/> |ST  <br/> |Outlook AutoDiscovery  <br/> |
|```https://outlook.office365.com/```  <br/> |WXPO  <br/> |ST  <br/> |Outlook slutpunkt for Microsoft 365 tjeneste.  <br/> |
|```https://r1.res.office365.com/```  <br/> |O  <br/> |ST  <br/> |Ikoner for Outlook tilføjelsesprogrammer.  <br/> |
   
> [!NOTE]
> Office Configuration Service fungerer som en automatisk registreringstjeneste for alle Microsoft Office klienter, ikke kun til Mac. De slutpunkter, der returneres i svaret, er semi-statiske i denne ændring er meget sjældne, men stadig mulige. 
  
 **Log på**
  
Følgende netværksslutpunkter kontaktes, når du logger på et cloudbaseret lager. Afhængigt af din kontotype kan der kontaktes forskellige tjenester. Eksempel:
  
- **MSA: Microsoft-konto** – bruges typisk til forbruger- og detailscenarier 
    
- **OrgID: Organisationskonto** – bruges typisk til kommercielle scenarier 
    
|**URL**|**Apps**|**Type**|**Beskrivelse**|
|:-----|:-----|:-----|:-----|
|```https://login.windows.net/```  <br/> |WXPON  <br/> |ST  <br/> |Windows godkendelsestjeneste  <br/> |
|```https://login.microsoftonline.com/```  <br/> |WXPON  <br/> |ST  <br/> |Microsoft 365 logontjeneste (OrgID)  <br/> |
|```https://login.live.com/```  <br/> |WXPON  <br/> |ST  <br/> |Microsoft-kontologontjeneste (MSA)  <br/> |
|```https://auth.gfx.ms/```  <br/> |WXPON  <br/> |CS  <br/> |MSA (Microsoft Account Login Service Helper)  <br/> |
|```https://secure.aadcdn.microsoftonline-p.com/```  <br/> |WXPON  <br/> |SS  <br/> |Microsoft 365 Branding af logon (OrgID)  <br/> |
|```https://ocws.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |Dokument og steder Storage søger  <br/> |
|```https://roaming.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |Senest anvendte dokumenttjeneste (MRU)  <br/> |
   
> [!NOTE]
> For abonnementsbaserede licenser og detaillicenser aktiverer logon både produktet og giver adgang til cloudressourcer, f.eks. OneDrive. I forbindelse med installationer af volumenlicenser bliver brugerne stadig bedt om at logge på (som standard), men det er kun påkrævet for at få adgang til cloudressourcer, da produktet allerede er aktiveret. 
  
 **Produktaktivering**
  
Følgende netværksslutpunkter gælder for aktivering af Microsoft 365-abonnement og detaillicens. Dette gælder IKKE specifikt for volumenlicensinstallationer.
  
|**URL**|**Apps**|**Type**|**Beskrivelse**|
|:-----|:-----|:-----|:-----|
|```https://ols.officeapps.live.com/```  <br/> |WXPON  <br/> |CS  <br/> |Office-licenstjeneste  <br/> |
   
 **Nyheder**
  
Følgende netværksslutpunkter gælder kun for Microsoft 365 Abonnement.
  
|**URL**|**Apps**|**Type**|**Beskrivelse**|
|:-----|:-----|:-----|:-----|
|```https://contentstorage.osi.office.net/```  <br/> |WXPO  <br/> |SS  <br/> |Indhold på JSON-siden Nyheder.  <br/> |
   
 **Researcher**
  
Følgende netværksslutpunkter gælder kun for Microsoft 365 Abonnement.
  
|**URL**|**Apps**|**Type**|**Beskrivelse**|
|:-----|:-----|:-----|:-----|
|```https://entity.osi.office.net/```  <br/> |W  <br/> |CS  <br/> |Researcher Web Service  <br/> |
|```https://cdn.entity.osi.office.net/```  <br/> |W  <br/> |CS  <br/> |Statisk indhold til researcher  <br/> |
|```https://www.bing.com/```  <br/> |W  <br/> |CS  <br/> |Udbyder af forskningsindhold  <br/> |
   
 **Smart opslag**
  
Følgende netværksslutpunkter gælder for både aktivering af Microsoft 365-abonnement og detail-/volumenlicens.
  
|**URL**|**Apps**|**Type**|**Beskrivelse**|
|:-----|:-----|:-----|:-----|
|```https://uci.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |Insights webtjeneste  <br/> |
|```https://ajax.googleapis.com/```  <br/> |WXPN  <br/> |CS  <br/> |JQuery-bibliotek  <br/> |
|```https://cdnjs.cloudflare.com/```  <br/> |WXPN  <br/> |CS  <br/> |Understøttende JavaScript-bibliotek  <br/> |
|```https://www.bing.com/```  <br/> |WXPN  <br/> |CS  <br/> |Insights indholdsudbyder  <br/> |
|```https://tse1.mm.bing.net/```  <br/> |WXPN  <br/> |CS  <br/> |Insights indholdsudbyder  <br/> |
   
 **PowerPoint Designer**
  
Følgende netværksslutpunkter gælder kun for Microsoft 365 Abonnement.
  
|**URL**|**Apps**|**Type**|**Beskrivelse**|
|:-----|:-----|:-----|:-----|
|```https://pptsgs.officeapps.live.com/```  <br/> |P  <br/> |CS  <br/> |PowerPoint Designer-webtjeneste  <br/> |
   
 **PowerPoint Hurtigstarter**
  
Følgende netværksslutpunkter gælder kun for Microsoft 365 Abonnement.
  
|**URL**|**Apps**|**Type**|**Beskrivelse**|
|:-----|:-----|:-----|:-----|
|```https://pptcts.officeapps.live.com/```  <br/> |P  <br/> |CS  <br/> |PowerPoint Webtjeneste til hurtig start  <br/> |
   
 **Send en smiley/pande**
  
Følgende netværksslutpunkter gælder for både aktivering af Microsoft 365-abonnement og detail-/volumenlicens.
  
|**URL**|**Apps**|**Type**|**Beskrivelse**|
|:-----|:-----|:-----|:-----|
|```https://sas.office.microsoft.com/```  <br/> |WXPON  <br/> |CS  <br/> |Send en smiley  <br/> |
   
 **Kontakt support**
  
Følgende netværksslutpunkter gælder for både aktivering af Microsoft 365-abonnement og detail-/volumenlicens.
  
|**URL**|**Apps**|**Type**|**Beskrivelse**|
|:-----|:-----|:-----|:-----|
|```https://powerlift-frontdesk.acompli.net/```  <br/> |O  <br/> |CS  <br/> |Kontakt supporttjenesten  <br/> |
|```https://acompli.helpshift.com/```  <br/> |O  <br/> |CS  <br/> |Supporttjeneste i appen  <br/> |
   
 **Gem som PDF**
  
Følgende netværksslutpunkter gælder for både aktivering af Microsoft 365-abonnement og detail-/volumenlicens.
  
|**URL**|**Apps**|**Type**|**Beskrivelse**|
|:-----|:-----|:-----|:-----|
|```https://wordcs.officeapps.live.com/```  <br/> |W  <br/> |CS  <br/> |Tjenesten Word-dokumentkonvertering (PDF)  <br/> |
   
 **Office apps (også kaldet tilføjelsesprogrammer)**
  
Følgende netværksslutpunkter gælder for både Microsoft 365-abonnements- og detail-/volumenlicensaktivering, når der er tillid til Office apptilføjelsesprogram.
  
|**URL**|**Apps**|**Type**|**Beskrivelse**|
|:-----|:-----|:-----|:-----|
|```https://store.office.com/```  <br/> |WXPO  <br/> |CS  <br/> |Office-app lagerkonfiguration  <br/> |
|```https://wikipedia.firstpartyapps.oaspapps.com/```  <br/> |W  <br/> |SS  <br/> |Ressourcer til Wikipedia-app  <br/> |
|```https://excelbingmap.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |SS  <br/> |Bing Afbild appressourcer  <br/> |
|```https://peoplegraph.firstpartyapps.oaspapps.com```  <br/> |X  <br/> |SS  <br/> |Personer Graph appressourcer  <br/> |
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
  
Følgende netværksslutpunkt gælder kun for alle Office programmer til Microsoft 365 Abonnement.
  
|**URL**|**Type**|**Beskrivelse**|
|:-----|:-----|:-----|
|```https://*.oscs.protection.outlook.com/```  <br/> |CS  <br/> |Microsoft Pengeskab Link Service  <br/> |
   
 **Rapportering om nedbrud**
  
Følgende netværksslutpunkt gælder for alle Office programmer for både Microsoft 365 abonnements- og detail-/volumenlicensaktivering. Når en proces uventet går ned, genereres en rapport, som sendes til Watson-tjenesten.
  
|**URL**|**Type**|**Beskrivelse**|
|:-----|:-----|:-----|
|```https://watson.microsoft.com/```  <br/> |ST  <br/> |Microsoft Fejlrapporteringstjeneste  <br/> |
|```https://officeci.azurewebsites.net/```  <br/> |ST  <br/> |Office samarbejdsbaseret Insights tjeneste  <br/> |
   
## <a name="options-for-reducing-network-requests-and-traffic"></a>Muligheder for at reducere netværksanmodninger og trafik

Standardkonfigurationen af Office til Mac giver den bedste brugeroplevelse, både med hensyn til funktionalitet og for at holde computeren opdateret. I nogle scenarier vil du måske forhindre programmer i at kontakte netværksslutpunkter. I dette afsnit beskrives mulighederne for at gøre det.
  
 ### <a name="disabling-cloud-sign-in-and-office-add-ins"></a>Deaktivering af Cloud Sign-In og Office Add-Ins
  
Kunder med volumenlicens kan have strenge politikker om lagring af dokumenter på skybaseret lager. Følgende indstillinger pr. program kan angives til at deaktivere MSA/OrgID Logon og adgang til Office tilføjelsesprogrammer.
  
- ```defaults write com.microsoft.Word UseOnlineContent -integer 0```

- ```defaults write com.microsoft.Excel UseOnlineContent -integer 0```

- ```defaults write com.microsoft.Powerpoint UseOnlineContent -integer 0```

Hvis brugerne forsøger at få adgang til funktionen Sign-In, får de vist en fejl om, at der ikke findes en netværksforbindelse. Da denne indstilling også blokerer for onlineproduktaktivering, bør den kun bruges til volumenlicensinstallationer. Hvis du bruger denne indstilling, vil det specifikt forhindre Office programmer i at få adgang til følgende slutpunkter:
  
- ```https://odc.officeapps.live.com```
    
- ```https://*.firstpartyapps.oaspapps.com```
    
- Alle slutpunkter, der er angivet i afsnittet 'Log på' ovenfor.
    
- Alle slutpunkter, der er angivet i afsnittet 'Smart opslag' ovenfor.
    
- Alle slutpunkter, der er angivet i afsnittet 'Produktaktivering' ovenfor.
    
- Alle slutpunkter, der er angivet i afsnittet 'Office Apps (også kaldet tilføjelsesprogrammer)' ovenfor.
    
Hvis du vil genoprette fuld funktionalitet for brugeren, skal du enten angive indstillingen til '2' eller fjerne den.
  
> [!NOTE]
> Denne indstilling kræver Office til Mac build 15.25 [160726] eller nyere. 
  
### <a name="telemetry"></a>Telemetri 
  
Office til Mac sender med jævne mellemrum telemetrioplysninger tilbage til Microsoft. Data uploades til slutpunktet 'Nexus'. Telemetridataene hjælper teknikerteamet med at vurdere tilstanden og eventuelle uventede funktionsmåder for hver Office-app. Der er to kategorier af telemetri:
  
- **Impulsen** indeholder oplysninger om version og licens. Disse data sendes umiddelbart efter appstart. 
    
- **Brug** indeholder oplysninger om, hvordan apps bruges, og ikke-alvorlige fejl. Disse data sendes hvert 60. minut. 
    
Microsoft tager dine personlige oplysninger meget alvorligt. Du kan læse om Microsofts politik for dataindsamling på [https://privacy.microsoft.com](https://privacy.microsoft.com). Hvis du vil forhindre programmer i at sende 'Usage'-telemetri, kan indstillingen **SendAllTelemetryEnabled** justeres. Indstillingen er pr. program og kan angives via macOS-konfigurationsprofiler eller manuelt fra Terminal: 
  
```defaults write com.microsoft.Word SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Excel SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Powerpoint SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Outlook SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.onenote.mac SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.autoupdate2 SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Office365ServiceV2 SendAllTelemetryEnabled -bool FALSE```

Impulstelemetri sendes altid og kan ikke deaktiveres.
  
### <a name="crash-reporting"></a>Rapportering om nedbrud
  
Når der opstår en alvorlig programfejl, afsluttes programmet uventet og uploader en nedbrudsrapport til tjenesten 'Watson'. Nedbrudsrapporten består af en kaldstak, som er listen over trin, som programmet har behandlet op til nedbruddet. Disse trin hjælper teknikerteamet med at identificere den nøjagtige funktion, der mislykkedes, og hvorfor.
  
I nogle tilfælde medfører indholdet af et dokument, at programmet går ned. Hvis appen identificerer dokumentet som årsagen, bliver brugeren spurgt, om det er i orden også at sende dokumentet sammen med opkaldsstakken. Brugerne kan foretage et informeret valg til dette spørgsmål. It-administratorer kan have strenge krav til overførsel af dokumenter og træffe beslutning på vegne af brugeren om aldrig at sende dokumenter. Følgende indstilling kan angives for at forhindre, at dokumenter sendes, og for at undertrykke prompten til brugeren:
  
```defaults write com.microsoft.errorreporting IsAttachFilesEnabled -bool FALSE```

> [!NOTE]
> Hvis **SendAllTelemetryEnabled** er angivet til **FALSK**, er al rapportering om nedbrud for den pågældende proces deaktiveret. Hvis du vil aktivere rapportering om nedbrud uden at sende brugstelemetri, kan du angive følgende indstilling: ```defaults write com.microsoft.errorreporting IsMerpEnabled -bool TRUE``` 
  
### <a name="updates"></a>Opdateringer
  
Microsoft udgiver Office til Mac opdateringer med jævne intervaller (typisk én gang om måneden). Vi opfordrer på det kraftigste brugere og it-administratorer til at holde maskiner opdateret for at sikre, at de nyeste sikkerhedsrettelser installeres. I de tilfælde, hvor it-administratorer ønsker nøje at styre og administrere computeropdateringer, kan følgende indstillinger angives for at forhindre, at Automatiske opdateringer automatisk registrerer og tilbyder produktopdateringer:
  
```defaults write com.microsoft.autoupdate2 HowToCheck -string 'Manual'```

### <a name="blocking-requests-with-a-firewallproxy"></a>Blokering af anmodninger med en firewall/proxy
  
Hvis din organisation blokerer anmodninger til URL-adresser via en firewall eller proxyserver, skal du sørge for at konfigurere de URL-adresser, der er angivet i dette dokument, som enten tilladt eller blokere angivet med et 40X-svar (f.eks. 403 eller 404). Et 40X-svar gør det muligt for Office programmer at acceptere den manglende adgang til ressourcen på en elegant måde, og det giver en hurtigere brugeroplevelse end blot at slippe forbindelsen, hvilket igen får klienten til at prøve igen.
  
Hvis proxyserveren kræver godkendelse, returneres der et 407-svar til klienten. Du får den bedste oplevelse ved at sikre, at du bruger Office til Mac builds 15.27 eller nyere, da de indeholder specifikke rettelser til at arbejde med NTLM- og Kerberos-servere.
  
  
## <a name="see-also"></a>Se også

[Office 365-URL-adresser og IP-adresseintervaller](urls-and-ip-address-ranges.md)

