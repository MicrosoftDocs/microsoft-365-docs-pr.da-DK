---
title: Administrer enheder i Microsoft Defender for Business
description: Få mere at vide om, hvordan du administrerer enheder i Microsoft Defender for Business
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.date: 02/24/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: f47e72b3651b4a86eed4001fc51f051f47e2f3c7
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/17/2022
ms.locfileid: "63593042"
---
# <a name="manage-devices-in-microsoft-defender-for-business"></a>Administrer enheder i Microsoft Defender for Business

> [!IMPORTANT]
> Microsoft Defender for Business udrulles til [Microsoft 365 Business Premium](../../business-premium/index.md) kunder fra d. 1. marts 2022. Defender for Business som et enkeltstående abonnement er i preview, og den udrulles gradvist til kunder og [it-partnere](https://aka.ms/mdb-preview) , der tilmelder sig her for at anmode om det. [Forhåndsvisning indeholder et indledende sæt scenarier](mdb-tutorials.md#try-these-preview-scenarios), og vi tilføjer funktioner regelmæssigt.
> 
> Nogle oplysninger i denne artikel relaterer til foreløbige produkter/tjenester, der kan være væsentligt ændret, før de frigives kommercielt. Microsoft giver ingen garantier, udtrykkelige eller underforståede, for de oplysninger, du har angivet her. 

I Microsoft Defender for Business kan du administrere enheder på følgende måde:

- [Få vist en liste over onboardede](#view-the-list-of-onboarded-devices) enheder for at se deres risikoniveau, eksponeringsniveau og tilstand

- [Handling på en enhed, der](#take-action-on-a-device-that-has-threat-detections) har trusselsregistreringer

- [Onboard en enhed til Defender for Business](#onboard-a-device)  

- [Offboard a device from Defender for Business](#offboard-a-device)

>
> **Har du et minut?**
> Tag vores korte <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">undersøgelse om Microsoft Defender for Business</a>. Vi vil meget gerne høre fra dig!
>

## <a name="view-the-list-of-onboarded-devices"></a>Få vist listen over onboardede enheder

:::image type="content" source="../../media/defender-business/mdb-deviceinventory.png" alt-text="Skærmbillede af lager over enheder":::

1. Gå til Microsoft 365 Defender -portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på.

2. Vælg Lagerliste for enhed i **navigationsruden**.

3. Vælg en enhed for at åbne pop op-panelet, hvor du kan få mere at vide om dens status og gøre noget. 

   Hvis du endnu ikke har angivet nogen enheder, skal [du onboarde enheder til Microsoft Defender for Business](mdb-onboard-devices.md)

## <a name="take-action-on-a-device-that-has-threat-detections"></a>Handling på en enhed, der har trusselsregistreringer

:::image type="content" source="../../media/defender-business/mdb-selected-device.png" alt-text="Skærmbillede af en valgt enhed med oplysninger og tilgængelige handlinger":::

1. Vælg lager Microsoft 365 Defender [https://security.microsoft.com](https://security.microsoft.com) enhed i navigationsruden i **navigationsruden**. 

2. Vælg en enhed for at åbne pop op-panelet, og gennemse de viste oplysninger.

3. Vælg ellipsen (**...**) for at åbne menuen Handlinger. 

4. Vælg en handling, f.eks **Kør antivirus-scanning** eller **Initier automatiseret undersøgelse**. 

## <a name="onboard-a-device"></a>Onboarde en enhed

Se [Onboard-enheder til Microsoft Defender for Business](mdb-onboard-devices.md).

## <a name="offboard-a-device"></a>Offboard a device

Se [Offboarding af en enhed](mdb-onboard-devices.md#offboarding-a-device).

## <a name="next-steps"></a>Næste trin

- [Få vist og administrer hændelser i Microsoft Defender for Business](mdb-view-manage-incidents.md)

- [Re besvare og afhjælpe trusler i Microsoft Defender for Business](mdb-respond-mitigate-threats.md)

- [Gennemse afhjælpningshandlinger i Handlingscenter](mdb-review-remediation-actions.md)

- [Opret eller rediger enhedsgrupper](mdb-create-edit-device-groups.md)