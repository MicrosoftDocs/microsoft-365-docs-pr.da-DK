---
title: Administrer adgang til Microsoft Whiteboard for GCC High-miljøer
ms.author: chucked
author: chuckedmonson
manager: alexfaulkner
ms.reviewer: ''
audience: admin
ms.topic: article
ms.custom: ''
ms.prod: microsoft-365-enterprise
search.appverid: MET150
ms.collection: ''
ms.localizationpriority: medium
description: Få mere at vide om, hvordan du aktiverer, deaktiverer og administrerer Whiteboard-data.
ROBOTS: NOINDEX, NOFOLLOW
ms.openlocfilehash: 3521d1cb7bafcb5f863f3902d2f54f96a30975cd
ms.sourcegitcommit: bc35c7826e3403f259725ac72cca5bafd36aa56a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/30/2022
ms.locfileid: "66858900"
---
# <a name="manage-access-to-microsoft-whiteboard-for-gcc-high-environments"></a>Administrer adgang til Microsoft Whiteboard for GCC High-miljøer

>[!NOTE]
> Denne vejledning gælder for GCC High-miljøer (US Government Community Cloud).

Microsoft Whiteboard på OneDrive for Business er som standard aktiveret for relevante Microsoft 365-lejere. Den kan aktiveres eller deaktiveres på lejerniveau. Du skal også sikre, at **Microsoft Whiteboard Services** er aktiveret i **Azure Active Directory Administration** > **Enterprise-programmer**.

Følgende URL-adresser er påkrævet:

- 'https://*.office365.us/'
- 'https://login.microsoftonline.us/'
- 'https://graph.microsoft.us/'
- 'https://graph.microsoftazure.us/'
- 'https://admin.onedrive.us'
- 'https://shell.cdn.office.net/'
- 'https://config.ecs.gov.teams.microsoft.us'
- 'https://tb.events.data.microsoft.com/'

Du kan styre adgangen til Whiteboard på følgende måder:

- Aktivér eller deaktiver Whiteboard for hele lejeren ved hjælp af [SharePoint Online PowerShell-modulet](/microsoft-365/enterprise/manage-sharepoint-online-with-microsoft-365-powershell).

- Vis eller skjul whiteboard for bestemte brugere i møder ved hjælp af en Teams-mødepolitik. Den vil stadig være synlig via internettet, oprindelige klienter og teams-faneappen.

- Kræv politikker for betinget adgang for at få adgang til Whiteboard ved hjælp af Azure Active Directory Administration.

>[!NOTE]
> Whiteboard på OneDrive for Business vises ikke i Microsoft 365 Administration. Teams-mødepolitik skjuler kun whiteboard-indgangspunkter. Den forhindrer ikke brugerne i at bruge Whiteboard. Betinget adgang forhindrer adgang til Whiteboard, men skjuler ikke indgangspunkterne.

## <a name="enable-or-disable-whiteboard"></a>Aktivér eller deaktiver Whiteboard

Benyt følgende fremgangsmåde for at aktivere eller deaktivere Whiteboard for din lejer: 

1. Brug [SharePoint Online PowerShell-modulet](/microsoft-365/enterprise/manage-sharepoint-online-with-microsoft-365-powershell) til at aktivere eller deaktivere alle Fluid Experiences på tværs af din Microsoft 365-lejer.

2. Opret forbindelse til [SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online).

3. Aktivér væske ved hjælp af følgende <code>Set-SPOTenant</code> cmdlet:

   <pre><code class="lang-powershell">Set-SPOTenant -IsWBFluidEnabled $true</code></pre>

Ændringen bør tage ca. 60 minutter at anvende på tværs af din leje. Hvis du ikke kan se denne indstilling, skal du opdatere modulet.

>[!NOTE]
> Whiteboard er som standard aktiveret. Hvis den er blevet deaktiveret i Azure Active Directory-virksomhedsprogrammer, fungerer Whiteboard på OneDrive for Business ikke.

## <a name="show-or-hide-whiteboard"></a>Vis eller skjul whiteboard

Hvis du vil vise eller skjule Whiteboard i møder, skal du se [Indstillinger for mødepolitik](/microsoftteams/meeting-policies-content-sharing).

## <a name="see-also"></a>Se også

[Administrer data for Whiteboard – GCC High](manage-data-gcc-high.md)

[Administrer deling for Whiteboard – GCC High](manage-sharing-gcc-high.md)

[Administrer klienter for Whiteboard – GCC High](manage-clients-gcc-high.md)




