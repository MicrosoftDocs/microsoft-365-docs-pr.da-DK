---
title: Foretag fejlfinding af problemer med rapporteringsværktøjer til Microsoft Defender Antivirus
description: Identificer og løs almindelige problemer, når du forsøger at rapportere i Microsoft Defender Antivirus beskyttelsesstatus i Opdateringsoverholdelse
keywords: fejlfinding, fejl, rettelse, opdateringsoverholdelse, oms, overvågning, rapport Microsoft Defender Antivirus
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: bf65bb13ab45d127bf2302464f1948437e1fe02d
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/14/2022
ms.locfileid: "65417968"
---
# <a name="troubleshoot-microsoft-defender-antivirus-reporting-in-update-compliance"></a>Fejlfinding af Microsoft Defender Antivirus-rapportering i Update Compliance

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Antivirus

**Platforme**
- Windows

> [!IMPORTANT]
> Den 31. marts 2020 fjernes funktionen Microsoft Defender Antivirus rapportering i Opdateringsoverholdelse. Du kan fortsætte med at definere og gennemse politikker for overholdelse af sikkerhed ved hjælp af [Microsoft Endpoint Manager](https://www.microsoft.com/microsoft-365/microsoft-endpoint-manager), hvilket giver bedre kontrol over sikkerhedsfunktioner og opdateringer.

Du kan bruge Microsoft Defender Antivirus med Opdateringsoverholdelse. Du får vist status for E3-, B-, F1-, VL- og Pro-licenser. Men for E5-licenser skal du bruge [Microsoft Defender for Endpoint-portalen](/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints). Du kan få mere at vide om licensmuligheder under [Windows 10 muligheder for produktlicenser](https://www.microsoft.com/licensing/product-licensing/windows10.aspx).

Når du bruger [overholdelse af Windows analytics-opdatering til at få rapportering til beskyttelsesstatus for enheder eller slutpunkter](/windows/deployment/update/update-compliance-using#wdav-assessment) på dit netværk, der bruger Microsoft Defender Antivirus, kan du støde på problemer eller problemer.

De mest almindelige indikatorer for et problem er typisk:

- Du kan kun se et lille antal eller et undersæt af alle de enheder, du forventede at se
- Du kan slet ikke se nogen enheder
- De rapporter og oplysninger, du kan se, er forældede (ældre end et par dage)

Du kan se almindelige fejlkoder og hændelses-id'er relateret til den Microsoft Defender Antivirus tjeneste, der ikke er relateret til Opdateringsoverholdelse, [under Microsoft Defender Antivirus hændelser](troubleshoot-microsoft-defender-antivirus.md).

Der er tre trin til fejlfinding af disse problemer:

1. Bekræft, at du har opfyldt alle forudsætninger
2. Kontrollér din forbindelse til den Windows Defender cloudbaserede tjeneste
3. Send supportlogge

> [!IMPORTANT]
> Det tager typisk tre dage, før enheder begynder at blive vist i Opdateringsoverholdelse.

## <a name="confirm-prerequisites"></a>Bekræft forudsætninger

Hvis enheder skal vises korrekt i opdateringsoverholdelse, skal du opfylde visse forudsætninger for både tjenesten Opdateringsoverholdelse og for Microsoft Defender Antivirus:

>[!div class="checklist"]
>
> - Slutpunkter bruger Microsoft Defender Antivirus som den eneste antivirusbeskyttelsesapp. [Brug af en anden antivirusapp medfører, at Microsoft Defender Antivirus deaktiverer sig selv](microsoft-defender-antivirus-compatibility.md), og slutpunktet rapporteres ikke i Opdateringsoverholdelse.
> - [Skybaseret beskyttelse er aktiveret](enable-cloud-protection-microsoft-defender-antivirus.md).
> - Slutpunkter kan [oprette forbindelse til Microsoft Defender Antivirus cloudmiljøet](configure-network-connections-microsoft-defender-antivirus.md#validate-connections-between-your-network-and-the-cloud)
> - Hvis slutpunktet kører Windows 10 version 1607 eller tidligere, [skal Windows 10 diagnosticeringsdata angives til niveauet Udvidet](/windows/configuration/configure-windows-diagnostic-data-in-your-organization#enhanced-level).
> - Der er gået tre dage, siden alle krav er opfyldt

"Du kan bruge Microsoft Defender Antivirus med Opdateringsoverholdelse. Du får vist status for E3-, B-, F1-, VL- og Pro-licenser. Men for E5-licenser skal du bruge Microsoft Defender for Endpoint-portalen (/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints). Hvis du vil vide mere om licensmuligheder, skal du se Windows 10 muligheder for produktlicens"

Hvis ovenstående forudsætninger alle er opfyldt, skal du muligvis gå videre til næste trin for at indsamle diagnosticeringsoplysninger og sende dem til os.

> [!div class="nextstepaction"]
> [Indsaml diagnosticeringsdata til fejlfinding af opdateringsoverholdelse](collect-diagnostic-data.md)

> [!TIP]
> Hvis du leder efter antivirusrelaterede oplysninger til andre platforme, kan du se:
> - [Angiv indstillinger for Microsoft Defender for Endpoint på macOS-](mac-preferences.md)
> - [Microsoft Defender for Endpoint på Mac](microsoft-defender-endpoint-mac.md)
> - [Politikindstillinger for macOS Antivirus for Microsoft Defender Antivirus for Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Angiv indstillinger for Microsoft Defender for Endpoint på Linux](linux-preferences.md)
> - [Microsoft Defender for Endpoint på Linux](microsoft-defender-endpoint-linux.md)
> - [Konfigurer Defender for Endpoint på Android-funktioner](android-configure.md)
> - [Konfigurer Microsoft Defender for Endpoint på iOS-funktioner](ios-configure-features.md)

## <a name="related-topics"></a>Relaterede emner

- [Microsoft Defender Antivirus i Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [Installer Microsoft Defender Antivirus](deploy-manage-report-microsoft-defender-antivirus.md)
