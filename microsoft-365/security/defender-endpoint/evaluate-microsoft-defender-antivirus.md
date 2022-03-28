---
title: Evaluer Microsoft Defender Antivirus
description: Virksomheder i alle størrelser kan bruge denne vejledning til at evaluere og teste den beskyttelse, der tilbydes Microsoft Defender Antivirus i Windows.
keywords: Microsoft Defender Antivirus, skybeskyttelse, sky, antimalware, sikkerhed, defender, evaluer, test, beskyttelse, sammenlign, beskyttelse i realtid
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
ms.openlocfilehash: 4dd25a599f144a60bfd2ebeb3e9bb8b1876bd3c6
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/14/2022
ms.locfileid: "63597891"
---
# <a name="evaluate-microsoft-defender-antivirus"></a>Evaluer Microsoft Defender Antivirus

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

Brug denne vejledning til at bestemme, hvor Microsoft Defender Antivirus beskytter dig mod virus, malware og potentielt uønskede programmer.

> [!TIP]
>Du kan også besøge demowebstedet for Microsoft Defender til Endpoint [på demo.wd.microsoft.com](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) for at bekræfte, at følgende funktioner virker, og se, hvordan de fungerer:
>
> - Cloud-leveret beskyttelse
> - Hurtig læring (herunder Blok ved første synsviden)
> - Potentielt uønsket programblokering

> [!NOTE]
> Defender for Endpoint-demowebstedet demo.wd.microsoft.com forældet og fjernes fremover.

I den forklares de vigtige funktioner til næste generations beskyttelse af Microsoft Defender Antivirus, der er tilgængelige for både små og store virksomheder, og hvordan de øger registrering af malware og beskyttelse på tværs af dit netværk.

Du kan vælge at konfigurere og evaluere hver indstilling enkeltvis eller alle på én gang. Vi har grupperet lignende indstillinger baseret på typiske evalueringsscenarier og indeholder instruktioner om brug af PowerShell til at aktivere indstillingerne.

Vejledningen er tilgængelig i PDF-format til offlinevisning:

- [Download vejledningen i PDF-format](https://www.microsoft.com/download/details.aspx?id=54795)

Du kan også downloade en PowerShell, der automatisk aktiverer alle de indstillinger, der er beskrevet i vejledningen. Du kan hente scriptet sammen med PDF-downloaden ovenfor eller individuelt fra PowerShell Gallery:

- [Download PowerShell-scriptet for at konfigurere indstillingerne automatisk](https://www.powershellgallery.com/packages/WindowsDefender_InternalEvaluationSettings)

> [!IMPORTANT]
> Vejledningen er i øjeblikket beregnet til evaluering af Microsoft Defender Antivirus. Aktivering af alle indstillingerne i denne vejledning er muligvis ikke egnet til den virkelige installation.
>
> Du kan finde de nyeste anbefalinger til den virkelige installation og overvågning af Microsoft Defender Antivirus på tværs af et netværk under [Installér Microsoft Defender Antivirus](deploy-manage-report-microsoft-defender-antivirus.md).

## <a name="related-topics"></a>Relaterede emner

- [Microsoft Defender Antivirus i Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [Installér Microsoft Defender Antivirus](deploy-manage-report-microsoft-defender-antivirus.md)