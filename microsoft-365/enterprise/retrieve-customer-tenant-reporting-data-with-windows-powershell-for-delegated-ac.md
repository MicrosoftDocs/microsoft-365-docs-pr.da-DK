---
title: Hent rapporteringsdata om kundelejer med Windows PowerShell for DAP-partnere
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: 'Oversigt: Brug eksterne Windows PowerShell til Microsoft Exchange Online at hente rapporter fra individuelle kundelejere.'
ms.openlocfilehash: cc9046ab5c90dcb40cbf012772fd80b56f71ec79
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63594214"
---
# <a name="retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a>Hent rapporteringsdata om kundelejer med Windows PowerShell for DAP-partnere (Delegated Access Permissions)

*Denne artikel gælder for både Microsoft 365 Enterprise og Office 365 Enterprise.*

Brug eksterne Windows PowerShell til Microsoft Exchange Online at hente rapporter fra individuelle kundelejere.

Syndication and Cloud Solution Provider-partnere (CSP) kan få adgang til de data, der udgør kundelejerrapporter direkte via Windows PowerShell til Exchange Online PowerShell. Det gør det muligt for partnere at indsamle og gemme rapporteringsdataene og derefter udføre andre handlinger på dem. Når du åbner en fjernforbindelse, er det identisk at hente rapporteringsdata om et kundelejer ved at køre en cmdlet mod en kundelejer.

I denne artikel bruger du ekstern Windows PowerShell til Exchange Online at oprette forbindelse til en enkelt kundes leje og hente en rapport. Som standard Windows PowerShell ikke sammenlægning af rapporteringsdata fra flere kunder. De rapporter, du henter med denne procedure, er kun for  _den DelegatedOrg_ , du opretter forbindelse til.

## <a name="before-you-begin"></a>Før du begynder

- Du skal oprette forbindelse til din Exchange Online lejer ved hjælp af Windows PowerShell. Du kan finde en [vejledning Forbind Exchange Online lejere med eksterne Windows PowerShell for DAP-partnere (Delegated Access Permissions)](/powershell/exchange/connect-to-exchange-online-powershell)

## <a name="run-the-get-stalemailboxreport-sample"></a>Kør Get-StaleMailboxReport eksempel

Når du har åbnet en fjernsession til Exchange Online, skal du køre denne kommando for at hente **Get-StaleMailboxReport** for datointervallet 25-03-2015 til og med 31-03-2015.

```powershell
Get-StaleMailboxReport -StartDate 03/25/2015 -EndDate 03/31/2015
```

Der findes mange andre rapporteringscmdlet'er til Exchange Online, Lync Online og SharePoint Online samt andre til meddelelsessporing, som du kan bruge. Hvis du vil vide mere om de tilgængelige rapporterings-cmdlet'er og Office 365 Reporting-webtjenesten, skal du se emnerne i det følgende afsnit.

## <a name="see-also"></a>Se også

[Office 365 Reporting-webtjeneste](/previous-versions/office/developer/o365-enterprise-developers/jj984325(v=office.15))

[Rapportering af cmdlet'er i Exchange Online](/powershell/module/exchange/get-csclientdevicedetailreport)

[Hjælp til partnere](https://go.microsoft.com/fwlink/p/?LinkID=533477)
