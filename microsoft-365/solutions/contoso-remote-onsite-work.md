---
title: Contosos COVID-19-svar og support til hybridarbejde
author: dansimp
f1.keywords:
- NOCSH
ms.author: dansimp
manager: dansimp
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: ''
description: Få mere at vide om, hvordan Contoso Corporation reagerede på COVID-19-teknikere og udviklede deres softwareinstallations- og opdateringsinfrastruktur til hybridarbejde.
ms.openlocfilehash: 8b3829b7d3361c3a29ee495dd5a335a28a08c0b4
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63591508"
---
# <a name="contosos-covid-19-response-and-support-for-hybrid-work"></a>Contosos COVID-19-svar og support til hybridarbejde

Contoso havde altid understøttet sine fjernarbejdere, der tilgås lokale ressourcer via en central VPN-server i Paris's hovedkvarter. Contoso havde udstedt en administreret bærbar computer til alle eksterne medarbejdere. Lokale medarbejdere havde en blanding af stationære og bærbare computere.

## <a name="contosos-response-to-covid-19"></a>Contosos svar på COVID-19

Da COVID-19 blev fjernet, var pludselig alle andre end vigtige medarbejdere eksterne medarbejdere. Contoso har svaret igen ved at flytte sine medarbejdere til arbejde hjemmefra og udføre sine primære aktiviteter via fjernadgang til lokale ressourcer og online ved hjælp Microsoft 365 skytjenester.

Contoso havde VPN-servere med fjernadgang i hovedkontoret i Paris til at understøtte de 25 % af sine allerede eksterne medarbejdere, men blev hurtigt flyttet for at opskalere sin eksterne adgangskapacitet til at understøtte 90 % af medarbejderne. Contoso har installeret VPN-fjernadgangsservere i hvert satellitkontor, så eksterne medarbejdere kan bruge et regionalt luk indgangspunkt til at få adgang til Contoso-intranettet.

Contoso opdaterede også konfigurationen af VPN-klienter, der er installeret på bærbare computere, tablets og smartphones, til at opdele netværksforbindelse, så trafik til optimer sæt Office 365-slutpunkter tilsidesættede VPN-forbindelsen og blev sendt direkte via internettet. Få mere at vide under [Optimer Office 365 forbindelse for eksterne brugere ved hjælp af VPN-opdeling](../enterprise/microsoft-365-vpn-split-tunnel.md).

Her er den resulterende konfiguration med VPN-enheder, der er installeret i Paris's hovedkvarter og hvert af de satellitkontorer. 

![Contosos VPN-infrastruktur.](../media/contoso-remote-onsite-work/contoso-vpn-infrastructure.png)

En fjernmedarbejder med den installerede VPN-klient bruger DNS til at finde det regionalt nærmeste kontor og opretter forbindelse til den VPN-enhed, der er installeret der. Med opdelte nedføringer sendes trafik Microsoft 365 Optimer slutpunkter direkte til de Microsoft 365 på netværksplaceringen. Al anden trafik bliver sendt via VPN-forbindelsen til VPN-enheden.

## <a name="contosos-support-for-hybrid-work"></a>Contosos understøttelse af hybridarbejde

Efter de første ændringer blev foretaget for primært at understøtte eksterne medarbejdere under regionale fastlåsninger, har Contoso foretaget ændringer i infrastrukturen for at understøtte hybridarbejde, hvor en medarbejder kunne:

- Altid fjern.
- Altid på stedet.
- En kombination af onsite og remote.

Microsoft 365 identitets-, sikkerheds- og overholdelsesfunktioner er designet til Zero Trust og til at fungere, uanset placeringen af brugeren og dennes enhed. Du kan få mere at vide under [Nul tillid](https://www.microsoft.com/security/business/zero-trust).

Administration af nye installationer og opdateringer af software afhænger dog af placeringen af enheden, fordi den software, der skal installeres, kan komme fra en lokal eller en internetkilde. Contoso IT-arkitekter designede deres nye installationer og opdaterer infrastruktur baseret på placeringen af enheden i stedet for arbejderen.

De udpegede to typer enheder: dedikeret til det lokale miljø og roaming.

### <a name="dedicated-on-premises"></a>Dedikeret lokalt miljø

En dedikeret lokal enhed er en stationær computer eller servercomputer, der aldrig forlader Contoso-intranettet og ikke har en VPN-klient installeret. Disse lokale enheder fortsætter med at bruge Microsoft Endpoint Configuration Manager og dets distributionspunkter til installationer og opdateringer af Windows 10, Microsoft 365 Apps for enterprise og Microsoft Edge-browseren.

### <a name="roaming"></a>Roaming

En roamingenhed kan forlade Contoso-intranettet og omfatter bærbare computere, der er udstedt til mange kontormedarbejdere og alle eksterne medarbejdere og andre enheder, der ejes af organisationen, f.eks. smartphones og tablets, hvor Contoso VPN-klienten er installeret. 

Da disse enheder kan have forbindelse til internettet når som helst, bruger de Intune eller andre skybaserede tjenester til installationer og opdateringer af Windows 10, Microsoft 365 Apps for enterprise og Edge. De bruger ikke de eksisterende lokale Konfigurationsstyring eller distributionspunkter.

Det betyder, at nogle af installationer og opdateringer til globale enheder vil blive udført via internettet, mens de er lokale og har forbindelse til intranettet. Men Contoso IT-arkitekter besluttede, at enkelhed i konfiguration var vigtigere end optimering af intranetbåndbredden til internettet, især når de fleste fjernmedarbejdere sjældent har forbindelse til intranettet.

Her er den resulterende infrastruktur.

![Contosos installationer og opdateringer af infrastruktur.](../media/contoso-remote-onsite-work/contoso-updates-infrastructure.png)

Installations- og opdateringsfunktionsmåden bestemmes ved at gøre computerkontiene for enheder til medlem af en af disse grupper:

- OnPremDevices

  Klienten Konfigurationsstyring på enheden bruger distributionspunkter til installationer og opdateringer.

- RoamingDevices

  Intune og andre indstillinger på enheden angiver brugen af Microsoft 365 til installationer og opdateringer.

## <a name="new-onboarding-process"></a>Ny onboardingproces

For en ny dedikeret enhed i det lokale miljø, der er udstedt til en ny medarbejder eller for en ny server i et datacenter, henter og installerer Konfigurationsstyring-klienten, når medarbejderen logger på, de nyeste opdateringer til Windows 10, Microsoft 365 Apps for enterprise og Edge fra lokale Konfigurationsstyring-distributionspunkter. Når det er fuldført, er den dedikerede lokale enhed klar til brug og bruger disse distributionspunkter til løbende opdateringer.

For en ny fjernenhed, der er udstedt til en ny medarbejder, kontakter enheden enheden, baseret på dens medlemskab i gruppen RoamingDevices, Intune-skytjenesten og andre tjenester samt downloader og installerer de seneste opdateringer til Windows 10, Microsoft 365 Apps for enterprise og Edge. Når det er fuldført, er fjernenheden klar til brug og bruger den installerede VPN-klient til at få adgang til lokale ressourcer og netværket Microsoft 365 til løbende opdateringer.

## <a name="next-step"></a>Næste trin

[Konfigurer din infrastruktur til hybridarbejde](empower-people-to-work-remotely.md) i din organisation.
