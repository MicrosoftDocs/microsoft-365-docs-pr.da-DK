---
title: Find og bloker potentielt uønskede programmer med Microsoft Defender til Slutpunkt på Mac
description: Find og bloker potentielt uønskede programmer (PUA) ved hjælp af Microsoft Defender til slutpunkt på macOS.
keywords: microsoft, defender, Microsoft Defender til Endpoint, mac, pua, pus
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
ms.openlocfilehash: a0fb8e19dd573da67936892c81cd515b463a7cba
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/12/2022
ms.locfileid: "63592011"
---
# <a name="detect-and-block-potentially-unwanted-applications-with-microsoft-defender-for-endpoint-on-macos"></a>Find og bloker potentielt uønskede programmer med Microsoft Defender til Endpoint på macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Den potentielt uønskede programbeskyttelsesfunktion (PUA) i Microsoft Defender til slutpunkt på macOS kan registrere og blokere PUA-filer på slutpunkter i dit netværk.

Disse programmer betragtes ikke som virus, malware eller andre typer af trusler, men kan udføre handlinger på slutpunkter, der påvirker deres ydeevne eller brug. PUA kan også referere til programmer, der anses for at have et dårligt ry.

Disse programmer kan øge risikoen for, at dit netværk bliver inficeret med malware, forårsage malwareinficering til at være sværere at identificere og være spild af it-ressourcer ved oprydning af programmerne.

## <a name="how-it-works"></a>Sådan fungerer det

Microsoft Defender til slutpunkt på macOS kan registrere og rapportere PUA-filer. Når PUA-filer er konfigureret i blokeringstilstand, flyttes de til karantæne.

Når der registreres en PUA på et slutpunkt, præsenterer Microsoft Defender for Endpoint på macOS en meddelelse til brugeren, medmindre meddelelser er blevet deaktiveret. Trusselsnavnet vil indeholde ordet "Application".

## <a name="configure-pua-protection"></a>Konfigurere PUA-beskyttelse

PUA-beskyttelse i Microsoft Defender til slutpunkt på macOS kan konfigureres på en af følgende måder:

- **Fra**: PUA-beskyttelse er deaktiveret.
- **Overvågning**: PUA-filer rapporteres i produktlogfilerne, men ikke i Microsoft 365 Defender portal. Brugeren får ingen besked, og produktet kan ikke gøre noget.
- **Bloker**: PUA-filer rapporteres i produktlogfilerne og Microsoft 365 Defender portal. Brugeren får vist en meddelelse, og produktet gør noget ved det.

> [!WARNING]
> Som standard er PUA-beskyttelse konfigureret i **overvågningstilstand** .

Du kan konfigurere, hvordan PUA-filer håndteres fra kommandolinjen eller fra administrationskonsollen.

### <a name="use-the-command-line-tool-to-configure-pua-protection"></a>Brug kommandolinjeværktøjet til at konfigurere PUA-beskyttelse:

I Terminal skal du udføre følgende kommando for at konfigurere PUA-beskyttelse:

```bash
mdatp threat policy set --type potentially_unwanted_application --action [off|audit|block]
```

### <a name="use-the-management-console-to-configure-pua-protection"></a>Brug administrationskonsollen til at konfigurere PUA-beskyttelse:

I din virksomhed kan du konfigurere PUA-beskyttelse fra en administrationskonsol, f.eks. SYLF eller Intune, på samme måde som andre produktindstillinger er konfigureret. Du kan finde flere oplysninger i [afsnittet Indstillinger for Trusselstype](mac-preferences.md#threat-type-settings) i [emnet Angiv indstillinger for Microsoft Defender til Slutpunkt på macOS](mac-preferences.md) .

## <a name="related-topics"></a>Relaterede emner

- [Angiv indstillinger for Microsoft Defender for Endpoint på macOS](mac-preferences.md)
