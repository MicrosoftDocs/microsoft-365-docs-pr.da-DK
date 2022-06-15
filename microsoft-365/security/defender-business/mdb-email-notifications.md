---
title: Konfigurer mailmeddelelser til dit sikkerhedsteam
description: Konfigurer mailmeddelelser for at fortælle dit sikkerhedsteam om beskeder og sikkerhedsrisici i Defender for Business.
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
ms.collection: M365-security-compliance
ms.openlocfilehash: b6ffc1325eb71bf366761545c8e21bfe5da3b4fa
ms.sourcegitcommit: 66228a5506fdceb4cbf0d55b9de3f2943740134f
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/15/2022
ms.locfileid: "66090096"
---
# <a name="set-up-email-notifications"></a>Konfigurer mailmeddelelser

Du kan konfigurere mailmeddelelser til dit sikkerhedsteam. Når der derefter genereres beskeder, eller der registreres nye sikkerhedsrisici, får personer i dit sikkerhedsteam automatisk besked. 

## <a name="what-to-do"></a>Sådan gør du

1. [Få mere at vide om typer af mailmeddelelser](#types-of-email-notifications).
2. [Få vist og rediger indstillinger for mailbeskeder](#view-and-edit-email-notifications).
3. [Fortsæt til de næste trin](#next-steps).



## <a name="types-of-email-notifications"></a>Typer af mailmeddelelser

Når du konfigurerer mailmeddelelser, kan du vælge mellem to typer, som beskrevet i følgende tabel:

| Meddelelsestype  | Beskrivelse  |
|---------|---------|
| Sårbarheder  | Når der registreres nye udnyttelser eller sårbarhedshændelser, modtager modtagerne en mail. |
| Beskeder & sikkerhedsrisici  | Når der genereres beskeder, fordi der registreres trusler på enheder, eller når der registreres nye udnyttelser eller sårbarhedshændelser, modtager modtagerne en mail. |

> [!TIP]
> **Mailmeddelelser er ikke den eneste måde, dit sikkerhedsteam kan finde ud af om nye beskeder eller sikkerhedsrisici**.
> 
> Mailmeddelelser er en praktisk måde at holde dit sikkerhedsteam informeret på i realtid. Men der er andre! Når dit sikkerhedsteam f.eks. logger på Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)), får de vist kort, der fremhæver nye trusler, beskeder og sårbarheder. Defender for Business er designet til at fremhæve vigtige oplysninger, som dit sikkerhedsteam bekymrer sig om, så snart de logger på.
> 
> Dit sikkerhedsteam kan også vælge **Hændelser** i navigationsruden for at få vist oplysninger. Du kan få mere at vide under [Få vist og administrer hændelser i Microsoft Defender til virksomheder](mdb-view-manage-incidents.md).

## <a name="view-and-edit-email-notifications"></a>Få vist og rediger mailmeddelelser

Hvis du vil have vist eller redigere indstillinger for mailbeskeder for dit firma, skal du følge disse trin:

1. Gå til Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på.

2. Vælg **Indstillinger** i navigationsruden, og vælg derefter **Slutpunkter**. Vælg derefter **Mailmeddelelser** under **Generelt**. 

3. Gennemse oplysningerne under fanerne **Beskeder** og **Sikkerhedsrisici** .

   - Hvis du ikke kan se nogen elementer på fanen **Beskeder** , kan du oprette en regel for personer, der skal have besked, når der genereres beskeder. Hvis du vil have hjælp til denne opgave, skal du se [Opret regler for beskeder](../defender-endpoint/configure-email-notifications.md).

   - Hvis du ikke kan se nogen elementer på fanen **Sårbarheder** , kan du oprette en regel, der giver personer besked, når der registreres en ny sikkerhedsrisiko. Hvis du vil have hjælp til denne opgave, skal du se [Opret regler for hændelser for sårbarheder](../defender-endpoint/configure-vulnerability-email-notifications.md).

   - Hvis du har oprettet regler, skal du vælge en regel for at redigere den. Du kan også slette en regel. 

> [!IMPORTANT]
> Når du konfigurerer mailmeddelelser i Defender for Business, skal du tildele meddelelsesreglerne til bestemte brugere. Defender for Business bruger ikke [rollebaseret adgangskontrol, som Defender for Endpoint gør](../defender-endpoint/rbac.md). Mailmeddelelser kan heller ikke anvendes på enhedsgrupper i Defender for Business. 

## <a name="next-steps"></a>Næste trin

Fortsæt til:

- [Trin 4: Onboard enheder til Microsoft Defender til virksomheder](mdb-onboard-devices.md)
