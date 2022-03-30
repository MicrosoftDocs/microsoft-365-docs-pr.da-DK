---
title: Få adgang Microsoft 365 Defender MSSP-kundeportal
description: Få adgang Microsoft 365 Defender MSSP-kundeportal
keywords: administreret sikkerheds serviceudbyder, mssp, konfigurer, integration
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
ms.topic: article
ms.technology: mde
ms.openlocfilehash: b1c133048e6600d553f0530e135ebfc2c441dd84
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63599296"
---
# <a name="access-the-microsoft-365-defender-mssp-customer-portal"></a>Få adgang Microsoft 365 Defender MSSP-kundeportal

**Gælder for:**
- [ Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [ Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-mssp-support-abovefoldlink)

> [!NOTE]
> Disse trin er rettet mod MSSP.

MsSP-kunder får som standard adgang til Microsoft 365 Defender lejer via følgende URL-adresse: `https://security.microsoft.com/`.

MSSP'er skal dog bruge en lejerspecifik URL-adresse i følgende format:  `https://security.microsoft.com?tid=customer_tenant_id` for at få adgang til MSSP-kundeportalen.

Generelt skal MSSP'er føjes til hver af MSSP-kundens Azure AD, som de vil administrere.

Brug følgende trin til at hente MSSP-kundelejer-id'et, og brug derefter id'et til at få adgang til den lejerspecifikke URL-adresse:

1. Som MSSP skal du logge på Azure AD med dine legitimationsoplysninger.

2. Skift mappe til MSSP-kundens lejer.

3. Vælg **Azure Active Directory > Egenskaber**. Du finder lejer-id'et i feltet Katalog-id.

4. Få adgang til MSSP-kundeportalen ved at erstatte `customer_tenant_id` værdien i følgende URL-adresse: `https://security.microsoft.com/?tid=customer_tenant_id`.

## <a name="related-topics"></a>Relaterede emner

- [Giv MSSP adgang til portalen](grant-mssp-access.md)
- [Konfigurere beskeder](configure-mssp-notifications.md)
- [Hent beskeder fra kundelejeren](fetch-alerts-mssp.md)
