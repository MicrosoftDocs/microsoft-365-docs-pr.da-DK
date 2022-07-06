---
title: Identificer de tilgængelige PowerShell-cmdlet'er til opbevaring
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
ms.localizationpriority: normal
ms.collection:
- M365-security-compliance
- SPO_Content
- m365initiative-compliance
description: Identificer PowerShell-cmdlet'erne til opbevaring, der understøtter konfiguration i stor skala, automatisering eller kan være nødvendige til avancerede konfigurationsscenarier.
ms.openlocfilehash: 23dda0c7e5cdc2ce52c2dfca8e5ab575d5653b99
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66625979"
---
# <a name="powershell-cmdlets-for-retention-policies-and-retention-labels"></a>PowerShell-cmdlet'er til opbevaringspolitikker og opbevaringsmærkater

>*[Microsoft 365-licensvejledning til sikkerhed & overholdelse af angivne standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Brug følgende afsnit til at identificere de PowerShell-cmdlet'er, der er tilgængelige for opbevaringspolitikker og opbevaringsmærkater, som du muligvis skal bruge til konfiguration i stor skala, automatiserede scripts eller avancerede konfigurationsscenarier. Du kan se den komplette liste over cmdlet'er på [listen over opbevaring af politik og overholdelse af angivne standarder i PowerShell-dokumentationen](/powershell/module/exchange#policy-and-compliance-retention) .

Før du bruger disse cmdlet'er, skal du først [oprette forbindelse til Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell).

I de efterfølgende beskrivelser kan en politik for opbevaring referere til en opbevaringspolitik (ingen mærkater) eller en politik for opbevaringsmærkater. Hver politik definerer, om den er statisk eller adaptiv, og placeringerne for den politik, der skal anvendes. Politikken kræver derefter én regel for at fuldføre konfigurationen.

Eksempel:
- En opbevaringspolitik skal bruge en regel, der definerer opbevaringsindstillingerne, f.eks. bevar i fem år og derefter sletter.

Når du bruger opbevaringsmærkater, indeholder disse opbevaringsindstillinger, og deres politikker har brug for forskellige regler:
- En politik for opbevaringsmærkater, som du publicerer, skal bruge en regel, der definerer, hvilke mærkater der skal vises i apps.
- En politik for opbevaringsmærkat til automatisk anvendelse skal bruge en regel, der definerer den etiket, der skal anvendes, og betingelserne for anvendelse af mærkaten.

## <a name="retention-cmdlets-for-most-locations"></a>Opbevarings-cmdlet'er for de fleste placeringer

Brug cmdlet'erne i følgende tabel, når placeringerne er **Exchange-mail**, **SharePoint-websteder**, **OneDrive-konti**, **Microsoft 365-grupper**, **Skype for Business**, **offentlige Exchange-mapper**, **Teams-chatbeskeder** eller **Teams-kanalmeddelelser**.

Brug ikke disse cmdlet'er, når placeringerne er til private Teams-kanalmeddelelser, Yammer-brugermeddelelser eller Yammer-communitymeddelelser. Disse placeringer har alternative cmdlet'er, der identificeres i [næste afsnit](#retention-cmdlets-specific-to-teams-private-channels-and-yammer).

|Cmdlet|Beskrivelse|Relevante placeringer|
|:-----|:-----|:-----|:-----|
|[Enable-ComplianceTagStorage](/powershell/module/exchange/enable-compliancetagstorage) <br /><br /> [Get-ComplianceTagStorage](/powershell/module/exchange/enable-compliancetagstorage) |En engangshandling til oprettelse af lager eller visning af dette lager til opbevaringsmærkater |Exchange-mail <br /><br />SharePoint-websteder <br /><br /> OneDrive-konti <br /><br /> Microsoft 365-grupper|
|[Get-ComplianceTag](/powershell/module/exchange/get-compliancetag)<br /><br> [New-ComplianceTag](/powershell/module/exchange/new-compliancetag) <br /><br> [Remove-ComplianceTag](/powershell/module/exchange/remove-compliancetag) <br /><br> [Set-ComplianceTag](/powershell/module/exchange/set-compliancetag) |Få vist, opret, slet, konfigurer opbevaringsmærkater |Exchange-mail <br /><br /> SharePoint-websteder <br /><br /> OneDrive-konti<br /><br /> Microsoft 365-grupper|
|[Get-RecordReviewNotificationTemplateConfig](/powershell/module/exchange/get-recordreviewnotificationtemplateconfig) <br /><br /> [Set-RecordReviewNotificationTemplateConfig](/powershell/module/exchange/remove-retentioncompliancepolicy)  |Få vist eller konfigurer konfigurationen for dispositionsgennemgang af meddelelses- og påmindelsesindstillinger |Exchange-mail <br /><br /> SharePoint-websteder <br /><br /> OneDrive-konti <br /><br /> Microsoft 365-grupper|
|[Get-RetentionCompliancePolicy](/powershell/module/exchange/get-retentioncompliancepolicy) <br /><br /> [New-RetentionCompliancePolicy](/powershell/module/exchange/new-retentioncompliancepolicy) <br /><br /> [Remove-RetentionCompliancePolicy](/powershell/module/exchange/remove-retentioncompliancepolicy) <br /><br /> [Set-RetentionCompliancePolicy](/powershell/module/exchange/set-retentioncompliancepolicy) |Få vist, opret, slet, konfigurer politikker for opbevaring |Exchange-mail <br /><br /> SharePoint-websteder <br /><br /> OneDrive-konti<br /><br /> Microsoft 365-grupper <br /><br /> Skype for Business <br /><br /> Offentlige Exchange-mapper <br /><br /> Teams-chatbeskeder <br /><br /> Teams-kanalmeddelelser |
|[Get-RetentionComplianceRule](/powershell/module/exchange/get-retentioncompliancepolicy) <br /><br /> [Overholdelse af overholdelse af ny opbevaring](/powershell/module/exchange/get-retentioncompliancepolicy) <br /><br /> [Set-RetentionComplianceRule](/powershell/module/exchange/set-retentioncompliancerule) <br /><br /> [Remove-RetentionComplianceRule](/powershell/module/exchange/remove-retentioncompliancerule)  | Få vist, opret, konfigurer, slet indstillinger for politik for opbevarings- eller opbevaringsmærkater |Exchange-mail <br /><br /> SharePoint-websteder <br /><br /> OneDrive-konti <br /><br /> Microsoft 365-grupper <br /><br /> Skype for Business <br /><br /> Offentlige Exchange-mapper <br /><br /> Teams-chatbeskeder <br /><br /> Teams-kanalmeddelelser |

## <a name="retention-cmdlets-specific-to-teams-private-channels-and-yammer"></a>Opbevarings-cmdlet'er, der er specifikke for private Teams-kanaler og Yammer

Brug følgende cmdlet'er, når placeringerne er til **private Teams-kanalmeddelelser**, **Yammer-brugermeddelelser** eller **Yammer-communitymeddelelser**.

Når placeringerne er til Teams-chatmeddelelser, Teams-kanalmeddelelser, Exchange-mail, SharePoint-websteder, OneDrive-konti, Microsoft 365-grupper, Skype for Business eller offentlige Exchange-mapper, skal du bruge de cmdlet'er, der er angivet i det [forrige afsnit](#retention-cmdlets-for-most-locations).

|Cmdlet|Beskrivelse|Relevante placeringer|
|:-----|:-----|:-----|:-----|
|[Get-AppRetentionCompliancePolicy](/powershell/module/exchange/get-appretentioncompliancepolicy) <br /><br> [New-AppRetentionCompliancePolicy](/powershell/module/exchange/new-appretentioncompliancepolicy) <br /><br> [Remove-AppRetentionCompliancePolicy](/powershell/module/exchange/remove-appretentioncompliancepolicy) <br /><br> [Set-AppRetentionCompliancePolicy](/powershell/module/exchange/remove-appretentioncompliancepolicy) | Få vist, opret, slet, konfigurer opbevaringspolitikker |Teams-meddelelser om privat kanal <br /><br /> Yammer-brugermeddelelser <br /><br /> Yammer-communitymeddelelser|
|[Get-AppRetentionComplianceRule](/powershell/module/exchange/get-appretentioncompliancerule) <br /><br /> [New-AppRetentionComplianceRule](/powershell/module/exchange/new-appretentioncompliancerule) <br /><br /> [Remove-AppRetentionComplianceRule](/powershell/module/exchange/remove-appretentioncompliancerule) <br /><br /> [Set-AppRetentionComplianceRule](/powershell/module/exchange/remove-appretentioncompliancerule) | Få vist, opret, slet, konfigurer opbevaringsindstillinger for opbevaringspolitikker |Teams-meddelelser om privat kanal <br /><br /> Yammer-brugermeddelelser <br /><br /> Yammer-communitymeddelelser|

## <a name="configuration-guidance"></a>Konfigurationsvejledning

Brug de hjælpesider, der er knyttet til hver cmdlet, for at få detaljerede oplysninger og eksempler.

Hvis du vil have hjælp til at oprette og derefter publicere opbevaringsmærkater, skal du se [Opret og publicer opbevaringsmærkater ved hjælp af PowerShell](bulk-create-publish-labels-using-powershell.md).