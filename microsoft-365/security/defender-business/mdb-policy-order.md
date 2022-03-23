---
title: Forstå politikrækkefølgen i Microsoft Defender for Business
description: Få mere at vide om prioritetsrækkefølgen med politikker i Microsoft Defender for Business
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 02/24/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 373f3eb821e00f903837f98896ed5dab0588e946
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/17/2022
ms.locfileid: "63593050"
---
# <a name="understand-policy-order-in-microsoft-defender-for-business"></a>Forstå politikrækkefølgen i Microsoft Defender for Business

> [!IMPORTANT]
> Microsoft Defender for Business udrulles til [Microsoft 365 Business Premium](../../business-premium/index.md) kunder fra d. 1. marts 2022. Defender for Business som et enkeltstående abonnement er i preview, og den udrulles gradvist til kunder og [it-partnere](https://aka.ms/mdb-preview) , der tilmelder sig her for at anmode om det. [Forhåndsvisning indeholder et indledende sæt scenarier](mdb-tutorials.md#try-these-preview-scenarios), og vi tilføjer funktioner regelmæssigt.
> 
> Nogle oplysninger i denne artikel relaterer til foreløbige produkter/tjenester, der kan være væsentligt ændret, før de frigives kommercielt. Microsoft giver ingen garantier, udtrykkelige eller underforståede, for de oplysninger, du har angivet her. 

## <a name="policy-order-in-microsoft-defender-for-business"></a>Politikrækkefølge i Microsoft Defender for Business

Microsoft Defender for Business indeholder foruddefinerede politikker, der er med til at sikre, at de enheder, dine medarbejdere bruger, er beskyttede. Dit sikkerhedsteam kan også tilføje nye politikker. Antag f.eks., at du vil anvende visse indstillinger på visse enheder og andre indstillinger på andre enheder. Det kan du gøre ved at tilføje politikker, f.eks. næste generations beskyttelsespolitikker eller firewallpolitikker.

Når politikker tilføjes, vil du bemærke, at der er tildelt en prioritetsrækkefølge. Du kan redigere prioritetsrækkefølgen for de politikker, du definerer, men du kan ikke ændre prioritetsrækkefølgen for standardpolitikker. Antag f.eks., at du har tre Windows næste generations beskyttelsespolitikker til dine Windows klientenheder. I dette tilfælde er standardpolitikken nummer 3 i prioritet. Du kan ændre rækkefølgen af dine politikker, der er nummereret 1 og 2, men standardpolitikken forbliver nummer 3 på listen. 

**Det vigtige at huske om flere politikker er, at enhederne kun modtager den første anvendte politik.** Når vi henviser til vores tidligere eksempel på tre næste generations politikker, så forestil dig, at du har enheder, der er målrettet af alle tre politikker. I dette tilfælde modtager disse enheder politik nummer 1, men modtager ikke politikker med nummer 2 og 3. 

>
> **Har du et minut?**
> Tag vores korte <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">undersøgelse om Microsoft Defender for Business</a>. Vi vil meget gerne høre fra dig!
>

## <a name="key-points-to-remember-about-policy-order"></a>Vigtige punkter, du skal huske om rækkefølgen af politikker

- Politikker tildeles en prioritetsrækkefølge.

- Enheder modtager kun den første anvendte politik.

- Du kan ændre prioritetsrækkefølgen for politikker.

- Standardpolitikker får den laveste prioritetsrækkefølge.

## <a name="next-steps"></a>Næste trin

- [Kom i gang med at bruge Defender for Business](mdb-get-started.md)

- [Administrer enheder](mdb-manage-devices.md)

- [Få vist og administrer hændelser i Microsoft Defender for Business](mdb-view-manage-incidents.md)

- [Re besvare og afhjælpe trusler i Microsoft Defender for Business](mdb-respond-mitigate-threats.md)

- [Gennemse afhjælpningshandlinger i Handlingscenter](mdb-review-remediation-actions.md)