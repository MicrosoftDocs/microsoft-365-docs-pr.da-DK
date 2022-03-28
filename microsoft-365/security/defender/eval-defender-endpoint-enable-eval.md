---
title: Aktivér Evaluering af Microsoft Defender til slutpunkt
description: Aktivér dit Microsoft 365 Defender-prøvelaboratorium eller pilotmiljø, herunder kontrol af licenstilstand og onboardingslutpunkter
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.date: 07/09/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: a12c81635f712dd0fac70101348d30bc1dc4f154
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/23/2022
ms.locfileid: "63754633"
---
# <a name="enable-microsoft-defender-for-endpoint-evaluation-environment"></a>Aktivér Microsoft Defender til slutpunktsevalueringsmiljø


Denne artikel fører dig gennem trinnene til konfiguration af evalueringsmiljøet for Microsoft Defender til slutpunkt ved hjælp af produktionsenheder. 


> [!TIP]
> Microsoft Defender til Slutpunkt leveres også med et evalueringslaboratorium i produktet, hvor du kan tilføje forudkonfigurerede enheder og køre simulering for at evaluere platformens funktioner. Laboratoriet leveres med en forenklet opsætningsoplevelse, der kan hjælpe dig med hurtigt at demonstrere værdien af Microsoft Defender til slutpunkt, herunder vejledning til mange funktioner som avanceret jagt- og trusselsanalyse. Du kan finde flere oplysninger [i Evaluere funktioner](../defender-endpoint/evaluation-lab.md). <br> Den vigtigste forskel mellem vejledningen i denne artikel og evalueringslaboratoriet er evalueringsmiljøet, der bruger produktionsenheder, hvorimod evalueringslaboratoriet bruger ikke-produktionsenheder. 

Brug følgende trin til at aktivere evalueringen af Microsoft Defender til slutpunkt.

:::image type="content" source="../../media/defender/m365-defender-endpoint-eval-enable-steps.png" alt-text="Disse trin til at aktivere Microsoft Defender til slutpunkt i Microsoft Defender-evalueringsmiljøet" lightbox="../../media/defender/m365-defender-endpoint-eval-enable-steps.png":::

- [Trin 1. Kontrollér licenstilstanden](#step-1-check-license-state)
- [Trin 2. Onboard slutpunkter](#step-2-onboard-endpoints-using-any-of-the-supported-management-tools)


## <a name="step-1-check-license-state"></a>Trin 1. Kontrollér licenstilstanden

Du skal først kontrollere licenstilstanden for at bekræfte, at den er blevet korrekt klargjort. Du kan gøre dette via Administration eller **Microsoft Azure-portalen**.


1. For at få vist dine licenser skal du **gå Microsoft Azure portal** og gå til [afsnittet Microsoft Azure portallicens](https://portal.azure.com/#blade/Microsoft_AAD_IAM/LicensesMenuBlade/Products).

   :::image type="content" source="../../media/defender/atp-licensing-azure-portal.png" alt-text="Siden Azure-licensering i Microsoft 365 Defender portalen" lightbox="../../media/defender/atp-licensing-azure-portal.png":::

1. Alternativt kan du i Administration gå til **BillingSubscriptions** > .

    På skærmen får du vist alle de klargjorte licenser og deres aktuelle **Status**.

    :::image type="content" source="../../media/defender/atp-billing-subscriptions.png" alt-text="Siden Faktureringslicenser i Microsoft Azure portal" lightbox="../../media/defender/atp-billing-subscriptions.png":::
    

## <a name="step-2-onboard-endpoints-using-any-of-the-supported-management-tools"></a>Trin 2. Onboard slutpunkter ved hjælp af et af de understøttede administrationsværktøjer

Når du har kontrolleret, at licenstilstanden er blevet klargjort korrekt, kan du starte onboardingenheder til tjenesten. 

Med henblik på evaluering af Microsoft Defender til slutpunkt anbefaler vi, at du vælger et par Windows enheder til at gennemføre evalueringen på.

Du kan vælge at bruge et af de understøttede administrationsværktøjer, men Intune leverer optimal integration. Du kan få mere at [vide under Konfigurer Microsoft Defender til slutpunkt i Microsoft Intune](/mem/intune/protect/advanced-threat-protection-configure#enable-microsoft-defender-for-endpoint-in-intune).

Emnet [Planlæg](../defender-endpoint/deployment-strategy.md) installation beskriver de generelle trin, du skal følge for at installere Defender til Slutpunkt.  

Watch this video for a quick overview of the onboarding process and learn about the available tools and methods.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4bGqr]

### <a name="onboarding-tool-options"></a>Indstillinger for onboardingværktøj

I følgende tabel vises de tilgængelige værktøjer baseret på det slutpunkt, du skal bruge til onboarding.

Slutpunkt | Værktøjsindstillinger
:---|:---
**Windows** | [Lokalt script (op til 10 enheder)](../defender-endpoint/configure-endpoints-script.md), [Gruppepolitik](../defender-endpoint/configure-endpoints-gp.md), [Microsoft Endpoint Manager/ Mobile Device Manager](../defender-endpoint/configure-endpoints-mdm.md), [Microsoft Endpoint Configuration Manager](../defender-endpoint/configure-endpoints-sccm.md), [VDI-scripts](../defender-endpoint/configure-endpoints-vdi.md), [Integration med Microsoft Defender til Cloud](../defender-endpoint/configure-server-endpoints.md#integration-with-azure-defender)
**macOS** | [Lokale scripts](../defender-endpoint/mac-install-manually.md), [Microsoft Endpoint Manager](../defender-endpoint/mac-install-with-intune.md), [JAMF Pro](../defender-endpoint/mac-install-with-jamf.md), [administration af mobilenheder](../defender-endpoint/mac-install-with-other-mdm.md)
**Linux Server** | [Lokalt script](../defender-endpoint/linux-install-manually.md),  [Ane](../defender-endpoint/linux-install-with-puppet.md),  [Ansible](../defender-endpoint/linux-install-with-ansible.md)
**iOS** | [Appbaseret](../defender-endpoint/ios-install.md)
**Android** | [Microsoft Endpoint Manager](../defender-endpoint/android-intune.md)



## <a name="next-step"></a>Næste trin
[Konfigurer pilotprojektet for Microsoft Defender til slutpunkt](eval-defender-endpoint-pilot.md)
 
Gå tilbage til oversigten for [Evaluer Microsoft Defender til slutpunkt](eval-defender-endpoint-overview.md)

Gå tilbage til oversigten for [Evaluer og Microsoft 365 Defender](eval-overview.md)
