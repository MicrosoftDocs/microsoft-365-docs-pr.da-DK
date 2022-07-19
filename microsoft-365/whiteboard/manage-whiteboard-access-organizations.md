---
title: Administrer adgang til Microsoft Whiteboard for din organisation
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
description: Få mere at vide om, hvordan du konfigurerer Microsoft Whiteboard til din organisation i Microsoft 365 Administration.
ROBOTS: NOINDEX, NOFOLLOW
ms.openlocfilehash: 1de0cd66a817a3db50b98bf6895be20184c974fc
ms.sourcegitcommit: bc35c7826e3403f259725ac72cca5bafd36aa56a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/30/2022
ms.locfileid: "66858887"
---
# <a name="manage-access-to-microsoft-whiteboard-for-your-organization"></a>Administrer adgang til Microsoft Whiteboard for din organisation

>[!NOTE]
> Denne artikel gælder for enterprise- eller education-organisationer, der bruger Whiteboard. For GCC High-miljøer for US Government skal du se [Administrer adgang til Microsoft Whiteboard for GCC High-miljøer](manage-whiteboard-access-gcc-high.md).

Microsoft Whiteboard er et visuelt samarbejdslærred, hvor personer, indhold og ideer mødes. Whiteboard kører i dag på Azure for Enterprise- og Education-kunder. Whiteboard overgår til at blive kørt oven på OneDrive for Business. Denne overgang giver mange nye funktioner og giver dig mulighed for at oprette, dele, finde og administrere whiteboards lige så nemt som et hvilket som helst Office-dokument.

Whiteboard er automatisk aktiveret for relevante Microsoft 365-lejere. 

Whiteboard overholder globale standarder, herunder standardbestemmelserne SOC 1, SOC 2, ISO 27001, HIPAA og EU. 

Følgende administratorindstillinger er påkrævet for Whiteboard:

- Whiteboard skal være aktiveret globalt i Microsoft 365 Administration.

- Cmdlet'en <code>Set-SPOTenant -IsWBFluidEnabled</code> skal aktiveres ved hjælp af [SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online).

>[!NOTE]
> Udrulningen af OneDrive for Business lager er i gang. Når du går til Microsoft 365 Administration, deaktiveres muligheden for at tilmelde dig eller fra OneDrive for Business lagerplads, hvis din lejer allerede er overgået til OneDrive for Business.

Du kan styre adgangen til Whiteboard på følgende måder:

- Aktivér eller deaktiver Whiteboard for hele lejeren ved hjælp af Microsoft 365 Administration.

- Vis eller skjul whiteboard for bestemte brugere i møder ved hjælp af en Teams-mødepolitik. Den vil stadig være synlig via internettet, oprindelige klienter og teams-faneappen.

- Kræv politikker for betinget adgang for at få adgang til Whiteboard ved hjælp af Azure Active Directory Administration.

>[!NOTE]
> Teams-mødepolitikker skjuler kun whiteboard-indgangspunkter. Det forhindrer ikke brugerne i at bruge Whiteboard. Politikker for betinget adgang forhindrer enhver adgang til Whiteboard, men skjuler ikke indgangspunkterne.

## <a name="enable-or-disable-whiteboard"></a>Aktivér eller deaktiver Whiteboard

Benyt følgende fremgangsmåde for at aktivere eller deaktivere Whiteboard for din lejer:

1. Gå til Microsoft 365 Administration.

2. Skriv Whiteboard øverst til højre i søgefeltet øverst til højre på *startsiden i Administration*.

3. I søgeresultaterne skal du vælge **Whiteboard-indstillinger**.

4. Slå **Whiteboard til eller fra på panelet Whiteboard til eller fra for hele organisationen** til **Til**.

5. Vælg **Gem**.

6. Opret forbindelse til [SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online).

7. Aktivér væske ved hjælp af følgende <code>Set-SPOTenant</code> cmdlet:

   <pre><code class="lang-powershell">Set-SPOTenant -IsWBFluidEnabled $true</code></pre>
 
## <a name="show-or-hide-whiteboard"></a>Vis eller skjul whiteboard

Hvis du vil vise eller skjule Whiteboard i møder, skal du se [Indstillinger for mødepolitik](/microsoftteams/meeting-policies-content-sharing). 

## <a name="prevent-access-to-whiteboard"></a>Undgå adgang til Whiteboard

Hvis du vil forhindre adgang til whiteboard for bestemte brugere, skal du se [Oprettelse af en politik for betinget adgang](/azure/active-directory/conditional-access/concept-conditional-access-policies).

## <a name="see-also"></a>Se også

[Administrer data for Whiteboard](manage-data-organizations.md)

[Administrer deling for Whiteboard](manage-sharing-organizations.md)

[Installer whiteboard på Windows](deploy-on-windows-organizations.md)
