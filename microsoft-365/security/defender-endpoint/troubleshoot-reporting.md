---
title: Fejlfinding af problemer med rapporteringsværktøjer til Microsoft Defender Antivirus
description: Identificer og løs almindelige problemer, når du forsøger at rapportere i Microsoft Defender Antivirus-beskyttelsesstatus i Opdateringsoverholdelse
keywords: fejlfinding, fejl, rettelse, opdateringsoverholdelse, oms, overvåge, rapportere, Microsoft Defender Antivirus
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
ms.openlocfilehash: e17f50eb02fa6fbc3c34526ca064543b7afbdea2
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2021
ms.locfileid: "63593221"
---
# <a name="troubleshoot-microsoft-defender-antivirus-reporting-in-update-compliance"></a>Fejlfinding af Microsoft Defender Antivirus i overholdelse af regler og standarder

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> [!IMPORTANT]
> Den 31. marts 2020 fjernes Microsoft Defender Antivirus rapporteringsfunktionen til overholdelse af opdatering. Du kan fortsætte med at definere og gennemse politikker for overholdelse af sikkerhed [ved hjælp Microsoft Endpoint Manager](https://www.microsoft.com/microsoft-365/microsoft-endpoint-manager) politikker, hvilket giver bedre kontrol over sikkerhedsfunktioner og opdateringer.

Du kan bruge Microsoft Defender Antivirus med overholdelse af regler og standarder. Du får vist status for E3, B, F1, VL og Pro licenser. Men for E5-licenser skal du bruge [Microsoft Defender for Endpoint-portalen](/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints). Du kan få mere at vide om licensmuligheder [Windows 10 produktlicensmuligheder](https://www.microsoft.com/licensing/product-licensing/windows10.aspx).

Når du bruger [Windows Analytics Update Compliance](/windows/deployment/update/update-compliance-using#wdav-assessment) til at få rapportering om beskyttelsesstatus for enheder eller slutpunkter i dit netværk, der bruger Microsoft Defender Antivirus, kan du støde på problemer eller problemer.

Typisk er de mest almindelige indikatorer for et problem:

- Du kan kun se et lille antal eller en delmængde af alle de enheder, du forventede at se
- Du kan slet ikke se nogen enheder
- De rapporter og oplysninger, du får vist, er forældede (ældre end et par dage)

Du kan finde almindelige fejlkoder og hændelses-Microsoft Defender Antivirus, der ikke er relateret til overholdelse af regler og standarder, [Microsoft Defender Antivirus hændelser](troubleshoot-microsoft-defender-antivirus.md).

Der er tre trin til fejlfinding af disse problemer:

1. Bekræft, at du har opfyldt alle forudsætninger
2. Kontrollér forbindelsen til Windows Defender skybaseret tjeneste
3. Sende supportlogfiler

> [!IMPORTANT]
> Det tager som regel 3 dage for enheder at begynde at blive vist i Overholdelse af opdatering.

## <a name="confirm-prerequisites"></a>Bekræft forudsætninger

For at enheder skal vises korrekt i Overholdelse af opdatering, skal du opfylde visse forudsætninger for både overholdelse af opdaterings- og Microsoft Defender Antivirus:

>[!div class="checklist"]
>
> - Slutpunkter bruger Microsoft Defender Antivirus som den eneste antivirusbeskyttelsesapp. [Hvis du bruger et andet antivirusprogram, Microsoft Defender Antivirus deaktivere sig](microsoft-defender-antivirus-compatibility.md) selv, og slutpunktet rapporteres ikke i Overholdelse af opdatering.
> - [Beskyttelse, der leveres i skyen, er aktiveret](enable-cloud-protection-microsoft-defender-antivirus.md).
> - Slutpunkter kan [oprette forbindelse til Microsoft Defender Antivirus skyen](configure-network-connections-microsoft-defender-antivirus.md#validate-connections-between-your-network-and-the-cloud)
> - Hvis slutpunktet kører i Windows 10 version 1607 eller tidligere, [Windows 10 diagnostiske data](/windows/configuration/configure-windows-diagnostic-data-in-your-organization#enhanced-level) være indstillet til det forbedrede niveau.
> - Der er gået 3 dage, siden alle krav er opfyldt

"Du kan bruge Microsoft Defender Antivirus med overholdelse af regler og standarder. Du får vist status for E3, B, F1, VL og Pro licenser. Men for E5-licenser skal du bruge Microsoft Defender til Endpoint-portalen (/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints). Du kan få mere at vide om licensmuligheder Windows 10 produktlicensmuligheder"

Hvis alle ovenstående forudsætninger er opfyldt, skal du muligvis fortsætte til næste trin for at indsamle diagnostiske oplysninger og sende dem til os.

> [!div class="nextstepaction"]
> [Indsaml diagnostiske data til fejlfinding i forbindelse med overholdelse af opdatering](collect-diagnostic-data.md)


## <a name="related-topics"></a>Relaterede emner

- [Microsoft Defender Antivirus i Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [Installér Microsoft Defender Antivirus](deploy-manage-report-microsoft-defender-antivirus.md)
