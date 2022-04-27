---
title: Konfigurer netværket til Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 11/19/2019
audience: ITPro
ms.topic: landing-page
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
description: Find links til artikler med oplysninger, der kan hjælpe dig med at konfigurere dit netværk til Microsoft 365, herunder en oversigt over netværksforbindelsen og en liste over slutpunkter.
ms.openlocfilehash: 8651fa23983cddf243081248bf1e03fb067232e2
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65092839"
---
# <a name="set-up-your-network-for-microsoft-365"></a>Konfigurer netværket til Microsoft 365

*Denne artikel gælder både for Microsoft 365 Enterprise og Office 365 Enterprise.*

En vigtig del af din Microsoft 365 onboarding er at sikre, at dine netværks- og internetforbindelser er konfigureret til optimeret adgang. Konfiguration af dit lokale netværk for at få adgang til et globalt distribueret SaaS-cloudmiljø (Software-as-a-Service) er forskelligt fra et traditionelt netværk, der er optimeret til trafik til datacentre i det lokale miljø og en central internetforbindelse. 

Brug disse artikler til at forstå de vigtigste forskelle og til at ændre edge-enheder, klientcomputere og netværk i det lokale miljø for at få den bedste ydeevne for dine brugere i det lokale miljø.

## <a name="how-microsoft-365-networking-works"></a>Sådan fungerer Microsoft 365 netværk

Se disse artikler for at få en oversigt over forbindelsen til Microsoft 365:

- [oversigt over Microsoft 365 netværksforbindelse](microsoft-365-networking-overview.md)
- [Microsoft 365 principper for netværksforbindelse](microsoft-365-network-connectivity-principles.md)
- [Vurderer Microsoft 365 netværksforbindelse](assessing-network-connectivity.md)

Du kan få råd om forbedring af ydeevnen under [Netværksplanlægning og justering af ydeevnen for Microsoft 365](network-planning-and-performance.md).

## <a name="support-microsoft-365-networking-as-a-network-equipment-vendor"></a>Support Microsoft 365 netværk som leverandør af netværksudstyr

Hvis du er leverandør af netværksudstyr, skal du tilmelde dig [Office 365 Netværkspartnerprogram](microsoft-365-networking-partner-program.md). Tilmeld dig programmet for at bygge Office 365 principper for netværksforbindelser i dine produkter og løsninger. 

## <a name="office-365-endpoints"></a>Office 365-slutpunkter

Slutpunkter er sættet af DESTINATIONS-IP-adresser, DNS-domænenavne og URL-adresser til Office 365 trafik på internettet. 

For at optimere ydeevnen for Office 365 cloudbaserede tjenester skal nogle slutpunkter håndteres specielt af dine klientbrowsere og enhederne i edge-netværket. Disse enheder omfatter firewalls, SSL Break and Inspect- og packet inspection-enheder og systemer til forebyggelse af datatab.

Se [Administration af Office 365 slutpunkter](managing-office-365-endpoints.md) for at få flere oplysninger.

Der er i øjeblikket fem forskellige Office 365 cloudmiljøer. Denne tabel fører dig til listen over slutpunkter for hver enkelt.

| Slutpunkter | Beskrivelse |
|:-------|:-----|
| [Verdensomspændende slutpunkter](urls-and-ip-address-ranges.md) | Slutpunkterne for abonnementer på verdensomspændende Office 365, som omfatter USA Government Community Cloud (GCC). |
| [Den amerikanske regering DoD-slutpunkter](microsoft-365-u-s-government-dod-endpoints.md) | Slutpunkterne for abonnementer på USA DoD (Department of Defense). |
| [Den amerikanske regering GCC High slutpunkter](microsoft-365-u-s-government-gcc-high-endpoints.md) | Slutpunkterne for abonnementer på USA Government Community Cloud High (GCC High). |
| [Office 365 drevet af 21Vianet-slutpunkter](urls-and-ip-address-ranges-21vianet.md) | Slutpunkterne for Office 365 drevet af 21Vianet, som er designet til at opfylde behovene for Office 365 i Kina. |
|||

Hvis du vil automatisere hentningen af den nyeste liste over slutpunkter for din Office 365 cloud, skal du se [Office 365 IP-adresse og URL-webtjeneste](microsoft-365-ip-web-service.md).

Du kan finde flere slutpunkter i disse artikler:

- [Yderligere slutpunkter, der ikke er inkluderet i webtjenesten](additional-office365-ip-addresses-and-urls.md)
- [Netværksanmodninger i Office 2016 til Mac](network-requests-in-office-2016-for-mac.md)


## <a name="additional-topics-for-microsoft-365-networking"></a>Flere emner i forbindelse med Microsoft 365 netværk

Se disse artikler for at få mere at vide om specialiserede emner i Microsoft 365 netværk:

- [Content Delivery Networks](content-delivery-networks.md)
- [IPv6-understøttelse i Office 365-tjenester](ipv6-support.md)
- [NAT-understøttelse med Office 365](nat-support-with-microsoft-365.md)

## <a name="expressroute-for-microsoft-365"></a>ExpressRoute til Microsoft 365

Se disse artikler for at få oplysninger om brugen af ExpressRoute til Office 365 trafik:

- [Azure ExpressRoute til Office 365](azure-expressroute.md)
- [Implementering af ExpressRoute for Office 365](implementing-expressroute.md)
- [Netværksplanlægning med ExpressRoute til Office 365](network-planning-with-expressroute.md)
- [Routing med ExpressRoute til Office 365](routing-with-expressroute.md)
