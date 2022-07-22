---
title: Opret meddelelser for aktiviteter med nøjagtigt datamatch
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
description: Få mere at vide om, hvordan du opretter meddelelser om aktiviteter, der matcher præcise data.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 09bb41de09b6f44a9f556446c5a566322b44ad0d
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/21/2022
ms.locfileid: "66949123"
---
# <a name="create-notifications-for-exact-data-match-activities"></a>Opret meddelelser for aktiviteter med nøjagtigt datamatch

Når du [opretter brugerdefinerede følsomme oplysningstyper med nøjagtigt datamatch (EDM),](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types) er der en række aktiviteter, der oprettes i [overvågningsloggen](search-the-audit-log-in-security-and-compliance.md#before-you-search-the-audit-log). Du kan bruge [PowerShell-cmdlet'en New-ProtectionAlert](/powershell/module/exchange/new-protectionalert) til at oprette meddelelser, der giver dig besked, når disse aktiviteter finder sted:

- `CreateSchema`
- `EditSchema`
- `RemoveSchema`
- `UploadDataFailed`
- `UploadDataCompleted`

> [!NOTE]
 Muligheden for at oprette meddelelser for EDM-aktiviteter er kun tilgængelig for world wide- og GCC-cloudmiljøer.

## <a name="pre-requisites"></a>Forudsætninger

Den konto, du bruger, skal være en af følgende:

- En global administrator
- Overholdelsesadministrator
- Exchange Online administrator

Du kan få mere at vide om DLP-tilladelser under [Tilladelser](data-loss-prevention-policies.md#permissions).

EDM-baseret klassificering er inkluderet i disse abonnementer:

- Office 365 E5
- Microsoft 365 E5
- Microsoft 365 E5 Overholdelse
- Microsoft E5/A5 Information Protection og styring

Du kan få mere at vide om DLP-licenser under [Vejledning til Microsoft 365-licenser om sikkerhed & overholdelse af angivne standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection).

## <a name="configure-notifications-for-edm-activities"></a>Konfigurer meddelelser for EDM-aktiviteter

1. Opret forbindelse til [PowerShell til sikkerhed & overholdelse af angivne standarder](/powershell/exchange/connect-to-scc-powershell).

2. Kør cmdlet'en `New-ProtectionAlert` ved hjælp af den aktivitet, du vil oprette meddelelsen for.  Hvis du f.eks. vil have besked, når `UploadDataCompleted` handlingen fandt sted, skal du køre:

    ```powershell
    New-ProtectionAlert -Name "EdmUploadCompleteAlertPolicy" -Category Others -NotifyUser <address to send notification to> -ThreatType Activity -Operation UploadDataCompleted -Description "Custom alert policy to track when EDM upload Completed" -AggregationType None
    ```
    
    For kan `UploadDataFailed` du køre:
    
    ```powershell
    New-ProtectionAlert -Name "EdmUploadFailAlertPolicy" -Category Others -NotifyUser <SMTP address to send notification to> -ThreatType Activity -Operation UploadDataFailed -Description "Custom alert policy to track when EDM upload Failed" -AggregationType None -Severity High
    ```

## <a name="related-articles"></a>Relaterede artikler

- [Få mere at vide om nøjagtigt datamatch baseret på typer af følsomme oplysninger](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)
- [Ny beskyttelseAlert](/powershell/module/exchange/new-protectionalert)
