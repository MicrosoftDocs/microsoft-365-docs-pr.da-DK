---
title: Brug scanner til forebyggelse af datatab i det lokale miljø
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
description: Få mere at vide om, hvordan du bruger forebyggelse af datatab i det lokale miljø til at scanne inaktive data og implementere beskyttende handlinger for filshares i det lokale miljø og SharePoint-mapper og dokumentbiblioteker i det lokale miljø.
ms.openlocfilehash: ae5ffce9e664ada6e7476bb02b40f4a5c279d441
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66624173"
---
# <a name="use-the-data-loss-prevention-on-premises-scanner"></a>Brug scanneren til forebyggelse af datatab i det lokale miljø

For at gøre dig fortrolig med Microsoft Purview Forebyggelse af datatab funktioner i det lokale miljø, og hvordan de dukker op i DLP-politikker, har vi sammensat nogle scenarier, som du kan følge.

> [!IMPORTANT]
> Disse DLP-scenarier i det lokale miljø er ikke de officielle procedurer for oprettelse og justering af DLP-politikker. Se nedenstående emner, når du har brug for at arbejde med DLP-politikker i generelle situationer:
>
> - [Få mere at vide om forebyggelse af datatab](dlp-learn-about-dlp.md)
> - [Kom i gang med DLP-standardpolitikken](get-started-with-the-default-dlp-policy.md)
> - [Opret en DLP-politik ud fra en skabelon](create-a-dlp-policy-from-a-template.md)
> - [Opret, test og finjuster en DLP-politik](create-test-tune-dlp-policy.md)

### <a name="scenario-discover-files-matching-dlp-rules"></a>Scenarie: Find filer, der stemmer overens med DLP-regler

Data fra DLP-scanneroverflader i det lokale miljø på flere områder

#### <a name="activity-explorer"></a>Aktivitetsoversigt

 Microsoft DLP til det lokale miljø registrerer DLP-regelforekomster og rapporterer dem til [Aktivitetsoversigt](https://compliance.microsoft.com/dataclassification?viewid=activitiesexplorer).

#### <a name="microsoft-365-audit-log"></a>Microsoft 365-overvågningslog

DLP-regelforekomsterne er tilgængelige i brugergrænsefladen i overvågningsloggen. [Se Søg i overvågningsloggen i Microsoft Purview-compliance-portal](search-the-audit-log-in-security-and-compliance.md) eller tilgængelig via [Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog) PowerShell.

#### <a name="aip"></a>AIP

Registreringsdata er tilgængelige i en lokal rapport i csv-format, som er gemt under:

**%localappdata%\Microsoft\MSIP\Scanner\Reports\DetailedReport_%timestamp%.csv rapport**.

 Søg efter følgende kolonner:

- DLP-tilstand
- DLP-status
- DLP-kommentar
- Navn på DLP-regel
- DLP-handlinger
- Ejer
- Aktuelle NTFS-tilladelser (SDDL)
- Anvendte NTFS-tilladelser (SDDL)
- NTFS-tilladelsestype

### <a name="scenario-enforce-dlp-rule"></a>Scenarie: Gennemtving DLP-regel

Hvis du vil gennemtvinge DLP-regler for de scannede filer, skal gennemtvingelse være aktiveret for både indholdsscanningsjobbet i AIP og på politikniveau i DLP.

#### <a name="configure-dlp-to-enforce-policy-actions"></a>Konfigurer DLP til at gennemtvinge politikhandlinger

1. Åbn [siden Forebyggelse af datatab](https://compliance.microsoft.com/datalossprevention?viewid=policies) , og vælg den DLP-politik, der er målrettet til de lokale placeringslagre, du har konfigureret i AIP.
2. Rediger politikken.
3. På siden **Test eller slå politik** til skal du vælge **Ja, slå den til med det samme**.

## <a name="see-also"></a>Se også

- [Få mere at vide om DLP-scanner i det lokale miljø](dlp-on-premises-scanner-learn.md)
- [Kom i gang med DLP-scanner i det lokale miljø](dlp-on-premises-scanner-get-started.md)
- [Få mere at vide om forebyggelse af datatab](dlp-learn-about-dlp.md)
- [Opret, test og finjuster en DLP-politik](create-test-tune-dlp-policy.md)
- [Kom i gang med Aktivitetsoversigt](data-classification-activity-explorer.md)
