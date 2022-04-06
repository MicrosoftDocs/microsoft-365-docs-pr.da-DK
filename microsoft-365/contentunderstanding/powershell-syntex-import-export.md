---
title: Eksportér og importér dokumentforståelsesmodeller med PowerShell
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
description: Få mere at vide om, hvordan du eksporterer og importerer dokumentforståelsesmodeller med PowerShell SharePoint Syntex.
ms.openlocfilehash: dc35d298ebd79752684c91ce944333277fcef621
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/17/2022
ms.locfileid: "63606821"
---
# <a name="export-and-import-document-understanding-models-with-powershell"></a>Eksportér og importér dokumentforståelsesmodeller med PowerShell

> [!IMPORTANT]
> The SharePoint Syntex PowerShell cmdlets and all other PnP components are open source tools backed by an active community providing support for them. Der er ingen SLA for understøttelse af open source-værktøjer fra officielle Microsoft-supportkanaler.

SharePoint Syntex modeller kan eksporteres som PnP-skabeloner, så du kan genbruge på tværs af indholdscentre eller lejere.

## <a name="export-all-models-in-a-content-center"></a>Eksportér alle modeller i et indholdscenter

Hvis du vil eksportere alle modeller i et indholdscenter til en enkelt PnP-skabelon, skal du bruge følgende [PnP](https://pnp.github.io/powershell/) PowerShell-cmdlet'er:

```powershell
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/yourContentCenter"

Get-PnPSiteTemplate -Out MyModels.pnp -Handlers SyntexModels
```

## <a name="export-specific-models"></a>Eksportér bestemte modeller

Hvis du vil eksportere bestemte modeller fra et indholdscenter til en PnP-skabelon, skal du bruge følgende [PnP](https://pnp.github.io/powershell/) PowerShell-cmdlet'er:

```powershell
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/yourContentCenter"

Get-PnPSiteTemplate -Out MyModels.pnp -Configuration .\extract.json
```

Extract.json definerer, hvilke modeller du vil eksportere, så du kan angive modellen efter navn eller id og eventuelt konfigurere for ikke at udtrække kursusdata.

### <a name="example---specify-model-by-name"></a>Eksempel – Angiv model efter navn

```json
{
    "$schema": "https://developer.microsoft.com/en-us/json-schemas/pnp/provisioning/202102/extract-configuration.schema.json",
    "persistAssetFiles": true,
    "handlers": [        
        "SyntexModels"
    ],
    "syntexModels": {
        "models": [
            {
                "name": "Sample - benefits change notice.classifier"
            }
        ]
    }
}
```

### <a name="example---specify-model-by-id"></a>Eksempel – Angiv model efter id

```json
{
    "$schema": "https://developer.microsoft.com/en-us/json-schemas/pnp/provisioning/202102/extract-configuration.schema.json",
    "persistAssetFiles": true,
    "handlers": [        
        "SyntexModels"
    ],
    "syntexModels": {
        "models": [
            {
                "id": 3,
                "excludeTrainingData": true
            }
        ]
    }
}
```

Hvis du ikke medtager egenskaben "includeTrainingData", er standardfunktionsmåden at medtage.

> [!NOTE]
> Kursusdata er påkrævet, for at en model kan redigeres, når den importeres til et destinationsindholdscenter.

## <a name="import-models-to-a-content-center"></a>Importér modeller til et indholdscenter
Dokumentforståelse af modeller, der er eksporteret til PnP-skabeloner, kan importeres til et indholdscenter på en hvilken som helst lejer. Hvis eksporten indeholder kursusdata, kan modellen redigeres, når den er importeret.

Hvis du vil importere en model, skal du bruge følgende kommandoer:

```PowerShell
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/yourContentCenter"

Invoke-PnPSiteTemplate -Path .\sampleModel.pnp
```
