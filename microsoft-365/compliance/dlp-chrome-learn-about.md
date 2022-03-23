---
title: Få mere at vide om Microsoft-udvidelse til overholdelse af regler og standarder
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
description: Microsoft Overholdelsesudvidelse udvider overvågning og kontrol af filaktiviteter og beskyttende handlinger til Google Chrome-browseren
ms.openlocfilehash: 15c62369bb8b4fc02926fa0e2b0bfc4834c371ac
ms.sourcegitcommit: 966344e1aa442a4d10a0fb05f56badd38c833bb2
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/19/2022
ms.locfileid: "63593410"
---
# <a name="learn-about-the-microsoft-compliance-extension"></a>Få mere at vide om Microsoft-udvidelse til overholdelse af regler og standarder

[Forebyggelse af datatab på slutpunkt (slutpunkt DLP)](endpoint-dlp-learn-about.md) udvider aktivitetsovervågnings- og beskyttelsesfunktionerne i [Microsoft 365 forebyggelse af datatab (DLP)](dlp-learn-about-dlp.md) til følsomme elementer, der findes på Windows 10 enheder. Når enheder er onboardet til løsninger til overholdelse af Microsoft 365, bliver oplysningerne om, hvad brugerne gør med følsomme elementer, synlige i Aktivitetsoversigt, og du kan gennemtvinge beskyttende handlinger for disse elementer via [DLP-politikker](create-test-tune-dlp-policy.md).[](data-classification-activity-explorer.md)

Når Microsoft Overholdelsesudvidelse er installeret på en Windows 10-enhed, kan organisationer overvåge, når en bruger forsøger at få adgang til eller overføre et følsomt element til en skybaseret tjeneste ved hjælp af Google Chrome og gennemtvinge beskyttende handlinger via DLP.  

## <a name="activities-you-can-monitor-and-take-action-on"></a>Aktiviteter, du kan overvåge og handle på

Microsoft-overholdelsesudvidelsen giver dig mulighed for at overvåge og administrere følgende typer af aktiviteter, som brugere tager på følsomme elementer på enheder, der Windows 10.

aktivitet |beskrivelse  | understøttede politikhandlinger|
|---------|---------|---------|
|fil, der er kopieret til skyen  | Registrerer, når en bruger forsøger at overføre et følsomt element til et begrænset tjenestedomæne via Chrome-browseren |overvågning, bloker med tilsidesættelse, bloker|
|fil udskrevet  |Registrerer, når en bruger forsøger at udskrive et følsomt element, der er åbent i Chrome-browseren, på en lokal printer eller netværksprinter |overvågning, bloker med tilsidesættelse, bloker|
|Fil kopieret til Udklipsholder |Registrerer, når en bruger forsøger at kopiere oplysninger fra et følsomt element, der vises i Chrome-browseren, og indsætter dem derefter i en anden app, proces eller et andet element. |overvågning, bloker med tilsidesættelse, bloker|
|Fil kopieret til flytbart lager    | Registrerer, når en bruger forsøger at kopiere et følsomt element eller oplysninger fra et følsomt element, der er åbent i Chrome-browseren til flytbare medier eller USB-enhed |overvågning, bloker med tilsidesættelse, bloker|
|Fil, der er kopieret til netværksdeling  |Registrerer, når en bruger forsøger at kopiere et følsomt element eller oplysninger fra et følsomt element, der er åbent i Chrome-browseren, til et netværksshare eller tilknyttet netværksdrev.|overvågning, bloker med tilsidesættelse, bloker |

## <a name="deployment-process"></a>Installationsproces
1. [Introduktion til forebyggelse af datatab på slutpunkt](endpoint-dlp-getting-started.md)
2. [Onboardingværktøjer og metoder til Windows 10 enheder](device-onboarding-overview.md)
3. [Installér udvidelsen på dine Windows 10-enheder](dlp-chrome-get-started.md)
4. [Opret eller rediger DLP-politikker](create-test-tune-dlp-policy.md), der begrænser upload til skytjeneste eller adgang ved ikke-tilladte browserhandlinger, og anvend dem på dine Windows 10 enheder

## <a name="next-steps"></a>Næste trin

Se [Introduktion til Microsoft Overholdelsesudvidelsen](dlp-chrome-get-started.md) for at få komplette installationsprocedurer og -scenarier.

## <a name="see-also"></a>Se også

- [Kom i gang med Microsoft-udvidelse til overholdelse af regler og standarder](dlp-chrome-get-started.md)
- [Få mere at Microsoft 365 om forebyggelse af datatab på slutpunkter](endpoint-dlp-learn-about.md)
- [Introduktion til forebyggelse af datatab i Microsoft Endpoint](endpoint-dlp-getting-started.md)
- [Brug af forebyggelse af datatab i Microsoft Endpoint](endpoint-dlp-using.md)
- [Få mere at vide om forebyggelse af datatab](dlp-learn-about-dlp.md)
- [Opret, test og finjuster en DLP-politik](create-test-tune-dlp-policy.md)
- [Introduktion til Aktivitetsstifinder](data-classification-activity-explorer.md)
- [Microsoft Defender til Slutpunkt](/windows/security/threat-protection/)
- [Insider-risikostyring](insider-risk-management.md)
