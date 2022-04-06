---
title: Konfigurer mailbeskeder til dit sikkerhedsteam
description: Konfigurer mailbeskeder til at fortælle personer om vigtige og sårbarheder med Microsoft Defender for Business
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 03/15/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection: M365-security-compliance
ms.openlocfilehash: bf11ed140d2e0609f2d12d1da3bcc448ff733235
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/20/2022
ms.locfileid: "63683137"
---
# <a name="set-up-email-notifications"></a>Konfigurer mailbeskeder

> [!IMPORTANT]
> Microsoft Defender for Business udrulles til [Microsoft 365 Business Premium](../../business-premium/index.md) kunder fra d. 1. marts 2022. Defender for Business som et enkeltstående abonnement er i preview, og den udrulles gradvist til kunder og [it-partnere](https://aka.ms/mdb-preview) , der tilmelder sig her for at anmode om det. [Forhåndsvisning indeholder et indledende sæt scenarier](mdb-tutorials.md#try-these-preview-scenarios), og vi tilføjer funktioner regelmæssigt.
> 
> Nogle oplysninger i denne artikel relaterer til foreløbige produkter/tjenester, der kan være væsentligt ændret, før de frigives kommercielt. Microsoft giver ingen garantier, udtrykkelige eller underforståede, for de oplysninger, du har angivet her. 

Du kan konfigurere mailbeskeder til dit sikkerhedsteam. I tilfælde af at der genereres beskeder, eller nye sårbarheder opdages, får personer i sikkerhedsteamet besked automatisk. 

## <a name="what-to-do"></a>Hvad kan du gøre?

1. [Få mere at vide om typer af mailmeddelelser](#types-of-email-notifications).

2. [Få vist og rediger indstillinger for mailbeskeder](#view-and-edit-email-notifications).

3. [Fortsæt til de næste trin](#next-steps).


>
> **Har du et minut?**
> Tag vores korte <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">undersøgelse om Microsoft Defender for Business</a>. Vi vil meget gerne høre fra dig!
>

## <a name="types-of-email-notifications"></a>Typer af mailbeskeder

Når du konfigurerer mailmeddelelser, kan du vælge mellem to typer, som beskrevet i følgende tabel: <br/><br/>

| Meddelelsestype  | Beskrivelse  |
|---------|---------|
| Sårbarheder  | Når der registreres nye udnyttelses- eller sikkerhedsrisikohændelser, modtager modtagerne en mail. |
| Beskeder & sårbarheder  | Når der genereres beskeder, fordi der registreres trusler på enheder, eller når der registreres nye udnyttelses- eller sikkerhedsrisikohændelser, modtager modtagerne en mail. |

> [!TIP]
> **Mailbeskeder er ikke den eneste måde, hvorpå dit sikkerhedsteam kan få oplysninger om nye beskeder eller sårbarheder**.
> 
> Mailmeddelelser er en praktisk metode til at holde dit sikkerhedsteam informeret i realtid. Men der er andre! Når sikkerhedsteamet f.eks. logger på Microsoft 365 Defender -portalen ([https://security.microsoft.com](https://security.microsoft.com)), får de vist kort, der fremhæver nye trusler, advarsler og sårbarheder. Defender for Business er udviklet til at fremhæve vigtige oplysninger, som dit sikkerhedsteam er særligt opmærksom på, så snart de logger på.
> 
> Dit sikkerhedsteam kan også vælge **Hændelser i navigationsruden** for at få vist oplysninger. Du kan få mere at [vide under Få vist og administrer hændelser i Microsoft Defender for Business](mdb-view-manage-incidents.md).

## <a name="view-and-edit-email-notifications"></a>Få vist og redigere mailbeskeder

Hvis du vil have vist eller redigere indstillinger for mailbeskeder for din virksomhed, skal du følge disse trin:

1. Gå til Microsoft 365 Defender -portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på.

2. I navigationsruden skal **du Indstillinger** slutpunkter og derefter **vælge Slutpunkter**. Derefter skal du under **Generelt** vælge **Mailbeskeder**. 

3. Gennemse oplysningerne under **fanerne Vigtige** beskeder **og sårbarheder** .

   - Hvis du ikke kan se nogen elementer på fanen Beskeder,  kan du oprette en regel for personer, der skal have besked, når der genereres beskeder. Hvis du vil have hjælp til denne opgave, skal [du se Opret regler for beskeder om beskeder](../defender-endpoint/configure-email-notifications.md).

   - Hvis du ikke kan se nogen elementer på fanen Sårbarheder, kan du oprette en regel, som giver personer besked, når der opdages en ny sikkerhedsrisiko. For at få hjælp til denne opgave skal du [se Opret regler for sikkerhedsrisikohændelser](../defender-endpoint/configure-vulnerability-email-notifications.md).

   - Hvis du har oprettet regler, skal du vælge en regel for at redigere den. Du kan også slette en regel. 

## <a name="next-steps"></a>Næste trin

Fortsæt til:

- [Trin 4: Onboard-enheder til Microsoft Defender for Business](mdb-onboard-devices.md)
