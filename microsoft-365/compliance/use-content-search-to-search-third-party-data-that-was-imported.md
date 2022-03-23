---
title: Brug indholdssøgning til at søge efter importerede data fra tredjeparter
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
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
description: Brug værktøjet eDiscovery til indholdssøgning til at søge efter elementer, der er importeret til postkasser i Microsoft 365 fra en tredjepartsdatakilde ved at oprette forespørgsler.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 068a6e3164154129ba9148b41138d50c518042ed
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63587917"
---
# <a name="use-content-search-to-search-third-party-data-imported-by-a-custom-partner-connector"></a>Brug indholdssøgning til at søge efter tredjepartsdata importeret af en brugerdefineret partnerforbindelse

Du kan bruge værktøjet [eDiscovery-indholdssøgning](content-search.md) i Microsoft 365 Overholdelsescenter til at søge efter elementer, der er importeret til postkasser Microsoft 365 fra en tredjepartsdatakilde. Du kan oprette en forespørgsel for at søge i alle importerede dataelementer fra tredjeparter, eller du kan oprette en forespørgsel for at søge efter bestemte tredjepartsdataelementer. Du kan også oprette en forespørgselsbaseret opbevaringspolitik eller en forespørgselsbaseret eDiscovery-venteposition for at bevare tredjepartsdata.
  
Hvis du vil have mere at vide om at arbejde med en partner om at importere tredjepartsdata og en liste over de tredjepartsdatatyper, du kan importere til Microsoft 365, skal du se Arbejde sammen med en partner om at arkivere [tredjepartsdata i Office 365](work-with-partner-to-archive-third-party-data.md).

> [!IMPORTANT]
> Vejledningen i denne artikel gælder kun for tredjepartsdata, der blev importeret af en brugerdefineret partnerforbindelse. Denne artikel gælder ikke for tredjepartsdata, der importeres ved hjælp af [tredjepartsdataforbindelser](archiving-third-party-data.md#third-party-data-connectors) i Microsofts overholdelsescenter.
  
## <a name="creating-a-query-to-search-all-third-party-data"></a>Oprette en forespørgsel for at søge i alle tredjepartsdata

Hvis du vil søge (eller placere i venteposition) en hvilken som helst type tredjepartsdata, du har importeret til Office 365, `kind:externaldata` kan du bruge parret med egenskabsværdier i nøgleordsfeltet for en indholdssøgning eller ved oprettelse af en forespørgselsbaseret venteposition. Hvis du f.eks. vil søge efter elementer, der er importeret fra en datakilde fra en tredjepart, og som indeholder ordet "contoso" i egenskaben Emne for det importerede element, skal du bruge følgende forespørgsel: 
  
```powershell
kind:externaldata AND subject:contoso
```

Eksemplet med den forrige nøgleordsforespørgsel indeholder emneegenskaben. Du kan finde en liste over andre egenskaber for dataelementer fra tredjepart, som kan indgå i en nøgleordsforespørgsel, i afsnittet "Flere oplysninger" i Arbejd sammen med en partner om at arkivere [tredjepartsdata i Office 365](work-with-partner-to-archive-third-party-data.md#more-information).
  
Når du opretter forespørgsler til at søge efter og holde tredjepartsdata nede, kan du også bruge betingelser til at indsnævre søgeresultaterne. Du kan finde flere oplysninger om oprettelse af forespørgsler om indholdssøgning [i Nøgleordsforespørgsler og søgebetingelser for indholdssøgning](keyword-queries-and-search-conditions.md).
  
## <a name="creating-a-query-to-search-specific-types-of-third-party-data"></a>Oprette en forespørgsel for at søge efter bestemte typer tredjepartsdata

I stedet for at søge i alle typer tredjepartsdata kan du oprette forespørgsler, der kun søger efter en bestemt type tredjepartsdata ved hjælp af følgende meddelelsesegenskab *:* værdipar i nøgleordsfeltet for en indholdssøgning:
  
```powershell
itemclass:ipm.externaldata.<third-party data type>* 
```

Hvis du f.eks. vil søge efter Facebook-data, der indeholder ordet "contoso" i egenskaben Emne, skal du bruge følgende forespørgsel:
  
```powershell
itemclass:ipm.externaldata.Facebook* AND subject:contoso
```

I følgende tabel vises de tredjepartsdatatyper, du kan søge efter, og den værdi, der skal bruges til  `itemclass:` meddelelsesegenskaben til specifikt at søge efter den pågældende type tredjepartsdata. Der er ikke store og små bogstaver i forespørgselssyntaksen. 
  
|**Tredjepartsdatatype**|**Værdi for  `itemclass:` egenskab**|
|:-----|:-----|
|AIM  <br/> | `ipm.externaldata.AIM*` <br/> |
|American American – 2010  <br/> | `ipm.externaldata.AmericanIdol*` <br/> |
|AOL med Pivot-klient  <br/> | `ipm.externaldata.Pivot.IM` <br/> |
|Apple Juice  <br/> | `ipm.externaldata.AppleJuice*` <br/> |
|Ares  <br/> | `ipm.externaldata.Ares*` <br/> |
|Akser krypteret  <br/> | `ipm.externaldata.AxsEncrypted*` <br/> |
|Akser Exchange  <br/> | `ipm.externaldata.AxsExchange*` <br/> |
|Det lokale axs-arkiv  <br/> | `ipm.externaldata.AxsLocalArchive*` <br/> |
|Axs-pladsholder  <br/> | `ipm.externaldata.AxsPlaceHolder*` <br/> |
|Akser signeret  <br/> | `ipm.externaldata.AxsSigned*` <br/> |
|Bazaarvoice  <br/> | `ipm.externaldata.Bazaarvoice*` <br/> |
|Bearshare  <br/> | `ipm.externaldata.Bearshare*` <br/> |
|BitTorrent  <br/> | `ipm.externaldata.BitTorrent*` <br/> |
|BlackBerry  <br/> | `ipm.externaldata.Blackberry*` <br/> |
|BlackBerry-opkaldslogfiler  <br/> | `ipm.externaldata.BlackBerryCall*` <br/> |
|BlackBerry Messenger  <br/> | `ipm.externaldata.BlackBerryMessenger*` <br/> |
|Pinkode til BlackBerry  <br/> | `ipm.externaldata.BlackBerryPIN*` <br/> |
|BlackBerry-sms  <br/> | `ipm.externaldata.BlackBerrySMS*` <br/> |
|Bloomberg  <br/> | `ipm.externaldata.Bloomberg*` <br/> |
|Bloomberg-meddelelse  <br/> | `ipm.externaldata.conversation.Bloomberg Message*` <br/> |
|Bloomberg Messaging  <br/> | `ipm.externaldata.BloombergMessaging*` <br/> |
|Box  <br/> | `ipm.externaldata.Box*` <br/> |
|Cisco IM &amp; Presence Server  <br/> | `ipm.externaldata.Jabber.IM` <br/> |
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
|GoToMyPC  <br/> | `ipm.externaldata.GoToMyPC*` <br/> |
|HipChat  <br/> | `ipm.externaldata.HipChat*` <br/> |
|Hopster  <br/> | `ipm.externaldata.Hopster*` <br/> |
|HubConnex  <br/> | `ipm.externaldata.HubConnex*` <br/> |
|IBM Connections  <br/> | `ipm.externaldata.Connections*` <br/> |
|IBM SameTime  <br/> | `ipm.externaldata.Sametime*` <br/> |
|ICE Chat  <br/> | `ipm.externaldata.conversation.Ice Chat*` <br/> |
|Indii Messenger  <br/> | `ipm.externaldata.Indii*` <br/> |
|Eller Ellers  <br/> | `ipm.externaldata.Instagram*` <br/> |
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
|MySpace  <br/> | `ipm.externaldata.MySpace*` <br/> |
|NEONetwork  <br/> | `ipm.externaldata.NEONetwork*` <br/> |
|OpenNap  <br/> | `ipm.externaldata.OpenNap*` <br/> |
|Pinterest  <br/> | `ipm.externaldata.Pinterest*` <br/> |
|Pivot  <br/> | `ipm.externaldata.Pivot*` <br/> |
|QQ  <br/> | `ipm.externaldata.QQ*` <br/> |
|Microsoft SharePoint  <br/> | `ipm.externaldata.SharePoint*` <br/> |
|Salesforce Chatter  <br/> | `ipm.externaldata.Chatter*` <br/> |
|Skype for Business  <br/> | `ipm.externaldata.Skype*` <br/> |
|Slæk i virksomhedsgitter  <br/> | `ipm.externaldata.Slack.IM` <br/> |
|SoftEther  <br/> | `ipm.externaldata.SoftEther*` <br/> |
|Squawker  <br/> | `ipm.externaldata.Squawker*` <br/> |
|Ikke-for-store  <br/> | `ipm.externaldata.Symphony*` <br/> |
|Tutoson Reuters  <br/> | `ipm.externaldata.Reuters*` <br/> |
| Tutoson Reuters Eikon Messenger  <br/> | `ipm.externaldata.ReutersEikon*` <br/> |
|Tor  <br/> | `ipm.externaldata.Tor*` <br/> |
|TTT  <br/> | `ipm.externaldata.TTT*` <br/> |
|Twitter  <br/> | `ipm.externaldata.Twitter*` <br/> |
|UBS-chat  <br/> | `ipm.externaldata.UBS*` <br/> |
|Vimeo  <br/> | `ipm.externaldata.Vimeo*` <br/> |
|WinMX  <br/> | `ipm.externaldata.WinMX*` <br/> |
|Winny  <br/> | `ipm.externaldata.Winny*` <br/> |
|Yahoo!  <br/> | `ipm.externaldata.Yahoo!*` <br/> |
|Yammer  <br/> | `ipm.externaldata.Yammer*` <br/> |
|YellowFileet  <br/> | `ipm.externaldata.YellowJacket*` <br/> |
|YouTube  <br/> | `ipm.externaldata.YouTube*` <br/> |
