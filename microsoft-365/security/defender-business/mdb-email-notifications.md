---
title: Konfigurer mailmeddelelser til dit sikkerhedsteam
description: Konfigurer mailmeddelelser for at fortælle personer om beskeder og sikkerhedsrisici med Microsoft Defender til virksomheder
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 04/12/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection: M365-security-compliance
ms.openlocfilehash: a65634a5827e60d710cec56ca10835c73053cb10
ms.sourcegitcommit: e3bc6563037bd2cce2abf108b3d1bcc2ccf538f6
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/15/2022
ms.locfileid: "64862846"
---
# <a name="set-up-email-notifications"></a>Konfigurer mailmeddelelser

> [!NOTE]
> Microsoft Defender til virksomheder er nu inkluderet i [Microsoft 365 Business Premium](../../business-premium/index.md). 

Du kan konfigurere mailmeddelelser til dit sikkerhedsteam. Når der derefter genereres beskeder, eller der registreres nye sikkerhedsrisici, får personer i dit sikkerhedsteam automatisk besked. 

## <a name="what-to-do"></a>Sådan gør du

1. [Få mere at vide om typer af mailmeddelelser](#types-of-email-notifications).

2. [Få vist og rediger indstillinger for mailbeskeder](#view-and-edit-email-notifications).

3. [Fortsæt til de næste trin](#next-steps).


>
> **Har du et øjeblik?**
> Tag vores <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">korte undersøgelse om sikkerhed</a>. Vi vil meget gerne høre fra dig!
>

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

## <a name="next-steps"></a>Næste trin

Fortsæt til:

- [Trin 4: Onboard enheder til Microsoft Defender til virksomheder](mdb-onboard-devices.md)
