---
title: Sørg for, at dine enheder er konfigureret korrekt
description: Konfigurer enheder korrekt for at øge den overordnede fleksibilitet over for trusler og forbedre din mulighed for at registrere og reagere på angreb.
keywords: onboard, Intune-administration, Microsoft Defender til Slutpunkt, Microsoft Defender, Windows Defender, reduktion af angrebsoverfladen, ASR, sikkerhedslinje
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
ms.openlocfilehash: 61b275e5e42a10743eee744ab44bce48a25fa2eb
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2021
ms.locfileid: "63593474"
---
# <a name="ensure-your-devices-are-configured-properly"></a>Sørg for, at dine enheder er konfigureret korrekt

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-onboardconfigure-abovefoldlink)

Med korrekt konfigurerede enheder kan du øge den overordnede fleksibilitet over for trusler og forbedre din mulighed for at registrere og reagere på angreb. Sikkerhedskonfigurationsstyring hjælper med at sikre, at dine enheder:

- Onboard to Microsoft Defender for Endpoint
- Mød eller overser konfigurationen af Defender for Endpoint-sikkerhedskonfigurationen
- Få afhjælpninger af strategiske angrebsoverfladen på plads

Klik **på Konfigurationsstyring** i navigationsmenuen for at åbne siden Enhedskonfigurationsstyring.

![Siden til administration af sikkerhedskonfiguration.](images/secconmgmt_main.png)

*Siden til administration af enhedskonfiguration*

Du kan spore konfigurationsstatus på organisationsniveau og hurtigt reagere på dårlig onboarding-dækning, problemer med overholdelse og dårligt optimerede afhjælpninger af angrebsoverfladen via direkte, dybtgående links til sider til administration af enheder på Microsoft Intune<a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">- og Microsoft 365 Defender-portalen</a>.

Når du gør det, kan du drage fordel af:

- Omfattende synlighed af begivenheder på dine enheder
- Robust trusselsintelligens og effektive teknologier til enhedslæring til at behandle rå hændelser og identificere indikatorer for brud og trusler
- En komplet stak af sikkerhedsfunktioner, der er konfigureret til effektivt at stoppe installationen af skadelige malwares, kapring af systemfiler og -processer, dataudfyldning og andre trusselsaktiviteter
- Optimerede afhjælpninger af angrebsoverfladen, optimering af det strategiske forsvar mod trusselsaktivitet, mens påvirkningen af produktiviteten minimeres

## <a name="enroll-devices-to-intune-management"></a>Tilmeld enheder til administration af Intune

Administration af enhedskonfiguration arbejder tæt sammen med Intune-enhedsstyring for at fastlægge lagerbeholdningen af enhederne i organisationen og sikkerhedskonfigurationen for den oprindelige plan. Du kan spore og administrere konfigurationsproblemer på Intune-administrerede Windows enheder.

Før du kan sikre dig, at dine enheder er konfigureret korrekt, skal du tilmelde dem til administration af Intune. Intune-tilmelding er robust og har flere registreringsmuligheder for Windows enheder. Du kan finde flere oplysninger om registreringsindstillinger for Intune ved at læse [om at konfigurere registrering for Windows enheder](/intune/windows-enroll).

> [!NOTE]
> For at tilmelde Windows enheder til Intune skal administratorer allerede have fået tildelt licenser. [Læs om tildeling af licenser til enhedsregistrering](/intune/licenses-assign).

> [!TIP]
> Hvis du vil optimere enhedshåndtering via Intune, [skal du forbinde Intune til Defender til Slutpunkt](/intune/advanced-threat-protection#enable-windows-defender-atp-in-intune).

## <a name="obtain-required-permissions"></a>Få nødvendige tilladelser

Som standard er det kun brugere, der har fået tildelt rollen som global administrator eller Intune-tjenesteadministrator på Azure AD, der kan administrere og tildele de enhedskonfigurationsprofiler, der er nødvendige for onboardingenheder og implementere grundlinjen med sikkerhed.

Hvis du har fået tildelt andre roller, skal du sikre dig, at du har de nødvendige tilladelser:

- Fulde tilladelser til enhedskonfigurationer
- Fulde tilladelser til oprindelige sikkerhedsscenarier
- Læse tilladelser til politikker for enhedsoverholdelse
- Læsetilladelser for organisationen

![Påkrævede tilladelser på intune.](images/secconmgmt_intune_permissions.png)

*Enhedskonfigurationstilladelser på Intune*

> [!TIP]
> Du kan få mere at vide om at tildele tilladelser på Intune ved at [læse om oprettelse af brugerdefinerede roller](/intune/create-custom-role#to-create-a-custom-role).

## <a name="in-this-section"></a>I dette afsnit

Emne|Beskrivelse
:---|:---
[Få enheder onboardet til Defender til Slutpunkt](configure-machines-onboarding.md)|Spor onboardingstatus for Intune-administrerede enheder, og onboard flere enheder via Intune. 
[Øg overholdelse af sikkerhed i Defender for Endpoint på grundlinjen](configure-machines-security-baseline.md)|Spor overholdelse af oprindelige planer og manglende overholdelse af regler og standarder. Implementer grundlinjen sikkerhed på flere Intune-administrerede enheder.
[Optimer installation og registrering af ASR-regler](configure-machines-asr.md)|Gennemse regelinstallation og finjusteringer ved hjælp af værktøjer til effektanalyse <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">i Microsoft 365 Defender portal</a>.

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-onboardconfigure-belowfoldlink)
