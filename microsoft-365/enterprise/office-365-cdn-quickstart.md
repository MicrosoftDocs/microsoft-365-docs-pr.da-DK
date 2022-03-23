---
title: Office 365 Content Delivery Network (CDN) Hurtig start
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 01/13/2022
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- SPO_Content
- m365initiative-coredeploy
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
description: Office 365 Content Delivery Network (CDN) Hurtig start
ms.openlocfilehash: b0684fdfd8583ae6780cb23d47dc697582ae133b
ms.sourcegitcommit: af73b93a904ce8604be319e8dc7cadaf65d50534
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/31/2022
ms.locfileid: "63591623"
---
# <a name="office-365-content-delivery-network-cdn-quickstart"></a>Office 365 Content Delivery Network (CDN) Hurtig start

Du kan bruge den indbyggede **Office 365 Content Delivery Network (CDN)** til at hoste statiske aktiver (billeder, JavaScript, Stylesheets, WOFF-filer) for at levere bedre ydeevne for dine SharePoint Online-sider. Overførselsvinduet Office 365 CDN ydeevnen ved at cache statiske aktiver tættere på browserne, der anmoder om dem, hvilket hjælper dig med at sætte fart på overførsler og reducere ventetiden. Derudover bruger Office 365 CDN HTTP/2-protokollen til forbedret komprimering og HTTP-pipelining. Tjenesten Office 365 CDN inkluderet som en del af dit SharePoint Online-abonnement.

Du kan finde en mere detaljeret [vejledning under Brug Office 365 Content Delivery Network (CDN) med SharePoint Online](use-microsoft-365-cdn-with-spo.md).

>[!NOTE]
>Lejerne Office 365 CDN kun tilgængelige for lejere i produktionsskyen (hele verden). Lejere i den amerikanske stat, Kina og Tysklands skyer understøtter i øjeblikket ikke Office 365 CDN.

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-identify-items-not-in-cdn"></a>Brug Værktøjet Sidediagnosticering til SharePoint til at identificere elementer, der ikke er CDN

Du kan bruge **Sidediagnosticering til browserudvidelsen SharePoint-værktøjet** til nemt at opliste aktiver på dine SharePoint Online-sider, der kan føjes til en CDN oprindelse.

**Sidediagnosticering til værktøjet SharePoint** er en browserudvidelse til de nye Microsoft Edge (<https://www.microsoft.com/edge>) og Chrome-browsere, der analyserer både SharePoint Online moderne portal og klassiske publiceringswebstedssider. Værktøjet indeholder en rapport for hver analyseret side, der viser, hvordan siden fungerer i forhold til et defineret sæt kriterier for ydeevne. Hvis du vil installere og få mere at vide om værktøjet Sidediagnosticering til SharePoint, skal du gå til Brug værktøjet [Sidediagnosticering til SharePoint Online](./page-diagnostics-for-spo.md).

Når du kører værktøjet Sidediagnosticering til SharePoint på en SharePoint Online-side, kan du klikke på fanen **Diagnosticeringstest** for at få vist en liste over aktiver, der ikke er hostet af CDN. Disse aktiver vil være angivet under overskriften **Content Delivery Network (CDN) som** vist på skærmbilledet nedenfor.

![Sidediagnosticering.](../media/page-diagnostics-for-spo/pagediag-results-general.PNG)

>[!NOTE]
>Værktøjet Sidediagnosticering fungerer kun for SharePoint Online og kan ikke bruges på en SharePoint systemside.

## <a name="cdn-overview"></a>CDN oversigt

The Office 365 CDN er udviklet til at optimere ydeevnen for brugere ved at distribuere ofte tilgåede objekter som f.eks. billeder og JavaScript-filer via et hurtigt globalt netværk, reducere sideindlæsningstiden og give adgang til hostede objekter så tæt som muligt på brugeren. Den CDN henter aktiverne fra en placering, der kaldes en _oprindelse_. En oprindelse kan være et SharePoint, et dokumentbibliotek eller en mappe, der er tilgængelig via en URL-adresse.

The Office 365 CDN er opdelt i to grundlæggende typer:

- **Offentlige CDN** er designet til at blive brugt til JS (JavaScript), CSS (StyleSheets), WOFF (Web Font File, WOFF2) og ikke-beskyttede billeder som f.eks. firmalogoer.
- **Private CDN** er designet til at blive brugt til billeder (PNG, JPG, JPEG osv.).

Du kan vælge at have både offentlige eller private oprindelser for din organisation. De fleste organisationer vælger at implementere en kombination af de to. Både offentlige og private muligheder giver lignende ydeevnefordele, men de har hver unikke attributter og fordele. Du kan finde flere oplysninger om offentlige og CDN oprindelser i Vælg, [om hver oprindelse skal være offentlig eller privat](use-microsoft-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate).

## <a name="how-to-enable-public-and-private-cdn-with-the-default-configuration"></a>Sådan aktiverer du offentlig og privat CDN med standardkonfigurationen
Før du foretager ændringer i lejerindstillingerne CDN, skal du kontrollere, at de overholder din organisations politikker for overholdelse, sikkerhed og beskyttelse af personlige oplysninger.

Hvis du vil have mere detaljerede konfigurationsindstillinger, eller hvis du allerede har aktiveret CDN og vil tilføje flere placeringer (oprindelser), skal du se afsnittet Konfigurere og konfigurere Office 365 CDN ved hjælp af [SharePoint Online Management Shell](use-microsoft-365-cdn-with-spo.md#set-up-and-configure-the-office-365-cdn-by-using-the-sharepoint-online-management-shell)

Forbind til din lejer ved hjælp af SharePoint Online Management Shell:

```PowerShell
Connect-SPOService -Url https://<YourTenantName>-admin.sharepoint.com
```

Hvis du vil aktivere din organisations adgang til at bruge både offentlige og private oprindelser med standardkonfigurationen, skal du indtaste følgende kommando:

```PowerShell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true
```

Output fra disse cmdlet'er bør se ud som følgende:

![Output fra Set-SPOTenantCdnEnabled.](../media/O365-CDN/o365-cdn-enable-output.png)

## <a name="see-also"></a>Se også

[Brug værktøjet Sidediagnosticering til SharePoint Online](./page-diagnostics-for-spo.md)

[Brug Office 365 Content Delivery Network (CDN) med SharePoint Online](use-microsoft-365-cdn-with-spo.md)

[Content Delivery Networks](./content-delivery-networks.md)

[Netværksplanlægning og justering af ydeevnen for Office 365](./network-planning-and-performance.md)

[SharePoint Ydeevneserie – Office 365 CDN videoserie](https://www.youtube.com/playlist?list=PLR9nK3mnD-OWMfr1BA9mr5oCw2aJXw4WA)
