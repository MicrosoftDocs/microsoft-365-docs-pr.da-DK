---
title: Konfigurer funktioner til overholdelse af angivne standarder
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: how-to
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- M365-identity-device-management
- Adm_TOC
ms.custom:
- MiniMaven
- MSB365
- OKR_SMB_M365
- seo-marvel-mar
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
description: Konfigurer funktioner til overholdelse af angivne standarder for at forhindre tab af data og holde dine og dine kunders følsomme oplysninger sikre.
ms.openlocfilehash: db1993a99292f9b90a3b567007b96742b0f359b2
ms.sourcegitcommit: e9692a40dfe1f8c2047699ae3301c114a01b0d3a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/01/2022
ms.locfileid: "66858911"
---
# <a name="set-up-compliance-features"></a>Konfigurer funktioner til overholdelse af angivne standarder


Se [Microsoft 365 small business-hjælp](https://go.microsoft.com/fwlink/?linkid=2197659) på YouTube.

Dit Microsoft 365 Business Premium abonnement indeholder funktioner til overholdelse af angivne standarder og beskyttelse af personlige oplysninger. Disse funktioner hjælper med at beskytte din virksomheds data og beskytte dine og dine kunders følsomme oplysninger. Denne artikel er designet til at hjælpe dig med at komme i gang med dine funktioner til overholdelse af angivne standarder.


## <a name="before-you-begin"></a>Før du begynder

Sørg for, at du har en af følgende roller tildelt i Azure Active Directory:

- Global administrator
- Administrator for overholdelse af angivne standarder

Du kan få mere at vide under [Kom i gang med rollesiden](../admin/add-users/admin-roles-page.md).

## <a name="use-compliance-manager-to-get-started"></a>Brug Overholdelsesstyring til at komme i gang

:::image type="content" source="./media/m365bp-compliancemanager.png" alt-text="Skærmbillede af Overholdelsesstyring i Microsoft 365 Business Premium.":::

Microsoft 365 Business Premium omfatter Overholdelsesstyring, som kan hjælpe dig med at komme i gang med at konfigurere dine funktioner til overholdelse af angivne standarder. Sådanne funktioner omfatter forebyggelse af datatab, administration af datalivscyklus og styring af insiderrisiko for at nævne nogle få. Overholdelsesstyring kan spare dig tid ved at fremhæve anbefalinger, en overholdelsesscore og metoder til at forbedre din score.

Sådan kommer du i gang:

1. Gå til , [https://compliance.microsoft.com](https://compliance.microsoft.com) og log på.

2. Vælg **Overholdelsesstyring** i navigationsruden.

3. Gennemse oplysningerne under fanen **Oversigt** . Vælg et element eller link for at få vist flere oplysninger eller for at udføre handlinger, f.eks. konfiguration af en DLP-politik (forebyggelse af datatab). I afsnittet **Løsninger, der påvirker din score** , kan du f.eks. vælge linket i kolonnen **Resterende handlinger** .

   :::image type="content" source="./media/m365bp-compliancesolutions.png" alt-text="Skærmbillede af løsninger, der påvirker ruden Score.":::

   Denne handling fører dig til fanen **Handlinger til forbedring** , som er filtreret efter det element, du har valgt. I dette eksempel kigger vi på DLP-politikker, der skal konfigureres.

   :::image type="content" source="./media/m365bp-dlppoliciestoconfigure.png" alt-text="Skærmbillede af DLP-politikker, der skal konfigureres.":::

4. Vælg et element under fanen **Forbedringshandlinger** . I vores eksempel har vi valgt **Opret tilpassede DLP-politikker eller personlige oplysninger**. En side indlæses, der indeholder flere oplysninger om den politik, der skal konfigureres.

   :::image type="content" source="./media/m365bp-dlppolicyinfo.png" alt-text="Skærmbillede af oplysninger om DLP-politik for kundeindhold.":::

   Følg oplysningerne på skærmen for at konfigurere din DLP-politik.

Du kan få flere oplysninger om funktioner til overholdelse af angivne standarder i Microsoft 365 til virksomheder i [dokumentationen til Microsoft Purview](../compliance/index.yml).

## <a name="use-sensitivity-labels"></a>Brug følsomhedsmærkater

Se denne og andre videoer på vores [YouTube-kanal](https://go.microsoft.com/fwlink/?linkid=2198022).

Følsomhedsmærkater er tilgængelige i Office-apps (f.eks. Outlook, Word, Excel og PowerPoint). Eksempler på mærkater omfatter:

- Normal
- Personal
- Privat
- Fortrolige

Du kan dog også definere andre mærkater for din virksomhed.

Brug følgende artikler til at komme i gang med følsomhedsmærkater:

1. [Få mere at vide om følsomhedsmærkater](../compliance/sensitivity-labels.md).

2. [Kom i gang med følsomhedsmærkater](../compliance/get-started-with-sensitivity-labels.md).

3. [Opret og konfigurer følsomhedsmærkater og deres politikker](../compliance/create-sensitivity-labels.md).

4. [Vis personer i din virksomhed, hvordan du bruger følsomhedsmærkater](https://support.microsoft.com/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9)