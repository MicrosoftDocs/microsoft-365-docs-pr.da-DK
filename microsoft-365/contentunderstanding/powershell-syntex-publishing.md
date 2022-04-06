---
title: Publicer dokumentforståelsesmodeller med PowerShell
ms.author: jaeccles
author: jameseccles
ms.reviewer: ssquires
manager: serdars
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.collection:
- enabler-strategic
- m365initiative-syntex
search.appverid: MET150
ms.localizationpriority: medium
description: Få mere at vide om, hvordan du SharePoint Syntex et dokument om modeller med PowerShell.
ms.openlocfilehash: 5169e5ea5839cd5c341baa2477fd82281f5e5d76
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/17/2022
ms.locfileid: "63606819"
---
# <a name="publish-document-understanding-models-with-powershell"></a>Publicer dokumentforståelsesmodeller med PowerShell

> [!IMPORTANT]
> The SharePoint Syntex PowerShell cmdlets and all other PnP components are open source tools backed by an active community providing support for them. Der er ingen SLA for understøttelse af open source-værktøjer fra officielle Microsoft-supportkanaler.

SharePoint Syntex-modeller installeres typisk i dokumentbiblioteker på tværs af din lejer. Dette kan gøres ved hjælp af webstedet for indholdscenter, men det kan også gøres ved hjælp [af PnP PowerShell](https://pnp.github.io/powershell/) som beskrevet i denne artikel.

## <a name="listing-the-available-models-in-a-content-center"></a>Liste over tilgængelige modeller i et indholdscenter

For at få et overblik over de modeller, der er føjet til det aktuelle SharePoint Syntex indholdscenterwebsted, skal du bruge [Get-PnPSyntexModel-cmdlet'en](https://pnp.github.io/powershell/cmdlets/Get-PnPSyntexModel.html):

```PowerShell
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/yourContentCenter"
Get-PnPSyntexModel
```

## <a name="apply-a-model-to-a-library"></a>Anvend en model på et bibliotek

Hvis du vil anvende en model på et bibliotek, skal du [bruge cmdlet'en Publish-PnPSyntexModel](https://pnp.github.io/powershell/cmdlets/Publish-PnPSyntexModel.html) :

```PowerShell
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/yourContentCenter"
Publish-PnPSyntexModel -Model "Contract Notice" -ListWebUrl "https://contoso.sharepoint.com/sites/finance" -List "Documents"
```

## <a name="understanding-where-a-model-is-used"></a>Forstå, hvor en model bruges

Når du har installeret en model til mange biblioteker, kan det være en god ide at gennemgå listen over biblioteker, der bruger modellen. Dette kan gøres ved hjælp af [Cmdlet'en Get-PnPSyntexModelPublication](https://pnp.github.io/powershell/cmdlets/Get-PnPSyntexModelPublication.html) :

```PowerShell
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/yourContentCenter"
Get-PnPSyntexModelPublication -Identity "Contract Notice"
```

## <a name="removing-a-model-from-a-library"></a>Fjerne en model fra et bibliotek

Når du fjerner en model fra et bibliotek, følger det samme mønster som at anvende og kan udføres ved hjælp af [cmdlet'en Unpublish-PnPSyntexModel](https://pnp.github.io/powershell/cmdlets/Unpublish-PnPSyntexModel.html) enten interaktivt eller som en batch af flere handlinger.

```PowerShell
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/yourSite"
Unpublish-PnPSyntexModel -Model "Invoice model" -ListWebUrl "https://contoso.sharepoint.com/sites/finance" -List "Documents"
```

## <a name="apply-models-in-bulk"></a>Anvend flere modeller flere

Hvis du vil publicere flere modeller i flere biblioteker, skal du oprette en INPUT CSV-fil med modellerne og målplaceringerne:

```CSV
ModelName,TargetSiteUrl,TargetWebServerRelativeUrl,TargetLibraryServerRelativeUrl
Contract Notice,https://contoso.sharepoint.com/sites/Site1,/sites/Site1,/sites/site1/shared%20documents
Contract Notice,https://contoso.sharepoint.com/sites/Site1,/sites/Site1,/sites/site1/other
Trade Confirmation,https://contoso.sharepoint.com/sites/Site2,/sites/Site2,/sites/site2/shared%20documents
```

Denne CSV-fil kan derefter bruges som input til et script, der publicerer de angivne modeller til de relevante biblioteker. I følgende eksempel bruges batching til at øge effektiviteten af anmodningerne.

```PowerShell
$contentCenterURL = "https://contoso.sharepoint.com/sites/yourSite"
$targetsCSV = "./Publish-SyntexModelBulk.csv"

Connect-PnPOnline -url $contentCenterURL

$targetLibraries = Import-Csv -Path $targetsCSV

$batch = New-PnPBatch

foreach ($target in $targetLibraries) {
    Publish-PnPSyntexModel -Model $target.ModelName -TargetSiteUrl $target.TargetSiteUrl -TargetWebServerRelativeUrl $target.TargetWebServerRelativeUrl -TargetLibraryServerRelativeUrl $target.TargetLibraryServerRelativeUrl -Batch $batch
}

Invoke-PnPBatch -Batch $batch
```
