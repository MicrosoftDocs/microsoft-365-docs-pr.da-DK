---
title: Offboard-enheder fra Microsoft Defender for Endpoint-tjenesten
description: Onboard Windows enheder, servere, Windows-enheder fra Microsoft Defender til Endpoint-tjenesten
keywords: offboarding, Microsoft Defender til endpoint offboarding, offboarding
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
ms.openlocfilehash: c2ec837ebc9fef0aabd2810dbd22db24597c52da
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63593427"
---
# <a name="offboard-devices-from-the-microsoft-defender-for-endpoint-service"></a>Offboard-enheder fra Microsoft Defender for Endpoint-tjenesten

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

**Platforme**
- macOS
- Linux
- Windows Server 2012 R2
- Windows Server 2016

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-offboarddevices-abovefoldlink)

Følg de tilsvarende instruktioner afhængigt af din foretrukne installationsmetode.

> [!NOTE]
> Status for en enhed ændres til [Inaktiv 7](fix-unhealthy-sensors.md#inactive-devices) dage efter offboarding.
>
> Data fra enheder, der ikke erboardet (f.eks. tidslinje, beskeder, sårbarheder osv.), forbliver i portalen, indtil den konfigurerede [opbevaringsperiode](data-storage-privacy.md#how-long-will-microsoft-store-my-data-what-is-microsofts-data-retention-policy) udløber.
>
> Enhedens profil (uden data) forbliver på listen [Enheder i](machines-view-overview.md) højst 180 dage.
>
> Desuden tages enheder, der ikke er aktive inden for de seneste 30 dage, ikke med i de data, der afspejler din organisations [Håndtering af trusler og sikkerhedsrisici-eksponeringsscore](tvm-exposure-score.md) og Microsoft Secure Score for enheder.
>
> Hvis du kun vil have vist aktive enheder, kan du filtrere efter [sensortilstand](machines-view-overview.md#use-filters-to-customize-the-device-inventory-views), [enhedsmærker](machine-tags.md) eller [maskingrupper](machine-groups.md).

## <a name="offboard-windows-devices"></a>Offboard Windows enheder

- [Offboard-enheder, der bruger et lokalt script](configure-endpoints-script.md#offboard-devices-using-a-local-script)
- [Offboard-enheder, der bruger Gruppepolitik](configure-endpoints-gp.md#offboard-devices-using-group-policy)
- [Offboard-enheder ved hjælp af værktøjer til administration af mobilenheder](configure-endpoints-mdm.md#offboard-and-monitor-devices-using-mobile-device-management-tools)

## <a name="offboard-servers"></a>Offboard-servere

- [Offboard-servere](configure-server-endpoints.md#offboard-windows-servers)

## <a name="offboard-non-windows-devices"></a>Offboard ikke-Windows enheder

- [Offboard ikke-Windows enheder](configure-endpoints-non-windows.md#offboard-non-windows-devices)
