---
title: Brug automatiserede undersøgelser til at undersøge og afhjælpe trusler
description: Forstå det automatiserede undersøgelsesflow i Microsoft Defender for Endpoint.
keywords: automatiseret, undersøgelse, registrering Microsoft Defender for Endpoint
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
ms.openlocfilehash: eadf9fe7f6112d1219f085662686b2a930b3ff28
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/12/2022
ms.locfileid: "64789794"
---
# <a name="overview-of-automated-investigations"></a>Oversigt over automatiserede undersøgelser

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Microsoft Defender Antivirus

**Platforme**
- Windows

Vil du se, hvordan det fungerer? Se følgende video:

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4bOeh]

Teknologien i den automatiserede undersøgelse bruger forskellige inspektionsalgoritmer og er baseret på processer, der bruges af sikkerhedsanalytikere. AIR-funktioner er designet til at undersøge beskeder og straks træffe foranstaltninger til at løse brud. AIR-kapaciteter reducerer alarmmængden væsentligt, hvilket gør det muligt for sikkerhedsoperationer at fokusere på mere avancerede trusler og andre initiativer af høj værdi. Alle afhjælpningshandlinger, uanset om de afventer eller er fuldført, spores i [Løsningscenter](auto-investigation-action-center.md). I Løsningscenter godkendes ventende handlinger (eller afvises), og fuldførte handlinger kan fortrydes, hvis det er nødvendigt.

Denne artikel indeholder en oversigt over AIR og indeholder links til næste trin og yderligere ressourcer.

> [!TIP]
> Vil du opleve Microsoft Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-automated-investigations-abovefoldlink)

## <a name="how-the-automated-investigation-starts"></a>Sådan starter den automatiserede undersøgelse

En automatiseret undersøgelse kan starte, når en besked udløses, eller når en sikkerhedsoperator starter undersøgelsen.

<br>

****

|Situation|Hvad sker der?|
|---|---|
|En besked udløses|Generelt starter en automatisk undersøgelse, når en [besked](review-alerts.md) udløses, og der oprettes en [hændelse](view-incidents-queue.md) . Antag f.eks., at der findes en skadelig fil på en enhed. Når filen registreres, udløses en besked, og der oprettes en hændelse. En automatisk undersøgelsesproces starter på enheden. Da andre beskeder genereres på grund af den samme fil på andre enheder, føjes de til den tilknyttede hændelse og til den automatiserede undersøgelse.|
|En undersøgelse startes manuelt|En automatiseret undersøgelse kan startes manuelt af sikkerhedsteamet. Lad os f.eks. antage, at en sikkerhedsoperatør gennemgår en liste over enheder og bemærker, at en enhed har et højt risikoniveau. Sikkerhedsoperatoren kan vælge enheden på listen for at åbne dens pop op-vindue og derefter vælge **Start automatiseret undersøgelse**.|
|

## <a name="how-an-automated-investigation-expands-its-scope"></a>Sådan udvider en automatiseret undersøgelse omfanget

Mens der kører en undersøgelse, føjes alle andre beskeder, der genereres fra enheden, til en igangværende automatisk undersøgelse, indtil undersøgelsen er fuldført. Hvis den samme trussel ses på andre enheder, føjes disse enheder desuden til undersøgelsen.

Hvis der vises et inkrimineret objekt på en anden enhed, udvider den automatiserede undersøgelsesproces dens omfang til at omfatte den pågældende enhed, og en generel sikkerhedslegebog starter på den pågældende enhed. Hvis der findes 10 eller flere enheder under denne udvidelsesproces fra den samme enhed, kræver denne udvidelseshandling en godkendelse og er synlig under fanen **Ventende handlinger** .

## <a name="how-threats-are-remediated"></a>Sådan afhjælpes trusler

Når beskeder udløses, og der køres en automatisk undersøgelse, genereres der en dom for hvert bevis, der undersøges. Dommene kan være:

- *Ondsindet*;
- *Mistænkelig*; Eller
- *Der blev ikke fundet nogen trusler*.

Efterhånden som dommene nås, kan automatiserede undersøgelser resultere i en eller flere afhjælpningshandlinger. Eksempler på afhjælpningshandlinger omfatter afsendelse af en fil for at sætte en fil i karantæne, stoppe en tjeneste, fjerne en planlagt opgave og meget mere. Du kan få mere at vide under [Afhjælpningshandlinger](manage-auto-investigation.md#remediation-actions).

Afhængigt af det [automatiseringsniveau](automation-levels.md) , der er angivet for din organisation, samt andre sikkerhedsindstillinger, kan afhjælpningshandlinger forekomme automatisk eller kun efter godkendelse af dit team for sikkerhedshandlinger. Yderligere sikkerhedsindstillinger, der kan påvirke automatisk afhjælpning, omfatter [beskyttelse mod potentielt uønskede programmer](/windows/security/threat-protection/microsoft-defender-antivirus/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus) (PUA).

Alle afhjælpningshandlinger, uanset om de afventer eller er fuldført, spores i [Løsningscenter](auto-investigation-action-center.md). Hvis det er nødvendigt, kan dit team af sikkerhedshandlinger fortryde en afhjælpningshandling. Du kan få mere at vide under [Gennemse og godkend afhjælpningshandlinger efter en automatisk undersøgelse](/microsoft-365/security/defender-endpoint/manage-auto-investigation).

> [!TIP]
> Se den nye, samlede undersøgelsesside på portalen Microsoft 365 Defender. Du kan få mere at vide under [(NY!) Unified Investigation-side](/microsoft-365/security/defender/m365d-autoir-results#new-unified-investigation-page).

## <a name="requirements-for-air"></a>Krav til LUFT

Din organisation skal have Defender for Endpoint (se [Minimumkrav til Microsoft Defender for Endpoint](minimum-requirements.md)).

> [!NOTE]
> Automatiseret undersøgelse og svar kræver Microsoft Defender Antivirus for at køre i passiv tilstand eller aktiv tilstand. Hvis Microsoft Defender Antivirus er deaktiveret eller fjernet, fungerer automatiseret undersøgelse og svar ikke korrekt.

AIR understøtter i øjeblikket kun følgende operativsystemversioner:

- Windows Server 2012 R2 (prøveversion)
- Windows Server 2016 (prøveversion)
- Windows Server 2019
- Windows Server 2022
- Windows 10, version 1709 (OS Build 16299.1085 med [KB4493441](https://support.microsoft.com/help/4493441/windows-10-update-kb4493441)) eller nyere
- Windows 10, version 1803 (OS Build 17134.704 med [KB4493464](https://support.microsoft.com/help/4493464/windows-10-update-kb4493464)) eller nyere
- Windows 10, version [1803](/windows/release-information/status-windows-10-1809-and-windows-server-2019) eller nyere
- Windows 11

## <a name="next-steps"></a>Næste trin

- [Få mere at vide om automatiseringsniveauer](automation-levels.md)
- [Se den interaktive vejledning: Undersøg og afhjælp trusler med Microsoft Defender for Endpoint](https://aka.ms/MDATP-IR-Interactive-Guide)
- [Konfigurer automatiserede undersøgelses- og afhjælpningsfunktioner i Microsoft Defender for Endpoint](configure-automated-investigations-remediation.md)

## <a name="see-also"></a>Se også

- [PUA-beskyttelse](/windows/security/threat-protection/microsoft-defender-antivirus/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus)
- [Automatiseret undersøgelse og svar i Microsoft Defender for Office 365](/microsoft-365/security/office-365-security/office-365-air)
- [Automatiseret undersøgelse og svar i Microsoft 365 Defender](/microsoft-365/security/defender/m365d-autoir)
