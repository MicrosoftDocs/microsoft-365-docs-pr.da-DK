---
title: Brug Microsoft 365 lokal scanner til forebyggelse af datatab
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: how-to
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
description: Få mere at vide om, hvordan du bruger den lokale scanner Microsoft 365 til forebyggelse af datatab og implementere beskyttende handlinger for lokale filshares og lokale SharePoint-mapper og dokumentbiblioteker.
ms.openlocfilehash: d726bfccf7dff2e95e3ccf996544f1db26bf09a2
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63593405"
---
# <a name="use-the-microsoft-365-data-loss-prevention-on-premises-scanner"></a>Brug Microsoft 365 lokal scanner til forebyggelse af datatab

For at gøre dig bekendt med DLP-funktioner i det lokale miljø, og hvordan de findes i DLP-politikker, har vi samlet nogle scenarier, som du kan følge.

> [!IMPORTANT]
> Disse lokale DLP-scenarier er ikke de officielle procedurer for oprettelse og justering af DLP-politikker. Se nedenstående emner, når du har brug for at arbejde med DLP-politikker i generelle situationer:
>
> - [Få mere at vide om forebyggelse af datatab](dlp-learn-about-dlp.md)
> - [Introduktion til DLP-standardpolitikken](get-started-with-the-default-dlp-policy.md)
> - [Opret en DLP-politik ud fra en skabelon](create-a-dlp-policy-from-a-template.md)
> - [Opret, test og finjuster en DLP-politik](create-test-tune-dlp-policy.md)

### <a name="scenario-discover-files-matching-dlp-rules"></a>Scenarie: Find filer, der matcher DLP-regler

Data fra lokale DLP-scanneroverflader i flere områder

#### <a name="activity-explorer"></a>Aktivitetsstifinder

 Microsoft DLP til det lokale miljø registrerer DLP-regel match og rapporterer dem til [Aktivitetsoversigt](https://compliance.microsoft.com/dataclassification?viewid=activitiesexplorer).

#### <a name="microsoft-365-audit-log"></a>Microsoft 365 overvågningslog

DLP-regeloverensstemmelsen er tilgængelig i brugergrænsefladen til overvågningsloggen, se Søg i overvågningsloggen i overholdelsescenteret eller tilgængelig via [Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog) PowerShell.[](search-the-audit-log-in-security-and-compliance.md)

#### <a name="aip"></a>AIP

Discovery-data er tilgængelige i en lokal rapport i CSV-format, som er gemt under:

**%localappdata%\Microsoft\MSIP\Scanner\Reports\DetailedReport_%timestamp%.csv report**.

 Se efter følgende kolonner:

- DLP-tilstand
- DLP-status
- DLP-kommentar
- Navn på DLP-regel
- DLP-handlinger
- Ejer
- Aktuelle NTFS-tilladelser (SDDL)
- Anvendt NTFS-tilladelser (SDDL)
- Type af NTFS-tilladelser

### <a name="scenario-enforce-dlp-rule"></a>Scenarie: Gennemtving DLP-regel

Hvis du vil gennemtvinge DLP-regler på scannede filer, skal gennemtvingelse være aktiveret både for indholdsscanningsjobbet i AIP og på politikniveau i DLP.

#### <a name="configure-dlp-to-enforce-policy-actions"></a>Konfigurere DLP til at gennemtvinge politikhandlinger

1. Åbn siden [forebyggelse af datatab](https://compliance.microsoft.com/datalossprevention?viewid=policies) , og vælg DLP-politikken, der er målrettet de lokale lagerplaceringer, du har konfigureret i AIP.
2. Rediger politikken.
3. På siden **Test eller slå politikken til skal** du vælge **Ja, slå den til med det samme**.

## <a name="see-also"></a>Se også

- [Få mere at vide om lokal DLP-scanner](dlp-on-premises-scanner-learn.md)
- [Kom i gang med en lokal DLP-scanner](dlp-on-premises-scanner-get-started.md)
- [Få mere at vide om forebyggelse af datatab](dlp-learn-about-dlp.md)
- [Opret, test og finjuster en DLP-politik](create-test-tune-dlp-policy.md)
- [Introduktion til Aktivitetsstifinder](data-classification-activity-explorer.md)
