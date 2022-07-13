---
title: Administrer enheder i Microsoft Defender til virksomheder
description: Få mere at vide om, hvordan du tilføjer, fjerner og administrerer enheder i Defender for Business, slutpunktsbeskyttelse for små og mellemstore virksomheder.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 735f9e04a9176ce1b6626a050429c0b7323a7c0b
ms.sourcegitcommit: fa90763559239c4c46c5e848939126763879d8e4
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/13/2022
ms.locfileid: "66772921"
---
# <a name="manage-devices-in-microsoft-defender-for-business"></a>Administrer enheder i Microsoft Defender til virksomheder

I Defender for Business kan du administrere enheder på følgende måde:

- [Få vist en liste over onboardede enheder](#view-the-list-of-onboarded-devices) for at se deres risikoniveau, eksponeringsniveau og tilstand
- [Udfør handlinger på en enhed](#take-action-on-a-device-that-has-threat-detections) , der har trusselsregistreringer
- [Onboarder en enhed til Defender for Business](#onboard-a-device)  
- [Om bord på en enhed fra Defender for Business](#offboard-a-device)


## <a name="view-the-list-of-onboarded-devices"></a>Få vist listen over onboardede enheder

:::image type="content" source="../../media/defender-business/mdb-deviceinventory.png" alt-text="Skærmbillede af enhedslager":::

1. Gå til Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på.

2. Vælg **Enhedslager** i navigationsruden.

3. Vælg en enhed for at åbne dens pop op-panel, hvor du kan få mere at vide om dens status og udføre handlinger. 

   Hvis du endnu ikke har nogen enheder angivet, kan du [onboarde enheder til Defender for Business](mdb-onboard-devices.md)

## <a name="take-action-on-a-device-that-has-threat-detections"></a>Udfør handlinger på en enhed, der har trusselsregistreringer

:::image type="content" source="../../media/defender-business/mdb-selected-device.png" alt-text="Skærmbillede af en valgt enhed med tilgængelige oplysninger og handlinger":::

1. Vælg **Enhedslager** i navigationsruden i Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)). 

2. Vælg en enhed for at åbne det tilhørende pop op-panel, og gennemse de oplysninger, der vises.

3. Vælg ellipsen (**...**) for at åbne menuen Handlinger. 

4. Vælg en handling, f.eks **. Kør antivirusscanning** eller **Start automatiseret undersøgelse**. 

## <a name="onboard-a-device"></a>Ombord på en enhed

Se [Om bord på enheder til Defender for Business](mdb-onboard-devices.md).

## <a name="offboard-a-device"></a>Uden for en enhed

Se [Offboarding af en enhed](mdb-offboard-devices.md).

## <a name="next-steps"></a>Næste trin

- [Få vist og administrer hændelser i Defender for Business](mdb-view-manage-incidents.md)
- [Reager på og afhjælp trusler i Defender for Business](mdb-respond-mitigate-threats.md)
- [Gennemse afhjælpningshandlinger i Løsningscenter](mdb-review-remediation-actions.md)
- [Opret eller rediger enhedsgrupper](mdb-create-edit-device-groups.md)