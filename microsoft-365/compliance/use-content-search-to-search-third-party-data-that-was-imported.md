---
title: Brug indholdssøgning til at søge efter importerede data fra tredjepart
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.collection: M365-security-compliance
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: ec2677ff-c4d7-4363-a9e7-22c80e015688
description: Brug eDiscovery-værktøjet til indholdssøgning til at søge efter elementer, der er importeret til postkasser i Microsoft 365 fra en datakilde fra en tredjepart, ved at oprette forespørgsler.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 73967c8897ee0fd5143b8e15dfe8874fc0c85755
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65095394"
---
# <a name="use-content-search-to-search-third-party-data-imported-by-a-custom-partner-connector"></a>Brug indholdssøgning til at søge efter tredjepartsdata, der er importeret af en brugerdefineret partnerconnector

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Du kan bruge [eDiscovery-værktøjet til indholdssøgning](content-search.md) på Microsoft Purview-overholdelsesportalen til at søge efter elementer, der er importeret til postkasser i Microsoft 365 fra en datakilde fra en tredjepart. Du kan oprette en forespørgsel for at søge i alle importerede dataelementer fra tredjepart, eller du kan oprette en forespørgsel for at søge efter bestemte dataelementer fra tredjepart. Du kan også oprette en forespørgselsbaseret opbevaringspolitik eller en forespørgselsbaseret eDiscovery-venteposition for at bevare tredjepartsdata.
  
Du kan få flere oplysninger om, hvordan du arbejder med en partner for at importere tredjepartsdata og en liste over de datatyper fra tredjepart, som du kan importere til Microsoft 365, [under Arbejd med en partner for at arkivere data fra tredjepart i Office 365](work-with-partner-to-archive-third-party-data.md).

> [!IMPORTANT]
> Vejledningen i denne artikel gælder kun for tredjepartsdata, der er importeret af en brugerdefineret partnerconnector. Denne artikel gælder ikke for tredjepartsdata, der importeres ved hjælp af [dataconnectors fra tredjepart](archiving-third-party-data.md#third-party-data-connectors) i Microsofts overholdelsescenter.
  
## <a name="creating-a-query-to-search-all-third-party-data"></a>Oprettelse af en forespørgsel til søgning i alle tredjepartsdata

Hvis du vil søge efter (eller sætte dem i venteposition) for alle typer tredjepartsdata, som du har importeret til Office 365, kan du bruge `kind:externaldata` meddelelsesegenskabsværdiparret i nøgleordsfeltet til en indholdssøgning, eller når du opretter en forespørgselsbaseret venteposition. Hvis du f.eks. vil søge efter elementer, der er importeret fra en hvilken som helst datakilde fra tredjepart og indeholde ordet "contoso" i egenskaben Subject for det importerede element, skal du bruge følgende forespørgsel: 
  
```powershell
kind:externaldata AND subject:contoso
```

Det forrige eksempel på nøgleordsforespørgslen indeholder emneegenskaben. Du kan se en liste over andre egenskaber for dataelementer fra tredjepart, der kan inkluderes i en nøgleordsforespørgsel, i afsnittet "Flere oplysninger" i [Arbejd med en partner for at arkivere tredjepartsdata i Office 365](work-with-partner-to-archive-third-party-data.md#more-information).
  
Når du opretter forespørgsler for at søge efter og indeholde tredjepartsdata, kan du også bruge betingelser til at indsnævre søgeresultaterne. Du kan finde flere oplysninger om oprettelse af indholdssøgningsforespørgsler under [Nøgleordsforespørgsler og søgebetingelser for indholdssøgning](keyword-queries-and-search-conditions.md).
  
## <a name="creating-a-query-to-search-specific-types-of-third-party-data"></a>Oprettelse af en forespørgsel for at søge efter bestemte typer tredjepartsdata

I stedet for at søge efter alle typer data fra tredjepart kan du oprette forespørgsler, der kun søger efter en angiv type tredjepartsdata ved hjælp af følgende *meddelelsesegenskab: værdipar* i nøgleordsfeltet for en indholdssøgning:
  
```powershell
itemclass:ipm.externaldata.<third-party data type>* 
```

Hvis du f.eks. vil søge efter Facebook-data, der indeholder ordet "contoso" i egenskaben Subject, skal du bruge følgende forespørgsel:
  
```powershell
itemclass:ipm.externaldata.Facebook* AND subject:contoso
```

I følgende tabel vises de datatyper fra tredjepart, som du kan søge efter, og den værdi, der skal bruges til meddelelsesegenskaben  `itemclass:` til specifikt at søge efter denne type tredjepartsdata. Der skelnes ikke mellem store og små bogstaver i forespørgselssyntaksen. 
  
|**Datatype fra tredjepart**|**Værdi for  `itemclass:` egenskab**|
|:-----|:-----|
|MÅL  <br/> | `ipm.externaldata.AIM*` <br/> |
|American Idol  <br/> | `ipm.externaldata.AmericanIdol*` <br/> |
|AOL med pivotklient  <br/> | `ipm.externaldata.Pivot.IM` <br/> |
|Æblejuice  <br/> | `ipm.externaldata.AppleJuice*` <br/> |
|Ares  <br/> | `ipm.externaldata.Ares*` <br/> |
|Akser krypteret  <br/> | `ipm.externaldata.AxsEncrypted*` <br/> |
|Akser Exchange  <br/> | `ipm.externaldata.AxsExchange*` <br/> |
|Akser lokalt arkiv  <br/> | `ipm.externaldata.AxsLocalArchive*` <br/> |
|Pladsholder til akser  <br/> | `ipm.externaldata.AxsPlaceHolder*` <br/> |
|Akser signeret  <br/> | `ipm.externaldata.AxsSigned*` <br/> |
|Basarvoice  <br/> | `ipm.externaldata.Bazaarvoice*` <br/> |
|Bearshare  <br/> | `ipm.externaldata.Bearshare*` <br/> |
|Bittorrent  <br/> | `ipm.externaldata.BitTorrent*` <br/> |
|Blackberry  <br/> | `ipm.externaldata.Blackberry*` <br/> |
|BlackBerry-opkaldslogge  <br/> | `ipm.externaldata.BlackBerryCall*` <br/> |
|BlackBerry Messenger  <br/> | `ipm.externaldata.BlackBerryMessenger*` <br/> |
|Pinkode til BlackBerry  <br/> | `ipm.externaldata.BlackBerryPIN*` <br/> |
|BlackBerry SMS  <br/> | `ipm.externaldata.BlackBerrySMS*` <br/> |
|Bloomberg  <br/> | `ipm.externaldata.Bloomberg*` <br/> |
|Meddelelse fra Bloomberg  <br/> | `ipm.externaldata.conversation.Bloomberg Message*` <br/> |
|Bloomberg Messaging  <br/> | `ipm.externaldata.BloombergMessaging*` <br/> |
|Boksen  <br/> | `ipm.externaldata.Box*` <br/> |
|Cisco IM-tilstedeværelsesserver &amp;  <br/> | `ipm.externaldata.Jabber.IM` <br/> |
|Cisco Jabber  <br/> | `ipm.externaldata.Jabber*` <br/> |
|CipherCloud til Salesforce Chatter  <br/> | `ipm.externaldata.Chatter.Post` <br/>  `ipm.externaldata.Chatter.Comment` <br/> |
|Direkte Forbind  <br/> | `ipm.externaldata.DirectConnect*` <br/> |
|Facebook  <br/> | `ipm.externaldata.Facebook*` <br/> |
|FastTrack  <br/> | `ipm.externaldata.FastTrack*` <br/> |
|FXConnect  <br/> | `ipm.externaldata.FXConnect.chat` <br/> |
|Flickr  <br/> | `ipm.externaldata.Flickr*` <br/> |
|Gnutella  <br/> | `ipm.externaldata.Gnutella*` <br/> |
|Google+  <br/> | `ipm.externaldata.GooglePlus*` <br/> |
|Google Talk  <br/> | `ipm.externaldata.GoogleTalk*` <br/> |
|Gå tilMitPC  <br/> | `ipm.externaldata.GoToMyPC*` <br/> |
|HipChat  <br/> | `ipm.externaldata.HipChat*` <br/> |
|Hopster  <br/> | `ipm.externaldata.Hopster*` <br/> |
|HubConnex  <br/> | `ipm.externaldata.HubConnex*` <br/> |
|IBM-forbindelser  <br/> | `ipm.externaldata.Connections*` <br/> |
|IBM SameTime  <br/> | `ipm.externaldata.Sametime*` <br/> |
|ICE Chat  <br/> | `ipm.externaldata.conversation.Ice Chat*` <br/> |
|Indii Messenger  <br/> | `ipm.externaldata.Indii*` <br/> |
|Instagram  <br/> | `ipm.externaldata.Instagram*` <br/> |
|Øjeblikkelig Bloomberg  <br/> | `ipm.externaldata.InstantBloomberg*` <br/> |
|InvestEdge  <br/> | `ipm.externaldata.InvestEdge*` <br/> |
|IRC  <br/> | `ipm.externaldata.IRC*` <br/> |
|Jive  <br/> | `ipm.externaldata.Jive*` <br/> |
|JiveApiRetention  <br/> | `ipm.externaldata.JiveApiRetention*` <br/> |
|JXTA  <br/> | `ipm.externaldata.JXTA*` <br/> |
|LinkedIn  <br/> | `ipm.externaldata.LinkedIn*` <br/> |
|MFTP  <br/> | `ipm.externaldata.MFTP*` <br/> |
|Microsoft UC  <br/> | `ipm.externaldata.MicrosoftUC*` <br/> |
|Mind Align  <br/> | `ipm.externaldata.MindAlign*` <br/> |
|Mobile Guard  <br/> | `ipm.externaldata.MobileGuard*` <br/> |
|MSN  <br/> | `ipm.externaldata.MSN*` <br/> |
|Myspace  <br/> | `ipm.externaldata.MySpace*` <br/> |
|NEONetwork  <br/> | `ipm.externaldata.NEONetwork*` <br/> |
|OpenNap  <br/> | `ipm.externaldata.OpenNap*` <br/> |
|Pinterest  <br/> | `ipm.externaldata.Pinterest*` <br/> |
|Pivot  <br/> | `ipm.externaldata.Pivot*` <br/> |
|QQ  <br/> | `ipm.externaldata.QQ*` <br/> |
|Microsoft SharePoint  <br/> | `ipm.externaldata.SharePoint*` <br/> |
|Salesforce-snak  <br/> | `ipm.externaldata.Chatter*` <br/> |
|Skype for Business  <br/> | `ipm.externaldata.Skype*` <br/> |
|Slack - virksomhedsgitter  <br/> | `ipm.externaldata.Slack.IM` <br/> |
|Blødere  <br/> | `ipm.externaldata.SoftEther*` <br/> |
|Squawker  <br/> | `ipm.externaldata.Squawker*` <br/> |
|Symphony  <br/> | `ipm.externaldata.Symphony*` <br/> |
|Thomson Reuters  <br/> | `ipm.externaldata.Reuters*` <br/> |
| Thomson Reuters Eikon Messenger  <br/> | `ipm.externaldata.ReutersEikon*` <br/> |
|Tor  <br/> | `ipm.externaldata.Tor*` <br/> |
|TTT  <br/> | `ipm.externaldata.TTT*` <br/> |
|Twitter  <br/> | `ipm.externaldata.Twitter*` <br/> |
|UBS-chat  <br/> | `ipm.externaldata.UBS*` <br/> |
|Vimeo  <br/> | `ipm.externaldata.Vimeo*` <br/> |
|Winmx  <br/> | `ipm.externaldata.WinMX*` <br/> |
|Winny  <br/> | `ipm.externaldata.Winny*` <br/> |
|Yahoo!  <br/> | `ipm.externaldata.Yahoo!*` <br/> |
|Yammer  <br/> | `ipm.externaldata.Yammer*` <br/> |
|Gul jakke  <br/> | `ipm.externaldata.YellowJacket*` <br/> |
|YouTube  <br/> | `ipm.externaldata.YouTube*` <br/> |
