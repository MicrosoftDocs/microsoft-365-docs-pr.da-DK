---
title: Brug af BGP-communities i ExpressRoute til Office 365 scenarier
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 6/26/2018
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099
description: Få mere at vide om, hvordan du bruger BGP-communities i Azure ExpressRoute til at administrere antallet af IP-præfikser og påkrævet båndbredde til Office 365 scenarier.
ms.openlocfilehash: 3e7ec6373299741cc1d34c18cc6be5b9366f3de6
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65095768"
---
# <a name="using-bgp-communities-in-expressroute-for-office-365-scenarios"></a>Brug af BGP-communities i ExpressRoute til Office 365 scenarier

Oprettelse af forbindelse til Office 365 ved hjælp af Azure ExpressRoute er baseret på BGP-reklamer for bestemte IP-undernet, der repræsenterer netværk, hvor Office 365 slutpunkter udrulles. På grund af den globale karakter af Office 365 og antallet af tjenester, der udgør Office 365, har kunderne ofte behov for at administrere de reklamer, de accepterer på deres netværk. Reducere antallet af IP-undernet; der refereres til som IP-præfikser i resten af denne artikel for at tilpasse sig terminologien for BGP-netværksadministration, opfylder følgende mål for kunderne:
  
- **Administrer det antal annoncerede IP-præfikser, der accepteres** – Kunder, der har en intern netværksinfrastruktur eller en netværksoperatør, som kun understøtter et begrænset antal IP-præfikser, og kunder, der har en netværksoperatør, der opkræver gebyrer for at acceptere præfikser over et begrænset antal, vil gerne evaluere det samlede antal præfikser, der allerede er annonceret på deres netværk, og vælge, hvilke Office 365 programmer der er bedst egnet til ExpressRoute.

- **Administrer den mængde båndbredde, der kræves i Azure ExpressRoute-kredsløbet** – Kunderne vil muligvis styre båndbreddekonvolutten for Office 365 tjenester via ExpressRoute-stien i forhold til internetstien. Dette giver kunderne mulighed for at reservere ExpressRoute-båndbredde for bestemte programmer, f.eks. Skype for Business og dirigere de resterende Office 365 programmer via internetstien.

For at hjælpe kunder med disse mål er Office 365 IP-præfikser, der annonceres via ExpressRoute, mærket med tjenestespecifikke BGP-communityværdier som vist i eksemplet nedenfor.
  
> [!NOTE]
> Du bør forvente, at noget netværkstrafik, der er knyttet til andre programmer, medtages i communityværdien. Dette er den forventede funktionsmåde for en global software som en tjeneste med delte tjenester og datacentre. Dette er blevet minimeret, hvor det er muligt med ovenstående to mål, administration af præfiksantal og/eller båndbredde i tankerne.

|**Tjeneste**|**BGP-communityværdi**|**Bemærkninger**|
|:-----|:-----|:-----|
|Exchange Online\*  <br/> |12076:5010  <br/> |Omfatter Exchange- og EOP-tjenester\*  <br/> |
|SharePoint Online\*  <br/> |12076:5020  <br/> |SharePoint Online  <br/> |
|Skype for Business\*  <br/> |12076:5030  <br/> |Skype for Business Online & Microsoft Teams-tjenester  <br/> |
|Andre Office 365 tjenester\*  <br/> |12076:5100  <br/> |Omfatter Azure Active Directory (scenarier med godkendelse og katalogsynkronisering) samt Office 365 portaltjenester  <br/> |
|\*Omfanget af de tjenestescenarier, der er inkluderet i ExpressRoute, er beskrevet i artiklen [Office 365 slutpunkter](./urls-and-ip-address-ranges.md).  <br/> \*\*Yderligere tjenester og værdier for BGP-community'et kan tilføjes i fremtiden. [Se den aktuelle liste over BGP-communities](/azure/expressroute/expressroute-routing).  <br/> |

## <a name="what-are-the-most-common-scenarios-for-using-bgp-communities"></a>Hvad er de mest almindelige scenarier for brug af BGP-communities?

Kunder kan bruge BGP-communities til at regulere grupper af IP-præfikser, der accepteres af deres netværk via Azure ExpressRoute, hvilket påvirker det samlede antal IP-præfikser og den forventede båndbreddekonvolut for visse Office 365 tjenester. Det er vigtigt at forstå, at alle Office 365 kræver internetbundet trafik uanset brugen af Azure ExpressRoute eller BGP Communities. Følgende tre scenarier er de mest almindelige måder at bruge denne funktionalitet på.
  
### <a name="scenario-1-minimizing-the-number-of-office-365-ip-prefixes"></a>Scenarie 1: Minimering af antallet af IP-præfikser Office 365

Contoso Corporation er en virksomhed på 50.000 personer, der i øjeblikket bruger Office 365 til Exchange Online og SharePoint Online. I forbindelse med gennemgangen af ExpressRoute-krav bestemmer Contoso sine netværksenheder på mange internationale placeringer, der ikke kan håndtere distributionstabelstørrelser over 100 yderligere ruteposter. Contoso gennemgik det samlede antal IP-præfikser, som ExpressRoute ville annoncere for for det fulde sæt Office 365 tjenester og konkluderede, at det overstiger 100. For at forblive under de 100 ekstra ruteposter begrænser Contoso brugen af ExpressRoute for Office 365 til kun den SharePoint Online BGP-communityværdi, 12076:5020, som modtages via ExpressRoute Microsoft-peering.

|**BGP-communitykode er brugt**|**Funktionalitet, der kan overføres via Azure ExpressRoute**|**Internetruter kræves**|
|:-----|:-----|:-----|
|SharePoint  <br/> (12076:5020)  <br/> |SharePoint Online-OneDrive for Business &amp;  <br/> | DNS-, CRL-CDN-anmodninger &amp;  <br/>  Alle andre Office 365 tjenester, der ikke understøttes specifikt via Azure ExpressRoute  <br/>  Alle andre Microsoft-cloudtjenester  <br/>  Office 365 portal, Office 365 godkendelse Office &amp; i en browser  <br/>  Exchange Online, Exchange Online Protection og Skype for Business Online  <br/> |

> [!NOTE]
> Hvis du vil opnå et lavere antal præfikser for hver tjeneste, vil der fortsat være et minimalt overlap mellem tjenester. Dette er den forventede funktionsmåde.
  
### <a name="scenario-2-scoping-expressroute-and-internal-bandwidth-use-to-some-office-365-services"></a>Scenarie 2: Brug af Scoping ExpressRoute og intern båndbredde til nogle Office 365 tjenester

Fabrikam Inc, en stor multinational virksomhed med et distribueret heterogent netværk, er abonnent på mange Office 365 tjenester, herunder; Exchange Online, SharePoint Online og Skype for Business Online. Fabrikams interne routinginfrastruktur kan håndtere tusindvis af IP-præfikser i sine routingtabeller. Fabrikam vil dog kun klargøre ExpressRoute og intern båndbredde til Office 365 programmer, der er mest følsomme over for netværksydeevne og bruger deres eksisterende internetbåndbredde til alle andre Office 365 programmer.
  
Fabrikam tilpasser derfor sin Azure ExpressRoute-båndbredde til blot Skype for Business Online BGP Community-værdi, 12076:5030, som modtages via ExpressRoute Microsoft-peering. Den resterende netværkstrafik, der er knyttet til Office 365 fortsætter med at bruge internet udgangspunkter.

|**BGP-communitykode er brugt**|**Funktionalitet, der kan overføres via Azure ExpressRoute**|**Internetruter kræves**|
|:-----|:-----|:-----|
|Skype for Business  <br/> (12076:5030)  <br/> |Skype SIP-signalering, downloads, stemme-, video- og skrivebordsdeling  <br/> | DNS-, CRL-CDN-anmodninger &amp;  <br/>  Alle andre Office 365 tjenester, der ikke understøttes specifikt via Azure ExpressRoute  <br/>  Alle andre Microsoft-cloudtjenester  <br/>  Office 365 portal, Office 365 godkendelse Office &amp; i en browser  <br/>  Skype for Business telemetri, hurtige tip til Skype klient, offentlig chatforbindelse  <br/>  Exchange Online, Exchange Online Protection og SharePoint Online  <br/> |

### <a name="scenario-3-scoping-azure-expressroute-for-office-365-services-only"></a>Scenarie 3: Kun Azure ExpressRoute til Office 365 tjenester

Woodgrove Bank er kunde hos flere Microsoft-cloudtjenester, herunder Office 365. Efter evalueringen af deres netværkskapacitet og forbrug beslutter Woodgrove Bank at udrulle Azure ExpressRoute som den foretrukne sti for de understøttede Office 365 tjenester. Routingtabellerne kan understøtte det fulde sæt Office 365 IP-præfikser og de Azure ExpressRoute-kredsløb, de har klargjort, understøtter al forventet båndbredde og ventetidsbehov.
  
For at sikre netværkstrafik, der er knyttet til andre Microsoft-cloudtjenester end Office 365, tilpasser Woodgrove Bank brugen af ExpressRoute til Office 365 til alle IP-præfikser, der er mærket med Office 365 specifikke BGP-communityværdier, 12076:5010, 12076:5020, 12076:5030, 12076:5100.

|**BGP-communitykode er brugt**|**Funktionalitet, der kan overføres via Azure ExpressRoute**|**Internetruter kræves**|
|:-----|:-----|:-----|
|Exchange, Skype for Business & Microsoft Teams, SharePoint, &amp; andre tjenester  <br/> (12076:5010, 12076:5020, 12076:5030, 12076:5100)  <br/> |&amp; Exchange Online Exchange Online Protection  <br/> SharePoint Online-OneDrive for Business &amp;  <br/> Skype SIP-signalering, downloads, stemme-, video- og skrivebordsdeling  <br/> Office 365 portal, Office 365 godkendelse Office &amp; i en browser  <br/> | DNS-, CRL-CDN-anmodninger &amp;  <br/>  Alle andre Office 365 tjenester, der ikke understøttes specifikt via Azure ExpressRoute  <br/>  Alle andre Microsoft-cloudtjenester  <br/> |

## <a name="key-planning-considerations-to-using-bgp-communities"></a>Vigtige overvejelser i forbindelse med planlægning i forbindelse med brug af BGP-communities

Kunder, der vælger at drage fordel af BGP-communities for at påvirke, hvordan ExpressRoute annonceres og overføres via kundenetværket, skal tage følgende hensyn:
  
- Når du bruger BGP-communities i dit netværksdesign, er det vigtigt at sikre, at rutesymmetri stadig opretholdes. I nogle tilfælde kan tilføjelse eller fjernelse af BGP-communities skabe en situation, hvor symmetrisk routing brydes, og distributionskonfigurationen skal opdateres for at genoprette symmetrisk routing.

- Scoping Azure ExpressRoute med BGP-communityværdier er en kundehandling. Microsoft reklamerer for alle IP-præfikser, der er knyttet til peering-relationen, uanset hvor meget kunden har konfigureret.

- Azure ExpressRoute understøtter ikke handlinger på Microsofts netværk, der er baseret på kundetildelte BGP-communities.

- De IP-præfikser, der bruges af Office 365, er kun markeret med tjenestespecifikke BGP-communityværdier, placeringsspecifikke BGP-communities understøttes ikke. Office 365 tjenester er globale, understøttes filtreringspræfikser baseret på lejerens placering eller dataene i Office 365 cloudmiljøet ikke. Den anbefalede fremgangsmåde er at konfigurere dit netværk til at koordinere den korteste eller mest foretrukne netværkssti fra brugerens netværksplacering til Microsofts globale netværk, uanset den fysiske placering af IP-adressen for den Office 365 tjeneste, de anmoder om.

- De IP-præfikser, der er inkluderet i hver BGP-communityværdi, repræsenterer et undernet, der indeholder IP-adresser for det Office 365 program, der er knyttet til værdien. I nogle tilfælde har mere end ét Office 365 program IP-adresser i et undernet, hvilket resulterer i et IP-præfiks, der findes i mere end én communityværdi. Dette forventes, men sjældent, funktionsmåde på grund af allokeringsfragmentering og påvirker ikke præfiksantallet eller båndbreddestyringsmålene. Kunder opfordres til at bruge tilgangen "tillad det, der er behov for" i modsætning til at "nægte, hvad der ikke er nødvendigt", når de udnytter BGP-communities til Office 365 at minimere effekten.

- Brug af BGP-communities ændrer ikke de underliggende krav til netværksforbindelsen eller den konfiguration, der kræves for at bruge Office 365. Kunder, der ønsker at få adgang til Office 365 skal stadig have adgang til internettet.

- Scoping Azure ExpressRoute med BGP-communities påvirker kun de ruter, dit interne netværk kan se via Microsoft-peering-relationen. Du skal muligvis foretage yderligere konfigurationer på programniveau, f.eks. brugen af en PAC- eller WPAD-konfiguration sammen med den områdeindtrerede routing.

- Ud over at bruge de Microsoft-tildelte BGP-communities kan kunderne vælge at tildele deres egne BGP-communities til Office 365 IP-præfikser, der er lært via Azure ExpressRoute for at påvirke den interne routing. En populær use case er at tildele et placeringsbaseret BGP-community til alle de ruter, der er lært via hver given ExpressRoute-peeringplacering, og derefter bruge disse oplysninger downstream i kundenetværket til at koordinere den korteste eller mest foretrukne netværkssti til Microsofts netværk. Brugen af kundetilknyttet BGP-communities med ExpressRoute til Office 365 scenarier er uden for Microsofts kontrol- eller synlighedsområde.

Her er et kort link, du kan bruge til at vende tilbage: [https://aka.ms/bgpexpressroute365]().
  
## <a name="related-topics"></a>Relaterede emner

[Vurdering af Office 365 netværksforbindelse](assessing-network-connectivity.md)
  
[Azure ExpressRoute til Office 365](azure-expressroute.md)
  
[Administration af ExpressRoute for Office 365 forbindelse](managing-expressroute-for-connectivity.md)
  
[Routing med ExpressRoute til Office 365](routing-with-expressroute.md)
  
[Netværksplanlægning med ExpressRoute til Office 365](network-planning-with-expressroute.md)
  
[Mediekvalitet og ydeevne for netværksforbindelsen i Skype for Business Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[ExpressRoute og QoS i Skype for Business Online](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[Opkaldsflow ved hjælp af ExpressRoute](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[Implementering af ExpressRoute for Office 365](implementing-expressroute.md)
  
[Understøttelse af BGP-communities](/azure/expressroute/expressroute-routing)
  
[Office 365 justering af ydeevnen ved hjælp af grundlinjer og ydeevnehistorik](performance-tuning-using-baselines-and-history.md)
  
[Plan for fejlfinding af ydeevnen for Office 365](performance-troubleshooting-plan.md)
  
[Azure ExpressRoute til oplæring af Office 365](https://channel9.msdn.com/series/aer)