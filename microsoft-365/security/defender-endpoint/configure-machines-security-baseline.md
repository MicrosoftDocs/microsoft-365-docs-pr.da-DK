---
title: Øg overholdelse af angivne standarder til sikkerheds grundlinjen Microsoft Defender for Endpoint
description: Sikkerhedslinjen Microsoft Defender for Endpoint angiver sikkerhedskontrolelementer for at give optimal beskyttelse.
keywords: Intune-administration, Microsoft Defender til slutpunkt, Microsoft Defender, Microsoft Defender til endpoint ASR, sikkerheds baseline
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
ms.openlocfilehash: 95790626461d7db02f3837321e0d9075e0597515
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2021
ms.locfileid: "63592840"
---
# <a name="increase-compliance-to-the-microsoft-defender-for-endpoint-security-baseline"></a>Øg overholdelse af angivne standarder til sikkerheds grundlinjen Microsoft Defender for Endpoint

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-onboardconfigure-abovefoldlink)

Sikkerheds oprindelige planer sikrer, at sikkerhedsfunktioner konfigureres i overensstemmelse med vejledning fra både sikkerhedseksperter og ekspert Windows systemadministratorer. Når den er installeret, indstiller sikkerhedskontrolelementerne Defender for Endpoint for at give optimal beskyttelse.

For at forstå grundlinjer for sikkerhed, og hvordan de tildeles på Intune ved hjælp af konfigurationsprofiler, skal du [læse disse ofte stillede spørgsmål](/intune/security-baselines#q--a).

Før du kan installere og registrere overholdelse af regler og standarder i oprindelige planer for sikkerhed:

- [Tilmeld dine enheder til intune-administration](configure-machines.md#enroll-devices-to-intune-management)
- [Sørg for, at du har de nødvendige tilladelser](configure-machines.md#obtain-required-permissions)

## <a name="compare-the-microsoft-defender-for-endpoint-and-the-windows-intune-security-baselines"></a>Sammenlign Microsoft Defender for Endpoint og Windows Intune-sikkerheds baselines

The Windows Intune security baseline provides a comprehensive set of recommended settings needed to securely configure devices running Windows, including browser settings, PowerShell settings, and settings for some security features like Microsoft Defender Antivirus. I modsætning hertil indeholder grundlinjen Defender til slutpunkt indstillinger, der optimerer alle sikkerhedskontrolelementerne i stakken Defender til slutpunkt, herunder indstillinger for slutpunktsregistrering og -svar (Slutpunktsregistrering og -svar) samt indstillinger, der også findes i Windows Intune-sikkerheds baseline. Du kan finde flere oplysninger om hver oprindelig plan i:

- [Windows indstillinger for grundlinjer for sikkerhed for Intune](/intune/security-baseline-settings-windows)
- [Grundlinjeindstillinger for Microsoft Defender for Endpoint for Intune](/intune/security-baseline-settings-defender-atp)

Ideelt set installeres enheder, der er onboardet til Defender til Slutpunkt, begge grundlinjer: sikkerheds baseline for Windows Intune til indledningsvist at sikre Windows og derefter Defender for Endpoint-sikkerhedslinjen lagdelt oven på for optimalt at konfigurere sikkerhedskontrolelementerne for Defender til Endpoint. For at drage fordel af de nyeste data om risici og trusler og minimere konflikter i forbindelse med udvikling af grundlinjer skal du altid anvende de nyeste versioner af de oprindelige planer på tværs af alle produkter, så snart de frigives.

> [!NOTE]
> Sikkerheds baseline for Defender til Slutpunkt er blevet optimeret til fysiske enheder og anbefales ikke til brug på virtuelle maskine (VMs) eller VDI-slutpunkter. Visse indstillinger for grundlinjer kan påvirke eksterne interaktive sessioner på virtualiserede miljøer.

## <a name="monitor-compliance-to-the-defender-for-endpoint-security-baseline"></a>Overvåg overholdelse af sikkerhed for Defender for Endpoint-sikkerheds baseline

Det **oprindelige sikkerhedskort** på [](configure-machines.md) enhedskonfigurationsstyring giver en oversigt over overholdelse på tværs af Windows 10 og Windows 11 enheder, der har fået tildelt Defender for Endpoint-sikkerheds baseline.

![Grundlinjekort for sikkerhed.](images/secconmgmt_baseline_card.png)

*Kort, der viser overholdelse af sikkerheds grundlinjen Defender for Endpoint*

Hver enhed får en af følgende statustyper:

- **Matcher grundlinje**: Enhedsindstillinger svarer til alle indstillingerne i grundlinjen.
- **Svarer ikke til grundlinje**: Mindst én enhedsindstilling svarer ikke til den oprindelige plan.
- **Forkert konfigureret**: Mindst én oprindelig planindstilling er ikke konfigureret korrekt på enheden og er i en konflikt, fejl eller afventende tilstand.
- **Ikke relevant**: Der kan ikke anvendes mindst én indstilling for grundlinje på enheden.

Hvis du vil gennemse bestemte enheder, skal **du vælge Konfigurer grundlinje** for sikkerhed på kortet. Dette fører dig til administration af enheder i Intune. Derfra skal du **vælge Enhedsstatus** for navnene og statusserne på enhederne.

> [!NOTE]
> Du kan opleve uoverensstemmelser i samlede data, der vises på siden til administration af enhedskonfiguration, og dem, der vises på oversigtsskærmbilleder i Intune.

## <a name="review-and-assign-the-microsoft-defender-for-endpoint-security-baseline"></a>Gennemse og tildel sikkerheds grundlinjen Microsoft Defender for Endpoint

Administration af enhedskonfiguration overvåger kun overholdelse af oprindelige planer for Windows 10 og Windows 11 enheder, der specifikt har fået tildelt sikkerhedslinjen Microsoft Defender for Endpoint. Du kan nemt gennemse den oprindelige plan og tildele den til enheder på administration af enheder i Intune.

1. Vælg **Konfigurer grundlinje for sikkerhed** på **kortet Grundlinje for** sikkerhed for at gå til Administration af intune-enheder. Der vises en lignende oversigt over overholdelse af oprindelige planer.

   > [!TIP]
   > Alternativt kan du gå til sikkerhedslinjen Defender for Endpoint i Microsoft Azure-portalen fra Alle tjenester **> Intune > Enhedssikkerhed > sikkerheds oprindelige planer > Microsoft Defender ATP**.

2. Opret en ny profil.

   ![Oversigt over sikkerhedsoversigt for Microsoft Defender for Endpoint på Intune.](images/secconmgmt_baseline_intuneprofile1.png)<br>
   *Oversigt over sikkerhedsoversigt for Microsoft Defender til Endpoint på Intune*

3. Under oprettelsen af profilen kan du gennemse og justere specifikke indstillinger i den oprindelige plan.

   ![Indstillinger for grundlinje for sikkerhed under oprettelse af profil på Intune.](images/secconmgmt_baseline_intuneprofile2.png)<br>
   *Indstillinger for grundlinje for sikkerhed under oprettelse af profil på Intune*

4. Tildel profilen til den relevante enhedsgruppe.

   ![Profiler for grundlinjer for sikkerhed på Intune.](images/secconmgmt_baseline_intuneprofile3.png)<br>
   *Tildele profilen for grundlinje for sikkerhed på Intune*

5. Opret profilen for at gemme den og installere den i den tildelte enhedsgruppe.

   ![Tildeling af sikkerheds baseline på Intune.](images/secconmgmt_baseline_intuneprofile4.png)<br>
   *Oprettelse af profilen for grundlinje for sikkerhed på Intune*

> [!TIP]
> Grundlinjer med sikkerhed på Intune er en nem måde at sikre og beskytte dine enheder på. [Få mere at vide om grundlinjer for sikkerhed på Intune](/intune/security-baselines).

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-onboardconfigure-belowfoldlink)

## <a name="related-topics"></a>Relaterede emner

- [Sørg for, at dine enheder er konfigureret korrekt](configure-machines.md)
- [Få enheder onboardet til Microsoft Defender til Slutpunkt](configure-machines-onboarding.md)
- [Optimer installation og registrering af ASR-regler](configure-machines-asr.md)
