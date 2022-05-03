---
title: Få mere at vide om Microsoft Purview-udvidelsen
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: conceptual
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
search.appverid:
- MET150
description: Microsoft Purview Extension udvider overvågning og kontrol af filaktiviteter og beskyttende handlinger til Google Chrome-browseren
ms.openlocfilehash: a74cfeb734f41622d491c8aaffe3a5e054479a2a
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/03/2022
ms.locfileid: "65172246"
---
# <a name="learn-about-the-microsoft-purview-extension"></a>Få mere at vide om Microsoft Purview-udvidelsen

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

[Forebyggelse af datatab for slutpunkter (slutpunkt DLP)](endpoint-dlp-learn-about.md) udvider aktivitetsovervågnings- og beskyttelsesfunktionerne i [Microsoft Purview DLP (forebyggelse af datatab)](dlp-learn-about-dlp.md) til følsomme elementer, der findes på Windows 10 enheder. Når enheder er onboardet i Microsoft Purview-løsninger, bliver oplysningerne om, hvad brugerne foretager sig med følsomme elementer, synlige i [Aktivitetsoversigt](data-classification-activity-explorer.md) , og du kan gennemtvinge beskyttende handlinger på disse elementer via [DLP-politikker](create-test-tune-dlp-policy.md).

Når udvidelsen er installeret på en Windows 10 enhed, kan organisationer overvåge, hvornår en bruger forsøger at få adgang til eller uploade et følsomt element til en cloudtjeneste ved hjælp af Google Chrome og gennemtvinge beskyttende handlinger via DLP.  

## <a name="activities-you-can-monitor-and-take-action-on"></a>Aktiviteter, du kan overvåge og udføre handlinger på

Udvidelsen giver dig mulighed for at overvåge og administrere følgende typer aktiviteter, som brugerne udfører på følsomme elementer på enheder, der kører Windows 10.

Aktivitet |Beskrivelse  | understøttede politikhandlinger|
|---------|---------|---------|
|fil, der er kopieret til skyen  | Registrerer, når en bruger forsøger at uploade et følsomt element til et tjenestedomæne med begrænset adgang via Chrome-browseren |overvågning, blok med tilsidesættelse, blok|
|udskrevet fil  |Registrerer, når en bruger forsøger at udskrive et følsomt element, der er åbent i Chrome-browseren, til en lokal printer eller netværksprinter |overvågning, blok med tilsidesættelse, blok|
|fil, der er kopieret til Udklipsholder |Registrerer, når en bruger forsøger at kopiere oplysninger fra et følsomt element, der vises i Chrome-browseren, og indsætter dem derefter i en anden app, i en anden proces eller et andet element. |overvågning, blok med tilsidesættelse, blok|
|fil, der er kopieret til et flytbart lager    | Registrerer, når en bruger forsøger at kopiere et følsomt element eller oplysninger fra et følsomt element, der er åbent i Chrome-browseren, til flytbare medier eller USB-enheder |overvågning, blok med tilsidesættelse, blok|
|fil, der er kopieret til netværksshare  |Registrerer, når en bruger forsøger at kopiere et følsomt element eller oplysninger fra et følsomt element, der er åbent i Chrome-browseren, til et netværksshare eller et tilknyttet netværksdrev.|overvågning, blok med tilsidesættelse, blok |

## <a name="deployment-process"></a>Installationsproces
1. [Kom i gang med forebyggelse af datatab for slutpunkter](endpoint-dlp-getting-started.md)
2. [Onboardingværktøjer og -metoder til Windows 10 enheder](device-onboarding-overview.md)
3. [Installér udvidelsen på dine Windows 10 enheder](dlp-chrome-get-started.md)
4. [Opret eller rediger DLP-politikker](create-test-tune-dlp-policy.md), der begrænser upload til cloudtjenesten, eller adgang via ikke-tilladte browserhandlinger og anvend dem på dine Windows 10 enheder

## <a name="next-steps"></a>Næste trin

Se [Kom i gang med Microsoft Purview-udvidelsen for at](dlp-chrome-get-started.md) få oplysninger om komplette udrulningsprocedurer og -scenarier.

## <a name="see-also"></a>Se også

- [Kom i gang med Microsoft Purview-udvidelsen](dlp-chrome-get-started.md)
- [Få mere at vide om forebyggelse af datatab ved slutpunkt](endpoint-dlp-learn-about.md)
- [Introduktion til forebyggelse af datatab i Slutpunkt](endpoint-dlp-getting-started.md)
- [Brug forebyggelse af datatab ved slutpunkt](endpoint-dlp-using.md)
- [Få mere at vide om forebyggelse af datatab](dlp-learn-about-dlp.md)
- [Opret, test og finjuster en DLP-politik](create-test-tune-dlp-policy.md)
- [Kom i gang med Aktivitetsoversigt](data-classification-activity-explorer.md)
- [Microsoft Defender for Endpoint](/windows/security/threat-protection/)
- [Styring af insider-risiko](insider-risk-management.md)
