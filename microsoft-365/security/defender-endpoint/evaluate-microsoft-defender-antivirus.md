---
title: Evaluer Microsoft Defender Antivirus
description: Virksomheder i alle størrelser kan bruge denne vejledning til at evaluere og teste den beskyttelse, der tilbydes af Microsoft Defender Antivirus i Windows.
keywords: Microsoft Defender Antivirus, cloudbeskyttelse, cloud, antimalware, sikkerhed, defender, evaluer, test, beskyttelse, sammenlign, beskyttelse i realtid
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
ms.topic: conceptual
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 10/18/2018
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: 89da56c0230772dab59ad02a751c3bb1ada164e7
ms.sourcegitcommit: c314e989202dc1c9c260fffd459d53bc1f08514e
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/12/2022
ms.locfileid: "66717796"
---
# <a name="evaluate-microsoft-defender-antivirus"></a>Evaluer Microsoft Defender Antivirus

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**

- Microsoft Defender Antivirus
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

**Platforme**
- Windows

Brug denne vejledning til at finde ud af, hvor godt Microsoft Defender Antivirus beskytter dig mod virus, malware og potentielt uønskede programmer. Det forklarer de vigtige næste generations beskyttelsesfunktioner i Microsoft Defender Antivirus, der er tilgængelige for både små og store virksomheder, og hvordan de øger registrering og beskyttelse af malware på tværs af dit netværk.

Du kan vælge at konfigurere og evaluere hver indstilling uafhængigt af hinanden eller på én gang. Vi har grupperet lignende indstillinger baseret på typiske evalueringsscenarier og indeholder instruktioner til, hvordan du bruger PowerShell til at aktivere indstillingerne.

Vejledningen er tilgængelig i PDF-format til offlinevisning:

- [Download vejledningen i PDF-format](https://www.microsoft.com/download/details.aspx?id=54795)

Du kan også downloade en PowerShell, der automatisk aktiverer alle de indstillinger, der er beskrevet i vejledningen. Du kan hente scriptet sammen med pdf-downloaden ovenfor eller individuelt fra PowerShell-galleriet:

- [Download PowerShell-scriptet for automatisk at konfigurere indstillingerne](https://www.powershellgallery.com/packages/WindowsDefender_InternalEvaluationSettings)

> [!IMPORTANT]
> Vejledningen er i øjeblikket beregnet til evaluering af Microsoft Defender Antivirus på en enkelt computer. Aktivering af alle indstillingerne i denne vejledning er muligvis ikke egnet til installation i den virkelige verden.
>
> Du kan se de nyeste anbefalinger til installation og overvågning af Microsoft Defender Antivirus på tværs af et netværk i [Installér Microsoft Defender Antivirus](deploy-manage-report-microsoft-defender-antivirus.md).

> [!TIP]
> Hvis du leder efter antivirusrelaterede oplysninger til andre platforme, skal du se:
> - [Angiv indstillinger for Microsoft Defender for Endpoint på macOS-](mac-preferences.md)
> - [Microsoft Defender for Endpoint på Mac](microsoft-defender-endpoint-mac.md)
> - [Politikindstillinger for macOS Antivirus for Microsoft Defender Antivirus for Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Angiv indstillinger for Microsoft Defender for Endpoint på Linux](linux-preferences.md)
> - [Microsoft Defender for Endpoint på Linux](microsoft-defender-endpoint-linux.md)
> - [Konfigurer Defender for Endpoint på Android-funktioner](android-configure.md)
> - [Konfigurer Microsoft Defender for Endpoint på iOS-funktioner](ios-configure-features.md)

## <a name="related-topics"></a>Relaterede emner

- [Microsoft Defender Antivirus i Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [Installér Microsoft Defender Antivirus](deploy-manage-report-microsoft-defender-antivirus.md)