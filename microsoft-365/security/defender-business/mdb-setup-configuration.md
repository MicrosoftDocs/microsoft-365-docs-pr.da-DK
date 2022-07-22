---
title: Konfigurer og konfigurer Microsoft Defender til virksomheder
description: Se, hvordan du konfigurerer din Defender for Business-løsning til cybersikkerhed. Onboarde enheder, gennemse dine politikker, og rediger dine indstillinger efter behov.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365solution-mdb-setup
ms.openlocfilehash: e6489fa45e85c8c9561a29bfc7e47615a5c0ea33
ms.sourcegitcommit: 00948161a72d8cea8c2baba873743fc4a0e19f90
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/22/2022
ms.locfileid: "66969721"
---
# <a name="set-up-and-configure-microsoft-defender-for-business"></a>Konfigurer og konfigurer Microsoft Defender til virksomheder

Defender for Business giver en strømlinet konfigurationsoplevelse, der er udviklet specielt til små og mellemstore virksomheder. Brug denne artikel som en vejledning til den overordnede proces.

> [!TIP]
> Hvis du har brugt [installationsguiden](mdb-use-wizard.md), har du allerede fuldført flere trin i den grundlæggende konfigurationsproces. I dette tilfælde kan du:
> - [Onboarder flere enheder](mdb-onboard-devices.md)
> - [Konfigurer dine sikkerhedspolitikker og -indstillinger](mdb-configure-security-settings.md)
> - [Besøg dashboardet til administration af sårbarheder](mdb-view-tvm-dashboard.md)


## <a name="the-setup-and-configuration-process"></a>Konfigurationsprocessen

I følgende diagram vises den overordnede konfigurationsproces for Defender for Business. Hvis du har brugt installationsguiden, har du sandsynligvis allerede fuldført trin 1-3 og muligvis trin 4. 

:::image type="content" source="media/mdb-setup-process-2.png" alt-text="Konfigurationsprocessen for Defender for Business.":::

| Trin  | Artikel | Beskrivelse  |
|---------|---------|--------|
| 1 | [Gennemse kravene](mdb-requirements.md) | Gennemse kravene, herunder understøttede operativsystemer, til Defender for Business. Se [Defender for Business-krav](mdb-requirements.md). |
| 2 | [Tildel roller og tilladelser](mdb-roles-permissions.md)     | Personer i dit sikkerhedsteam skal have tilladelse til at udføre opgaver, f.eks. gennemse registrerede trusler & afhjælpningshandlinger, få vist & redigeringspolitikker, onboardingenheder og bruge rapporter. Du kan tildele disse tilladelser via bestemte roller. Se [Tildel roller og tilladelser](mdb-roles-permissions.md).        |
| 3 | [Konfigurer mailmeddelelser](mdb-email-notifications.md) | Du kan angive, hvem der skal modtage mailmeddelelser, når beskeder udløses, eller der registreres nye sikkerhedsrisici. Se [Konfigurer mailmeddelelser](mdb-email-notifications.md).| 
| 4 | [Onboard enheder](mdb-onboard-devices.md)     | Defender for Business er konfigureret, så du kan vælge mellem flere muligheder for at onboarde din virksomheds enheder. Se [Om bord på enheder til Defender for Business](mdb-onboard-devices.md).         |
| 5 | [Konfigurer dine sikkerhedsindstillinger og -politikker](mdb-configure-security-settings.md) | Du kan vælge mellem flere indstillinger for at konfigurere dine sikkerhedsindstillinger og politikker, f.eks. den [forenklede konfigurationsproces](mdb-simplified-configuration.md) i Defender for Business eller Microsoft Endpoint Manager Administration. Se [Konfigurer dine sikkerhedsindstillinger og -politikker](mdb-configure-security-settings.md). |

## <a name="next-steps"></a>Næste trin

Fortsæt til [trin 1: Gennemse kravene til Microsoft Defender til virksomheder](mdb-requirements.md).
