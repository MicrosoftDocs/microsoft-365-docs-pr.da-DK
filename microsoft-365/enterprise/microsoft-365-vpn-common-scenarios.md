---
title: Almindelige scenarier for opdeling af VPN-Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 3/3/2022
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- remotework
f1.keywords:
- NOCSH
description: Almindelige scenarier for opdeling af VPN-Microsoft 365
ms.openlocfilehash: 26f4cf10de3282c5257592a26ea61d073a0d3cd4
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63705175"
---
# <a name="common-vpn-split-tunneling-scenarios-for-microsoft-365"></a>Almindelige scenarier for opdeling af VPN-Microsoft 365

>[!NOTE]
>Denne artikel er en del af et sæt artikler, der adresserer Microsoft 365 optimering for eksterne brugere.

>- Du kan få et overblik over, hvordan du bruger VPN-opdelte forbindelser til at optimere Microsoft 365 forbindelse for eksterne brugere, under [Oversigt: VPN-opdelt Microsoft 365](microsoft-365-vpn-split-tunnel.md).
>- Hvis du vil have detaljeret vejledning til implementering af VPN-opdeling, skal du [se Implementering af VPN-opdeling for at Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md).
>- Du kan finde en vejledning til sikring Teams medietrafik i VPN-opdelte netværksmiljøer under Sikring [Teams medietrafik til VPN-opdelte netværkstrafik](microsoft-365-vpn-securing-teams.md).
>- Du kan finde oplysninger om, hvordan du konfigurerer Stream og livebegivenheder i VPN-miljøer, under Særlige overvejelser [i forbindelse med Stream og livebegivenheder i VPN-miljøer](microsoft-365-vpn-stream-and-live-events.md).
>- Du kan finde oplysninger om optimering Microsoft 365 globale lejerydeevne for brugere i Kina under [Microsoft 365 optimering af ydeevnen for Brugere i Kina](microsoft-365-networking-china.md).

På listen herunder kan du se de mest almindelige VPN-scenarier i virksomhedsmiljøer. De fleste kunder har traditionelt model 1 (VPN Forced Tunnel). Dette afsnit hjælper dig med hurtigt og sikkert at overgå til **model 2**, som er opnåeligt med relativ lille indsats, og har enorme fordele ved netværkets ydeevne og brugeroplevelse.

| Model | Beskrivelse |
| --- | --- |
| [1. VPN gennemtvungne Tunnel](#1-vpn-forced-tunnel) | 100 % af trafikken går til VPN-trafik, herunder lokalt, internet og alt O365/M365 |
| [2. VPN gennemtvungne Tunnel med få undtagelser](#2-vpn-forced-tunnel-with-a-small-number-of-trusted-exceptions) | VPN-bro bruges som standard (standardrutepunkter til VPN) med få, vigtigste undtaget scenarier, der har tilladelse til at gå direkte |
| [3. VPN gennemtvungne Tunnel med generelle undtagelser](#3-vpn-forced-tunnel-with-broad-exceptions) | VPN-arkitekturen bruges som standard (standardrutepunkter til VPN) med generelle undtagelser, der har tilladelse til at gå direkte (f.eks. alle Microsoft 365, Alle Salesforce, Alle Zoom) |
| [4. VPN-selektivt Tunnel](#4-vpn-selective-tunnel) | VPN-vpn-vpn bruges kun til corpnet-baserede tjenester. Standardrute (internet og alle internetbaserede tjenester) går direkte. |
| [5. Intet VPN](#5-no-vpn) | En variant af #2. I stedet for det ældre VPN publiceres alle corpnet-tjenester via moderne sikkerhedstilgange (f.eks. Zscaler ZPA, Azure Active Directory (Azure AD) Proxy/MCAS osv.) |

## <a name="1-vpn-forced-tunnel"></a>1. VPN gennemtvungne Tunnel

Det mest almindelige startscenarie for de fleste virksomhedskunder. Et gennemtvunget VPN bruges, hvilket betyder, at 100 % af trafikken dirigeres til virksomhedens netværk, uanset om slutpunktet er placeret inden for virksomhedens netværk eller ej. Ekstern (internet) bundet trafik, f.eks. Microsoft 365 eller internetbrowsing, bliver derefter hair-fastgjort ud af det lokale sikkerhedsudstyr, f.eks. proxyer. I den aktuelle situation med næsten 100 % af brugere, der arbejder eksternt, lægger denne model derfor høj belastning på VPN-infrastrukturen og er sandsynligvis en væsentlig aflastning af ydeevnen for al virksomhedstrafik og dermed virksomheden til at fungere effektivt på et tidspunkt med krise.

![VPN Gennemtvunget Tunnel model 1.](../media/vpn-split-tunneling/vpn-model-1.png)

## <a name="2-vpn-forced-tunnel-with-a-small-number-of-trusted-exceptions"></a>2. VPN gennemtvungne Tunnel med et lille antal undtagelser, der er tillid til

Markant mere effektiv for en virksomhed at arbejde under. Denne model tillader et par kontrollerede og definerede slutpunkter, der er høj belastning og ventetid følsom for at omgå VPN-forbindelsen og gå direkte til Microsoft 365 tjeneste. Dette forbedrer ydeevnen betydeligt for de aflastede tjenester og reducerer også belastningen på VPN-infrastrukturen, så elementer, der stadig kræver det, kan fungere med lavere indholdsoverensstemmelse for ressourcer. Det er denne model, som denne artikel fokuserer på at hjælpe med overgangen, da den gør det muligt hurtigt at udføre enkle, definerede handlinger med mange positive resultater.

![Opdel Tunnel VPN-model 2.](../media/vpn-split-tunneling/vpn-model-2.png)

## <a name="3-vpn-forced-tunnel-with-broad-exceptions"></a>3. VPN gennemtvungne Tunnel med generelle undtagelser

Udvider omfanget af model 2. I stedet for blot at sende en lille gruppe af definerede slutpunkter direkte sender den i stedet al trafik direkte til pålidelige tjenester Microsoft 365 og SalesForce. Dette reducerer belastningen af virksomhedens VPN-infrastruktur yderligere og forbedrer ydeevnen for de definerede tjenester. Da denne model sandsynligvis vil tage længere tid at vurdere vurder og implementere, er det sandsynligvis et trin, der kan tages iterativt på et senere tidspunkt, når model to er på plads.

![Opdel Tunnel VPN-model 3.](../media/vpn-split-tunneling/vpn-model-3.png)

## <a name="4-vpn-selective-tunnel"></a>4. VPN-selektivt Tunnel

Vender den tredje model om på, at kun trafik, der identificeres som havende en virksomheds IP-adresse, sendes ned gennem VPN-kanalen, og således er internetstien standardruteen for alt andet. Denne model kræver, at en organisation er godt på rette spor til [Nul tillid](https://www.microsoft.com/security/zero-trust?rtc=1) i stand til sikkert at implementere denne model. Det skal bemærkes, at denne model eller en variant heraf sandsynligvis vil blive den nødvendige standard over tid, efterhånden som flere tjenester flyttes væk fra virksomhedens netværk og ind i skyen.

Microsoft bruger denne model internt. Du kan finde flere oplysninger om Microsofts implementering af VPN-opdeling ved at køre på [VPN: Sådan holder Microsoft sin eksterne arbejdsstyrke forbundet](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv).

![Opdel Tunnel VPN-model 4.](../media/vpn-split-tunneling/vpn-model-4.png)

## <a name="5-no-vpn"></a>5. Intet VPN

En mere avanceret version af model nummer 2, hvor alle interne tjenester publiceres via en moderne sikkerheds tilgang eller SDWAN-løsning som Azure AD Proxy, Defender for Cloud Apps, Zscaler ZPA osv.

![Opdel Tunnel VPN-model 5.](../media/vpn-split-tunneling/vpn-model-5.png)

## <a name="related-articles"></a>Relaterede artikler

[Oversigt: VPN-opdeling af Microsoft 365](microsoft-365-vpn-split-tunnel.md)

[Implementering af VPN-opdeling af Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md)

[Sikring Teams medietrafik til VPN-opdelte netværkstrafik](microsoft-365-vpn-securing-teams.md)

[Særlige overvejelser i forbindelse med Stream og livebegivenheder i VPN-miljøer](microsoft-365-vpn-stream-and-live-events.md)

[Microsoft 365 optimering af ydeevnen for Kinas brugere](microsoft-365-networking-china.md)

[Microsoft 365 principper for netværksforbindelse](microsoft-365-network-connectivity-principles.md)

[Vurdering Microsoft 365 af netværksforbindelsen](assessing-network-connectivity.md)

[Microsoft 365 netværk og justering af ydeevnen](network-planning-and-performance.md)

[Alternative måder for sikkerhedsmedarbejdere og it-medarbejdere til at opnå moderne sikkerhedskontrolelementer i dagens unikke scenarier for fjernarbejde (Microsoft Security Team-blog)](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)

[Forbedring af VPN-ydeevnen hos Microsoft: brug Windows 10 VPN-profiler til at tillade automatiske til-forbindelser](https://www.microsoft.com/itshowcase/enhancing-remote-access-in-windows-10-with-an-automatic-vpn-profile)

[Kører på VPN: Sådan holder Microsoft sin eksterne arbejdsstyrke forbundet](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv)

[Microsofts globale netværk](/azure/networking/microsoft-global-network)
