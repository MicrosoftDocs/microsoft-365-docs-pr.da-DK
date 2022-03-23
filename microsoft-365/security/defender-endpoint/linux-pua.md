---
title: Find og bloker potentielt uønskede programmer med Microsoft Defender til slutpunkt på Linux
description: Find og bloker potentielt uønskede programmer (PUA) ved hjælp af Microsoft Defender til slutpunkt på Linux.
keywords: microsoft, defender, Microsoft Defender til Endpoint, linux, pua, pus
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 03c6f64e7272706262ef622a173e58260468e01b
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2021
ms.locfileid: "63592094"
---
# <a name="detect-and-block-potentially-unwanted-applications-with-microsoft-defender-for-endpoint-on-linux"></a>Find og bloker potentielt uønskede programmer med Microsoft Defender til slutpunkt på Linux

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

Den potentielt uønskede beskyttelsesfunktion (PUA) i Defender til slutpunkt på Linux kan registrere og blokere PUA-filer på slutpunkter i dit netværk.

Disse programmer betragtes ikke som virus, malware eller andre typer af trusler, men kan udføre handlinger på slutpunkter, der påvirker deres ydeevne eller brug. PUA kan også referere til programmer, der anses for at have et dårligt ry.

Disse programmer kan øge risikoen for, at dit netværk bliver inficeret med malware, forårsage malwareinficering til at være sværere at identificere og være spild af it-ressourcer ved oprydning af programmerne.

## <a name="how-it-works"></a>Sådan fungerer det

Defender til Slutpunkt på Linux kan registrere og rapportere PUA-filer. Når PUA-filer er konfigureret i blokeringstilstand, flyttes de til karantæne.

Når der registreres en PUA på et slutpunkt, holder Defender til slutpunkt på Linux en registrering af inficeret i trusselshistorikken. Historikken kan visualiseres fra Microsoft 365 Defender portal eller via `mdatp` kommandolinjeværktøjet. Trusselsnavnet vil indeholde ordet "Application".

## <a name="configure-pua-protection"></a>Konfigurere PUA-beskyttelse

PUA-beskyttelse i Defender til slutpunkt på Linux kan konfigureres på en af følgende måder:

- **Fra**: PUA-beskyttelse er deaktiveret.
- **Overvågning**: PUA-filer rapporteres i produktlogfilerne, men ikke i Microsoft 365 Defender. Der gemmes ingen registrering af instrusler i trusselsoversigten, og produktet kan ikke gøre noget.
- **Bloker**: PUA-filer rapporteres i produktlogfilerne og Microsoft 365 Defender. Der gemmes en post for instruensen i trusselsoversigten, og produktet tager skridtet.

> [!WARNING]
> Som standard er PUA-beskyttelse konfigureret i **overvågningstilstand** .

Du kan konfigurere, hvordan PUA-filer håndteres fra kommandolinjen eller fra administrationskonsollen.

### <a name="use-the-command-line-tool-to-configure-pua-protection"></a>Brug kommandolinjeværktøjet til at konfigurere PUA-beskyttelse:

I Terminal skal du udføre følgende kommando for at konfigurere PUA-beskyttelse:

```bash
mdatp threat policy set --type potentially_unwanted_application --action [off|audit|block]
```

### <a name="use-the-management-console-to-configure-pua-protection"></a>Brug administrationskonsollen til at konfigurere PUA-beskyttelse:

I din virksomhed kan du konfigurere PUA-beskyttelse fra en administrationskonsol, f.eks Programmer eller Ansible, på samme måde som andre produktindstillinger er konfigureret. Du kan finde flere oplysninger [i afsnittet Indstillinger for Trusselstype](linux-preferences.md#threat-type-settings) [i artiklen Angiv indstillinger for Defender til Slutpunkt på Linux](linux-preferences.md) .

## <a name="related-articles"></a>Relaterede artikler

- [Angiv indstillinger for Defender til slutpunkt på Linux](linux-preferences.md)
