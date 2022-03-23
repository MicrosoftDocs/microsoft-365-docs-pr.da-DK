---
title: Administrere ExpressRoute til Office 365 forbindelse
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Få mere at vide om, hvordan du administrerer ExpressRoute til Office 365, herunder almindelige områder til konfiguration, f.eks. præfiksfiltrering, sikkerhed og overholdelse af regler og standarder.
ms.openlocfilehash: bffe82249a9d8a531ee85525f9db0eb38a344d50
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63594274"
---
# <a name="managing-expressroute-for-office-365-connectivity"></a>Administrere ExpressRoute til Office 365 forbindelse

ExpressRoute til Office 365 tilbyder en alternativ routingsti til at nå mange Office 365-tjenester, uden at al trafik behøver at gå ud på internettet. Selvom der stadig kræves internetforbindelse til Office 365, gør de specifikke ruter, som Microsoft annoncerer gennem BGP til dit netværk, det direkte ExpressRoute-kredsløb til foretrukket, medmindre der er andre konfigurationer i dit netværk. De tre almindelige områder, du kan konfigurere for at administrere denne routing, omfatter præfiksfiltrering, sikkerhed og overholdelse af regler og standarder.
  
> [!NOTE]
> Microsoft har ændret den måde, som Microsoft Peering-routingdomænet gennemgås for Azure ExpressRoute på. Fra den 31. juli 2017 kan alle Azure ExpressRoute-kunder aktivere Microsoft Peering direkte fra Den Azure-administrative konsol eller via PowerShell. Når Microsoft Peering er aktiveret, kan alle kunder oprette rutefiltre for at modtage BGP-ruteannoncering for Dynamics 365 Customer Engagement-programmer (tidligere kaldet CRM Online). Kunder, der har brug for Azure ExpressRoute til Office 365, skal have en vurdering fra Microsoft, før de kan oprette rutefiltre til Office 365. Kontakt dit Microsoft-kontoteam for at få mere at vide om, hvordan du anmoder om en gennemgang af, Office 365 ExpressRoute. Uautoriserede abonnementer, der forsøger at oprette rutefiltre for Office 365 modtager [en fejlmeddelelse](https://support.microsoft.com/kb/3181709)
  
## <a name="prefix-filtering"></a>Præfiksfiltrering

Microsoft anbefaler, at kunderne accepterer alle BGP-ruter som annonceret fra Microsoft. De leverede ruter gennemgår en grundig gennemgangs- og valideringsproces, hvilket fjerner eventuelle fordele for yderligere granshed. ExpressRoute tilbyder indbygget de anbefalede kontrolelementer som f.eks. ejerskab af IP-præfiks, integritet og skalering – uden indgående rutefiltrering på kundesiden.
  
Hvis du kræver yderligere validering af ejerskab af rute på tværs af offentlig ExpressRoute-peering, kan du kontrollere de annoncerede ruter i forhold til listen over alle IPv4- og IPv6 IP-præfikser, der repræsenterer [Microsofts offentlige IP-områder](https://www.microsoft.com/download/details.aspx?id=53602). Disse områder dækker hele Microsoft-adresseområdet og ændres sjældent, hvilket giver et pålideligt sæt områder at filtrere mod, som også giver yderligere beskyttelse til kunder, der er bekymrede for ikke-Microsoft-ejet ruter, derlækager i deres miljø. I tilfælde af at der er en ændring, foretages den den 1. i måneden, og versionsnummeret i detaljesektionen på siden ændres, hver gang filen opdateres.
  
Der er flere grunde til at undgå at bruge URL-adresser [](./urls-and-ip-address-ranges.md) Office 365 IP-adresseintervaller til at generere præfiksfilterlister. Herunder følgende:
  
- DE Office 365 IP-præfikser gennemgår mange hyppige ændringer.

- Webadresserne Office 365 IP-adresseintervaller er designet til at administrere tilladelseslister for firewall og proxyinfrastruktur, ikke routing.

- Webadresserne Office 365 IP-adresseintervaller og IP-adresseintervaller dækker ikke andre Microsoft-tjenester, som kan være omfattet af dine ExpressRoute-forbindelser.

|**Indstilling**|**Kompleksitet**|**Skift kontrolelement**|
|:-----|:-----|:-----|
|Acceptér alle Microsoft-ruter  <br/> |**Lav:** Kunden er afhængig af Microsoft-kontrolelementer for at sikre, at alle ruter ejes korrekt.  <br/> |Ingen  <br/> |
|Filtrer supernet ejet af Microsoft  <br/> |**Mellem:** Kunden implementerer opsummerede præfiksfilterlister for kun at tillade ruter ejet af Microsoft.  <br/> |Kunder skal sikre, at de sjældne opdateringer afspejles i rutefiltrene.  <br/> |
|Filtrer Office 365 IP-områder  <br/> [!CAUTION] Not-Recommended |**Høj:** Kunden filtrerer ruter baseret på definerede Office 365 IP-præfikser.  <br/> |Kunder skal implementere en robust proces til styring af ændringer for de månedlige opdateringer.  <br/> [!CAUTION] Denne løsning kræver væsentlige ændringer i gang. Ændringer, der ikke implementeres i tide, vil sandsynligvis medføre et tjenestesvigt.   |

Oprettelse af forbindelse til Office 365 der bruger Azure ExpressRoute, er baseret på BGP-annonceringer for bestemte IP-undernet, der repræsenterer netværk, Office 365 hvor slutpunkter er installeret. På grund af den globale Office 365 og antallet af tjenester, der udgør Office 365, har kunder ofte brug for at administrere de reklamer, de accepterer på deres netværk. Hvis du er bekymret over antallet af præfikser, der annonceres i dit miljø, giver [BGP-community-funktionen](https://support.office.com/article/Using-BGP-communities-in-ExpressRoute-for-Office-365-scenarios-preview-9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099) dig mulighed at filtrere reklamerne til et bestemt sæt Office 365-tjenester. Denne funktion er nu i forhåndsvisning.
  
Uanset hvordan du administrerer de BGP-ruteannoncering, der kommer fra Microsoft, får du ingen særlig eksponering for Office 365-tjenester sammenlignet med at oprette forbindelse til Office 365 over et internetkredsløb alene. Microsoft opretholder de samme niveauer for sikkerhed, overholdelse af regler og standarder og ydeevne, uanset hvilken type kredsløb en kunde bruger til at oprette forbindelse til Office 365.
  
### <a name="security"></a>Sikkerhed

Microsoft anbefaler, at du vedligeholder dit eget netværk og sikkerhedsperimeterkontroller for forbindelser til og fra offentlig ExpressRoute- og Microsoft-peering, som omfatter forbindelser til og fra Office 365-tjenester. Der skal være installeret sikkerhedskontrolelementer for netværksanmodninger, der er udgående fra dit netværk til Microsofts netværk, samt indgående fra Microsofts netværk til dit netværk.
  
#### <a name="outbound-from-customer-to-microsoft"></a>Udgående fra kunde til Microsoft
  
Når computere opretter forbindelse Office 365, opretter de forbindelse til det samme sæt slutpunkter, uanset om der er oprettet forbindelse via et internet- eller ExpressRoute-kredsløb. Uanset hvilket kredsløb der bruges, anbefaler Microsoft, at du behandler Office 365 som mere pålidelige end generiske internetdestinationer. Dine udgående sikkerhedskontrolelementer bør fokusere på porte og protokoller for at reducere eksponering og minimere løbende vedligeholdelse. De påkrævede portoplysninger er tilgængelige [i Office 365 referenceartikel for](./urls-and-ip-address-ranges.md) slutpunkter.
  
For tilføjede kontrolelementer kan du bruge filtrering på FQDN-niveau inden for din proxyinfrastruktur til at begrænse eller undersøge nogle eller alle netværksanmodninger, der er beregnet til internettet eller Office 365. Vedligeholdelse af listen over FQDN'er efterhånden som funktioner frigives, og Office 365-tilbud udvikler sig kræver mere robust ændringsstyring og registrering af ændringer til de publicerede [Office 365 slutpunkter](./urls-and-ip-address-ranges.md).
  
> [!CAUTION]
> Microsoft anbefaler, at du ikke udelukkende benytter IP-præfikser til at administrere udgående sikkerhed for at Office 365.

|**Indstilling**|**Kompleksitet**|**Skift kontrolelement**|
|:-----|:-----|:-----|
|Ingen begrænsninger  <br/> |**Lav:** Kunden tillader ubegrænset udgående adgang til Microsoft.  <br/> |Ingen  <br/> |
|Begrænsninger for port  <br/> |**Lav:** Kunden begrænser de forventede portes udgående adgang til Microsoft.  <br/> |Sjælden.  <br/> |
|FQDN-begrænsninger  <br/> |**Høj:** Kunden begrænser udgående adgang til Office 365 baseret på de publicerede FQDN'er.  <br/> |Månedlige ændringer.  <br/> |

#### <a name="inbound-from-microsoft-to-customer"></a>Indgående fra Microsoft til kunde
  
Der er flere valgfri scenarier, der kræver, at Microsoft starter forbindelser til dit netværk.
  
- ADFS under adgangskodevalidering for logon.

- [Exchange Server hybridinstallationer](/exchange/exchange-hybrid).

- Mail fra Exchange Online lejer til en vært i det lokale miljø.

- SharePoint Onlinemail fra SharePoint Online til en vært i det lokale miljø.

- [SharePoint hybridsøgning i organisationsnetværket](/SharePoint/hybrid/display-hybrid-federated-search-results-in-sharepoint-online).

- [SharePoint BCS-hybrid](/SharePoint/hybrid/deploy-a-business-connectivity-services-hybrid-solution).

- [Skype for Business og](/skypeforbusiness/hybrid/plan-hybrid-connectivity?bc=%2fSkypeForBusiness%2fbreadcrumb%2ftoc.json&toc=%2fSkypeForBusiness%2ftoc.json)/eller [Skype for Business sammenslutning](/office365/servicedescriptions/skype-for-business-online-service-description/skype-for-business-online-features).

- [Skype for Business Skyforbindelse](/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-skype-for-business-cloud-connector-edition).

Microsoft anbefaler, at du accepterer disse forbindelser via dit internetkredsløb i stedet for dit ExpressRoute-kredsløb for at reducere kompleksiteten. Hvis dine behov for overholdelse af regler og standarder eller ydeevne dikterer, at disse indgående forbindelser skal accepteres over et ExpressRoute-kredsløb, anbefales det at bruge en firewall eller omvendt proxy til at begrænse de accepterede forbindelser. Du kan bruge Office 365 [til at finde frem](./urls-and-ip-address-ranges.md) til de rigtige FQDN'er og IP-præfikser.
  
### <a name="compliance"></a>Overholdelse af regler og standarder

Vi er ikke afhængige af den routingsti, du bruger til nogle af vores kompatibilitetskontroller. Uanset om du opretter forbindelse til Office 365-tjenester via et ExpressRoute- eller internetkredsløb, ændres vores kompatibilitetskontroller ikke. Du bør gennemgå de forskellige kompatibilitets- og sikkerhedscertificeringsniveauer for at Office 365 finde frem til den valgmulighed, der bedst opfylder din organisations behov.
  
Her er et kort link, du kan bruge til at vende tilbage: [https://aka.ms/manageexpressroute365]()
  
## <a name="related-topics"></a>Relaterede emner

[Netværk, der kan levere indhold](content-delivery-networks.md)
  
[Office 365-URL-adresser og IP-adresseintervaller](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Administrere Office 365 slutpunkter](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Azure ExpressRoute til Office 365 kurser](https://channel9.msdn.com/series/aer)