---
title: Brug guiden til at konfigurere Microsoft Defender for Business
description: Defender for Business omfatter en guide-lignende konfigurations- og konfigurationsproces. Brug guiden til at spare tid og besvær.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: article
ms.date: 03/15/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.custom: intro-get-started
ms.openlocfilehash: 243630a43d75a4530024e246fbea57f26a51d06b
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/17/2022
ms.locfileid: "63597006"
---
# <a name="use-the-wizard-to-set-up-microsoft-defender-for-business"></a>Brug guiden til at konfigurere Microsoft Defender for Business

> [!IMPORTANT]
> Microsoft Defender for Business udrulles til [Microsoft 365 Business Premium](../../business-premium/index.md) kunder fra d. 1. marts 2022. Defender for Business som et enkeltstående abonnement er i preview, og den udrulles gradvist til kunder og [it-partnere](https://aka.ms/mdb-preview) , der tilmelder sig her for at anmode om det. [Forhåndsvisning indeholder et indledende sæt scenarier](mdb-tutorials.md#try-these-preview-scenarios), og vi tilføjer funktioner regelmæssigt.
> 
> Nogle oplysninger i denne artikel relaterer til foreløbige produkter/tjenester, der kan være væsentligt ændret, før de frigives kommercielt. Microsoft giver ingen garantier, udtrykkelige eller underforståede, for de oplysninger, du har angivet her. 

Microsoft Defender for Business er udviklet til at spare tid og besvær for små og mellemstore virksomheder med en guide-lignende oplevelse til indledende konfiguration og konfiguration. I denne artikel beskrives trinnene i guiden og dine muligheder for at konfigurere Defender for Business manuelt.

:::image type="content" source="media/mdb-wizard-start.png" alt-text="Skærmbillede af startskærmen i guiden til konfiguration af Defender for Business.":::

>
> **Har du et minut?**
> Tag vores korte <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">undersøgelse om Microsoft Defender for Business</a>. Vi vil meget gerne høre fra dig!
>

## <a name="overview-of-the-wizard"></a>Oversigt over guiden

Guiden er udviklet til at hjælpe dig med hurtigt og effektivt at konfigurere Defender for Business. Guiden fører dig gennem følgende trin:

1. **Tildel brugertilladelser**. I dette trin giver du dit sikkerhedsteam adgang til Microsoft 365 Defender portal ([https://security.microsoft.com](https://security.microsoft.com)). Portaladgang tildeles gennem roller, der indebærer visse tilladelser. [Få mere at vide om roller og tilladelser](mdb-roles-permissions.md).

   - En global administrator kan få vist og redigere alle indstillinger på tværs af Microsoft 365 lejer. 
   - En sikkerhedsadministrator kan få vist og redigere sikkerhedsindstillinger. 
   - En sikkerhedslæser kan kun vise oplysninger i rapporter. 

2. **Onboard og konfigurer Windows-enheder**. I dette trin kan du hurtigt onboarde din virksomheds Windows til Defender for Business. Onboardingenheder hjælper med det samme med at beskytte disse enheder fra dag ét. Se [Onboard-enheder til Microsoft Defender for Business for at](mdb-onboard-devices.md) få flere oplysninger.

   - Hvis du allerede bruger Microsoft Intune (en del af Microsoft Endpoint Manager), og din virksomhed har enheder, der er tilmeldt Endpoint Manager, bliver du spurgt, om du vil bruge automatisk [onboarding](mdb-onboard-devices.md#automatic-onboarding-for-windows-devices-enrolled-in-microsoft-endpoint-manager) til nogle eller alle dine tilmeldte Windows-enheder. Automatisk onboarding konfigurerer en forbindelse mellem Endpoint Manager og Defender for Business og derefter onboardingenheder Windows Defender for Business problemfrit.

   - Hvis du ikke allerede bruger Endpoint Manager, eller hvis du har ikke-Windows-enheder, der er tilmeldt Endpoint Manager, kan du tilføje enheder til [Defender for Business manuelt](mdb-onboard-devices.md#local-script-in-defender-for-business). 
   
3. **Konfigurer dine sikkerhedspolitikker**. Defender for Business omfatter standardsikkerhedspolitikker til næste generations beskyttelse og firewallbeskyttelse, der kan anvendes på din virksomheds enheder. Disse standardpolitikker anvender anbefalede indstillinger og er udviklet til at yde stærk beskyttelse til dine enheder. 

   Du kan også oprette dine egne sikkerhedspolitikker, hvis du ønsker det. Og hvis du allerede bruger en Endpoint Manager, kan du fortsætte med at bruge den til at administrere dine sikkerhedspolitikker. 

   Du kan få mere at vide [under Få vist og redigere dine sikkerhedspolitikker og -indstillinger](mdb-configure-security-settings.md).

## <a name="what-happens-if-i-dont-use-the-wizard"></a>Hvad sker der, hvis jeg ikke bruger guiden?

Hvis du vælger ikke at bruge guiden, eller hvis guiden er lukket, før konfigurationen er fuldført, kan du stadig selv fuldføre konfigurationen og konfigurationen. 

Se [Konfigurere Microsoft Defender for Business, så du](mdb-setup-configuration.md) kan gennemgå disse trin:

1. [Tildel roller og tilladelser,](mdb-roles-permissions.md) så dit sikkerhedsteam kan få adgang til og bruge Microsoft 365 Defender -portalen ([https://security.microsoft.com](https://security.microsoft.com)).

2. [Konfigurer mailbeskeder til dit sikkerhedsteam](mdb-email-notifications.md) , så de er informeret om nye advarsler eller sårbarheder.

3. [Onboard-enheder](mdb-onboard-devices.md) , så de er beskyttet af Defender for Business.

4. [Administrer dine sikkerhedspolitikker](mdb-configure-security-settings.md), som omfatter næste generations beskyttelse, firewallbeskyttelse og filtrering af webindhold.

## <a name="next-steps"></a>Næste trin

- [Konfigurer mailbeskeder til dit sikkerhedsteam](mdb-email-notifications.md)

- [Kom i gang med at bruge Microsoft 365 Defender portalen](mdb-get-started.md)

- [Brug dashboardet til & til administration af trusselssikkerhedsrisiko](mdb-view-tvm-dashboard.md)