---
title: Offboard-enheder fra Microsoft Defender for Endpoint-tjenesten
description: Onboarde Windows-enheder, servere, ikke-Windows-enheder fra Microsoft Defender for Endpoint-tjenesten
keywords: offboarding, Microsoft Defender for Endpoint offboarding, offboarding
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
ms.openlocfilehash: 3fec93e45fbdced0cc6c4106d24a29eb13087d02
ms.sourcegitcommit: c6f1486617b39565bfd8f662ee6ad65a9cefd3e3
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/29/2022
ms.locfileid: "66531016"
---
# <a name="offboard-devices-from-the-microsoft-defender-for-endpoint-service"></a>Offboard-enheder fra Microsoft Defender for Endpoint-tjenesten

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

**Platforme**
- Macos
- Linux
- Windows Server 2012 R2
- Windows Server 2016

> Vil du opleve Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-offboarddevices-abovefoldlink)

Følg de tilsvarende instruktioner, afhængigt af din foretrukne installationsmetode.

> [!NOTE]
> Status for en enhed ændres til [Inaktiv](fix-unhealthy-sensors.md#inactive-devices) 7 dage efter offboarding.
>
> Offboardede enheders data (f.eks. tidslinje, beskeder, sikkerhedsrisici osv.) forbliver på portalen, indtil den konfigurerede [opbevaringsperiode](data-storage-privacy.md#how-long-will-microsoft-store-my-data-what-is-microsofts-data-retention-policy) udløber.
>
> Enhedens profil (uden data) forbliver på [enhedslisten](machines-view-overview.md) i højst 180 dage.
>
> Desuden indregnes enheder, der ikke er aktive inden for de sidste 30 dage, ikke på de data, der afspejler organisationens Håndtering af trusler og sikkerhedsrisici [eksponeringsscore](tvm-exposure-score.md) og Microsoft Secure Score for Devices.
>
> Hvis du kun vil have vist aktive enheder, kan du filtrere efter [sensortilstandstilstand](machines-view-overview.md#use-filters-to-customize-the-device-inventory-views), [enhedskoder](machine-tags.md) eller [computergrupper](machine-groups.md).

## <a name="offboard-windows-devices"></a>Windows-enheder uden for bord

- [Offboard-enheder, der bruger et lokalt script](configure-endpoints-script.md#offboard-devices-using-a-local-script)
- [Offboard-enheder, der bruger Gruppepolitik](configure-endpoints-gp.md#offboard-devices-using-group-policy)
- [Offboard-enheder, der bruger værktøjer til Enhedshåndtering mobilenheder](configure-endpoints-mdm.md#offboard-devices-using-mobile-device-management-tools)

## <a name="offboard-servers"></a>Offboard-servere

- [Offboard-servere](configure-server-endpoints.md#offboard-windows-servers)

## <a name="offboard-non-windows-devices"></a>Offboard ikke-Windows-enheder

- [Offboard ikke-Windows-enheder](configure-endpoints-non-windows.md#offboard-non-windows-devices)
