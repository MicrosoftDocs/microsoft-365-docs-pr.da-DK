---
title: Azure ExpressRoute til Office 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 6/5/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 6d2534a2-c19c-4a99-be5e-33a0cee5d3bd
description: Få mere at vide om, hvordan du bruger Azure ExpressRoute med Office 365 og planlægger projektet til netværksimplementering, hvis du udruller med det.
ms.openlocfilehash: 1350bf73fdddd2141a2df1cbcec5edebeacf7ad4
ms.sourcegitcommit: 6a981ca15bac84adbbed67341c89235029aad476
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/27/2022
ms.locfileid: "65754284"
---
# <a name="azure-expressroute-for-office-365"></a>Azure ExpressRoute til Office 365

*Denne artikel gælder både for Microsoft 365 Enterprise og Office 365 Enterprise.*

Få mere at vide om, hvordan Azure ExpressRoute bruges sammen med Office 365, og hvordan du planlægger det netværksimplementeringsprojekt, der kræves, hvis du udruller Azure ExpressRoute til brug sammen med Office 365. Infrastruktur- og platformstjenester, der kører i Azure, vil ofte drage fordel af at tage højde for netværksarkitektur og overvejelser om ydeevne. Vi anbefaler ExpressRoute til Azure i disse tilfælde. Software as a Service-tilbud som Office 365 og Dynamics 365 er udviklet til at kunne tilgås sikkert og pålideligt via internettet. Du kan læse om internetydeevne og -sikkerhed, og hvornår du måske overvejer Azure ExpressRoute til Office 365 i artiklen [Vurdering af Office 365 netværksforbindelse](assessing-network-connectivity.md).

> [!NOTE]
> Microsoft Defender for Endpoint leverer ikke integration med Azure ExpressRoute. Selvom dette ikke forhindrer kunderne i at definere ExpressRoute-regler, der muliggør forbindelse fra et privat netværk til Microsoft Defender for Endpoint cloudtjenester, er det op til kunden at vedligeholde regler, efterhånden som tjenesten eller cloudinfrastrukturen udvikler sig.

> [!NOTE]
> Vi anbefaler ikke ExpressRoute til Microsoft 365, fordi den i de fleste tilfælde ikke leverer den bedste forbindelsesmodel til tjenesten. Microsoft-godkendelse er derfor påkrævet for at bruge denne forbindelsesmodel til Microsoft 365. Vi gennemser alle kundeanmodninger og godkender ExpressRoute for Microsoft 365 kun i de sjældne scenarier, hvor det er nødvendigt. Læs [ExpressRoute for Microsoft 365 vejledning](https://aka.ms/erguide) for at få flere oplysninger og efter en omfattende gennemgang af dokumentet med dine produktivitets-, netværks- og sikkerhedsteams, og arbejd sammen med dit Microsoft-kontoteam om at indsende en undtagelse, hvis det er nødvendigt. Der vises en [fejlmeddelelse](https://support.microsoft.com/kb/3181709) for uautoriserede abonnementer, der forsøger at oprette rutefiltre for Office 365.

## <a name="planning-azure-expressroute-for-office-365"></a>Planlægning af Azure ExpressRoute til Office 365

Ud over internetforbindelsen kan du vælge at dirigere et undersæt af deres Office 365 netværkstrafik via en direkte forbindelse, der giver forudsigelighed og en SLA på 99,95 % i oppetid for Microsoft-netværkskomponenterne. Azure ExpressRoute giver dig denne dedikerede netværksforbindelse til Office 365 og andre Microsoft-cloudtjenester.

Uanset om du har et eksisterende MPLS WAN, kan ExpressRoute føjes til din netværksarkitektur på en af tre måder. via en understøttet udbyder af samplacering af cloududveksling, en Ethernet-point-to-point-forbindelsesprovider eller via en MPLS-forbindelsesudbyder. Se, hvilke [udbydere der er tilgængelige i dit område](/azure/expressroute/expressroute-locations). Den direkte ExpressRoute-forbindelse muliggør forbindelse til de programmer, der er beskrevet i [Hvilke Office 365 tjenester er inkluderet](azure-expressroute.md#BKMK_WhatDoIGet) nedenfor. Netværkstrafik for alle andre programmer og tjenester vil fortsætte med at krydse internettet.

Overvej følgende netværksdiagram på højt niveau, som viser en typisk Office 365 kunde, der opretter forbindelse til Microsofts datacentre via internettet for at få adgang til alle Microsoft-programmer, f.eks. Office 365, Windows Update og TechNet. Kunder bruger en lignende netværkssti, uanset om de opretter forbindelse fra et lokalt netværk eller fra en uafhængig internetforbindelse.

![Office 365 netværksforbindelse.](../media/9d8bc622-4a38-4a3b-a0f3-68657712d460.png)

Se nu det opdaterede diagram, der viser en Office 365 kunde, der bruger både internettet og ExpressRoute til at oprette forbindelse til Office 365. Bemærk, at nogle forbindelser, f.eks. Offentlig DNS og Content Delivery Network noder, stadig kræver den offentlige internetforbindelse. Bemærk også, at kundens brugere, der ikke er placeret i deres Bygning med ExpressRoute-forbindelse, opretter forbindelse via internettet.

![Office 365 forbindelse til ExpressRoute.](../media/251788c4-0937-4584-9b2c-df08e11611fc.png)

Vil du stadig have flere oplysninger? Få mere at vide om, hvordan [du administrerer din netværkstrafik med Azure ExpressRoute til Office 365](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408), og få mere at vide om, hvordan du [konfigurerer Azure ExpressRoute til Office 365](/azure/expressroute/expressroute-faqs). Vi har også optaget en [Azure ExpressRoute på 10 dele til Office 365 træningsserie](https://channel9.msdn.com/series/aer) på Channel 9 for at hjælpe med at forklare koncepterne mere grundigt.

## <a name="what-office-365-services-are-included"></a>Hvilke Office 365 tjenester er inkluderet?
<a name="BKMK_WhatDoIGet"> </a>

I følgende tabel vises de Office 365 tjenester, der understøttes via ExpressRoute. Gennemse [artiklen Office 365 slutpunkter](./urls-and-ip-address-ranges.md) for at forstå, hvilke netværksanmodninger til disse programmer der kræver internetforbindelse.

| Inkluderede programmer |
|:-----|
|Exchange Online <sup>1</sup> <br/> Exchange Online Protection <sup>1</sup> <br/> Delve <sup>1</sup> <br/> |
|Skype for Business Online<sup>1</sup> <br/> Microsoft Teams <sup>1</sup> <br/> |
|SharePoint Online<sup>1</sup> <br/> OneDrive for Business <sup>1</sup> <br/> Project Online <sup>1</sup> <br/> |
|Portal og delt<sup>1</sup> <br/> Azure Active Directory (Azure AD) <sup>1</sup> <br/> Azure AD Forbind <sup>1</sup> <br/> Office <sup>1</sup> <br/> |

<sup>1</sup> Hvert af disse programmer har krav til internetforbindelse, der ikke understøttes via ExpressRoute. Du kan finde flere oplysninger i [artiklen om Office 365 slutpunkter](./urls-and-ip-address-ranges.md).

De tjenester, der ikke er inkluderet i ExpressRoute til Office 365, er Microsoft 365 Apps for enterprise klientoverførsler, logon på identitetsudbyder i det lokale miljø og Office 365 (drevet af 21 Vianet)-tjenesten i Kina.

## <a name="implementing-expressroute-for-office-365"></a>Implementering af ExpressRoute for Office 365

Implementering af ExpressRoute kræver involvering af netværks- og programejere og kræver omhyggelig planlægning for at bestemme den nye [arkitektur for netværksrouting](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408), krav til båndbredde, hvor sikkerhed implementeres, høj tilgængelighed osv. Hvis du vil implementere ExpressRoute, skal du:

1. Fuld forståelse af behovet ExpressRoute opfylder i din Office 365 forbindelse planlægning. Forstå, hvilke programmer der bruger internettet eller ExpressRoute, og planlæg fuldt ud dine behov for netværkskapacitet, sikkerhed og høj tilgængelighed i forbindelse med brug af både internet og ExpressRoute til Office 365 trafik.

2. Bestem udgangs- og peeringplaceringerne for både internet- og ExpressRoute-trafik<sup>1</sup>.

3. Fastlæg den kapacitet, der kræves på internettet og ExpressRoute-forbindelser.

4. Har en plan for implementering af sikkerhed og andre standard perimeterkontroller<sup>1</sup>.

5. Have en gyldig Microsoft Azure konto for at abonnere på ExpressRoute.

6. Vælg en forbindelsesmodel og en [godkendt udbyder](/azure/expressroute/expressroute-locations). Husk, at kunderne kan vælge flere forbindelsesmodeller eller partnere, og partneren behøver ikke at være den samme som din eksisterende netværksudbyder.

7. Valider udrulningen, før trafik dirigeres til ExpressRoute.

8. Implementer eventuelt [QoS](https://support.office.com/article/ExpressRoute-and-QoS-in-Skype-for-Business-Online-20c654da-30ee-4e4f-a764-8b7d8844431d) , og evaluer regional udvidelse.

<sup>1</sup> Vigtige overvejelser i forbindelse med ydeevnen. Beslutninger her kan påvirke ventetiden dramatisk, hvilket er afgørende for programmer som f.eks. Skype for Business.

Hvis du vil have flere referencer, skal du bruge vores [routingvejledning](https://support.office.com/article/Routing-with-ExpressRoute-for-Office-365-e1da26c6-2d39-4379-af6f-4da213218408) ud over [dokumentationen til ExpressRoute](/azure/expressroute/expressroute-introduction).

Hvis du vil købe ExpressRoute til Office 365, skal du samarbejde med en eller flere [godkendte udbydere](/azure/expressroute/expressroute-locations) om at klargøre det ønskede antal og størrelseskredsløb med et ExpressRoute-Premium-abonnement. Der er ingen yderligere licenser at købe fra Office 365.

Her er et kort link, du kan bruge til at vende tilbage: [https://aka.ms/expressrouteoffice365]()

Er du klar til at tilmelde dig [ExpressRoute til Office 365](https://aka.ms/ert)?

## <a name="related-topics"></a>Relaterede emner

[Vurdering af Office 365 netværksforbindelse](assessing-network-connectivity.md)

[Administration af ExpressRoute for Office 365 forbindelse](managing-expressroute-for-connectivity.md)

[Routing med ExpressRoute til Office 365](routing-with-expressroute.md)

[Netværksplanlægning med ExpressRoute til Office 365](network-planning-with-expressroute.md)

[Implementering af ExpressRoute for Office 365](implementing-expressroute.md)

[Brug af BGP-communities i ExpressRoute til Office 365 scenarier](bgp-communities-in-expressroute.md)

[Mediekvalitet og ydeevne for netværksforbindelsen i Skype for Business Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)

[Office 365 justering af ydeevnen ved hjælp af grundlinjer og ydeevnehistorik](performance-tuning-using-baselines-and-history.md)

[Plan for fejlfinding af ydeevnen for Office 365](performance-troubleshooting-plan.md)

[Office 365-URL-adresser og IP-adresseintervaller](urls-and-ip-address-ranges.md)

[Office 365 netværk og justering af ydeevne](network-planning-and-performance.md)

## <a name="see-also"></a>Se også

[oversigt over Microsoft 365 Enterprise](microsoft-365-overview.md)
