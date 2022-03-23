---
title: Konfigurere beskeder, der sendes til MSSP'er
description: Konfigurere beskeder, der sendes til MSSP'er
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
ms.openlocfilehash: 0cead78048fcf8ef25637e969aae816b7a8d8e76
ms.sourcegitcommit: dfa9f28a5a5055a9530ec82c7f594808bf28d0dc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/29/2021
ms.locfileid: "63592652"
---
# <a name="configure-alert-notifications-that-are-sent-to-mssps"></a>Konfigurere beskeder, der sendes til MSSP'er

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-mssp-support-abovefoldlink)

> [!NOTE]
> Dette trin kan udføres af enten MSSP-kunde eller MSSP. MSSP'er skal have de relevante tilladelser til at konfigurere dette på vegne af MSSP-kunden.

Når portalen er tildelt adgang, kan du oprette beskedregler, så mails sendes til MSSP'er, når der oprettes beskeder tilknyttet lejeren, og angive betingelser opfyldes.

Få mere at vide under [Opret regler for beskeder om beskeder](configure-email-notifications.md#create-rules-for-alert-notifications).

Disse afkrydsningsfelter skal være markeret:

- **Medtag organisationens** navn – Kundenavnet føjes til mailmeddelelser
- **Medtag lejerspecifik portallink – URL-adresse** til påmindelseslink har lejerspecifik parameter (tid=target_tenant_id), der giver direkte adgang til mållejerportalen

## <a name="related-topics"></a>Relaterede emner

- [Giv MSSP adgang til portalen](grant-mssp-access.md)
- [Få adgang til MSSP-kundeportalen](access-mssp-portal.md)
- [Hent beskeder fra kundelejeren](fetch-alerts-mssp.md)
