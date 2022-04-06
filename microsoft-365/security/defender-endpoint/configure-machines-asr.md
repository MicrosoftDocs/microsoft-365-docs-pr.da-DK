---
title: Optimer installation og registrering af ASR-regler
description: Optimer dine AA-regler (Attack Surface Reduction) for at identificere og forhindre typiske malwareudbytninger.
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
ms.topic: article
ms.technology: mde
ms.openlocfilehash: d2bf9a6fa1f874e7d550d0d0f7a42742a07665eb
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64468253"
---
# <a name="optimize-asr-rule-deployment-and-detections"></a>Optimer installation og registrering af ASR-regler

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-onboardconfigure-abovefoldlink)

[ASR-regler (Attack Surface Reduction)](./attack-surface-reduction.md) identificerer og forhindrer typiske malwareudbytninger. De styrer, hvornår og hvordan potentielt skadelig kode kan køre. De kan f.eks. forhindre JavaScript eller VBScript i at starte en downloadet eksekverbar fil, blokere Win32 API-opkald fra Office-makroer og blokere processer, der køres fra USB-drev.


:::image type="content" source="../../media/attack-surface-mgmt.png" alt-text="Administrationskort til angrebsoverfladen" lightbox="../../media/attack-surface-mgmt.png":::
<br>
*Administrationskort til angrebsoverfladen*

*Angrebsoverfladeadministrationskortet* er et indgangspunkt til værktøjer i <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender,</a> som du kan bruge til at:

* Få mere at vide om, hvordan ASR-regler aktuelt installeres i organisationen.
* Gennemse ASR-registreringer, og identificer mulige forkerte registreringer.
* Analysér effekten af udeladelse, og opret listen over filstier, der skal udelades.

Vælg **Gå til rapporter om reduktion af angrebsoverfladens** \>  \> **angrebsoverfladen, og** \> **tilføj udeladelse.** Derfra kan du navigere til andre sektioner i Microsoft 365 Defender portal.

:::image type="content" source="images/secconmgmt_asr_m365exlusions.png" alt-text="Tilføj fanen udeladelse på siden Med reduktionsregler for angrebsoverfladen på Microsoft 365 Defender portal" lightbox="images/secconmgmt_asr_m365exlusions.png":::<br>
Fanen ***Tilføj udeladelse på** siden Regler for reduktion af angrebsoverfladen i Microsoft 365 Defender portal*

> [!NOTE]
> For at få Microsoft 365 Defender-portalen skal du have en Microsoft 365 E3- eller E5-licens og en konto, der har bestemte roller Azure Active Directory. [Læs om nødvendige licenser og tilladelser](/office365/securitycompliance/microsoft-security-and-compliance#required-licenses-and-permissions).

Du kan finde flere oplysninger om installation af <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">ASR-regler i Microsoft 365 Defender-portalen</a> i Overvåge og administrere installation og registrering af [ASR-regler](/office365/securitycompliance/monitor-devices#monitor-and-manage-asr-rule-deployment-and-detections).

**Relaterede emner**

* [Sørg for, at dine enheder er konfigureret korrekt](configure-machines.md)
* [Få enheder onboardet til Microsoft Defender for Endpoint](configure-machines-onboarding.md)
* [Overvåg overholdelse Microsoft Defender for Endpoint den oprindelige sikkerhed](configure-machines-security-baseline.md)
