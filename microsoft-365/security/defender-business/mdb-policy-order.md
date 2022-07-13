---
title: Forstå politikrækkefølgen i Microsoft Defender til virksomheder
description: Få mere at vide om prioritetsrækkefølgen med politikker for cybersikkerhed for at beskytte dine virksomhedsenheder med Defender for Business.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 361a1a08569f24c83498fddeb0e4c2b9bd8c5d02
ms.sourcegitcommit: fa90763559239c4c46c5e848939126763879d8e4
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/13/2022
ms.locfileid: "66770871"
---
# <a name="understand-policy-order-in-microsoft-defender-for-business"></a>Forstå politikrækkefølgen i Microsoft Defender til virksomheder

## <a name="policy-order-in-defender-for-business"></a>Politikrækkefølge i Defender for Business

Defender for Business indeholder foruddefinerede politikker, der hjælper med at sikre, at de enheder, dine medarbejdere bruger, er beskyttet. Dit sikkerhedsteam kan også tilføje nye politikker. Lad os f.eks. antage, at du vil anvende visse indstillinger på nogle enheder og andre indstillinger på andre enheder. Det kan du gøre ved at tilføje politikker, f.eks. næste generations beskyttelsespolitikker eller firewallpolitikker.

Når politikker tilføjes, kan du se, at der tildeles en prioritetsrækkefølge. Du kan redigere prioritetsrækkefølgen for de politikker, du definerer, men du kan ikke ændre prioritetsrækkefølgen for standardpolitikker. Lad os f.eks. antage, at du har tre beskyttelsespolitikker af næste generation til dine Windows-klientenheder. I dette tilfælde er din standardpolitik nummer 3 i prioritet. Du kan ændre rækkefølgen af dine politikker med nummer 1 og 2, men standardpolitikken forbliver nummer 3 på listen. 

**Det vigtigste at huske på ved flere politikker er, at enheder kun modtager den første anvendte politik.** Med henvisning til vores tidligere eksempel på tre næste generations politikker kan du antage, at du har enheder, der er målrettet af alle tre politikker. I dette tilfælde modtager disse enheder politiknummer 1, men modtager ikke politikker nummer 2 og 3. 


## <a name="key-points-to-remember-about-policy-order"></a>Vigtige punkter at huske om politikrækkefølge

- Politikker tildeles en prioritetsrækkefølge.
- Enheder modtager kun den første anvendte politik.
- Du kan ændre prioritetsrækkefølgen for politikker.
- Standardpolitikker får den laveste prioritetsrækkefølge.

## <a name="next-steps"></a>Næste trin

- [Kom i gang med at bruge Defender for Business](mdb-get-started.md)
- [Administrer enheder](mdb-manage-devices.md)
- [Få vist og administrer hændelser i Defender for Business](mdb-view-manage-incidents.md)
- [Reager på og afhjælp trusler i Defender for Business](mdb-respond-mitigate-threats.md)
- [Gennemse afhjælpningshandlinger i Løsningscenter](mdb-review-remediation-actions.md)