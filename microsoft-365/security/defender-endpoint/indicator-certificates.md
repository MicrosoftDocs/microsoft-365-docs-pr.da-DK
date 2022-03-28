---
title: Opret indikatorer baseret på certifikater
ms.reviewer: ''
description: Opret indikatorer, der er baseret på certifikater, som definerer registrering, forhindring og udelukkelse af enheder.
keywords: ioc, certifikat, certifikater, administrer, tilladt, blokeret, bloker, ren, skadelig, filhash, IP-adresse, URL-adresser, domæne
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 7140b5714dd3660fe8dead37c3b6341d026fbb7c
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2021
ms.locfileid: "63597622"
---
# <a name="create-indicators-based-on-certificates"></a>Opret indikatorer baseret på certifikater

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-automationexclusionlist-abovefoldlink)

Du kan oprette indikatorer for certifikater. Nogle almindelige brugstilfælde omfatter:

- Scenarier, hvor du skal implementere blokeringsteknologier, f.eks[](attack-surface-reduction.md). regler for reduktion af [](controlled-folders.md) angrebsoverfladen og styret mappeadgang, men skal tillade funktionsmåder fra signerede programmer ved at tilføje certifikatet på listen over tilladte.
- Blokering af brugen af et bestemt signeret program på tværs af organisationen. Ved at oprette en indikator til at blokere certifikatet for programmet vil Windows Defender AV forhindre filudførelser (blokere og afhjælpe), og Automatiseret undersøgelse og afhjælpning fungerer på samme måde.

## <a name="before-you-begin"></a>Før du begynder

Det er vigtigt at forstå følgende krav, før du opretter indikatorer for certifikater:

- Denne funktion er tilgængelig, hvis din organisation bruger Windows Defender Antivirus og skybaseret beskyttelse er aktiveret. Få mere at vide under [Administrer skybaseret beskyttelse](/windows/security/threat-protection/microsoft-defender-antivirus/deploy-manage-report-microsoft-defender-antivirus).
- Versionen af Antimalware-klienten skal være 4.18.1901.x eller nyere.
- Understøttes på computere på Windows 10, version 1703 eller nyere, Windows Server 2019, Windows Server 2016, Windows Server 2012 R2 og Windows Server 2022.
    
    >[!NOTE]
    >Windows Server 2016 og Windows Server 2012 R2 skal være onboardet ved hjælp af instruktionerne i [Onboard Windows-servere](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016), for at denne funktion kan fungere. 

- Definitionerne af virus- og trusselsbeskyttelse skal være opdateret.
- Denne funktion understøtter i øjeblikket indtastning af . CER eller . PEM-filtypenavne.

> [!IMPORTANT]
>
> - Et gyldigt bladcertifikat er et signeringscertifikat, der har en gyldig certifikatsti og skal være kædet sammen med det rodnøglecenter, som Microsoft har tillid til. Alternativt kan et brugerdefineret certifikat (selv signeret) bruges, så længe klienten har tillid til det (rodnøglecentercertifikatet er installeret under den lokale computer 'Pålidelige rodnøglecenter').
> - Børn eller overordnede for tilladelses-/blokcertifikatets IOC'er er ikke inkluderet i funktionen tillad/bloker IoC, kun bladcertifikater understøttes.
> - Microsoft-signerede certifikater kan ikke blokeres.

## <a name="create-an-indicator-for-certificates-from-the-settings-page"></a>Opret en indikator for certifikater fra siden med indstillinger:

> [!IMPORTANT]
> Det kan tage op til 3 timer at oprette og fjerne et certifikat IoC.

1. I **navigationsruden** skal du **vælge Indstillinger** \> **Slutpunktsindikatorer** \> (under **Regler**).

2. Vælg **Tilføj indikator**.

3. Angiv følgende oplysninger:
   - Indikator – Angiv enhedsdetaljerne, og definer udløb af indikatoren.
   - Handling – Angiv den handling, der skal gøres, og angiv en beskrivelse.
   - Omfang – Definer computergruppens omfang.

4. Gennemgå oplysningerne under fanen Oversigt, og klik derefter på **Gem**.

## <a name="related-topics"></a>Relaterede emner

- [Opret indikatorer](manage-indicators.md)
- [Opret indikatorer for filer](indicator-file.md)
- [Opret indikatorer for IP'er og URL-adresser/domæner](indicator-ip-domain.md)
- [Administrer indikatorer](indicator-manage.md)
