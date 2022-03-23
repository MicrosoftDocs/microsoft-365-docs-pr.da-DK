---
title: Konfigurer enhedsgrupper i Jamf-Pro
description: Få mere at vide om, hvordan du konfigurerer enhedsgrupper i Jamf Pro til Microsoft Defender til Slutpunkt på macOS
keywords: enhed, gruppe, microsoft, defender, Microsoft Defender til Endpoint, mac, installation, deploy, uninstallation, intune,propfpro, macos, catalina, mojave, high sierra
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
ms.openlocfilehash: 3b9d6255320b5d702768614059bb9edff28be3b3
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/12/2022
ms.locfileid: "63592825"
---
# <a name="set-up-microsoft-defender-for-endpoint-on-macos-device-groups-in-jamf-pro"></a>Konfigurer Microsoft Defender til Slutpunkt på macOS-enhedsgrupper i Jamf Pro

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

Konfigurer enhedsgrupper, der ligner organisationsenheden for gruppepolitik (OUs), Microsoft Endpoint Configuration Manager gruppen af enheder og Intunes enhedsgrupper.

1. Gå til **Statiske computergrupper**.

2. Vælg **Ny**. 

    ![Billede af Jamf Pro1.](images/jamf-pro-static-group.png)

3. Angiv et visningsnavn, og vælg **Gem**.

    ![Billede af Jamf Pro2.](images/jamfpro-machine-group.png)

4. Nu kan du se **Contosos computergruppe** under **Statiske computergrupper**.

    ![Billede af Jamf Pro3.](images/contoso-machine-group.png)

## <a name="next-step"></a>Næste trin
- [Konfigurer Microsoft Defender til Slutpunkt på macOS-politikker i Jamf Pro](mac-jamfpro-policies.md)
