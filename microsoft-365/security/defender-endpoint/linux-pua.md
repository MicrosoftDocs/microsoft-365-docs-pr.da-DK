---
title: Registrer og bloker potentielt uønskede programmer med Microsoft Defender for Endpoint på Linux
description: Registrer og bloker potentielt uønskede programmer (PUA) ved hjælp af Microsoft Defender for Endpoint på Linux.
keywords: microsoft, defender, Microsoft Defender for Endpoint, linux, pua, pus
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
ms.openlocfilehash: 004a9d7af09e8a2abb656c29db558d797173edcd
ms.sourcegitcommit: 612ce4d15d8a2fdbf7795393b50af477d81b6139
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/24/2022
ms.locfileid: "65663596"
---
# <a name="detect-and-block-potentially-unwanted-applications-with-microsoft-defender-for-endpoint-on-linux"></a>Registrer og bloker potentielt uønskede programmer med Microsoft Defender for Endpoint på Linux

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

Den potentielt uønskede funktion til programbeskyttelse i Defender for Endpoint på Linux kan registrere og blokere PUA-filer på slutpunkter i dit netværk.

Disse programmer betragtes ikke som virus, malware eller andre typer trusler, men kan udføre handlinger på slutpunkter, der påvirker deres ydeevne eller brug negativt. PUA kan også henvise til programmer, der anses for at have et dårligt omdømme.

Disse programmer kan øge risikoen for, at dit netværk bliver inficeret med malware, forårsage, at malwareinfektioner bliver sværere at identificere, og kan spilde it-ressourcer i at rydde op i programmerne.

## <a name="how-it-works"></a>Sådan fungerer det

Defender for Endpoint på Linux kan registrere og rapportere PUA-filer. Når pua-filer er konfigureret i blokerende tilstand, flyttes de til karantænen.

Når der registreres en PUA på et slutpunkt, registrerer Defender for Endpoint på Linux infektionen i trusselshistorikken. Oversigten kan visualiseres fra Microsoft 365 Defender-portalen eller via `mdatp` kommandolinjeværktøjet. Trusselsnavnet indeholder ordet "Program".

## <a name="configure-pua-protection"></a>Konfigurer PUA-beskyttelse

PUA-beskyttelse i Defender for Endpoint på Linux kan konfigureres på en af følgende måder:

- **Fra**: PUA-beskyttelse er deaktiveret.
- **Overvågning**: PUA-filer rapporteres i produktlogfilerne, men ikke i Microsoft 365 Defender. Ingen registrering af infektionen er gemt i trusselshistorikken, og produktet tager ingen handling.
- **Blok**: PUA-filer rapporteres i produktlogfilerne og i Microsoft 365 Defender. En registrering af infektionen opbevares i trusselshistorikken, og handling træffes af produktet.

> [!WARNING]
> Som standard er PUA-beskyttelse konfigureret i **overvågningstilstand** .

Du kan konfigurere, hvordan PUA-filer håndteres fra kommandolinjen eller fra administrationskonsollen.

### <a name="use-the-command-line-tool-to-configure-pua-protection"></a>Brug kommandolinjeværktøjet til at konfigurere PUA-beskyttelse:

Udfør følgende kommando i Terminal for at konfigurere PUA-beskyttelse:

```bash
mdatp threat policy set --type potentially_unwanted_application --action [off|audit|block]
```

### <a name="use-the-management-console-to-configure-pua-protection"></a>Brug administrationskonsollen til at konfigurere PUA-beskyttelse:

I din virksomhed kan du konfigurere PUA-beskyttelse fra en administrationskonsol, f.eks. Dukke eller Ansible, på samme måde som andre produktindstillinger er konfigureret. Du kan finde flere oplysninger i afsnittet [Indstillinger for trusselstype](linux-preferences.md#threat-type-settings) i artiklen [Angiv indstillinger for Defender for Endpoint på Linux](linux-preferences.md) .

## <a name="related-articles"></a>Relaterede artikler

- [Angiv indstillinger for Defender for Endpoint på Linux](linux-preferences.md)
