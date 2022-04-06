---
title: Forbundne programmer i Microsoft Defender for Endpoint
ms.reviewer: ''
description: Få vist forbundne partnerprogrammer, der bruger standard-OAuth 2.0-protokollen til at godkende og angive tokens til brug med Microsoft Defender for Endpoint API'er.
keywords: partnere, programmer, tredjepartsforbindelser, sentinelone, lookout, bitdefender, corrata, morphisec, paloalto, ziften, bedre mobil
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 9e15103f4366d0717af9cec44d516b4b16a7160a
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64475559"
---
# <a name="connected-applications-in-microsoft-defender-for-endpoint"></a>Forbundne programmer i Microsoft Defender for Endpoint

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

Tilsluttede programmer integreres med Defender for Endpoint-platformen ved hjælp af API'er.

Programmer bruger standard-OAuth 2.0-protokollen til at godkende og angive tokens til brug med Microsoft Defender for Endpoint API'er. Desuden giver Azure Active Directory (Azure AD)-programmer lejeradministratorer mulighed for at angive eksplicit kontrol over, hvilke API'er der kan tilgås ved hjælp af den tilsvarende app.

Du skal følge disse trin for [at bruge](/microsoft-365/security/defender-endpoint/apis-intro) API'er med det forbundne program.

I venstre **navigationsmenu** skal du **vælge Partnere & API'er** (under Slutpunkter) > **tilknyttede programmer**.

## <a name="view-connected-application-details"></a>Få vist oplysninger om forbundne programmer

Siden Forbundne programmer indeholder oplysninger om de Azure AD-programmer, der er Microsoft Defender for Endpoint i organisationen. Du kan gennemse brugen af de tilknyttede programmer: Sidst set, antallet af anmodninger inden for de seneste 24 timer og anmode om tendenser inden for de seneste 30 dage.

:::image type="content" source="images/connected-apps.png" alt-text="De tilknyttede programmer" lightbox="images/connected-apps.png":::
 
## <a name="edit-reconfigure-or-delete-a-connected-application"></a>Redigere, omkonfigurere eller slette et tilknyttet program

Linket **Åbn programindstillinger** åbner den tilsvarende Azure AD-programadministrationsside i Azure Portal. Fra Azure Portal kan du administrere tilladelser, omkonfigurere eller slette de tilknyttede programmer.
