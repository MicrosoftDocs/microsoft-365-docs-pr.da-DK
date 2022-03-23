---
title: Brug automatiserede undersøgelser til at undersøge og afhjælpe trusler
description: Forstå det automatiserede undersøgelsesflow i Microsoft Defender til slutpunkt.
keywords: automatiseret, undersøgelse, registrering, Microsoft Defender til Slutpunkt
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: dansimp
ms.author: dansimp
ms.date: 11/24/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: how-to
ms.reviewer: ramarom, evaldm, isco, mabraitm, chriggs
ms.custom: AIR
ms.openlocfilehash: 31b2a7b41c26bdba22e6f364e517471e31e9115c
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63591895"
---
# <a name="overview-of-automated-investigations"></a>Oversigt over automatiserede undersøgelser

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Vil du se, hvordan det fungerer? Se følgende video:

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4bOeh]

Teknologien i automatiseret undersøgelse bruger forskellige inspektionsalgoritmer og er baseret på processer, der bruges af sikkerhedsanalytikere. AIR-funktioner er designet til at undersøge beskeder og straks tage skridt til at løse brud. AIR-funktioner reducerer mængden af beskeder markant, hvilket giver sikkerhedshandlinger mulighed for at fokusere på mere avancerede trusler og andre tiltag med høj værdi. Alle afhjælpningshandlinger, uanset om de er ventende eller fuldførte, registreres [i Handlingscenter](auto-investigation-action-center.md). I Handlingscenter godkendes (eller afvises) afventende handlinger, og afsluttede handlinger kan fortrydes, hvis det er nødvendigt.

Denne artikel indeholder en oversigt over AIR og indeholder links til næste trin og yderligere ressourcer.

> [!TIP]
> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-automated-investigations-abovefoldlink)

## <a name="how-the-automated-investigation-starts"></a>Sådan starter den automatiserede undersøgelse

En automatisk undersøgelse kan starte, når der udløses en besked, eller når en sikkerhedsoperatør starter undersøgelsen.

<br>

****

|Situation|Hvad sker der?|
|---|---|
|Der udløses en besked|Generelt starter en automatisk undersøgelse, [når der](review-alerts.md) udløses en besked, og der [oprettes en](view-incidents-queue.md) hændelse. Antag f.eks., at der findes en skadelig fil på en enhed. Når den pågældende fil registreres, udløses der en besked, og der oprettes en hændelse. Der starter en automatiseret undersøgelsesproces på enheden. Da andre beskeder genereres på grund af den samme fil på andre enheder, føjes de til den tilknyttede hændelse og til den automatiserede undersøgelse.|
|En undersøgelse startes manuelt|En automatisk undersøgelse kan startes manuelt af dit sikkerhedsteam. Antag f.eks., at en sikkerhedsoperatør gennemser en liste over enheder og bemærker, at en enhed har et højt risikoniveau. Sikkerhedsoperatøren kan vælge enheden på listen for at åbne pop op-mailen og derefter vælge **Initier automatiseret undersøgelse**.|
|

## <a name="how-an-automated-investigation-expands-its-scope"></a>Sådan udvider en automatiseret undersøgelse omfanget

Mens en undersøgelse kører, føjes alle andre beskeder, der genereres fra enheden, til en igangværende automatisk undersøgelse, indtil undersøgelsen er afsluttet. Hvis den samme trussel kan ses på andre enheder, føjes disse enheder til undersøgelsen.

Hvis en inkrimineret enhed ses i en anden enhed, udvider den automatiske undersøgelsesproces omfanget til at omfatte den pågældende enhed, og en generel sikkerhedsspilbog starter på den pågældende enhed. Hvis der findes 10 eller flere enheder under denne udvidelsesproces fra den samme enhed, kræver den pågældende udvidelseshandling godkendelse, og den vises under **fanen Afventende** handlinger.

## <a name="how-threats-are-remediated"></a>Sådan afhjælpes trusler

Når der udløses beskeder, og en automatisk undersøgelse køres, genereres der en vurdering af hvert enkelt beviser, der undersøges. Bedømmelser kan være:

- *Ondsindet*;
- *Mistænkelig;* eller
- *Der blev ikke fundet nogen trusler*.

Efterhånden som der opnås konklusioner, kan automatiserede undersøgelser resultere i en eller flere afhjælpningshandlinger. Eksempler på afhjælpningshandlinger er at sende en fil til karantæne, stoppe en tjeneste, fjerne en planlagt opgave og meget mere. Du kan få mere at vide [under Afhjælpningshandlinger](manage-auto-investigation.md#remediation-actions).

Afhængigt af [niveauet af automatisering](automation-levels.md) , der er angivet for organisationen, samt andre sikkerhedsindstillinger, kan afhjælpningshandlinger udføres automatisk eller kun efter godkendelse fra dit sikkerhedsteam. Yderligere sikkerhedsindstillinger, der kan påvirke automatisk afhjælpning, [omfatter beskyttelse mod potentielt uønskede programmer](/windows/security/threat-protection/microsoft-defender-antivirus/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus) .

Alle afhjælpningshandlinger, uanset om de er ventende eller fuldførte, registreres [i Handlingscenter](auto-investigation-action-center.md). Hvis det er nødvendigt, kan dit sikkerhedsteam fortryde en afhjælpningshandling. Du kan få mere at vide [under Gennemse og godkend afhjælpningshandlinger efter en automatisk undersøgelse](/microsoft-365/security/defender-endpoint/manage-auto-investigation).

> [!TIP]
> Se den nye, samlede undersøgelsesside i Microsoft 365 Defender portal. Du kan få mere at vide under [(NY!) Siden Samlet undersøgelse](/microsoft-365/security/defender/m365d-autoir-results#new-unified-investigation-page).

## <a name="requirements-for-air"></a>Krav til AIR

Din organisation skal have Defender til slutpunkt (se [Minimumskrav til Microsoft Defender til slutpunkt](minimum-requirements.md)).

> [!NOTE]
> Automatiseret undersøgelse og svar kræver Microsoft Defender Antivirus for at køre i passiv tilstand eller aktiv tilstand. Hvis Microsoft Defender Antivirus deaktiveres eller afinstalleres, fungerer Automatiseret undersøgelse og svar ikke korrekt.

Aktuelt understøtter AIR kun følgende os-versioner:

- Windows Server 2012 R2 (preview)
- Windows Server 2016 (Preview)
- Windows Server 2019
- Windows Server 2022
- Windows 10, version 1709 (OS Build 16299.1085 med [KB4493441](https://support.microsoft.com/help/4493441/windows-10-update-kb4493441)) eller nyere
- Windows 10, version 1803 (OS-build 17134.704 med [KB4493464](https://support.microsoft.com/help/4493464/windows-10-update-kb4493464)) eller nyere
- Windows 10, version [1803](/windows/release-information/status-windows-10-1809-and-windows-server-2019) eller nyere
- Windows 11

## <a name="next-steps"></a>Næste trin

- [Få mere at vide om automatiseringsniveauer](automation-levels.md)
- [Se den interaktive vejledning: Undersøg og afhjulpet trusler med Microsoft Defender til Slutpunkt](https://aka.ms/MDATP-IR-Interactive-Guide)
- [Konfigurer automatiseret undersøgelse og afhjælpningsfunktioner i Microsoft Defender til Slutpunkt](configure-automated-investigations-remediation.md)

## <a name="see-also"></a>Se også

- [PUA-beskyttelse](/windows/security/threat-protection/microsoft-defender-antivirus/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus)
- [Automatiseret undersøgelse og svar i Microsoft Defender til Office 365](/microsoft-365/security/office-365-security/office-365-air)
- [Automatiseret undersøgelse og svar i Microsoft 365 Defender](/microsoft-365/security/defender/m365d-autoir)
