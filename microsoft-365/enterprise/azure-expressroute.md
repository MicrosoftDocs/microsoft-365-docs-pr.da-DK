---
title: Azure ExpressRoute til Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Få mere at vide om, hvordan du bruger Azure ExpressRoute Office 365 og planlægger projekt for netværksimplementeringen, hvis du installerer med programmet.
ms.openlocfilehash: 9a4f4be76751ec03610bd766f51ec91526ca18a4
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63601557"
---
# <a name="azure-expressroute-for-office-365"></a>Azure ExpressRoute til Office 365

*Denne artikel gælder for både Microsoft 365 Enterprise og Office 365 Enterprise.*

Få mere at vide om, hvordan Azure ExpressRoute bruges sammen med Office 365, og hvordan du planlægger det projekt for netværksimplementeringen, der vil være påkrævet, hvis du installerer Azure ExpressRoute til brug med Office 365. Infrastruktur og platformstjenester, der kører i Azure, vil ofte drage fordel af at tage hensyn til netværksarkitektur og overvejelser om ydeevne. Vi anbefaler ExpressRoute til Azure i disse tilfælde. Software som et servicetilbud som Office 365 og Dynamics 365 er blevet bygget til at blive åbnet sikkert og pålideligt via internettet. Du kan læse om internetydeevne og -sikkerhed, og hvornår du kan overveje Azure ExpressRoute til Office 365 i artiklen Vurdere [Office 365 netværksforbindelsen](assessing-network-connectivity.md).

> [!NOTE]
> Microsoft Defender til Slutpunkt leverer ikke integration med Azure ExpressRoute. Selvom dette ikke stopper kunder i at definere ExpressRoute-regler, der gør det muligt at oprette forbindelse fra et privat netværk til Microsoft Defender for Endpoint-skytjenester, er det op til kunden at opretholde regler, efterhånden som tjenesten eller skyinfrastrukturen udvikles.

> [!NOTE]
> Vi anbefaler ikke ExpressRoute til Microsoft 365, fordi det under de fleste omstændigheder ikke giver den bedste forbindelsesmodel for tjenesten. Derfor kræves Microsoft-autorisation for at bruge denne forbindelsesmodel til Microsoft 365. Vi gennemser alle kundeanmodninger og godkender kun ExpressRoute Microsoft 365 i de sjældne scenarier, hvor det er nødvendigt. Læs [ExpressRoute til Microsoft 365-vejledningen for](https://aka.ms/erguide) at få flere oplysninger, og følg en omfattende gennemgang af dokumentet med produktivitets-, netværks- og sikkerhedsteams, arbejd sammen med dit Microsoft-kontoteam om at indsende en undtagelse, hvis det er nødvendigt. Uautoriserede abonnementer, der forsøger at oprette rutefiltre til Office 365, modtager [en fejlmeddelelse](https://support.microsoft.com/kb/3181709).

## <a name="planning-azure-expressroute-for-office-365"></a>Planlægning af Azure ExpressRoute til Office 365

Ud over internetforbindelse kan du vælge at distribuere et undersæt af deres Office 365-netværkstrafik via en direkte forbindelse, som tilbyder forudsigelighed og en SLA 99,95 % oppetid for Microsoft-netværkskomponenter. Azure ExpressRoute giver dig denne dedikerede netværksforbindelse til Office 365 og andre Microsoft-skytjenester.

Uanset om du har et eksisterende MPLS WAN, kan ExpressRoute føjes til din netværksarkitektur på én af tre måder: via en understøttet cloud exchange-coplaceringsudbyder, en Ethernet punkt-til-punkt-forbindelsesudbyder eller via en MPLS-forbindelsesudbyder. Se, [hvilke udbydere der er tilgængelige i dit område](/azure/expressroute/expressroute-locations). Den direkte ExpressRoute-forbindelse aktiverer forbindelsen til de programmer, der er [beskrevet i Hvilke Office 365 er inkluderet?](azure-expressroute.md#BKMK_WhatDoIGet) nedenfor. Netværkstrafik for alle andre programmer og tjenester fortsætter med at krydse internettet.

Overvej følgende netværksdiagram på højt niveau, som viser en typisk Office 365-kunde, der opretter forbindelse til Microsofts datacentre via internettet for at få adgang til alle Microsoft-programmer som Office 365, Windows Update og TechNet. Kunder bruger en lignende netværkssti, uanset om de opretter forbindelse fra et lokalt netværk eller fra en uafhængig internetforbindelse.

![Office 365 netværksforbindelsen.](../media/9d8bc622-4a38-4a3b-a0f3-68657712d460.png)

Kig nu på det opdaterede diagram, der afbilder en Office 365, der bruger både internettet og ExpressRoute til at oprette forbindelse til Office 365. Bemærk, at nogle forbindelser, f.eks. offentlig DNS Content Delivery Network noder, stadig kræver en offentlig internetforbindelse. Bemærk også, at kundens brugere, der ikke befinder sig i deres ExpressRoute-forbundne bygning, opretter forbindelse via internettet.

![Office 365 forbindelse med ExpressRoute.](../media/251788c4-0937-4584-9b2c-df08e11611fc.png)

Vil du stadig have flere oplysninger? Få mere at vide om, hvordan du administrerer din netværkstrafik [med Azure ExpressRoute til Office 365](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408) og få mere at vide om, hvordan du [konfigurerer Azure ExpressRoute til Office 365](/azure/expressroute/expressroute-faqs). Vi har også indspillet en [Azure ExpressRoute](https://channel9.msdn.com/series/aer) til 10 dele til Office 365-kursusserie på kanal 9 for at forklare begreberne grundigere.

## <a name="what-office-365-services-are-included"></a>Hvilke Office 365 tjenester er inkluderet?
<a name="BKMK_WhatDoIGet"> </a>

I følgende tabel vises de Office 365, der understøttes over ExpressRoute. Gennemgå artiklen om [Office 365 slutpunkter for at forstå,](./urls-and-ip-address-ranges.md) hvilke netværksanmodninger til disse programmer kræver forbindelse til internettet.

| Inkluderede programmer |
|:-----|
|Exchange Online <sup>1</sup> <br/> Exchange Online Protection <sup>1</sup> <br/> Delve <sup>1</sup> <br/> |
|Skype for Business <sup>Online1</sup> <br/> Microsoft Teams <sup>1</sup> <br/> |
|SharePoint <sup>Online1</sup> <br/> OneDrive for Business <sup>1</sup> <br/> Project Online <sup>1</sup> <br/> |
|Portal og <sup>delt1</sup> <br/> Azure Active Directory (Azure AD) <sup>1</sup> <br/> Azure AD Forbind <sup>1</sup> <br/> Office <sup>1</sup> <br/> |

<sup>1</sup> Hvert af disse programmer har krav til internetforbindelse, der ikke understøttes via ExpressRoute, se artiklen [Office 365-slutpunkter](./urls-and-ip-address-ranges.md) for at få flere oplysninger.

De tjenester, der ikke er inkluderet i ExpressRoute til Office 365, er Microsoft 365 Apps for enterprise-klientoverførsler, logon på lokale identitetsudbydere og Office 365 (drevet af 21 Vianet) i Kina.

## <a name="implementing-expressroute-for-office-365"></a>Implementering af ExpressRoute til Office 365

Implementering af ExpressRoute kræver deltagelse af netværk og programejere og kræver nøje planlægning for at fastlægge den nye netværksroutingarkitektur [, krav](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408) til båndbredde, hvor sikkerhed vil blive implementeret, høj tilgængelighed osv. For at implementere ExpressRoute skal du:

1. Forstå det behov, ExpressRoute opfylder i din Office 365 forbindelsesplanlægning. Forstå, hvilke programmer vil bruge internettet eller ExpressRoute og fuldt ud planlægge din netværkskapacitet, sikkerhed og behov for høj tilgængelighed i forbindelse med brug af både internettet og ExpressRoute til Office 365 trafik.

2. Bestemme udgangspunktet og peeringplaceringerne for både internet- og <sup>ExpressRoute-trafik1</sup>.

3. Afgør den påkrævede kapacitet på internet- og ExpressRoute-forbindelserne.

4. Have en plan på plads for implementering af sikkerhed og andre almindelige <sup>kontrolelementer1</sup>.

5. Have en gyldig Microsoft Azure til at abonnere på ExpressRoute.

6. Vælg en forbindelsesmodel og en [godkendt udbyder](/azure/expressroute/expressroute-locations). Husk, at kunder kan vælge flere forbindelsesmodeller eller -partnere, og partneren behøver ikke at være den samme som din eksisterende netværksudbyder.

7. Valider installation, før du dirigerer trafik til ExpressRoute.

8. Du kan [også implementere QoS og](https://support.office.com/article/ExpressRoute-and-QoS-in-Skype-for-Business-Online-20c654da-30ee-4e4f-a764-8b7d8844431d) evaluere regional udvidelse.

<sup>1 Vigtige</sup> overvejelser om ydeevne. Beslutninger kan her påvirke ventetid dramatisk, hvilket er afgørende for programmer som f.eks. Skype for Business.

For yderligere referencer kan du [bruge vores routingvejledning](https://support.office.com/article/Routing-with-ExpressRoute-for-Office-365-e1da26c6-2d39-4379-af6f-4da213218408) ud over [ExpressRoute-dokumentationen](/azure/expressroute/expressroute-introduction).

For at købe ExpressRoute til Office 365 skal du arbejde med en eller flere godkendte udbydere for at klargøre det ønskede antal og størrelse af kredsløb med et ExpressRoute Premium abonnement.[](/azure/expressroute/expressroute-locations) Der er ingen yderligere licenser at købe fra Office 365.

Her er et kort link, du kan bruge til at vende tilbage: [https://aka.ms/expressrouteoffice365]()

Er du klar til at tilmelde [dig ExpressRoute til Office 365](https://aka.ms/ert)?

## <a name="related-topics"></a>Relaterede emner

[Vurdering Office 365 netværksforbindelsen](assessing-network-connectivity.md)

[Administrere ExpressRoute til Office 365 forbindelse](managing-expressroute-for-connectivity.md)

[Routing med ExpressRoute til Office 365](routing-with-expressroute.md)

[Netværksplanlægning med ExpressRoute til Office 365](network-planning-with-expressroute.md)

[Implementering af ExpressRoute til Office 365](implementing-expressroute.md)

[Brug af BGP-communities i ExpressRoute til Office 365 scenarier](bgp-communities-in-expressroute.md)

[Mediekvalitet og ydeevne for netværksforbindelse i Skype for Business Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)

[Office 365 justering af ydeevnen ved hjælp af grundlinjer og ydeevnehistorik](performance-tuning-using-baselines-and-history.md)

[Fejlfinding af ydeevne i forbindelse med planen for Office 365](performance-troubleshooting-plan.md)

[Office 365-URL-adresser og IP-adresseintervaller](urls-and-ip-address-ranges.md)

[Office 365 netværk og justering af ydeevnen](network-planning-and-performance.md)

## <a name="see-also"></a>Se også

[Microsoft 365 Enterprise oversigt](microsoft-365-overview.md)
