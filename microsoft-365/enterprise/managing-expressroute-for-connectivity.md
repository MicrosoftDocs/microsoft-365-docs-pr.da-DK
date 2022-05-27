---
title: Administration af ExpressRoute for Office 365 forbindelse
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 7/13/2017
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
search.appverid:
- MET150
- BCS160
ms.assetid: e4468915-15e1-4530-9361-cd18ce82e231
description: Få mere at vide om, hvordan du administrerer ExpressRoute for Office 365, herunder almindelige områder, der skal konfigureres, f.eks. præfiksfiltrering, sikkerhed og overholdelse af angivne standarder.
ms.openlocfilehash: 493a7c0ca14d05a2b84763b9e9485f828574a930
ms.sourcegitcommit: 6a981ca15bac84adbbed67341c89235029aad476
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/27/2022
ms.locfileid: "65753864"
---
# <a name="managing-expressroute-for-office-365-connectivity"></a>Administration af ExpressRoute for Office 365 forbindelse

ExpressRoute til Office 365 tilbyder en alternativ routingsti til at nå mange Office 365-tjenester uden at skulle bruge al trafik til udgående data til internettet. Selvom internetforbindelsen til Office 365 stadig er nødvendig, gør de specifikke ruter, som Microsoft reklamerer for via BGP til dit netværk, det direkte ExpressRoute-kredsløb foretrukket, medmindre der er andre konfigurationer i netværket. De tre almindelige områder, du måske vil konfigurere til at administrere denne routing, omfatter præfiksfiltrering, sikkerhed og overholdelse af angivne standarder.
  
> [!NOTE]
> Microsoft ændrede, hvordan Microsoft Peering-routingdomænet gennemses for Azure ExpressRoute. Fra den 31. juli 2017 kan alle Azure ExpressRoute-kunder aktivere Microsoft Peering direkte fra Azure Administrative Console eller via PowerShell. Når du har aktiveret Microsoft Peering, kan alle kunder oprette rutefiltre for at modtage BGP-ruteannoncer for Dynamics 365 Customer Engagement-programmer (tidligere kaldet CRM Online). Kunder, der har brug for Azure ExpressRoute til Office 365, skal modtage en anmeldelse fra Microsoft, før de kan oprette rutefiltre til Office 365. Kontakt dit Microsoft-kontoteam for at få mere at vide om, hvordan du anmoder om en anmeldelse for at aktivere Office 365 ExpressRoute. Uautoriserede abonnementer, der forsøger at oprette rutefiltre for Office 365, får vist en [fejlmeddelelse](https://support.microsoft.com/kb/3181709)
  
## <a name="prefix-filtering"></a>Præfiksfiltrering

Microsoft anbefaler, at kunderne accepterer alle BGP-ruter som annonceret fra Microsoft. De leverede ruter gennemgår en streng gennemgangs- og valideringsproces, der fjerner eventuelle fordele ved tilføjet kontrol. ExpressRoute tilbyder oprindeligt de anbefalede kontrolelementer, f.eks. ejerskab af IP-præfiks, integritet og skalering – uden indgående rutefiltrering på kundesiden.
  
Hvis du har brug for yderligere validering af ruteejerskabet på tværs af den offentlige peering for ExpressRoute, kan du kontrollere de annoncerede ruter i forhold til listen over alle IPv4- og IPv6-IP-præfikser, der repræsenterer [Microsofts offentlige IP-intervaller](https://www.microsoft.com/download/details.aspx?id=53602). Disse intervaller dækker hele Microsoft-adresseområdet og ændres sjældent, hvilket giver et pålideligt sæt intervaller, der kan filtreres mod, hvilket også giver yderligere beskyttelse til kunder, der er bekymrede for, at ikke-Microsoft-ejede ruter lækker ind i deres miljø. Hvis der er en ændring, foretages den den 1. i måneden, og versionsnummeret **i detaljesektionen** på siden ændres, hver gang filen opdateres.
  
Der er mange grunde til at undgå at bruge [Office 365 URL-adresser og IP-adresseområder](./urls-and-ip-address-ranges.md) til at generere præfiksfilterlister. Herunder følgende:
  
- De Office 365 IP-præfikser gennemgår ofte mange ændringer.

- De Office 365 URL-adresser og IP-adresseområder er designet til at administrere lister over tilladte firewalls og proxyinfrastruktur og ikke routing.

- De Office 365 URL-adresser og IP-adresseområder dækker ikke andre Microsoft-tjenester, der kan være i området for dine ExpressRoute-forbindelser.

|**Mulighed**|**Kompleksitet**|**Skift kontrolelement**|
|:-----|:-----|:-----|
|Acceptér alle Microsoft-ruter  <br/> |**Lav:** Kunden er afhængig af Microsoft-kontrolelementer for at sikre, at alle ruter ejes korrekt.  <br/> |Ingen  <br/> |
|Filtrer Microsoft-ejede supernet  <br/> |**Medium:** Kunden implementerer opsummerede præfiksfilterlister for kun at tillade Microsoft-ejede ruter.  <br/> |Kunderne skal sikre, at de sjældne opdateringer afspejles i rutefiltre.  <br/> |
|Filtrer Office 365 IP-områder  <br/> [!CAUTION] Not-Recommended |**Høj:** Kundefiltrer ruter baseret på definerede Office 365 IP-præfikser.  <br/> |Kunderne skal implementere en robust proces til administration af ændringer for de månedlige opdateringer.  <br/> [!CAUTION] Denne løsning kræver betydelige igangværende ændringer. Ændringer, der ikke implementeres i tide, vil sandsynligvis resultere i en tjenesteafbrydelse.   |

Oprettelse af forbindelse til Office 365 ved hjælp af Azure ExpressRoute er baseret på BGP-reklamer for bestemte IP-undernet, der repræsenterer netværk, hvor Office 365 slutpunkter udrulles. På grund af den globale karakter af Office 365 og antallet af tjenester, der udgør Office 365, har kunderne ofte behov for at administrere de reklamer, de accepterer på deres netværk. Hvis du er bekymret for antallet af præfikser, der annonceres i dit miljø, giver [BGP-communityfunktionen](https://support.office.com/article/Using-BGP-communities-in-ExpressRoute-for-Office-365-scenarios-preview-9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099) dig mulighed for at filtrere reklamerne til et bestemt sæt Office 365 tjenester. Denne funktion er nu en prøveversion.
  
Uanset hvordan du administrerer BGP-ruteannoncer, der kommer fra Microsoft, får du ikke nogen særlig eksponering for Office 365 tjenester sammenlignet med at oprette forbindelse til Office 365 via et internetkredsløb alene. Microsoft opretholder de samme niveauer for sikkerhed, overholdelse af angivne standarder og ydeevne, uanset hvilken type kredsløb en kunde bruger til at oprette forbindelse til Office 365.
  
### <a name="security"></a>Sikkerhed

Microsoft anbefaler, at du vedligeholder dine egne netværks- og sikkerhedsperimeterkontroller for forbindelser, der går til og fra offentlige ExpressRoute- og Microsoft-peering, som omfatter forbindelser til og fra Office 365 tjenester. Sikkerhedskontroller skal være på plads for netværksanmodninger, der rejser udgående fra dit netværk til Microsofts netværk og indgående fra Microsofts netværk til dit netværk.
  
#### <a name="outbound-from-customer-to-microsoft"></a>Udgående fra kunde til Microsoft
  
Når computere opretter forbindelse til Office 365, opretter de forbindelse til det samme sæt slutpunkter, uanset om forbindelsen er oprettet via et internet- eller ExpressRoute-kredsløb. Uanset hvilke kredsløb der bruges, anbefaler Microsoft, at du behandler Office 365 tjenester som mere pålidelige end generiske internetdestinationer. Dine udgående sikkerhedskontroller bør fokusere på portene og protokollerne for at reducere eksponeringen og minimere den løbende vedligeholdelse. De nødvendige portoplysninger er tilgængelige i artiklen [reference til Office 365 slutpunkter](./urls-and-ip-address-ranges.md).
  
I forbindelse med tilføjede kontrolelementer kan du bruge filtrering på FQDN-niveau i din proxyinfrastruktur til at begrænse eller inspicere nogle eller alle netværksanmodninger, der er beregnet til internettet eller Office 365. Hvis du bevarer listen over FQDN'er, efterhånden som funktioner udgives, og de Office 365 tilbud udvikles, kræver det mere robust ændringsstyring og registrering af ændringer i de publicerede [Office 365 slutpunkter](./urls-and-ip-address-ranges.md).
  
> [!CAUTION]
> Microsoft anbefaler, at du ikke udelukkende bruger IP-præfikser til at administrere udgående sikkerhed for at Office 365.

|**Mulighed**|**Kompleksitet**|**Skift kontrolelement**|
|:-----|:-----|:-----|
|Ingen begrænsninger  <br/> |**Lav:** Kunden tillader ubegrænset udgående adgang til Microsoft.  <br/> |Ingen  <br/> |
|Portbegrænsninger  <br/> |**Lav:** Kunden begrænser udgående adgang til Microsoft efter de forventede porte.  <br/> |Sjældne.  <br/> |
|Begrænsninger for FQDN  <br/> |**Høj:** Kunden begrænser udgående adgang til Office 365 baseret på de publicerede FQDN'er.  <br/> |Månedlige ændringer.  <br/> |

#### <a name="inbound-from-microsoft-to-customer"></a>Indgående fra Microsoft til kunde
  
Der er flere valgfrie scenarier, der kræver, at Microsoft starter forbindelser til dit netværk.
  
- ADFS under adgangskodevalidering for logon.

- [Exchange Server hybridinstallationer](/exchange/exchange-hybrid).

- Mail fra en Exchange Online lejer til en vært i det lokale miljø.

- SharePoint Onlinemail, der er sendt fra SharePoint Online til en vært i det lokale miljø.

- [SharePoint hybridsøgning i organisationsnetværket](/SharePoint/hybrid/display-hybrid-federated-search-results-in-sharepoint-online).

- [SharePoint hybrid BCS](/SharePoint/hybrid/deploy-a-business-connectivity-services-hybrid-solution).

- [Skype for Business hybrid-](/skypeforbusiness/hybrid/plan-hybrid-connectivity?bc=%2fSkypeForBusiness%2fbreadcrumb%2ftoc.json&toc=%2fSkypeForBusiness%2ftoc.json) og/eller [Skype for Business-sammenslutning](/office365/servicedescriptions/skype-for-business-online-service-description/skype-for-business-online-features).

- [Skype for Business Cloud Connector](/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-skype-for-business-cloud-connector-edition).

Microsoft anbefaler, at du accepterer disse forbindelser via dit internetkredsløb i stedet for dit ExpressRoute-kredsløb for at reducere kompleksiteten. Hvis dine behov for overholdelse af angivne standarder eller ydeevne kræver, at disse indgående forbindelser accepteres via et ExpressRoute-kredsløb, anbefales det at bruge en firewall eller en omvendt proxy for at omfanget af de accepterede forbindelser. Du kan bruge [de Office 365 slutpunkter](./urls-and-ip-address-ranges.md) til at finde de rigtige FQDN'er og IP-præfikser.
  
### <a name="compliance"></a>Overholdelse af regler og standarder

Vi er ikke afhængige af den routingsti, du bruger til nogen af vores kontrolelementer til overholdelse af angivne standarder. Uanset om du opretter forbindelse til Office 365 tjenester via et ExpressRoute- eller internetkredsløb, ændres vores kontrolelementer til overholdelse af angivne standarder ikke. Du bør gennemgå de forskellige niveauer for overholdelse af angivne standarder og sikkerhedscertificering for Office 365 for at finde ud af, hvad der passer bedst til organisationens behov.
  
Her er et kort link, du kan bruge til at vende tilbage: [https://aka.ms/manageexpressroute365]()
  
## <a name="related-topics"></a>Relaterede emner

[Content Delivery Networks](content-delivery-networks.md)
  
[Office 365-URL-adresser og IP-adresseintervaller](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Administrere Office 365-slutpunkter](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Azure ExpressRoute til oplæring af Office 365](https://channel9.msdn.com/series/aer)