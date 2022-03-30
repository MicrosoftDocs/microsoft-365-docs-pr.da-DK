---
title: Konfigurere udeladelse for Microsoft Defender Antivirus scanninger
description: Du kan udelade filer (herunder filer, der er ændret af angivne processer), og mapper kan ikke scannes af Microsoft Defender Antivirus. Valider dine undtagelser med PowerShell.
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
ms.openlocfilehash: 6ef9cfcec1c54cf9754d7152c098d7ef5b67b456
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63599362"
---
# <a name="configure-and-validate-exclusions-for-microsoft-defender-antivirus-scans"></a>Konfigurere og validere udeladelse for Microsoft Defender Antivirus scanninger

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)


Du kan udelade visse filer, mapper, processer og procesåbnede filer fra Microsoft Defender Antivirus scanninger. Disse undtagelser gælder for [planlagte scanninger](scheduled-catch-up-scans-microsoft-defender-antivirus.md), [scanninger](run-scan-microsoft-defender-antivirus.md) efter behov og altid beskyttelse og overvågning [i realtid](configure-real-time-protection-microsoft-defender-antivirus.md). Udeladelse for proces åbne filer gælder kun for beskyttelse i realtid.

## <a name="configure-and-validate-exclusions"></a>Konfigurere og validere udeladelse

Hvis du vil konfigurere og validere udeladelse, skal du se følgende:

- [Konfigurer og valider udeladelse baseret på filnavn, filtypenavn og mappeplacering](configure-extension-file-exclusions-microsoft-defender-antivirus.md). Du kan udelade filer fra Microsoft Defender Antivirus scanninger baseret på deres filtypenavn, filnavn eller placering.

- [Konfigurer og valider udeladelse af filer, der åbnes af processer](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md). Du kan udelukke filer fra scanninger, der har været åbnet af en bestemt proces.

## <a name="recommendations-for-defining-exclusions"></a>Anbefalinger definition af udeladelse

> [!IMPORTANT]
> Microsoft Defender Antivirus indeholder mange automatiske udeladelsesforanstaltninger, der er baseret på kendte funktionsmåder i operativsystemet og typiske administrationsfiler, f.eks. dem, der bruges i virksomhedsadministration, databaseadministration og andre virksomhedsscenarier og -situationer.
>
> Hvis du definerer udeladelse, sænkes den beskyttelse, der tilbydes Microsoft Defender Antivirus. Du bør altid evaluere de risici, der er forbundet med implementering af udeladelse, og du bør kun udelade filer, som du er sikker på ikke er skadelige.

Husk følgende punkter, når du definerer udeladelse:

- Udeladelse er rent teknisk et sikkerheds hul. Overvej alle dine muligheder, når du definerer udeladelse. Andre indstillinger kan være noget så enkelt som at sørge for, at den ekskluderede placering har de relevante adgangskontrollister (ACLs) eller at indstille politikker til overvågningstilstand i starten.

- Gennemse udeladelse med jævne mellemrum. Gentjek og genhåndhævning af afhjælpninger som en del af din gennemgangsproces.

- Ideelt set bør du undgå at definere udeladelse i et forsøg på at være proaktiv. Du skal f.eks. ikke udelukke noget, blot fordi du tror, at det kan være et problem i fremtiden. Brug kun udeladelse for bestemte problemer, f.eks. vedrørende ydeevne eller programkompatibilitet, som udeladelse kan reducere.

- Gennemse og overhold ændringer af din liste over udeladelses medtagelser. Dit sikkerhedsteam bør bevare konteksten omkring, hvorfor en bestemt udelukkelse blev tilføjet for at undgå forvirring senere. Dit sikkerhedsteam bør kunne give specifikke svar på spørgsmål om, hvorfor udeladelse findes.

## <a name="see-also"></a>Se også

- [Microsoft Defender Antivirus udeladelse på Windows Server 2016](configure-server-exclusions-microsoft-defender-antivirus.md)
- [Almindelige fejl at undgå, når du definerer udeladelse](common-exclusion-mistakes-microsoft-defender-antivirus.md)
