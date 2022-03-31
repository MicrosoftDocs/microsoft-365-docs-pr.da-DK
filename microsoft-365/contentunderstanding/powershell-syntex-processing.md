---
title: Brug PowerShell til at anmode om behandling af en dokumentforståelsesmodel
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
description: Få mere at vide om, hvordan du bruger PowerShell til at anmode om behandling af SharePoint Syntex dokumentforståelsesmodel.
ms.openlocfilehash: 8f66a0cc5e59ad2ccb6b92d98cfaee8ce84470f2
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/17/2022
ms.locfileid: "63601073"
---
# <a name="use-powershell-to-request-processing-by-a-document-understanding-model"></a>Brug PowerShell til at anmode om behandling af en dokumentforståelsesmodel

> [!IMPORTANT]
> The SharePoint Syntex PowerShell cmdlets and all other PnP components are open source tools backed by an active community providing support for them. Der er ingen SLA for understøttelse af open source-værktøjer fra officielle Microsoft-supportkanaler.

Dokumentforståelsesmodeller behandler nyligt overførte filer til et bibliotek. Det er også muligt manuelt at anmode om behandling i brugergrænsefladen. Der kan dog være scenarier, hvor det er mere effektivt at udløse behandlingen via PowerShell.

## <a name="request-processing-of-all-items-that-have-not-been-previously-classified"></a>Anmod om behandling af alle elementer, der ikke tidligere er blevet klassificeret

Du kan anmode om behandling af alle elementer i biblioteket, der ikke tidligere er blevet klassificeret ved hjælp af denne kommando:

```PowerShell
#Note: you're connecting here to the site that holds the document library you want to process
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/finance"

Request-PnPSyntexClassifyAndExtract -List "Documents"
```

Til behandling med lavere prioritet kan du også overveje at bruge parameteren -OffPeak, som sætter filer i kø til behandling uden for arbejdstiden, hvor din lejer er placeret. Se [Request-PnPSyntexClassifyAndExtract for at](https://pnp.github.io/powershell/cmdlets/Request-PnPSyntexClassifyAndExtract.html) få flere oplysninger.

## <a name="request-processing-of-all-items-in-a-library"></a>Anmod om behandling af alle elementer i et bibliotek

Du kan anmode om behandling af alle filer i biblioteket, også selvom de tidligere er blevet klassificeret. Dette kan være nyttigt, hvis du har opdateret en model eller føjet en anden model til biblioteket.

```PowerShell
#Note: you're connecting here to the site that holds the document library you want to process
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/finance"

Request-PnPSyntexClassifyAndExtract -List "Documents" -Force
```

> [!NOTE]
> Hvis du bruger indstillingen -Gennemtving med mere end 5.000 elementer, aktiveres automatisk behandling uden spidsbelastning.

## <a name="request-processing-of-all-items-based-on-a-property"></a>Anmod om behandling af alle elementer baseret på en egenskab

Hvis du vil begrænse behandlingen til et bestemt undersæt af elementer i et bibliotek, kan du bruge et script til at vælge en bestemt gruppe af filer. I følgende eksempel gør scriptet det muligt at markere et felt og at filtrere efter en feltværdi. Mere komplekse forespørgsler kan gennemføres ved hjælp [af Get-PnPListItem](https://pnp.github.io/powershell/cmdlets/Get-PnPListItem.html).

```PowerShell
#Note: you're connecting here to the site that holds the document library you want to process
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/finance"
$list = Get-PnPList -Identity "Documents"
# Set the field name to filter items by
$fieldName = "Vendor"
# Set the field value to filter by
$fieldFilter = "Fabrikam"

$listItems = (Get-PnPListItem -List $list -fields $fieldName).fieldValues
$targetItems = $listItems | Where-Object -Property Provider -EQ -Value $fieldFilter

# Create a new batch
$batch = New-PnPBatch

# Add files to classify to the batch
foreach ($listItem in $targetItems) {
    Request-PnPSyntexClassifyAndExtract -FileUrl $listItem.FileRef -Batch $classifyBatch
}

# Execute batch
Invoke-PnPBatch -Batch $batch
```

## <a name="request-processing-of-specific-files"></a>Anmod om behandling af bestemte filer

Der kan også anmodes om behandling af bestemte filer.

```PowerShell
#Note: you're connecting here to the site that holds the document library you want to process
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/finance"

Request-PnPSyntexClassifyAndExtract -FileUrl "/sites/finance/documents/contoso contract.docx"
```

Fil efter fil-model understøtter også batching:

```PowerShell
#Note: you're connecting here to the site that holds the document library you want to process
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/finance"

# Create a new batch
$batch = New-PnPBatch

# Add files to classify to the batch
Request-PnPSyntexClassifyAndExtract -FileUrl "/sites/finance/documents/contoso contract.docx" -Batch $batch
Request-PnPSyntexClassifyAndExtract -FileUrl "/sites/finance/documents/relecloud contract.docx" -Batch $batch

# Execute batch
Invoke-PnPBatch -Batch $batch
```
