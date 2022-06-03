---
title: IPv6-understøttelse i Microsoft 365-tjenester
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 06/02/2022
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: c08786fb-298e-437c-8222-dab7625fc815
description: 'Resumé: Beskriver IPv6-understøttelse i Microsoft 365 komponenter og i Microsoft 365 offentlige tilbud.'
ms.openlocfilehash: 2619567e8dac6f4b87cba0108bcf105011c4a87c
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/03/2022
ms.locfileid: "65872736"
---
# <a name="ipv6-support-in-microsoft-365-services"></a>IPv6-understøttelse i Microsoft 365-tjenester

Med den stigende indførelse og understøttelse af IPv6 på tværs af virksomhedsnetværk, tjenesteudbydere og enheder spekulerer mange kunder på, om deres brugere fortsat kan få adgang til Microsoft 365 tjenester fra IPv6-klienter og IPv6-netværk. Microsoft 365 tjenester kan bruges korrekt fra både IPv6 Dual Stack- og IPv6-enheder. Faktisk har vi et stigende antal kunder, fra forbrugere til store virksomheder, som bevæger sig i retning af større indførelse af IPv6. For de fleste kunder forsvinder IPv4 ikke helt fra deres digitale landskab, så vi planlægger ikke at kræve IPv6 eller at afprioritere IPv4 i nogen Microsoft 365 funktioner eller tjenester.

En af vores vigtigste prioriteter med Microsoft 365 er at sikre problemfri kunde- og brugeroplevelser via internettet fra enhver placering, fra enhver enhed. Dette omfatter adgang til Microsoft 365 fra kundeenheder, der bruger IPv6 i konfigurationen af dobbelt stak, samt overgang til klientinstallationer, der kun er IPv6. Når du i de fleste tilfælde følger en internetbaseret standardmodel for oprettelse af forbindelse til Microsoft 365 som beskrevet i [principperne for Microsoft 365 netværksforbindelse](microsoft-365-network-connectivity-principles.md), [Microsoft 365 URL-adresser og IP-adresseintervaller](urls-and-ip-address-ranges.md) og [Microsoft 365 bedste praksis for netværksplanlægning](network-and-migration-planning.md#best-practices-for-network-planning-and-improving-migration-performance-for-office-365) – IPv6-overgange forstyrrer ikke din brugeroplevelse.

Mange Microsoft 365-tjenester yder allerede indbygget IPv6-understøttelse i dag og kan tilgås direkte fra klienter, der kun har IPv6 og IPv6. Microsoft 365 giver også adgang via konventionelle IPv6-oversættelsesteknologier til IPv4 (f.eks. basis 64 proxyer eller DNS64/NAT64), der ofte bruges af kunder og netværksløsningsudbydere til at oprette forbindelse til IPv4-internetressourcer.

Som med alle SaaS-tjenester og internettet generelt udvides omfanget af indbygget IPv6-aktiverede Microsoft 365 grænseflader, funktioner og API'er løbende og uden direkte kundehandling eller -kontrol. Hvis du kører IPv6- eller IPv6-tjenester på dine netværk, der har brug for adgang til Microsoft 365 og internettet, anbefales det, at du inkluderer dynamiske overgangsmekanismer for IPv6/IPv4, f.eks. DNS64/NAT64, for at sikre, at end-to-end IPv6-forbindelsen Microsoft 365 uden yderligere netværkskonfigurationer.

De fleste Microsoft 365 tjenester er blevet eller vil blive aktiveret med IPv6-funktioner helt gennemsigtigt for slutbrugere og it-administratorer. Nogle Microsoft 365 scenarier (f.eks. anonym indgående mail) har særlige krav og overvejelser til brug sammen med IPv6. Kontakt dit Microsoft-kontoteam eller Microsoft-support for at få flere oplysninger om scenariespecifikke IPv6-krav og -overvejelser.

Her er et kort link, du kan bruge til at vende tilbage: [https://aka.ms/o365ip6](https://aka.ms/o365ip6)

## <a name="see-also"></a>Se også

[oversigt over Microsoft 365 Netværksforbindelse](microsoft-365-networking-overview.md)

[Administrere Office 365-slutpunkter](managing-office-365-endpoints.md)

[Office 365-URL-adresser og IP-adresseintervaller](urls-and-ip-address-ranges.md)

[Office 365 IP-adresse og URL-adressewebtjeneste](microsoft-365-ip-web-service.md)

[Vurderer Microsoft 365 netværksforbindelse](assessing-network-connectivity.md)

[Netværksplanlægning og justering af ydeevnen for Microsoft 365](network-planning-and-performance.md)

[Office 365 justering af ydeevnen ved hjælp af grundlinjer og ydeevnehistorik](performance-tuning-using-baselines-and-history.md)

[Plan for fejlfinding af ydeevnen for Office 365](performance-troubleshooting-plan.md)

[Netværk til levering af indhold](content-delivery-networks.md)

[Microsoft 365 forbindelsestest](https://aka.ms/netonboard)

[Sådan bygger Microsoft sit hurtige og pålidelige globale netværk](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)

[Office 365 netværksblog](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)
