---
title: Konfigurer enhedsgrupper i Jamf-Pro
description: Få mere at vide om, hvordan du konfigurerer enhedsgrupper i Jamf Pro til Microsoft Defender for Endpoint på macOS
keywords: enhed, gruppe, microsoft, defender, Microsoft Defender for Endpoint, mac, installation, deploy, uninstallation, intune,propfpro, macos, catalina, mojave, high sierra
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: c22a1a68af2722e6b17d155a37632c1f6417b605
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64471753"
---
# <a name="set-up-microsoft-defender-for-endpoint-on-macos-device-groups-in-jamf-pro"></a>Konfigurer Microsoft Defender for Endpoint i macOS-enhedsgrupper i Jamf Pro

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

Konfigurer enhedsgrupper, der ligner organisationsenheden for gruppepolitik (OUs), Microsoft Endpoint Configuration Manager gruppen af enheder og Intune gruppe af enheder.

1. Gå til **Statiske computergrupper**.

2. Vælg **Ny**. 

   :::image type="content" source="images/jamf-pro-static-group.png" alt-text="Siden Jamf Pro1" lightbox="images/jamf-pro-static-group.png":::

3. Angiv et visningsnavn, og vælg **Gem**.

   :::image type="content" source="images/jamfpro-machine-group.png" alt-text="Siden Jamf Pro2" lightbox="images/jamfpro-machine-group.png":::

4. Nu kan du se **Contosos computergruppe** under **Statiske computergrupper**.

   :::image type="content" source="images/contoso-machine-group.png" alt-text="Siden Syltef Pro3" lightbox="images/contoso-machine-group.png":::

## <a name="next-step"></a>Næste trin
- [Konfigurer Microsoft Defender for Endpoint macOS-politikker i Jamf Pro](mac-jamfpro-policies.md)
