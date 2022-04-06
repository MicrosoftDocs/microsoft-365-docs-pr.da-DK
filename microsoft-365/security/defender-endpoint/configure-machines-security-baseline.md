---
title: Øg overholdelse af de Microsoft Defender for Endpoint grundlinje for sikkerhed
description: Den Microsoft Defender for Endpoint indstiller sikkerhedskontrolelementerne for at give optimal beskyttelse.
keywords: Intune administration, Microsoft Defender for Endpoint, Microsoft Defender, Microsoft Defender for Endpoint ASR, sikkerheds baseline
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
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 1980567c93364f35923a9a7f2433733e05878e61
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64467967"
---
# <a name="increase-compliance-to-the-microsoft-defender-for-endpoint-security-baseline"></a>Øg overholdelse af de Microsoft Defender for Endpoint grundlinje for sikkerhed

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-onboardconfigure-abovefoldlink)

Sikkerheds oprindelige planer sikrer, at sikkerhedsfunktioner konfigureres i overensstemmelse med vejledning fra både sikkerhedseksperter og ekspert Windows systemadministratorer. Når den er installeret, indstiller sikkerhedskontrolelementerne Defender for Endpoint for at give optimal beskyttelse.

Hvis du vil have mere at vide om grundlinjer for sikkerhed, og hvordan de tildeles Intune ved hjælp af konfigurationsprofiler, skal [du læse disse ofte stillede spørgsmål](/intune/security-baselines#q--a).

Før du kan installere og registrere overholdelse af regler og standarder i oprindelige planer for sikkerhed:

- [Tilmeld dine enheder til Intune administration](configure-machines.md#enroll-devices-to-intune-management)
- [Sørg for, at du har de nødvendige tilladelser](configure-machines.md#obtain-required-permissions)

## <a name="compare-the-microsoft-defender-for-endpoint-and-the-windows-intune-security-baselines"></a>Sammenlign de Microsoft Defender for Endpoint og de Windows Intune oprindelige planer for sikkerhed

The Windows Intune security baseline provides a comprehensive set of recommended settings needed to securely configure devices running Windows, including browser settings, PowerShell settings, and settings for some security features like Microsoft Defender Antivirus. I modsætning hertil indeholder grundlinjen Defender til slutpunkt indstillinger, der optimerer alle sikkerhedskontrolelementerne i stakken Defender til slutpunkt, herunder indstillinger for slutpunktsregistrering og -svar (Slutpunktsregistrering og -svar) samt indstillinger, der også findes i Windows Intune-sikkerhed grundlinje. Du kan finde flere oplysninger om hver oprindelig plan i:

- [Windows indstillinger for grundlinjer for sikkerhed for Intune](/intune/security-baseline-settings-windows)
- [Microsoft Defender for Endpoint indstillinger for grundlinjer for Intune](/intune/security-baseline-settings-defender-atp)

Ideelt set installeres enheder, der er onboardet til Defender til Slutpunkt, begge grundlinjer: Windows Intune-sikkerheds baseline til i første omgang at sikre Windows og derefter Defender for Endpoint-sikkerheds baseline lagdelt oven på for at konfigurere sikkerhedskontrolelementerne for Defender til Slutpunkt optimalt. For at drage fordel af de nyeste data om risici og trusler og minimere konflikter i forbindelse med udvikling af grundlinjer skal du altid anvende de nyeste versioner af de oprindelige planer på tværs af alle produkter, så snart de frigives.

> [!NOTE]
> Sikkerheds baseline for Defender til Slutpunkt er blevet optimeret til fysiske enheder og anbefales ikke til brug på virtuelle maskine (VMs) eller VDI-slutpunkter. Visse indstillinger for grundlinjer kan påvirke eksterne interaktive sessioner på virtualiserede miljøer.

## <a name="monitor-compliance-to-the-defender-for-endpoint-security-baseline"></a>Overvåg overholdelse af sikkerhed for Defender for Endpoint-sikkerheds baseline

Det **oprindelige kort Sikkerhed** på [](configure-machines.md) enhedskonfigurationsstyring giver en oversigt over overholdelse på tværs Windows 10 og Windows 11 enheder, der har fået tildelt Defender som sikkerhedslinje for Slutpunkt.

:::image type="content" source="images/secconmgmt_baseline_card.png" alt-text="Grundlinjekortet Sikkerhed" lightbox="images/secconmgmt_baseline_card.png":::

*Kort, der viser overholdelse af sikkerheds grundlinjen Defender for Endpoint*

Hver enhed får en af følgende statustyper:

- **Matcher grundlinje**: Enhedsindstillinger svarer til alle indstillingerne i grundlinjen.
- **Svarer ikke til grundlinje**: Mindst én enhedsindstilling svarer ikke til den oprindelige plan.
- **Forkert konfigureret**: Mindst én oprindelig planindstilling er ikke konfigureret korrekt på enheden og er i en konflikt, fejl eller afventende tilstand.
- **Ikke relevant**: Der kan ikke anvendes mindst én indstilling for grundlinje på enheden.

Hvis du vil gennemse bestemte enheder, skal **du vælge Konfigurer grundlinje** for sikkerhed på kortet. Dette fører dig til Intune af enheder. Derfra skal du **vælge Enhedsstatus** for navnene og statusserne på enhederne.

> [!NOTE]
> Du kan opleve uoverensstemmelser i samlede data, der vises på siden til administration af enhedskonfiguration, og dem, der vises på oversigtsskærmbilleder Intune.

## <a name="review-and-assign-the-microsoft-defender-for-endpoint-security-baseline"></a>Gennemse og tildele den Microsoft Defender for Endpoint oprindelige plan for sikkerhed

Administration af enhedskonfiguration overvåger kun overholdelse af oprindelige planer for Windows 10 og Windows 11 enheder, der specifikt har fået tildelt Microsoft Defender for Endpoint grundlinje for sikkerhed. Du kan nemt gennemse den oprindelige plan og tildele den til enheder Intune administration af enheder.

1. Vælg **Konfigurer grundlinje for** sikkerhed **på kortet Grundlinje for** sikkerhed for at Intune af enheder. Der vises en lignende oversigt over overholdelse af oprindelige planer.

   > [!TIP]
   > Alternativt kan du gå til sikkerhedslinjen Defender for Endpoint i Microsoft Azure-portalen fra Alle tjenester **> Intune > Enhedssikkerhed > grundlinjer med sikkerhed > Microsoft Defender ATP-grundlinjen**.

2. Opret en ny profil.

   :::image type="content" source="images/secconmgmt_baseline_intuneprofile1.png" alt-text="Fanen Opret profil i Microsoft Defender for Endpoint oversigt over grundlinjer for sikkerhed på Intune" lightbox="images/secconmgmt_baseline_intuneprofile1.png":::<br>
   *Microsoft Defender for Endpoint oversigt over grundlinjer for sikkerhed på Intune*

3. Under oprettelsen af profilen kan du gennemse og justere specifikke indstillinger i den oprindelige plan.

   :::image type="content" source="images/secconmgmt_baseline_intuneprofile2.png" alt-text="Indstillingerne for grundlinje for sikkerhed under oprettelse af profil på Intune" lightbox="images/secconmgmt_baseline_intuneprofile2.png":::<br>
   *Indstillinger for grundlinje over sikkerhed under oprettelse af profil på Intune*

4. Tildel profilen til den relevante enhedsgruppe.

   :::image type="content" source="images/secconmgmt_baseline_intuneprofile3.png" alt-text="De oprindelige sikkerhedsprofiler på Intune" lightbox="images/secconmgmt_baseline_intuneprofile3.png":::<br>
   *Tildeling af den oprindelige sikkerhedsprofil på Intune*

5. Opret profilen for at gemme den og installere den i den tildelte enhedsgruppe.

   :::image type="content" source="images/secconmgmt_baseline_intuneprofile4.png" alt-text="Tildele den oprindelige sikkerhed til den Intune" lightbox="images/secconmgmt_baseline_intuneprofile4.png":::<br>
   *Oprettelse af profilen for den oprindelige sikkerhed på Intune*

> [!TIP]
> Grundlinjer med sikkerhed på Intune en nem måde at sikre og beskytte dine enheder på. [Få mere at vide om grundlinjer for sikkerhed Intune](/intune/security-baselines).

> Vil du gerne Microsoft Defender for Endpoint? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-onboardconfigure-belowfoldlink)

## <a name="related-topics"></a>Relaterede emner

- [Sørg for, at dine enheder er konfigureret korrekt](configure-machines.md)
- [Få enheder onboardet til Microsoft Defender for Endpoint](configure-machines-onboarding.md)
- [Optimer installation og registrering af ASR-regler](configure-machines-asr.md)
