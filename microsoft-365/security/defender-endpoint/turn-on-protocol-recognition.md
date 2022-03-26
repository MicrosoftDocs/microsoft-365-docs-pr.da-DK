---
title: Slå protokolgenkendelse til for Microsoft Defender Antivirus
description: Slå protokolgenkendelse til for Microsoft Defender Antivirus.
keywords: Microsoft Defender Antivirus, antimalware, sikkerhed, defender, protokolgenkendelse
search.product: eADQiWindows 10XVcnh
ms.pagetype: security
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.date: 02/21/2022
ms.reviewer: ''
manager: dansimp
ms.custom: nextgen
ms.technology: mde
ms.topic: article
ms.collection: m365-security-compliance
ms.openlocfilehash: 221eff4af6bf8e77f29db84694bf3a683107fc8c
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63595931"
---
# <a name="turn-on-protocol-recognition"></a>Slå protokolgenkendelse til

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Denne politikindstilling gør det muligt at konfigurere protokolgenkendelse for netværksbeskyttelse mod udnyttelse af kendte sårbarheder. Hvis du aktiverer eller ikke konfigurerer denne indstilling, aktiveres protokolgenkendelse. Hvis du deaktiverer denne indstilling, deaktiveres protokolgenkendelse.

[!IMPORTANT]
Denne indstilling frarådes nu. 

## <a name="use-group-policy-to-configure-protocol-recognition"></a>Brug Gruppepolitik til at konfigurere protokolgenkendelse

1. På slutpunktet Gruppepolitik administration skal du åbne [Gruppepolitik administrationskonsollen](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)).

2. Gå til **Administrative skabeloner til** \> **computerkonfiguration** \> **Windows komponenter** \> **Microsoft Defender Antivirus dit** \> **netværksinspektionssystem**.

3. Vælg **protokolgenkendelse**. Denne politik er som standard aktiveret. Hvis indstillet **til Ikke konfigureret**, aktiveres tilbagetrækning af definition.

4. Hvis du vil redigere politikken, skal du vælge **linket rediger politikindstilling** .

5. Vælg **Aktiveret**, og vælg derefter **OK**.

6. Installér den opdaterede Gruppepolitik-objekt. Se [Gruppepolitik Administrationskonsol](/windows/win32/srvnodes/group-policy).

> [!TIP]
> Bruger du Gruppepolitik lokale objekter? Se, hvordan de oversættes i skyen. [Analysér dine lokale gruppepolitikobjekter ved hjælp Gruppepolitik analyser i Microsoft Endpoint Manager – forhåndsvisning](/mem/intune/configuration/group-policy-analytics).

## <a name="related-articles"></a>Relaterede artikler

- [Microsoft Defender Antivirus i Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [Aktivér skybaseret leveringsbeskyttelse](enable-cloud-protection-microsoft-defender-antivirus.md)
- [Sådan oprettes og installeres antimalwarepolitikker: Skybeskyttelsestjeneste](/configmgr/protect/deploy-use/endpoint-antimalware-policies#cloud-protection-service)
