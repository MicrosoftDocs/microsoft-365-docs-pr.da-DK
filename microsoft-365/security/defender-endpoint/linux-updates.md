---
title: Installér opdateringer til Microsoft Defender til slutpunkt på Linux
ms.reviewer: ''
description: Beskrivelse af, hvordan du installerer opdateringer til Microsoft Defender til slutpunkt på Linux i virksomhedsmiljøer.
keywords: microsoft, defender, Microsoft Defender for Endpoint, linux, updates, deploy
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
ms.openlocfilehash: 71c689143feca3d8c87d219a55c4ea42b4f9d950
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/12/2022
ms.locfileid: "63597517"
---
# <a name="deploy-updates-for-microsoft-defender-for-endpoint-on-linux"></a>Installér opdateringer til Microsoft Defender til slutpunkt på Linux

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

Microsoft udgiver jævnligt softwareopdateringer for at forbedre ydeevnen, sikkerheden og levere nye funktioner.

> [!WARNING]
> Hver version af Defender til Slutpunkt på Linux har en udløbsdato, hvorefter den ikke længere vil fortsætte med at beskytte din enhed. Du skal opdatere produktet før denne dato. Kør følgende kommando for at kontrollere udløbsdatoen:
> ```bash
> mdatp health --field product_expiration
> ```


Generelt tilgængelige Microsoft Defender for slutpunktsfunktioner er tilsvarende, uanset hvilken opdateringskanal der bruges til en installation (Beta (Insider), Prøveversion (Ekstern), Aktuel (produktion)).


Hvis du vil opdatere Defender til slutpunkt på Linux manuelt, skal du udføre en af følgende kommandoer:

## <a name="rhel-and-variants-centos-and-oracle-linux"></a>RHEL og varianter (CentOS og Oracle Linux)

```bash
sudo yum update mdatp
```

## <a name="sles-and-variants"></a>SLES og varianter

```bash
sudo zypper update mdatp
```

## <a name="ubuntu-and-debian-systems"></a>Ubuntu- og Ink- systemer

```bash
sudo apt-get install --only-upgrade mdatp
```

> [!IMPORTANT]
> Når du integrerer Microsoft Defender for Endpoint og Defender for Cloud, modtager mdatp-agenten automatisk opdateringer som standard.
