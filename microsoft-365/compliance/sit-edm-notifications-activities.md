---
title: Opret meddelelser for aktiviteter, der stemmer overens med de nøjagtige data
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.date: ''
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Få mere at vide om, hvordan du opretter meddelelser om nøjagtige datamatchingaktiviteter.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: e5f7c2a2d724a66aea1ce55658ff84e6e0da4738
ms.sourcegitcommit: 39838c1a77d4e23df56af74059fb95970223f718
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/24/2022
ms.locfileid: "63591735"
---
# <a name="create-notifications-for-exact-data-match-activities"></a>Opret meddelelser for aktiviteter, der stemmer overens med de nøjagtige data

Når du opretter brugerdefinerede typer af følsomme oplysninger med et nøjagtigt [data match (EDM),](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types) oprettes der en række aktiviteter i [overvågningsloggen](search-the-audit-log-in-security-and-compliance.md#before-you-search-the-audit-log). Du kan bruge [New-ProtectionAlert](/powershell/module/exchange/new-protectionalert) PowerShell-cmdlet'en til at oprette meddelelser, der giver dig besked, når disse aktiviteter sker:

- CreateSchema
- EditSchema
- RemoveSchema
- UploadDataFailed
- UploadDataCompleted

> [!NOTE]
 Muligheden for at oprette meddelelser for EDM-aktiviteter er kun tilgængelig for GCC hele verden.

## <a name="pre-requisites"></a>Forudsætninger

Den konto, du bruger, skal være en af følgende:

- En global administrator
- Overholdelsesadministrator
- Exchange Online administrator

Du kan få mere at vide om DLP-tilladelser [under Tilladelser](data-loss-prevention-policies.md#permissions).

EDM-baseret klassificering er inkluderet i disse abonnementer:

- Office 365 E5
- Microsoft 365 E5
- Microsoft 365 E5 Overholdelse
- Microsoft E5/A5 Information Protection and Governance

Du kan få mere at vide om [DLP-licensering Microsoft 365 vejledning i licensering for & overholdelse af regler og standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection).

## <a name="configure-notifications-for-edm-activities"></a>Konfigurere meddelelser for EDM-aktiviteter

1. Forbind til [Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell).

2. `New-ProtectionAlert` Kør cmdlet'en ved hjælp af den aktivitet, du vil oprette en meddelelse for.  Hvis du f.eks. vil have besked, når handlingen **UploadDataCompleted** opstod, skal du køre:

    ```powershell
    New-ProtectionAlert -Name "EdmUploadCompleteAlertPolicy" -Category Others -NotifyUser <address to send notification to> -ThreatType Activity -Operation UploadDataCompleted -Description "Custom alert policy to track when EDM upload Completed" -AggregationType None
    ```
    
    For **UploadDataFailed kan** du køre:
    
    ```powershell
    New-ProtectionAlert -Name "EdmUploadFailAlertPolicy" -Category Others -NotifyUser <SMTP address to send notification to> -ThreatType Activity -Operation UploadDataFailed -Description "Custom alert policy to track when EDM upload Failed" -AggregationType None -Severity High
    ```

## <a name="related-articles"></a>Relaterede artikler

- [Få mere at vide om nøjagtige dataoverensstemmelsesbaserede typer af følsomme oplysninger](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)
- [New-ProtectionAlert](/powershell/module/exchange/new-protectionalert)