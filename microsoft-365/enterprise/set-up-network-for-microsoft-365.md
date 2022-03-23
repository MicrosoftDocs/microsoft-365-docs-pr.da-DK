---
title: Konfigurer dit netværk til Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/19/2019
audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_TLGs
- seo-marvel-apr2020
ms.assetid: ''
description: Find links til artikler med oplysninger, der kan hjælpe dig med at konfigurere dit netværk til Microsoft 365, herunder en oversigt over netværksforbindelser og en liste over slutpunkter.
ms.openlocfilehash: c21a7a09e43957c806bca9dd64d425fcef2415fc
ms.sourcegitcommit: 59b1b0abfde30a8f2d8210b696aac3dc9183544e
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/18/2021
ms.locfileid: "63591562"
---
# <a name="set-up-your-network-for-microsoft-365"></a>Konfigurer dit netværk til Microsoft 365

*Denne artikel gælder for både Microsoft 365 Enterprise og Office 365 Enterprise.*

En vigtig del af din Microsoft 365 onboarding er at sikre, at dit netværk og dine internetforbindelser er konfigureret til optimeret adgang. Konfiguration af dit lokale netværk til at få adgang til en globalt distribueret SaaS-sky (Software-as-a-Service) er anderledes end et traditionelt netværk, der er optimeret til trafik til lokale datacentre og en central internetforbindelse. 

Brug disse artikler til at forstå de vigtigste forskelle og til at ændre dine edge-enheder, klientcomputere og lokale netværk for at få den bedste ydeevne for dine lokale brugere.

## <a name="how-microsoft-365-networking-works"></a>Sådan Microsoft 365 netværk fungerer

Se disse artikler for at få en oversigt over forbindelsen til Microsoft 365:

- [Microsoft 365 over netværksforbindelse](microsoft-365-networking-overview.md)
- [Microsoft 365 principper for netværksforbindelse](microsoft-365-network-connectivity-principles.md)
- [Vurdering Microsoft 365 af netværksforbindelsen](assessing-network-connectivity.md)

Få råd om forbedring af ydeevnen under [Netværksplanlægning og justering af ydeevnen for Microsoft 365](network-planning-and-performance.md).

## <a name="support-microsoft-365-networking-as-a-network-equipment-vendor"></a>Support Microsoft 365 netværk som leverandør af netværksudstyr

Hvis du er leverandør af netværksudstyr, kan du deltage [i Office 365 Netværkspartnerprogram](microsoft-365-networking-partner-program.md). Tilmeld dig programmet for at opbygge Office 365 til dine produkter og løsninger. 

## <a name="office-365-endpoints"></a>Office 365 slutpunkter

Slutpunkter er sættet af DESTINATIONS-IP-adresser, DNS-domænenavne og URL-adresser til Office 365 til trafik på internettet. 

For at optimere ydeevnen Office 365 skybaserede tjenester skal nogle slutpunkter have særlig håndtering af dine klientbrowsere og enhederne i dit grænsenetværk. Disse enheder omfatter firewalls, SSL Break og Inspect- og pakkeinspektionsenheder og systemer til forebyggelse af datatab.

Se [Office 365 og slutpunkter](managing-office-365-endpoints.md) for at få flere oplysninger.

Der er i øjeblikket fem Office 365 skyer. Denne tabel fører dig til listen over slutpunkter for hver enkelt.

| Slutpunkter | Beskrivelse |
|:-------|:-----|
| [Verdensomspændende slutpunkter](urls-and-ip-address-ranges.md) | Slutpunkterne for verdensomspændende abonnementer Office 365, som omfatter USA Government Community Cloud (GCC). |
| [Amerikanske Government DoD-slutpunkter](microsoft-365-u-s-government-dod-endpoints.md) | Slutpunkterne for det amerikanske forsvarsministerium (DoD) abonnementer. |
| [Amerikanske Government GCC High-slutpunkter](microsoft-365-u-s-government-gcc-high-endpoints.md) | Slutpunkterne for abonnementer af Government Community Cloud High (GCC High). |
| [Office 365 drevet af 21Vianet-slutpunkter](urls-and-ip-address-ranges-21vianet.md) | Slutpunkterne for Office 365 drevet af 21Vianet, som er designet til at opfylde behovene Office 365 i Kina. |
|||

Hvis du vil automatisere med at hente den seneste liste over slutpunkter til din Office 365-sky, skal du [se Office 365 IP-adresse og URL-webtjeneste](microsoft-365-ip-web-service.md).

Du kan finde flere slutpunkter i følgende artikler:

- [Yderligere slutpunkter, der ikke er inkluderet i webtjenesten](additional-office365-ip-addresses-and-urls.md)
- [Netværksanmodninger i Office 2016 til Mac](network-requests-in-office-2016-for-mac.md)


## <a name="additional-topics-for-microsoft-365-networking"></a>Flere emner om Microsoft 365 netværk

Se disse artikler om specialiserede emner i Microsoft 365 netværket:

- [Netværk, der kan levere indhold](content-delivery-networks.md)
- [IPv6-understøttelse i Office 365 tjenester](ipv6-support.md)
- [NAT-understøttelse med Office 365](nat-support-with-microsoft-365.md)

## <a name="expressroute-for-microsoft-365"></a>ExpressRoute til Microsoft 365

Se disse artikler for at få oplysninger om brug af ExpressRoute til Office 365 trafik:

- [Azure ExpressRoute til Office 365](azure-expressroute.md)
- [Implementering af ExpressRoute til Office 365](implementing-expressroute.md)
- [Netværksplanlægning med ExpressRoute til Office 365](network-planning-with-expressroute.md)
- [Routing med ExpressRoute til Office 365](routing-with-expressroute.md)
