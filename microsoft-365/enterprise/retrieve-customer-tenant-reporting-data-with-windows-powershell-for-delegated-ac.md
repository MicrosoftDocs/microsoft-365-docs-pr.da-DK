---
title: Hent rapporteringsdata for kundelejer med Windows PowerShell til DAP-partnere
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.assetid: 893e5275-30b3-433f-8ecd-644f78f513e2
description: 'Oversigt: Brug eksterne Windows PowerShell til Microsoft Exchange Online til at hente rapporter fra individuelle kundelejere.'
ms.openlocfilehash: 8529e95e8aefbd45cf381ff21bec49e669fd7c6a
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65096694"
---
# <a name="retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a>Hent rapporteringsdata for kundelejer med Windows PowerShell for DAP-partnere (Delegated Access Permissions)

*Denne artikel gælder både for Microsoft 365 Enterprise og Office 365 Enterprise.*

Brug eksterne Windows PowerShell til Microsoft Exchange Online til at hente rapporter fra individuelle kundelejere.

Syndikerings- og Cloud Solution Provider-partnere (CSP) kan få adgang til de data, der udgør kundelejerrapporter direkte via eksterne Windows PowerShell til Exchange Online PowerShell. Dette gør det muligt for partnere at indsamle og gemme rapporteringsdata og derefter udføre andre handlinger på dem. Når du har åbnet en fjernforbindelse, er hentning af rapporteringsdata om en kundelejer identisk med kørsel af en cmdlet i forhold til en kundeleje.

I denne artikel bruger du eksterne Windows PowerShell til Exchange Online til at oprette forbindelse til en enkelt kundelejer og hente en rapport. Som standard understøtter Windows PowerShell ikke sammenlægning af rapporteringsdata fra flere kundelejere. De rapporter, du henter med denne procedure, gælder kun for de  _DelegatedOrg_ , du opretter forbindelse til.

## <a name="before-you-begin"></a>Før du begynder

- Du skal oprette forbindelse til din Exchange Online lejer ved hjælp af eksterne Windows PowerShell. Du kan finde instruktioner [under Forbind til at Exchange Online lejere med eksterne Windows PowerShell til DAP-partnere (Delegated Access Permissions)](/powershell/exchange/connect-to-exchange-online-powershell)

## <a name="run-the-get-stalemailboxreport-sample"></a>Kør eksemplet på Get-StaleMailboxReport

Når du har åbnet en fjernsession for at Exchange Online, skal du køre denne kommando for at hente **Get-StaleMailboxReport** for datointervallet 25-03-2015 til 31-03-2015.

```powershell
Get-StaleMailboxReport -StartDate 03/25/2015 -EndDate 03/31/2015
```

Der er mange andre rapport-cmdlet'er tilgængelige til Exchange Online, Lync Online og SharePoint Online samt andre til meddelelsessporing, som du kan bruge. Du kan få mere at vide om de tilgængelige cmdlet'er til rapportering og Office 365 Reporting-webtjenesten i emnerne i følgende afsnit.

## <a name="see-also"></a>Se også

[Office 365 Reporting-webtjeneste](/previous-versions/office/developer/o365-enterprise-developers/jj984325(v=office.15))

[Rapporterings-cmdlet'er i Exchange Online](/powershell/module/exchange/get-csclientdevicedetailreport)

[Hjælp til partnere](https://go.microsoft.com/fwlink/p/?LinkID=533477)
