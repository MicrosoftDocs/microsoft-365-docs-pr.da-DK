---
title: Sørg for, at dine enheder er konfigureret korrekt
description: Konfigurer enheder korrekt for at øge den overordnede fleksibilitet over for trusler og forbedre din mulighed for at registrere og reagere på angreb.
keywords: onboard, Intune management, Microsoft Defender for Endpoint, Microsoft Defender, Windows Defender, reduktion af angrebsoverfladen, ASR, sikkerheds baseline
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 47c3cb5d680899a28e6467b24ef398a428851a07
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64476153"
---
# <a name="ensure-your-devices-are-configured-properly"></a>Sørg for, at dine enheder er konfigureret korrekt

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-onboardconfigure-abovefoldlink)

Med korrekt konfigurerede enheder kan du øge den overordnede fleksibilitet over for trusler og forbedre din mulighed for at registrere og reagere på angreb. Sikkerhedskonfigurationsstyring hjælper med at sikre, at dine enheder:

- Onboard til Microsoft Defender for Endpoint
- Mød eller overser konfigurationen af Defender for Endpoint-sikkerhedskonfigurationen
- Få afhjælpninger af strategiske angrebsoverfladen på plads

Klik **på Konfigurationsstyring** i navigationsmenuen for at åbne siden Enhedskonfigurationsstyring.

:::image type="content" source="images/secconmgmt_main.png" alt-text="Siden Til administration af sikkerhedskonfiguration" lightbox="images/secconmgmt_main.png":::

*Siden til administration af enhedskonfiguration*

Du kan spore konfigurationsstatus på organisationsniveau og hurtigt reagere på dårlig onboarding-dækning, problemer med overholdelse og dårligt optimerede afhjælpninger af angrebsoverfladen via direkte, dybtgående links til sider til administration af enheder på Microsoft Intune<a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">- og Microsoft 365 Defender-portalen</a>.

Når du gør det, kan du drage fordel af:

- Omfattende synlighed af begivenheder på dine enheder
- Robust trusselsintelligens og effektive teknologier til enhedslæring til at behandle rå hændelser og identificere indikatorer for brud og trusler
- En komplet stak af sikkerhedsfunktioner, der er konfigureret til effektivt at stoppe installationen af skadelige malwares, kapring af systemfiler og -processer, dataudfyldning og andre trusselsaktiviteter
- Optimerede afhjælpninger af angrebsoverfladen, optimering af det strategiske forsvar mod trusselsaktivitet, mens påvirkningen af produktiviteten minimeres

## <a name="enroll-devices-to-intune-management"></a>Tilmeld enheder til Intune administration

Administration af enhedskonfiguration arbejder tæt sammen Intune administration af enheder for at fastlægge lagerbeholdningen af enhederne i organisationen og sikkerhedskonfigurationen for den oprindelige plan. Du vil kunne spore og administrere konfigurationsproblemer på Intune-administrerede Windows enheder.

Før du kan sikre dig, at dine enheder er konfigureret korrekt, skal du tilmelde dem Intune administration. Intune registrering er robust og har flere registreringsmuligheder for Windows enheder. Du kan finde flere Intune om registreringsindstillinger ved at læse [om at konfigurere registrering for Windows enheder](/intune/windows-enroll).

> [!NOTE]
> For at tilmelde Windows enheder til Intune skal administratorer allerede have fået tildelt licenser. [Læs om tildeling af licenser til enhedsregistrering](/intune/licenses-assign).

> [!TIP]
> Hvis du vil optimere enhedshåndtering via Intune, [skal Intune til Defender til Slutpunkt](/intune/advanced-threat-protection#enable-windows-defender-atp-in-intune).

## <a name="obtain-required-permissions"></a>Få nødvendige tilladelser

Som standard er det kun brugere, der har fået tildelt rollen som global administrator eller Intune-tjenesteadministrator på Azure AD, der kan administrere og tildele de enhedskonfigurationsprofiler, der er nødvendige for onboardingenheder og udrulle den oprindelige sikkerhed.

Hvis du har fået tildelt andre roller, skal du sikre dig, at du har de nødvendige tilladelser:

- Fulde tilladelser til enhedskonfigurationer
- Fulde tilladelser til oprindelige sikkerhedsscenarier
- Læse tilladelser til politikker for enhedsoverholdelse
- Læsetilladelser for organisationen

:::image type="content" source="images/secconmgmt_intune_permissions.png" alt-text="De nødvendige tilladelser på intune" lightbox="images/secconmgmt_intune_permissions.png":::

*Enhedskonfigurationstilladelser på Intune*

> [!TIP]
> Du kan få mere at vide om at tildele tilladelser Intune ved at [læse om at oprette brugerdefinerede roller](/intune/create-custom-role#to-create-a-custom-role).

## <a name="in-this-section"></a>I dette afsnit

Emne|Beskrivelse
:---|:---
[Få enheder onboardet til Defender til Slutpunkt](configure-machines-onboarding.md)|Spor onboardingstatus for Intune-administrerede enheder og onboard flere enheder Intune. 
[Øg overholdelse af sikkerhed i Defender for Endpoint på grundlinjen](configure-machines-security-baseline.md)|Spor overholdelse af oprindelige planer og manglende overholdelse af regler og standarder. Installér grundlinjen sikkerhed på flere Intune-administrerede enheder.
[Optimer installation og registrering af ASR-regler](configure-machines-asr.md)|Gennemse regelinstallation og finjusteringer ved hjælp af værktøjer til effektanalyse <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">i Microsoft 365 Defender portal</a>.

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-onboardconfigure-belowfoldlink)
