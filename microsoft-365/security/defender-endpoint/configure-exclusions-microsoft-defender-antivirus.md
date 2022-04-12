---
title: Konfigurer udeladelser for Microsoft Defender Antivirus scanninger
description: Du kan udelade filer (herunder filer, der er ændret af angivne processer) og mapper fra at blive scannet af Microsoft Defender Antivirus. Valider dine udeladelser med PowerShell.
keywords: ''
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ksarens
manager: dansimp
ms.technology: mde
ms.audience: ITPro
ms.topic: how-to
ms.collection: m365-security-compliance
ms.openlocfilehash: c9796f4e5154fd46d1479f0cbfa25f2afaf4e9bb
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/12/2022
ms.locfileid: "64787506"
---
# <a name="configure-and-validate-exclusions-for-microsoft-defender-antivirus-scans"></a>Konfigurer og valider udeladelser for Microsoft Defender Antivirus scanninger

**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Antivirus

**Platforme**
- Windows

Du kan udelade visse filer, mapper, processer og procesåbnede filer fra Microsoft Defender Antivirus scanninger. Sådanne undtagelser gælder for [planlagte scanninger](scheduled-catch-up-scans-microsoft-defender-antivirus.md), [efter behovsscanninger](run-scan-microsoft-defender-antivirus.md) og altid i [realtid beskyttelse og overvågning](configure-real-time-protection-microsoft-defender-antivirus.md). Undtagelser for procesåbnede filer gælder kun for beskyttelse i realtid.

## <a name="configure-and-validate-exclusions"></a>Konfigurer og valider udeladelser

Hvis du vil konfigurere og validere udeladelser, skal du se følgende:

- [Konfigurer og valider udeladelser baseret på filnavn, filtypenavn og mappeplacering](configure-extension-file-exclusions-microsoft-defender-antivirus.md). Du kan udelade filer fra Microsoft Defender Antivirus scanninger baseret på filtypenavnet, filnavnet eller placeringen.

- [Konfigurer og valider udeladelser for filer, der er åbnet af processer](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md). Du kan udelade filer fra scanninger, der er blevet åbnet af en bestemt proces.

## <a name="recommendations-for-defining-exclusions"></a>Anbefalinger til definition af udeladelser

> [!IMPORTANT]
> Microsoft Defender Antivirus omfatter mange automatiske undtagelser, der er baseret på kendte funktionsmåder i operativsystemet og typiske administrationsfiler, f.eks. dem, der bruges i virksomhedsadministration, databaseadministration og andre virksomhedsscenarier og -situationer.
>
> Definition af udeladelser reducerer den beskyttelse, der tilbydes af Microsoft Defender Antivirus. Du bør altid evaluere de risici, der er forbundet med implementering af undtagelser, og du bør kun ekskludere filer, som du er sikker på ikke er skadelige.

Vær opmærksom på følgende punkter, når du definerer udeladelser:

- Udelukkelser er teknisk set et beskyttelsesgab. Overvej alle dine muligheder, når du definerer udeladelser. Andre indstillinger kan være lige så enkle som at sikre, at den udeladte placering har de relevante adgangskontrollister (ACL'er) eller at angive politikker til overvågningstilstand i første omgang.

- Gennemse undtagelserne jævnligt. Kontrollér og gennemtving afhjælpninger igen som en del af korrekturprocessen.

- Ideelt set bør du undgå at definere undtagelser i et forsøg på at være proaktive. Du skal f.eks. ikke udelade noget, bare fordi du mener, at det kan være et problem i fremtiden. Brug kun undtagelser til specifikke problemer, f.eks. problemer, der vedrører ydeevne eller programkompatibilitet, som udeladelser kan afhjælpe.

- Gennemse og overvåg ændringer af listen over undtagelser. Dit sikkerhedsteam bør bevare konteksten omkring, hvorfor en bestemt udelukkelse blev tilføjet for at undgå forvirring senere. Dit sikkerhedsteam bør kunne give specifikke svar på spørgsmål om, hvorfor der findes undtagelser.

> [!TIP]
> Hvis du leder efter antivirusrelaterede oplysninger til andre platforme, kan du se:
> - [Angiv indstillinger for Microsoft Defender for Endpoint på macOS](mac-preferences.md)
> - [Microsoft Defender for Endpoint på Mac](microsoft-defender-endpoint-mac.md)
> - [macOS Antivirus politikindstillinger for Microsoft Defender Antivirus til Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Angiv indstillinger for Microsoft Defender for Endpoint på Linux](linux-preferences.md)
> - [Microsoft Defender for Endpoint på Linux](microsoft-defender-endpoint-linux.md)
> - [Konfigurer Defender for Endpoint på Android-funktioner](android-configure.md)
> - [Konfigurer Microsoft Defender for Endpoint på iOS-funktioner](ios-configure-features.md)

## <a name="see-also"></a>Se også

- [Microsoft Defender Antivirus udeladelser på Windows Server 2016](configure-server-exclusions-microsoft-defender-antivirus.md)
- [Almindelige fejl, der skal undgås, når du definerer udeladelser](common-exclusion-mistakes-microsoft-defender-antivirus.md)
