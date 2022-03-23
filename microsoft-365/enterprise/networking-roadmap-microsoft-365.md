---
title: Netværksoversigt for Microsoft 365
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 03/03/2022
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: ''
description: Roadmap til planlægning, implementering og administration af Microsoft 365 netværk.
ms.openlocfilehash: cfefd668f91eb074259d056b3b573b9c0f636bb6
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63590347"
---
# <a name="networking-roadmap-for-microsoft-365"></a>Netværksoversigt for Microsoft 365

Microsoft 365 til virksomheder omfatter samarbejde og produktivitet i skytjenester, Microsoft Intune og mange identitets- og sikkerhedstjenester Microsoft Azure. Alle disse skybaserede tjenester er afhængige af sikkerhed, ydeevne og pålidelighed af forbindelser fra klientenheder via internettet eller dedikerede kredsløb. Microsoft har udviklet en netværksinfrastruktur, der fremhæver ydeevne og integration, for at kunne hoste disse tjenester og gøre dem tilgængelige for kunder over hele verden.

En vigtig del af din Microsoft 365 onboarding er at sikre, at dit netværk og dine internetforbindelser er konfigureret til optimeret adgang. Konfiguration af dit lokale netværk til at få adgang til en globalt distribueret SaaS-sky (Software-as-a-Service) er anderledes end et traditionelt netværk, der er optimeret til trafik til lokale datacentre og en central internetforbindelse.

Brug disse artikler til at forstå de vigtigste forskelle og til at ændre dine edge-enheder, klientcomputere og lokale netværk for at få den bedste ydeevne for dine lokale brugere.

## <a name="plan"></a>Plan

I planlægningsfasen for din netværksimplementeringen:

- [Forstå, Microsoft 365 netværk fungerer](microsoft-365-networking-overview.md)
- [Få mere at vide om principper for netværksforbindelse](microsoft-365-network-connectivity-principles.md)
- [Vurder din aktuelle netværksforbindelse](assessing-network-connectivity.md)
- [Afgør, om ExpressRoute passer til din organisation](network-planning-with-expressroute.md)
- [Planlæg dine netværksenheder](plan-for-network-devices.md)
- [Få konfigureret dit netværk til overførsel](network-and-migration-planning.md)

## <a name="deploy"></a>Installér

I implementeringsfasen for din netværksinstallation:

- [Sørg for, at dit virksomhedsnetværk er optimeret til Microsoft 365 forbindelse](set-up-network-for-microsoft-365.md)
- [Tilføj DNS-domænerne for din organisation](../admin/setup/add-domain.md)
- [Optimer forbindelsen for fjernmedarbejdere ved hjælp af VPN-opdeling](microsoft-365-vpn-split-tunnel.md)
- [Konfigurere CDN for at forbedre netværkets ydeevne](office-365-cdn-quickstart.md)
- [Optimere forbindelsen til Microsoft 365 slutpunkter](microsoft-365-ip-web-service.md)
- Hvis det er nødvendigt, [skal du konfigurere ExpressRoute](azure-expressroute.md)

## <a name="manage"></a>Administrer

I administrationsfasen for din netværksimplementeringen:

- [Test og optimer ved hjælp Microsoft 365 testværktøj til netværksforbindelse](office-365-network-mac-perf-onboarding-tool.md)
- [Sørg for, at dine netværksenheder bruger de nyeste Office 365 slutpunkter](microsoft-365-endpoints.md)
- [Overvåge og finjustere netværksydeevnen](network-planning-and-performance.md)
- [Overvåg din Microsoft 365 forbindelse](monitor-connectivity.md)

## <a name="network-equipment-vendors"></a>Leverandører af netværksudstyr

Hvis du er leverandør af netværksudstyr, skal [du Microsoft 365 Netværkspartnerprogram.](microsoft-365-networking-partner-program.md) Tilmeld dig programmet for at opbygge Microsoft 365 til dine produkter og løsninger.

## <a name="how-contoso-did-networking-for-microsoft-365"></a>Sådan netværker Contoso for Microsoft 365

Se, hvordan Contoso Corporation, en fiktiv men repræsentativ multi national virksomhed, optimerede deres netværksenheder og [internetforbindelser](contoso-networking.md) til Microsoft 365 skytjenester.

![The Contoso Corporation.](../media/contoso-overview/contoso-icon.png)

## <a name="next-step"></a>Næste trin

Start din netværksplanlægning med [oversigten Microsoft 365 netværksforbindelsen](microsoft-365-networking-overview.md).
