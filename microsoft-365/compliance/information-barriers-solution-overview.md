---
title: Informationsbarrierer
description: Få mere at vide om, hvordan du konfigurerer informationsbarrierer i Microsoft Purview.
keywords: Microsoft 365, Microsoft Purview, overholdelse af angivne standarder, informationsbarrierer
ms.localizationpriority: medium
ms.service: O365-seccomp
ms.topic: article
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection:
- m365-security-compliance
- m365solution-insiderrisk
- m365initiative-compliance
- m365solution-scenario
ms.openlocfilehash: 21ad4f0cc6614bed3c579a8025d83200446fec18
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66627233"
---
# <a name="information-barriers"></a>Informationsbarrierer

Microsoft 365 muliggør kommunikation og samarbejde på tværs af grupper og organisationer og understøtter metoder til at begrænse kommunikation og samarbejde mellem bestemte grupper af brugere, når det er nødvendigt. Dette kan omfatte situationer eller scenarier, hvor du vil begrænse kommunikation og samarbejde mellem to grupper for at undgå, at der opstår en interessekonflikt i din organisation. Dette kan også omfatte situationer, hvor du har brug for at begrænse kommunikation og samarbejde mellem visse personer i organisationen for at beskytte interne oplysninger.

Microsoft Purview Information Barriers (IB) understøttes i Microsoft Teams, SharePoint Online og OneDrive for Business. En overholdelsesadministrator eller IB-administrator kan definere politikker for at tillade eller forhindre kommunikation mellem grupper af brugere i Microsoft Teams. IB-politikker kan bruges til situationer som disse:

- Brugeren i dag erhvervsdrivende gruppe bør ikke kommunikere eller dele filer med markedsføring team
- Økonomiafdelingen, der arbejder med fortrolige virksomhedsoplysninger, må ikke kommunikere eller dele filer med bestemte grupper i organisationen
- Et internt team med faghemmeligt materiale må ikke ringe til eller chatte online med personer i visse grupper i organisationen
- Et forskningsteam bør kun ringe til eller chatte online med et produktudviklingsteam

## <a name="configure-information-barriers"></a>Konfigurer informationsbarrierer

Brug følgende trin til at konfigurere IB for din organisation:

![Skridt til informationsbarrierer i forbindelse med insiderrisikoløsning.](../media/ir-solution-ib-steps.png)

1. Få mere at vide om [informationsbarrierer](information-barriers.md)
2. Konfigurer [forudsætninger og tilladelser](information-barriers-policies.md#step-1-make-sure-prerequisites-are-met)
3. [Segmentér brugere i din organisation](information-barriers-policies.md#step-2-segment-users-in-your-organization)
4. Opret og konfigurer [IB-politikker](information-barriers-policies.md#step-3-create-ib-policies)
5. Anvend [IB-politikker](information-barriers-policies.md#step-4-apply-ib-policies)

## <a name="more-information-about-information-barriers"></a>Flere oplysninger om informationsbarrierer

- [Attributter for IB-politikker](information-barriers-attributes.md)
- [Rediger eller fjern IB-politikker](information-barriers-edit-segments-policies.md)
