---
title: Brug af BGP-communities i ExpressRoute til Office 365 scenarier
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Få mere at vide om, hvordan du bruger BGP-communities i Azure ExpressRoute til at administrere antallet af IP-præfikser og den påkrævede båndbredde Office 365 scenarier.
ms.openlocfilehash: afcbbbebda8dcc7c9425831b44f0d95f0eca5a18
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63590588"
---
# <a name="using-bgp-communities-in-expressroute-for-office-365-scenarios"></a>Brug af BGP-communities i ExpressRoute til Office 365 scenarier

Oprettelse af forbindelse til Office 365 der bruger Azure ExpressRoute, er baseret på BGP-annonceringer for bestemte IP-undernet, der repræsenterer netværk, Office 365 hvor slutpunkter er installeret. På grund af den globale Office 365 og antallet af tjenester, der udgør Office 365, har kunder ofte brug for at administrere de reklamer, de accepterer på deres netværk. Reduktion af antallet af IP-undernet; som IP-præfikser i resten af denne artikel for at være på linje med terminologien for BGP-netværksadministration, tjener følgende slutmål for kunder:
  
- Administrer antallet af accepterede **annoncerede** IP-præfikser – Kunder, der har en intern netværksinfrastruktur eller netværksudbyder, der kun understøtter et begrænset antal IP-præfikser, og kunder, der har en netværksudbyder, der opkræver gebyrer for at acceptere præfikser over et begrænset antal, vil ønske at evaluere det samlede antal præfikser, der allerede er annonceret til deres netværk, og vælge, hvilke Office 365-programmer der er bedst egnet til ExpressRoute.

- Administrer mængden af båndbredde, der kræves på **Azure ExpressRoute-kredsløbet** – Kunder kan ønske at styre båndbredden for Office 365-tjenesterne via ExpressRoute-stien vs. internetstien. Dette giver kunderne mulighed for at reservere ExpressRoute-båndbredde til bestemte programmer som f.eks Skype for Business og distribuere de resterende Office 365 programmer via internetstien.

For at hjælpe kunder med disse mål mærkes Office 365 IP-præfikser, der er annonceret over ExpressRoute, med tjenestespecifikke BGP-community-værdier som vist i eksemplet nedenfor.
  
> [!NOTE]
> Du kan forvente, at noget netværkstrafik, der er knyttet til andre programmer, medtages i community-værdien. Dette er den forventede funktionsmåde for en global software som et servicetilbud med delte tjenester og datacentre. Hvor det er muligt, er dette blevet minimeret med ovennævnte to mål for øje, administration af præfiks og/eller båndbredde.

|**Tjeneste**|**BGP-community-værdi**|**Bemærkninger**|
|:-----|:-----|:-----|
|Exchange Online\*  <br/> |12076:5010  <br/> |Omfatter Exchange- og EOP-tjenester\*  <br/> |
|SharePoint Online\*  <br/> |12076:5020  <br/> |SharePoint Online  <br/> |
|Skype for Business\*  <br/> |12076:5030  <br/> |Skype for Business online & Microsoft Teams tjenester  <br/> |
|Andre Office 365 tjenester\*  <br/> |12076:5100  <br/> |Omfatter Azure Active Directory (godkendelses- og katalogsynkroniseringsscenarier) samt Office 365 Portal-tjenester  <br/> |
|\*Omfanget af tjenestescenarier, der er inkluderet i ExpressRoute, er [dokumenteret Office 365 artikel om slutpunkter](./urls-and-ip-address-ranges.md).  <br/> \*\*Der tilføjes muligvis yderligere tjenester og BGP-community-værdier i fremtiden. [Se den aktuelle liste over BGP-communities](/azure/expressroute/expressroute-routing).  <br/> |

## <a name="what-are-the-most-common-scenarios-for-using-bgp-communities"></a>Hvad er de mest almindelige scenarier for brug af BGP-communities?

Kunder kan bruge BGP-communities til at regulere grupper af IP-præfikser, der accepteres af deres netværk via Azure ExpressRoute, og har således indflydelse på det samlede antal IP-præfikser og forventede båndbredde for visse Office 365-tjenester. Det er vigtigt at forstå, at alle Office 365 kræver trafik bundet til internettet uanset brugen af Azure ExpressRoute eller BGP-communities. Følgende tre scenarier er de mest almindelige anvendelser af denne funktionalitet.
  
### <a name="scenario-1-minimizing-the-number-of-office-365-ip-prefixes"></a>Scenarie 1: Minimering af antallet af Office 365 IP-præfikser

Contoso Corporation er en virksomhed med 50.000 personer, der aktuelt Office 365 til Exchange Online og SharePoint Online. Under en gennemgang af kravene til ExpressRoute afgør Contoso, at dens netværksenheder på mange regionale placeringer ikke kan håndtere routingtabelstørrelser over 100 ekstra ruteposter. Contoso gennemgik det samlede antal IP-præfikser, som ExpressRoute ville annoncere for det komplette sæt Office 365-tjenester, og afsluttede, at den oversteg 100. For at holde sig under de 100 ekstra ruteposter, begrænses brugen af ExpressRoute til Office 365 kun til SharePoint Online BGP-community-værdi, 12076:5020, modtaget via ExpressRoute Microsoft-peering.

|**BGP-community-tag brugt**|**Funktionaliteten kan overdrives over Azure ExpressRoute**|**Internetruter er påkrævede**|
|:-----|:-----|:-----|
|SharePoint  <br/> (12076:5020)  <br/> |SharePoint Online &amp; OneDrive for Business  <br/> | DNS, liste over tilbagekaldte liste, &amp; CDN anmodninger  <br/>  Alle andre Office 365-tjenester, der ikke specifikt understøttes over Azure ExpressRoute  <br/>  Alle andre Microsoft-skytjenester  <br/>  Office 365, Office 365, Office &amp; i en browser  <br/>  Exchange Online, Exchange Online Protection og Skype for Business Online  <br/> |

> [!NOTE]
> For at opnå et lavere antal præfikser for hver tjeneste bevares en minimal mængde overlap mellem tjenester. Dette er den forventede funktionsmåde.
  
### <a name="scenario-2-scoping-expressroute-and-internal-bandwidth-use-to-some-office-365-services"></a>Scenarie 2: Angivelse af ExpressRoute og brug af intern båndbredde for nogle Office 365 tjenester

Fabrikam Inc, en stor, multi national virksomhed med et distribueret hetergene netværk, er abonnent på mange af Office 365 tjenester, herunder: Exchange Online, SharePoint Online og Skype for Business Online. Fabrikams interne routinginfrastruktur kan håndtere tusindvis af IP-præfikser i dens routingtabeller. Fabrikam ønsker dog kun at klargøre ExpressRoute og intern båndbredde til Office 365-programmer, som er de mest følsomme over for netværkets ydeevne, og bruge deres eksisterende internetbåndbredde til alle andre Office 365-programmer.
  
Derfor søger Fabrikam efter sin Azure ExpressRoute-båndbredde kun til Skype for Business Online BGP-community-værdi, 12076:5030, modtaget via ExpressRoute Microsoft-peering. Den resterende netværkstrafik, der er knyttet Office 365, fortsætter med at bruge internet udgangspunkterne.

|**BGP-community-tag brugt**|**Funktionaliteten kan overdrives over Azure ExpressRoute**|**Internetruter er påkrævede**|
|:-----|:-----|:-----|
|Skype for Business  <br/> (12076:5030)  <br/> |Skype SIP-signal, downloads, tale, video og skrivebordsdeling  <br/> | DNS, liste over tilbagekaldte liste, &amp; CDN anmodninger  <br/>  Alle andre Office 365-tjenester, der ikke specifikt understøttes over Azure ExpressRoute  <br/>  Alle andre Microsoft-skytjenester  <br/>  Office 365, Office 365, Office &amp; i en browser  <br/>  Skype for Business, hurtige tip Skype klient, offentlige chatforbindelser  <br/>  Exchange Online, Exchange Online Protection og SharePoint Online  <br/> |

### <a name="scenario-3-scoping-azure-expressroute-for-office-365-services-only"></a>Scenarie 3: Angivelse af Azure ExpressRoute Office 365 kun for tjenester

Woodgrove Bank er kunde hos flere microsoft-skytjenester, herunder Office 365. Efter at have evalueret deres netværkskapacitet og -forbrug beslutter Woodgrove Bank sig for at installere Azure ExpressRoute som den foretrukne sti til de understøttede Office 365-tjenester. Routingtabellerne kan understøtte det komplette sæt Office 365 IP-præfikser, og de Azure ExpressRoute-kredsløb, de har klargjort, understøtter alle forventede behov for båndbredde og ventetid.
  
For at sikre netværkstrafik, der er knyttet til andre Microsoft-skytjenester end Office 365, søger Woodgrove Bank efter brugen af ExpressRoute til Office 365 på alle IP-præfikser, der er kodet med Office 365 specifikke BGP-community-værdier, 12076:5010, 12076:5076, 12076:5100.

|**BGP-community-tag brugt**|**Funktionaliteten kan overdrives over Azure ExpressRoute**|**Internetruter er påkrævede**|
|:-----|:-----|:-----|
|Exchange, Skype for Business & Microsoft Teams, SharePoint, &amp; andre tjenester  <br/> (12076:5010, 12076:5020, 12076:5030, 12076:5100)  <br/> |&amp; Exchange Online Exchange Online Protection  <br/> SharePoint Online &amp; OneDrive for Business  <br/> Skype SIP-signal, downloads, tale, video og skrivebordsdeling  <br/> Office 365, Office 365, Office &amp; i en browser  <br/> | DNS, liste over tilbagekaldte liste, &amp; CDN anmodninger  <br/>  Alle andre Office 365-tjenester, der ikke specifikt understøttes over Azure ExpressRoute  <br/>  Alle andre Microsoft-skytjenester  <br/> |

## <a name="key-planning-considerations-to-using-bgp-communities"></a>Vigtige overvejelser i forbindelse med brug af BGP-communities

Kunder, der vælger at drage fordel af BGP-communities for at påvirke, hvordan ExpressRoute annonceres og gennemføres i hele kundenetværket, skal tage følgende overvejelser i betragtning:
  
- Når du bruger BGP-communities i dit netværksdesign, er det vigtigt at sikre, der er stadig er rutesymmetri. I nogle tilfælde kan tilføjelse eller fjernelse af BGP-communities skabe en situation, hvor symmetrisk routing brydes, og din routingkonfiguration skal opdateres for at genoprette symmetrisk routing.

- Angivelse af Azure ExpressRoute med BGP-community-værdier er en kundehandling. Microsoft annoncerer alle IP-præfikser, der er knyttet til peeringrelationen, uanset eventuelle angivelser, der er konfigureret af kunden.

- Azure ExpressRoute understøtter ikke nogen handlinger på Microsofts netværk baseret på kundetilde tildelte BGP-communities.

- De IP-præfikser, der bruges af Office 365, er kun markeret med tjenestespecifikke BGP-community-værdier, placeringsspecifikke BGP-communities understøttes ikke. Office 365-tjenester er af global karakter, understøttes filtreringpræfikser, der er baseret på placeringen af lejeren eller dataene i Office 365 skyen, ikke. Den anbefalede fremgangsmåde er at konfigurere dit netværk til at koordinere den korteste eller mest foretrukne netværkssti fra brugerens netværksplacering til Microsofts globale netværk, uanset den fysiske placering af IP-adressen på den Office 365-tjeneste, de anmoder om.

- De IP-præfikser, der er inkluderet i hver BGP-community-værdi, repræsenterer et undernet, der indeholder IP-adresser for det Office 365 program, der er knyttet til værdien. I nogle tilfælde har mere end ét Office 365-program IP-adresser i et undernet, hvilket resulterer i et IP-præfiks, der findes i mere end én community-værdi. Selvom det er sjældent, er dette en forventet funktionsmåde, der skyldes fordelingsfragmenteringen, og påvirker ikke antallet af præfikser eller mål for båndbreddestyring. Kunder opfordres til at bruge tilgangen "Tillad det, der er nødvendigt" i modsætning til "Næb det, der ikke er nødvendigt", når de udnytter BGP-communities til Office 365 at minimere effekten.

- Brug af BGP-communities ændrer ikke de underliggende krav til netværksforbindelser eller konfigurationen, der kræves for at Office 365. Kunder, der vil have adgang Office 365, skal stadig være i stand til at få adgang til internettet.

- Angivelse af Azure ExpressRoute med BGP-communities påvirker kun de ruter, dit interne netværk kan se over Microsoft-peeringrelationen. Det kan være nødvendigt at foretage yderligere konfigurationer på programniveau, f.eks. brug af en PAC- eller WPAD-konfiguration sammen med den omfangsdelagte routing.

- Ud over at bruge Microsofts tildelte BGP-communities kan kunder vælge at tildele deres egne BGP-communities til Office 365 IP-præfikser lært via Azure ExpressRoute for at påvirke intern routing. En populær use case er at tildele et placeringsbaseret BGP-community til alle ruter, der er lært gennem hver given ExpressRoute-peeringplacering og derefter bruge disse oplysninger i kundenetværket til at koordinere den korteste eller mest foretrukne netværkssti til Microsofts netværk. Brug af kunde-tildelte BGP-communities med ExpressRoute til Office 365 scenarier er uden for Microsofts kontrol eller synlighed.

Her er et kort link, du kan bruge til at vende tilbage: [https://aka.ms/bgpexpressroute365]().
  
## <a name="related-topics"></a>Relaterede emner

[Vurdering Office 365 netværksforbindelsen](assessing-network-connectivity.md)
  
[Azure ExpressRoute til Office 365](azure-expressroute.md)
  
[Administrere ExpressRoute til Office 365 forbindelse](managing-expressroute-for-connectivity.md)
  
[Routing med ExpressRoute til Office 365](routing-with-expressroute.md)
  
[Netværksplanlægning med ExpressRoute til Office 365](network-planning-with-expressroute.md)
  
[Mediekvalitet og ydeevne for netværksforbindelse i Skype for Business Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[ExpressRoute og QoS i Skype for Business Online](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[Opkaldsflow med ExpressRoute](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[Implementering af ExpressRoute til Office 365](implementing-expressroute.md)
  
[Understøttelse af BGP-communities](/azure/expressroute/expressroute-routing)
  
[Office 365 justering af ydeevnen ved hjælp af grundlinjer og ydeevnehistorik](performance-tuning-using-baselines-and-history.md)
  
[Fejlfinding af ydeevne i forbindelse med planen for Office 365](performance-troubleshooting-plan.md)
  
[Azure ExpressRoute til Office 365 kurser](https://channel9.msdn.com/series/aer)